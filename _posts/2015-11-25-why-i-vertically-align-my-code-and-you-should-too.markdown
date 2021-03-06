---
author: viviworld
comments: true
date: 2015-11-25 02:22:41+00:00
excerpt: 对于清晰的应用程序，要借助命名习惯、间隔和大写，从而让代码更易于阅读。只要能让你更快地理解这段代码的用途，它就是好的东西！代码是具有创造性的平台，我们通过这个平台来表达想法。如果工具增加了理解这些想法的难度，那么，需要改变的就是工具、而非我们。
layout: post
link: http://www.labazhou.net/2015/11/why-i-vertically-align-my-code-and-you-should-too/
slug: why-i-vertically-align-my-code-and-you-should-too
title: 为什么我要垂直对齐代码（你也要如此！）
wordpress_id: 2780
categories:
- 编程
tags:
- 90-90法则
- diff
- Elastic Tabstops
- hacker news
- IDE
- linux
- 代码
- 想法
- 比例字体
- 等宽字体
---


	
  * 原文地址（original source）：[https://shkspr.mobi/blog/2014/11/why-i-vertically-align-my-code-and-you-should-too/](https://shkspr.mobi/blog/2014/11/why-i-vertically-align-my-code-and-you-should-too/)

	
  * 作者（author）：[Terence Eden](https://twitter.com/edent)





* * *



上周在 HackerNews，关于 [Linux Kernel 代码风格](https://www.kernel.org/doc/Documentation/CodingStyle)展开了[有趣的讨论](https://news.ycombinator.com/item?id=8661740)。

在讨论中，我就[应不应该垂直对齐代码](https://news.ycombinator.com/item?id=8662276)发起了一场小小的圣战。我完全支持！让我细说端详。


### 什么是垂直对齐？


举个小例子：

    
    int robert_age = 32;
    int annalouise_age = 25;
    int bob_age = 250;
    int dorothy_age = 56;


下面的代码更易于阅读：

    
    int robert_age     = 32;
    int annalouise_age = 25;
    int bob_age        = 250;
    int dorothy_age    = 56;


我扫一眼就能看到"bob_age"有点儿不正常。我不用多费事，就轻松地看出来它们都是整数。

这条意见还没被[广为](http://programmers.stackexchange.com/questions/30029/vertical-alignment-yea-or-nay)[分享](http://www.zeyalabs.ch/posts/2013/vertical-alignment-sucks/)，因此我打算解释一下，为什么[很多](http://www.andrewewhite.net/wordpress/2010/09/24/writing-beautiful-code-vertical-alignment-coding-style/)[人](http://francoishill.fr/aligning-patterns-in-code/)认为这是一种有用的风格指南。


### 理解


90% 的编程工作是为了解决问题，剩下的 10% 的工作需要再用 90% 的时间用来理解问题是怎样被解决的。【注1】

阅读代码和阅读散文，有着极大的不同。我们期望作者能够清晰地解释他们的语句，而不是用他们选中的语言过于冗长地说些不相干的东东，我们都期待普通的语法风格。

的确，Kernel 代码风格着重强调了这一点。你选择变量命名的方式，和代码的用途一样重要。

考虑下面的代码：

    
    var thinG=doIt(thestuff,MORE_sTuff); /* LOL! */


即便你对代码库有深入理解，它也不是特别易读的代码行。

    
    var totalBill = apply_tax(initialBill, taxRate);


对于清晰的应用程序，要借助命名习惯、间隔和大写，从而让代码更易于阅读。这意味着，接手我们代码的可怜家伙，将用更少的时间来解密代码，把更多时间放在理解上面。


### 为什么使用等宽字体？


在所有著名的、老生常谈的舌战中，有两个实力基本相当的阵营，即 等宽字体 【注2】VS 比例字体【注3】 的争论。

某些异教徒会对你说，[比例](https://code.google.com/p/i3project/wiki/Fonts)[字体](http://nickgravgaard.com/elastictabstops/news/programming-fonts/)是[最棒的](http://www.slant.co/topics/67/~what-are-the-best-programming-fonts)------无视这些异教徒吧。另一些异教徒则在他们争论[比例](http://blog.codinghorror.com/revisiting-programming-fonts/)[字体](http://programmers.stackexchange.com/questions/5473/does-anyone-prefer-proportional-fonts)所具有的上等[纯洁度](https://news.ycombinator.com/item?id=4623781)时，给你的心灵留下了不和谐------这些可怜的、受谴责的灵魂呀。

最终，还要归结到可读性。你觉得，什么东西能够最容易地帮助你理解代码？为什么 IDE 有着色方案------因此你能一眼看出“foo”是函数、常量、变量还是注释。只要能让你更快地理解这段代码的用途，[它就是好的东西](http://www.labazhou.net/2015/04/code-is-ux/)！

这也是电子表格如此受欢迎的原因之一。列提高了可读性。你可以快速地顺着一列扫视，并能注意到某行和其它行是否存在明显不同。


### 我们没有工具


有趣的是，在 HackerNews 上的讨论中，我面临的最大批评与垂直对齐是否有用无关，而是我们的工具有多么糟糕。


<blockquote>「这破坏了 diff 的可读性和可用性。比如你修改了某个常量，需要快速追踪因此引起的严重 bug。对于水平排列的代码，diff 或许包含了所有修改过的行，从而掩盖了关键修改。有一些忽视空格的变通方案，以及基于单词的 diff，不过依本人愚见，不值得这么麻烦。
------[Andreas van Cranenburgh](https://news.ycombinator.com/item?id=8662938)</blockquote>


……还有……


<blockquote>假如你有 50 行赋值语句，你把所有值都和最大的那个对齐了，那么增加一个赋值语句，将迫使你更新 50 行代码。我已经遇到过这些情形了，每当那时候，我就明白了，不要那样对齐值 是多么地重要。
------[scrollaway](https://news.ycombinator.com/item?id=8665741)</blockquote>


这些论点在某些语境中是合理的，但是说明了需要更好的工具。

我想起了 [Elastic Tabstops](http://nickgravgaard.com/elastictabstops/) ------自动排列代码块的方法。

[caption id="attachment_2781" align="alignnone" width="393"][![Elastic Tabstops](http://www.labazhou.net/wp-content/uploads/2015/11/columnblocks_coloured.gif)](http://www.labazhou.net/wp-content/uploads/2015/11/columnblocks_coloured.gif) By Nick Gravgaard[/caption]

工具能够轻松容纳这种工作方式。计算机就是为我们做单调、重复工作的，CPU 周期「浪费」在让代码更可读方面的代价，已经足够便宜了。

在 [Linux](https://github.com/torvalds/linux/blob/9a3c4145af32125c5ee39c0272662b47307a8323/arch/mips/include/asm/octeon/cvmx-bootmem.h) [Kernel](https://github.com/torvalds/linux/blob/c6c9161d064d30e78904f3affe5184487493e0fc/arch/x86/kernel/cpu/common.c#L103) 中，还有[大量](https://github.com/torvalds/linux/blob/9a3c4145af32125c5ee39c0272662b47307a8323/net/wireless/wext-proc.c#L135)的[例子](https://github.com/torvalds/linux/blob/cba3b00deab5a8564d61ec18e61ba6ba82203299/include/uapi/sound/asound.h)，垂直排列让代码更便于人类分析。

垂直排列不适用于每个场景，但是对于快速评估代码，其可读性是无与伦比的。

代码是具有创造性的平台，我们通过这个平台来表达想法。如果工具增加了理解这些想法的难度，那么，需要改变的就是工具、而非我们。


### 注释

* 注1：90-90法则（ninety-ninety rule，九九定律，99定律）是计算机编程和软件工程领域的一个有名的法则，出自于一句幽默的格言：（开发软件时）前90%的代码要花费90%的开发时间，剩余的10%的代码要再花费90%的开发时间。 [https://zh.wikipedia.org/wiki/90-90%E6%B3%95%E5%88%99](https://zh.wikipedia.org/wiki/90-90%E6%B3%95%E5%88%99) 
* 注2：等宽字体（Monospaced Font）是指字符宽度相同的电脑字体。与此相对，字符宽度不尽相同的电脑字体称为比例字体。在等宽字体中，字母i,j显得两侧余白较多，而字母w,m等的笔画显得相当拥挤。但是随着图形用户界面主流的更新和电脑技术的提高，处理比例字体的局限性得到了突破，因此现在排版上显得比较自然的比例字体的使用已经相当普及。另外，代码也经常使用等宽字体。[https://zh.wikipedia.org/wiki/%E7%AD%89%E5%AE%BD%E5%AD%97%E4%BD%93](https://zh.wikipedia.org/wiki/%E7%AD%89%E5%AE%BD%E5%AD%97%E4%BD%93) 
* 注3：比例字体（Proportional Font）是指字符宽度不尽相同的电脑字体。与此相对，字符宽度相同的电脑字体称为等宽字体。[https://zh.wikipedia.org/wiki/%E6%AF%94%E4%BE%8B%E5%AD%97%E4%BD%93](https://zh.wikipedia.org/wiki/%E6%AF%94%E4%BE%8B%E5%AD%97%E4%BD%93)
