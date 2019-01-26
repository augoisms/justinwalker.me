---
layout: post
title: Set iChat status to current track in Spotify with AppleScript
date: '2012-03-20 16:20:45'
tags:
- applescript
- ichat
- mac-os-x
- spotify
---

![](/content/images/2014/May/ichat-status-current-spotify-track.png)

For years now I have really enjoyed the feature that lets you automatically set your iChat status to the current iTunes track.  These days, however, I find myself using Spotify more and more.  A while back I looked into this and found a few posts on how to do it, but it looked rather difficult.  Today I decided to sit down and figure it out.

The script I came up works the best for me.  I was looking for the status message to not only have the title and artist of the current track, but also a link that someone could click to launch that track in spotify.  Something I might experiment with in the future is using an application URL instead of a web url.  An application URL would launch spotify directly.  They usually look like "spotify:track:trackid" I just need to figure out if iChat would still register this as a clickable link.

If you have a suggestion on how it could be impletmented better, let me know.  This is my first dabble in AppleScript.  I didn't realize how powerful AppleScript it.  I'm looking forward to future projects using it.

You can download the code at <a href="https://github.com/augoisms/Set-iChat-status-to-current-Spotify-track" target="_blank">github</a>.