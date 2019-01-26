---
layout: post
title: Edit JS And CSS Without Rebuild In Visual Studio
date: '2014-07-07 22:13:23'
tags:
- visual-studio
- windows
- web-development
---

I came across an issue when starting a new project in Visual Studio where I would edit a CSS, JS, or razor view file and in order to view the changes in the browser I *had* to rebuild the entire project. By default Visual Studio should be aware of the change and you should be able to refresh the browser sans-rebuild. It had worked before, but for new projects was an issue.

**TL;DR**

When developing in Visual Studio inside a Windows VM, do not save your project to a networked, mirrored, or shared drive in order to prevent issues with detecting file changes.

**Full Explanation**

After many hours of scouring the web I did not find the answer, but I eventually figured out what the issue was.

I was running Windows in a VM using VMWare Fusion and I had my documents folder mirrored with that of my Mac. I saved the new project in this folder, which was then accessible to OS X. Due to the way that VMWare handles this mirroring/mapping of the folders, Visual Studio was unable to detect any file changes.

Solution: either disable folder mirroring or save your project somewhere on the C: drive that is only accessible to Windows.

I hope if you find this you'll save yourself hours of hairpulling.

