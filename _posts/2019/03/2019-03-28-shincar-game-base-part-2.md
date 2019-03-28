---
layout: post
title:  "打造一個線上board game平台 - Part 2"
date:   2019-03-28 02:00:00 +0800
categories: HTML shincar-game
# permalink: /:year-:month-:day-:title
comments: true
author: adam
---
有了計畫要寫一個通用的遊戲大廳之後，就開始想像整個流程。一個玩家進到大廳，網站就需要他輸入使用者名稱。不管是在聊天室裡打屁，還是開遊戲對戰室，都會有這個需求。之後如果要新增一些功能，遲早要建立使用者管理系統。那就趁早在規畫時期把地基打穩吧！

在做[Winstons & Ohnoes][winstons-and-ohnoes-v3]的網路對戰功能時，把後端資料庫掛在Google Cloud Datastore上。那時就有看到[Google Firebase][google-firebase]。但是當時看了一下實作的細節，覺得好像要花一些時間了解才比較能上手，所以就回頭去用舊有的Google Cloud Datastore先完成再說。效果確實也不錯。

這次要寫個通用大廳，加上我對網路程式設計的了解越來越多，所以決定用Firebase來實作。一方面是Google目前正在強推，所以開發重心都在這，除了Firestore、Realtime Database之外，Firebase還支援帳號管理的大部分基礎功能。例如：
- 註冊新使用者
- 登入驗證
- 修改密碼
- 寄出重設密碼的電子郵件

大幅降低建置網站的時間。註冊新使用者的部分，還能直接整合Google、Facebook、Twitter帳號，直接讓使用者以原有的帳號登入，也是一大方便。

實作的部分，我基本上是參考[這篇][A-Firebase-in-React-Tutorial-for-Beginners]的步驟。我沒有買書，完全是看React文件跟一些網路上的範例邊學邊做，所以一直處在一知半解的狀況。看了[Think in React][think-in-react]之後，雖然是對React的設計哲學有較多的理解，但都沒有看到Best Practice的文章。

[這篇][A-Firebase-in-React-Tutorial-for-Beginners]文章的步驟跟網站元件的架構都很值得參考。從一開始就把每個元件分資料夾放。讓元件各自獨立，你會更注意每個元件的用法。另外一個好用的pattern是recompose這個package。讓元件可以直接用compose的方式，擁有某項能力。例如：
- withRouter():可以讓元件能直接跳轉到其他URI
- withFirebase()：可以讓元件有能力對Firebase資料庫操作
- withAuthentication()：可以驗證使用者是不是Firebase資料庫裡的使用者。
- withAuthorization(): 可以騤證使用者有沒有權限瀏覽某些頁面。

完成使用者管理的功能之後，[Adam & Alvin的遊戲基地][shincar-game-base]就成型了。

複習一下，當初的規畫。

**大廳元件**
- 頁首（header)
- 頁尾（footer）
- 側欄（sidebar）
- 主畫面（main-contain）
- 聊天室（chat-room）

現在改成：

**大廳元件**
- 頁首（AppBar)
- 頁尾（Footer）
- 側欄（Menu）
- 主畫面（main-contain）
- 聊天室（chat-room）

頁首由AppBar取代，側欄的部分也在AppBar上可以搞定。使用者可以利用AppBar進行註冊、登入、進大廳主畫面等等動作。Part 3的目標是把聊天室做出來。可能會跟頁尾做結合，把它Dock在網頁的下方。可以展開跟縮小。等聊天室完成，再把Winstons & Ohnoes掛上來。再重新把網路對戰的功能改的更方便一點。今天就到這啦！


[winstons-and-ohnoes-v3]: https://shincar.appspot.com/
[google-firebase]: https://firebase.google.com
[A-Firebase-in-React-Tutorial-for-Beginners]: https://www.robinwieruch.de/complete-firebase-authentication-react-tutorial/
[think-in-react]: https://reactjs.org/docs/thinking-in-react.html
[shincar-game-base]: https://shincar-game-base.firebaseapp.com
