---
title: Ruby 的缺點
id: 209
comment: false
categories:
  - 頭殼壞去
date: 2007-01-24 04:30:00
tags:
---

[![](http://farm1.static.flickr.com/154/354044811_725cf2e6a7_m.jpg)](http://www.flickr.com/photos/alphadesigner/354044811/)

圖：Red Rain, by [NeverB4Breakfast](http://www.flickr.com/photos/alphadesigner/)

Ruby 用到現在, 也有三年餘了, 從一開始被他的 Iterator 震懾,
然後被他的 Pure-OO 概念吸引, 到現在發現了不少缺點,
不管是語法上, 架構上, 實作上, 都有諸多不滿意的地方,
而就我所知這些缺陷, Ruby 也早就試著改進, 雖然優點多於缺點,
但 Rite 推出之前, 還是不吐不快.
所以今天就讓我大快朵頤狠咬 Ruby 一口吧!

## JavaEye 的觀點

JavaEye 的這篇[罵一罵 Ruby](http://www.javaeye.com/topic/22061)
已經說了不少 Ruby 的缺點, 來總結一下吧:

1.  缺乏 Virtual Machine
2.  Unicode 支援不佳
3.  企業應用 ( 2PC, scaling problem, etc. )
4.  Library, default action 匱乏
5.  沒有編譯階段
6.  缺乏文件

Ruby 發展過快，有些缺點是難免的, 這裡也不是要幫 Ruby 說話, 不過就我所知這些問題大概都有解──沒有解的, 至少也有解釋.

1.  Ruby 已經有很多套 Virtual Machine 正在開發,
 Ruby 的理念中並不想把這種 Language 跟其他 Tools
 綁在一起, 因此這樣的設計架構是可以理解的.
2.  這是很嚴重的問題，Unicode 現在大致上已經被解決了,
 但其他 encoding 的問題並沒有太大的進展,
 不過我在這方面很弱，所以也不方便做太多 Comments (倒)
3.  Scaling 的問題一直有在改善, 這種 Full-Stack 的語言工具,
 其實都面臨同樣的問題, 不過正因為我們已經交給他們了,
 因此就請信任 Ruby 開發者們的能力吧.
 2PC 的問題倒是比較難解,
 不能以 「Ruby 的社群不在大企業」萊矇混過關,
 身為以平行處理為目標的 Ruby 而言,
 這其實有點難自圓其說, 但要更改現有架構,
 對於彈性強的 Ruby 而言, 恐怕也是有些窒礙難行.
4.  Library 早已經不缺了, 倒是品質確實參差不齊,
 管理上雖已有 RubyGems 了但還是不方便,
 而且 RubyGems 也還在 0.9.x 的開發階段,
 但是面對現有的 Gems, 要更改架構我看也相當困難吧.
5.  Ruby 這種直譯式語言本來要 Compile 就會有點困難,
 天曉得你下一步會往哪裡去? 變數有沒有定義根本無從知道,
 不過對於強型態的語言來說, 沒能 Compile 確實有點詭異.
6.  文件啊… 這也是 Ruby 一直以來的痛, 倒也不是不齊全,
 其實文件數量很夠, 但是由於發展過為迅速,
 導致於很多今天才寫出來的 document, 可能明天就不適用了,
 關於這點我認為 Ruby 需要一套更完善的文件系統,
 metadata 當然也要儘量描述,
 這份文件到底是適用於哪個版本的軟體,
 免得牛頭不對馬嘴.

## 我的觀點

那問題到底出在哪裡呢? 就我而言, Ruby 在語法上有幾個我看不慣的地方:

1.  Iterator indicator delimit

     這東西不確定是好是壞, 不過我就是看那幾個 |a, b| 不順眼,
 後來想想這可能是為了要方便某些場合下可以一行秒殺的程式,
 但是為了這點就要多按兩次 shift 更令人難過.
2.  Overloading 醜斃了

     我的媽, 哪有人 method 裡面的 overloading 都用 .is_a?
 在實作的? 不僅不美觀又不實用, 打起字來又特別費力,
 氣死人了.
3.  預設用 underscore, 也很醜

     不過這是個人習慣問題, 像我就比較喜歡 camel 型態,
 toSym 比 to_sym 要來得經濟划算多了, 看起來也不會多吃力.

架構上:

1.  Install libraries 需要 administrator/root 權限

     雖然 RubyGems 成功模仿 CPAN 架構,
 但希望能更進一步區分哪些 libs 不需要 root 權.
 很多 libs 明明不需要裝在 /usr/lib/
 卻還是沒辦法輕鬆在自己的 work directory 使用這些 libs.
2.  過度包裝

     require 'iconv' 之後還得 include Iconv,
 這雖然比較保險啦, 但是一想到不 include 就得用
 Iconv.iconv() 來 call method 就不禁覺得有些好笑.

實作上也有令人流淚的悲傷:

1.  有時縮寫有時不縮寫

     to_s 這種縮寫實在很詭譎, 誰知道 s 是指什麼啊?
 既然是要讓程式碼變得更易於閱讀,
 那麼 「知其所指」 應該是非常基本的.
2.  Overloading again

     忘記從哪一版開始, 「string」 + fixnum
 竟然會產生 TypeError,
 這是要使用者自己定義 operator overloading 的意思嗎?
3.  Meta-meta-programming

     Ruby 雖是我目前看過最漂亮的語言, 但也是最暴力的語言!
 怎麼可以有個 Tool 能發展至今, 底層卻依然充滿了 eval 呢?
 就連新興的 Gems 也一樣, 動不動就使用 eval.
 幸虧這些 developer 都有一定功力,
 不至於發生太嚴重的 Injection 災情, 但天有不測風雲,
 Ruby 也有摔破的一天, 這樣惡搞, 安全性令人質疑.

這時候就會很恨自己平常沒有記下缺陷的地方, 因此這些缺陷也是講得零零散散, 有待大家把它補齊吧! 大家一起為新世代的程式語言一起努力.