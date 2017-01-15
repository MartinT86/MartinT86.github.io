---
layout: post
title: "What is a unit of work?"
description: "I've been evaluating my definition of a unit of work for testing"
tags: [TDD, Unit Tests]
---

Recently I've been looking at how a unit of work should be tested and asking myself the question "should every class have it's own unit
test?"

## A test per class?

A lot of my unit testing historically has been around making sure every class is individually tested. Every dependecy in the
class would be mocked so I could focus the test on the class itself.

However, I've been experimenting with testing a full unit of work rather than just each class itself. In some cases this might be a single class but only if the class covers a unit of work.

## The boundaries

For my dependecies I now create a new instance of each so in effect I am still testing each class, just not individually.

These aren't integration tests though. The boundaries will still be mocked out. The boundaries may be external, such as 
a database or an api, or they may be internal still, such as the layers of the application.

## Refactoring

By focusing on the tests on what the code is trying to achieve and not the implementation I have found it much easier to refactor.

If a class or method is becoming too bulky and needs to be abstracted in to a new class for example, the test will still cover this new class while still ensuring the desired outcome is still happening.

With not having to keep in my head how all these little classes will fit together to perform the pice of work, my confidence in wanting to refactor has grown. When each little class is just tested individually, with no tests to ensure they are are fitting together
I find I can be reluctant to start changing the design of the system.

## Reveal intent

The increased scope of my unit tests from class to unit of work has helped not only my code, but helped my tests to follow one of Kent
Beck's [4 simple design rules](http://martinfowler.com/bliki/BeckDesignRules.html);

> Reveals intention

I've always taken care when naming tests, but now my names tend to be more useful. They have moved from names such as;

    [Test]
    public void GivenValueIsX_DependencyBIsCalled()
    {
      //testing the individual class goes here
    }

To something more like;

    [Test]
    public void GivenAFormPost_TheCorrectDataIsCalculatedThenStored()
    {
      //here a call will be made to the controller
      //new up the required services rather than mock them
      //only the external call to the database would be mocked
    }

Again, I'm finding this means I have to keep less of the systems reasoning in my head. I don't have to remember why its important
a certain service is called. The test will tell me why something is happening and test the result. It doesn't care how I
get there.

## So should every class have its own unit test?

No.

Unless there is a good reason, such as external dependencies, each class should be covered by tests but not necessarily
their own.
