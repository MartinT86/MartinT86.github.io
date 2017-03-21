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
By swapping the Z and Y, the phone at rest is flat rather than upright. After having a few people test my app, they
said that this felt much more natural.

## FixedUpdate()

I put the code for the movement in FixedUpdate() over Update() so the calculation would be handled before each frame is rendered.

## Rigid Body

To make the movement look more natural, I applied the movement as force rather than just moving the position of my object.

To do this, I added a rigid body component to my object.

    rb = GetComponent<Rigidbody>();
    
The above will get the rigid body from your game object and this be assigned to a private variable.
Then to apply the movement;

    rb.AddForce(movement * speed);

## Change to dynamic collider

During testing my app, my objects would sometimes fly through the other box colliders in the scene.

!!!!!!!!!!!!!!!!get the info of the collider change

## The code in use

Here is my code in action!

!!!!!!!!!!!!!!!!!!!screen shot of game!!!!!!!!!!!!!!!

You can get my first Unity app in the Google Play store from [here](https://play.google.com/store/apps/details?id=com.MTDevelopment.DiceShaker)
