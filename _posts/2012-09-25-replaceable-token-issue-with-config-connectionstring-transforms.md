---
layout: post
title:  "Replaceable token issue with config ConnectionString transforms"
comments: true
categories: [asp.net,C#,config,Deploy,msbuild,transforms]
---

I ran into a little conundrum the other day trying to make a .net C# project build and deploy. I was making a build using MSBuild which also transforms config files. This was all working, but in the config's ConnectionStrings element, the transform was coming out with:
<add name="Connection" connectionString="$(ReplacableToken_ProjectName-Web.config Connection String_0)" providerName="System.Data.SqlClient" />

Now, I thought that $(ReplacableToken_ part would be properly transformed for the relevant environment like:
<add name="Connection" connectionString="[LiveDB connectionstring]" providerName="System.Data.SqlClient" />

The issue is that MSBuild actually does this on deploy, not on build. It's a feature. On build, it just creates a placeholder. You can, however, make MSBuild switch the connectionstrings on build by adding the following line of xml into your .csproj file inside the first PropertyGroup:

<AutoParameterizationWebConfigConnectionStrings>
False
</AutoParameterizationWebConfigConnectionStrings>


I've only found this for Web config connectionstrings so far, the others seem to just work immediately.
