---
layout: post
title: "Unity - 2D Velocity"
description: "How to add velocity to a 2D sprite"
tags: [Unity, GameDev]
---

While making my latest game I wanted to move a sprite that was attached to another sprite via a hinge joint. However I realised that just moving the position of the original sprite's transform would make the joint fail.

So here is how I added velocity to the sprite to ensure the hinge joint worked appropriately.

## Add the velocity

I set a Vector3 for where I wanted the sprite to move to then set the velocity on my RigidBody to equal the Vector3 multipled by a speed value.

    Vector3 movement = new Vector3 (-3, 0.0f, 0.0f);
	rigidBody.velocity = movement * speed;

The speed value is a public variable so it can be easily set from the Unity editor.

## Stop the velocity 

Since adding velocity will be using physics within unity, the RigidBody will keep moving even after you stop adding the velocity.

For my game I didn't want to rely on drag to stop my RigidBody, I wanted a more instant stopping.
As such I had to reset the velocity.

    rigidBody.velocity = Vector2.zero;