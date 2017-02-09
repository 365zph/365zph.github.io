---
author: viviworld
comments: true
date: 2015-08-10 03:20:03+00:00
excerpt: 我受 HTML 的启发，其代码常常非常清晰，因为你能看到一个标签从哪儿开始、到哪儿结束。一目了然，下面是我相应做出的注释风格
layout: post
link: http://www.labazhou.net/2015/08/code-commenting/
slug: code-commenting
title: 用 HTML 标记的古怪代码注释
wordpress_id: 2366
categories:
- 编程
tags:
- php
- sublime
- 代码
- 注释
---


	
  * 原文地址（original source）：[https://levels.io/code-commenting/](https://levels.io/code-commenting/)

	
  * 作者（author）：[https://twitter.com/levelsio](https://twitter.com/levelsio)





* * *



现在我明白了，我在编程方面的很多做法都是古怪的、不入流的，不过，对我而言，多多少少是有帮助的。我的网站比大部分网站，肯定存在更多的问题，但是我交付的速度快了不少。你不都懂的。

我从来无法正确学到的一件事，就是[注释我的代码](http://www.labazhou.net/2015/04/why-comments-are-stupid-a-real-example/)。人们通常注释代码的方式如下：

[![PHP The Right Way 的代码摘录](http://www.labazhou.net/wp-content/uploads/2015/08/Screenshot-2015-05-04-13.25.37-600x232.png)](http://www.labazhou.net/wp-content/uploads/2015/08/Screenshot-2015-05-04-13.25.37.png)

上面的代码是从 [PHP The Right Way](http://www.phptherightway.com/) 直接摘录的。我纠结的地方在于，代码缩进越深，代码就变得越发难以理解。如果你深入两个 foreach 循环，你该如何知道这部分代码起始何处？问题在于注释无法以某种方式来分割代码。你看不到某段代码的结尾。

你可以使用函数把代码简化为一行，这解决了很多问题。但是把每个小段代码弄成函数，也会减慢你的速度。

是否有一个折衷方案呢？

我受 HTML 的启发，其代码常常非常清晰，因为你能看到一个标签从哪儿开始、到哪儿结束。一目了然，下面是我相应做出的注释风格：

[![HTML 标记风格的代码注释](http://www.labazhou.net/wp-content/uploads/2015/08/Screenshot-2015-05-04-13.25.24-600x230.png)](http://www.labazhou.net/wp-content/uploads/2015/08/Screenshot-2015-05-04-13.25.24.png)

我在 PHP、JavaScript、Obj-C、甚至 Shell 脚本里使用这种注释风格，实际上对于我快速地搞清楚要编辑某个文件的哪个部分、以及其功能，让我节省了大量时间。

更有意思的是，如果你在用 Sublime Text，那么你还能折叠标签之间的整个代码，比如：

[![在Sublime Text 可折叠的HTML 标记风格的代码注释](http://www.labazhou.net/wp-content/uploads/2015/08/Screenshot-2015-05-04-13.42.39-600x132.png)](http://www.labazhou.net/wp-content/uploads/2015/08/Screenshot-2015-05-04-13.42.39.png)

这可能违背了在 Hacker News 游荡的、留着大胡子的委员会编写的编码法则的宏大指导。不过还行，我没有留胡子。

顺便提一下，如果你想关注我的更多冒险经历，请访问我的 [Twitter](https://twitter.com/levelsio)。
