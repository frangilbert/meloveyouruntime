---
layout: post
title:  "[CSS3] System Selection"
comments: true
categories: [CSS]
---

A new selector is available in CSS3. It goes something like:
::selection and it allows the user to change the highlight colour of the page. e.g.

.red::selection {
	background: #ff0000;
}

It's a small step, but nice and it gracefully degrades (or progressively enhances, depending on your outlook on life) if the user is using an older browser.
