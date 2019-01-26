---
layout: post
title: Better than an alias. Create a symbolic link in Mac OS X
date: '2012-02-28 13:14:25'
tags:
- alias
- dropbox
- mac-os-x
- mamp
- sym-link
- symbolic-link
- terminal
- unix
---

I've been familiar with creating aliases in OS X, and they usually work pretty well for me.  Recently, however, I was working on a project where a friend has shared a root folder of a website with me via dropbox.  This folder now lives in my dropbox, but I need it to be in my htdocs folder for use with MAMP.  Obviously I could just copy it over, but I wanted to keep the working files in Dropbox so that whenever I made any changes, my friend would always have the most up to date files.  I tried creating a normal alias by right-clicking on the root folder, but even though I moved that alias into my htdocs folder, MAMP would not connect to any of the files.

After doing some Google searching I found my solution in a symbolic link.  I used these two articles for reference: <a href="http://techpatterns.com/forums/about1841.html" target="_blank">Tech Patterns</a>, <a href="http://hints.macworld.com/article.php?story=2001110610290643" target="_blank">MacWorld</a>.

A symbolic link is similar to an alias that you create within the OS X Finder, but it provides a deeper connection in the underlying file system.  To create a symbolic link, fire up Terminal and type in the following code:
<pre style="white-space: pre-wrap;"><code>ln -s <span style="color: #ff0000;">/users/Justin/Dropbox/website-root</span> <span style="color: #0000ff;">/users/Justin/Applications/MAMP/htdocs/website-root</span></code></pre>
This creates the following connection: <span style="color: #0000ff;">Blue file path</span>  points to  <span style="color: #ff0000;">Red file path</span>

Note that there is a space in between the two file paths. The first file path is the path to the folder or file you want to point to. The second path is where you want to create the symbolic link. This code will create a symbolic link in my htdocs folder that points to the folder "website-root" in my Dropbox. Determining file paths can be a little tricky, so instead of trying to figure out what the path is, simply drag the target and destination folder into the terminal window, and the path will be automatically generated.

Hopefully this works for you.  If I've missed something let me know, but this should get the job done.