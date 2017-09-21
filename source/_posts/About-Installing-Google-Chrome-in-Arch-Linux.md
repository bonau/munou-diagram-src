---
title: About Installing Google Chrome in Arch Linux
tags: []
date: 2012-01-20 18:33:00
---

**<span style="font-size: x-large;">If you choose Chromium&#8230;</span>**
It&#8217;s easy to install Chromium, the most powerful browser from Google, in Arch Linux. Just make sure you have enabled &#8220;extra&#8221; repository in /etc/pacman.conf and type:

$ pacman -S chromium

all things done.

**<span style="font-size: x-large;">If you&#8217;d like to install Google Chrome Stable&#8230;</span>**
However, if you&#8217;d like it more stable, you can take a look in [AUR](https://aur.archlinux.org/). Of course it&#8217;s not provided by Arch Linux&nbsp;officially. The package I use is here:

<span style=""><span style="color: #6c83b0; font-family: 'Bitstream Vera Sans', 'Lucida Grande', Arial, sans-serif; font-size: 14px; font-weight: bold;">google-chrome 16.0.912.75-1 by&nbsp;</span><span style="color: #888888; font-family: 'Bitstream Vera Sans', 'Lucida Grande', Arial, sans-serif; font-size: 14px; font-weight: bold;">t3ddy</span></span>
[https://aur.archlinux.org/packages.php?ID=37469](https://aur.archlinux.org/packages.php?ID=37469)

Download the tarbell and untar it:

$ tar xzf google-chrome.tar.gz
$ cd google-chrome/

And then make package:

$ makepkg -s

You may see the makepkg script asking you to download required libraries. Confirm and continue. After running makepkg script, the current directory (google-chrome/) contains a few extra files, include &#8220;google-chrome-xx.x.xxx.xx-x-YOUR_ARCH.pkg.tar.xz&#8221;. Install it by pacman, for example in my case:

$ pacman -U&nbsp;google-chrome-16.0.912.75-1-x86_64.pkg.tar.xz

Confirm and install. Now you should see Google Chrome in gnome-shell (kde kickoff or something.)<div class="blogger-post-footer">![](https://blogger.googleusercontent.com/tracker/7273332692755259172-8398508615793915320?l=polar-dev.blogspot.com)</div>