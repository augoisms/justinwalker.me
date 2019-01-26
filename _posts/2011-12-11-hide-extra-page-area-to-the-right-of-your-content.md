---
layout: post
title: Hide extra page area to the right of your content
date: '2011-12-11 18:15:46'
tags:
- center
- css
- extra-space
- overflow
---

This is an issue that I've had for quite some time that would pop up here and there. In some cases I was never able to figure it out.  This issue:  an extra 500px or more of background space would be placed to the right of my content when I would design a page with centered content. The content would be perfectly centered in the window, but the extra space would exist, complete with scroll bars.  It turns out that it was an issue with overflow on the x-axis.
<pre><code>body { overflow-x:hidden; }</code></pre>
My page now maintains the width of the browser windows. Check out <a href="http://www.w3schools.com/cssref/css3_pr_overflow-x.asp">this article</a> for info on the different usage options.