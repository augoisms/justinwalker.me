---
layout: post
title: Set Messages Status to Current Rdio Track
date: '2013-03-23 18:27:39'
tags:
- alfred
- applescript
- messages
- rdio
---

![screenshot of messages status](/content/images/2014/May/messages-status-current-rdio-track.png)

Semi-recently I switched to Rdio from Spotify and in doing so I was forced to revisit my <a href="http://justinwalker.me/2012/03/set-ichat-status-to-current-track-in-spotify-with-applescript/">iChat-Spotify-AppleScript</a> post.  I have adapted the script to work with Rdio and have also made a few updates.  For one, iChat is now Messages and, of course, Spotify is now Rdio.  I also made some changes that makes the script check if Rdio is ready before attempting to retrieve the track info.  

Rdio has basic AppleScript <a href="http://developer.rdio.com/docs/read/Desktop">support</a>, but I am hoping that Rdio adds short URL support for AppleScript, but for now we'll have to survive with the long version.

You can find the AppleScript I wrote on <a href="https://github.com/augoisms/set-messages-status-to-current-rdio-track">GitHub</a>.

To run the script I am using the workflow feature of the latest version of <a href="http://www.alfredapp.com/">Alfred</a>. When I invoke Alfred, I type the keyword "status" and it launches my script.
