---
author: viviworld
comments: true
date: 2015-06-09 08:40:38+00:00
excerpt: 我经常在工作中用到 Google 的相对较新的 Go 语言。我非常肯定，Go 不是解决所有问题的语言，但是对于我的这个项目、以及我看到的其它很多项目，Go
  一直都是我的工具集中的得力工具。
layout: post
link: http://www.labazhou.net/2015/06/experiences-in-writing-an-integration-service-in-go/
slug: experiences-in-writing-an-integration-service-in-go
title: 用 Go 编写集成服务的体验
wordpress_id: 2149
categories:
- 编程
tags:
- api
- CMS
- Go
- google
- Goroutines
- REST
- 微服务
---


	
  * 原文地址（original source）：[http://adampresley.com/2015/06/08/experiences-in-writing-an-integration-service-in-go.html](http://adampresley.com/2015/06/08/experiences-in-writing-an-integration-service-in-go.html)

	
  * 作者（author）：[https://twitter.com/adampresley](https://twitter.com/adampresley)





* * *



在过去 6 个月，我经常在工作中用到 Google 的相对较新的 [Go 语言](http://golang.org/)。我已经编写了一些关于文件服务器和 Subversion 钩子的命令行工具，我还写了一些基于 web 的工具，比如针对内存指标的本地开发工具、代码搜索等等。最近我开始专门把 Go 用于项目中，我感觉 Go 能满足长期运行守护进程的需求，为其它应用程序提供服务。

最近我手头的一个项目，牵扯到从我的客户使用的第三方后台系统，向我们维护的一个 CMS（内容管理系统）平台提供数据。CMS 平台驱动客户的、面向用户的网站，而后台提供诸如日程、预定等工具。客户最近才迁移到这套系统，他们为了驱动销售，想让网站显示来自后台的某些数据。然而，对于复杂的情况，他们想要展示的某些数据没有存放在后台，因此我们决定在我们的 CMS 平台管理这些缺失的数据。这意味着，现在网站需要来自两个完全不同的数据源。第一个数据源支持 CMS 平台以及网站的 SQL 数据库，第二个源来自于通过 HTTP 获取后台的、基于 XML 的 API。

我们这里的思路是建立一个微服务应用，由它从 SQL 和 HTTP 源，将数据聚合到 CMS 能够使用的、单一的 REST 服务里。该微服务提供遵循 REST 范式的端点（endpoint）。请求通过使用 JWT token 验证，让 CMS 直接使用 JavaScript 通讯，而不必重复 CMS 里的 C# 代码的模型。

**高级架构**

[![go语言集成服务范式](http://www.labazhou.net/wp-content/uploads/2015/06/golang-integration-service-diagram.png)](http://www.labazhou.net/wp-content/uploads/2015/06/golang-integration-service-diagram.png)

**请求流程**

[![cms 到微服务的请求处理](http://www.labazhou.net/wp-content/uploads/2015/06/cms-to-microservice-request-process.png)](http://www.labazhou.net/wp-content/uploads/2015/06/cms-to-microservice-request-process.png)

如果你稍后看看互联网上就 Google Go 语言的讨论，你将发现存在两极分化的阵营。有一些人喜爱这门语言，另一些人貌似恨它。


### 喜欢的人





	
  * 简单 - 没有太多烂大街的语言结构，没有充满想象力的 OOP 思想。

	
  * 快速编译时间 - Go 编译就是快。

	
  * 原生 - 为了快速执行和便于部署，编译成单个的、本地的二进制。

	
  * Goroutines - 可以跨渠道通信的绿色线程，常常规避互斥和锁定。

	
  * 垃圾回收 - 不必应付手动的内存管理。




### 不喜欢的人





	
  * 没有异常 - 大量憎恨都是围绕着频率奇高的错误代码检查。

	
  * 没有泛型 - 围绕某种特定类型创建的某种函数，由于缺乏泛型，而不得不针对其它类型去重复。

	
  * 没有类 - Go 没有类的真正概念。只是把函数 attach 到结构和接口上。

	
  * 垃圾回收 - 不是每个人都喜欢自动化的内存管理。存在成本，Go 的垃圾回收仍然不成熟。


上面的清单远远不够完整，但是说明了一点，那就是[关于是否使用 Go 的争论](http://www.labazhou.net/2014/05/adopting-a-new-programming-language-or-not/)正在发生着。尽管如此，根据我目前的经验，我算作喜欢使用 Go 编程的那一类人，尤其对于某些特定工作。下面列出了让人感到愉快的一些原因：



	
  * 在 Go 里创建一个 HTTP 服务器，是超级容易的。

	
  * 第三方 API 返回 XML 格式的响应。在 Go 里，反序列化 XML，就像在结构里定义属性一样容易。

	
  * HTTP 的标准类库灵活到足以为处理请求配置中间件，比如为身份验证配置 JWT 就十分容易。

	
  * Goroutines 支持并行执行那些属于瓶颈的任务。


我非常肯定，Go 不是解决所有问题的语言，但是对于我的这个项目、以及我看到的其它很多项目，Go 一直都是我的工具集中的得力工具。
