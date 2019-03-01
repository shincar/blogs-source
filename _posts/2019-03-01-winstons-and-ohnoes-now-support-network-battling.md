---
layout: post
title:  "Winstons & Ohnoes現在支援網路對戰囉！"
date:   2019-03-01 02:00:00 +0800
categories: HTML GAE ProcessJS GCP Node.js soket.io
permalink: /:year-:month-:day-:title
comments: true
author: adam
---
經過幾天的努力，現在Winstons & Ohnoes終於可以支援網路對戰啦！萬歲！
![主畫面]({{site.baseurl}}/images/WinstonNOhnoesv2_main.png){:width="500px"}

玩法是點選網路對戰，進入對戰資訊頁面。填入一個對戰室名稱跟玩家大名之後，按下加入按鈕。

![對戰資訊畫面]({{site.baseurl}}/images/WinstonNOhnoesV2_BattleInfo.png){:width="500px"}

如果對戰室名稱不存在，就會新增一個對戰室。然後進入等待畫面。

![等待畫面]({{site.baseurl}}/images/WinstonNOhnoesV2_Waiting.png){:width="500px"}

第二位玩家一樣進入對戰資訊頁面，輸入同一個對戰室名稱和玩家大名之，按下加入按鈕。

![對戰資訊畫面]({{site.baseurl}}/images/WinstonNOhnoesV2_Player2.png){:width="500px"}

伺服器收到訊息之後，如果有同一個對戰室的對手已經在等待，就會進入遊戲主畫面。

![遊戲主畫面]({{site.baseurl}}/images/WinstonNOhnoesV2_Game.png){:width="500px"}

第一個新增對戰室的人為玩家一，後加入的人為玩家二。左上角顯示的是目前輪到哪個玩家。之後的規則就跟原本的一樣啦！
如果不熟，可以參考這篇[Winson & Ohnoes][winston-and-ohnones]

另外，如果新增對戰室時，伺服器已經有同一個對戰室名稱存在，且已經在對戰，則會回傳"對戰室已滿，換個名稱吧！"

![遊戲主畫面]({{site.baseurl}}/images/WinstonNOhnoesV2_BattleFull.png){:width="500px"}

這時可以按下取消，換個名字再加入對戰室哦！祝大家玩的愉快！如果有什麼建議歡迎留言告訴我哦！ :)

[winston-and-ohnones]: https://shincar.github.io/blogs/2019-02-15-winston-and-ohnoes
