---
title: 'Haml: HTML Abstraction Markup Language'
id: 212
comment: false
categories:
  - 頭殼壞去
date: 2007-01-26 08:44:00
tags:
---

[HAML project](http://haml.hamptoncatlin.com/)

http://haml.hamptoncatlin.com/

Rails 又出奇招啦, 雖然這東西早就被支援了,
不過我在更新 typo 的時候發現裝了一個 haml plugin,
還有個 theme 順勢改為 haml 來寫,
於是我翻開來看看, 哇, 好醜!

但是比 Erb 好看多了.

總之他就只是把 HTML 變成 YAML-like 的東西,
不過 HTML tag 的 prefix 竟然是 %
然後指令碼的 prefix 則是 = 

來看看程式碼

    %html
      %head
        %title= "草安您好"
      %body
        #contents
          %h1 "tyr.munou.tw"
          %ul.cast
            %li "tyr 是大神"
            %li "munou 沒腦"
            %li "tw 台灣"
        #outer= render :partial =&gt; 'sidebar'
    `</pre>

    會相當於什麼呢?

    <pre>`&lt;html&gt;
      &lt;head&gt;
        &lt;title&gt;草安您好&lt;/title&gt;
      &lt;/head&gt;
      &lt;body&gt;
        &lt;div id="content"&gt;
          &lt;ul class="cast"&gt;
            &lt;li&gt;tyr 是大神&lt;/li&gt;
            &lt;li&gt;munou 沒腦&lt;/li&gt;
            &lt;li&gt;tw 台灣&lt;/li&gt;
          &lt;/ul&gt;
        &lt;/div&gt;
        &lt;div id="outer"&gt;
          &lt;%= render :partial =&gt; 'sidebar' %&gt;
        &lt;/div&gt;
      &lt;/body&gt;
    &lt;/html&gt;

看起來不錯, 但是看久了都是奇怪符號反兒不太順眼,
因此我也沒有要詳細介紹下去的意思,
等待另一個 alternative 出現吧.