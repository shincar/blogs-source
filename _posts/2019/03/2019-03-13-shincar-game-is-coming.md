---
layout: post
title:  "打造一個線上board game平台 - Part 1"
date:   2019-03-13 02:00:00 +0800
categories: HTML shincar-game
permalink: /:year-:month-:day-:title
comments: true
author: adam
---
為了幫Winstons & Ohnoes打造一個遊戲大廳，又帶出我另一個想法（人生就是一直充滿變化），何不寫一個能夠讓我一直加入新遊戲的通用大廳？把[Think in React][think-in-react]看完之後，我認真的覺得要弄出一個大廳不會太困難。只要先規畫好前端要秀出來的元件，再一個一個完成，應該能在有生之年完成。要完成任何事的先決要件就是動起來，把一件大事切成很多件小事。一件一件完成，最後就會完成了。

所以第一件事就是規畫第一版的遊戲大廳。想一想我的大廳要是什麼樣子。

**大廳元件**
- 頁首（header)
- 頁尾（footer）
- 側欄（sidebar）
- 主畫面（main-contain）
- 聊天室（chat-room）

頁首跟頁尾很單純，側欄跟主畫面須要再細部規畫一下。

**側欄**

側欄目前想要提供的列表有
- 使用者設定
- Winstons & Ohnoes

這樣之後進大廳後，USE CASE應該是先到使用者設定頁面，輸入遊戲使用者名稱，然後點Winstons & Ohnoes裡面會要開房間跟目前的遊戲房列表。

**主畫面**

使用者點選側欄後，內容就會秀在主畫面裡。例如：點選使用者設定，就會跑出介面讓使用者改遊戲使用者名稱；點選Winstons & Ohnoes就進到遊戲主畫面。

**聊天室**

目前先只提供大廳模式，所有的人都可以在裡面打字聊天。可以最小化，以後再擴充。

[think-in-react]: https://reactjs.org/docs/thinking-in-react.html
