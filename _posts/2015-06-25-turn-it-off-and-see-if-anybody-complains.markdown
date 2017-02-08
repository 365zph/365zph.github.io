---
author: viviworld
comments: true
date: 2015-06-25 07:40:01+00:00
excerpt: 对我们小组而言，要处理成百上千个小型 web 应用，主要的好处就是，对于用户是否真的在用当前关闭的功能，我们得到了明确清晰的指示。我们明白用户是否真的在意这个功能，而不只是因为他们嘴上说在意。我们非直接地询问用户是否真的在意，如果他们不在意，我们就可以着手移除这个功能，因为我们不再需要它了。
layout: post
link: http://www.labazhou.net/2015/06/turn-it-off-and-see-if-anybody-complains/
slug: turn-it-off-and-see-if-anybody-complains
title: 关掉它，看看是否有人抱怨
wordpress_id: 2204
categories:
- 编程
tags:
- APP
- bug
- Heisenbug
---


	
  * 原文地址（original source）：[http://www.exceptionnotfound.net/turn-it-off-and-see-if-anybody-complains/](http://www.exceptionnotfound.net/turn-it-off-and-see-if-anybody-complains/)

	
  * 作者（author）：[https://twitter.com/ExceptionFound](https://twitter.com/ExceptionFound)





* * *



在我工作中的 Internal Web Tools 小组，我们定期处理一些终端用户【注1】，怎么说呢，他们坚持认为自己需要 app 里的某项特定功能，要求我们为他们开发出来。当问他们需要这个功能的理由时，他们的反馈通常包含「我想要 X 功能，否则我的豹猫就挖出你的眼睛」、或「Y 功能必须在某个时间段上线，以便于我到那个时候还活着【注2】」（我可能不记得这些对话了）

一旦我们提供了这个受人追捧的功能，我们经常再也听不到那些终端用户是否在用，甚至他们是否真的需要它。我们的很多项目因受时间限制，无法完整记录日志，因此我们得不到需要的信息。而且，如果你不从他们那儿哄骗（或者贿赂）一些反馈，那么用户对于提供反馈一向不甚热衷，我们的反馈也没有什么不同。**如果用户不告诉我们，那么通常我们最后要做的，就是假定这些功能是按照用户想要的方式在运行着**。

尽管如此，有时候我们会碰到一个 bug，为了追踪 bug，我们需要临时关闭某个功能。这或许是个许可问题（我们的外部敌人）、或 [Heisenbug](http://en.wikipedia.org/wiki/Heisenbug)【注3】等。无论如何，当这些问题跳出来时，我经常说出下面一句话：


<blockquote>关掉它，看看是否有人抱怨</blockquote>


面对此情此景，貌似要去冒险，通常我的内心独白会反抗这种想法。[关掉它？](http://www.labazhou.net/2014/07/why-google-killed-your-favorite-feature/)！我们不能这样做！如果有人恰恰在这个时刻在用，那该怎么办？用户的愤怒会气炸他们，他们将讨伐我们，因为我们拿走了他们钟爱的 Excel 导出功能。当他们扬言杀掉我们时，他们不得不回到刚才的状态，从头开始！我们以前遇见过，还记得吧？！我们不能让宝贵的用户经历这种体验！

[![关掉它，看看是否有人抱怨](http://www.labazhou.net/wp-content/uploads/2015/06/Complaint-Department-Grenade-489x600.jpg)](http://www.labazhou.net/wp-content/uploads/2015/06/Complaint-Department-Grenade.jpg)

把夸张的内心独白搁在一边，实际上它反映了在决定用户是否真正关心某些功能时的、一种让人惊奇的有效途径。如果他们介意，就会马上强烈地抱怨；如果不介意，我们压根就听不到抱怨。

这意味着，**当我们决定关闭 app 里的某项功能以解决 bug 时，我们可以更好地确认，我们的用户不打算抱怨**（至少不是立即抱怨）。

这是一项寻求原谅、而非许可的策略，它会带来某些风险。比如，你不能经常这样做、或波及到较大影响的功能。如果你想关闭企业内部网的登录系统，你就能搞清楚谁正在上传错误的 JPEG 图片，你最好重新考虑你的计划。人们真的不喜欢你[去动他们的奶酪](http://en.wikipedia.org/wiki/Who_Moved_My_Cheese%3F)，因此没有正当理由而经常这样搞，就会激怒他们。

还有，为了解决 bug，你关闭了某个功能，对此要更有信心；否则在没有正当理由的前提下，你将潜在地让用户不爽。如果你只是随意地关掉而没有需要这样做的任何理由，那么你的老板可能要找你谈话，这不是好的方式。

不过这种策略带来一些好处。对我们小组而言，要处理成百上千个小型 web 应用，主要的好处就是，对于用户是否真的在用当前关闭的功能，我们得到了明确清晰的指示。我们明白用户是否真的在意这个功能，而不只是因为他们嘴上说在意。我们非直接地询问用户是否真的在意，如果他们不在意，我们就可以着手移除这个功能，[因为我们不再需要它了](http://www.exceptionnotfound.net/kiss-dry-yagni-good-code-basic-training/)。

最后，如果它不起作用，我们就不会那样做，对我们而言，它运作得还算可以。我们已经在某些场合这样做了，只有一次、我能想起来的就这一次，在我们找到并修复反馈的 bug 之前（用户在这个地方抱怨竟然有很多次了），用户抱怨过。对于我的小组而言，这个流程执行得不错，尤其是[分析瘫痪](http://www.exceptionnotfound.net/the-peril-of-infinite-knowledge/)（Analysis paralysis，【注4】）的情况；或许它同样适用于你的团队。

你之前尝试过吗？它对你有用吗？或者它最后伤害了你？请在评论里分享！



* * *






	
  * 注1：终端用户（end user），是公司内信息系统发展群体以外的人员代表，应用程序是为他们开发的。这些用户在信息系统的实际和开发中将起到越来越大的作用。[https://zh.wikipedia.org/wiki/%E7%BB%88%E7%AB%AF%E7%94%A8%E6%88%B7](https://zh.wikipedia.org/wiki/%E7%BB%88%E7%AB%AF%E7%94%A8%E6%88%B7)

	
  * 注2：原文为「Implementation Y must be in place by this date so we can be sure to be live before Marge's boyfriend's Zodiac sign is in the fifth house of Lannister」，颇为费解，查阅了「辛普森一家」和「冰与火之歌」，仍然无法翻译。作者给我的答复为：「 Its a nonsense sentence, meant to illustrate that the requirements were silly, it doesn't mean anything. It's just a joke.」，才有了现在的翻译。参考：1）[https://zh.wikipedia.org/wiki/%E8%BE%9B%E6%99%AE%E6%A3%AE%E4%B8%80%E5%AE%B6](https://zh.wikipedia.org/wiki/%E8%BE%9B%E6%99%AE%E6%A3%AE%E4%B8%80%E5%AE%B6) 2）[https://zh.wikipedia.org/wiki/%E5%86%B0%E8%88%87%E7%81%AB%E4%B9%8B%E6%AD%8C](https://zh.wikipedia.org/wiki/%E5%86%B0%E8%88%87%E7%81%AB%E4%B9%8B%E6%AD%8C)

	
  * 注3：Heisenbug 这一名字源自物理学家 Werner Heisenberg，特指一类程序 bug，当有人试图对其进行研究之后它会消失或改变行为。[https://en.wikipedia.org/wiki/Heisenbug](https://en.wikipedia.org/wiki/Heisenbug)

	
  * 1. 注4：分析瘫痪（Analysis paralysis）：花费太多精力在项目的分析阶段。[https://zh.wikipedia.org/wiki/%E5%8F%8D%E9%9D%A2%E6%A8%A1%E5%BC%8F](https://zh.wikipedia.org/wiki/%E5%8F%8D%E9%9D%A2%E6%A8%A1%E5%BC%8F)


