---
author: viviworld
comments: true
date: 2014-03-28 01:01:19+00:00
layout: post
link: http://www.labazhou.net/2014/03/clojure-web-security-is-worse-than-you-think/
slug: clojure-web-security-is-worse-than-you-think
title: Clojure的web安全比你想象的还要差
wordpress_id: 471
categories:
- 安全
- 编程
tags:
- Clojure
- friend
- HMAC
- lib-noir
- md5
- Ring
- XSS
---

ClojureWest大会结束了，[Aaron Bedra](https://twitter.com/abedra)发表了题为 [Clojure.web/with-security](http://www.youtube.com/watch?v=CBL59w7fXw4)的演说。如果你用Clojure开发web应用程序，你必须看这个视频。现在就看。

这篇博客综合了Aaron的讲话笔记和一些我自己的想法。


### 有多差？




<blockquote>“Clojure web应用程序是我曾经见过的、在安全方面做得最差的。”
“……像PHP级别……没有框架级别，安全。”
---Aaron Bedra</blockquote>


Aaron宣称，根据可供选择的类库来倒腾你自己的（web）栈，这种Clojure思想方法导致了系统级的安全问题。我们有碎片，但是没有把它们组合成一个强健的、可靠的框架。相反，开发者挑选不同的类库，不是所有的类库都提供了完整的覆盖或健全的安全默认项。


### 密码管理


password/crypt相关操作的前三名类库（[crypto-password](https://github.com/weavejester/crypto-password), [friend](https://github.com/cemerick/friend) 和 [lib-noir](https://github.com/noir-clojure/lib-noir)）不支持HMAC，不需要逐个更新就可以实现从一个模式迁移（MD5到SHA1到……），通常具备有限的选项。

Aaron推荐的不是要有多个选项可供选择，而是Clojure社区致力于一个（他推荐crypto-password），让friend和lib-noir依赖它。我认为这是明智的想法。


### 会话管理


Clojure web应用程序通常依赖Ring处理会话管理。Ring不能提供持久会话管理（基于数据库，保存/验证合法的会话cookie）来阻止重放攻击（replay attack），会话cookie不能默认成http only标识（允许XSS攻击盗取cookie）。

对于Ring而言，安全的会话管理只有非常少量的、被证明过的最佳实践。


### 身份验证


[friend](https://github.com/cemerick/friend)类库就是基于Ring的web应用程序在身份验证管理上的、事实上的类库，它基本满足了。不幸的是，friend不支持更加复杂的身份验证策略，在基于Ring之外的情况下就表现不好了。

我们不要用你自己的独立身份验证类库来填补这个空白，而应该反馈给friend。这里我被人提醒了Ruby的[omniauth](https://github.com/intridea/omniauth)。


### XSS


数量庞大的Clojure HTML模板类库提高了持续防护XSS攻击的难度（转义HTML标签，控制标签被转义或不被转义）。

最终有太多的可供选择的模板类库。开发组应该挑选一个并坚持用下去。在选择一个模板类库时，要把XSS控制的支持做为一个考虑因素。


### 安全头


在Clojure web应用程序，没有集中的类库来居中管理安全头。安全头可以在Ring里手动设置，但是你不得不知道配置的正确位置。Aaron指出，Ruby的[secureheaders](https://github.com/twitter/secureheaders) gem就是Clojure所需的一个例子。

更新：Dhruv Chandna已经为其Ring中间件类库推出了一个更新，增加了安全头：ring-secure-headers。做得不错！随后我会详细研究的。


### 总结


我的结论：开发安全性高(参考[ OWASP Top Ten List of Security Issues ](https://www.owasp.org/index.php/Top_10_2013)和 [OWASP Testing Guide](https://www.owasp.org/index.php/OWASP_Testing_Guide_v4_Table_of_Contents))的Clojure web应用程序是几乎不可能的，当你决定这样做的时候，是很痛苦的。

建立安全的Clojure web应用程序需要更加容易点儿、需要集成了安全的框架，而不是孤立的类库！我们已经有了一些标准部件（crypto-password，friend），但是更大的开发和集成仍然是有必要的。

原文地址：[https://hackworth.be/2014/03/26/clojure-web-security-is-worse-than-you-think/](https://hackworth.be/2014/03/26/clojure-web-security-is-worse-than-you-think/)
