---
layout: post
status: publish
published: true
title: Swing Threading
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 45
wordpress_url: http://192.168.123.112/?p=45
date: '2003-10-31 08:36:30 +0000'
date_gmt: '2003-10-31 14:36:30 +0000'
categories:
- Software
tags: []
---
<p>
The article <a href="http://today.java.net/pub/a/today/2003/10/24/swing.html" target="_blank">Rethinking Swing Threading</a> by <a href="http://today.java.net/pub/au/5" target="_blank">Jonathan Simon</a> provides a good description on how to use event based programming to simplify your Swing development.</p>
<p>
I used a similar method in the past and it worked very well. My only addition to what he did was to add a Job system for handling the tasks. Basically, I wrote a Task for each operation that I wanted to perform in the system and handed it off to the job manager to execute and monitor.  In addition to being able to simplify the Swing code, it made it possible to easily annotate the task with any exceptions that occurred for use in displaying errors to the user.</p>
