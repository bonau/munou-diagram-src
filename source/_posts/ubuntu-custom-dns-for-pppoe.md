---
title: Ubuntu custom DNS for PPPoE
tags:
  - custom
  - dns
  - pppoe
  - ubuntu
id: 318
categories:
  - 有腦世界
  - 主機環境
date: 2010-04-07 06:05:14
---

I've found that whenever I dial up PPPoE
the /etc/resolv.conf will be rewritten
so that name server is always set as ISP's default DNS.
However, it's affected by the configuration of PPPoE.
Now we'll try to solve this.

<pre>
$ sudoedit /etc/ppp/peers/dsl-provider
</pre>
find:
<pre>
usepeerdns
</pre>
change it to:
<pre>
#usepeerdns
</pre>

Then feel free to edit /etc/resolv.conf.
PPPoE will not overwrite your settings anymore.