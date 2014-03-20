---
layout: post
status: publish
published: true
title: Tomcat Configuration
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 44
wordpress_url: http://192.168.123.112/?p=44
date: '2003-06-26 09:36:45 +0000'
date_gmt: '2003-06-26 15:36:45 +0000'
categories:
- Software
tags: []
comments: []
---
<p>
There is a great article at <a href="http:&#47;&#47;www.onjava.com">OnJava.com<&#47;a> called <a href="http:&#47;&#47;www.onjava.com&#47;pub&#47;a&#47;onjava&#47;2003&#47;06&#47;25&#47;tomcat_tips.html" target="_blank">Top Ten Tomcat Configuration Tips<&#47;a>. It points out a method of adding new web applications without adding a context in server.xml.<br />
<&#47;p></p>
<p>
Basically, you can create an XML fragment that contains the context you would have placed in the server.xml and put it in a separate xml file. Name the file MyApp.xml, place it in the webapps directory and there you go. The docBase attribute can point to anywhere on your file system, so you don't have to place your application in the Tomcat webapps directory.<br />
<&#47;p></p>
<p>
Why is this important? If you have a web application and you want to write an installation program for it what do you do? You could write code to edit server.xml to add&#47;remove&#47;modify your context or you could simply copy&#47;delete&#47;replace MyApp.xml in the Tomcat webapps directory. On Windows, you could do a standard install, put your web application under <em>Program Files&#47;My Company&#47;MyApp<&#47;em> and copy your context file to <em>CATALINA_HOME&#47;webapps<&#47;em>. You're uninstall process also becomes much simpler.<br />
<&#47;p></p>
