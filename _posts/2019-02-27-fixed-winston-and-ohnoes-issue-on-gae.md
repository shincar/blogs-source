---
layout: post
title:  "在Google App Engine中，Winstons & Ohnoes無法載入，原因出在PNG檔"
date:   2019-02-25 02:00:00 +0800
categories: HTML GAE ProcessJS
permalink: /:year-:month-:day-:title
comments: true
author: adam
---
原本正興高采烈的實作Winstons & Ohnoes的網路對戰功能，卻突然發現host在GAE的Winstons & Ohnoes根本沒辦法玩。比對了一下在github裡的程式碼跟在GAE裡的完全一樣，但在GAE裡的硬是load不出來。就只好開始debug了。

使用Google Chrome內建的Inspect工具，查看程式碼有沒有完整的下載成功，結果是有的。怪！看了半天都看不出來，只好用分解法，把可以簡化的宣告跟函式都先去掉。一點一點增加程式碼，看看是加到哪邊的時候會壞掉。

簡化到只畫homeScene時就壞了，算是好消息。只要能把homeScene畫出來，可能問題就解了。畫homeScene時，總共做了以下幾件事：
1. 初始化畫布
2. 畫背景
3. 畫player1.image跟player2.image
4. 畫標題
5. 畫兩個按鈕

檢查到3.時發現是image在做怪，當ProcessJS試著預載圖檔時，沒辦法成功。所以就卡在那了。
{% highlight javascript %}
/＊ @pjs preload="images/cs-winston.png, images/cs-ohnoes.png"; ＊／
{% endhighlight %}

剛好在github裡有絕對路徑的圖檔URL可以用，就拿來試試看
{% highlight javascript %}
/* @pjs preload="https://shincar.github.io/games/images/cs-winston.png,https://shincar.github.io/games/images/cs-ohnoes.png"; */
{% endhighlight %}

一試成功，結論就是它啦！終於可以繼續搞網路對戰功能了～ 嚇死老狗啊～

原始碼看[這裡][github-winstons-and-ohnoes-v2]

網路上有另一個解法是在app.yaml裡加入handlers把圖檔在GAE環境裡的位置指對。詳細可以看這份[文件][gae-app-yaml-handlers]。

[github-winstons-and-ohnoes-v2]: https://github.com/shincar/WinstonsNOhnoes_v2
[gae-app-yaml-handlers]:  https://cloud.google.com/appengine/docs/standard/nodejs/config/appref#handlers_element
