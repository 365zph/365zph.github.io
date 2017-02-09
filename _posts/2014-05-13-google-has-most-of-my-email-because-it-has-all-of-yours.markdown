---
author: viviworld
comments: true
date: 2014-05-13 03:00:34+00:00
layout: post
link: http://www.labazhou.net/2014/05/google-has-most-of-my-email-because-it-has-all-of-yours/
slug: google-has-most-of-my-email-because-it-has-all-of-yours
title: Google拥有我的大部分邮件，因为它拥有你的全部邮件
wordpress_id: 655
categories:
- 安全
- 网络
- 软件
tags:
- email
- gmail
- google
- python
- R
---

大约15年来，我一直运行着我自己的邮件服务器，用于我的所有非工作信函。我这样做是为了让我的邮件保持[自治](http://autonomo.us/)、控制和隐私，防止大公司拥有我的所有个人邮件的拷贝。

数年前，我非常惊奇地发现我的朋友[Peter Eckersley](https://www.eff.org/about/staff/peter-eckersley)------一名对隐私非常在意的朋友，是[EFF](https://eff.org/)的技术项目总监------使用Gmail。我问他为什么愿意把他的所有邮件给Google做拷贝。Peter说，如果你所有的朋友在用Gmail，那么无论如何Google就有你的邮件了。任何时候我给使用Gmail的某个人发邮件了------任何时候他们给我写邮件------Google就有了那封邮件。

有了这次谈话，我就一直想知道Google究竟拥有多少封我的邮件。本周，我写了一个遍历我个人收件箱里的、自从2004年4月（那是Gmail开始的时候）以后的、所有邮件的小程序来找出来。

回答这个问题的一个挑战是有很多人，比如Peter，用Gmail阅读、撰写和发送邮件，但是他们配置Gmail使用一个非gmail.com的“From”地址来发送邮件。为了处理这种情况，我的程序查看每个消息头，它记录了在到达我的服务器的路上都有哪些电脑处理了这条消息，然后筛选出经过了google.com、gmail.com或googleemail.com的消息。虽然我通常会过滤它们，我的个人收件箱包含了通过很多邮件列表（mailing list）发送过来的邮件。由于这些邮件列表经常“隐藏”消息的真正来源，我从列表中排除了 标记为来自于 使用了“Precedence”头（通常是不可见的）的消息。

下图，红色表示我的个人收件箱每周的邮件数量，蓝色表示来自Google的子集。因为我每周收到的邮件数量变化比较大，我包含了一个[LOESS](https://en.wikipedia.org/wiki/LOESS)“平滑线”【注1】来显示一个基于数周的移动平均线。

[![邮件中的Gmail占比](http://www.labazhou.net/wp-content/uploads/2014/05/emails-gmail-over-time.png)](http://www.labazhou.net/wp-content/uploads/2014/05/emails-gmail-over-time.png)

目测图表，答案好像就是那样，尽管它在变化，我的收件箱有大约三分之一的邮件来自于Google！

需要注意的是，这是我的所有个人邮件，包括来自于银行和零售商的、自动的和电脑生成的邮件等。虽然Google没有这些消息，它也说明了我的真正“个人的”邮箱来自于Google的比例很可能相当高了。

我也想知道我发送的邮件有多少经过了Google。我通过查看收件箱里的、我回复的邮件来搞定。如果我愿意假定，无论我是否回复了从Google发送来的邮件，他最终还是要回到Google，这就是可行的。在某种程度上，由于我几乎没有回复过来自于零售商和银行的邮件，这样做会带来这些邮件的问题。在这一点上，它也反映出了更为真实的个人邮件的测量方法。

我已经在下图分析出了我收到的来自于Google的邮件比例，所有邮件占比（上）和我回复的邮件占比（下）。图中，点的大小代表累计的邮件总数所占的比例。重申，我增加了LOESS移动平均线。

[![邮件中Gmail占比图2](http://www.labazhou.net/wp-content/uploads/2014/05/emails-gmail-prop-over-time.png)](http://www.labazhou.net/wp-content/uploads/2014/05/emails-gmail-prop-over-time.png)

结果大得惊人。无论我每年花费数百美元、数个小时的工作来托管我自己的邮件服务器与否，Google拥有了我一半的个人邮件！去年，Google传送了我回复的邮件的比例是57%。从2006年起，每年它们传送了三分之一的我的回复邮件，2010年之后这一比例更高。在上图，存在比例正在下降的迹象。截止到今年，我回复的邮件只有51%的比例来自于Google。

数量比我想象得要高，多少折射出悲观的消息。它们表明了，在团体沟通之间考虑隐私和自治是多么地复杂。在被斯诺登泄密和其它任何事情惊醒时，无论你是否真的想让Google拥有你的所有邮件，除了鼓励其他人去考虑，我不确定还能做什么。Google拥有了我的一半邮件。

如果你想自己运行该分析工具，欢迎[使用借助Python和R来生成数字和图表的代码](http://projects.mako.cc/source/?p=gmail-maildir-counter)。

原文地址：[http://mako.cc/copyrighteous/google-has-most-of-my-email-because-it-has-all-of-yours](http://mako.cc/copyrighteous/google-has-most-of-my-email-because-it-has-all-of-yours)



	
  * 注1：LOESS曲线是另一种重要的探查图形工具，它添加一条平滑曲线到散布图，以便更好地理解依赖模式。loess 一词是“局部回归”（local regression）的缩写。


