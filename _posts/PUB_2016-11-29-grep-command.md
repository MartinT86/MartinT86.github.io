---
layout: post
title: "Grep Command"
description: "Using the grep command to filter a file and put the results in a new file"
tags: [Linux, UNIX, grep]
---

As Linux continues to blow my mind, I thought I better start getting down some of the commands that I've been finding useful.

## My Linux command posts

These posts are NOT supposed to be exhaustive documentation for the commands they cover, but are here as a reminder for myself as I've found them useful and my memory is terrible.

## The grep command

The grep command is used for searching text for regular expressions and returning the lines that match. The result can then be output to a new file

## Why I needed it

Recently I asked to get certain details out of a very large log file. My first thought was to open the log in Excel and start filtering away. But then a Linux loving colleague showed me the grep command.

<iframe src="//giphy.com/embed/EldfH1VJdbrwY" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="http://giphy.com/gifs/tim-and-eric-mind-blown-EldfH1VJdbrwY">via GIPHY</a></p>

## How I used it

    grep "the text I was searching for" mylogfile.log > newfile.txt
    
I couldn't believe how easy and fast this made a boring task. Definitely a command I need to remember.
