---
layout: post
title:  "MS package and deploy"
comments: true
categories: [asp.net,Deploy,deploy,IIS,msbuild]
---

I've been looking into better ways of deploying recently. Microsoft have released their deploy tool which seems very capable, but it is quite tricky (mainly as it is a product which needs to cater for all types of environment setup within .net). It's very simple to set up within [Visual Studio 2010 once you have set up IIS](http://weblogs.asp.net/scottgu/archive/2010/09/13/automating-deployment-with-microsoft-web-deploy.aspx).

All I need to do is run a package and push it to my server using MS Deploy. Once I have the commands I can easily add to my nant build script and then run a package and deploy from my build server ([Bamboo](http://www.atlassian.com/software/bamboo/)) or, even better, use the [Jira](http://www.atlassian.com/software/jira/) deploy integration with Bamboo and deploy from there. Well, let's not go too crazy with that, that's a whole other post right there. Let's jump into some commands.

If I change directory (cd) to the site I want to deploy, go to the site project (I usually call this [projectname].Site mimicking my work's standard). Once there, I just build my site project with msbuild:
[path to msbuild, usually C:WindowsMicrosoft.NETFramework64v4.0.30319]msbuild.exe "MyProject.Site.csproj" /T:Package /P:Configuration=Release /P:PackageLocation="D:ProjectsDeploymentMyProject.zip"

Let's run through this. I execute msbuild pointing to my csproj (or vbproj if you are that way incline) file for the site I want to deploy. The /T:Package makes sure I am packaging that project, I set the /P:Configuration to release so it will take my relevant web.config transform and build in the correct way. PackageLocation says where to put my package as a zip.

So that's the package done. I hope you're with me so far. Next is the push to server. If you have read Scott Gu's post linked to above, it shows you how to set up IIS to accept this type of deploy. Then you just need to change directory (cd) to where your package is built, it will have also added a few extra files, the one we want is MyProject.deploy.cmd. It's just a command line template to run for this project. Run this:

MyProject.deploy.cmd /y /M:https://WebDeployUrl:8172/MsDeploy.axd /u:username /p:password –allowUntrusted /A:basic

fill in the server URL and username and password depending on your setup, and BAM! Project deployed. This can also be set up for an SSL connection. This is a simple view of how to do this, and it can be customised well so you can add to build servers, version etc.
