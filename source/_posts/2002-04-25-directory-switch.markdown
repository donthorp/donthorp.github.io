---
layout: post
status: publish
published: true
title: Directory Switch
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 29
wordpress_url: http://192.168.123.112/?p=29
date: '2002-04-25 11:35:00 +0000'
date_gmt: '2002-04-25 16:35:00 +0000'
categories:
- Software
tags: []
---
<p>function sister() {<br />
    cd "`pwd | sed -e s/$1/$2/`"<br />
}</p>
<p>function sist() {<br />
    sister main test<br />
}</p>
<p>function sism() {<br />
    sister test main<br />
}</p>
