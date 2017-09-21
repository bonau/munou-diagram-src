---
title: SCGI solution with slow speed
id: 224
comment: false
categories:
  - 頭殼壞去
date: 2006-03-05 20:27:00
tags:
---

http://www.zedshaw.com/projects/scgi_rails/faq.html

<pre>Q:  It's really slow when I start it up and seems to leak memory.</pre>

A:  You’re running it in development mode.  You most likely configured
your processor with “-e development” so all you need to do is:

> scgi_ctrl config -M -e development
> scgi_ctrl restart

This “merges” (-M) your previous configuration with the new config
of “-e development” and then restarts your processor.

XD