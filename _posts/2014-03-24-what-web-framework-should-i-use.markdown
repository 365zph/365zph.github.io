---
author: viviworld
comments: true
date: 2014-03-24 22:52:12+00:00
layout: post
link: http://www.labazhou.net/2014/03/what-web-framework-should-i-use/
slug: what-web-framework-should-i-use
title: 在Clojure里我应当使用什么web框架？
wordpress_id: 453
categories:
- 编程
tags:
- Clojure
- Compojure
- Django
- drupal
- Hiccup
- Hoplon
- lib-noir
- Pedestal
- Ring
- Ruby on Rails
---

摘要：_在Clojure里有大量的web框架，但是初学者应该把他们自己的服务器栈移动到Ring生态系统。_

我经常被Clojure的初学者问到的一个问题是“我应该使用什么web框架？”这是一个好问题。Python有Django。PHP有Drupal。当然Ruby有所有web框架之王，Ruby on Rails。

在Clojure里你应该使用什么框架？实际上这个问题是难以回答的。外面有很多web框架了。有人把[Compojure](https://github.com/weavejester/compojure)叫做框架，虽然它真正是一个类库。[lib-noir](https://github.com/noir-clojure/lib-noir)为你做了大量工作。然而有属于你的真正框架，像[Pedestal](https://github.com/pedestal/pedestal)或[Hoplon](http://hoplon.io/)，它们提供基础功能和解决web开发的抽象。所有这些项目是伟大的，但是对于初学者，我不得不推荐建立你自己的web栈，从Ring开始。

Compojure实际上只是一个路由类库，而不是框架。虽然有[playnice](https://github.com/ericnormand/playnice), [bidi](https://github.com/juxt/bidi), [Route One ](https://github.com/clojurewerkz/route-one)和 [gudu](https://github.com/thatismatt/gudu)等其它替代品，但是你能够用它满足路由需要。如果你不想下决定，那就使用Compojure。它使用广泛、表现优秀。如果你想深入，可以看看其他文档。它们针对不同的场景各有优点。

[lib-noir](https://github.com/noir-clojure/lib-noir)来自于[Noir](http://www.webnoir.org/)，后者是一个web框架（现在废弃了）。它比较容易，还为你提供了一些管道，因此你刚好借助建好的大量基础设施来开始一个项目。lib-noir是以类库形式存在的基础设施。我还没有用过，但是很多人喜欢它。然而，当我研究它的时候，我发现它提供了太多我不需要的东西，或太过琐碎。如果得到了大规模的应用（像Rails），你就能得到生态系统的效应，这通常是良性的，但是还没有这样。lib-noir被应用了，只是完全不占优势。

[Pedestal](https://github.com/pedestal/pedestal)有很多支持者。它的目标是通过提供使用ClojureScript、消息队列形式的、一个明智的前端环境来处理单页app。如果你需要“实时app”，它或许为是你准备的。尽管如此，我仍然警告你，它不适合Clojure初学者。Pedestal引入了大量新概念，甚至有经验的Clojure程序员也不得不去学习。[这个教程](https://github.com/pedestal/app-tutorial/wiki)又长又费力。如果你不了解Clojure，你去学习Pedestal会遇到问题的。

[Hoplon](http://hoplon.io/)也是为web app设计的。它为你提供了用ClojureScript实现的DOM（包括自定义组件），数据流编程（像电子表格）和客户端-服务器端通信。这是勇敢的一步，但是再一次，需要你接受花很长时间才能理解的编程模型。如果你还不熟悉Clojure，你就是在自找麻烦。

外面还有其它框架。但是我推荐你考虑自己条件。如果你在学习Clojure，掌握web app如何工作的最好方法就是得到一个配置了一些基本handler的[Ring](https://github.com/ring-clojure/ring) Jetty适配器。根据需要添加中间件。写一些自己的中间件。使用Compojure做路由。使用[Hiccup](https://github.com/weavejester/hiccup)生成HTML。这个安装将让你学到很多。

Ring仅仅是个函数。借助一些基本概念和Ring SPEC，你可以快速建立正是你想要的web服务器，你能够全面理解它。自己建立的经历能够让你在框架如何整合上受益良多。

况且，Ring有优势。大多数人写功能（以中间件或handler的形式）是以Ring为假设、而不是其它。因此保持靠近本质，你就会接近庞大的彼此兼容的、预编写的类库池。Ring就是Clojure web生态系统的所在地。

编写你自己的中间件栈不是那样让人气馁的。如果你想要指导，我的[Clojure web开发视频系列](http://www.purelyfunctional.tv/web-dev-in-clojure)现在开售了。它从一个全新的Clojure项目开始，直到一个功能齐全的app，有数据库支持，托管在Heroku（免费！）。一个小时里，它解释了所有概念，并向你展示了很多例子。有很多让你大脑飞速运转的练习题。

推荐：



	
  * [Ring](https://github.com/ring-clojure/ring) (with Jetty adapter)

	
    * [wrap-params](http://ring-clojure.github.io/ring/ring.middleware.params.html#var-wrap-params) (parsing params)

	
    * [wrap-reload](https://github.com/ring-clojure/ring/blob/master/ring-devel/src/ring/middleware/reload.clj) (for development)

	
    * [wrap-resource](http://ring-clojure.github.io/ring/ring.middleware.resource.html#var-wrap-resource) and [wrap-file-info](http://ring-clojure.github.io/ring/ring.middleware.file-info.html#var-wrap-file-info) (static files)




	
  * [Compojure](https://github.com/weavejester/compojure)

	
  * [Hiccup](https://github.com/weavejester/hiccup)


然后保持添加和定制。

原文地址：[http://www.lispcast.com/what-web-framework-should-i-use](http://www.lispcast.com/what-web-framework-should-i-use)
