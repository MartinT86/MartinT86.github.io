---
layout: post
title: "JS - scope chains and closures"
description: "My solutions to Nodeschool's scope chains and closures lesson"
tags: [Javascript, Nodeschool]
---

As I'm trying to improve my Javscript knowledge I've started working my way through [Nodeschool's
Workshoppers](http://nodeschool.io/). If you haven't come across the Workshoppers before, they are brilliant. They are self 
contained Javascript (among other things) lessons that come in the form of a Node module. If you are 
anything like me, actually doing, really helps to make the lessons sink in rather than just reading.

For example, run the below commands and you are up and running;

    npm install -g scope-chains-closures
    scope-chains-closures

<figure>
	<img src="{{ site.url }}/images/scope-chains.png" alt="Scope chains">
</figure>

## Lesson 1 - Scopes
So a pretty straight forward one here, setting a variable within the scope of a function. 
However, one of the things I liked about this module is that they also give information as well as 
set the challenge for the lesson.

So it was nice to learn that scoping with a function is actually called lexical scoping. Also, that 
ES6 has block scoping but you use "let" rather than "var".

### Solution
    function foo(){
        var bar = 1;
    }

## Lesson 2 - Scope Chains
Here we are looking at how scopes can be nested and that a variable from an inner scope will have access
to an outer scope but not vice versa.

### Solution
    function foo(){
        var bar = 1;
        function zip(){
            var quux;
        }
    }

## Lesson 3 - Global Scope
It was interesting to see how forgetting to declare a variable with "var" would create that variable
globally. With my background in C#, this seemed pretty strange to me and will be something to be 
careful of.

### Solution
    function foo(){
        var bar = 1;
        function zip(){
            var quux = 1;z
        }
        quux = 2;    
    }
    
## Lesson 4 - Closures
Closures are a term that I have heard of before in Javascript but never really known what they are, so
it was nice to find what they actually were.

When an inner function references a variable from up the scope chain, its closes over it and is a closure.
The closure and the variable are maintained even if the inner function isn't called immediately,
 and the function can be passed around.
 
### Solution

    function foo(){
        var bar = 1;
        quux = 2;    
        
        function zip(){
            var quux = 1;
            bar = true;
        }
        
        return zip;
    }

## Lesson 5 - Garbage Collection
Obviously Chrome dev tools is something I use all the time, but this lesson showed me tools in there
that I haven't used before. Recording the memory profile on the timeline tab to see where garbage
collection took place was very interesting.
Its always useful to have another technique to help analyse site performance.

If you want to get my solutions to ths Node School module, you can get them from my [repository here](https://github.com/MartinT86/nodeschool_scopes-chains-closures).