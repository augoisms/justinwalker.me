---
layout: post
title: Simple forms authentication for Azure Websites
date: '2015-02-13 22:16:14'
tags:
- iis
- azure
- authentication
- bootstrap
---

I needed a way to password-protect a staged version of a project I was working on that was up on azure websites. Normally I would use an `.htpasswd` but that doesn't work on IIS. I found gist that someone had put together that was using forms authentication and I made it all bootstrappy.

Just place both files in the root of your project.

![bootstrap login form](/content/images/2015/02/bootstrap-auth-1.png)

<script src="https://gist.github.com/augoisms/4e6e2506a366a848d3b3.js"></script>