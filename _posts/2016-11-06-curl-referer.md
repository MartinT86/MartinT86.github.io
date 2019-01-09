---
layout: post
title: "curl referer"
description: "Setting the curl referer option to spoof requests from other sites"
tags: [curl]
---

I had to use the referer option on a curl command recently in order to spoof the referer header.
After initially thinking my code wouldn't be testable until going live, I was pretty pleased 
to find this option was available.

## My curl posts

The more I use curl the more useful I think it is.
Each time I find a useful command or option I'm going to make a post about it so I can use it as a reference.
If anyone else finds it useful as well, that's awesome. 

## What is curl

According to the [curl website](https://curl.haxx.se/), curl is "used in command lines or scripts to transfer data".
I use it most day to day to test websites I'm working on. 

It's incredibly useful for testing things like
redirect status codes as you don't get all the overly aggressive caching that you often get with browsers.

## Referer option

<figure>
	<a href="{{ site.url }}/images/referer.png"><img src="{{ site.url }}/images/referer.png" alt="Referer header"></a>
	<figcaption>The referer header</figcaption>
</figure>

This post is all about the referer option on the curl command.
By using the referer option, you can set the referer header.

You can use -e or --referer.

    curl -e https://www.google.co.uk/ http://mywebsite.com

For full curl options here is the [documentation](https://curl.haxx.se/docs/manpage.html#-e)

## Using the Referer option to debug a .net solution

Recently I had to implement a feature on a site where the logic depended on what the referring site was.

Initially I thought this work was going to be untestable until it went live I could get the real 
site in the referer header.

However by using the -e option on the curl command I was able to set the referring site and
still be able to hit breakpoints in my Visual Studio solution.