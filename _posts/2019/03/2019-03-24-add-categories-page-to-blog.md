---
layout: post
title: "分類文章上線！"
date:   2019-03-24 02:00:00 +0800
categories: jekyll
permalink: /:year-:month-:day-:title
comments: true
author: adam
---
隨著文章變多，分類就變得蠻重要的。原本就預留了一個分類文章的區塊。今天有空，就來把它做好。

看了一下[jekyll對文章的說明][jekyll-posts]，只要有定義categories在front matter裡，這篇文章就有歸類了。這時就可以用以下語法把分類列出來。
{% highlight javascript %}
  {{"{%" }} for category in site.categories %}
    {{ "{{" }} category[0] }}
  {{"{% endfor " }}%}
{% endhighlight %}

把這段範例稍微修改一下，就加入連結讓每個人都可以點選來讀特定分類的文章了。接下來就是要為每個分類提供內容。我在根目錄下新增一個categories資料夾，然後新增每個分類的markdown。

每個分類的front matter長類似這樣。
{% hightlight javascript %}
---
layout: category_page
title: HTML
---
{% endhighlight %}

layout是這個頁面參考的template，title裡是每個分類的名字。這樣每個分類就有他們的頁面。

在category_page.html裡，用page.title跟category[0]比對，完全相同的才秀出來。這樣就可以只列出這個分類的posts啦！

[原始碼在這][github-shincar-blogs]

[jekyll-posts]: https://jekyllrb.com/docs/posts/
[github-shincar-blogs]: https://github.com/shincar/blogs
