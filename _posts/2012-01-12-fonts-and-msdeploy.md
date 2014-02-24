---
layout: post
title:  "Fonts and MsDeploy"
comments: true
categories: [asp.net,Content,Deploy,Fonts,MSDeploy]
---

While trying to deploy a site this morning using MsDeploy triggered by my build server, most worked well, apart from the fonts I was using being pushed as well. Some fonts are called from the CSS and need to be in there too. These didn't upload with the deploy at all. Well, one did, but I have 4. I realised that each of these files need to be set to be Content in Visual Studio and hey presto, fonts will go in the build. 

![](http://meloveyouruntime.files.wordpress.com/2012/01/vs-properties.gif)

This should work with other files if you're having problems with them not being in the build.
