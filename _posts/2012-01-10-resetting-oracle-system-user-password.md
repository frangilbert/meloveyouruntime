---
layout: post
title:  "Resetting Oracle SYSTEM user password"
comments: true
categories: [Database,Oracle,system user]
---

I recently got locked out of my Oracle DB (before you think I am an Oracle fan, I am not, but hopefully this will help others who have had the struggle). Someone had changed the SYSTEM user password and not noted it down. I managed to work out a way of changing this. You do need access to the DB box of course. Then you need to go into SQL Plus, Oracle's Command Line tool.

To open this time though, type:
sqlplus "/ as sysdba"

You should be logged into Oracle now. Have a look at whether you are now a SYS user by trying:
SQL> show user

It should respond as:
USER is "SYS"

If all is well by this point, you can then change the SYSTEM password.
SQL> passw system

Good luck to you.
