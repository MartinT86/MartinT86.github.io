---
layout: post
title: "Concentric Slicing"
description: "When delivering software, slicing your stories can help to deliver value sooner"
tags: [Agile, User Stories, Delivery, Value]
---

As a big fan of agile ways of working, story slicing is pretty important to me. How you break down work can have a huge impact on how quickly you can start realising value. 

Recently I've been thinking of a new way to slice work so it can be delivered iteratively and get the most value in the shortest time.

## Why slice work at all?

It's important to think about how software is delivered, not just the end result. 

Releasing regularly can help to create smaller feedback loops to validate ideas and assumptions, and to help you start getting value for the effort sooner. 

If it is a larger piece of work, slicing up the work avoids a team from working in a waterfall fashion where nothing is seen for a long time and when it is revealed in a tada moment it may be wrong.

## Horizontal and vertical slicing

Two common ways of slicing down work are to do it either horizontally or vertically. 

To look at the differences between horizontal and vertical slices, let's imagine a new form page is needed on a website to collect potential customer details, process this information, and then store them.

## Horizontal

When work is split horizontally, this refers to tasks being divided by each part of a system. For example, you might have one ticket to update the UI, another to update the business logic layer, and finally a ticket to implement a data store.

The issue I have with horizontal slicing is when it comes to releasing work and realising value from the work. In this example, you could only really release to live once all the work has been completed. You can't really release a new form that isn't hooked up to anything.

<div class="center">
<figure>
	<a href="{{ site.url }}/images/concentricslicing/horizontal.png"><img src="{{ site.url }}/images/concentricslicing/horizontal.png" alt="horizontal slices"></a>
	<figcaption>Example horizontal slices</figcaption>
</figure>
</div>

## Vertical

A different way of slicing this work might be to slice it vertically. When slicing vertically it is important for each piece of work to be releasable on its own. An example way of slicing the work here could be to have the first story just collecting a single field, such as email address. But the email address work would be implemented in each layer of the application. Then the following tickets of work would be to expand the form to add in the following fields.

I like vertical slicing as you can release features as they developed, allowing you to get value sooner. You also hit unknowns more quickly, for example if the data later and the domain application are developed separately and there is a disconnect somewhere, you would only find that out when both pieces of work are complete.

However, I do often face the questions, is it worth doing those first super thin slices? How will we get value from those alone? The more I've thought about it, the more I think these are valid questions on vertical slicing. Vertical slicing is of huge benefit to developers but I can see how it can be frustrating or hard to appreciate for a business. Certain functionality was requested but delivering it incrementally can be seen as frustrating.

<div class="center">
<figure>
	<a href="{{ site.url }}/images/concentricslicing/vertical.png"><img src="{{ site.url }}/images/concentricslicing/vertical.png" alt="vertical slices"></a>
	<figcaption>Example vertical slices</figcaption>
</figure>
</div>

## Concentric slicing

This is where I came up with the idea of concentric slicing. Rather than slicing a story or feature along lines in the architecture, I thought it would be useful to slice stories around their value.

What if the first slice was to address the core need in the simplest way possible? Then each following slice would be to expand the functionality by wrapping around the previous slices.

Going back to the form example, the slices could work in the following way. Initially you would need to understand what the main need is. So if the main need was to collect customer details so you contact them and you do need all the fields to do this, the simplest way might be to log out the form entries to a file on the server. This file could then be manually passed to the people doing the customer contact.

This first slice allows the actual value of the work (contacting the customers) in the shortest time. Yes there may be some manual steps after only this first slice is done, but at least you can start validating the value.

Subsequent slices can then focus on refining the process. For example the next slice might be to do some data processing on the form entries but then still log them to the file. Followed by a slice that stores them in a database. With a final slice to automatically contact the customers.

This approach may incur some form of re-work, but I would wager in most cases the cost of that re-work would be greatly outweighed by getting the value from the work as fast as possible and being able to validate the idea much more quickly.

This approach to story slicing can have huge benefits in a time pressured environment. By focusing on where the actual value lies and making sure that gets achieved, allowing for manual process and re-work, you can try and make the first slice meet the actual deadline. Any subsequent stories will just be improving the process and be under much less time pressure.

<div class="center">
<figure>
	<a href="{{ site.url }}/images/concentricslicing/concentric.png"><img src="{{ site.url }}/images/concentricslicing/concentric.png" alt="concentric slices"></a>
	<figcaption>Example concentric slices</figcaption>
</figure>
</div>

## When life doesn't match the theory

I think it's important to remember why we slice work on the first place. We do it so that work can be delivered incrementally by multiple releases and find blockers sooner, and deliver value as quickly as we can.

With that in mind I can't really say one way of story slicing is better than another. You need to take your current context into account. But if you remember why we slice, knowing different ways to do it can help a lot.

If you've got any thoughts on story slicing I'd love to hear them.
