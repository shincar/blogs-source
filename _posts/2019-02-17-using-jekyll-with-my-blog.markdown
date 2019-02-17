---
layout: post
title:  "使用jekyll寫blog"
date:   2019-02-17 8:00:00 +0800
categories: HTML jekyll
author: adam
---
隨著文章越來越多，決定把BLOG改版一下，主要想做的是
- 能好好將文章分類。
- 讓每次寫文章所需要的前置步驟越少越好。
- 未來能有更多的彈性增加各樣小功能。
- 容易使用。

這樣才能將心力多花在內容上。花了些時間google了一下，現在好像蠻流行用[jekyll][jekyll]，就決定拿來試試啦！結果一試成主顧。新增文章很方便，只要做一次版型，之後的文章都能套用。如果決定在主版型上加入啥小功能，全部的文章也能會跟著更新。

目前使用的版型是預設的版型，使用的指令是
{% highlight bash %}
jekyll new shincar-blog
cd shincar-blog
bundler exec jekyll serve
{% endhighlight %}

接下來就是看[document][jekyll-documents]把原本我自己刻的版型弄回來啦~

[jekyll]: https://jekyllrb.com/
[jekyll-documents]: https://jekyllrb.com/docs/
