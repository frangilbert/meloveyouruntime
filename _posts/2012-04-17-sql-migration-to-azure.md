---
layout: post
title:  "SQL Migration to Azure"
comments: true
categories: [Azure,Azure,cloud,hosting,Migration,Platform,SQL Azure,SQL Server,Umbraco]
---

I've been playing about with Azure at work recently to test it out and see if it will work as we need for clients. For the most part it has been blindingly easy to set up. But one thing I had a few issues with was migrating my SQL data to SQL Azure (on the Azure platform there are 2 database types, rather helpfully named Windows Azure - which is a noSQL database and SQL Azure - which is based on SQL server).

As we have developed a site using Umbraco, we wanted to package the database and just restore it on Azure. You can connect to SQL Azure by SQL Server Management Studio (if you do, be sure to install SSMS 2008R2 as 2008 will not work properly) but you can't backup and restore an Azure DB using this method. Enter the [SQL Azure Migration tool](http://sqlazuremw.codeplex.com/), which is very simple to use. You connect to your SQL server, choose your database, then connect to your SQL Azure instance and select which DB you want to restore to. Easy life. One gotcha though: You can only restore SQL server 2008 R2 database. If you try an older DB you will get errors, so try and upgrade before even considering Azure.
