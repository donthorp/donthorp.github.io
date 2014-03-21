---
layout: post
status: publish
published: true
title: SVCHOST - Why is it using so much CPU
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 24
wordpress_url: http://192.168.123.112/?p=24
date: '2002-04-09 09:03:53 +0000'
date_gmt: '2002-04-09 15:03:53 +0000'
categories:
- Software
tags:
- meandering
---
<p>
Every once in a while, you find an article on Microsoft's knowledge base that actually helps answer questions you've had for a long time. While researching why a process was eating up so much of my CPU I found the following article - <a href="http://support.microsoft.com/search/preview.aspx?scid=kb;en-us;Q314056" target="_blank">A Description of Svchost.exe in Windows XP (Q314056)</a>.</p>
<p>
For years I've wondered how to find out what tasks were behind <code>svchost.exe</code>; this article shows you how.  At a command prompt simply type <code>tasklist /svc</code>.</p>
