---
author: viviworld
comments: true
date: 2014-01-21 09:37:49+00:00
layout: post
link: http://www.labazhou.net/2014/01/why_should_you_care_about_nodejs/
slug: why_should_you_care_about_nodejs
title: 为什么你要关注Nodejs
wordpress_id: 212
categories:
- 编程
tags:
- .net
- javascript
- nodejs
---

我知道我的很多读者都是讨厌JavaScript、支持.NET的活跃核心的家伙，因此请容许我简单谈论一下[Nodejs](http://nodejs.org/)。

清楚起见，我在本文不主张任何东西。做为一个成熟的开发者，你看到社区正在发生的一切，对于为什么有些东西是新的、以及新想法是如何被新技术催生出来，我想这是重要的。我希望本文能够带来一些。


### 认识Nodejs


简单讲，Nodejs是为JavaScript提供的运行时，它鼓励非阻塞I/O和快速的网络。Nodejs本身不是用JavaScript写的，它只是用Chrome的V8引擎来执行JavaScript。引擎提供了很多当今强大的工具（比如Bower，GruntJS等），但是主要用在简单的web服务器平台。


### Nodejs有魔法般的可伸缩性吗？


在我第一次听到Nodejs时，大家的讨论一直是你怎样才能用它产生一个快速的、可伸缩的网站/APP。然而这是真的，它的本性没有魔法。诀窍是Nodejs鼓励非阻塞的行为。Nodejs本身是单线程的（尽管你可以运用它的多个实例），但是它鼓励你去考虑事件和回调等事情。当等待这些回调时，线程是不忙的，因此它能够承载比传统web服务器（比如IIS或Apache）每个线程更多的流量。

Nodejs是一个令人钦佩的技术，我认为它真正的好处是，它不依赖线程池来完成智能异步。它鼓励在服务器端写异步的代码。如果请求在等待一个操作，它就能够释放线程去处理另一个请求。

这意味着你能够容易地用Nodejs每个线程来构建更好的可伸缩性。Nodejs的吞吐量并不一定比你从IIS或Apache得到的多，这是因为后者在这个问题上可以产生更多的线程。Nodejs不能把横向扩展的概念做为一个明显的选择，因为它取决与被独立应用的情景。这有解决方案，只不过这些方案就是你在寻找或‘购买“的（比如Azure，AWS等）。


### .NET能从Nodejs学到什么


由于我能够说（我对这些技术做了深入的研究），我认为.NET正在借鉴Nodejs。这就是为什么有那么多[OWIN](http://owin.org/)的东东，结合OWIN和[scriptcs](http://scriptcs.net/)就可以使.NET非常接近Nodejs的愿景。但是做为开发者，我能学到什么？

如果你像我一样，在ASP.NET（等等）有很好的技能和经验，我非常想从Nodejs的优点中获益。你应该考虑的一个概念是非阻塞I/O，和事件回调。它大量存在于ASP.NET MVC 和 Web API中的异步控制器。开发者通常不用担心异步，如果它们不是花很长时间的话（像调用另一个web服务器或调用一个数据库），但是我认为你应该考虑你发起的每一次异步调用所花费的任何时间。Windows团队开始考虑，WinRT中任何超过50ms的调用都要求你通过一个异步的API来实现。C#异步特性很容易使用，因此我们在web开发中，应当用同样的方法。据我所知，多数控制器应该是异步的，特别是EF6支持异步请求了。


### 你应该看Nodejs吗？


是的。

好的，或许多点儿是有用的。我认为你应该了解Nodejs并理解它的哲学。你或许找到了某种类型的项目（比如，API或网络项目），Nodejs是一个伟大的model，你应当部署Nodejs项目。但是我至少认为Nodejs编程将教会你如何考虑非阻塞I/O。不管你怎样开发软件，这都是很好的技能。

原文地址：[http://wildermuth.com/2014/01/17/Why_Should_You_Care_About_NodeJS](http://wildermuth.com/2014/01/17/Why_Should_You_Care_About_NodeJS)
