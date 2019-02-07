---
layout: post
title: "concurrently npm"
description: "Running multiple process with the concurrently npm package is awesome"
tags: [Javascript, npm, concurrently]
---

Tired of opening multiple terminals to run processes? Then you should check out [concurrently on npm!](https://www.npmjs.com/package/concurrently)

## What was my issue?

Recently I've been working a lot more with JavaScript. This has been great, I'm finding the js world a lot more mature recently.

I'm loving the tooling around JS. Particularly tools such as Parcel JS and good old Express.

However running multiple terminals for different processes was causing me a headache. When writing with others on a project, having to know multiple commands to run the development environment also creates a cognitive overhead that shouldn't be there.

## What is concurrently?

Concurrently to the rescue!

Concurrently is an npm package that allows you to run multiple commands concurrently. A very well named package this one.

## How I used it

I'm never really a fan of installing packages globally, and I wanted to use concurrently via npm scripts so I installed it as a dev dependency.

    npm install concurrently --save-dev

Then with the concurrently command you can pass multiple other commands at the same time, remembering to surround commands with quotes.

    concurrently "my process" "my other process"

To add as a npm script, remember to escape the quotes

    "start": "concurrently \"my process\" \"my other process\""

## Other features

You can find the full documentation [here](https://www.npmjs.com/package/concurrently)

There are loads of options that look useful such as killing other processes of one dies and changing how the prefixing works.

However, since my original issue was to simplify starting a dev environment when working with others remotely, using wildcards to list commands to run looks great.

For example;

    concurrently "npm:watch-*"

Anything that can speed up my development time is good by me, so go give concurrently a try.