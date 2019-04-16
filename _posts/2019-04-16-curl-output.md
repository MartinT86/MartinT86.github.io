---
layout: post
title: "curl output"
description: "Saving the output from curl to a file using the output option"
tags: [curl]
---

I've just seen a really useful option for curl commands; using the output option to save the return value to a file.

## Using curl

Curl isn't a tool I use everyday, but whenever I do, it always impresses me at how useful it is.

By using curl on the command line or in scripts, you can automate grabbing data from URLs. This can be super useful to speed up manual processes. By using the curl options to check things like headers you can quickly get through a lot of URLS that would have taken a long time by using a browser manually.

## Output option

Using the output option, the data returned from the curl command will be saved to a file rather than stdout.

For example;

	curl http://myurl.com -o myfile.txt

or 

	curl http://myurl.com --output myfile.txt

You can check out the rest of the curl options [here](https://curl.haxx.se/docs/manpage.html#-o).

## Future processes

I saw this option while downloading the install script for the Python package installer (pip).
But I thought this would be helpful in automating processes where I had to get information from URLs and save the outputs, then use those files as an input to another process.

If anyone else knows of any useful curl options I would love to hear them!