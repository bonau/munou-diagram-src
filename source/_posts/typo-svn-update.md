---
title: Typo update problem &amp; solution with Subversion
id: 233
comment: false
categories:
  - 頭殼壞去
date: 2007-07-29 22:28:00
tags:
---

If you update Typo with Subversion and get the error message below:

    svn: Working copy 'tmp/cache' is missing or not locked
    `</pre>

    The way to solve it looks a little bit silly:

    <pre>`rm -rf tmp/cache/; svn up

Nevertheless,
I find out that I only have to remove tmp/cache/ once.
And it makes everything back to the right track.
I make another checkout
in order to check if the problem occurs on every case,
but it does not happen.

I have no idea how this situation will happen again.
However, the solution is not so tricky, huh?