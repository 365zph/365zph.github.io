---
author: viviworld
comments: true
date: 2015-05-25 06:03:24+00:00
excerpt: 如果 Blendle 上的文章阅读体验尽可能接近于文章的原生体验，那会怎样呢？结论让人大吃一惊：为每一份报纸和杂志使用不同的字体、颜色和布局，文章瞬间就觉得更有价值了。通过强调原生出版，我们的用户就对他们将阅读哪种类型的文章有了较好的理解（比如，无论它是一本八卦杂志，还是欧盟扩大化的分析。）。
layout: post
link: http://www.labazhou.net/2015/05/how-we-designed-the-itunes-of-journalism/
slug: how-we-designed-the-itunes-of-journalism
title: 我们是如何设计 iTunes 杂志的
wordpress_id: 2080
categories:
- 杂项
- 软件
tags:
- APP
- Blendle
- Flipboard
- iTunes
- 排版
- 阅读
---


	
  * 原文地址（original source）：[https://medium.com/@jortdevries/how-we-designed-the-itunes-of-journalism-46bf61c9e603](https://medium.com/@jortdevries/how-we-designed-the-itunes-of-journalism-46bf61c9e603)

	
  * 作者（author）：[https://twitter.com/jortdevries](https://twitter.com/jortdevries)





* * *





## 通过授权超过 200 种字体，让人们为杂志付费




<blockquote>六个月前，我们在荷兰发布了 [iTunes 杂志应用](https://medium.com/on-blendle/from-0-to-100-000-users-in-4-months-this-is-blendle-the-itunes-of-journalism-fea25b56959c)，[Blendle](http://www.blendle.nl/)。超过 140,000 个用户（相当于我们国家每个人都在用）使用我们的服务，可以阅读到每份新闻和杂志的精美文章，而只需为他们喜欢的文章付费。</blockquote>


上周，我们宣布，纽约时报公司和欧洲出版商 Axel Springer 共同投资了三百万欧元，帮助我们在其它国家推广 Blendle。

我们相信，截至目前，我们相当一部分成功的原因来自于我们的设计：我们认为，文章的布局和文章本身一样重要，这就是我们为什么要投入大量时间和资金来提高付费阅读体验的原因。

在过去的一年半里，我们构思数百种草图，以期搞清楚在线付费杂志应该是什么样子。最难的部分在于，我们不得不推出一些比其它网站更有价值的东东。因为，如果一篇付费文章看起来比你能够免费阅读到的文章还要糟糕，那么你为什么要付费呢？

我们尝试了大量不同的方式，但是每一次我们都以 Flipboard 式【注1】的设计而告终：漂亮，但丢失了原生报纸或杂志的灵魂。一篇小报文章应该看起来没有多少价值，来自于流行杂志的一篇文章应该看起来，嗯，流行，而来自于纽约时报的一篇文章应该给人的感觉是，它就是一篇来自于纽约时报的文章。

Your browser does not support the video tag.

因此我们决定尝试其它方式。如果 Blendle 上的[文章阅读体验](http://www.labazhou.net/2014/08/how-we-read/)尽可能接近于文章的原生体验，那会怎样呢？结论让人大吃一惊：为每一份报纸和杂志使用不同的字体、颜色和布局，文章瞬间就觉得更有价值了。通过强调原生出版，我们的用户就对他们将阅读哪种类型的文章有了较好的理解（比如，无论它是一本八卦杂志，还是欧盟扩大化的分析。）。

[caption id="attachment_2085" align="alignnone" width="604"][![Blendle 时间线](http://www.labazhou.net/wp-content/uploads/2015/05/1_two5EKobH0Lc1CarwqXldg-1024x683.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/05/1_two5EKobH0Lc1CarwqXldg.jpeg) Blendle 时间线[/caption]


### 模板


从这个时刻起，我们决定，为加入 Blendle 的每份报纸或杂志创建一份新模板。我们每次设计一个模板，来最好地呈现这份报纸的特征。模板包括字族【注2】、大小、粗细和颜色。我的同事 [Laurens](https://twitter.com/laurenscarbo) 将这些价值翻译为不同的 CSS 模板：针对时间线、针对桌面端阅读器的版本，另一种是针对移动端阅读器。

[![报纸的截图](http://www.labazhou.net/wp-content/uploads/2015/05/1_kpJ1kDQLmHHYY9wAO4c-9w-1024x667.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/05/1_kpJ1kDQLmHHYY9wAO4c-9w.jpeg)

[caption id="attachment_2083" align="alignnone" width="604"][![Blendle 的截图](http://www.labazhou.net/wp-content/uploads/2015/05/1_ZNN1VMrqW5LYKd295-HeEw-1024x685.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/05/1_ZNN1VMrqW5LYKd295-HeEw.jpeg) 同一篇文章，前者是报纸，后者是 Blendle 阅读器[/caption]


### 阅读器


我们针对文章阅读器使用相同策略。我们做了大胆的决定，桌面和 iPad 用户应该可以通过我们的 web 应用进行水平滚动。我们这样做，就开创了一种在线阅读体验，它更接近于印刷，它使用了分栏、不包含广告，它和其它博客或网站有着不同的感觉。尽管如此，我们还是得到了移动端的垂直读者------尤其是因为每个人已经习惯了垂直滚动。但是，人们就是喜欢这样。

[![新的在线阅读体验](http://www.labazhou.net/wp-content/uploads/2015/05/1_Og0AaN_byNTghIPNaLyUOw-1024x305.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/05/1_Og0AaN_byNTghIPNaLyUOw.jpeg)

文章的封面图片以全尺寸显示在文章左侧。文章阅读器打开了可见的图片前 300px，以确保你能够立即开始阅读。如果你点击左侧，Blendle 将显示图片的剩余部分。如果你点击右侧，Blendle 将显示更多文本。

所有内容被放在行高为 30px 的基线网格里，确保内容在任何分辨率下排列美观。这非常酷，然而，也限制了我们修改行高，比如标题 H1。行高被锁定为 30px，因此增加 H1 字体大小就意味着一个相对较小的行高。

[caption id="attachment_2089" align="alignnone" width="604"][![所有内容都被排列在 30 px 的基线网格里](http://www.labazhou.net/wp-content/uploads/2015/05/1_OFDwtss5m4z6BxraZeebPw-1024x572.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/05/1_OFDwtss5m4z6BxraZeebPw.jpeg) 所有内容都被排列在 30 px 的基线网格里[/caption]


### 影响


为我们当前的 75+ 份报纸和杂志创建新 CSS 模板的影响是，这需要超过 200 种网络字体的海量字体集。为了确保我们尽可能快速地载入，以提供完美的阅读体验，我们的开发人员开发了一套系统，它检查内容并决定哪种字体是必需的、以及应该在渲染各栏之前载入。这样，只有可见字体被载入。字体集剥去了不会被用到的外国字母。

但是更重要的是，发布商和用户都喜爱。我们甚至得到了一些发布商的说法，我们设法把他们报纸或杂志的特征翻译为网页，这比他们自己的网站还要好。对于用户，他们也买了大量文章。

[![1_GRPcI8vMuj1Z1gN1TRmisw](http://www.labazhou.net/wp-content/uploads/2015/05/1_GRPcI8vMuj1Z1gN1TRmisw-1024x682.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/05/1_GRPcI8vMuj1Z1gN1TRmisw.jpeg)[![1_Y0UsIEGcLbHKKuE_I3WC3Q](http://www.labazhou.net/wp-content/uploads/2015/05/1_Y0UsIEGcLbHKKuE_I3WC3Q-1024x683.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/05/1_Y0UsIEGcLbHKKuE_I3WC3Q.jpeg)[![1_mFPiBLNaS7yKBxS2muh45A](http://www.labazhou.net/wp-content/uploads/2015/05/1_mFPiBLNaS7yKBxS2muh45A-1024x682.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/05/1_mFPiBLNaS7yKBxS2muh45A.jpeg)[![1_FVJpFW_Xqp3aXLiftRcK7w](http://www.labazhou.net/wp-content/uploads/2015/05/1_FVJpFW_Xqp3aXLiftRcK7w-1024x683.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/05/1_FVJpFW_Xqp3aXLiftRcK7w.jpeg)


### 下一步


上线 Blendle 是一个巨大的冒险，不过这只是开始。既然我们有了接近 140,000 个注册用户，20% 的付费转化率 ------很高的转化率。在过去的几个月里，我们陆续增加了越来越多的功能，大部分都是基于我们的假设。有时候我们的假设是错误的，有时候它们是正确的。现在，是时候分析我们收集到的数据、并开始优化了。我们让 Blendle 更聪明、更快、更平滑、更惊艳。我们正在改善可发现性【注3】、可阅读性。我们添加了更多的动画。我们打算发布一个 iOS 应用，努力在新的国家发布。要做的事情太多，乐趣也不少！



* * *






	
  * 注1：Flipboard是一款社交及杂志形式的应用程序，支持Android、iOS、BlackBerry 10及Windows 8操作系统。应用程序需要用户拥有一个Flipboard账号，支持绑定包括Twitter、Facebook、新浪微博在内的多款社交网络平台，并根据喜好定制以电子杂志形式输出的信息和Google Reader的内容，通过“翻转”（Flip）的方式进行浏览和刷新。 [http://zh.wikipedia.org/wiki/Flipboard](http://zh.wikipedia.org/wiki/Flipboard)

	
  * 注2：在 HTML 和 XHTML，font face 或 font family 是网页浏览器套用于某些文字的字型。该字型会用于在屏幕，或于打印机或其他装置显示。在 CSS，font-family (或 HTML 的 face) 包含一堆相关的字型，名为“字族（font families）”。举例来说，Times 字族包含不同的大小、styles (比如 roman 和 italic（斜体）)，以及重量（weight） (比如“常规 regular 和粗体 bold)。[http://zh.wikipedia.org/wiki/Font_family_(HTML)](http://zh.wikipedia.org/wiki/Font_family_(HTML))

	
  * 注3：可发现性（Discoverability）是某种东东、尤其是一条内容或信息被发现的能力。[http://en.wikipedia.org/wiki/Discoverability](http://en.wikipedia.org/wiki/Discoverability)


