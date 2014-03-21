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
---
<p>Over the years, we've had a lot of people submit jokes for <a href="http://lol.com/">LOL</a>. Since we've recently upgraded the site to allow user submissions, we thought it would be nice to let them know they can now add their own jokes (Truth be told, we were slow adding them).</p>
<p>I'm not going to go into great detail, but I thought I'd post a mini howto. <em>Note: I'm not supporting this code, but you are free to use it</em></p>
<p>Firstly, <a href="http://ruby-lang.org">Ruby</a> 1.8's <a href="http://ruby-doc.org/stdlib/libdoc/net/pop/rdoc/classes/Net/POP3.html">POP3</a> implementation doesn't support SSL. stunnel provides encrypted channels for software that doesn't understand SSL. I run <a href="http://sources.redhat.com/cygwin">cygwin</a> on my Windows box to get access to essential tools. <em>Note: Configuring cygwin and installing it is beyond the scope of this entry, so ask <a href="http://www.google.com" target="_blank">Google</a> for help.</em></p>
<p>A quick search for gmail and stunnel allowed me to cobble together the following configuration file called <strong>gmail-tunnel.txt</strong></p>
<pre>
client = yes
debug = debug
foreground = yes

[pop3s]
accept = 127.0.0.1:42
connect = pop.gmail.com:995</pre>
<p>Open up a command window and issue this command to start the tunnel:</p>
<pre>
C&gt;stunnel gmail-tunnel.txt</pre>
<p>Save the following code in <strong>rpopget.rb</strong> and then execute it from another command window while the tunnel is active. It will write a file called <strong>address.csv</strong> that lists each address and the number of times that person sent mail.</p>
<pre>
#!/usr/bin/ruby

require 'net/pop'

HOST = 'localhost'
USER = 'YOURACCOUT@gmail.com'
PASS = 'YOURPASSWORD'

$addr = {}

def add_address(a)
    $addr[a] = $addr[a].nil? ? 1 : $addr[a] + 1
end

Net::POP3.start(HOST, 42 , USER, PASS) do |pop|
    if pop.mails.empty?
        puts 'No mail'
    else
        pop.mails.each do |email|
            $stderr.printf(".")

            lines = email.header.split("rn")
            lines.each do |l|
                if l =~ /^From:/
                    if l =~ /^.*/
                        add_address($1)
                    elsif l =~ /^From: (.*@.*)[ ]*/
                        add_address($1)
                    end
                end
            end
        end
    end
end

open("address.csv", "w") do |f|
    f.puts "Address,Count"
    $addr.each_pair do |a, c|
        f.puts "#{a},#{c}"
    end
end</pre>
