---
layout: post
title: "Sphero Controller"
description: "My first attempt at creating a controller for my sphero"
tags: [Sphero]
---

<figure>
	<img src="{{ site.url }}/images/sphero_pic.jpg" alt="Sphero">
</figure>

If you've not heard of sphero then I recommend you go check them out now. They are a remote 
controlled sphere with a bluetooth connection and they are a lot of fun. There are plenty of apps
available to control a sphero and its nice to see that there are even some for Windows phone. Unsurprisingly though
the majority of apps are available for ios. They do look cool though, you can draw with the sphero, shoot aliens
and play golf just to name a few. However I wanted a go at making my own controller.

Orbotix have made loads of SDKs available. Ruby, Python, Arduino, PhoneGap, OSX, Node, Unity, Android and more.
I decided to use sphero.js as I'm still teaching myself Node as well. Installation of sphero.js
was pretty straight forward by following the instructions on the [github page](https://github.com/orbotix/sphero.js).
As I'm currently using Ubuntu, I did have to do the extra steps to allow the dialout group permissions
to the bluetooth port. 

The only problem I had, was that I had to use sudo when running node app.js due to the elevated 
permissions. May be obvious to others but as an Ubuntu newbie, had me stumped for a bit.
If you are also on Ubuntu I would also defintely suggest getting the Blueman Blutooth
Manager rather than the built in bluetooth app.

After getting up and running, I decided that I was going to focus on controlling the colour of sphero 
to start with. Making it zip around was fun, but I was too lazy to keep getting up and retrieving 
sphero from under the couch. If you have more energy than I do and want to get the full list of 
commands commands available on Javascript API the docs are available [here](http://sdk.sphero.com/community-apis/javascript-sdk/).

<figure class="third">
	<a href="{{ site.url }}/images/sphero_pic_blue.jpg"><img src="{{ site.url }}/images/sphero_pic_blue.jpg" alt=""></a>
	<a href="{{ site.url }}/images/sphero_pic_red.jpg"><img src="{{ site.url }}/images/sphero_pic_red.jpg" alt=""></a>
	<a href="{{ site.url }}/images/sphero_pic_green.jpg"><img src="{{ site.url }}/images/sphero_pic_green.jpg" alt=""></a>
	<figcaption>Sphero changing colour!</figcaption>
</figure>

I built a simple Express app that connects to the sphero on start up. As with most of my simple Express apps, I went with EJS
for the rendering engine over Jade. Not because I have a problem with Jade, I just find the straight markup in EJS a 
little bit easier to work with usually.

I added a few colour buttons for control, good old bootstrap to the rescue for button styling! 
When each button is pressed it fires a basic jquery ajax post to a pre-defined route wich in turn changes
the colour of the sphero. I went for an ajax call so the page didn't have to refresh each time the sphero changed colour.

To know that the call had fired and just to make the controller look a little nicer
I put a css circle with a gradient on to change the same colour as the sphero. On app start I had the sphero turn white so its
clear everything is connected properly. To make the css circle look
a little bit more like a sphero I used [this nice article](https://cssanimation.rocks/spheres/) for how 
to apply 3D gradients to circles.

<figure class="third">
	<a href="{{ site.url }}/images/sphero-blue.png"><img src="{{ site.url }}/images/sphero-blue.png" alt=""></a>
	<a href="{{ site.url }}/images/sphero-red.png"><img src="{{ site.url }}/images/sphero-red.png" alt=""></a>
	<a href="{{ site.url }}/images/sphero-green.png"><img src="{{ site.url }}/images/sphero-green.png" alt=""></a>
	<figcaption>My basic controller</figcaption>
</figure>

The next thing I aim to do is turn the controller in to a memory game where you have to copy the
list of colours that the sphero flashes. If you want to keep track of my controller, you can find the [repo here](https://github.com/MartinT86/sphero-controller)