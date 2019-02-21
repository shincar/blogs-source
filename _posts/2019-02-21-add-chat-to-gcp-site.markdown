---
layout: post
title:  "在Google Could Platform中，加入即時聊天室"
date:   2019-02-21 08:00:00 +0800
categories: HTML GCP Node.js soket.io
permalink: /:year-:month-:day-:title
author: adam
---
[上一篇][host-winstons-and-ohnoes-on-google-could-platform]是把 Winston & Ohnoes 架到能支援[Node.js][node.js]的環境。接下來就是要能在這個環境下，提供簡單的連線溝通功能啦!連線溝通的功能，要靠[socket.io][socket.io]的幫忙。

**socket.io的基本功能**
- 建立client跟server的連線
- 約定一個共同溝通的房間
- 透過socket.on()來接收訊息
- 透過socket.emit()來發送訊息

有了這個功能，要支援網路對戰就不是夢啦!


[host-winstons-and-ohnoes-on-google-could-platform]: https://shincar.github.io/2019-02-19-host-winstons-and-ohnoes-on-google-could-platform
[node.js]: https://nodejs.org/
[socket.io]: https://socket.io/
[winstons-and-ohnoes-v2]: https://github.com/shincar/WinstonsNOhnoes_v2
[gpc-winstons-and-ohnoes]: https://shincar.appspot.com
[socket.io-github]: https://github.com/socketio/socket.io
[gcp-shincar-chat-room]: https://shincar.appspot.com/chat/
