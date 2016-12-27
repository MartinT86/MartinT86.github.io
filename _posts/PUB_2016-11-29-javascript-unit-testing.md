---
layout: post
title: "Introduction to Javascript Unit Testing"
description: "Here is my first attempt at unit testing in Javascript"
tags: [TDD, Unit Tests, Javascript]
---

I've decided to start writing it properly and learn how unit testing can work in Javascript.

## Mocha

I decided to go with [Mocha](https://mochajs.org/) as my test framework as it seems pretty popular and I've heard good things about it.

Good old npm made it wasy to setup as usual.

    npm install mocha --save-dev
    
Initially I decided not to bring in any assertion libraries such as Chai as it was a small project relying on node's
assert library seemed adequate.

## Pending tests

One of the fetures of mocha that I was really impressed with was the ability to have pending tests.

If you call the "it" function with only a decsription, in the results the test will be show up as pending.
This feature could be really useful to get all the requirements down first and work through them as a check list.

### done()

If you have any asynchronous code that has a callback you'll need to use the done method.

## npm scripts

## Refactoring

As with any unit tests, having mocha tests in place has made refactoring a lot easier.


## Now I'm calmer
