---
layout: post
title: "SQL LocalDB to Azure"
description: "This is the easist way I could find to move a LocalDB SQL database to Azure"
tags: [SQL, LocalDB, Azure]
---

Recently I tried migrating a SQL Server LocalDB to Azure and found what I thought would be an easy job, to actually be
a bit pf a pain.

I'm not saying this is the best way to get a LocalDB live on Azure but below is the easiest way I could find, if anyone knows a better way, please feel free to let me know.

## Why LocalDB

Usually I would never choose to develop against a LocalDB database but I had started my site with a Visual Studio 
template MVC site and thats what it gave me.

## Moving to Azure

Now this is what I thought would be the easy bit. My local prototpye had gone well, so lets get this bad boy live!
LocalDB is just a mdf and a ldf file like any SQL database, so I didn't foresee any issues.

## Azure

!!!!!!!!!!!!!Azure DB Image

So the only way I could find in Azure to upload an existing database was to use a .bacpac file. I couldn't tell you 
the technical differences between a .bak file and .bacpac but Azure was asking for a .bacpac so that's what I was after.

## SQL Server Management Studio

I couldn't figure out a way of getting the .bacpac file directly from LocalDB or from within Visual Studio.
The easiest way I could think of was to attach the mdf file to a local of instance of SQL Server. The fact that I didn't have
a local instance and had to set one up was a bit annoying.

!!!!!!!!!!!!!!attach db image
