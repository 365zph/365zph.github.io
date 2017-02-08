---
author: viviworld
comments: true
date: 2014-02-26 06:17:57+00:00
layout: post
link: http://www.labazhou.net/2014/02/read-the-docs-faster/
slug: read-the-docs-faster
title: 阅读文档，更便捷
wordpress_id: 350
categories:
- 软件
tags:
- alfred
- dash
- docsets
- google
- StackOverflow
- Zeal
---

做为一名开发者，我的大把时间花在阅读文档上。甚至大部分时间花在找到上面提到的文档。过去一直这样，直到[Dash](http://kapeli.com/dash)走进我的生活。

[Dash](http://kapeli.com/dash)是一个管理自包含文档包的应用程序，称作docsets。你会找到几乎每种语言、每个类库、框架和内容管理系统，你甚至能够导入其他东东以扩大它的类库。通过启用、不启用docsets，你能够刚好根据你的要求来调整Dash。

更好的功能是，它本地化存储，因此你总是可以访问，无论你在飞机上办公，还是在网速慢、经常掉线的网络上。

强大的搜索引擎允许你瞬间精确找到所需资料，开始输入，你就会得到来自于所有启用的docsets上的结果。你甚至能够通过在查询里增加前缀比如html:, css:, 或sass: 把搜索限制到某个特定的感兴趣的范围。

[![Dash docsets 搜索](http://www.labazhou.net/wp-content/uploads/2014/02/dash-css-search.png)](http://www.labazhou.net/wp-content/uploads/2014/02/dash-css-search.png)

在侧边栏列表底部，有指向Google和StackOverflow查询结果的帮助链接，对于极少数搜索不到文档的情况下，这是有帮助的。


### Dash的朋友


Dash本身已经证明了它对于我的工作流是一款极有帮助的附属，但是当和[Alfred](http://alfredapp.com/)集成的时候，速度快得难以置信。Alfred是加速启动程序、查找文件和运行脚本等任务的极具生产力的app。Dash[打包Alfred集成](http://www.alfredforum.com/topic/1919-dash-documentation-for-80-apis/)一定会让你和我一样着迷于它。

和启动Dash，点击搜索条，敲入你的查询一样，仅仅打开Alfred（借助你喜好的快捷键，我用Option+Space键），然后开始敲入你的搜索，以dash为前缀。你就能在Alfred里看到一个结果列表；选择一条，你刚好就被定位到Dash里的文档上的一个地方。你可以用上面提到的限制查询的方法，比如 dash css:background 。

[![dash-css-alfred-search](http://www.labazhou.net/wp-content/uploads/2014/02/dash-css-alfred-search.png)](http://www.labazhou.net/wp-content/uploads/2014/02/dash-css-alfred-search.png)

不幸的是，Dash和Alfred只在Mac OS X上有。如果你在Windows或Linux上，好像[Zeal](http://zealdocs.org/)是你的选择。我自己没有试用过，但是它受到Dash的启发，因此它必须是速度和离线访问的灵魂。

说起来有些可笑和懒惰，但是Dash和Alfred的集成每天节约了我大把时间。从代码跳到文档、再跳回代码，我的手从来不需要离开键盘，这是一个微小却富有意义的改进。

原文地址：[http://alistapart.com/blog/post/read-the-docs-faster](http://alistapart.com/blog/post/read-the-docs-faster)
