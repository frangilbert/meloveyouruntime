---
layout: post
title:  "Remove your Webforms ViewEngine for MVC"
comments: true
categories: [asp.net,C#,global.asax,MVC,razor,viewengine,webforms]
---

I learnt something interesting today. When we use MVC and the Razor view engine, we can end up with a bit of a performance hit. In fact, Razor can end up running much slower than Webforms because we don't clear the Webform view engine (up to half as fast!), so your app will run that view engine first, and only when it fails to find the relevant files will it switch to the Razor view engine. And to get round this, all you do is add the following to your Application_Start method in the Global.asax.

{% highlight cs %}
ViewEngines.Engines.Clear();
ViewEngines.Engines.Add(new RazorViewEngine());
{% endhighlight %}

You're welcome!
