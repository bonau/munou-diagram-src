---
title: 果然猜不透 FastCGI
id: 200
comment: false
categories:
  - 頭殼壞去
date: 2006-10-19 10:50:00
tags:
---

我不懂，為什麼 dispatch.cgi 就可以正常運作，但是一換成 dispatch.fcgi 就會吃鱉呢？

我參考[這篇](http://andrewhocoo.blogspot.com/2006/02/rails-apache-cgifastcgi-on-windows.html)的作法，將 Apache2 設定完成，cgi 模式可以跑得很正常，但是就如大家所知──慢到令人拷貝。於是我把 .htaccess 下面這行

> RewriteRule ^(.*)$ dispatch.cgi [QSA,L]
>     `</pre>

    換成

    > <pre>`RewriteRule ^(.*)$ dispatch.fcgi [QSA,L]

嗯，啟動首頁果然快很多，大概兩三秒就 Fully loaded 了，可是呢？當我要進 admin 介面的時候，卻發現 dispatch.fcgi 的原始完整的呈現在我面前，於是我開始懷疑首頁到底是怎麼產生的？是不是只是 Apache restart 的時候沒清 cache？我動手把 cache 清除後再次 restart，奇怪，還是一兩秒就 loaded 了，進入 admin 也還是會顯示 dispatch.fcgi 原始碼，這讓我再度開始懷疑，該不會其實 dispatch.cgi 就沒能好好運作吧？我再次將 RewriteRule 換成 dispatch.cgi，咦？明明就是正常的！

這真是令人火冒八丈，原始檔既然顯示出來，也就是說這根本沒有經過 FastCGI，就直接當 text/plain 輸出了，於是我做了幾個考慮

1.  **FastCGI 有可能安裝失敗**。但首頁是怎麼回事？如果說是 FastCGI 裝錯了，應該連首頁也是會顯示原始檔才對啊
2.  **RewriteRule 寫錯了**。可是 dispatch.cgi 都可以正常運作啊，所以也初步排除這個可能性，[QSA, L] 也寫了，沒道理......

結果寫到這裡，我發現我在 /etc/conf.d/apache2 裡面忘記加上 -D FASTCGI，原來是個腦殘錯誤 = =

可是這樣的話，我清了 server 跟 client 端的 cache，如果沒有 load mod_fastcgi 的話，那麼首頁又是怎麼產生的呢？太玄疑了。