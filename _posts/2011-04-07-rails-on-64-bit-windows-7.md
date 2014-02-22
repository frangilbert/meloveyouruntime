---
layout: post
title:  "Rails on 64-bit Windows 7"
comments: true
categories: [Rails,Ruby]
---

Recently I have decided to try out Ruby on Rails again. Ok, I have done one or two projects with it, but I want to have another go. I'm going to share my thoughts here about it and what's got me. After some time with C#, most error messages don't phase me much anymore, however, Rails starts my learning again.

I've just been bashing the keyboard to bits in an attempt to get  Rails 3 to work on my 64-bit Windows machine. The error was that SQLite3.dll could not be found, even when I changed my config.yaml to look for postgresql.

To fix, download the sqlite-dll-win32-x[version].zip from the Sqlite website, then unzip to C:Windowssystem (not System32) and oddly it works.

I hope this helps someone from losing their hair :).
