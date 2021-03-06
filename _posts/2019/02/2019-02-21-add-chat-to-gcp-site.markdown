---
layout: post
title:  "在Google Could Platform中，加入即時聊天室"
date:   2019-02-21 08:00:00 +0800
categories: HTML GCP NodeJS soket.io
permalink: /:year-:month-:day-:title
comments: true
author: adam
---
[上一篇][host-winstons-and-ohnoes-on-google-could-platform]是把 Winston & Ohnoes 架到能支援[Node.js][node.js]的環境。接下來就是要能在這個環境下，提供簡單的連線溝通功能啦！連線溝通的功能，要靠[socket.io][socket.io]的幫忙。

**socket.io的基本功能**
- 建立client跟server的連線
- 約定一個共同溝通的房間
- 透過socket.on()來接收訊息
- 透過socket.emit()來發送訊息

有了這些功能，要支援網路對戰就不是夢啦！

要直接把socket.io整進Winstons & Ohnoes，對於一個老手來說可能很容易。但我其實在web design還是個新手，所以我的策略是先把socket.io的功能在Google Cloud Platform上掛起來，等我對socket.io的運作有多一點的理解之後，再把它加到Winstons & Ohnoes。理論上，Winstons & Ohnoes的實作可能也還要調整。因為我對javascript也沒有到很專家，不過別擔心，一切都在進步中。

我想做到的是先提供另一個URL把socket.io的功能先玩一遍，然後確認在Google Cloud Platform上也都能正常運作。這樣整合到Winstons & Ohnoes的時候，比較能得心應手。

我以[socket-io原始碼][socket.io-github]裡的examples/chat為藍本，在index.js中把WinstonNOhnoes_Fullscreen.html指定給/，而把chat/index.html指向 /chat。

{% highlight javascript %}
app.get('/', function(req, res) {
  console.log('SendFile: ' + path.join(__dirname, '/public/WinstonNOhnoes_Fullscreen.html'));
  res.sendFile(path.join(__dirname, '/public/WinstonNOhnoes_Fullscreen.html'));
});

app.get('/chat', function(req, res) {
  res.sendFile(path.join(__dirname, '/public/chat.html'));
})
{% endhighlight %}


使用者在瀏覽器的網址列輸入
- https://shincar.appspot.com/ 就會和原本一樣，可以玩Winstons & Ohnoes
- https://shincar.appspot.com/chat 則會導向/chat/index.html，輸入大名之後，就可以進入聊天室。

另外，index.js裡socket.io的路徑，在examples裡是相對路徑
{% highlight javascript %}
var io = require('../..')(server);
{% endhighlight %}
要改成
{% highlight javascript %}
var io = require('socket.io')(server);
{% endhighlight %}

弄好之後，先在local環境下試試看，完全沒問題。科科

{% highlight shell %}
npm install --save socket.io
npm start
{% endhighlight %}

接下來就是部署到Google Cloud Platform
{% highlight shell %}
gcloud app deploy
{% endhighlight %}

就完成啦~ [點我開始聊天][gcp-shincar-chat-room]

做到這裡可以想像一下，網路對戰功能到時要怎麼做啦~ 就像是兩個人進到同一個聊天室(對戰室)一樣。

玩家一進入對戰室

![玩家一進入對戰室]({{site.baseurl}}/images/socket.io-player1_enter.png){:width="400px"}

玩家二進入對戰室

![玩家二進入對戰室]({{site.baseurl}}/images/socket.io-lobby.png){:width="400px"}

兩人開始對戰，直到遊戲結束

![開始對戰]({{site.baseurl}}/images/socket.io-chat.png){:width="400px"}



[host-winstons-and-ohnoes-on-google-could-platform]: https://shincar.github.io/2019-02-19-host-winstons-and-ohnoes-on-google-could-platform
[node.js]: https://nodejs.org/
[socket.io]: https://socket.io/
[winstons-and-ohnoes-v2]: https://github.com/shincar/WinstonsNOhnoes_v2
[gpc-winstons-and-ohnoes]: https://20190221t154429-dot-shincar.appspot.com/
[socket.io-github]: https://github.com/socketio/socket.io
[gcp-shincar-chat-room]: https://20190301t085415-dot-shincar.appspot.com/chat/
