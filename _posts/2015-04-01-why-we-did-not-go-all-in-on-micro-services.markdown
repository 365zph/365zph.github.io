---
author: viviworld
comments: true
date: 2015-04-01 06:42:37+00:00
layout: post
link: http://www.labazhou.net/2015/04/why-we-did-not-go-all-in-on-micro-services/
slug: why-we-did-not-go-all-in-on-micro-services
title: 为什么没有全部押宝在微服务上
wordpress_id: 1793
categories:
- 编程
tags:
- DevOps
- nodejs
- Thrift
- 优化
- 团队
- 微服务
---


	
  * 原文地址（original source）：[https://medium.com/@joelcox/why-we-did-not-go-all-in-on-micro-services-65b080ba02a5](https://medium.com/@joelcox/why-we-did-not-go-all-in-on-micro-services-65b080ba02a5)

	
  * 作者（author）：[https://twitter.com/joelcox](https://twitter.com/joelcox)

	
  * 作者网站（website）：[http://joelcox.nl/](http://joelcox.nl/)


很容易迷失在最新趋势中。在为积极推出的产品起草架构时，最近的（微）服务【注1】的复兴让我蠢蠢欲动。在这个新项目上动手，一定是伟大的方式。

做为工程师，你必须能够后退一步，看下蓝图，并基于已有信息做出理性的判断。一旦当初的激情耗尽，我将严重怀疑我最初的设计。下面是原因。


### DevOps的投入


拥有多种服务、而不是一个庞大的应用程序，需要在保持运转方面投入额外努力。对于服务发现（service discovery【注2】）、日志、多种应用服务器和潜在多样化的技术栈之类的事情，没有更多的运营经费。

你的团队应该在 DevOps【注3】思维上下定决心。我们仍然为这个项目组合了一个团队，找到优秀的工程师已经是很难了。将另一项要求增加到我们的“技能”清单，不会让这种搜索变得简单。他们当中某些人可能对 DevOps 工作感兴趣，但是这一定不能被强迫。


### 做好事情或回家


对于面向服务的架构，你应该明确地规划编写异步代码来改善吞吐量。然而，大部分在传统 web 后端方面有经验的工程师，对于异步编程的经验不足。

我还有个建议，当编写异步代码时，如果有可能，你应该选择天然支持这种范例的编程语言。当然，你可以把事件循环放到 Ruby 或 Python 里，但是你难道不愿意用 Node.js 或 Go 之类的语言吗？在雇佣团队新成员时，这将成为另一项要求。


### 工程领域


服务高度解耦，让团队运转是更伟大的隔离。当处于更大组织时，这是不错的特性，但是只有 3-4 人时，一定不是必需的。我甚至讨论过，让更多的人（在一定程度上）共用一套代码库将提高产品质量。

另外，服务之间的通信必须要定义（我喜欢把 [Thrift](https://thrift.apache.org/) 做为 RPC 框架）。当你仍然在具体化产品细节时，这些接口能够快速更改，难以在代码库之间协调。当应用程序成熟时，这个问题遇到的频率就少了，额外的考虑应该放在跨服务的后向兼容维护方面。


### 不需要的网络规模（至少现在是这样）


面向规模编写软件是有趣的，不过可能起到反作用。在面向服务的架构中，你能够很容易地水平扩展每个独立的服务，进而提高总体系统的吞吐量。


<blockquote>“过早优化是万恶之源。” ------Donald Knuth</blockquote>


以这样的方式开发应用程序，可以处理一些负载，或许不太需要，有些浪费了，不过有一些替代方式。把模块当做外部服务来设计，你就能克服随后全新重构的痛苦。随着时间的进行，这些模块可以被放在隔离的服务里。


### 结论


如果你可以接触到[一个工程师团队](http://www.labazhou.net/2015/01/hidden-costs-that-engineers-ignore/)，他们拥抱 DevOps，致力于必须面对规模问题的系统，请记得加入微服务的潮流中。如果不是这种情况，请一定将这种架构记在心里，但也不要忘了，鱼和熊掌不可兼得。

感谢阅读。我也乐于[在 Twitter 上听到你的想法](https://twitter.com/joelcox)！



	
  * 注1：In computing, microservices is a software architecture design pattern, in which complex applications are composed of small, independent processes communicating with each other using language-agnostic APIs. These services are small, highly decoupled and focus on doing a small task. [http://en.wikipedia.org/wiki/Microservices](http://en.wikipedia.org/wiki/Microservices)

	
  * 注2：[http://en.wikipedia.org/wiki/Service_discovery](http://en.wikipedia.org/wiki/Service_discovery)

	
  * 注3：DevOps（英文Development和Operations的组合）是一组过程、方法与系统的统称，用于促进开发（应用程序/软件工程）、技术运营和质量保障（QA）部门之间的沟通、协作与整合。它的出现是由于软件行业日益清晰地认识到：为了按时交付软件产品和服务，开发和运营工作必须紧密合作。[http://zh.wikipedia.org/wiki/DevOps](http://zh.wikipedia.org/wiki/DevOps)


