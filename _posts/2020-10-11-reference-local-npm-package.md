---
layout: post
title: "Local npm package"
description: "Reference local npm packages to help keep feedback loops smaller"
tags: [Node, npm]
---

A small blog post just to serve as a reminder for myself (or anybody else) on how to reference local npm packages to help keep feedback loops small during development.

## Why

I'm not the most patient person in the world, so anything that lengthens feedback loops I find a real pain.

Recently I was making an npm package and I wanted to be able test it as I went along. Especially as the package wasn't ready to be deployed to npm. So I wanted to be able to reference the package locally.

## How

To reference the local package, all you need to do is to add it to your list of dependencies with the following syntax. Making sure that the file path is the package.json of the package you want to import.

```
"dependencies": {
    "packagea": "file://../packageA"
}
```

After running npm install, you can the require/import your local package just like you would with a published package.


