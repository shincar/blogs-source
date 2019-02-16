---
layout: post
title:  "趁新鮮記錄一下我的第二個作品 - Winson & Ohnoes"
date:   2019-02-13 12:00:00 +0800
categories: HTML ProcessJS
---
這個作品是改編自一個我覺得很有趣的桌遊，叫做[奇雞連連][gobblet-gobbers]。是我跟Alvin去年在桃園展演中心的桌遊展接觸到的遊戲。基本上像是進階版的 O X 遊戲。當時買了卡卡頌和速速城國，考慮到不想一口氣買太多，所以沒買奇雞連連。一直有點後悔沒買，學了[ProcessJS][projessjs]之後，就想說拿他的規則來寫一個網頁小遊戲當練功吧!

**遊戲連結：**[點我玩 Winston & Ohnoes][winston-and-ohnoes]

**遊戲規則：**
- 基本規則跟 O X 一樣，每位玩家在九宮格中輪流下棋。
- 每位玩家起始都有6顆棋子。分別是兩顆小棋、兩顆中棋、兩顆大棋。
- 跟 O X 不一樣的地方在於下棋時，尺寸大的棋子可以蓋過對方玩家尺寸較小的棋子。
- 已經下過的棋子，可以在九宮格中自由移動。可以移到沒有棋子的地方，也可以選擇蓋過對方尺寸比你小的棋子。
- 結束條件就跟原本的 O X一樣，先連線成功者獲勝。
- 如果將自己的棋子拿起來的時候，下面有對方的棋子，而且對方因你將棋子拿起來而連線成功，也算對方獲勝。

**遊戲畫面：**

![遊戲主畫面]({{site.baseurl}}/images/WinstonNOhnoes_home.png){:width="400px" :margin-bottom="10px"}
![對戰畫面]({{site.baseurl}}/images/WinstonNOhnoes_playground.png){:width="400px" :margin-bottom="10px"}
![結束畫面]({{site.baseurl}}/images/WinstonNOhnoes_end.png){:width="400px :margin-bottom="10px"}

**遊戲玩法：**
- 按下Start之後，會進入遊戲畫面。上方會顯示目前是哪個玩家的回合。同時也列出玩家還沒下過的棋子。
- 點選想要下的棋子之後，再點選要下的位置。
- 玩家一為Winston，玩家二為Ohnoes。兩人輪流下棋，直到有一方獲得勝利。
- 結束遊戲之後，點選任意位置即可回到主畫面。再次按下Start就可以再玩一次。

**遊戲連結：**[點我玩 Winston & Ohnoes][winston-and-ohnoes]

**後記：**

原本的版本只有很單調的兩個顏色的圈圈，Demo給老婆看的時候，她說：這配色看來很不吸引人。 QQ

早上跟Alvin討論時，本來要用他跟妹妹的大頭照當玩家的圖示。結果他說他想要[Khan Academy][khan-academy]的Ohnoes。所以我就把Winston跟Ohnes找來當素材啦! 希望他們不會介意。
            
如果有侵權問題的話，可以到[這裡][shincar-github]留言給我。謝啦~ 下次見~ 拜拜

[gobblet-gobblers]: http://www.swanpanasia.com/products/get-bit
[projessjs]: http://processingjs.org/
[winston-and-ohnoes]: https://shincar.github.io/games/WinstonNOhnoes.html
[khan-academy]: https://www.khanacademy.org/
[shincar-github]: https://github.com/shincar/shincar.github.io/issues

