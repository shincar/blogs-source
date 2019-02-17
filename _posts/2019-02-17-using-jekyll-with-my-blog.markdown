---
layout: post
title:  "使用jekyll寫blog"
date:   2019-02-17 8:00:00 +0800
categories: HTML jekyll
permalink: /:year-:month-:day-:title
author: adam
---
隨著文章越來越多，決定把BLOG改版一下，主要想做的是
- 能好好將文章分類。
- 讓每次寫文章所需要的前置步驟越少越好。
- 未來能有更多的彈性增加各樣小功能。
- 容易使用。

這樣才能將心力多花在內容上。花了些時間google了一下，現在好像蠻流行用[jekyll][jekyll]，就決定拿來試試啦！結果一試成主顧。新增文章很方便，只要做一次版型，之後的文章都能套用。如果決定在主版型上加入啥小功能，全部的文章也能會跟著更新。

目前使用的版型是預設的版型，使用的指令是
{% highlight shell %}
jekyll new shincar-blog
cd shincar-blog
bundler exec jekyll serve
{% endhighlight %}

接下來就是看[document][jekyll-documents]把原本我自己刻的版型弄回來啦！發現一個蠻好的[jekyll YouTube 教學][jekyll-youtube-tutorial]，懶得看很多英文的人，也可以看這個影片學喔！

看完tutorial之後，學到的密技
- 每篇文章的front matter加入permalink，這樣url不會因categories而變的世界長。
- 新增一個_layouts資料夾，重新把原本的版型加到post.html (Minimai這個theme預設文章會套用的layout裡的post.html)
- 把原本我[改編][add-theme-with-css]的css放到assets/css裡，再把post.html裡css的相對路徑改對，原本的theme就回來啦！科科
- 發現標題、日期跟作者資訊不見了。原來是因為我漏了。把post.html改了一下，就統一加好了。舒服~

P.S. 當新增文章的時候，如果在markdown裡date的時間是未來時間的話，這篇文章就不會顯示出來。一開始我以為是我什麼語法用錯。後來才發現我把前一篇文章的時間直接複制貼上過來改日期。結果文章一直沒顯示是因為那篇是晚上10點多寫的，這篇是早上8點起來寫的。耍笨了 Orz

[jekyll]: https://jekyllrb.com/
[jekyll-documents]: https://jekyllrb.com/docs/
[jekyll-youtube-tutorial]: https://www.youtube.com/watch?v=T1itpPvFWHI&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB
[add-theme-with-css]: https://shincar.github.io/blogs/2019-02-13-add-a-theme-for-a-blog
