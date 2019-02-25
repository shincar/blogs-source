---
layout: post
title:  "把Winstons & Ohnoes掛到Google Cloud Platform"
date:   2019-02-19 20:00:00 +0800
categories: HTML GCP Node.js
permalink: /:year-:month-:day-:title
author: adam
---
為了要[Winstons & Ohnoes][winstons-and-ohnoes]裡加入網路對戰功能，就不能只host在[github][github].因為github只支援靜態網頁。網路對戰的話，兩個人必須要能跟彼此溝通。這時靜態網頁就不夠用了。剛好之前有摸過一點點[Google Cloud Platform][google-cloud-platform]，就把[Winstons & Ohnoes][winstons-and-ohnoes]掛上去看看吧！

點我玩[Google Cloud Platform 版 Winstons & Ohnoes][gpc-winstons-and-ohnoes]

決定好平台之後，就要看看要用哪個server side的架構啦！目前Google Cloud Platform支援的架構有
- Python 2.7, Python 3.7
- Java 8
- Node.js 8, and Node.js 10 (beta)
- PHP 5.5, and PHP 7.2 (beta)
- Go 1.9, and Go 1.11 (beta)

因為工作的關係，曾經跟Python跟Node.js當過朋友。[Node.js][node.js]是我2011年時支援過的一個專案，開發一支用Node.js為基礎的手機作業系統。那時的Node.js還不是很成熟，但是我對它event-driven的玩法一直覺得很酷。後來那個專案胎死腹中，我也跟著就回頭做其他的專案。想不到現在Node.js還蠻夯的，剛好Google Cloud Platform現在有支援Node.js，就決定給老朋友一個機會啦！

兩樣都決定好之後，就是開工啦！

**步驟一**

先在Google Cloud Platform開一個project，取名叫shincar。

![GPC Project Page]({{site.baseurl}}/images/create-project-in-gcp.png){:width="400px" :margin-bottom="10px"}

**步驟二**

照著[這篇][gpc-nodejs-quickstart]先把hello world搞出來。然後就是把Winstons & Ohnoes的程式碼（其實就是html啦！）想辦法塞到app.js就可以了。

app.js的內容如下：
{% highlight javascript %}
// [START gae_node_request_example]
const express = require('express');

const app = express();

app.get('/', (req, res) => {
  res
    .status(200)
    .send('Hello, world!')
    .end();
});

// Start the server
const PORT = process.env.PORT || 8080;
app.listen(PORT, () => {
  console.log(`App listening on port ${PORT}`);
  console.log('Press Ctrl+C to quit.');
});
// [END gae_node_request_example]
{% endhighlight %}

重點只有一個，就是send('Hello, world!')這行，server是靠這行把html傳給client。所以我只要把Winston & Ohnoes的html檔案從這裡送出去。查了一下Node.js送檔案內容的方法，是[res.sendFile()][response-send-file]。app.get()那行，從send('Hello, world!')改成sendFile()，然後把html在server上的路徑串上去， 可能就收工了

{% highlight javascript %}
app.get('/', (req, res) => {
  console.log('Send file: ' + path.join(__dirname + '/WinstonNOhnoes_Fullscreen.html'));
  res.sendFile(path.join(__dirname + '/WinstonNOhnoes_Fullscreen.html'));
});
{% endhighlight %}

試著下
{% highlight shell %}
gcloud app deploy
{% endhighlight %}
結果悲劇，什麼都看不到。研究之後，發現是html沒有參考到images, css, js...等檔案。找了一下，看到用[app.use()][app-use]可以讓client存取靜態資源。新增一個public資料夾，把images, css, js...都丟進去。再加上
{% highlight javascript %}
app.use(express.static('public'));
{% endhighlight %}

這樣WinstonsNOhnoes_Fullscreen.html裡就能載入image, css, js...了。

再次deploy之後，就可以正常玩啦！

點我玩[Google Cloud Platform 版 Winstons & Ohnoes][gpc-winstons-and-ohnoes]

我的完整的app.js如下：
{% highlight javascript %}
/**
 * Copyright 2017, Google, Inc.
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *    http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */

'use strict';

const express = require('express');
var path = require("path");

const app = express();

app.use(express.static('public'));

app.get('/', (req, res) => {
  console.log('Send file: ' + path.join(__dirname + '/WinstonNOhnoes_Fullscreen.html'));
  res.sendFile(path.join(__dirname + '/WinstonNOhnoes_Fullscreen.html'));
});

// Start the server
const PORT = process.env.PORT || 8080;
app.listen(PORT, () => {
  console.log(`App listening on port ${PORT}`);
  console.log('Press Ctrl+C to quit.');
});
// [END gae_node_request_example]
{% endhighlight %}

[winstons-and-ohnoes]: https://shincar.github.io/games/WinstonNOhnoes.html
[github]: https://github.com/
[google-cloud-platform]: https://cloud.google.com
[node.js]: https://nodejs.org/
[gpc-nodejs-quickstart]: https://cloud.google.com/appengine/docs/standard/nodejs/quickstart
[response-send-file]: http://expressjs.com/en/api.html#res.sendFile
[app-use]: http://expressjs.com/en/api.html#app.use
[gpc-winstons-and-ohnoes]: https://20190221t154429-dot-shincar.appspot.com/
