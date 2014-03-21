---
layout: post
status: publish
published: true
title: LTools - Reading and Writing ext2 partitions from Windows
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 38
wordpress_url: http://192.168.123.112/?p=38
date: '2002-09-19 15:50:22 +0000'
date_gmt: '2002-09-19 21:50:22 +0000'
categories:
- Software
tags: []
---
<p>
A while back, I had a DDR module go bad and trash portions of my Win2k registry. Not a huge deal, Installed XP and copied all of the data over. The bigger problem was that I was dual booting to RedHat 7.3 using Grub. When I installed XP, it proceeded to wipe out my bootloader thereby making it impossible to boot into Linux (for the record, I haven't tried to restore the partition).</p>
<p>
These tools were all found at <a href="http://penguin.cz/~mhi/fs/Filesystems-HOWTO/Filesystems-HOWTO-6.html" target="_blank">FileSystems:HOWTO</a></p>
<h4>LTools</h4>
<p>
On a whim today, I decided to see if there were any tools available for reading Ext2/Ext3 partitions from Windows. A little google magic and up pops  <a href="http://www.it.fht-esslingen.de/~zimmerma/software/ltools.htm" target="_blank">LTools</a>. I extracted it, ran it's setup program, started the Java version of the UI, pointed it the drive which contains the Ext2 partitions and viola! I got my data.  This product is great for browsing, but it won't let you do recursive copies.</p>
<h4>Explore2fs</h4>
<p>
Failing to be able to copy the files I needed using LTools, I found <a href="http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm" target="_blank">Explore2fs</a>. While not as polished as LTools from a UI perspective, it does seem to be able to recursively copy files.</p>
