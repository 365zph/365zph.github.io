---
author: viviworld
comments: true
date: 2015-06-30 01:26:04+00:00
excerpt: Node.js 已经成为流行的服务器端平台，用作很多现代 web 应用程序的 web 服务器。在开发 Node.js 应用程序时，你将使用 JavaScript
  编写所有东西，还能够在任何一种类型的服务器（Windows、Mac 或 Linux）上运行你的应用程序。Node.js 由大量的限定范围的模块（module）
  和 包（package） 组成
layout: post
link: http://www.labazhou.net/2015/06/node-js-for-side-projects/
slug: node-js-for-side-projects
title: 在业余项目使用 Node.js
wordpress_id: 2226
categories:
- 编程
tags:
- api
- ECMAScript
- express.js
- javascript
- json
- nodejs
- npm
- 业余项目
- 教程
---


	
  * 原文地址（original source）：[http://jkchu.com/2015/06/23/node-js-for-side-projects/](http://jkchu.com/2015/06/23/node-js-for-side-projects/)





* * *



有一种东西，把软件行业的人们联系在了一起：我们喜欢创造能够运行的东西。完成一个功能、或刚好符合预期的项目，是最让人满意的。对于我的业余项目（side projects），我热爱学习新框架、技术和语言。但是到了最后，最有收获和欣慰的地方，是完成了项目并对外发布了某些东西。老实讲，如果你有全职工作，[担心锻炼身体、杂事和可能还要睡觉](http://www.labazhou.net/2014/09/work-life-imbalance/)，那么，常常难以找到完成业余项目的时间，当我谈到这个问题时，你会理解的。借助提前规划，或许利用一些不错的项目管理工具，我们就可以帮助自己。但是我们的技术栈怎么样？如果完成并发布项目是我们的目标，那么挑选一种能够较好适应快速开发的技术栈就显得十分重要了。

[Node.js](https://nodejs.org/) 已经成为流行的服务器端平台，用作很多现代 web 应用程序的 web 服务器。在开发 Node.js 应用程序时，你将使用 JavaScript 编写所有东西，还能够在任何一种类型的服务器（Windows、Mac 或 Linux）上运行你的应用程序。Node.js 由大量的限定范围的模块（module） 和 包（package） 组成，你可以将它们利用起来。尽管如此，你最好取你所需，确保你的应用程序尽可能地轻量级。在一天结束时，你应该享受业余项目，Node.js 应用程序写起来比较有乐趣。


### 1.Node.js 究竟是什么？


Node.js 本身只是一种运行时环境，适合使用 JavaScript 来编写服务器端应用程序。**Node.js 不是 JavaScript 框架，但是大部分 Node.js 应用程序使用了框架**。[Express.js](http://expressjs.com/) 是最受欢迎的 Node.js 框架，有着出色的文档和海量的优秀资源。因此对于 Node.js web 应用程序栈而言，你应安装 Node.js 和 Express.js 来运行你的 web 服务器，这将成为一个快速、轻量级的中间人，它能够在你的客户端和数据库之间迅速地传递请求和响应。


### 2.你不应该使用 Node.js 的场景


在我们深入 Node.js 开发的精彩部分之前，让我们首先说清楚你不应该使用 Node.js 的情况。

如果你要开发的应用程序涉及到 CPU 密集型的操作，你就不应该使用 Node.js。Node.js 是单线程的，在服务器上运行要耗费太长时间，会拖垮应用程序的性能。对于服务器上任何种类的大数据集，你的应用程序都不应该处理它们。要么把这部分工作转移到数据库，要么粗暴地切换到更适合的平台上。

如果你不喜欢 JavaScript 开发，你就不应该使用 Node.js。你应该享受业余项目，不要因为网上有人告诉你这样做，就把不愉快的东西强加给自己。但是在你放弃之前，听我把话说完，我遇到过很多人，他们漠视着 JavaScript，甚至没有给 JavaScript 一个公平的机会。刚开始时，JavaScript 貌似狂野、难以驾驭，不过当你学会了如何正确地使用，你就能看到它的力量有多大了。JavaScript 是应用最广泛的编程语言之一，随着 [ECMAScript 6](https://github.com/lukehoban/es6features) 的发布，它将变得更好。


### 3.JavaScript ------前端和后端


让我们深入了解一下，Node.js 最大化你的业余项目生产力的方式。JavaScript 已经接管了互联网，不再单纯用于琐碎功能。对于很多现代 web 应用程序，运行在客户端的核心功能是由 JavaScript 提供的。除了改善用户体验，它还从 web 服务器分担了大量工作。还记得之前我们讨论的轻量级的服务器吗？让客户端的浏览器承担自己的工作，这样我们就能够充分利用 Node.js 的最大力量------减轻快捷的 I/O。

应用程序逻辑在前后端之间传播；对于我们这些 Node.js 开发人员，我们能够幸运地在前后端使用完全相同的编程语言。大部分开发人员对于上下文切换的成本，已经有了更多的认识。不得不把你的思维重新聚焦和调整在新任务、新语言、以及新问题上，常常会让开发人员耗费一些宝贵的有效率的时间。减少上下文之间切换的距离，使我们在各种任务的处理上游刃有余，相应的恢复时间也更加迅速。


### 4.JSON------数据丛林之王


对于服务器端和客户端之间的数据传输，JSON（JavaScript Object Notation）【注1】已经成为事实上的数据格式。根据我在其它平台上开发 web 应用程序的经历，把你的数据转换成各种格式和模型，所花费的时间是相当惊人的。对于 Node.js 应用程序，JSON 可以用在应用程序的所有三个领域------客户端、服务器端和数据库。[MongoDB](https://www.mongodb.org/) 和 [CouchDB](http://couchdb.apache.org/) 是流行的 NoSQL 数据库，使用 JSON 存储数据。[PostgreSQL](http://www.postgresql.org/)，一个流行的开源关系型数据库系统，也支持存储 JSON 对象。微软甚至[宣布](http://blogs.msdn.com/b/jocapc/archive/2015/05/16/json-support-in-sql-server-2016.aspx) SQL Server 2016 将支持 JSON。有如此丰富的可选项，就可轻松地给你的 Node.js 应用程序挑选一种可靠数据库，以挤出每一点生产力，而不必担心数据格式的转换。


### 5.模块------取你所需


业余项目的一个经验法则就是保持小而专注。该法则有助于确保真正地完成你的项目。同样的概念可在 Node.js 项目中找到------你只使用那些真正需要的模块。这使得你的应用程序足够轻量级。和其它那些以企业为中心的平台不同，你不会有大量根本用不到的额外东东。你的开发和部署将更迅速，你的项目将占用更少空间，项目里的每样东西恰恰都是你需要的，你明白这些，内心感到平静。[NPM](https://www.npmjs.com/)（Node Package Manager）【注2】是 Node.js 应用程序的一大卖点。它让你简单快捷地访问所有公共 Node 模块，选择范围超过了 150,000 个包。减少开发时间、利用已有开源软件和工具，从未如此简单过。


### 6.总结


Node.js 给我们提供了一个了不起的应用程序平台，因其高 I/O 需求而真正胜出的 web 应用程序。如果你打算在下一个业余项目使用 Node.js，就尽量开发一个轻量的 web 服务器 API，以最小化服务器端的真正负载。Node.js 极易理解，开发人员学习和掌握起来，相对容易些，为什么不尝试一下呢？


### 7.我的下一步规划


我想包含一些优秀资源的简单清单，帮助我掌握 Node.js。



	
  * [https://thinkster.io/mean-stack-tutorial/](https://thinkster.io/mean-stack-tutorial/) ：它是对我帮助最大的教程。该教程结构精妙，覆盖了极有价值的海量内容。该教程免费，但是你还能付费，以访问到源代码和视频（当时我为源代码支付了 25 美元，不过他们好像变成了每月 20 美元的订阅，就可看到他们的所有教程）。

	
  * [http://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js](http://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js) ：一篇写得不错的文章，帮助我理解了 Node.js 的优点和缺点。





* * *






	
  * 注1：JSON（JavaScript Object Notation）是一种由道格拉斯·克罗克福特构想设计、轻量级的数据交换语言，以文字为基础，且易于让人阅读。尽管JSON是Javascript的一个子集，但JSON是独立于语言的文本格式，并且采用了类似于C语言家族的一些习惯。[https://zh.wikipedia.org/wiki/JSON](https://zh.wikipedia.org/wiki/JSON)

	
  * 注2：Node包管理器（Node Package Manager）。它是一个javascript的软件包管理系统，默认环境为Node.js，从Node.js0.6.3版本开始，npm被自动附带在安装包中。[https://zh.wikipedia.org/wiki/Node%E5%8C%85%E7%AE%A1%E7%90%86%E5%99%A8](https://zh.wikipedia.org/wiki/Node%E5%8C%85%E7%AE%A1%E7%90%86%E5%99%A8)


