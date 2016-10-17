---
layout: post
title: "Razor View Interfaces"
description: "Using interfaces for razor view models to make your views more flexible"
tags: [Razor, MVC, NancyFx, Atomic Design]
---

By using interfaces rather than classes for Razor models you can decouple them and make them more flexible.

## Atomic Design

After reading [Brad Frost's awesome blog post on atomic design](http://bradfrost.com/blog/post/atomic-web-design/) 
I got to thinking how a similar approach could be taken with Razor views.

Here is a very brief introduction to some concepts from Atomic Design.

Atomic Design is based around creating design systems from reusable and composable parts.
These are split in to five sections.

#### Atoms

Atoms are the smallest parts of the system. They can include the styles of a button or heading.

#### Molecules

When you start to gather several Atoms together you end up with a Molecule.
An example would be a site search form. Consisting of an input atom, a label atom and a button atom.
This molecule can then be used in different places on the site.

#### Organisms

Organisms are made by bringing together molecules to form parts of a UI.
For example a navigation molecule and a site search molecule might make up a site's header.

#### Templates

A template is the framework for a page and how it will look when the organisms are arranged.

#### Pages

Once the template is populatd with final content the page is then complete.

I found this concept of breaking down designs brilliant and it really reminded me of the 
Don't Repeat Yourself rule in development.

## Razor views

I started thinking how the principles of Atomic Design could be applied to Razor views.
After some experimenting I realised that you could use an interface as the model for a strongly
typed view. This sounds like a small change but it was news to me and opened up several new possibilities.

#### Reusable Partials

By setting the model for a partial view to be an interface rather than a class they can be more reusable.

Partial view;

    @model ViewInterfaces.Interfaces.ICanRenderTitleSection
    
    <div>
        <h1>@Model.Title</h1>
        <h3>@Model.SubTitle</h3>
    </div>

This partial then can be used by any model that implements that interface.

Calling view;

    @model ViewInterfaces.Models.HomeViewModel
    
    @{
        ViewBag.Title = "Home Page";
    }
    
    @Html.Partial("/Views/Partials/_TitleSection.cshtml", Model)

Since the main view model is implementing all of the small interfaces required for the small partials, 
the partials are easily composable. As with Atomic Design the partials can reflect the organisms, 
molecules and atoms.

Interface;

    namespace ViewInterfaces.Interfaces
    {
        public interface ICanRenderTitleSection
        {
            string Title { get; set; }
            string SubTitle { get; set; }
        }
    }

#### Small Interfaces

It is better to have your main view model to implement many small interfaces rather than one large one 
your model will be more flexible.

By following the Interface Segregation principle from the SOLID principles you are giving clear 
instructions on what partials the model can be used for and showing clear intent.

I've also found that it can help when it comes to using the model in the partial. Any properties on the 
view model that aren't needed for that partial won't be accessible due to using the interface.

## Example

You can check my MVC example on [GitHub](https://github.com/MartinT86/ViewInterfaces)