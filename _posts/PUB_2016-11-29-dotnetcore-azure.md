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

## Configuring your app to run in IIS

For your app to work in Azure, you need to configure it to with IIS and there are a few steps to this.
The detail on them can be found [here](https://docs.microsoft.com/en-us/aspnet/core/publishing/iis)

### project.json

Microsoft.AspNetCore.Server.IISIntegration needs adding as a dependency in project.json.

There are a few additions needed to the file as well.

    "tools": {
      "Microsoft.AspNetCore.Server.IISIntegration.Tools": "1.1.0-preview4-final"
    }

    "scripts": {
      "postpublish": "dotnet publish-iis --publish-folder %publish:OutputPath% --framework %publish:FullTargetFramework%"
    }

Any files that will need to be deployed with your app, such as the now required web.config will need to go in the 
publishing options. The publishOptions docs are [here](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/project-json#publishoptions)

    "publishOptions": {
        "include": ["wwwroot", "Views"],
        "includeFiles":["web.config"]
    }

### web.config

Now we are setting the app up to run in IIS we will need a web.config.
This is my basic web.config, just the processPath dll will need to be updated;

    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <system.webServer>
        <handlers>
          <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />
        </handlers>
        <aspNetCore processPath=".\Site.dll" arguments="" forwardWindowsAuthToken="false" stdoutLogEnabled="true" stdoutLogFile="\\?\%home%\LogFiles\stdout" />
      </system.webServer>
    </configuration>

### WebHostBuilder

In the webHostBuilder in Program.cs you need to call .UseIISIntegration()

    var host = new WebHostBuilder()
        .UseKestrel()
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

## Troubleshooting Azure

There was a lot of hair pulling to get this up and running, but on the bright side it was good practice trouble shooting Azure.

### 
