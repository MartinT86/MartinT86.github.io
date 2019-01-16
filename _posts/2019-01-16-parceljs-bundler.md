---
layout: post
title: "ParcelJS Bundler"
description: "The promise of a zero config bundler was just too strong for me not to check out"
tags: [Javascript, Bundler]
---

As Javascript continues its march to world domination, it's great to keep up with all of the new tools. However, if you are like me, then some of the build tools can be pretty daunting.

Webpack and Gulp are awesome and really do add a lot of value but I've found they can take a long time to setup and configure. So when I heard about [Parcel](https://parceljs.org/) I had to give it a go.

## What is Parcel?

Parcel is a web application bundler that promises to be zero configuration and fast.

The zero configuration was the real draw for me. Build times are important in software development, but when you are measuring builds in seconds, the hours/days I've lost to other bundlers is more important to me.

Out of the box it supports a lot of the JS/front end world's big names. SCSS, Typescript, Vue and more are all there.

It even has hot reloading just like create react app.

## Setup

Setup is super easy.

Install Parccel globally

    npm install -g parcel-bundler

Then run Parcel with your entry point, for example

    parcel index.html

Simple.

## Build

When it's time to build your application, you just need the build flag;

    parcel build index.html

This will place the built application in a folder called dist at the package.json level. I've not seen a way to change that, but I guess that's the point of a zero configuration system.

## The demo

If you are giving Parcel a try, one thing to keep in mind is that the simple example on the homepage doesn't work out of the box.

I lost a bit of time to this but found a [Github issue](https://github.com/parcel-bundler/parcel/issues/823) in the end.
The Parcel homepage example is using postcss-modules, but Parcel doesn't support that out of the box.
It looks pretty easy to add, but it seems a strange choice to include it in the first example.

## What's next?

ParcelJS has massively impressed me. With a mountain of frameworks and tools I want to learn, I can see myself leaning on it quite a bit. For example, I really want to put some time in to Typescript and Parcel will mean I can spend more time in Typescript and less on seeting up the project and bundler.
