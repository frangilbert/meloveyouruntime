---
layout: post
title:  "Remotely disconnect an RDP session"
comments: true
categories: [General,log off,rdp,remote]
---

If you find someone doesn't log off their session after using RDP and just disconnects, you may need to regularly ask them to log off, or force a log off. But you can also log off their session remotely by doing the following in your command line (this should work in your dev environments internally, it may not work on servers outside your domain etc.).

{% highlight shell %}
qwinsta /server:
{% endhighlight %}

You get results with who is logged in, a state and an id (session Id). Just remember the id.

Then type:
{% highlight shell %}
logoff  /server:
{% endhighlight %}
