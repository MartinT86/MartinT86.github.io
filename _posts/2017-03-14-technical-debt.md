---
layout: post
title: "Technical debt"
description: "Why I don't like the term technical debt"
tags: [Technical debt, Value]
---

You hear the term "technical debt" a lot in development. You also hear a lot of discussion about how to deal with it.
Here I'm going to discuss why I don't like the term.

## What is technical debt

From my experience, "technical debt" is a term applied to any technical task that isn't directly related to a new feature.

Examples of this could be, refactoring an old piece of code, scripting the creation of a site or putting a new type of 
automated tests in place.

## Why I don't like the term

I'm not saying technical tasks aren't important. I hope they are or I'd be out of work.

The term "technical debt" hides the real reason that the technical task should be carried out. I see it as if someone asks why
you are doing that task your response could be "you don't need to worry about it, it's technical".

It implies that there isn't value to be gained from doing that work, like paying a debt, you aren't improving your balance just getting
back to zero.

It's a very rare situation that you have unlimited
resources to polish and refine something. Decisions are made when "enough is enough", and I feel that is a benefit of working in
an agile environment. You get as much value as you can for the decided budget.

## Focus on value

You need to ask yourself "why do I feel this task needs doing?".

As with adding a new feature (I hope) you would set out your success criteria, the problem you are trying to solve and the value you hope to gain.

Lets take an old piece of code that could do with some refactoring as an example.
When was this code last updated? Are you likely to need to be in this area of the solution anytime soon?
If you haven't touched the code for long time and it's not throwing errors, why does it need refactoring? What's the value to be
gained here?

It's also good to remember that there are different types of value. New features aren't the only things that deliver value.
Scripting the creation of your server for example is something that could easily be classified as technical debt.
However, being able to recover your server quickly in the event of failure sounds pretty valuable to me.

## Then what should we call it?

Perhaps the distinction between "features" and other work is part of the problem? Why does a piece of work need to be 
defined separately to another?

Work is work and you should be working on the most valuable thing you can. It shouldn't matter if that work is adding a new feature 
or updating an old one.

## How we should deal with technical issues

I would say it depends on what this "debt" is.

If it is indeed a piece or "work" then treat it as such. Examine the value you expect to get from it and prioritise it
accordingly.

For any refactoring "debt" I really like Uncle Bob's boy scout rule.
Anyone who knows me, knows I'm a pretty big fan of Uncle Bob (if you've not heard of him, check him out [here](https://sites.google.com/site/unclebobconsultingllc/). 
Basically, you always leave the code in a better state than when you found it. By following this principle, the code base should 
be cleaned up relatively quickly while still delivering value.

Don't get me wrong, refactoring is extremly important but I would be wary of refactoring with the goal of refactoring. If you are refactoring something so new functionality can be added or some other value gained, fantastic. 
If you are refactoring and don't know the value that will come from it, why are you doing it?

## tl;dr

<div class="slides-container">
<div class="center">
<iframe src="//giphy.com/embed/3o6Zt0hNCfak3QCqsw" width="480" height="352" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="http://giphy.com/gifs/the-matrix-there-is-no-spoon-3o6Zt0hNCfak3QCqsw">via GIPHY</a></p>
</div>
</div>

There is no such thing as techincal debt.

There is however, more work to do. Treat it like you would any other piece of work. Understand the expected value and
plan accordingly.


