---
layout: post
title:  "Exception Development"
comments: true
categories: [development,driven,exception,General]
---

This is more to get into my head than anything. Catching errors and reporting them is a good thing. 'm not talking about try and catch blocks round every part of your code, but rather using HTTP Modules and the Global.asax to catch all errors thrown, and a. sending to a nice designed page and more importantly b. storing the error.

When a site first goes live, you can have added unit tests, tested it through development, sent it off to your testers, but there is always someone out there who types in one character too long and breaks your site, and this is a good thing. Well, a good thing if you store it because you can then see the error that was thrown and fix it.

There is nothing worse than 2 weeks after your site has gone live, finding out that the form didn't post if you typed a hyphen in the text box or something. Well, there are worse things, but it involves pliers and cotton wool.

As a predominantly C# asp.net developer. There are many ways of catching an error. To utilise this, I have used [Elmah](http://code.google.com/p/elmah/), an open source project which just catches errors, well. You don't even need to recompile code generally, and after a little set up in your web.config, you're up and running with a page showing you what errors can in. Then, when your site goes live, you can keep an eye on the stats, or even have each error emailed to you. The user, and your client will thank you, when they realise your site is working (they probably won't, but a working site means no complaints).

Jeff Atwood probably puts it a little better here:
http://www.codinghorror.com/blog/2009/04/exception-driven-development.html
