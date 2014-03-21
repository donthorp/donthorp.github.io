---
layout: post
status: publish
published: true
title: Slow Tomcat Mystery Solved!
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 26
wordpress_url: http://192.168.123.112/?p=26
date: '2002-04-17 23:41:54 +0000'
date_gmt: '2002-04-18 05:41:54 +0000'
categories:
- Software
tags: []
---
<p>
Before you say..."you really should pay more attention", I just want you to know<br />
I've been <b>REALLY</b> swamped at work. We have a really important deadline<br />
 looming so I had to let some things slide. On to the mystery!</p>
<p>
For the last couple of weeks I've been wondering why this website has been<br />
taking 5 to 6 seconds to return a page. This website and<br />
<a href="http://www.johnmunsch.com" target="_blank">John's</a> are<br />
webapps under Tomcat 3.2.2 and have been running that way for quite a while.<br />
When we first set up our sites, I remember being impressed with the<br />
responsiveness of Tomcat. But lately, it has been depressingly slow and I<br />
just couldn't imagine why. The normal Apache sites were responding very<br />
nicely, but the JSP based sites were sluggish.</p>
<p>
Having a hard time waking up this morning, I decided to do a little<br />
sleuthing. I spent a good deal of time with<br />
my friends google and the Tomcat mailing list archives and found absolutely<br />
nothing that was related to my problem. Finally waking up at the office and<br />
getting busy, I forgot my search ... for a while.</p>
<p>
Having a few extra minutes before bedtime, I decided to explore the server. Acting on a<br />
whim, I decided to check disk utilization. At this point in my story most of you<br />
probably just slapped you head and said "DUH! What do you expect!" and you'd<br />
be right <code>/var</code> was out of space.</p>
<p>
Knowing how expensive exceptions can be in general, and especially since<br />
Tomcat was logging to <code>/var</code> I decided to do some spring cleaning. After<br />
moving the logs to another filesystem for archiving, I<br />
restarted the server and then slapped my own head.</p>
<p> My website returned in &lt; 3 seconds on the first pull and &lt; 2 seconds on the second.<br />
John's site being lighter weight than mine<br />
now has a sub-second response time! All this time I had been worrying about<br />
Tomcat as a deployment platform, and it was simple sloth (on my part) that<br />
caused the whole thing.</p>
