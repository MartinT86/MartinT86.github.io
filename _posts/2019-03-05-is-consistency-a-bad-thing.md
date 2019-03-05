---
layout: post
title: "Is consistency a bad thing?"
description: "Is consistency always something to aim for in a codebase?"
tags: [Code smells, Clean code]
---

Like most developers I've met, I've always believed consistency in code to be a good thing.

Recently though I've been starting to question if consistency is always a good thing.

## What do I mean by consistency?

Consistency can be applied to many areas within a codebase. You can have consistent naming strategies, formatting rules, and code design patterns to name just a few.

When it comes to formatting, people can often have very strongly held views. Tabs Vs spaces, do braces for a function start with a new line, should you end a line with a semicolon, and so on.

If you are spending time thinking about formatting consistencies you are a very lucky developer. If those are your biggest issues, you've done a great job, go ahead and take the rest of the day off. Unless these formatting inconsistencies are stopping the code from compiling or causing massive readability issues, I wouldn't really worry about them. Or better yet, have the conversation once and stick a linter in your project.

The other main area I've seen discussed when it comes to consistency is the patterns within the application logic. For example, how the data access objects are structured or how a request is parsed into the application domain.

## Good points for consistency

Now don't get me wrong, consistency can be very helpful.

One of the main aims I hear for consistency is making it easier for other developers to understand how the code works across the application. This is a strong point for consistency. It's rare a single developer will be working on an application, so making things easy for your teammates is pretty important.

“Indeed, the ratio of time spent reading versus writing is well over 10 to 1. We are constantly reading old code as part of the effort to write new code. ...[Therefore,] making it easy to read makes it easier to write” (Robert c Martin, Clean Code)

Keeping a codebase readable should be one of the main aims of a developer. One of the worst things a developer can do is to reduce the readability of code. By giving patterns to recognise, code readability can be another benefit of sticking to consistent patterns. 


## Bad points for consistency

It's clear that consistency can be very helpful, but recently I've been thinking it might be a bit of a code smell. So rather than just sticking with consistency for consistency's sake, maybe think about some of the following points as well.

#### Inertia

I've seen consistency become a real blocker when it comes to refactoring. When you have the same pattern in many places throughout a codebase, when you see a refactoring you want to implement, having to do that refactoring in many places can be time consuming. Sometimes to the point where the benefits of the refactoring are outweighed by the time to implement it.

Communication can help here. Maybe you don't need to refactor every single instance of a pattern. Try refactoring the one instance you originally wanted to, but make sure you communicate with the team that you have done this.

Big refactorings scare me. It's too easy for them to turn in to a thread that just won't stop unraveling. I think the boy scout role is much more effective. Every time you touch code, leave it in a better state than you found it. Even if that's just renaming one variable, the codebase will quickly start to look great. But I find the need for consistency at odds with this approach. It's easy to feel, “I can't just update this, it won't be consistent with the rest of the application”. This can lead to just keeping the status quo.

The inertia of trying to make big changes is much greater than if you are making many small ones.

#### Highlighting duplication

If the consistency you are trying to protect is something like a design pattern, then maybe this is a sign of duplication of logic. The fact that there are multiple things done in a consistent way may mean there is a possibility for a cleaner more general implementation that you could be using.

#### Unit testing

If your unit tests are a mirror of your code then consistency can mean you have to update all your tests every time you refactor your code. However, your tests shouldn't be a mirror of your code. The test suite should be a collection of the units of work. If you have to update all your tests every time you refactor, these are likely to be implementation tests rather than unit tests.

#### Making it easier for others

I've seen “making it easier for new team members to navigate around the codebase” be a reason why consistency is important. However, if consistency is the enabling factor for navigation, perhaps that is a signal that the code could be cleaner anyway. 

By following Uncle Bob's techniques for clean code, such as naming things clearly and many small functions that do one thing, the code could be easier to navigate. I would rather find my way around a code base that “reads like well written prose” (Grady Booch) rather than relying on spotting a duplicated pattern.

## Conclusion

I'm not saying consistency is a bad thing or that it should be avoided. But if you are ever tempted not to refactor code to preserve consistency, I would be on the lookout for other code smells such as duplication, code that could be cleaner, or unit tests that are too closely coupled to the implementation.
