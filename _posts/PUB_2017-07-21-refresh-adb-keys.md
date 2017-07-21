---
layout: post
title: "Refresh Android Debug Bridge Keys"
description: "Here is how I refreshed my adb keys to solve adb not authorising the phone"
tags: [adb, Android]
---

I'm not an expert about the Android Debug Bridge (adb) at all, however this issues cost me a couple of hours to resove the other day so I thought I would write this to remind myself if it happens again.

## What is adb




## What was my problem

When trying to attach a phone to debug via USB I wasn't getting the prompt to rust the computer's RSA key fingerprint.
This meant that the device was not being authorized in adb. As such, debugging and running Espresso tests was impossible.

After trying the usual switch things off and on again and trying a different wire I was still having no luck.

## How I fixed it

!!!!!
location of adb key files
mac + windows
~/.android/adbkey
~/.android/adbkey.pub

How to call the adb commands

delete old keys
adb kill-server
adb devices
