---
title: 在 Win32 把 VMware 硬碟掛載起來！
id: 300
categories:
  - 有腦世界
  - 不勞而獲
  - 不斷開發
  - 主機環境
  - 他山之腦
date: 2008-09-08 10:09:37
tags:
---

這是 VMware 官方的軟體，叫 VMware DiskMount Utilities，目前出到 5.5.0 版，不過我不知道他能不能掛載 6.0 的硬碟，因為我現在也還在用 VMware Workstation 5.5。那麼首先就先去下載 VMware DiskMount Utilities 吧，官網上我目前還找不到連結可以連過去，是後來才拿掉的，不知道原因為何，可能真的不支援 6.0 吧。
 > [http://www.vmware.com/download/eula/diskmount_ws_v55.html](http://www.vmware.com/download/eula/diskmount_ws_v55.html "http://www.vmware.com/download/eula/diskmount_ws_v55.html") 

安裝之後按「開始 / 執行 / 輸入 cmd」後執行下列語法：
 > C:\&gt; cd "C:\Program Files\VMware\VMware DiskMount Utility\"
> C:\&gt; vmware-mount x: D:\vmware硬碟路徑.vmdk 

就可以看到多了一個 X 槽，裡面就是你 vmdk 檔案的第一個 Volume 啦，如果還要掛載其他 Volume 可以在 x: 前面加上 /v:2 或 /v:3 依此類推。

也是有 GUI 的介面啦，不過我沒用過，不知道會不會有版本相容問題，可以到這裡下載：[http://petruska.stardock.net/Software/VMware.html](http://petruska.stardock.net/Software/VMware.html "http://petruska.stardock.net/Software/VMware.html")