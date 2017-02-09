---
author: viviworld
comments: true
date: 2014-06-26 00:46:36+00:00
layout: post
link: http://www.labazhou.net/2014/06/introducing-lotus/
slug: introducing-lotus
title: Lotus简介
wordpress_id: 792
categories:
- 编程
- 软件
tags:
- Lotus
- MVC
- ruby
- Ruby on Rails
- 框架
---

一年半以前，我对Ruby的最先进的web开发感到沮丧。在业余时间，我悄悄地开始引入新思想，不认为什么是理所当然的，破坏并从头开始好多次，直到这个软件在一个美丽的API里提炼出来。

**遵循对不必要的东西做减法的过程**，我花了十年才到达这一步。为了取得模块化，为了用坚固的设计平衡优雅与性能、便利而进行了不计其数的优化。

每个抉择都是依据真实环境而定。一直是痛点的、或在我和其他开发者经验看来是好选择的用例。

但是这个项目在我的计算机里呆了太长时间。

由于这个原因，在今年年初，我[宣布](http://lucaguidi.com/2014/01/01/announcing-lotus.html)了这个项目极其缓慢的发布日程。每月我发布一个类库，因为我想和其他开发者分享每次努力的结果，并在Ruby社区产生一个讨论。现在，六个月以及六个框架之后，我自豪地介绍主要元素：**Lotus**。

这是[一个完整的web框架](http://lotusrb.org/)，特别注重面向对象设计和易测性（testability）。如果你使用Lotus，你采用较少的DSL和更多的对象、没有猴子补丁【注1】，MVC层之间关注点的隔离。每个类库被设计成小巧（不超过500的代码行数）、快速和可测试。

具备了一种HTTP路由功能的[Lotus::Router](https://github.com/lotus/router)，还有用于控制器和action的[Lotus::Controller](https://github.com/lotus/controller)。他们都采用[Rack](http://rack.github.io/)协议，因此它们被用于现存代码库，或为了小API端点组合在一起，又或者，一起组合为一个全堆栈Lotus应用程序。

[Lotus::View](https://github.com/lotus/view)是标记隔离view对象和template的、面向Ruby的第一个类库。而[Lotus::Model](https://github.com/lotus/model)，与仓库、数据映射以及适配器一道，有助于从持久化中远离主要的特定逻辑。

我们有无限个组合。根据可复用原则，**小的组件有着巨大的优势**。

这些框架的力量在Lotus应用程序中被组合在了一起。

微服务【注2】是核心。一些独立的应用程序能够一起存在于相同的Ruby过程里。

Lotus有一个智能的框架复制的机制，所有类库可以被使用多次。随着代码库的增长，它能够容易地划分到较小的、可交付的产品里。

Lotus拥有[广泛的](http://rdoc.info/gems/lotusrb)[文档](https://github.com/lotus/lotus/blob/master/README.md)，覆盖了所有支持的架构。


### 未来


Lotus仍然是一个年轻的框架，需要到达代码成熟的某个程度。根据我对未来功能的愿景，它会通过从真实世界的应用程序收集的[反馈](https://gitter.im/lotus/chat)中获得改善。

还有，从今天起，我会给那些对Lotus感兴趣的公司和个人提供**免费咨询时间**。

为了保持更新最新的发布，收到代码示例，实现细节和公告，请考虑订阅[Lotus的邮件列表](http://lotusrb.org/mailing-list)。



	
  * 原文地址：[http://lucaguidi.com/2014/06/23/introducing-lotus.html](http://lucaguidi.com/2014/06/23/introducing-lotus.html)

	
  * 注1：猴子补丁的含义是指在动态语言中，不去改变源码而对功能进行追加和变更。[http://my.oschina.net/chihz/blog/214183](http://my.oschina.net/chihz/blog/214183)

	
  * 注2：[http://www.infoq.com/cn/news/2014/06/microservices](http://www.infoq.com/cn/news/2014/06/microservices)


