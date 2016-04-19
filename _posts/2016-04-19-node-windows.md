---
layout: post
title: "node-windows"
description: "A great node package for setting up Windows services"
tags: [Node.JS, Javascript, Services]
---

Using node-windows was the first time I've tried to setup a Node application as a Windows
service and I couldn't believe how simple it was.

I needed to serve up a static html file, so installing and configuring IIS seemed like overkill.
So for in order to get the file served as quickly as possible I made a very basic express.js app.

## Setting up the express app

To initially set up the app and create the package.json I ran the below command and taking all of the defaults apart fron the entry point which 
I set to app.js

    npm init

Once the package.json file is in place from running npm init, then I installed express itself.

    npm install express --save

The app.js file itself was extremely basic. Listen on a port and just return the html file.

    var express = require('express');
    var app = express();
    var path    = require("path");

    app.get('/', function (req, res) {
    res.sendFile(path.join(__dirname+'/index.html'));
    });

    app.listen(3000, function () {
    console.log('Example app listening on port 3000!');
    });

To make the app accessible I just needed to add a new firewall rule in for the port it was listening on.

## Adding the app as a Windows service

Initially I ran the express app from the command line with 

    node app.js
    
Which worked great initially, however, unsurprisingly it wasn't long until someone else logged on to the
server and thought "I wonder why this command prompt is open, lets close it".

I was told about [node-windows](https://www.npmjs.com/package/node-windows) and thought I'd give it
a go. 

First job was to install node-windows globally

    npm install -g node-windows

Then at my project root

    npm link node-windows

Finally, I ran the below script taken from the docs with updating the path to app.js

    var Service = require('node-windows').Service;
    
    // Create a new service object 
    var svc = new Service({
        name:'Hello World',
        description: 'The nodejs.org example web server.',
        script: 'C:\\MyApp\\app.js'
    });
    
    // Listen for the "install" event, which indicates the 
    // process is available as a service. 
    svc.on('install',function(){
        svc.start();
    });
    
    svc.install();
    
and that was it! The express app was then accessible without having to run the app via the command
line.

So this was just the basic setup of node-windows but it does have other features that are pretty cool.
These include uninstalling services, killing processes by their PID and a clever wrapper 
around the node app for handling if the app crashes and needs restarting.