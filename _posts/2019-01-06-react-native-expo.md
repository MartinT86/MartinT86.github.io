---
layout: post
title: "React Native Expo"
description: "My first experiences with React Native and Expo"
tags: [React Native, Expo, Mobile]
---

I've been meaning to take a look at React Native for a while, but I've been pushing it back due to how good web apps are now.

However, the new year is bringing with it the urge to learn and make something new.

## What is React Native

React Native is a framework for building native mobile applications using a single codebase.
After working with mobile applications and trying to keep both an iOS and Android code base inline, the lure of just having one codebase to maintain is pretty strong.

## What is Expo

Expo is a set of tools for helping to create React Native applications. With it being the suggested tool from React Native docs, it seems to be the best way to start and maintain a React Native application.

## Not Git Bash!

Setting up the Expo CLI and getting your first application running is super easy.
The instructions can be found [here](https://facebook.github.io/react-native/docs/getting-started).

One piece of advice that had me stumped for a little while though; don't use git bash!
The expo init command doesn't work with git bash, but it works just fine with cmd.

## Testing on a phone

I'm far from an expert but I do have some experience with native Android development.
Running your local application on a device feels a lot smoother than I remember Android Studio feeling.

<div class="center">
<figure>
	<a href="{{ site.url }}/images/expo.png"><img src="{{ site.url }}/images/expo.png" alt="Expo device testing"></a>
	<figcaption>It's super easy to test a React Native application with Expo</figcaption>
</figure>
</div>

By running 'npm start', Expo wil start up and give you a QR code to scan. Scanning this with the Expo client app will download the Javascript for your application.

This is so much quicker and easier than starting up Android Studio, enabling your device for debugging, and connecting physically.

## Tunnel not LAN

Expo is really impressive when it comes to testing on a device, scan the QR code and you're off.

However, it turns out it is not idiot proof. You can choose to access the app through your network or through tunneling.
For a while I couldn't get it to work through the LAN option on my network. But then I remembered that my router has two channels, it helps to have devices on the same network when trying to connect via the network I guess.

## React Native Debugger

Another feature that really impressed me were the debugging capabilities.

Initially I assumed it would be easiest to debug the application with some text on screen, but React Native allows you to debug on your computer.

Shake your device to bring up the developer menu and select remote debugging to use the chrome developer tools. For other debugging options check out [here.](https://facebook.github.io/react-native/docs/debugging)

## First thoughts

React Native has massively impressed me. I've not gone deep in to it yet, I've not had to drop down in native code or anything, but if I needed to make a mobile application this would defintely be my starting point now.

My next big challenge though is to come up with an app idea to make my millions!