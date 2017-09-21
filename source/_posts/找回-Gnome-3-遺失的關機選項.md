---
title: 找回 Gnome 3 遺失的關機選項
tags: []
date: 2012-01-08 02:52:00
---

除了 Ubuntu 自家擁有優秀(?)的 Unity 之外，近期各 Linux 發行版都陸續升級到了 Gnome 3，界面乾淨俐落，清新可人。然而忙碌了一天之後要關機時，卻遍尋不著關機的選項……。
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-CH-afycLoIQ/TwiQXTGD22I/AAAAAAAADJk/4KtsqV4vTrU/s320/%25E8%259E%25A2%25E5%25B9%2595%25E6%2588%25AA%25E5%259C%2596%25E5%25AD%2598%25E7%2582%25BA+2012-01-08+02%253A34%253A41.png)](http://1.bp.blogspot.com/-CH-afycLoIQ/TwiQXTGD22I/AAAAAAAADJk/4KtsqV4vTrU/s1600/%25E8%259E%25A2%25E5%25B9%2595%25E6%2588%25AA%25E5%259C%2596%25E5%25AD%2598%25E7%2582%25BA+2012-01-08+02%253A34%253A41.png)</div>

鎖定、切換、登出，啊怎麼只有暫停 囧 說好的關機呢？重新開機呢？就算登出了還是找不到。別擔心，其實他們都還在，只是需要多按一個 Alt 鍵而已。點開螢幕右上角，有你名字的選單後，按下 Alt 鍵，「關閉電源…」按鈕就會出現了，重新開機也在裡面。

嫌每次都要多按 Alt 太麻煩嗎？多數 Linux 發行版裡面都有這個套件：gnome-shell-extension-alternative-status-menu 以 Arch Linux 的文字界面安裝為例，以 root 權限執行：

<pre>$ pacman -S gnome-shell-extension-alternative-status-menu
</pre>
再重新登入就可以了！
<div class="blogger-post-footer">![](https://blogger.googleusercontent.com/tracker/7273332692755259172-5864629396768117441?l=polar-dev.blogspot.com)</div>