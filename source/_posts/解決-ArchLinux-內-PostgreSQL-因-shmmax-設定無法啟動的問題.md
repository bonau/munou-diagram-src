---
title: 解決 ArchLinux 內 PostgreSQL 因 shmmax 設定無法啟動的問題
tags: []
date: 2012-01-25 11:42:00
---

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Hq2C6FYVwF8/Tx95ktvy8UI/AAAAAAAAD8c/EHdvlKtIVCk/s400/PostgreSQL-9.gif)](http://2.bp.blogspot.com/-Hq2C6FYVwF8/Tx95ktvy8UI/AAAAAAAAD8c/EHdvlKtIVCk/s1600/PostgreSQL-9.gif)</div>
上次更新後，重新啟動電腦時 PostgreSQL service 發生錯誤，
看到 /var/log/postgresql.log 裡面有這些東西：

<div>LOG:  received smart shutdown request
LOG:  autovacuum launcher shutting down
LOG:  shutting down
LOG:  database system is shut down
FATAL:  could not create shared memory segment: Invalid argument
DETAIL:  Failed system call was shmget(key=5432001, size=41279488, 03600).
HINT:  **This error usually means that PostgreSQL&#8217;s request for a shared memory segment exceeded your kernel&#8217;s SHMMAX parameter. ** You can either reduce the request size or reconfigure the kernel with larger SHMMAX.  To reduce the request size (currently 41279488 bytes), reduce PostgreSQL&#8217;s shared memory usage, perhaps by reducing shared_buffers or max_connections.
        If the request size is already small, it&#8217;s possible that it is less than your kernel&#8217;s SHMMIN parameter, in which case raising the request size or reconfiguring SHMMIN is called for.
        The PostgreSQL documentation contains more information about shared memory configuration.
LOG:  database system was shut down at 2012-01-25 03:53:18 CST
</div>
根據粗體字貼心的提醒，可以先來更改系統設定：

$ sysctl -w kernel.shmmax=134217728

再重新啟動 PostgreSQL 就大功告成：

$ rc.d start postgresql

但這個設定重新開機之後就沒了，所以還要寫入系統設定檔裡

$ echo &#8216;kernel.shmmax = 134217728&#8217; >> /etc/sysctl.conf

<div class="blogger-post-footer">![](https://blogger.googleusercontent.com/tracker/7273332692755259172-2666709530526127847?l=polar-dev.blogspot.com)</div>