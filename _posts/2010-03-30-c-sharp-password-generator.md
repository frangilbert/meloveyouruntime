---
layout: post
title:  "C# Password generator"
comments: true
categories: [Uncategorized]
---

I recently wrote a small amount of code to generate a password without using a GUID  or something. Pretty simple stuff, but good for a library.

{% highlight cs %}
string pwdChars = "abcdefghijkmnopqrstuvwxyzABCDEFGHJKLMNOPQRSTUVWXYZ0123456789";
char[] pwdElements = pwdChars.ToCharArray();

Random random = new Random();
StringBuilder builder = new StringBuilder();

//Generate password in loop
for(int i = 0; i < passwordLength; i++)
{
	int randomChar = random.Next(0, pwdElements.Length);
	builder.Append(pwdElements[randomChar]);
}

return builder.ToString();
{% endhighlight %}