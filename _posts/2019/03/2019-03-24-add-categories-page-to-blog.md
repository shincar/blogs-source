---
layout: post
title: "分類文章上線！"
date:   2019-03-24 02:00:00 +0800
categories: jekyll
# permalink: /:year-:month-:day-:title
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
{% highlight javascript %}
---
layout: category_page
title: HTML
---
{% endhighlight %}

layout是這個頁面參考的template，title裡是每個分類的名字。這樣每個分類就有他們的頁面。

在category_page.html裡，用page.title跟category[0]比對，完全相同的才秀出來。這樣就可以只列出這個分類的posts啦！

**後記：**

完成第一版之後，發現有的分類可能還不適合列出來。所以就研究了一下能不能只顯示我想要列出的分類。我找到的[解法][jekyll-collection-example]是在_config.yml中使用collections，在新增一個文章分類(my-categories)的collection，定義好之後新增一個目錄叫_my-categories。把原本每個類別的markdown放到這個目錄。然後修改一下right.html裡面分類文章改從my-categories裡面拿資訊。這樣就搞定收工囉！

[原始碼在這][github-shincar-blogs]

[jekyll-posts]: https://jekyllrb.com/docs/posts/
[github-shincar-blogs]: https://github.com/shincar/blogs
[jekyll-collection-example]: https://alligator.io/jekyll/collections/
