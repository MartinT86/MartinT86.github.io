---
layout: post
title: "My elephant carpaccio workshop"
description: "My heavily modified elephant workshop"
tags: [User Stories]
---

Recently I was fortunate to be able to run a learning session with my team. I decided to run my session
based on the Elephant Carpaccio workshop to see if we could all think more about how user stories can
be effectively split up.

## The original workshop

If you haven't come across the Elephant Carpaccio workshop before it's based on Alistair Cockburn's 
[awesome article](http://alistair.cockburn.us/Elephant+carpaccio) of the same name. It's a great explanation
of the benefits for slicing user stories into the smallest possible size and deliver them incrementally.
I'm a big proponent of small user stories, however reading Cockburn's article again it reminded me that once
the elephant has been sliced as finely as possible, it is important that once the slices are all delivered they
still need to resemeble the elephant.

It's important to note that while stories should be sliced as small as possible, the story should be sliced 
vertically. This means that a story should go through all layers of the infrastructure and still deliver value. 
As such if there are a lot of layers of infrastructure required to deliver a story, then it needs to reduce in size 
horizontally. For example when building a new form, the new page will be needed, any logic for processing the 
form data and storing the data will all be needed. So the first story might be very thin horizontally and only
be for a single field on the form. A lot of value is still gained from such a story as a lot of knowledge will 
be gained. The following story may be the rest of the fields on the form as vertically a lot of the work has already
been done.

In the [original workshop](http://alistair.cockburn.us/Elephant+Carpaccio+exercise) you spend some time deciding on
how best to slice the user stories to deliver a checkout that can calculate total price, discounts and tax 
based on the location. If you ever get the chance to take part in the work shop I definitely recommend having
a go.

<figure class="half">
	<img src="{{ site.url }}/images/elephant-24732_640.png" alt="Elephant">
	<img src="{{ site.url }}/images/carpaccio-643020_640.jpg" alt="Carpaccio">
</figure>

## My version of the workshop

For my session I only had around 30 minutes, so unfortunately I couldn't do the full workshop. I wanted to 
do something that was open to non-developers as well as developers and show the importance of thinner user
stories.

I put together a list of different features for a hypothetical website and asked the group how they thought 
they could best be broken down. I split the group into pairs and they had 3 minutes to decide what work they
thought they could release in a day. At the end of each 3 minutes, I marked off which features, or which parts 
of features they felt they could have released. 

Before the start of the session I assigned each feature a value increase
to over all sales for the hypothetical website, and this sales increase was split over the parts of the feature. 
The first part of each feature
was given greater value. I wanted to show that stories don't necessarily need to be grouped and completed by
feature, but you should target the most valuable stories first.

After several rounds, I added up the overall impact each pair would have made on sales.

## My workshop Rules

### Aim of the game

To increase sales for the website as possible

### Scenario

I'm a widget seller who sells 2 types of widgets. Type A and Type B.
I want to improve my website to sell them more effectively.
Below are the baseline expected sales figures

* Widget A - 50 a day
* Widget B - 100 a day

The checkout is already in place and took 3 days to complete. Please use this a reference
point for the size of implementing new features.

Below are the features that I want my site to have and impact I expect them to have on sales of widgets.
The sales impacts are once a feature is fully implemented, benefits can be gained from partially implemented
features.

* Product information page - 30%
    - Text
    - Image
    - Reviews
    - Related products
* Product gallery - 10%
    - carousel
    - quick view box
* Banner carousel - 10%
    - Overlay text
    - Image cropper so I can put various images in
* FAQ - 20%
    - Customers can ask questions
    - Customers can answer questions
* Store Finder - 5%

## How the sesson went

Overall, I would say that the session turned out to be a success. Everyone seemed to enjoy it and it raised 
some good discussion and thought over how its best to tackle the most valuable stories first, not just 
fully complete a feature.

The group were very helpful and gave me some really constructive feedback for the next time I get to 
run the session. Firstly it was to lower the 3 minute timer for each round, it was too long and it gave 
people time to chat about other things. Also, I had a spreadsheet to calculate the impact on sales each team
was having, however the more astute members of the group were keeping on eye on which features were getting the
other teams a lot of value and going for that themselves. As such, next time after each round I would just show
them the overall results, not how they were calculated.

One thing I did learn to take in to future workshops is that you can really motivate a group of people
by turning a session in to a competition with cookies as the prize.