---
layout: post
title: "Manifold JS"
description: "Creating hosted web apps with Manifold JS"
tags: [Manifold JS, Hosted Web Apps, Android]
---

I thought I'd give Manifold JS a try and create a hosted web app for Android

## Manifold JS

[Manifold JS](http://manifoldjs.com/) is a node application that will package up a website like a native app.

You can get it from NPM or you can use thr package generator from their site. I decided to go down the package 
generator route as it will create the W3C manifest and give you any warnings that you may have for your target 
device.

## Android Asset Studio

I'm not a designer, so one thing I found massively useful in getting my website ready to be an app was
[Android Asset Studio](https://romannurik.github.io/AndroidAssetStudio/icons-launcher.html).
It's a really quick and easy way to create the icons in the needed sizes for the Google Play store.

## Android Studio

Once you have completed the package creation and download from Manifold JS there will be a Gradle file under 
the Android folder.

You'll need to install the Java SDK and Android Studio. Using Android Studio and APK will need to be generated.
Luckily you don't really need to know how to use Android Studio (as I dont...yet).

Import the Gradle file, then under the build menu select Generate Signed APK. It has to be a signed APK in  
order to be uploaded to the Google Play Developer Console.

!!!!!!!!!!!!!!!!!!!!!!build image here

## Google Play Developer Console
