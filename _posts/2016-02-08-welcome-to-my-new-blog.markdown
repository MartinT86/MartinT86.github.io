---
layout: post
title:  "Welcome to my new blog!"
date:   2016-02-08 20:41:11 +0000
categories: jekyll blog
---
Thanks for looking at my new blog.

I wanted to start a blog to help me keep track of all the things I learn and any useful resources I have used along the way.
If anyone else is able to find anything useful on here then all the better.

### Blog platform
So I've used blogging platforms before, such as Umbraco and Wordpress.
I wanted my new blog to be something simple to manage and something that would make me want to write rather than working on the blog.
So that pretty much ruled out Umbraco and Wordpress :)

Plus I wanted to learn something new. I've been teaching myself Node recently so Ghost looked pretty interesting.
However I ran in to some issues during testing with hosting Ghost. I ran in to dependency hell on Azure; that coupled with having to 
pay to be able to use a custom domain put me off Azure. Ghost's own hosting looked pretty good but at $8/month, a bit more than I wanted
to pay ideally.

So I settled on Jekyll.

Being able to create posts in markdown looked like a massive benefit to me. Not only so all my posts would be
nicely source controlled. Hosting the blog on github pages is also another massive plus point.

### Setup
After reading the docs for Jekyll i was pretty disappointed. Not in Jekyll but in Windows. Jekyll is yet another tool that is not
fully supported on Windows.

I made the big decision to install Ubuntu on to my old laptop. As a Windows user through and through, I'm sure Ubuntu in itself 
is going to be a learning experience and give me lots to blog about.

Setting up Jekyll itself is super straightforward, with a few commands you have your skeleton and Github pages up and running.
You can find the install instructions [here](https://help.github.com/articles/using-jekyll-with-pages/)

The only pain point I had was with the dependency on Ruby. Using the standard apt-get on Ubuntu I could only figure out how to install 1.9. 
But for Jekyll I needed 2 or higher. From looking through Stack Overflow I could have downloaded the source and complied it but as a
Linux newbie that seemed a little too far off the beaten track for me yet.

Then I found that Brightbox cloud hosting have provided more up to date Ruby packages. Even I was able to follow the instructions they provide [here](https://www.brightbox.com/docs/ruby/ubuntu/)

### Next Steps
I want to keep improving this blog

* Maybe add a theme
* Add new posts on what I've been learning
* Use this blog to help me improve my front end technologies

Thanks for reading,
Martin
