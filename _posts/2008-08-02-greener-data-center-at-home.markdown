---
layout: post
status: publish
published: true
title: Greener Data Center at Home
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 94
wordpress_url: http://www.donthorp.net/?p=94
date: '2008-08-02 09:49:59 +0000'
date_gmt: '2008-08-02 14:49:59 +0000'
categories:
- Technology
tags:
- musing
- dell
- pc
- ubuntu
- vm
- vmware
- energy
- noise
comments:
- id: 59
  author: John Hattan
  author_email: john@thecodezone.com
  author_url: http://www.thecodezone.com
  date: '2008-08-02 13:34:19 +0000'
  date_gmt: '2008-08-02 18:34:19 +0000'
  content: Yeah, I saw those last week. Very classy looking machine, although $130
    for the bamboo housing is pretty steep. I'd get one for Maggie but it's pretty
    hard to cost-justify that purchase when I'm getting ready to spend $4k on a new
    plotter.
---
<p>Let's face it, I collect computers. Trust me, I don't want to be in the computer collection business, but some how I have several sitting in the closet and many up and running as I write. Being an entrepreneur, start-up engineer, software developer, etc, I need machines to get things done. So, I tend to treat the house like a personal data center. Several enabling technologies have emerged that have helped me start down-sizing my home data center to be much more energy and space efficient. At this point noise and heat are still my biggest issues.<img src="&#47;content&#47;uploads&#47;2008&#47;08&#47;295.jpg" alt="Product photo of a blue Dell Studio Hybrid" title="Dell Studio Hybrid" width="200" height="200" class="alignnone size-full wp-image-96" style="float:right"&#47;> </p>
<p>In the past, I would buy the best computer I could build and install everything under the sun on it to try and keep costs down. Problem is each machine would start collecting more and more cruft and the next thing you know, you're wanting another box.</p>
<p>Not too long ago, <a href="http:&#47;&#47;www.vmware.com&#47;" target="_blank">VMWare<&#47;a> unshackled their server product and allowed me to start collapsing physical hardware on to virtual hardware. They also made their product run on Linux, including <a href="http:&#47;&#47;www.ubuntu.com" target="_blank">Ubuntu<&#47;a> my current distro of choice. The combination of VMWare Server with Ubuntu gave me the power to have a low&#47;no cost solution for collapsing physical machines and easily re-using older hardware.</p>
<p>Another benefit is that I could start building single purpose "machines". I could afford to run a Virtual Machine (VM) per application or have development specific VMs. A huge benefit was that you can migrate a VMs quickly to different hardware. I can, for example, take a web application from my "data center" drop it on my laptop and go mobile. When I get home, I simply move it back into the data center. When I buy a new host machine, I can easily move the VMs and recycle the old hardware without having to re-install all of the software. Not only have I started running server type applications in their own VM, I have also started creating single purpose VMs for desktop applications. Currently, I have a VM for my trading&#47;investment software and I'm about to build a VM for my QuickBooks and other bookkeeping and business tasks.</p>
<p>I know I'm behind, but I finally took a look at the <a href="http:&#47;&#47;www.dell.com&#47;content&#47;products&#47;productdetails.aspx&#47;desktop-studio-hybrid?c=us&cs=19&l=en&s=dhs" target="_blank">Dell Studio Hybrid<&#47;a>. There is a <a href="http:&#47;&#47;www.pcmag.com&#47;article2&#47;0,2704,2326613,00.asp" target="_blank">review<&#47;a> on PC Magazine. Seeing the form factor, I immediately wondered if it would run Ubuntu. Quick little search and I found the quote below at <a href="http:&#47;&#47;ideastorm.com&#47;article&#47;show&#47;10091209&#47;Can_we_get_Studio_Hybrid_with_Ubuntu" target="_blank">Dell's IdeaStorm<&#47;a>. </p>
<p><img src="&#47;content&#47;uploads&#47;2008&#47;08&#47;picture-2.png" alt="Posted 01 Aug 2008 on Dell&#039;s IdeaStorm. " title="Quote: We're not planning to sell Ubuntu on the Studio Hybrid, but it is a pretty nice little machine. The team did some testing on it with 8.04 several months back. Most of the hardware works bu default, except for video (had to switch to generic VESA driver). The system's Intel graphics chipset isn't supported in 8.04, but I would expect 8.10 to work very well." width="90%" height="90%" class="alignnone size-full wp-image-95" &#47;></p>
<p>To me, a home VM server needs:</p>
<ol>
<li>The capacity to have lots of RAM<&#47;li>
<li>Enough storage for all of the VMs you want to host<&#47;li>
<li>A fast, cool running multi-core CPU<&#47;li>
<li>Runs quietly. Noise is tiring and annoying<&#47;li>
<li>The ability to run Ubuntu and VMWare server<&#47;li>
<li>Draw as little energy as possible<&#47;li>
<li>One or more Gb ethernet adapters<&#47;li><br />
<&#47;ol></p>
<p>What it doesn't need:</p>
<ol>
<li>Fast graphics, I access the machines remotely<&#47;li>
<li>Big form factor, I might want it in a closet.<&#47;li>
<li>Proprietary anything, we want to run linux<&#47;li>
<li>It should be relatively inexpensive<&#47;li><br />
<&#47;ol></p>
<p>The Studio Hybrid allows:</p>
<ul>
<li>Intel Core 2 Duo up to 2.6GHz<&#47;li>
<li>4 GB RAM<&#47;li>
<li>320 GB SATA Hard Drive<&#47;li>
<li>Integrated video with DVI and HDMI<&#47;li>
<li>Built-in wireless N and Gigabit Ethernet<&#47;li><br />
<&#47;ul></p>
<p>What I haven't been able to determine is how quiet it is. You can see from the <a href="http:&#47;&#47;www.dell.com&#47;content&#47;topics&#47;topic.aspx&#47;global&#47;products&#47;desktop_studio&#47;includes&#47;en&#47;us&#47;desktop-studio-hybrid-superview?c=us&cs=19&l=en&pageoverride=features_view6&s=dhs" target="_blank">back panel<&#47;a> that it does have a fan, so it can't be completely silent. But in all other aspects, it looks like it could be a viable platform for a VM host in my greener home data center.</p>
