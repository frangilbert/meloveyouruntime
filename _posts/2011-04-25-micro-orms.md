---
layout: post
title:  "Micro ORMs"
comments: true
categories: [asp.net,Database,Micro ORM,ORM,SQL]
---

I've always been a little wary of ORMs. Linq to SQL, Entity Framework, NHibernate. They're all powerful, great to use and ease up development time quite a bit. The reason I'm not sure about them is the Select n+1 issue, general performance, tweakability and, well, DBAs don't particularly like them, and if they don't like them, I wonder how that can be good for the database they control.

Enter the micro ORM. Yes, we are going back to writing SQL, they are just small libraries that take your SQL, and convert them to objects. It makes for much better performance and DBAs should be much happier to write their stored procedures for you to consume with fewer issues.

The current micro ORMs are:
PetaPoco: [http://www.toptensoftware.com/petapoco/](http://www.toptensoftware.com/petapoco/)
Dapper: [http://code.google.com/p/dapper-dot-net/](http://code.google.com/p/dapper-dot-net/)
Massive: [https://github.com/robconery/massive](https://github.com/robconery/massive)[Mr. Scott Hanselmann also covers this](http://www.hanselman.com/blog/HanselminutesPodcast262TheRiseOfTheMicroORMWithSamSaffronAndRobConery.aspx).

What are your thoughts on this? Is it a bit too light? I can see both the benefits and downsides, but it is an interesting way of working.
