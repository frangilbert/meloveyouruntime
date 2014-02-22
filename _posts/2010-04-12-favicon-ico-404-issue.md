---
layout: post
title:  "Favicon.ico 404 issue"
comments: true
categories: [asp.net,favicon]
---

So, sometimes you will find that browsers look for the favicon.ico file at the root of your site. A lot of the time you haven't yet/won't add one of these. As the browser looks for this, it can cause a 404 error in asp.net MVC. It can be made to ignore this file by adding the following code to the global.asax route index.

routes.IgnoreRoute("{*favicon}", new { favicon = @"(.*/)?favicon.ico(/.*)?" });

Thanks to [Phil Haack](http://haacked.com/) for that nugget.
