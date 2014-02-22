---
layout: post
title:  "ORA-28001: the password has expired"
comments: true
categories: [Database,Oracle,Password,Sitecore]
---

Recently, I have been working with a client who uses Oracle as their database. We have been running Sitecore from this and it works ok, bar a few bugs.

However, one day, without warning, we started getting the following error:
ORA-28001: the password has expired

Great. After some searching, we realised it is easily fixable. You need to get into the server and open SQLPlus, Oracle's command line tool.

Type in the user and password. You will then get an error that your password has expired. It should then start the process to change it. You can use the old password (depending on settings) or type a new one.
