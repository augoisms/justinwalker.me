---
layout: post
title: Jekyll Slow On Windows
date: '2018-07-31'
---

Compiling a simple jekyll site on Windows was painfully slow, where as the same site on my Mac was super quick. Took me a bit to find the solve, but it was simple:

```bash
gem install wdm
```

Source: <https://github.com/jekyll/jekyll/issues/4103#issuecomment-160137585>