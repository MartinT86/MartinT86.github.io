---
layout: post
title: "ASP.Net Core Azure"
description: "Deploying an ASP.Net MVC app to Azure Web App"
tags: [ASP.Net Core, Azure]
---

I'm a big fan of Azure and the Web Apps especially. I know how easy it is to deploy an ASP.Net or Node app.
I assumed that deploying an ASP.Net Core app would be as easy, turns out I was wrong.

There are a few steps to complete before the app will work in Azure.

## global.json

Firstly you need to set the SDK version in the global.json file, so your local version will match the one
being used in Azure.

    {
        "projects": [
            "src",
            "test"
        ],
        "sdk": {
            "version": "1.0.0-preview2-1-003177"
        }
    }
    
You can get your local dotnet version by;

    dotnet --version
    
Thanks to [Scott Hanselman](http://www.hanselman.com/blog/PublishingASPNETCore11ApplicationsToAzureUsingGitDeploy.aspx) for getting me over the first hurdle.
