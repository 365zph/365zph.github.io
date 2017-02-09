---
author: viviworld
comments: true
date: 2014-07-15 12:15:37+00:00
layout: post
link: http://www.labazhou.net/2014/07/code-review-without-your-glasses/
slug: code-review-without-your-glasses
title: 没有戴眼镜，该怎么做代码审查
wordpress_id: 817
categories:
- 编程
tags:
- DRY
- ruby
- 代码审查
- 命名空间
---

你是一个不可思议的、有见识的开发团队中的一员，你安排了一整天只做代码审查。然而，过了最初的两个小时之后，你意识到你忘记戴眼镜了，整个早上只是盯着各种花花绿绿的模糊区域。你要做什么？

正确做法是回家取眼镜，因为只有步行10分钟的路程，天气也不错。但是假如在你早上离开家的时候，你发现一大群特别好斗的大黄蜂刚刚在你眼镜柜子上盖好了一座房子，他们看起来一定不喜欢被打扰。这可怎么办。

新的正确做法当然就是假装你戴着隐形眼镜来避免尴尬，你可以就一个文件滔滔不绝地评论，事实上你根本就没有看过。


### 展示1


[![代码审查](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-1.jpg)](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-1.jpg)

我们都认可关注点应该绝对隔离。当然任何类只应该负责一个功能。但是你创建的这个`UserCreator`对象很可能做的事情多了些。如果这就是`UserCreator`不得不做的所有事情，那么`Users`可以创建它们。否则，曾经简单的`User.new`会变成一个不必要的、令人毛骨悚然的噩梦，只要你想修改某些地方或去理解foo要做什么时，你需要找遍半个地球上的这些多个小文件。


### 展示2


[![代码审查-2](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-2.jpg)](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-2.jpg)

看看伪装成一个类的庞大方法，我能理解它在技术上是非常DRY的，没有什么可以被考虑在词语的字面意思里。但是我隐约觉得，你不是一名单元测试人员。同时我能够看出来，中间约20行的代码块是用来确定哪些用户是我们需要发送邮件的。如果你给我一下午时间和一些浓咖啡，我会谦虚地建议你把它们放在 `def users_to_send_emails_to` 里，然后我就不必这么写了。


### 展示3


[![代码审查-3](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-3.jpg)](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-3.jpg)

好，在这个类里，你的方法都很短，这很可能是进步。然而，你做得过头了。Ruby解释器不介意你在每隔一行的方法之间跳跃，只是大部分人类解释器会介意。和后来接手的人一样，我会开心地在文件里一点点移动，但是当我开始不得不写个堆栈跟踪来记住我到了哪里时，很可能该把某些方法一起改回去了。


### 展示4


[![代码审查-4](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-4.jpg)](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-4.jpg)

我明白你急于确保这个类精确地处在合适的命名空间里。不错，命名空间是好的。但是你套了6层，貌似你在把过多的东西塞进一个狭小的空间。考虑一下，要么不要如此详细地分割命名空间（是的，我看到那两个Helper类有它们自己的命名空间，但是它们真的在伤害相邻的命名空间吗？），要么退耦、把一些代码完全分离到不同的基础命名空间里。


### 展示5


[![代码审查-5](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-5.jpg)](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-5.jpg)

解释性的注释，赞一个！这里的代码需要一个附加的多节文章才能理解，踩一下。


### 展示6


[![代码审查-6](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-6.jpg)](http://www.labazhou.net/wp-content/uploads/2014/07/code-review-6.jpg)

仔细看下第二个方法。如果一个方法需要8个参数是为了搞清楚其意图以及怎么实现，那么这个方法就是过度的。传递负载，通过春季重构分担一些体积。分割成两个（或更多），或许把某些参数分配给某个实例的做法会更加明晰。你能够同时处理8个参数吗？那么不要期望你的方法这样做。

那么当你忘记戴眼镜的时候，或者直视太阳的时间比医学推荐的时间还要长的时候，这就是做代码审查的方法。如果我更擅长编程，那么我敢保证我可以提供更微妙的例子。另一方面，有人可以辩解（我完全会这样）说，无聊的事情有时候是有趣的，几乎比我们能想到的更加重要。然而，你的设计可以是清晰的、简单的和构建较好的，如果你不用心构建的，那将是徒劳无益的。



	
  * 原文地址：[http://ninjasandrobots.com/what-are-you-drawing-lily](http://ninjasandrobots.com/what-are-you-drawing-lily)

	
  * 注1：mung：计算机术语，逐步对计算机系统或文件做小改动导致大的损害，[http://en.wikipedia.org/wiki/Mung_(computer_term)](http://en.wikipedia.org/wiki/Mung_(computer_term))

	
  * 另一个版本：巧合的是，oschina.net今天刚刚发布了另一个版本，[http://www.oschina.net/news/53682/code-review-without-your-eyes](http://www.oschina.net/news/53682/code-review-without-your-eyes)。刚好我最后一句话拿不准，就重新编辑了：）


