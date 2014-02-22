---
layout: post
title:  "Returning a default with generics"
comments: true
categories: [asp.net,C#,c#,default,generics]
---

Today I was working on a generic method which gets a querystring and converts it. If the querystring exists, it would convert the type and return it. However, I'd also need to return a default if the querystring doesn't exist. As it was a generic method, I couldn't rely on just returning a null as if the type was an integer, this wouldn't work (assuming not a nullable integer).

I disovered this nifty little method though:
return default(T);

Lovely, it will then respond appropriately, if an integer, it would return a 0, if a string, a null.
