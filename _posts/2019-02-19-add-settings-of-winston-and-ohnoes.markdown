---
layout: post
title:  "Winson & Ohnoes的改版事項"
date:   2019-02-19 08:00:00 +0800
categories: HTML ProcessJS
permalink: /:year-:month-:day-:title
author: adam
---
跟老婆、Alvin玩了很多次[Winston & Ohnoes][winston-and-ohnoes]之後，發現先手優勢確實蠻大的，所以有了改動規則的念頭。另外，分享到ptt之後，也得到一些建議。列在下面當TODO List，以免忘記。

**ToDo List:**
- 加入全螢幕畫面。
- 加入網路對戰功能。
- 加入設定頁面。可以設定每個人能使用的棋子大小、數量。
- 加入電腦對戰功能

**全螢幕畫面**

目前已經完成，在主畫面上有個Fullscreen的按鈕，按下之後會帶到全螢幕版型的遊戲畫面。由於技術還沒有很好，只能堪用。請大家將就一下。

**網路對戰功能**

要學習[socket.io][socket.io]，另外，要把遊戲host在可以跑server side javascript的伺服器。可能會放在[google cloud platform][google-cloud-platform]。看來不是短時間能做出來的功能。Orz

**設定頁面**

主要是先手優勢大，要改善這遊戲的平衡，只好從棋子的大小和數量做起。後來轉念一想，讓棋子大小和數量可以設定，大家就可以依照自己的喜好做調整，自己的遊戲自己設。之後可能還可以設定要3x3、4x4、5x5之類的。

**加入電腦對戰功能**

一個人的時候，自己玩兩個人覺得有點孤單。剛好對AI也有點興趣，找時間也來研究一下這個功能。

[winston-and-ohnoes]: https://shincar.github.io/games/WinstonNOhnoes.html
[socket.io]: https://socket.io/
[google-cloud-platform]: https://cloud.google.com
