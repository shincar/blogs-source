---
layout: post
title:  "在jekyll blog中加入留言系統"
date:   2019-02-25 02:00:00 +0800
categories: HTML jekyll Disqus
permalink: /:year-:month-:day-:title
comments: true
author: adam
---
寫了那麼多篇文章，當然是希望哪天有人看到。為了讓來看的人有機會留下足跡，或是對文章的內容提出疑問。所以有個留言板也是很正常的。

起手式一樣是GOOGLE一下，馬上就找到一個可以跟jekyll整合的獨立留言系統，叫做[Disqus][disqus]。這系統蠻方便的，可以讓使用者決定要用哪個帳號登入。預設支援disqus、facebook、google或twitter登入。就可以留言啦！

我是直接用google account登入創建Disqus帳號，然後選擇"I want to install Disqus on my site"
![Disqus get started]({{site.baseurl}}/images/disqus_get_started.png)

填入正確資料之後，按下Create Site
![Create Site]({{site.baseurl}}/images/disqus_create_new_site.png)

就會有在jekyll系統中，加入Disqus的語法，跟要加在哪邊的說明。
![Install instructions]({{site.baseurl}}/images/discus_jekyll_install_instructions.png){:width="600px"}

它預設的說明是建議你每個post都加comments: true來決定要不要秀出留言系統。我自己是在_layouts\post.html裡也加了comments: true
這樣的好處是如果我要直接關閉整個留言系統，直接改_layouts\post.html就可以了。

立馬去[第一篇][first-post]文章頭推試試，看來沒問題！讚啦～

[disqus]: https://disqus.com/
[first-post]: https://shincar.github.io/blogs/2019-01-29-my-first-game
