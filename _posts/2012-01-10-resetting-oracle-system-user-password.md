---
layout: post
title:  "Resetting Oracle SYSTEM user password"
comments: true
categories: [Database,Oracle,system user]
---

I recently got locked out of my Oracle DB (before you think I am an Oracle fan, I am not, but hopefully this will help others who have had the struggle). Someone had changed the SYSTEM user password and not noted it down. I managed to work out a way of changing this. You do need access to the DB box of course. Then you need to go into SQL Plus, Oracle's Command Line tool.

To open this time though, type:
{% highlight shell %}
sqlplus "/ as sysdba"
{% endhighlight %}

You should be logged into Oracle now. Have a look at whether you are now a SYS user by trying:
{% highlight shell %}
SQL> show user
{% endhighlight %}

It should respond as:
{% highlight shell %}
USER is "SYS"
{% endhighlight %}

If all is well by this point, you can then change the SYSTEM password.
{% highlight shell %}
SQL> passw system
{% endhighlight %}

Good luck to you.
