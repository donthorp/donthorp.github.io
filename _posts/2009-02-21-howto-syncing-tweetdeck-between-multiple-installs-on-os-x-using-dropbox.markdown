---
layout: post
status: publish
published: true
title: 'Howto: Syncing TweetDeck Between Multiple Installs on OS X using DropBox'
author: Don Thorp
author_login: donthorp
author_email: don@donthorp.net
author_url: http://www.donthorp.net
wordpress_id: 321
wordpress_url: http://donthorp.net/?p=321
date: '2009-02-21 16:43:47 +0000'
date_gmt: '2009-02-21 21:43:47 +0000'
categories:
- SocNet
tags:
- Howto
- twitter
- tweetdeck
- dropbox
- sync
comments:
- id: 283
  author: How to Get Six Pack Fast
  author_email: vincedel422@gmail.com
  author_url: http://www.linkedin.com/in/howtogetasixpackfast
  date: '2009-04-15 09:01:56 +0000'
  date_gmt: '2009-04-15 14:01:56 +0000'
  content: My fellow on Facebook shared this link with me and I'm not dissapointed   that
    I came here.
- id: 327
  author: Alissa Biegler
  author_email: Cierra_Linkovich@gmail.com
  author_url: ''
  date: '2012-07-29 11:20:32 +0000'
  date_gmt: '2012-07-29 16:20:32 +0000'
  content: Scott, it's nice to meet you. I hope Shutterstock will continue to accept
    my scientific work. Shutterstock now has a educational micrograph (photos taken
    with a microscope) section second to none.
- id: 383
  author: does hypnosis work
  author_email: teodorogirardi@web.de
  author_url: http://thehypnotherapyworks.com/blog-page
  date: '2013-11-26 17:03:22 +0000'
  date_gmt: '2013-11-26 22:03:22 +0000'
  content: "Pretty nice post. I just stumbled upon your blog and wished to say that
    I've truly loved surfing around \r\nyour blog posts. After all I will be subscribing
    on your \r\nfeed and I'm hoping you write again very soon!"
---
<p>A big thanks to <a href="http:&#47;&#47;h0bbel.p0ggel.org&#47;about" target="_blank">Christian Mohn aka h0bbel<&#47;a> for his <a href="http:&#47;&#47;h0bbel.p0ggel.org&#47;howto-sync-settings-between-multiple-tweetdeck-installs-on-windows" target="_blank">article<&#47;a> on syncing TweetDeck between multiple Windows installations. It quickly pointed me in the right direction on OS X. In many ways, it's much easier on OS X because it has soft links as part of its Unix heritage. Since I no longer use Windows computers for communication, I'll leave it to someone else to figure out how to keep multiple OSs in sync.</p>
<h4>DropBox<&#47;h4><br />
The technique I use also happens to take advantage of <a href="http:&#47;&#47;www.getdropbox.com&#47;" target="_blank">DropBox<&#47;a>. If you're not familiar with DropBox you should be. There are many ways to keep files in sync on multiple computers, some easier than others. I consider DropBox to be the easiest, most pain-free method I've found to date. DropBox provides a client integration piece that simply appears in your file system. Put a file in a folder and it will show up on all of your other machines.</p>
<p>DropBox also allows you to create shared folders for transferring files between friends and co-workers. <a href="http:&#47;&#47;www.johnmunsch.com">John<&#47;a> and I use it fairly regularly to transfer files that aren't in our subversion repositories. I've also used DropBox to safely get files to and from my servers with their web interface. </p>
<h4>TweetDeck on OS X<&#47;h4></p>
<p>This howto assumes that you are already using TweetDeck on at least one computer. It should also be noted that this technique has the same limitation as h0bble's; You must only run TweetDeck on one machine at a time. If this becomes an issue for me, I've considered creating a launcher for TweetDeck that would place a lock file in the shared directory to help prevent accidental launches. The same launcher could also monitor a termination file to close the remote instance.</p>
<p>TweetDeck stores your configuration files in your Preferences folder. As mentioned in h0bbel's article, a random number is part of the filename. I used the Unix command <em>find<&#47;em> to locate my TweetDeck files. Open a terminal window in your home directory and issue the following command.</p>
<blockquote class="code"><p>
find . -name TweetDeckFast.*<br />
<&#47;blockquote></p>
<p>You will most likely see multiple results. You are interested in the folder <em>Library&#47;Preferences&#47;TweetDeckFast.[random number]<&#47;em>. Inside that folder is a sub-folder named <em>Local Store<&#47;em> that TweetDeck uses to store your configuration files. There are two files of interest in that folder.</p>
<blockquote class="code"><p>
<em>preferences_[twitter_username].xml<&#47;em><br />
<em>td_26_[twitter_username].db<&#47;em><br />
<&#47;blockquote></p>
<h4>The Technique<&#47;h4></p>
<p>The technique takes advantage of the soft links I mentioned earlier. For those unfamiliar with the term, a soft link is simply a name or alias that provides a direct link to another name anywhere in the file system. Soft links will be created to fool TweetDeck into thinking its files are where they have always been, when in fact, they're going to reside in the DropBox. DropBox will insure that the contents of the TweetDeck files are synchronized on all other computers where you have a DropBox as long as those machines have a network connection.</p>
<p>The reason it is important to run TweetDeck on only one machine at a time is that DropBox will try and keep the files in sync thereby generating conflicts in the files. The other reason is that you will blow through your Twitter API limits in no time.</p>
<h4>How<&#47;h4></p>
<ol>
<li>Stop TweetDeck on all computers<&#47;li>
<li>Open a Terminal window in your home directory<&#47;li>
<li>Create a folder in your DropBox.<br />
<blockquote class="code"><p>
mkdir Dropbox&#47;TweetDeck<br />
<&#47;blockquote><br />
<&#47;li></p>
<li>Change to your TweetDeck Local Store<br />
<blockquote class="code"><p>cd Library&#47;Preferences&#47;TweetDeckFast.*&#47;Local\ Store<&#47;blockquote><br />
<&#47;li></p>
<li>Move your files to your DropBox<br />
<blockquote class="code"><p>
mv preferences*.xml ~&#47;Dropbox&#47;TweetDeck<br />
mv td_26_*.db ~&#47;Dropbox&#47;TweetDeck<br />
<&#47;blockquote><br />
<&#47;li></p>
<li>Create your soft links. Please replace <em>[twitter_username]<&#47;em> with your twitter name. For example I used my twitter username <a href="http:&#47;&#47;twitter.com&#47;donthorp" target="_blank">donthorp<&#47;a>.<br />
<blockquote class="code"><p>
ln -s &#47;Users&#47;$USER&#47;Dropbox&#47;TweetDeck&#47;preferences_[twitter_username].xml&nbsp;preferences_[twitter_username].xml<br />
<&#47;blockquote></p>
<blockquote class="code"><p>
ln -s &#47;Users&#47;$USER&#47;Dropbox&#47;TweetDeck&#47;td_26_[twitter_username].db&nbsp; td_26_[twitter_username].db<br />
<&#47;blockquote><br />
<&#47;li><br />
<&#47;ol></p>
<p>On every other machine you want to use your synchronized TweetDeck files do the following</p>
<ol>
<li>Stop TweetDeck<&#47;li>
<li>Open a Terminal window in your home directory<&#47;li>
<li>Verify that DropBox has synchronized your TweetDeck files. You should see the .xml and .db files.<br />
<blockquote class="code"><p>
ls Dropbox&#47;TweetDeck<br />
<&#47;blockquote><br />
<&#47;li></p>
<li>Change to your TweetDeck Local Store<br />
<blockquote class="code"><p>cd Library&#47;Preferences&#47;TweetDeckFast.*&#47;Local\ Store<&#47;blockquote><br />
<&#47;li></p>
<li>Remove your files so that you can create your symlink. Note: If you want to preserve them, copy them somewhere else before deleting.<br />
<blockquote class="code"><p>
rm preferences*.xml<br />
rm td_26_*.db<br />
<&#47;blockquote><br />
<&#47;li></p>
<li>Create your soft links. Please replace <em>[twitter_username]<&#47;em> with your twitter name. For example I used my twitter username <a href="http:&#47;&#47;twitter.com&#47;donthorp" target="_blank">donthorp<&#47;a>.<br />
<blockquote class="code"><p>
ln -s &#47;Users&#47;$USER&#47;Dropbox&#47;TweetDeck&#47;preferences_[twitter_username].xml preferences_[twitter username].xml<br />
<&#47;blockquote></p>
<blockquote class="code"><p>
ln -d &#47;Users&#47;$USER&#47;Dropbox&#47;TweetDeck&#47;td_26_[twitter_username].db td_26_[twitter_username].db<br />
<&#47;blockquote><br />
<&#47;li><br />
<&#47;ol></p>
<p>Now you are ready to enjoy TweetDeck with all of your setting synchronized between machines. While I used DropBox for this solution, it is not required. Any method you have of moving the actual TweetDeck files between machines will suffice. Personally, using DropBox made it simple, efficient, and took advantage of my current workflow.</p>
