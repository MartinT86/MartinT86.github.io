---
layout: post
title: "ASP.NET Core MVC"
description: "My further look at MVC in ASP.NET Core"
tags: [.NET Core, ASP.NET Core, MVC]
---

After setting up my first ASP.NET Core MVC site I've looked in to expanding it with a test project
and taking advantage of more new features.

## Test project

One of the first things I wanted to learn how to do in ASP.NET Core was how to 
get some unit testing going.

Firstly I set up the solution structure by creating a source directory and a seperate test directory.
At the root of the solution I added a global.json file.

    {
        "projects": [
            "src",
            "test"
        ]
    }

In the test directory, to create the test project, there is a very helpful dotnet command.

    dotnet new -t xunittest

This is a very helpful option to the new command. In the project.json file it sets the testrunner
to xunit and the needed dependencies.

I've not used xunit before, but apart from a few syntax differences to nunit, it seems pretty
straightforward.

For a mocking framework I went with Moq. It's not my first choice, but I read it worked with 
ASP.NET Core so I went for it. 

Once all the tests are in place, you just need to run the following command in the test project;

    dotnet test

The docs for testing in ASP.NET Core can be found [here](https://docs.microsoft.com/en-us/dotnet/articles/core/testing/unit-testing-with-dotnet-test).

It was a big relief to find that setting up unit testing was straightforward as I'm loving
learning ASP.NET Core and I didn't want it to be a blocker.

## tag helpers

_ViewImports.cshtml
form tag helper

## debuging

attach to process

## static files

need wwwroot folder