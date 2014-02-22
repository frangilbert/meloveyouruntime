---
layout: post
title:  "Upgrading Sitecore causes Global.asax to not work"
comments: true
categories: [asp.net,CMS,global.asax,Sitecore,Sitecore,sitecore upgrade,upgrade]
---

AAAAAHHHH! This fix, I hope, will save you a lot of time. Recently we have been upgrading some clients to the latest Sitecore. Generally that works fine, however, on re-compile, then running the application, I get a nasty StructureMap Exception Code: 202 (we use this lovely little nugget for IoC). Panic ensues. You check everything, it's all in place. You check the Global.asax in Visual Studio (where we kick off Structuremap and any application wide methods), it has all the code there. And there's the problem. Visual Studio opens global.asax.cs by default, which is correct really, code should really only be in there. However, if you open the global.asax file in your favourite text editor, you see the issue. Sitecore replaces the global.asax file with a default, which has default, empty code and methods in it! It looks like:

<%@Application Language='C#' Inherits="Sitecore.Web.Application" %>
<script runat="server">
  public void Application_Start() {
  }

  public void Application_End() {
  }

  public void Application_Error(object sender, EventArgs args) {
  }
</script>


What this means is, although Visual Studio sees all your code in global.asax.cs, that code is not running because it isn't even referenced by the global.asax in the first place, it should look something like this instead:
<%@ Application Codebehind="Global.asax.cs" Inherits="YourSiteAssembly.Site.Global" Language="C#" %>

Infuriating? Very! Just keep an eye on that global.asax file! I hope this saves you some time and a lot of pain.
