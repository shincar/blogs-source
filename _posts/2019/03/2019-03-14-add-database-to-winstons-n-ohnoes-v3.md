---
layout: post
title: "用Google Cloud Datastore做為Winstons & Ohnoes的資料庫"
date:   2019-03-14 02:00:00 +0800
categories: HTML boardgame.io GCP
permalink: /:year-:month-:day-:title
comments: true
author: adam
---
 完成大廳功能之後，就很高興的找了幾個同事朋友試玩。原本玩的好好的，卻會突然沒反應。晚上跟Alvin玩的時候，又遇到一樣的斷線問題，只好又花點時間看看是什麼問題。發現原來是Google Cloud Platform裡的Google App Engine會在流量高的時候，自動增加伺服器。白話文就是多搬一台電腦出來給你用，跑一樣的程式。這樣才不會大家都用同一台電腦一起玩，網路會塞車。

 對我原本的程式，把所有的遊戲資料能存在記憶體裡，如果多台伺服器一起跑，就變成看運氣，兩個玩家要剛好都用同一台伺服器上搭上線，才不會有問題。如果玩家一開了一場遊戲，被分配到伺服器A，玩家二進網站的時候，Google把他分配到伺服器B。這兩個人就注定遇不到彼此了。Orz

 為了解決這個問題，只好開始研究資料儲存。在boardgame.io的原始碼中，我看到他有支援[mongodb][mongodb]、[firebase][firebase]。兩個我都不熟，都要從頭學起。後來選了firebase，想說是Google新一代的專案服務。結果早上起床花了一兩個小時，弄好之後卻有變多連線上的問題。加上之前有一咪咪用[Google Cloud Datastore][google-cloud-datastore]的經驗。所以後來就決定自己寫一個資料庫的元件給boardgame.io用。

開放源始碼最大的好處就是完全可以掌控程式，只要有耐心，一定能找到要怎麼修改能做到你要的功能。之前為了把game server架起來，就看過server端的code的位置。這次要加資料庫，也是在src/server/db/裡就看的到要怎麼運作啦！隨便選一個db，例如：mongo.js，把實作的部分都去掉，比較清爽。就像C++的header file一樣乾淨。

要實作的部分有
- constructor()
- connect()
- set()
- get()
- has()
- remove()
- list()

看來不是太困難。接著就是看Google Cloud Datastore，加上不停的google。把每一個方法都作出來。然後再串到原本的Server class，把db丟到宣告裡，就會自動取代原本的資料庫元件囉！

[點我玩Winstons & Ohnoes！][winstons-and-ohnoes-v3]

看到這好像寫的很輕描淡寫，其實也是有遇到很多小眉角。寫在下面如果以後有遇到需要回想的時候，可以回來看。
- Google Cloud Datastore不允許寫入像[[],[],[],[]]的資料。當初的game.js裡面有用到類似的結構。我的解法是把它改成[{'0': []}, {'1': []}, {'2': []}, {'3': []}]，錯誤的說明是list_value cannot contains another list_value之類的。
- Datastore在查詢時，如果要拿key，要用Datastore.KEY來當欄位名稱。然後runQuery()的回傳值，要用results[0]，拿到的才是查詢回來的陣列資料。所以要拿Key是要用results[0].forEach(entity)，才能在entity裡拿到。


[winstons-and-ohnoes-v3]: http://shincar.appspot.com/
[mongodb]: https://www.mongodb.com/
[firebase]: https://firebase.google.com/?hl=zh-TW
[google-cloud-datastore]: https://cloud.google.com/nodejs/getting-started/using-cloud-datastore?hl=zh-tw
