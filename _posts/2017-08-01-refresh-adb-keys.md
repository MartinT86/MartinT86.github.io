---
layout: post
title: "Refresh Android Debug Bridge Keys"
description: "Here is how I refreshed my adb keys to solve adb not authorising the phone"
tags: [adb, Android]
---

I'm not an expert about the Android Debug Bridge (adb) at all, however this issue cost me a couple of hours to resove the other day so I thought I would write this to remind myself if it happens again.

<div class="center">
<figure>
	<a href="{{ site.url }}/images/rsa_android.png"><img src="{{ site.url }}/images/rsa_android.png" alt="rsa key fingerprint"></a>
	<figcaption>RSA key fingerprint</figcaption>
</figure>
</div>

## What is adb

The Android Debug Bridge is a command line tool that lets you interact with both virtual and physical android devices.

For example you can press the power button on the device via the command line.

For more information on adb, check out the Android [docs](https://developer.android.com/studio/command-line/adb.html).

## What was my problem

When trying to attach a phone to debug via USB I wasn't getting the prompt to trust the computer's RSA key fingerprint.
This meant that the device was not being authorized in adb. As such, debugging and running Espresso tests was impossible.

After trying the usual switch things off and on again and trying a different wire I was still having no luck.

## How I fixed it

I read that if the RSA key for adb is not correct then the device will not be able to trust the 
computer and won't connect.

Regenerating the keys is easy by following the following steps

### Delete the old keys

For Macs the keys are found in;

    ~/.android/adbkey
    ~/.android/adbkey.pub

On Windows they are found;

    C:\Users\{username}\.android\adbkey
    C:\Users\{username}\.android\adbkey.pub

### Call the adb commands

If you don't have adb added to your path, you will need to call adb from the right 
location;

For Macs;

    ~/Library/Android/sdk/platform-tools

For Windows;

    C:\Users\{username}\AppData\Local\Android\sdk\platform-tools

Once the keys are deleted, calling the below commands will stop the adb server, restart it, and 
regenerate the keys.

    adb kill-server
    adb devices
