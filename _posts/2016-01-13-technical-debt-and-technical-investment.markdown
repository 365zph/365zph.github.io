---
author: viviworld
comments: true
date: 2016-01-13 01:21:26+00:00
excerpt: 一些人把技术债务的说法用作糟糕的代码。这不太正确。技术债务是某种原因导致的糟糕代码。有时候，你用错误的方式，以更快地完成工作；有时候更快速地完成，的确重要。当速度的好处超过维护成本或重构糟糕代码时，你会选择承担债务。技术债务和技术投资均有风险。
layout: post
link: http://www.labazhou.net/2016/01/technical-debt-and-technical-investment/
slug: technical-debt-and-technical-investment
title: 技术债务和技术投资
wordpress_id: 3008
categories:
- 管理
- 编程
tags:
- Cycle.js
- Elm
- javascript
- PureScript
- RxJS
- 技术债务
- 技术投资
---


	
  * 原文地址（original source）：http://jamison.dance/12-31-2015/technical-debt-and-technical-investment/

	
  * 作者（author）： lexical NOPE（[@jergason](https://twitter.com/jergason)）





* * *





### 技术债务


技术债务，是软件工程讨论折衷方案时所用到的一种工具。当你遇到技术债务【注1】时，你就会堆积一些快速、肮脏的代码，它们更难以维护、或拉低了图中的效率曲线。随着时间的推移，和你一开始用正确的方式开发相比，维护快速、肮脏代码或基础架构的成本，要更高一些。你能够感受到此言不虚，因为我画了一张图。

[![技术债务](http://www.labazhou.net/wp-content/uploads/2016/01/tech-debt-600x450.png)](http://www.labazhou.net/wp-content/uploads/2016/01/tech-debt.png)

一些人把技术债务的说法用作糟糕的代码。这不太正确。[技术债务是某种原因导致的糟糕代码](http://www.labazhou.net/2014/07/developer-inequality-and-the-technical-debt-crisis/)。有时候，你用错误的方式，以更快地完成工作；有时候更快速地完成，的确重要。当速度的好处超过维护成本或重构糟糕代码时，你会选择承担债务。


### 技术投资


技术债务的对立面是技术投资【注2】。对于技术投资而言，你当下放慢速度，是为了将来能够加快速度。或许你选择编程语言或 web 框架。你的团队花时间学习新工具，但是在某种程度上，如果你选择得当，它们就更有效率。下图是没有标数字的手绘图，它无可置疑地证明了这一点。

[![技术投资](http://www.labazhou.net/wp-content/uploads/2016/01/tech-investment-600x450.png)](http://www.labazhou.net/wp-content/uploads/2016/01/tech-investment.png)


### 你需要投资


成功的产品，只会变得更加复杂。如果人们喜欢并使用你的产品，你将会增加更多功能和复杂性。对于人们愿意付费的、或大体上在使用的现有功能，是不可能移除掉的。

在最初原型阶段，工具和技巧是有生产力的，但是，有时候它会与较大型产品的复杂度发生冲突。如果你在处理复杂度方面不能投入，随着复杂度的增加，开发速度就会减缓。随着产品复杂度和团队成员的增加，技术投资能够规模化增加你的团队生产力。


### 风险


技术债务和技术投资均有风险。如果你低估了维护技术债务、或承担它所带来的好处，你的产品在长期收益方面将放慢脚步。如果你高估了技术投资的价值，你在短期内就会减缓进度，而没有长期加速。


### 好的技术投资所需条件？


如果你认同了技术投资，接下来的问题就成了「我该如何评判一项优秀的技术投资呢」？其答案可能和普通投资一样------你做不到的。你可以审核当前情况，并尽量预测未来趋势，但是，平心而论，这都是臆测。

技术上很难评判，因为我们经常期望看到立竿见影，如果我们看不到，就会放弃。计算机历史充斥着过早放弃的好思想，但是也长期散落着坏思想。

既然有了这些警告，下面给出一些预示，它们反映出 web 开发团队中属于好的技术投资。我不保证全部都是对的。


#### Elm、PureScript、或其它语言


静态类型的纯函数式编程是一种[老思想](http://haskell.cs.yale.edu/wp-content/uploads/2011/01/cs.pdf)了，它从未引起主流编程的注意。我认为，它是未来的一种方式，尤其对于客户端应用程序，更是如此。Elm【注3】 和 PureScript【注4】 正在解决文化和教育方面的问题，它们阻碍了类似语言赢得主流的使用，我觉得，在未来几年，它们当中一定会有一种语言赢得广泛的用户基数。


#### 可观察对象


这包括了类似 [RxJS](https://github.com/Reactive-Extensions/RxJS)【注5】 的技术、构建于 [Cycle.js](http://cycle.js.org/) 之类的可观察对象之上的框架，还包括在 JavaScript 应用程序里使用可观察对象来管理状态和通信的通用实践。我认为，我们在管理客户端 JavaScript 方面还没找到有效的解决方案。可观察对象貌似成了更好方式的良好选择。


#### 雇佣和指导初级开发人员


我可能要多谈一下这个问题，但是重点在于，人才市场的初级开发人员有着很低的薪水，他们常常为了找到工作而不顾一切。如果团队或公司能够和初级开发人员较有效率地协作，并帮助他们成长为高级开发人员，就会在雇佣方面获得巨大优势。


### 技术债务和技术投资


对于技术债务，你把代码搞得一团糟，随后需要自己擦干净屁股。对于技术投资，你预先理顺一切，以后你就能更有效率地工作。二者都可以被理智地使用，它们对于保持一种健康的工程师组织和文化也是必要的。

你对技术投资有什么看法？你有一些好的技术投资想法吗？



* * *



Jamison Dance 是 [Kuali Co](http://kuali.co/) 的一名软件工程师。他喜欢小猫、让计算机更聪明、以及孩子们开怀大笑的魔力。他在 [http://jamisondance.com](http://jamisondance.com/) 撰文，twitter 账号 [@jergason](http://twitter.com/jergason)，GitHub 账号 [jergason](https://github.com/jergason)。他还是 [JavaScript Jabber](http://javascriptjabber.com/) 网站上的播客。


### 注释

* 注1：原文注释翻译：对于术语「技术债务」，我所能找到的最早的引用来自于 1992 年 Ward Cunningham 写的文章，地址为：[http://c2.com/doc/oopsla92.html](http://c2.com/doc/oopsla92.html)。有意思的是，当 Ward 参与一个财务应用程序的工作时，这种想法就产生了关联。有时候，我们在和软件完全不相关的领域里，就能找到不错的比喻。
* 注2：原文注释翻译：我是在几个月前和 [Randal Bennet](https://twitter.com/randallb) 的一次讨论时第一次听到技术投资的。
* 注3：Elm 是一种函数式语言，可编译为 HTML、CSS 和 JavaScript。Elm 为函数式反应编程而设计，便于创建高可交互应用。[http://www.oschina.net/p/elm](http://www.oschina.net/p/elm) 
* 注4：PureScript 是个小巧而强大的静态类型语言，可以编译成 JavaScript。purescript 主要是由 Haskell 和 PureScript 编写的。[http://www.oschina.net/p/purescript](http://www.oschina.net/p/purescript) 
* 注5：RxJS全名Reactive Extensions for JavaScript，Javascript的响应式扩展。响应式的思路是把随时间不断变化的数据、状态、事件等等转成可被观察的序列(Observable Sequence)，然后订阅序列中那些Observable对象的变化，一旦变化，就会执行事先安排好的各种转换和操作。[http://www.w3ctech.com/topic/1298](http://www.w3ctech.com/topic/1298)
