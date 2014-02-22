---
layout: post
title:  "TestCaseSource in Nunit 2.5"
comments: true
categories: [asp.net,Case,nunit,Nunit Case,TestCaseSource,Unit Testing]
---

Recently, one my team mates discovered the [TestCaseSource](http://nunit.com/index.php?p=testCaseSource&amp;r=2.5.2) attribute in Nunit 2.5. I have been using the TestCase attribute for a little while. It enables you to tes multiple inputs with one test:

{% highlight cs %}
[TestCase(12,3,4)]
[TestCase(12,2,6)]
[TestCase(12,4,3)]
public void DivideTest(int n, int d, int q)
{
Assert.AreEqual( q, n / d );
}
{% endhighlight %}

This is useful for various reasons, mainly that you don't have to write a separate test for each input. TestCaseSource is a different way of doing this by allowing the user to build up an IEnumerable of test cases and just add that to the test.

{% highlight cs %}
[Test, TestCaseSource("DivideCases")]
public void DivideTest(int n, int d, int q)
{
Assert.AreEqual( q, n / d );
}

static object[] DivideCases =
{
new object[] { 12, 3, 4 },
new object[] { 12, 2, 6 },
new object[] { 12, 4, 3 } 
};
{% endhighlight %}

This is helpful as you won't have a load of testcase attributes at the top of each test, and you could reuse this data. Lovely!
