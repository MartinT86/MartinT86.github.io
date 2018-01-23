---
layout: post
title: "Unity - action while button pressed"
description: "How to perform an action while a button is pressed"
tags: [Unity, GameDev]
---

I usually make games to be released on the Andrid platform and my UI usually involves buttons that have to be held down in order for something to happen. For example, the player character should walk forwards while the move button is held down.

Here is how I achieved this through the event trigger system and public methods on my scripts.

## Public methods

Since Unity uses C# as it's scripting language methods can be marked as public or private. In order for something outside of the script to call a method we have to mark the method as public. We do this like below;

    public void DoSomething()
    {
    }

## Using the event trigger system

The way I've been moving my sprites in my games may be to move the position of the transform of the sprite by using methods should as MoveTowards. Such methods will want to be called continuously as the button is pressed. In order to achieve this I create a private boolean field in the script, such as;

    bool moveForward;
    
Then in the FixedUpdate method of the script you can check if the bool is true and if it move your player as desired.

   void FixedUpdate()
   {
     if(moveForward)
     {
       // move player as desired
     }
   }

In order to set the moveForward field to true I use the event trigger system to call a public method on the script. One method for button pressed and one method for button released.

   public void MoveButtonPressed()
   {
     moveForward = true;
   }
   
   public void MoveButtonReleased()
   {
     moveForward = false;
   }

## Adding the instance of the script




