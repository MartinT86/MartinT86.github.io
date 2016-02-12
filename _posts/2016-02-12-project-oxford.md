---
layout: post
title: "Project Oxford Example"
description: "My simple web page showing how easy Project Oxford is to use"
tags: [Microsoft, Project Oxford]
---

<figure>
	<a href="https://www.projectoxford.ai/"><img src="{{ site.url }}/images/projectoxford.png" alt="Project Oxford"></a>
</figure>

Project Oxford is a collection of really cool APIs that Microsoft have been working on and expanding.

They include APIs that cover all sorts of facial recognition, image evaluation and speech tools.
Its pretty impressive stuff, they can tell what an image is of, read somebody's emotions, process natural language and more.

All the [documentation](https://www.projectoxford.ai/doc) is straight forward and they have generous
free tiers for most of the APIs with limits of 5,000 calls or more a month.

You can check out just how easy it is to make use of these APIs in my [sample project](https://github.com/MartinT86/oxford-example).
Its just a simple Express app using ajax to make the calls. Its nice to see that Microsoft haven't restricted use of them
to just Nuget and C#. My example makes use of the Face API and the Emotion API to get gender, age and emotion levels from
a photo of a face.

There is an [app gallery](https://www.projectoxford.ai/appgallery) showing off some of the cool stuff that can be done with the 
collection of APIs. Annoyingly though, when I wanted to get one for my Windows phone the app only works on Android!