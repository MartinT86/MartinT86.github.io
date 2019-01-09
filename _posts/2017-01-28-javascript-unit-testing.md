---
layout: post
title: "Introduction to Javascript Unit Testing"
description: "Here is my first attempt at unit testing in Javascript"
tags: [TDD, Unit Tests, Javascript]
---

I've decided to learn how unit testing can work in Javascript in order to start writing Javascript I trust.
Here is my mocha [example](https://github.com/MartinT86/mochaexample)

## Mocha

I decided to go with [Mocha](https://mochajs.org/) as my test framework as it seems pretty popular and I've heard good things about it.

Good old npm made it easy to setup as usual.

    npm install mocha --save-dev
    
I decided not to bring in any assertion libraries such as Chai as it was a small project, relying on node's
assert library seemed adequate.

If any of my tests get more complicated I may look at other assertion libraries, but so far I feel that if a test 
needs a complicated assertion then the test itself is likely to be testing more that one thing.

## Pending tests

One of the fetures of mocha that I was really impressed with was the ability to have pending tests.

If you call the "it" function with only a decsription, in the results the test will be show up as pending.
This feature could be really useful to get all the requirements down first and work through them as a check list.

### done()

If you have any asynchronous code that has a callback you'll need to use the done method.
Mocha passes the done parameter to each test, it can then be called from the callback function.

Without done, any tests that have asynchronous code will always return positive as the assertion will not have been called.
This is one thing I didn't like about mocha, for me, if a test has no assertion it should return negative.

    describe('service(param, callback)', function () {
        it('should square the first param', function (done) {
            var param = 3;
            var expectedResult = 9;
            callbackExample.service(param, function (err, data) {
                assert.equal(data, expectedResult);
                done();
            });
        });
    });

## npm scripts

To run the tests easily I put the command in to the package.json, using the local install of mocha.

    "scripts": {
      "test": "node ./node_modules/mocha/bin/mocha"
    },

## Refactoring

As with any unit tests, having mocha tests in place has made refactoring a lot easier.

When making applications in node, my code is much easier to break down in to small, testable modules.
I find its a good rule of thumb that if code is difficult to test, it's probably not designed very well.

