---
layout: post
title:  "Cookie Versioning"
comments: true
categories: [Back end,Cookies]
---

Working on some major sites in the past. I have noticed one thing a lot of devs (including me) don't do. Version cookies. We are taught as developers that code changes and we must make sure our code is easily maintainable because of that. Cookies tend to be forgotten though.

Take this example: We have a simple login for a site. When the user is logged in, some details like name are stored in the cookie and retrieved by the site. The client comes along and says "I want the user to also have their t-shirt size persisted in the cookie". So we dutifully add this detail to the cookie. No issue there, we login to test and it works! The cookie is read and their correct t-shirt sizes are displayed. However, we don't notice other users on the site might already have the old cookie and don't log in again. They may well get an error as we expect the cookie to have the t-shirt size.

The solution is very easy though, you've probably guessed it already. If you have a key in your cookie called version and its value of 1 or whatever you want. If there is a change, we can then change the version to 2 in our configuration file. When a user's cookie is read, we can then do a simple compare on the server, if they have a different cookie version or one which is less than the latest, we can delete the cookie, so they have to log in again, or just update it with the new details, or whatever behaviour you want your app to do as a reaction. This makes for a stronger cookie reading process.

Of course, this is an example, you'd probably have the user's shirt size in the database and retrieve it with a call when the user logs in. But cookies can change with data. Sometimes, it is best to be ready for that from the start so you can be sure the user doesn't get an error.
