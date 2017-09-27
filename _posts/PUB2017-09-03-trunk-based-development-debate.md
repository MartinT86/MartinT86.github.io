
---
layout: post
title: "Trunk based development debate"
description: "I recently took part in a debate arguing for trunk based development, here's how it went"
tags: [Source control]
---

Recently I had the opportunity to take part in a debate of trunk based development vs branching. Here's how it went.

## What is trunk based development?

In trunk based development all developers work only from the trunk or master. No branches are created for feature development or releases. You work on master and release from master.

Other factors may influence exactly how this is implemented though. For example, depending on the team size and composition, you may create short lived branches for peer reviews or pull requests. However, it is important that the spirit of trunk based development is still observed and these branches are short lived.

For more information on trunk based development, [here](https://trunkbaseddevelopment.com/) is a great website explaining it in much more detail.

## My arguments for trunk based development

### XP principles

When pulling together my arguments for trunk based development it occured to me that this sort of source control strategy supports several of the XP principles.

### Collective ownership

Since when following trunk based developer every commit should be going to the master branch which in turn will be checked out by every member of the team and break the build for everyone if there is anything wrong, collective ownership sort of just happens. If you eave broken tests, you aren't just effecting yourself, you are effecting the whole team. This quickly promotes car and attention to the work and others in the team.

### Continuous integration

You should set your continuous integration pipeline to be built from commits to the master branch. If these commits are coming from every member of the team and going through continuous integration, you should always be in a position where a release to live is possible.

### Small releases

By working in branches you are working against the principle of small releases. Even if you keep those branches relatively small you are going against the spirit of small releases. If commits need to be gathered together in a branch for something like a feature, then by definition these are bigger releases.

In an ideal world, each commit would be going straight to live through your continuous integration pipeline, in turn ensuring small releases. However, even without automated deployment, avoiding feature branches is a great way to avaoid large releases.

### Sustainable pace

By avoiding the large releases and gaps between deployments, trunk based development can definitely support a sustainable pace of development.

## Conclusion
