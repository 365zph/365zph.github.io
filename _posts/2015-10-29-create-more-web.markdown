---
author: viviworld
comments: true
date: 2015-10-29 07:54:05+00:00
excerpt: 我从来无意于成为 REST 或 HTTP 布道者。你越是彻底地利用该协议，你最终就越多地符合 REST 约束，因为 HTTP 的设计是 REST
  的基础。
layout: post
link: http://www.labazhou.net/2015/10/create-more-web/
slug: create-more-web
title: 创造更多的 web
wordpress_id: 2683
categories:
- 网络
tags:
- api
- http
- REST
- 维基百科
---


	
  * 原文地址（original source）：[https://www.pandastrike.com/posts/20151019-create-more-web](https://www.pandastrike.com/posts/20151019-create-more-web)

	
  * 作者（author）：[https://twitter.com/deliciousbamboo](https://twitter.com/deliciousbamboo)





* * *



我从来无意于成为 REST 或 HTTP 布道者。然而，我深信，web------互联网就建立其上------可能是继印刷术以来、影响最为深远的技术发展。这也是「web is broken」让我感到如此烦恼的原因。web 没有被破坏------它比以往都要好。它还不完美，但是我认为，答案不会退回到技术孤岛的世界了。然而，对我而言，web 连接到 REST 架构的风格，并不总是明显。事实上，直到最近，我还未能向你做出解释。


### 我为什么关心？


毕竟，你可以无需满足 REST 约束就能使用 HTTP。当然，你越是彻底地利用该协议，你最终就越多地符合 REST 约束，因为 HTTP 的设计是 REST 的基础。但是，这根本上还是循环论证[note]循环论证（circular argument）、循环推理（循环推论；circular reasoning）、或循环证成（循环证立；circular justification），是论点的真确性最终由自身支持的推理方式循环论证或循环推理有时也泛指包括循环证成、循环因果、循环定义、循环解释等各种有循环形式的陈述。[https://zh.wikipedia.org/wiki/%E5%BE%AA%E7%92%B0%E8%AB%96%E8%AD%89](https://zh.wikipedia.org/wiki/%E5%BE%AA%E7%92%B0%E8%AB%96%E8%AD%89) [/note]。当然，随着协议的发展，HTTP 已经取得了划时代的成功。这当然说明了其研究价值。但是仍然没有回答这个问题。为什么 REST 风格如此地重要？为什么完全发挥 HTTP 协议的效用如此重要呢？为什么我们发现忍不住要花时间[对其解释](https://www.pandastrike.com/posts/20131211-http-made-simple)呢？或者解释与之相关的[开发工具](https://github.com/pandastrike/jsck)、[资源库](https://github.com/pandastrike/pbx)和[框架](https://github.com/patchboard)呢？


### 一次显现


Roy Fielding 是 HTTP 规范的主要作者以及 REST 风格的创建者，[在最近的一次采访中](http://www.infoq.com/articles/roy-fielding-on-versioning)，为我提供了答案。


<blockquote>关于如何使用一种风格来开发面向 web 的应用程序，它可以长期良好地运行，而且相应地能够创造更多的 web（更多可访问的资源），因此广为人知。我的建议仍然是 REST。</blockquote>


这里的循环论证就是「创造更多的 web」。如果你认为 web 是一个巨大的进步（继印刷术之后最伟大的进步），你自然就喜欢创造更多的 web。值得一提的是，web 是那些得益于网络效应[note]网络外部性（英语：network externality），又称网络效应（英语：network effect），或需求方规模经济（英语：demand-side economies of scale），指在经济学或商业中，消费者选用某项商品或服务，其所获得的效用与“使用该商品或服务的其他用户人数”具有相关性时，此商品或服务即被称为具有网络外部性。 最常见的例子是电话或社群网络服务：采用某一种社交媒体的用户人数越多，每一位用户获得越高的使用价值。[https://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E5%A4%96%E9%83%A8%E6%80%A7](https://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E5%A4%96%E9%83%A8%E6%80%A7) [/note]的技术之一。

例如，根据网络效应，我现在只能链接到维基百科上的一个词条。回到百科全书还是商业上售卖的 DVD 时，我是做不到的，你或许还没有买到呢。维基百科词条的存在，为我的博文增加了价值。

更广泛地说，从我的文章里链接到越多的 web，它就变得越丰富。做为回报，这种丰富就驱使人们使用 web 而非其它东西。他们在 feed 里阅读有兴趣的内容，他们通过点击发现更多的内容。

这就激励人们把他们的内容放在 web 上供别人访问，创造更多的 web，等等。


### 然后呢……？


这就是设计资源相关的 API 变得如此有价值的原因。我们倾向于认为 API 不同于 web 页，这就成了自我实施的主张。我们创建 API，它只是把 HTTP 做为传输。有时候它们看起来多多少少像美化的 RPC，有时候它们像[面向对象的 RPC](https://zh.wikipedia.org/wiki/CORBA)，有时候像[数据库查询](https://zh.wikipedia.org/wiki/SPARQL)。正如你看到的，API 和 web 页是不一样的，后者完全没有抓住要领。

REST 正面对的问题是，如果它们是 web 页，又该如何呢？

如果 API 是 web 页，它们就能创造更多 web。正如我们已经看到的，它使得现有 web 变得更好。

用你的 API 创造更多 web，需要很多工作。我们的资源库和工具简化了这一工作，但是我们还有很长的路要走。如果我们联手起来，我们就减轻独立开发者的负担，默认状态就能创造更多 web。

但是，如果我们坚持摒弃和拒绝世界上最成功的应用程序协议 HTTP，并发明我们自己定义的变量，比如 [Realy](https://facebook.github.io/relay/)、[Falcor](https://github.com/Netflix/falcor)、[JetStream](https://github.com/uber/jetstream)，那么，我们就永远无法走到那一步。API 生态的网络效应就永远无法累积起来。


### Yoder 第十定律[note]笔者通过 twitter 联系了原文作者，他说，引用的文字是格林斯潘的，但是，删除线以后增加的那一版，据作者猜测应该是 Yoder 提出的：[https://twitter.com/deliciousbamboo/status/659912242805104640](https://twitter.com/deliciousbamboo/status/659912242805104640)[/note]


对于早期打造分布式系统的努力，REST 和 HTTP 也从中吸取了大量经验并编入规范。我们已经尝试过 RPC、面向对象的 RPC 和查询语言，或许 HTTP 运作良好是有原因的，或许我们吸取了过去犯错的教训，或许你也能从中学到什么。我喜欢把格林斯潘第十定律[note]格林斯潘第十定律是计算机编程领域，尤其是编程语言领域的一句格言：「任何 C 或 Fortran 程序复杂到一定程度之后，都会包含一个临时开发的、不合规范的、充满程序错误的、运行速度很慢的、只有一半功能的 Common Lisp 实现。」这表现了 Lisp 语言的灵活性和可扩展性，它包含了理论上编写复杂计算机程序需要的所有功能。而其他编程语言的核心实现却不能提供开发复杂程序的关键性功能支持。[https://zh.wikipedia.org/wiki/%E6%A0%BC%E6%9E%97%E6%96%AF%E6%BD%98%E7%AC%AC%E5%8D%81%E5%AE%9A%E5%BE%8B](https://zh.wikipedia.org/wiki/%E6%A0%BC%E6%9E%97%E6%96%AF%E6%BD%98%E7%AC%AC%E5%8D%81%E5%AE%9A%E5%BE%8B) [/note]应用到 HTTP：


<blockquote>任何 <del>C或Fortran程序</del> API 复杂到一定程度之后，都会包含一个临时开发的、不合规范的、充满程序错误的、运行速度很慢的、只有一半功能的 <del>Common Lisp</del> HTTP 实现。</blockquote>




### 不要破坏 web


但是我已经意识到，激发我为 REST 和 HTTP 布道的原因还不在于架构上的好处。原因在于直觉，用我们开发的每一个 API，就能创造更多的 web。我们已经有了一个良好的开始，不管 API 采用什么愚蠢的方式，它们甚至都能在 web 上访问到，这就是让人称奇的地方。

但是，我们现在的所作所为让我们想起了网站的早期时代，那时候开发者们习惯了「破坏 web」。比如，如果你的 web 应用上的返回按钮不好使了，你就破坏了 web。或许到了今天有了更好的类比，web 应用程序不是[响应式设计](https://en.wikipedia.org/wiki/Responsive_web_design)。REST 给你提供了指南，不但总结了开发分布式系统的[最佳实践](http://www.labazhou.net/2015/05/what-is-a-best-practice-in-software-development/)，而且确保你不会用 API 破坏网络。


### 回馈别人


尽管 web 给你很多了，但是如果你不关心 web、如果你认为创造更多 web 没有多少价值、如果你认为没有好办法来回馈别人，那么很明显你不关心创造更多 web。但是如果你关心 web，就要致力于创造更多 web，在此过程中尽力不要破坏它。这也是 REST 和 HTTP 要帮你做的事情。


### 一个 API，一次投票


你的选择影响着我们所有人。每一个创造更多 web 的决定，除了是对免费、开放技术的投票，最终也是对免费、开放社会的投票。每一个放弃这种技术的决定，也是回到过去的投票------每个厂商和他们自己独有的技术孤岛。这只是一次投票，的确如此，但是，就总体而言，它让一切有所不同。这就是我们把 web 摆在首位的原因，因为像你这样的开发者们决定这样做。

或许我们已经有了足够多的 web，或许如果 API 不是更多的 web，也没关系。但是我们现有的 web，可能只是它应有规模的一半、四分之一、八分之一……

对于 web 应有的样子，我充满期待。
