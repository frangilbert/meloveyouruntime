---
layout: post
title:  "Static Content in IIS7"
comments: true
categories: [asp.net,IIS,IIS,Static Content]
---

Everytime I start a new server install on IIS7 I forget one thing, I install IIS and its management console and also .net 3.5 and 4.0, but always forget to check that Static Content is checked.

This means that when I start my site, it generally works straight away, but no images or CSS or even javascript are shown, when I look at the response for these items, I get a 200, but the content is empty.

To rectify, just go to your server and in your Server Manager within the Roles area, in Role Services, select Static Content under the Common HTTP Features category and try again.

![](http://meloveyouruntime.wordpress.com/wp-content/uploads/2011/04/static_content.gif)
