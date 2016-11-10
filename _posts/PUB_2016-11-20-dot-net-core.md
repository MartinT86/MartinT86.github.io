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
C# application on Linux!

Download and install instructions for your chosen platform are available [here.](https://www.microsoft.com/net/core)

I purposefully avoided the Windows installation with Visual Studio as I was keen to try it with just a 
text editor. Visual Studio is great and I love it, but I do find it can feel slow and clunky, especially on older laptops.

## Basic set up

After installation you can have a .NET application running in just 5 lines.
   
    mkdir hwapp
    cd hwapp
    dotnet new
    dotnet restore
    dotnet run    

## MVC

With ASP.NET Core being pretty different from what I'm used to I wanted to hold on to something I knew so I set out to build an MVC site with it.

Overall, things went pretty smoothly but there were definitely some head banging moments. Mainly these caused by the [documentation](https://docs.asp.net/en/latest/) being so bad. Maybe I just need to get my head around Core more first but I didn't find them very useful at all. They spend a lot of time explaining the concepts and patterns behing MVC itself rather than how to set up a site in Core.

The tutorials weren't a great deal of help either as they wanted you to use the Visual Studio templates. Something I was avoiding as I wanted to get it working with the minimal amount of boilerplate/templating I could.

### controllers

After running the initializer, a controller was my first step.

So I added my folder and my controller class, used the new Microsoft.AspNetCore.Mvc reference and unsurprisingly it didn't work.
Rather than a nice tutorial to use I had to bounce about the docs for a while.

A couple of things are needed to get the controller to work.

### Startup.cs

In an ASP.NET Core program you can use an optional startup configuration file.

Along with the Configuration method required in a startup class, you also can have an optional ConfigureServices method.
This takes an IServiceCollection, and its on here that you need to enable MVC by calling AddMvc().

It's also in the startup class that you can define your routes for your MVC site.
I decided to go for this option;

    app.UseMvc(routes =>
            {
                routes.MapRoute("default", "{controller=Home}/{action=Index}/{id?}");
            });

but you also have the option of using attribute based routing;



not working to start with
need configure services method
need app.usemvc

        "Microsoft.AspNetCore.Mvc": "1.0.1",
        "Microsoft.Extensions.DependencyInjection": "1.0.0",
        
        
### views
not working to start with

?
"Microsoft.AspNetCore.Mvc.Razor": "1.0.1",
        "Microsoft.AspNetCore.StaticFiles": "1.0.0",

                .UseContentRoot(Directory.GetCurrentDirectory())

                app.UseStaticFiles();



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

## logging

## next steps

tdd
deployment
