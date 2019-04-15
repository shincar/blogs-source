---
layout: post
title: "在Ubuntu下開發C#程式"
date:   2019-04-15 02:00:00 +0800
categories: c-sharp
permalink: /:year-:month-:day-:title
comments: true
author: adam
---

前陣子比較有空，所以下班後開始研究一下網路程式設計。最後公司又開始忙了，只能先把興趣放一邊。繼續充實本業相關的知識。

工作上我比較常用的程式語言是C++和C#。本來都是以在Windows上運作為主，最近聞到可能也會要支援Linux，趁今天有空，來看一下能不能在Ubuntu下寫出一個Hello World來。直接參考[MSDN][get-started-with-c-sharp]上的文章，一步一步做。

首先，要安裝
- Visual Studio Code（這個我本來就裝了）
- .Net Core SDK（目前最新的版本是.Net Core 2.2）
- C# Extension for Visual Studio Code

裝完之後，就開一個空的資料夾。然後在Visual Studio Code的Terminal打入
{% highlight shell %}
dotnet new console
{% endhighlight %}

就會產生Project檔跟一個Program.cs的原始碼檔案。預設它就是印出Hello World字樣。

接下來就是編譯程式。指令是
{% highlight shell %}
dotnet build
{% endhighlight %}

完成之後，會把Output生在/bin/Debug目錄裡。

執行程式的指令是
{% highlight shell %}
dotnet run
{% endhighlight %}

注意的一點是執行程式時不用切換目錄，直接在跟Project同目錄下就可以執行。非常方便。

[get-started-with-c-sharp]: https://docs.microsoft.com/zh-tw/dotnet/core/tutorials/with-visual-studio-code