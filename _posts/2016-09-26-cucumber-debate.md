---
layout: post
title: "Cucumber Style Tests Debate"
description: "I had the chance to argue for Cucumber style tests; here's how it went"
tags: [User Stories, Cucumber, Specflow, Tests]
---

Recently I had the opportunity to take part in a debate around Cucumber style tests.
Luckily I was arguing for Cucumber tests as I'm actually quite a big fan of them.

## What is Cucumber?

A Cucumber test follows the Given, When, Then style.
For example;

    Given there is a name field
    When I enter a number
    Then an error message is displayed

Cucumber tests are a very useful way of running automated tests, especially user based acceptance tests.
However they are much more than that.

Check out [cucumber.io](https://cucumber.io/) to get a much more detailed explanation.

## My points for Cucumber

### Single source of truth
They provide a single source of truth of the software being created.
Creating a single set of requirements/tests that can follow the software through the entire development life cycle.

### Living documentation
Living documentation is another benefit that comes from using Cucumber tests. 
If the requirements change, you will then have to change the software.
Since you will have breaking tests you are forced to keep them (and you documentation) up to date.  

### Avoiding regression
Since these tests can be automated and be part of a build pipeline, rework can be avoided when new features are added.

### Collaboration
This I think is probably one of the main benefits of this style of test.
Getting the correct Given, When, and Then isn't easy. 
However, whenever I have seen Cucumber used, it has always been a great conversation starter.
It provides a common language for technical and non-technical to come together and focus on the behavior of the software.

## Some well made points against Cucumber

So this was a debate and did have some good arguments againt the use of Cucumber tests.

### It's another tool we need to learn

Yes, it is another tool that people would need to learn. However if you can get it part of your workflow, the benefits should outweigh that effort.
Although I do agree that you don't need Cucumber to get the benefits. 
If you can get the benefits using your current tooling then why would you add another layer of complexity.
But I have found that Cucumber is a great way to start realising those benefits. 

### They are brittle

Yes, Cucumber can tests can become extremely brittle. Especially if they are tightly coupled to a UI.
However I feel that can be said about a lot of code.
Tests should be treated like the code that it is. 
The same care will need to be taken when writing the tests as any code would need, such as following the 4 simple rules of code and refactoring techniques.

## The debate

Here are my great slides from the debate;

<div class="slides-container">
<iframe src="//slides.com/martintierney/deck/embed" width="576" height="420" scrolling="no" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
</div>

And here is the debate itself;

<iframe width="560" height="315" src="https://www.youtube.com/embed/U093groi8Os" frameborder="0" allowfullscreen></iframe>

And the following discussions;

<iframe width="560" height="315" src="https://www.youtube.com/embed/CejGdnzetm8" frameborder="0" allowfullscreen></iframe>

## TL;DR

Cucumber tests can be very useful and are more than just automated tests.
However, as with many tools, they are not a silver bullet. 
They need to be thought about carefully and weigh up are the advantages greater than the cost.