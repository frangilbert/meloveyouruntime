---
layout: post
title:  "NVelocity & calling functions"
comments: true
categories: [asp.net,Back end,functions,nvelocity,templating]
---

The other day a dev was using NVelocity for templating emails. He realised that When sending an email, you would need to html encode the data to stop Cross Site Scripting (XSS). Not so much javascript, but being able to embed an image or link which could be malicious. He discovered it is possible to call functions within NVelocity like:

Your Utility:
{% highlight js %}
public class HtmlHelper
{
	public static string HtmlEncode(string value)
	{
		return HttpUtility.HtmlEncode(value);
	}
}
{% endhighlight %}

Pass to NVelocity:
{% highlight js %}
var context = new VelocityContext(parameters);
context.Put("helper", new HtmlHelper());
{% endhighlight %}

And in your template you can then use your function:
{% highlight js %}
$helper.HtmlEncode($user.FirstName)
{% endhighlight %}
Of course, nowadays, we'd tend to use Razor for templating. But this could be useful for your legacy projects or if you still have a soft spot for NVelocity.
