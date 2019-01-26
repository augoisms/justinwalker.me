---
layout: post
title: CSS - Full Page Fixed Background on iOS
date: '2014-07-07 23:23:27'
tags:
- css
- web-development
---

I struggled for a bit trying to get this to work on iOS. I had a background set to cover on the HTML element and on a desktop browser it worked great. The issue with iOS (and other touch screen devices) is that the background did not stay fixed and was also stretched to the total height of the content (not the viewport). 

This was the solution I came up with that worked:

```language-css
html {
	background: url('path-to-image') no-repeat top center fixed;
	background-size: cover;
	height: 100%;
	overflow: hidden;
}

body {
	height:100%;
	overflow: scroll;
	-webkit-overflow-scrolling: touch;
}
```

Depending on how you have your page set up, you might want to wrap this in a media query.