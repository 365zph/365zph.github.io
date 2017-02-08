---
author: viviworld
comments: true
date: 2015-01-08 07:44:07+00:00
layout: post
link: http://www.labazhou.net/2015/01/the-perilous-world-of-machine-learning-for-fun-and-profit/
slug: the-perilous-world-of-machine-learning-for-fun-and-profit
title: 乐趣和利益并存的机器学习的危险世界
wordpress_id: 1498
categories:
- 编程
- 设计
tags:
- google
- MailChimp
- spam
- 团队
- 机器学习
---

原文地址（source）：[http://www.john-foreman.com/blog/the-perilous-world-of-machine-learning-for-fun-and-profit](http://www.john-foreman.com/blog/the-perilous-world-of-machine-learning-for-fun-and-profit)


## 管道丛林和隐藏的反馈循环


我很久没有写博客了。然而，我不想放弃，没有写作的主要原因是我在MailChimp的工作太忙了。数据科学小组和公司其他人一起紧密配合，期望在未来做一些有趣的东西。

受到Google出品的优秀论文“[Machine Learning: The High Interest Credit Card of Technical Debt](http://research.google.com/pubs/pub43146.html)”的启发，我写了一篇文章。

那些计划靠开发产品数学模型系统谋生的人们需要关注这篇论文了。

然而我在这里不想扼要重复整篇论文，我想强调与生活密切相关的一些观点。


### 管道丛林（Pipeline Jungles）


[![Roald Dahl写的《George's Marvelous Medicine》](http://www.labazhou.net/wp-content/uploads/2015/01/george-marvelous-medicine.jpg)](http://www.labazhou.net/wp-content/uploads/2015/01/george-marvelous-medicine.jpg)

在我孩提时代我喜欢的一本书是Roald Dahl写的《[George's Marvelous Medicine](http://en.wikipedia.org/wiki/George%27s_Marvellous_Medicine)》。这本书充满了淘气鬼和恶作剧，使得Dahl的作品趣味十足。

书中的George非常好奇，从家里找到化学物质，混合成棕色的汤，以替换他祖母平时的药。这种孩子式的谋杀祖母的重罪，常常让我忍俊不禁。

规划一种新的机器学习模型的原型，与George制作化学毒物的需求类似。对于[数据科学家](http://www.labazhou.net/2014/03/what-i-think-when-interviewing-data-scientist/)来说，翻遍公司去寻找数据源和工程特性、以帮助预测一种结果，这是一个机会。

一些日志文件，一些Google Analytics数据，一些Marge提供的会计方面的电子表格。

哇！我们具备了大量的模型。

和别人分享你是如何找到reddit投票、万年历和你的瑜伽老师说短链碳水化合物（FODMAP）的次数组合之间的神话，是多么地有趣呀，实际上多少有些预测作用。

不过它们是一些糟糕的开发人员规划你的原型模型工作，从海量数据源（嘿，为了更好地测量，你很可能也收集了Twitter）拉取，并转化到产品系统里。

突然，出现了一种“管道丛林”，数据源的流和工程特性的胶水代码，建立了你不得不按照《George's Marvelous Medicine》狂欢里手动创造的、在产品上可编程的、可靠的某种东东。

在机器学习项目的研究和设计阶段，很容易把产品搞成过度工程。太多的数据源、太多的新奇脆弱的功能，相应地，成为太复杂的一个模型。论文提到的策略是，忽视原型模型中的不重要功能，因为它们帮助不大，它们也没有伤害任何人，对吧？

这些功能的价值和忽视它们的成本，两相比较，结果如何呢？那就是需要维护额外代码，或许是需要从中拉取的额外数据源。正如Google论文指出的，[世界在变化](https://www.youtube.com/watch?v=BjJvOm94W5U)，数据在变化，每个模型功能都是打破一切的潜在风险。

切记，科技媒体（和供应商）将让你开发一个深度的学习模型，从互联网的屁眼里攫取收集到的数据，但是稍微自我控制比较重要。正如技术债务论文作者Preach所指出的，“对于以大规模增加系统复杂度的成本为代价、而提供微小精确好处的研究解决方案，几乎不是明智的实践”。

随着定好的阈值开始偏离，谁将拥有这个模型、关心它、热爱它、照顾它并提供紧急救助？因为它将消耗人力相关的费用，把资源投入到维护模型上，那么这个模型对于业务是值得投入的吗？如果模型没有这样重要（在重要性上，我经常讨论顶线收入【Top Line Revenue】），或许具有一些相互作用的逻辑回归【注1】就适合你了。


### 人类是反馈循环（feedback loop）机器


[![英国哈沃斯（Haworth）的墓地](http://www.labazhou.net/wp-content/uploads/2015/01/the-graveyard-at-Haworth.jpg)](http://www.labazhou.net/wp-content/uploads/2015/01/the-graveyard-at-Haworth.jpg)

在英国哈沃斯（Haworth）【注2】，人们常常在城镇上面的山顶掩埋尸体。当有人死去的时候，他们把尸体运到山上拥挤的墓地里，然后尸体流出的带有霍乱病菌的液体渗入到供水系统，进而影响山下的人，为墓地产生了更多的尸体。

哈沃斯有着特别凶险的反馈循环。

机器学习模型也吸收着各种各样凶险死尸的液体。

在MailChimp，如果我知道一个用户将来会成为垃圾邮件发送者（spammer），我现在就能通过机器模型关闭掉，快速地遏制该用户。

但是我正在改变的将来，可能是某一天、下一周、下一年，有可能是机器学习系统的现在。

任何训练眼下数据的企图都充满了危险，这些数据如今已经被业务的模型驱动行为（山顶被埋葬的、死亡的垃圾邮件发送者）污染了。这是一个反馈循环。突然地，或许我没有用来训练ML模型的垃圾邮件发送者了，因为我把它们都关掉了。现在，我新训练的模型认为，垃圾邮件貌似不是我当初所认为的那个样子。

当然，这种反馈循环可以用很多方式得到缓解。比如保留数据（holdout set）。

但是，我们仅仅能够在知道其存在的情况下才可以缓解，我们人类精于生成反馈循环而害怕重新认识它们。

考虑一下小说中的时光旅行。一旦你有了时光机（毫无疑问，合适的ML模型在处理销售和市场方面，非常接近于跨越式时光机），很容易穿越去搅和事情，但是很难参与这些变化的所有影响以及他们可能改变你将来训练数据的方式。

还有，当ML模型产出的数据放到执行人的手里时，你敢打赌将来（和相应的训练数据池的将来）会被改变的。这是关键！我不能预测用它们会做些什么！预测意味着被采纳。

因此，当[警察预测](http://www.theverge.com/2014/2/19/5419854/the-minority-report-this-computer-predicts-crime-but-is-it-racist)某个社区充满了犯罪，然后开始反复突击社区时，你认为接下来要发生什么？未来训练的数据将受到警察“特别关注”的影响。预测的模型反过来影响了系统鉴别。

但是我们不应当期望警察会理解他们正在山顶埋死人。

这是我对于数据科学技术步行街化（pedestrianization）的担忧之一。随着我们把预言性的模型越来越多地交到外行手里，我们可能把理解或关心他们滥用情况的人从循环中清除，对此我们考虑过吗？


### 集成，保持警惕


技术债务论文做了这样的敏锐评论，“胶水代码和管道丛林是整合问题的征兆，可能在根本上引起‘研究’和‘工程’角色的过度分离，这是不值得的”。

这绝对是真实的。当数据科学家把产品执行当做黑盒子时，他们将快速推出其原型；而工程师把ML包做为黑盒时，他们将快速推出管道。问题在滋生了。

数学的模型制作者在开发产品数据系统时，需要与工程师密切沟通。二者需要彼此在意对方、在意业务。目标不是使用深度学习，目标不是使用Go语言编程。目标是创建一个业务赖以运行的系统。在此基础上，精确性、可维护性、健壮性……它们有着同样的权重。

因此，数据科学家应该让你的统计兄弟和其它团队（工程师、MBA、法务……）的同事保持密切沟通，你们的目标是一起把事情搞定。这是你的模型从原型开始并存活下来的唯一方法。



	
  * 注1：逻辑回归或罗吉斯回归（英语：Logistic regression 或logit regression），即逻辑模型（英语：Logit model，也译作“评定模型”、“分类评定模型”）是离散选择法模型之一，属于多重变量分析范畴，是社会学、生物统计学、临床、数量心理学、计量经济学、市场营销等统计实证分析的常用方法。[http://zh.wikipedia.org/wiki/%E9%82%8F%E8%BC%AF%E8%BF%B4%E6%AD%B8](http://zh.wikipedia.org/wiki/%E9%82%8F%E8%BC%AF%E8%BF%B4%E6%AD%B8)

	
  * 注2：Haworth is a historic village in the City of Bradford metropolitan borough of West Yorkshire, England.[http://en.wikipedia.org/wiki/Haworth](http://en.wikipedia.org/wiki/Haworth)


