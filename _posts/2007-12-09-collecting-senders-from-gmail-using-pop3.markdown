---
layout: post
status: publish
published: true
title: Collecting Senders from Gmail Using POP3
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 52
wordpress_url: http://192.168.123.112/?p=52
date: '2007-12-09 09:27:23 +0000'
date_gmt: '2007-12-09 14:27:23 +0000'
categories:
- Development
tags:
- gmail
- Howto
- pop3
- ruby
- stunnel
- Software
comments: []
---
<p>Over the years, we've had a lot of people submit jokes for <a href="http:&#47;&#47;lol.com&#47;">LOL<&#47;a>. Since we've recently upgraded the site to allow user submissions, we thought it would be nice to let them know they can now add their own jokes (Truth be told, we were slow adding them).</p>
<p>I'm not going to go into great detail, but I thought I'd post a mini howto. <em>Note: I'm not supporting this code, but you are free to use it<&#47;em></p>
<p>Firstly, <a href="http:&#47;&#47;ruby-lang.org">Ruby<&#47;a> 1.8's <a href="http:&#47;&#47;ruby-doc.org&#47;stdlib&#47;libdoc&#47;net&#47;pop&#47;rdoc&#47;classes&#47;Net&#47;POP3.html">POP3<&#47;a> implementation doesn't support SSL. stunnel provides encrypted channels for software that doesn't understand SSL. I run <a href="http:&#47;&#47;sources.redhat.com&#47;cygwin">cygwin<&#47;a> on my Windows box to get access to essential tools. <em>Note: Configuring cygwin and installing it is beyond the scope of this entry, so ask <a href="http:&#47;&#47;www.google.com" target="_blank">Google<&#47;a> for help.<&#47;em></p>
<p>A quick search for gmail and stunnel allowed me to cobble together the following configuration file called <strong>gmail-tunnel.txt<&#47;strong></p>
<pre>
client = yes<br />
debug = debug<br />
foreground = yes</p>
<p>[pop3s]<br />
accept = 127.0.0.1:42<br />
connect = pop.gmail.com:995<&#47;pre><br />
Open up a command window and issue this command to start the tunnel:</p>
<pre>
C>stunnel gmail-tunnel.txt<&#47;pre><br />
Save the following code in <strong>rpopget.rb<&#47;strong> and then execute it from another command window while the tunnel is active. It will write a file called <strong>address.csv<&#47;strong> that lists each address and the number of times that person sent mail.</p>
<pre>
#!&#47;usr&#47;bin&#47;ruby</p>
<p>require 'net&#47;pop'</p>
<p>HOST = 'localhost'<br />
USER = 'YOURACCOUT@gmail.com'<br />
PASS = 'YOURPASSWORD'</p>
<p>$addr = {}</p>
<p>def add_address(a)<br />
    $addr[a] = $addr[a].nil? ? 1 : $addr[a] + 1<br />
end</p>
<p>Net::POP3.start(HOST, 42 , USER, PASS) do |pop|<br />
    if pop.mails.empty?<br />
        puts 'No mail'<br />
    else<br />
        pop.mails.each do |email|<br />
            $stderr.printf(".")</p>
<p>            lines = email.header.split("rn")<br />
            lines.each do |l|<br />
                if l =~ &#47;^From:&#47;<br />
                    if l =~ &#47;^.*&#47;<br />
                        add_address($1)<br />
                    elsif l =~ &#47;^From: (.*@.*)[ ]*&#47;<br />
                        add_address($1)<br />
                    end<br />
                end<br />
            end<br />
        end<br />
    end<br />
end</p>
<p>open("address.csv", "w") do |f|<br />
    f.puts "Address,Count"<br />
    $addr.each_pair do |a, c|<br />
        f.puts "#{a},#{c}"<br />
    end<br />
end<&#47;pre></p>
