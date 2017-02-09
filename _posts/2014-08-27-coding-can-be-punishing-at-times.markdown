---
author: viviworld
comments: true
date: 2014-08-27 00:56:40+00:00
layout: post
link: http://www.labazhou.net/2014/08/coding-can-be-punishing-at-times/
slug: coding-can-be-punishing-at-times
title: 伴随着AngularJS的压力，写代码常常是吃力的
wordpress_id: 937
categories:
- 编程
- 软件
tags:
- AngularJS
- google
- javascript
- jquery
- Karma
- O’Reilly
- StackOverflow
---

我这里提到的观点是程序员相当熟悉的。我来自90年代早期的C语言世界。有很少的可用工具，我不得不为每个小东西写一个链接列表。我乐此不疲，毫无怨言。现在看起来蠢多了。但是，这就是世界本来的样子，你不得不一点一点地写代码。

如今编程情景与往日大大不同了。因为开源、StackOverflow，当然还有Google，产生了很多协作。每个问题都被人问过了，还有一堆回答。对于程序员这算作快乐的时光，可用的框架和工具的数量十分惊人。

我上手了Servlets、JSP、JQuery、JS、AngularJS等等，到现在，我在AngularJS上花了一年多的时间。我有一分为二的观点，不是关于它能解决什么问题，而是对于来自各个社区的程序员所能获得的信息。有太多不同的声音和不同的方式在解释着同样的问题。我担心我在这里写的观点也能引发讨论。与K&R C【注1】做个比较，一本也是唯一一本权威的、精确的、清晰的解释C语言的书。当然，还有其它书。但是，解决了编程结构的、非常详细的语法和语义的语言可以在一本小书里完美地表达出来。如何根据它去解决问题，在很多带有实例的其它书里做了解释。就是这样。

现在，有了网络，每个人都成为了作家。每个问题Google都能抛出一百多万个链接。那么你究竟怎么才能就某个问题给出一个简单、清晰的答案？答案是非常简单的，只是迷失了，我的意思是，迷失在了信息的海洋里。这是你为民主付出的代价。数百万的声音，无数的东东。看看，我并不同意我要说的观点。

到处都有AngularJS的代码示例和demo，如果你对JavaScript认识足够多，可以理解JavaScript设计模式、控制反转（Inversion of Control，缩写为IoC）、范围阶层（scope hierarchy），依赖注入【注2】、面向对象JS以及发布/订阅通知【注3】等等，就好像能够做得很好。然而，并没有一样东西来给你解释其原理以及讨论AngularJS如何引入这些方面的。拥有海量的demo和特定例子。O'Reilly的AngularJS书根本没有覆盖到以一种简单方式、让所有人理解的基础方面。这只是我曾经看过的唯一一本书。很多次，语法杂乱，难以理解。只有你花了1年时间才能弄明白。你也被一直混在一起的中括号、大括号和$符搞晕。胆小的肯定就躲了。

由于存在很多已有的、解决问题的不同变体，在某人想解决头疼的业务问题时，它放大了这种痛苦。语法令人悲催，如果你是新手，刚刚接触的时候，能够带来进度上的巨大延期。没有来自AngularJS团队或提供支持的其他人的视频，这本应该通过简单地阅读语法来简化生活的，却徒增烦恼。

还有这是关于测试的喋喋不休，测试所有地方减轻压力是不错。AngularJS有来自于像Yo、Grunt、Bower、Karma、Jasmine等社区的稳定的工具支持。我后来才试用了一些工具。特别地，我发现就像使用AngularJS框架一样，这些工具也缺乏解释其原理以及与其它工具如何关联的简化文档。

举个例子，Yo是一个脚手架服务，用来生成AngularJS文件的模板，它与Bower交互来下载依赖项、用Grunt运行任务。用简单的可视化图表就可以解释清楚，而不需要立即深入配置的、大量的文字或demo示例。

毫无疑问，一旦你熟悉了，它们会简化工作。但如我所言，对新手就不是这样了，它们看到要尝试的数量和初期花费的时间就敬而远之了。

我请求过这些工具的作者，让他们用更为简洁的英语、可视化的东东以及例子来提供更加简单、更加基本的说明，而不仅仅只是绝对没有解释、反而期望读者自己搞清楚的、demo的代码片段。

为了明白什么是更好的解释，我给出关于AngularJS作用域的链接。这更为基本、图文并茂以及涵盖了大量脚本。[https://github.com/angular/angular.js/wiki/Understanding-Scopes](https://github.com/angular/angular.js/wiki/Understanding-Scopes)

如果你认为我是在抵制AngularJS，那就错了。我尊重团队所付出的努力，尊重不计成本解决问题的社区，尊重他们解决纠缠在一起的HTML/CSS/JS来让生活更美好的各种方式。我用了，并从中受益。唯有的抱怨就是理解它们（我这里说的理解，是指用简单的方式搞清楚它们）所遇到的、刚开始的难度，新手能够编写复杂行为的代码，会碰到整个网络协作中的术语和问题，让人费解。

这些新工具需要在文档内容上有更大改善，这些工具是由在StackOverflow回答问题的聪明人编写的，不要只是就 为什么展望一个东东以及他们如何用每个人可以理解的方式解决问题 张贴文档。

为了结束本文，我举个例子，我花了一天才搞定某个问题的例子。我当时使用Yo/Grunt运行着关于AngularJS指令的Karma测试，我出错的地方是，在karma.conf.js，我把带有AngularJS的脚本放在了我自己脚本的后面，结果没有编译我的指令，也就没有生成HTML，JQuery也找不到。对于创造这些工具的人来说，这可能是一个简单的、低级的错误。还有，这可能与AngularJS或Karma没有关系，可能这是JS里依赖载入的问题。然而，既然我对这些都不熟，我只好搜寻了每个地方，从语法到配置文件、到StackOverflow、Google，不知疲倦地尝试了很多不同的选项，直到最后，关于指令没有被生成的HMTL错误才被我发现。

天哪！生活应该比这更美好的。



	
  * 原文地址：[http://productionjava.blogspot.com/2014/08/coding-can-be-punishing-at-timeswith.html](http://productionjava.blogspot.com/2014/08/coding-can-be-punishing-at-timeswith.html)

	
  * 注1：K&R 是C语言的开发者Brian W.Kernighan,Dennis M.Ritchie （人名），C是指他们的著作《C程序设计语言》，被誉为C语言"圣经"，所有C程序开发人员都必看的书，但书内容过于简洁，不适用于初学者。

	
  * 注2：控制反转（Inversion of Control，缩写为IoC），是面向对象编程中的一种设计原则，可以用来减低计算机代码之间的耦合度。其中最常见的方式叫做依赖注入（Dependency Injection，简称DI），还有一种方式叫“依赖查找”（Dependency Lookup）。[http://zh.wikipedia.org/wiki/%E6%8E%A7%E5%88%B6%E5%8F%8D%E8%BD%AC](http://zh.wikipedia.org/wiki/%E6%8E%A7%E5%88%B6%E5%8F%8D%E8%BD%AC)

	
  * 注3：发布/订阅（Publish/subscribe 或pub/sub）是一种消息范式，消息的发送者（发布者）不是计划发送其消息给特定的接收者（订阅者）。[http://zh.wikipedia.org/wiki/%E5%8F%91%E5%B8%83/%E8%AE%A2%E9%98%85](http://zh.wikipedia.org/wiki/%E5%8F%91%E5%B8%83/%E8%AE%A2%E9%98%85)


