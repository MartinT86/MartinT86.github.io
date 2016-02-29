---
layout: post
title: "Arduino - Initial Setup"
description: "How I got on setting up my Arduino for the first time"
tags: [Arduino, Ubuntu]
---

I've finally got around to setting up my Arduino Uno, a few minor teething problems and I'm away!

I love seeing some of the projects other people have done by using an Arduino. I can't wait to get
that good and be creative with it. For example, check out this [secret knock detecting door lock](http://www.instructables.com/id/Secret-Knock-Detecting-Door-Lock/)

<iframe width="560" height="315" src="//www.youtube.com/embed/zE5PGeh2K9k" frameborder="0"> </iframe>

The first step was to get the Arduino IDE. As I'm working on Ubuntu and still a Linux newbie this in
itself presented me with some challenges. My first attempt was was by using the Ubuntu package manager.
However I realised that the packaged version of the IDE was quite old. At the time of writing this post, 
the apt-get package was 1.0.5, but the version available for download was 1.6.7. So I decided to 
manually install the IDE.

As the Arduino tar came with an install script I didn't have to run configure and make. So after moving 
the extracted folder to the /opt folder, I was able to give the install script executable permission and run it.
I found this [set of instructions](http://ubuntuhandbook.org/index.php/2015/11/install-arduino-ide-1-6-6-ubuntu/)
very useful.

Pretty impressively, the Arduino IDE comes pre-loaded with a quite a few examples. The setup example
I was working through pointed me towards the Blink example.  

<figure>
	<a href="{{ site.url }}/images/blink-example.png"><img src="{{ site.url }}/images/blink-example.png" alt="Blink example in Arduino IDE"></a>
	<figcaption>The blink example provided with the Arduino IDE.</figcaption>
</figure>

Initially I was getting an error when trying to upload onto the board;

> ser_open(): can't open device "/dev/ttyACM0": Permission denied
ioctl("TIOCMGET"): Inappropriate ioctl for device

I found another very helpful [article here](http://arduino-er.blogspot.co.uk/2014/08/arduino-ide-error-avrdude-seropen-cant.html).
By following the instructions on the article I was able to add my user to the dialout group and 
change the filer permissions on /dev/ttyACM0. After this was done the blink example uploaded just
fine.
While this isn't the most exciting thing in the world you can do with an Arduino. It was awesome to 
know that I had successfully uploaded my first program to my board.

<figure>
	<a href="{{ site.url }}/images/arduino-blink.jpg"><img src="{{ site.url }}/images/arduino-blink.jpg" alt="My blinking Arduino!"></a>
	<figcaption>My blinking Arduino!</figcaption>
</figure>

Interestingly, once I had uploaded blink, I then wondered "how do I stop it?". It turns out that there isn't
such a thing as stopping the Arduino. So unless a stop was part of the program (where it wasn't in
blink) it would just keep going until the power supply is stopped.

Now to move on to more interesting lessons! 