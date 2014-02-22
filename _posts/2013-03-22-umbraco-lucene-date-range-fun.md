---
layout: post
title:  "Umbraco Lucene Date Range fun"
comments: true
categories: [asp.net,C#,CMS,Date Range,Indexing,Lucene,Umbraco]
---

You know days when you think everything is fine, then you hit a snag and it takes the rest of the day? Yup. That happened today. The issue this time was with an Umbraco implementation I am working on at the moment.

With searching using indexes in Umbraco it's all rather buggy. DateTimes are stored as the format: yyyyMMddTHH:mm:ss in Lucene when Umbraco indexes. The issue with this is that it stores in Lucene as a string. So when you do a query in Lucene for a date range. It'll give you some pretty gnarly results. Lucene expects the format: yyyyMMddHHmmss000

The best thing to do is to convert the string before putting in the index. Umbraco has a nifty Interface you can use for this called IApplicationEventHandler. This is automatically hooked up when Umbraco finds it in your assembly.

You can then use the following method to add the custom string in:

{% highlight js %}
public void OnApplicationStarting(UmbracoApplication httpApplication, ApplicationContext applicationContext)
{
	var siteIndexer = ExamineManager.Instance.IndexProviderCollection["IndexerName"];
	siteIndexer.GatheringNodeData += GatheringSiteIndexDataHandler;
}

void GatheringTagIndexDataHandler(object sender, IndexingNodeDataEventArgs e)
{
	var node = new Node(e.NodeId);
	e.Fields.Add("yourdatefield", "your new date string");
}
{% endhighlight %}

If you want to override a field already in Lucene, you can just remove it first by using:
{% highlight js %}e.Fields.Remove("yourfieldname"){% endhighlight %}

Good luck!
