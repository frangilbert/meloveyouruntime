---
layout: post
title:  "Mercurial: Adding a remote repository"
comments: true
categories: [hgrc,Mercurial,mercurial,remote repository,Version Control]
---

For home projects I have started using Mercurial. I have a fairly good grasp of Git and DVCS. I have been using Bitbucket for this and it's pretty damn slick. But one thing they don't say is how to add a remote repository to your existing code. It just shows how to clone. With Git the way to add a remote repo is:
remote add origin [remote repo url here]

But in Mercurial, there doesn't seem to be such a thing. I'm sure there is, and please, if you have found one, just leave a comment. In the meantime, the best I have is to add an hgrc file in your .hg folder (created when hg init is run). This should contain the following:

{% highlight git %}
[paths]
default = https://[your repo url here]
{% endhighlight %}

I hope this helps someone.
