---
layout: post
title: "dot net core"
description: "my first intro to dot net core"
tags: [.NET Core]
---

## installing

https://www.microsoft.com/net/core

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


## examples

https://docs.asp.net/en/latest/getting-started.html