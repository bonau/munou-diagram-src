---
title: Mandriva Linux 編輯 MIDI 攻略
id: 285
categories:
  - 我愛音樂
  - 有腦世界
  - 桌面環境
date: 2008-08-25 20:49:21
tags:
---

<pre>  # [懶人快速安裝法]
  # (註：我用的是 cooker 套件庫)
  #
  # 先下載 http://www.alsa-project.org/~james/sound-fonts/8MBGMSFX.SF2
  sudo urpmi fluidsynth jackit qsynth rosegarden
  jackd -d alsa # 啟動 jack audio server

  qsynth        # Setup / 進入 Soundfonts 頁面 / 開啟 8MBGMSFX.SF2 / 按下 OK
  rosegarden    # 做音樂囉！</pre>
Rosegarden 是一款不錯的 MIDI Sequencer 軟體，不過之前在使用 Linux 的時候 MIDI 的設定可說是相當的麻煩，而且又缺少好的音源，實在有點可惜。在這裡要分享一下如何在 Mandriva Linux 編輯 MIDI 又可以即時播放的撇步。

要安裝軟體音源則要安裝 fluidsynth：
<pre>sudo urpmi fluidsynth</pre>
這套軟體是管理 SoundFont 的 client command 軟體，
他需要透過 jack audio server 來運作，
而由於 Mandriva One 預設有安裝 jackd，
所以就可以不用裝了。
如果您的系統沒有 jack audio server 的話，
請用下列指令安裝：
<pre>sudo urpmi jackit</pre>
注意喔，不是 jack，那是一個 Python 的音效相關介面，
裝了也沒用的啊，哈哈哈。

為了方便，再安裝一個 GUI frontend 叫做 Qsynth：
<pre>sudo urpmi qsynth</pre>
要使用 fluidsynth 或 Qsynth 來為您的系統增加 SoundFont 音源之前，
必須先啟動 jackd，假設使用者的系統使用的音效驅動為 ALSA：
<pre>jackd -d alsa</pre>
選項 -d 後面也可以加上 oss, dummy, etc.
不過我跟這些 driver 沒有很熟，
所以聲音都播不出來 囧，
建議先用 ALSA 試試看吧，
其他的我改天研究。

然後啟動 Qsynth，看是你要用 Application Menu 還是要用終端機輸入 qsynth 都可以，正常的話應該會出現一個控制面板，過了兩三秒之後他就會自己啟動一個 Qsynth1 的元件。

這時候按下視窗左方的 Setup 按鈕，又跳出一個視窗，切換到 Soundfonts 那一頁，按下 "Open..." 打開你要的 *.sf2 檔案，如此即可讓 Rosegarden 發出動人的 MIDI 聲音，<span style="color:red;">若您沒有適當的 SoundFont 檔案，可以使用 ALSA Wiki 網站的[免費 8MB SoundFont](http://www.alsa-project.org/~james/sound-fonts/8MBGMSFX.SF2)</span>(雖然版權好像是 Creative 公司的，哈！)，最後再按下 OK 就可以了。

最後當然就是安裝 MIDI 編輯軟體--Rosegarden：
<pre>sudo urpmi rosegarden</pre>