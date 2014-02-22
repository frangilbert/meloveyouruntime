---
layout: post
title:  "Sitecore desktop freezes"
comments: true
categories: [freeze,Sitecore,Sitecore,sitecore desktop]
---

While working on a site recently, I noticed that trying to get to the Desktop version of Sitecore, it would get stuck just in a request state, nothing happening. This was always after logging in, the Sitecore login page itself worked fine. It would also not log any issues in the log files. The thing that fixed it was to make C:\Windows\Temp a writable folder for the IIS user. Almost immediately it worked. Phew!

I hope this helps :).
