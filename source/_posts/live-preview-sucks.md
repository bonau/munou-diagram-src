---
title: 關掉可惡的 Live Preview 了
id: 214
comment: false
categories:
  - 頭殼壞去
date: 2007-01-27 15:17:00
tags:
---

Typo 的 Live Preview 很可怕, 貼文每兩秒就會送一次 XMLHttpRequest,
然後我的 SQLite 就負荷不了了 Orz

雖然我認為這應該不是 Rails 的問題而是 Typo 的問題啦,
不過目前尚未證實,
關掉 Live Preview 的方法很簡單,
把

    app/views/admin/shared/_edit.rhtml
    `</pre>

    最後的

    <pre>`&lt;%= observe_form "#{form_type}_form",
          :frequency =&gt; 2,
          :complete =&gt; "$('preview').src = request.responseText; Element.show('preview');",
          :url =&gt; { :action =&gt; "preview" } %&gt;

其中的 &lt;%= 改成 &lt;%# 就好啦!
不過我是在用 svn 定期更新 typo,
不知道後來會不會出問題?
反正 svn 會提醒我這邊有 diff 吧?
應該沒問題啦.

應該啦.