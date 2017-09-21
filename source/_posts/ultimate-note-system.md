---
title: 終極筆記系統
id: 230
comment: false
categories:
  - 頭殼壞去
date: 2007-07-28 20:34:00
tags:
---

# Ultimate Note

此專案尚未 Materialize，可能的實作方式是寫成 Web Service，
然後提供 API 方便其他 Application 使用.

累加形容詞 =&gt; :
指定形容詞 =&gt; =

## Basic Description

    user1# polarpolar:munou   ←提示字元# input
    polarpolar: munou         ←Output
    user1# pc035860:munou
    pc035860: munou
    user1# Almond:munou
    Almond: munou
    user1# .find munou
    polarpolar, pc035860, Almond

    user1# pc035860:superman
    pc035860: munou, superman
    user1# .find munou
    polarpolar, pc035860, Almond

    user1# polarpolar=smart
    polarpolar: smart ←munou 屬性不見了
    `</pre>

    ## Detail Description 1

    <pre>`user1# polarpolar university=NCCU
    polarpolar: smart
      university: NCCU
    user1# polarpolar university id=0806449
    polarpolar: smart
      university: NCCU
        id: 0806449

    ; ←註解符號 (MASM？！)
    ; 這時候發現 NCCU 錯了，應該是 FJU 才對
    ; 不過我們很可能忘記曾經輸入 NCCU 的紀錄
    ; 結果學號會 Lost 掉
    user1# polarpolar university=FJU
    polarpoalr: smart
      university: FJU

    ; 若改成這樣
    user1# polarpolar university==FJU
    polarpoalr: smart
      university: FJU
        id: 0806449

    ; 嘖嘖，好像很奇怪，上課想一下好了 XD
    