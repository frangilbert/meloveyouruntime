---
layout: post
title:  "JsonRequestBehavior.AllowGet"
comments: true
categories: [asp.net,MVC]
---

I recently had an issue with the JsonResult controller type. I tried to connect to an API to return some JSON and received the error:
"This request has been blocked because sensitive information could be disclosed to third party web sites when this is used in a GET request."

Hmmm, I thought. This looks like the library I'm using is faulty, so I tried another library, same issue. So it was the controller. In MVC 2.0, they have tightened up the security to stop JSON Hijacking. Very good indeed. But some changes have been made to the way you can call JSON. If you are making a POST request to the JSON you're good, go back to the sunshine and happiness.

Anyone else will need to return the JSON as follows:
{% highlight cs %}
return new JsonResult { Data = (records), JsonRequestBehavior = JsonRequestBehavior.AllowGet };
{% endhighlight %}

This allows a GET request. Though really, if you are using JSON, it is usually as a service, so just change the request to only accept a POST request ([HttpPost()]) and make the consumer do the same. It is the better way really.
