---
layout: post
status: publish
published: true
title: ActiveX - Resident Evil
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 64
wordpress_url: "/post/64"
date: '2008-02-05 09:47:26 +0000'
date_gmt: '2008-02-05 14:47:26 +0000'
categories:
- Technology
tags:
- internet explorer
- Security
- activex
---
<p>I've always wondered why ActiveX controls continue to be written. There are cases where you need access to the local machine to provide a useful service, but most things don't, at least not outside of a sandbox. There will always be security flaws in every type of software, but ActiveX controls seem to be the easiest target for the dark side. Most of my friends and I stopped using Internet Explorer years ago except for a few sites that either require IE (e.g. Outlook Web Mail) or other poorly written sites that won't even display data unless you're using IE.</p>
<p>Browsing through my email today I ran across an article on eWeek, <a href="http://www.eweek.com/c/a/Security/ActiveX-Under-Seige-Facebook-MySpace-Image-Uploaders-Vulnerable/?kc=EWKNLNAV020508STR1" target="_blank">ActiveX Under Seige: Facebook, MySpace Image Uploaders Vulnerable</a> that once again highlights the problem. Here is a small excerpt:</p>
<blockquote><p>
"In tandem with the public release of this information, remote code-execution exploits targeting the Aurigma, Facebook, and Yahoo! issues were released. Each issue allows remote attackers to execute arbitrary code in the context of the application using the ActiveX control (typically Internet Explorer)," Kamerling said.</p>
<p>In the absence of patches, Symantec recommends that IE users take "extreme caution" when browsing the Web and ensure that the browser is configured with the highest security settings.</p>
<p>The US-CERT goes a step further, recommending that IE users completely disable ActiveX scripting in the browser.
</p></blockquote>
<p>The article also points you to a helpful guide from US-CERT on <a href="http://www.us-cert.gov/reading_room/securing_browser/browser_security.html#Internet_Explorer" target="_blank">Securing Your Web Browser</a>.</p>
