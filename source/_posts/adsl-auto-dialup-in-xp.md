---
title: WindowsXP 下 ADSL 自動撥接
id: 236
comment: false
categories:
  - 頭殼壞去
date: 2007-08-03 00:45:00
tags:
---

不久前哈比提到系統排程的問題，我忽然聯想到 WindowsXP 的系統排程好像不用登入就可以 Work，那這麼一來重開機無法自動撥接的問題就有解啦！不過在我設定三分鐘跑一次 rasdial 的時候，執行 Shell 指令就會有個 cmd 視窗出來亂，很麻煩，不但影響視線又會影響工作，就算設定不要在非閒置時工作也一樣。於是我把腦筋動到了 VBScript 身上，印象中他可以在背景執行 Shell 指令，就稍微查了一下用法，以下是 Script 內容：

    Set objShell=wscript.createObject("wscript.shell")
    objShell.Run "rasdial HiShit 8xxxxxxx@ip.hinet.net password", 0, True

其中 HiShit 是您自訂的撥號連線名稱，帳號密碼則在其後。把這個檔案存成 dialup.vbs，之後放到排程裡，設定「從 2007/08/01 起，每天從上午 09:00 起每隔 3 分鐘為時 24 小時」跑一次，另外別忘記不要勾「登入後才執行」，這樣就大功告成啦！

今天有點懶得截圖:p