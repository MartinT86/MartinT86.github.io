---
layout: post
title: "Razor view interfaces"
description: "Using interfaces for razor view models to make your views more flexible"
tags: [Razor, MVC, NancyFx, Atomic Design]
---

By using interfaces rather than classes for Razor models you can decouple them and make them more flexible.

## Atomic Design

After reading [Brad Frost's awesome blog post on atomic design](http://bradfrost.com/blog/post/atomic-web-design/) 
I got to thinking how a similar approach could be taken with Razor views.

Here is a very brief introduction to some concepts from Atomic Design.

Atomic Design is based around creating design systems from reusable and composable parts.
These are split in to five sections.

#### Atoms

Atoms are the smallest parts of the system. They can include the styles of a button or heading for example.

#### Molecules

When you start to gather several Atoms together you end up with a Molecule.
An example would be a site search form. Consisting of an input atom, a label atom and a button atom.
This molecule can then be used in different places on the site.

#### Organisms

Organisms are made by bringing together molecules to form parts of a UI.
For example a navigation molecule and a site search molecule might make up a site's header.

#### Templates

A template is the framework for a page and how it will look when the organisms are arranged.

#### Pages

Once the template is populatd with final content the page is then complete.

I found this concept of breaking down designs brilliant and it really reminded me of the 
Don't Repeat Yourself rule in development.

## Razor views

I started thinking how the principles of Atomic Design could be applied to Razor views.
After some experimenting I realised that you could use an interface as the model for a strongly
typed view. This sounds like a small impact but it was news to me and opened up a possibilities.

