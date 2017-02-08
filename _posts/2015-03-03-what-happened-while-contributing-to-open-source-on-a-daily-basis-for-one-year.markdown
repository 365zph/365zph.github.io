---
author: viviworld
comments: true
date: 2015-03-03 06:25:54+00:00
layout: post
link: http://www.labazhou.net/2015/03/what-happened-while-contributing-to-open-source-on-a-daily-basis-for-one-year/
slug: what-happened-while-contributing-to-open-source-on-a-daily-basis-for-one-year
title: 一年内每天向开源贡献代码所发生的事情
wordpress_id: 1663
categories:
- 编程
tags:
- CouchDB
- erlang
- github
- nodejs
- npm
- Scheme
- 开源
---


	
  * 原文地址（original source）：[http://robert-kowalski.de/blog/what-happened-while-contributing-to-open-source-on-a-daily-basis-for-one-year/](http://robert-kowalski.de/blog/what-happened-while-contributing-to-open-source-on-a-daily-basis-for-one-year/)

	
  * 作者（author）：[https://twitter.com/robinson_k](https://twitter.com/robinson_k)


最近我在GitHub连续冲刺了365天，我想写篇博客，记录下为什么开始每天提交，以及它对我的生活带来了什么变化。

[![github提交图表](http://www.labazhou.net/wp-content/uploads/2015/03/streak-github.png)](http://www.labazhou.net/wp-content/uploads/2015/03/streak-github.png)

我对贡献代码的要求比较简单：



	
  * 每次贡献必须有意义，必须有实际影响。我可以提交只有空格的修复，但是它们不应该被算作有影响的提交。

	
  * 它必须是开源的。


早在2013年夏天我就开始了，略早于John Resig，他写了关于每天提交代码的[博客](http://ejohn.org/blog/write-code-every-day/)，但是我的第一次尝试失败了。正是他的文章鼓舞了我，告诉我不是一个人在战斗。

我和John有着同样的理由：我热爱业余项目（side project），但是我不乐意为了完成它们而投入整个周末。有时候，我在周末投入一整夜，但是这帮助不大：去做业余项目的时间跨度太大了，我经常想不起来在做什么以及项目的下一个想法是什么。我总要用很长时间才能重新回到项目上。另外，我不想在周末的两天里完全忙于业余项目，因为我想花些时间和朋友在一起，以缓解一直坐在电脑前面的紧张状况。

我开始每天贡献代码的其它原因是，我认为这很可能将提高我的技能。


### 好的方面




#### 改善我的业余时间管理


我的业余时间整个计划发生了变化。往好了讲，我开始计划和管理我的业余时间了。在此之前，我没有真正考虑过工作之外的时间。在完成白天工作之后，我突然（震惊，震惊！）有了一些业余时间却不知道做什么。


#### 技能提高


每天忙于代码，我没有看到每天的工作真正地提高了我的技能。由于我在学Erlang，用Scheme编写了我的第一个程序，我在简历里增加了新语言。我仍然在写Erlang。

我还学到了，较大型开源项目是如何运作和组织的，以及开源对于公司意味着什么（我甚至可以说，对于每家公司意味着什么，但这需要另一篇博文了）。我不是说，开发不包含任何开源组件的产品就不赚钱，据我看来，每个项目都拥有大量的开源组件，盈利并在长期从更好的代码上获益，这是有可能的事情。

另外，我在数不胜数的知识点上提高了我的知识和技能，列举一些：解析和词法分析、分布式计算、架构、安全、项目（代码规范）之间快速切换、理解代码以及代码review。我也提高了软技能：沟通、团队精神、解决冲突、指导和处理高难度/突发情况下的问题。


#### 一份新的工作


刚开始时，我有很多自己的小型业余项目，十分有趣，但是到了某个阶段，我感到不开心了，没人fork，貌似没人使用。我是唯一的开发者，我没有伙伴可以讨论解决方案或得到review的途径，而这是提高代码和技能的最佳途径。

我决定[向较大型的项目提交代码](http://www.labazhou.net/2014/03/beginners-contributing-to-open-source/)，既然我从0.4版本就在使用node，是一名日常npm用户，我就向npm提交了一个补丁。Isaac Schlueter审查了我的一个PR，真不错，这让我为npm提交了更多的代码。

npm registry使用CouchDB做数据库，但是我不知道如何使用。我开始把CouchDB文档翻译成德语，这样我就学会了如何使用CouchDB和如何帮助项目。有一天，我想托管我自己的私有registry，当时我的硬盘里有CouchDB源代码，我不确定为什么registry没有引导。当通读代码时，我看到CouchDB有一个JavaScript MVC app，它不是官方发布的。这一天我开始向CouchDB贡献代码，而npm的PR有一堆，我不想再提交了：我不想让花时间查看的审核人感到太难。我向CouchDB贡献了更多的代码，因为他们真是不错的人们。

有时候，npm有一些与Node.js直接相关的bug和问题，因此我也向Node.js项目提交代码。

加入所有这些项目，得到review，与其他很多不同的贡献者协作，阅读其他人写的大量代码，审核补丁，和用户交流，解决他们的问题，实实在在地加强了我的技能。

在2014年，我足够幸运，得到了一份工作，我因为致力于开源项目CouchDB而获得了回报。


#### 交新朋友


经过在开源技术社区的工作，我结识了大量新朋友。我遇到很多忙于同样工作的协作者，还有人在使用我参与的项目。他们大多比我聪明，至少对于我参与的项目来说，我可以说，他们都是非常优秀、思维开放的人。

他们就是我在发送了最初PR之后、还提交了更多补丁的理由。我认为，任何人没有兴趣把业余时间（甚至工作时间）投入到一个充满敌意的、糟糕的环境里。


### 坏的方面


每天贡献代码并真正坚持下来，不会一直都顺利。我想，大部分让人郁闷的事情都是那些对开源产品有着古怪期望的人们，他们免费用着人们在业余时间维护的产品。

npm里的[这个issue](https://github.com/npm/npm/issues/2568)是个例子，我过去和Domenic一起在业余时间做了大量工作，Domenic也花了大量时间去维护npm：

[![开源review截图](http://www.labazhou.net/wp-content/uploads/2015/03/work-harder.png)](http://www.labazhou.net/wp-content/uploads/2015/03/work-harder.png)


### 结论


每天向开源软件贡献代码的决定，改变了我生活的很多方面。我现在有偿参与着开源，在很多项目中交了很多朋友，这提高了我的技能。

我乐于看到公司支持他们的员工向开源软件贡献代码---他们99.99%都依靠开源软件，比如，他们的开发工具，直接应用的产品，甚至两者兼而有之。令人悲哀的是，对于大部分员工来说，在工作时间参与开源软件是相当难的，不是每个人都有足够的特权能够每天花费业余时间里的1小时参与到开源软件里。

像[Kyle Simpson](http://blog.getify.com/learned-on-a-1-year-github-streak/)和[Mathias Lafeldt](http://mlafeldt.github.io/blog/write-every-day/)这些人开始了类似的项目，貌似也改变了他们的生活，还有他们看待世界的方式，我对未来充满着渴望。
