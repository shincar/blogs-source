---
layout: post
title:  "規畫socket.io支援網路對戰所需要的流程與指令"
date:   2019-02-22 02:00:00 +0800
categories: soket.io
# permalink: /:year-:month-:day-:title
comments: true
author: adam
---
了解[socket.io][socket.io]的運作之後，接下來要規畫如何在Winstons & Ohnoes裡面加入網路對戰的功能啦！基本上就是把玩家在遊戲裡的動作，都包裝成指令在玩家跟伺服器之間傳來傳去。往下看下去應該就會懂了！目前只規畫最基本能對戰所需要的步驟。

**網路對戰流程**
1. 玩家一進入遊戲，給自己一個名字
2. 新增一間對戰室，給對戰室一個名字，加入對戰室
3. 玩家二進入遊戲，給自己一個名字
4. 輸入要加入的對戰室的名字，加入對戰室
5. 對戰室人數已滿，開始遊戲
6. 等待玩家一的下棋指令
7. 伺服器收到玩家一的下棋指令，發送給玩家二
8. 等待玩家二的下棋指令
9. 伺服器收次玩家二的下棋指令，發送給玩家一
10. 重覆步驟6－9，直到有一個玩家獲得勝利
11. 玩家一跟玩家二都進入結束畫面。

列完對戰流程之後，就可以開始把每個流程對應的socket.io指令設計出來。

**socket.io指令表**
1. 玩家指令：'add user' 參數：username
2. 玩家指令：'join fightroom' 參數：username, fightroomName
3. 玩家指令：'add user' 參數：username
4. 玩家指令：'join fightroom' 參數：username, fightroomName
5. 伺服器指令：'fight start' 參數：firstplayer
6. 玩家指令：'fight command' 參數：username, grid, token
7. 伺服器指令：'fight change' 參數：username, grid, token
8. 玩家指令：'fight move' 參數：username, grid, token
9. 伺服器指令：'fight change' 參數：username, grid, token
10. 伺服指令：'fight end' 參數：winner

翻譯完流程所需要的指令之後，接下來就是再補強每個指令的回應啦！舉例來說，玩家送出'add user'指令後，可能已經有其他玩家用了一樣的名字，所以伺服器要回應'add user'有沒有成功。所以要再多一些回應類的指令。

**額外指令**
- 伺服器指令：'add user result' 參數：result, message
- 伺服器指令：'join fightroom result' 參數：result, message

（烏鴉飛過...)本來以為會很多，結果也就只有這些...XD

整理一下要實做的指令如下：

**玩家指令**
- 指令：'add user' 參數：username
- 指令：'join fightroom' 參數：username, fightroomName
- 指令：'fight move' 參數：username, grid, token

**伺服器指令**
- 指令：'add user result' 參數：result, message
- 指令：'join fightroom result' 參數：result, message
- 指令：'fight start' 參數：firstplayer
- 指令：'fight change' 參數：username, grid, token
- 指令：'fight end' 參數：winner

指令分析完之後，接下來在伺服器的部分，還有資料要存起來的問題。目前還沒有要和資料庫做連結，所以只要設計資料結構就好。從上面的流程分析大致上也能幫助思考伺服器端要存放哪些資料可以讓網路對戰能夠進行。例如：步驟一看完就會知道伺服器端要存一個玩家列表。步驟二看完就知道要有個對戰室列表。加上對戰室中要存目前對戰室的人數、對戰室的最大人數（以Winstons & Ohnoes來說是2）...等等。下面就把我的理解整理出來，要實作的時候，就參考這份資料結構啦！

**伺服器資料結構**
- PlayerList: A collection of player names
- FightroomList: A collection of Fightrooms
- Player: A player class
  - name: Player name
  - fightroomname: The fightroom player joined
- Move: A move player could make
  - playername
  - grid
  - token
- Fightroom: A fight room for players
  - name: Fightroom name
  - maxPlayerCount: 2
  - currentPlayers: A collection of player name
  - currentPlayer: Player name who now could perform a move
  - moves: a collection of moves players performed
  - winner: Player who won this game

從目前Winstons & Ohnoes的架構index.js就是伺服器端要實作指令的地方。而玩家端實作則是打算新增一個games/client.js，做完之後，讓WinstonNOhnoes_Fullscreen.html使用。

等socket.io的部份之後，再來改遊戲畫面，加入一些按鈕、輸入框等，讓玩家可以送出指令。可能網路對戰功能就完成了！有點興奮 呼～

[socket.io]: https://socket.io/
