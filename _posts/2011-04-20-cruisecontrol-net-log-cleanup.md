---
layout: post
title:  "CruiseControl.net Log Cleanup"
comments: true
categories: [Build servers,CruiseControl.net,Cruisecontrol.net]
---

I've recently got well into CruiseControl.net. Having a server building, testing and even packaging for you is, well, brilliant for so may reasons which I will not get into here.

However, at my current work, we constantly use up space with log files, every build builds a log file, and as we have a huge amount of code to compile, it gets messy quickly. Gigs of files which we will only use the last 10 of at the most.

One dev wrote a Powershell script which just scans the logs folders and deletes any logs older than a certain date. Pretty good, but I realised there is a cleaner built in to Cruisecontrol.net already called Artifact Cleanup Publisher (added in version 1.6).

You just add the following in your publishers area for projects in your Cruisecontrol config file:

```
<artifactcleanup cleanUpMethod="KeepLastXBuilds" cleanUpValue="50" />
```

Let's put that in the context of a project:

```
<publishers>
   <xmllogger/>
   <artifactcleanup cleanUpMethod="KeepLastXBuilds" cleanUpValue="10" />
</publishers>
```

This will then only keep the last 10 logs, you can also cleanup by file age. You can read more here:
[http://build.nauck-it.de/doc/CCNET/Artifact%20Cleanup%20Publisher.html](http://build.nauck-it.de/doc/CCNET/Artifact%20Cleanup%20Publisher.html)
