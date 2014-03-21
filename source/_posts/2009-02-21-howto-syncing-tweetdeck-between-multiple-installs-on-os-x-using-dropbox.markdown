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
---
<p>A big thanks to <a href="http://h0bbel.p0ggel.org/about" target="_blank">Christian Mohn aka h0bbel</a> for his <a href="http://h0bbel.p0ggel.org/howto-sync-settings-between-multiple-tweetdeck-installs-on-windows" target="_blank">article</a> on syncing TweetDeck between multiple Windows installations. It quickly pointed me in the right direction on OS X. In many ways, it's much easier on OS X because it has soft links as part of its Unix heritage. Since I no longer use Windows computers for communication, I'll leave it to someone else to figure out how to keep multiple OSs in sync.</p>
<h4>DropBox</h4>
<p>The technique I use also happens to take advantage of <a href="http://www.getdropbox.com/" target="_blank">DropBox</a>. If you're not familiar with DropBox you should be. There are many ways to keep files in sync on multiple computers, some easier than others. I consider DropBox to be the easiest, most pain-free method I've found to date. DropBox provides a client integration piece that simply appears in your file system. Put a file in a folder and it will show up on all of your other machines.</p>
<p>DropBox also allows you to create shared folders for transferring files between friends and co-workers. <a href="http://www.johnmunsch.com">John</a> and I use it fairly regularly to transfer files that aren't in our subversion repositories. I've also used DropBox to safely get files to and from my servers with their web interface. </p>
<h4>TweetDeck on OS X</h4>
<p>This howto assumes that you are already using TweetDeck on at least one computer. It should also be noted that this technique has the same limitation as h0bble's; You must only run TweetDeck on one machine at a time. If this becomes an issue for me, I've considered creating a launcher for TweetDeck that would place a lock file in the shared directory to help prevent accidental launches. The same launcher could also monitor a termination file to close the remote instance.</p>
<p>TweetDeck stores your configuration files in your Preferences folder. As mentioned in h0bbel's article, a random number is part of the filename. I used the Unix command <em>find</em> to locate my TweetDeck files. Open a terminal window in your home directory and issue the following command.</p>
<blockquote class="code"><p>
find . -name TweetDeckFast.*
</p></blockquote>
<p>You will most likely see multiple results. You are interested in the folder <em>Library/Preferences/TweetDeckFast.[random number]</em>. Inside that folder is a sub-folder named <em>Local Store</em> that TweetDeck uses to store your configuration files. There are two files of interest in that folder.</p>
<blockquote class="code"><p>
<em>preferences_[twitter_username].xml</em><br />
<em>td_26_[twitter_username].db</em>
</p></blockquote>
<h4>The Technique</h4>
<p>The technique takes advantage of the soft links I mentioned earlier. For those unfamiliar with the term, a soft link is simply a name or alias that provides a direct link to another name anywhere in the file system. Soft links will be created to fool TweetDeck into thinking its files are where they have always been, when in fact, they're going to reside in the DropBox. DropBox will insure that the contents of the TweetDeck files are synchronized on all other computers where you have a DropBox as long as those machines have a network connection.</p>
<p>The reason it is important to run TweetDeck on only one machine at a time is that DropBox will try and keep the files in sync thereby generating conflicts in the files. The other reason is that you will blow through your Twitter API limits in no time.</p>
<h4>How</h4>
<ol>
<li>Stop TweetDeck on all computers</li>
<li>Open a Terminal window in your home directory</li>
<li>Create a folder in your DropBox.<br />
<blockquote class="code"><p>
mkdir Dropbox/TweetDeck
</p></blockquote>
</li>
<li>Change to your TweetDeck Local Store<br />
<blockquote class="code"><p>cd Library/Preferences/TweetDeckFast.*/Local\ Store</p></blockquote>
</li>
<li>Move your files to your DropBox<br />
<blockquote class="code"><p>
mv preferences*.xml ~/Dropbox/TweetDeck<br />
mv td_26_*.db ~/Dropbox/TweetDeck
</p></blockquote>
</li>
<li>Create your soft links. Please replace <em>[twitter_username]</em> with your twitter name. For example I used my twitter username <a href="http://twitter.com/donthorp" target="_blank">donthorp</a>.<br />
<blockquote class="code"><p>
ln -s /Users/$USER/Dropbox/TweetDeck/preferences_[twitter_username].xml&nbsp;preferences_[twitter_username].xml
</p></blockquote>
<blockquote class="code"><p>
ln -s /Users/$USER/Dropbox/TweetDeck/td_26_[twitter_username].db&nbsp; td_26_[twitter_username].db
</p></blockquote>
</li>
</ol>
<p>On every other machine you want to use your synchronized TweetDeck files do the following</p>
<ol>
<li>Stop TweetDeck</li>
<li>Open a Terminal window in your home directory</li>
<li>Verify that DropBox has synchronized your TweetDeck files. You should see the .xml and .db files.<br />
<blockquote class="code"><p>
ls Dropbox/TweetDeck
</p></blockquote>
</li>
<li>Change to your TweetDeck Local Store<br />
<blockquote class="code"><p>cd Library/Preferences/TweetDeckFast.*/Local\ Store</p></blockquote>
</li>
<li>Remove your files so that you can create your symlink. Note: If you want to preserve them, copy them somewhere else before deleting.<br />
<blockquote class="code"><p>
rm preferences*.xml<br />
rm td_26_*.db
</p></blockquote>
</li>
<li>Create your soft links. Please replace <em>[twitter_username]</em> with your twitter name. For example I used my twitter username <a href="http://twitter.com/donthorp" target="_blank">donthorp</a>.<br />
<blockquote class="code"><p>
ln -s /Users/$USER/Dropbox/TweetDeck/preferences_[twitter_username].xml preferences_[twitter username].xml
</p></blockquote>
<blockquote class="code"><p>
ln -d /Users/$USER/Dropbox/TweetDeck/td_26_[twitter_username].db td_26_[twitter_username].db
</p></blockquote>
</li>
</ol>
<p>Now you are ready to enjoy TweetDeck with all of your setting synchronized between machines. While I used DropBox for this solution, it is not required. Any method you have of moving the actual TweetDeck files between machines will suffice. Personally, using DropBox made it simple, efficient, and took advantage of my current workflow.</p>
