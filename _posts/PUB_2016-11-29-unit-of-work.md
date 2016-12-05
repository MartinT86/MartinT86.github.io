---
layout: post
title: "What is a unit of work?"
description: "I've been evaluating my definition of a unit of work for testing"
tags: [TDD, Unit Tests]
---

Recently I've been looking at how a unit of work should be tested and asking myself the question "should every class have it's own unit
test?"

## What is a unit of work?

## A test per class

A lot of my unit testing historically has been around making sure every class is individually tested. Every dependecy in the
class would be mocked so I could focus the test on the class itself.

However, I've been experimenting with testing a full unit of work rather than just each class itself.

## The boundaries

For my dependecies I now create a new instance of each so in effect I am still testing each class, just not individually.

These aren't integration tests though. 

## Refactoring

## Reveal intent

## Slower
