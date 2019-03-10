---
layout: post
title: "Decoding a JWT in Node"
description: "How to decode a JWT from AWS in Node"
tags: [Node, AWS, JWT]
---

In an app I was working on, I wanted to decouple the UI from the other architectural resources by using a Node back-end with an Express API. Using the JSON Web Token provided by Cognito allowed me to authenticate AWS Cognito users in the back-end. 

AWS does have great documentation, but I couldn't find many code examples of how to decode the JWT in Node. So hopefully this post might be able to help somebody in a similar position.

##  Getting the token

The first step is to get the JWT for the Cognito user from the client. The JWT is accessible from the user session when you are using [amazon-cognito-identity-js](https://www.npmjs.com/package/amazon-cognito-identity-js)

    cognitoUser.getSession((err, session) => {
        const token = session.getIdToken().getJwtToken()
    })

## Sending the token with fetch

Once you have your token, you can send that token to your back-end server. In my case I'm using an Express server, so I've set up some routes for my API.

Using the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) I posted the token to the server in the headers.

    fetch("/api/myEndPoint", {
        method: "POST",
        headers: {
            "Content-Type": "application/json",
            "token": token
        },
        body: JSON.stringify({
            something: "some data"
        })
    })

## Get the header

To get the token out of the header in Express, you can get it from the request.

    router.post('/api/myEndPoint', function(req, res, next) {
        var token = req.get("token")

        // { decode and use the token here }

        res.send(200)
    })

## Decode and check the JWT

Once you have the token on the server, you can use [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken) to decode and verify the JWT token.

    const decodedJwt = jwt.decode(token, { complete: true });

The audience on the token should match the app client ID for the Cognito user pool.

    if (decodedJwt.payload.aud !== "{app client ID}") {
        throw new Error('Invalid audience: ' + decodedJwt.payload.aud);
    }

The issuer on the token should match the Cognito issuer URL; which is made up by adding the region and the user pool ID in the URL below.

    if (decodedJwt.payload.iss !== "https://cognito-idp.{region}.amazonaws.com/{user pool ID}") {
        throw new Error('Invalid issuer: ' + decodedJwt.payload.iss);
    }

## Get the JWK

The JSON Web Keys are available by calling the below URL;

https://cognito-idp.{region}.amazonaws.com/{user pool ID}/.well-known/jwks.json

I used [request-promise](https://www.npmjs.com/package/request-promise) to call AWS for the JWKs. However, AWS will return all the JWKs for your account, so you have to then extract the correct JWK by comparing Key ID of the decoded JWT. 

    const options = {
        method: 'GET',
        uri: 'https://cognito-idp.{region}.amazonaws.com/{user pool ID}/.well-known/jwks.json',
        json: true
    }
    
    rp(options)
        .then(jwk => {
            var key = jwk.keys.find(key => {
                return key.kid === decodedJwt.header.kid
            })

            // get the PEM from the JWK
            // verify the JWT
        })

## Get the PEM

Using [jwk-to-pem](https://www.npmjs.com/package/jwk-to-pem) you can then convert the JWK to PEM format to be used to verify the JWT.

    var pem = jwkToPem(key);

## Verify the JWT 

Then by using [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken) again, you can verify the original token against the PEM key.

    jwt.verify(token, pem, function (err, decoded) {
        if (err) {
            throw new Error('error: ', err)
        }
        
        // verified token!
    });

## Conclusion

Hopefully this example will save some time for people who are looking to verify AWS Cognito JWT tokens on their server side back end code.