---
layout: post
title: "Cat Command"
description: "Using the cat command to combine several files in to a new file"
tags: [Linux, UNIX, grep]
---

Here is another Linux command that I want to remember; the cat command.

## My Linux command posts

These posts are NOT supposed to be exhaustive documentation for the commands they cover, but are here as a reminder for myself as I've found them useful and my memory is terrible.

## The cat command

The cat (concatenate) command is pretty useful. It can be used make files, look at the contents of a file and combine files to make a new one.

<div class="slides-container">
<div class="center">
<iframe src="//giphy.com/embed/o0vwzuFwCGAFO" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="http://giphy.com/gifs/cat-hacker-webs-o0vwzuFwCGAFO">via GIPHY</a></p>
</div>
</div>

## Why I needed it

The task it came in useful for was to combine the logs from several days from several load balanced servers.

## How I used it

    cat file1.txt file2.txt > myNewFile.txt
    
Much easier than going in to each file, copying the contents, pasting in to a new file and remembering which files I had already done.

[Here](/grep-command/) is the link to my other Linux command posts.
