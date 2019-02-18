---
layout: post
title: "AWS Cognito - Higher Order Component"
description: "Using a React Higher Order Component to handle AWS Cognito sign ins"
tags: [AWS, Cognito, React]
---

I've been building a React app recently that uses AWS Cognito for its authentication. Several of the components were using the same Auth logic to check if they should render or not.

To remove the duplication and keep my authentication logic in one place I created a Higher Order Component.

## Signing in with AWS Cognito Javascript SDK

I wanted certain pages of my React application to be only reachable by authenticated users. For authentication I'm using Cognito from AWS along with the [Amazon Cognito Identity SDK for JavaScript](https://www.npmjs.com/package/amazon-cognito-identity-js).

The AWS JS SDK makes it really easy to interact with Cognito from your JS application. Signing up users, verifying users’ emails, and signing in users are pretty straightforward but those are for blog posts for another day.

To check if a user is signed in, you create a user pool to get the current user. Then if there is a current user, get their current session.

    var poolData = {
        UserPoolId: '', // your user pool id here
        ClientId: '' // your app client id here
    };
    var userPool = new AmazonCognitoIdentity.CognitoUserPool(poolData);
    var cognitoUser = userPool.getCurrentUser();

    if (cognitoUser != null) {
        cognitoUser.getSession((err, session) => {
            if (err) {
                console.log('error:', err.message || JSON.stringify(err));
                // redirect to sign in page
            }
            // handle authenticated user
        })
    } else {
        // redirect to sign in page
    }

This is pretty straightforward but you don’t want to be duplicating this code on every page that you want to check if a user is authentication on though. This is where Higher Order Components for React can help out.

## Cross cutting concerns

Application requirements that are needed throughout an application but aren’t necessarily part of the main application are sometimes referred to as cross cutting concerns. Logging and security are good examples of cross cutting concerns. 

Using the decorator pattern is a good way of dealing with cross cutting concerns. This allows you to keep your actual application logic clean while adding, potentially multiple, decorating pieces of functionality around it.

## Higher Order Components

A Higher Order Component is like a higher order function in Javascript. It is a function that takes a component and returns a new component.

Acting just like the decorator pattern, a Higher Order Component can be used to add logic or cross cutting concerns to components while keeping the original component clean. 

## Creating a Higher Order Component

For my needs, a Higher Order Component will allow me to add my Cognito authentication logic to multiple page components cleanly. In the example below, the Cognito user check is in the componentDidMount function. If the user and session is valid, a boolean check in the state of the component is set to true. If the user check or the session doesn’t return successfully the component will redirect to the sign in page.

In the render function, it checks the loggedIn boolean in the state, then if true, it returns the component that was passed to the Higher Order Component.

    import * as React from 'react'
    import * as AmazonCognitoIdentity from 'amazon-cognito-identity-js'
    import { withRouter } from 'react-router-dom'

    const withAuth = Component => {
        class WithAuthUser extends React.Component {
            constructor(props) {
                super(props);

                this.state = {
                    loggedIn: false,
                }

                this.onSession = this.onSession.bind(this)
            }

            onSession(err, session) {
                if (err) {
                    console.log('error:', err.message || JSON.stringify(err));
                    this.props.history.push('/signin')
                }
                this.setState({ loggedIn: true })
            }

            componentDidMount() {
                var poolData = {
                    UserPoolId: '', // your user pool id here
                    ClientId: '' // your app client id here
                };
                var userPool = new AmazonCognitoIdentity.CognitoUserPool(poolData);
                var cognitoUser = userPool.getCurrentUser();

                if (cognitoUser != null) {
                    cognitoUser.getSession(this.onSession)
                } else {
                    this.props.history.push('/signin')
                }
            }

            render() {
                if (this.state.loggedIn) {
                    return (
                        <Component {...this.props} />
                    );
                } else {
                    return null
                }
            }
        }

        return withRouter(WithAuthUser)
    }

    export default withAuth

## To use a Higher Order Component

To use a Higher Order Component you import the component like any other component;

    import withAuth from './withAuth'

Then wrap it around the component you want to apply the decorating logic to;

    const ExampleComponent = () => {
        <p>My component!</p>
    }

    export default withAuth(ExampleComponent)

For some more examples of Higher Order Components in React, you can check out the documentation for them [here](https://reactjs.org/docs/higher-order-components.html).
