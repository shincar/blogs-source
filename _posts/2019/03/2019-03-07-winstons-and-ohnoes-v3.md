---
layout: post
title:  "Winstons & Ohnoesd大改版！"
date:   2019-03-07 02:00:00 +0800
categories: HTML React Node.js GCP boardgame.io
permalink: /:year-:month-:day-:title
comments: true
author: adam
---
噹！噹！噹！最新一版的Winstons & Ohnoes出爐啦！

[點我搶先玩看看！][winstons-and-ohnoes-v3]

點選Single可以單機玩。對選Player 1可以新增一場對戰。新增成功在畫面下方會有Game ID，傳給想要對戰的朋友，將Game ID貼到Player 2的欄位按下Join就可以對戰了。目前對戰的功能使用上還沒有很方便，應該再過幾天會做出一個遊戲大廳，可以查看正在等候加入的對戰室，就會更方便啦！

自從完成Winstons & Ohnoes的網路對戰功能之後，又發給一些同學、朋友們試玩看看。結果遇到的狀況還真多。包括
- 玩一玩會斷線
- 在手機上顯示比例不佳
- 在高解析度＋高DPI的電腦上不能玩

一方面是我當初學ProcessJS的時候，一頭熱的想快速寫出一個遊戲。忽略了前期的規畫。加上對網路程式的不熟悉，越寫就發現越麻煩。種種原因讓我興起改架構的念頭。這次改動主要想要達成
- 遊戲的邏輯跟遊戲介面能獨立開來
- 介面要能簡單的做出手機與電腦都能使用的版型
- 介面的改動要容易，之後要擴充功能重覆使用原本的元件

照例請出Google大神，果然找到一個設計良好的boardgame架構元件。名字淺顯易懂，就叫[boardgame.io][boardgame-io]，在github裡的範例剛好是Tic-Tak-Toe(就是OX遊戲)。照著指令把範例跑起來之後，看來蠻舒服的。接著就是把它的範例改成Winstons & Ohnoes的規則，就完成文字版的Winstons & Ohnoes v3啦！

作者的目標應該是在設計遊戲邏輯的時候，幾乎可以完全不寫多餘的程式碼，這點我在剛開始用的時候，還摸不清楚。等到了解越多之後發現真的可以不用寫。另外，還看到裡面內建了socket.io，代表網路對戰也不是問題。讚啦！

完成文字版的Winstons & Ohnoes之後，就是把介面的部分做出來讓遊戲邏輯套上去。在看Tic-Tak-Toe範例時，發現作者用的是一個叫[React][react]的Javascript架構，由Facebook為主力開發維護。這又勾起我多年前工作時的回憶。React是那個專案用的架構。當年那個客戶就是Facebook XD 想不到那時問題多多的架構如今已經成為一方之霸。跟AngularJS、VUE並列一線Javascript UI framework。用起來很神奇，而且開發工具做的很不賴。開啟之後，每當你的程式有變動，就會觸發瀏覽器刷新讓你看結果。非常貼心！之後如果有機會再專文介紹。（其實是自己也還不熟～ 哈）

等到Winstons & Ohnoes做的差不多的話，下一個目標來試試卡卡頌或是馬尼拉好了～ 拜拜

[winstons-and-ohnoes-v3]: http://shincar.appspot.com/
[boardgame-io]: https://boardgame.io
[react]: https://reactjs.org/
