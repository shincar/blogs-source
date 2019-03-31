---
layout: post
title: "在jekyll首頁加入分頁功能"
date:   2019-03-30 02:00:00 +0800
categories: jekyll
permalink: /:year-:month-:day-:title
comments: true
author: adam
---

在加入分類功能之後，下一件blogs常有的功能就是分頁。原本在jekyll裡加入分頁的功能應該是蠻容易的。但是要在github上也能運作，就變的有點複雜。

主要是因為我為了整理方便，在每篇post的Front Matter都有加permalink。結果原本的pagination plugin不支援，只好找替代方案。找到一個jekyll-paginate-v2，但是在github上不支援。看到一個解決方案是只接把jekyll build的output放到github上。

所以現在blogs.git變成只放_site裡的東東。
新開一個blog-source.git放jekyll的原始碼。

要寫什麼東東都跟以前一樣，但是要發佈到github上的時候，要切到_site目錄把內容push到blogs.git裡。呼～ 有點麻煩，但是至少是完成了。