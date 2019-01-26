---
layout: post
title: OS X 10.11 Keychain - Can't Click Allow
date: '2016-03-10 21:49:55'
tags:
- os-x
- keychain
- el-capitan
---


![OS X Keychain dialog](/content/images/2016/03/Screen-Shot-2016-03-10-at-1-41-57-PM-1.png)

After upgrading to OS X 10.11 El Capitan, I noticed that when the Keychain would ask for permission I would be unable to click "Allow." I could click Deny but otherwise could not get it to authorize. Not wanting to nuke my Keychain as so many posts recommended, I resolved to just do nothing.

Today I searched again and came across this very helpful thread:

<http://apple.stackexchange.com/questions/208704/os-x-10-11-unable-to-press-allow-on-keychain-access-dialogs>

One of the comments mentioned that disconnecting the person's Wacom tablet allowed them to proceed. This turned out to be part of the solve for me! In addition to unplugging my tablet, I also had to disable all apps in my Accessibility settings.

![](/content/images/2016/03/Screen-Shot-2016-03-10-at-1-55-47-PM.png)

The likely culprits here were BetterSnapTool and Karabiner, but to save time I just unchecked them all.

It seems crazy that I would have to disconnect my tablet and disable some apps just to allow access to my Keychain. I'm hoping that Apple sees this as a bug and fixes it in an update or the next major version. Hopefully if you are having this same problem you'll find this post and it will make your day!
