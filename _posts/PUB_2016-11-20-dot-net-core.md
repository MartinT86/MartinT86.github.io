---
layout: post
title: "ASP.NET Core MVC"
description: "My first look at MVC in ASP.NET Core"
tags: [.NET Core, ASP.NET Core, MVC]
---

I've heard a lot of good things about ASP.NET Core so I thought I'd check it out.
It feels very different to the Microsoft development I'm used to, but after a bit of learning curve
it seems pretty good.

## Why ASP.NET Core?

Rather than just bringing out a new version of ASP.NET with version 5, Microsoft decided to 
give us ASP.NET Core 1.0.

So far it seems pretty cool and addresses some of the issues with good old Microsoft development.

Microsoft can describe it better than I can; so here it is.

> ASP.NET Core is a new open-source and cross-platform framework for building modern cloud based internet connected applications, such as web apps, IoT apps and mobile backends.

> ASP.NET Core has a number of architectural changes that result in a much leaner and modular framework. ASP.NET Core is no longer based on System.Web.dll. It is based on a set of granular and well factored NuGet packages. This allows you to optimize your app to include just the NuGet packages you need. The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.
According to Microsoft, there a lot benefits from moving to the new framework.

[ASP.NET Core Introduction](https://docs.asp.net/en/latest/intro.html)

Some of the main benefits that made me want to try out include;

* Lightweight, modular system
* Cross platform (yes, that's right, it runs on Linux and Mac!)
* Use a text editor rather than Visual Studio
* Open source

## Installing

As I've mentioned, one of the most exciting things about ASP.NET Core is that it is cross platform.

It can run on Windows, Mac, Docker and various Linux platforms. My mind was blown when I ran my first 
C# app on Linux!

Download and install instructions for your chosen platform are available [here.](https://www.microsoft.com/net/core)

I purposefully avoided the Windows installation with Visual Studio as I was keen to try it with just a 
text editor. Visual Studio is great and I love it, but I do find 

## basic set up

https://www.microsoft.com/net/core#ubuntu

## mvc

### views
not working to start with

?
"Microsoft.AspNetCore.Mvc.Razor": "1.0.1",
        "Microsoft.AspNetCore.StaticFiles": "1.0.0",

                .UseContentRoot(Directory.GetCurrentDirectory())

                app.UseStaticFiles();

### controllers
not working to start with
need configure services method
need app.usemvc

        "Microsoft.AspNetCore.Mvc": "1.0.1",
        "Microsoft.Extensions.DependencyInjection": "1.0.0",

### models

referencing model in Razor
using a service with DependencyInjection

### vscode refactoring

eg. implement interface
ctor
rename = f2 (not effect views)
remove unused usings

## examples

https://docs.asp.net/en/latest/getting-started.html

## next steps

tdd
deployment