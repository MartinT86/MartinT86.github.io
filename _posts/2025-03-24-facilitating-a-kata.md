---
layout: post
title: "Facilitating a kata"
description: "Some thoughts and tips for facilitating a coding kata"
tags: [TDD, Unit Tests, Kata]
---

Recently I've been lucky enough to have the opportunity to start running some coding katas within my team! I love facilitating katas, they prompt great discussions, it's great practice, and it's great when they take unexpected turns.

## What is a kata?

The term "kata" comes from the martial arts world. It's a set routine of movements that you practice repeatedly until those movements are solidified in to your muscle memory and come to you without having to think about them.

A coding kata is there to do the same thing. It's all about picking the technique you want to practice and focussing on how you do it, until that technique is naturally at your finger tips.

## Kata ideas

A good kata needs a technique to focus on, and a problem to solve.

Some of the classic problems to solve include Checkout Kata, the Bowling Kata, and the Roman Numerals kata.

For the Checkout Kata, you are to create a checkout that can scan multiple items and return a total value. If you want to take the session further you can add in discount rules such as, a discount when 3 of a certain item is scanned.

For the bowling kata, you create a bowling calculator that accepts the number of pins each turn and calculates the game total based on the rules of ten pin bowling.

For Roman Numerals kata, you create an application that takes an integer as an input and returns the corresponding Roman Numeral value.

## It's not the day job!

It's important to remember that a kata isn't your day job. It's a time to learn and take the time to try new ideas and techniques. Especially if you're doing a kata with other people, make sure you explore and talk about everyone's ideas. It's always super interesting to see how different people tackle the same problem.

The quality of the time spent during a kata is far more important than the quantity of the output. If a single line of code gets written but that prompts useful and interesting discussions, that is more valuable than completing any requirements.

Take the time to try different approaches to pairing or mobbing that you may not normally do. While not everything you try might make back to your day job, it's always good to try and share different approaches.

## Be strict in your approach

When doing a kata, I like to take the practices to the extreme. For example, I follow red, green, refactor to the letter. Think about what is the next smallest test that will drive out the design. Once you have that red test, what is the absolute quickest way to make that test green, no jumping ahead to the refactoring stage. If I find my self in a situation where I'm making changes while in a red state, I'll back out those changes and refactor while in a green state. Obviously, the tests must be run frequently!


## Go and practice!

There are loads of ideas and variations of katas out there to try. Go give them a go, and remember, they are for practice and for fun, so think about your approach and enjoy them.

Feel free to use my [blank kata template](https://github.com/MartinT86/ts-kata-blank) to get you started.