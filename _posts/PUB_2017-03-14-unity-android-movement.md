---
layout: post
title: "Unity Android Movement"
description: "How to use your phone's movement in Unity"
tags: [Unity, Android]
---

It turns out that using the movement from your phone is pretty easy. Here's how I did it in my first Unity app.

## The code

Traditionally I'm a C# developer so naturally I picked to make my Unity scripts in C#, but you do have the option
of choosing Javascript.

To get the movement from your phone, all you need to do is;

    Vector3 movement = new Vector3(Input.acceleration.x, Input.acceleration.z, Input.acceleration.y);
    
I couldn't believe how easy that was!

All we are doing here is setting a new Vector3 as our movement value with the movement the phone has made.

## Z and Y axis

The Unity reference for Vector3 can be found [here](https://docs.unity3d.com/ScriptReference/Vector3-ctor.html).
Below is the constructor for a Vector3;

    public Vector3(float x, float y, float z);
    
The keen eyed of you will notice that I have my Z and Y values the wrong way around.    



## Script


## Rigid Body


## The code in use
