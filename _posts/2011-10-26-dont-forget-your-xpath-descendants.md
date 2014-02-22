---
layout: post
title:  "Don't forget your (XPATH) descendants"
comments: true
categories: [General,xml,xpath]
---

Recently at work, we've been getting into Selenium tests for regression testing. With this comes a lot of XPath. I love a bit of XPath, and along with Regex and XSLT as long as you use the KISS principle, everything will be ok.

A developer was working on getting each link in a page within a div to be checked. The issue was that these could be on different levels (it was a Sitemap). e.g. one link may be in a list item, the next may be embedded within another sub-list item.

We had real issues in getting all the links in the right way. We tried:
{% highlight xml %}
//div[@id='mod-site-map']//a
{% endhighlight %}
(The a's would be iterated through) with varying degrees of success.

I'd forgotten descendants completely. In a head slapping moment, we tried:
{% highlight xml %}
//div[@id='mod-site-map']/descendant::a
{% endhighlight %}

Done! One of my favourite XPath reference sites is still: [http://zvon.org/xxl/XPathTutorial/General/examples.html](http://zvon.org/xxl/XPathTutorial/General/examples.html). It's been there since about 1997, but still helps out.
