---
layout: post
title:  "Setting up Sitecore on Amazon RDS"
comments: true
categories: [amazon,Amazon Web Services,asp.net,CMS,Database,rds,relational database service,Sitecore,Sitecore]
---

This week I have had a bit of a nightmare setting up a client's site using Amazon's Relational Database Service (RDS). The issue arises because you can't just restore a .bak file on RDS as there is no access to the service's file system. I read a blog post here: http://blog.xcentium.com/2012/06/how-to-install-sitecore-on-aws-using-amazon-rds/. This didn't really fix any issues and caused errors. I tried scripting the database and it's data which kind of worked, but caused some data to not work properly, mainly the membership provider.

I looked into Red Gate's SQL Packager and realised it creates a .net executeable of the full database. Originally I rejected this thinking it would need access to the RDS file system again. How wrong I was. You can just run it and connect to the RDS instance and away it goes. If you're working on RDS at all with Sitecore, this is a really useful tool.
