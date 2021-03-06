---
author: viviworld
comments: true
date: 2015-05-10 06:16:31+00:00
excerpt: 所谓的行业最佳实践，实际上对于你的团队或组织没有意义。不错，是这样的。重要的是，你根据可测量的经验和数据做决定，而不是嘴里的词语和猜测。最重要的是要明白，所谓的最佳实践是否为真正的最佳实践。
layout: post
link: http://www.labazhou.net/2015/05/what-is-a-best-practice-in-software-development/
slug: what-is-a-best-practice-in-software-development
title: 软件开发中的最佳实践是什么？
wordpress_id: 2025
categories:
- 编程
tags:
- 代码审查
- 敏捷开发
- 设计模式
---


	
  * 原文地址（original source）：[http://www.daedtech.com/what-is-a-best-practice-in-software-development](http://www.daedtech.com/what-is-a-best-practice-in-software-development)

	
  * 作者（author）：[https://twitter.com/daedtech](https://twitter.com/daedtech)





* * *



刚才，我在 Pluralsight 网站发布了一个教程，标题为“[促成商业交易的最佳实践](http://www.pluralsight.com/courses/making-business-case-for-best-practices)”。（如果你想阅读、但没有 Pluralsight 账号，请注册右边侧栏中的邮件列表，我将给你发送一份免费的 30 天订阅）。这个标题有个不太认真的元素，它在媒介上或许不是必要的最好想法，我这里的好处是和标题吸引力最大化有着关联。但是，如果你在笑，生活会更加有趣。

不管怎样，它有些不太认真的理由是，我发现“最佳实践”这个术语在很多语境中是骗人的。最好情况下，它是模糊的、主观的、和语境高度相关的。本质上，这个课程的目的是，“嘿，如果你认为，你的团队应该采用 X 实践，那么你最好搞清楚在管理上得到纯利益的东西------‘最佳’实践是有利可图的实践。”因此，我想可以送出这份教程介绍部分的副本，我在这个部分详细讨论了这个术语。事实上，第一部分称之为“‘最佳实践’究竟是什么？”


### 最佳实践：理想的、真正的和愤世嫉俗的


我提供的“最佳实践”【注1】的第一个定义是，某个人或许将其描述为“官方”版本，但是我把它称作“理想版本”。维基百科对其定义为，“为持续有效地达到企业目标而采取的最成功的解决方案或解决问题的方法，它被用作一种基准。”换句话讲，一种“最佳实践”，多多少少在经验上验证过是最好的一种实践。举个例子，如果你准备鸡肉有三种可能方法：生的、半生不熟、完全熟，那么根据死亡和疾病的事故次数，完全熟将显现为一种最佳实践。我把这种定义称为“理想”的原因是，它意味着明确地有一种做某个事情的最好方法，现实生活很少如此齐整。拿鸡肉的例子。完全熟好于半生不熟，但是并不缺乏完全弄熟鸡肉的方法------你能用火烤、用烤箱、用烤炉、有油炸等。任意一条这些方法是经验上认为的“最佳”、或者它变成了偏爱和看法的一种方式？

[![烤鸡肉的最佳实践](http://www.labazhou.net/wp-content/uploads/2015/05/Barbecue-chicken.png)](http://www.labazhou.net/wp-content/uploads/2015/05/Barbecue-chicken.png)

这导致我将轻率地将其称为最佳实践的“真正的”定义，我的意思是，这也变成了最被普遍应用的定义。它通常被称作是做某事的、可接受方式的一种约定，经常为某些标准机构所推崇，比如 ISO 或其它类似的机构。从这个角度看，或许，关于最佳实践的更好名字可能是“标准化实践”或“可接受的实践”。关于这种情况的例子或许是，外科医生洗手的优先级要高于外科手术。它是如此地被广泛接受且被标准化地实践，以致于那些不遵循此实践的实习生，会让人心生反感。洗手相较于不洗手，在病人治疗效果方面已经从经验上被论证为是更好的了。在该领域，外科医生令人信服地在手术之前洗手，那么这种洗手是绝对的“最佳”实践吗？好吧，这个哲学问题相对于我把最佳实践称作“理想的”定义，不是特别重要。重要的是，洗手是有好处的、且广为接受。

现在，谈谈愤世嫉俗的定义。对于很多人来说，“最佳实践”基本上是一种无意义的漂亮口号，让一个人的行动看起来比实际情况更重要、更合理、或更正当。我敢肯定，不只是我听到人们把“最佳实践”的术语挂在嘴边，以此评判人们的行动，明显的是，这种实践既没有在经验上被论证为最好的可能实践，也没有受到规范或标准组织的通过。你将经常听到开发人员把他们解决某些问题的方法谈论为一种“最佳实践”，当他们在高资历的位置、或控制着组织的技术决定时，就更明显了。但是，它是一种真正的最佳实践吗？或者，他们只是使用这个词语来避开争论？

通过考虑这三种定义，我们可能定义成一种连续统一体。愤世嫉俗版本在最佳实践术语的使用上，有着最少的可信度，而理想版符合这个术语防弹的用法。这样，有人把某种实践定义为“最佳实践”，如果他不能提供证据，就符合愤世嫉俗版。如果他成功地论证了价值，并建立了一种正当的标准，就符合真正版；如果他或多或少地论证了这种实践基本上是可能的最佳实践，就符合理想版。


### 软件开发的“最佳实践”


我们已经讨论过了“最佳实践”术语的一些定义了，接下来说一些例子， 它们通常在某种程度上提到了最佳实践，或者我刚才提到的连续统一体。我打算讨论一个小组或组织中的某些具体东东，比如你们的设计师认为，一个小组的“最佳实践”就是使用她写的校验资源库。我也不打算讨论家喻户晓的、已经定义好的行业实践。不是这些实践没有被一致通过或没有他们的诋毁，而是多数开发人员貌似看到了采用的潜在价值，即使他们相信，可能地，采用的价值比其成本和麻烦更加重要。换句话说，可能是相信某些东东是最佳实践，[而不是值得这样做](http://www.labazhou.net/2014/05/why-bad-scientific-code-beats-code-following-best-practices/)。

下面是软件开发领域里的一些例子。



	
  * 敏捷方法论如日中天。现在整个行业都在致力于帮助公司采用敏捷实践。

	
  * 自动化测试几乎被普遍赞同而作为一种值得赞美的目标。

	
  * 测试驱动开发或许更多地归结为有争议的影响，但是根本就不缺乏那些认为这是最佳实践的开发人员。

	
  * 持续集成，相对于仓库分支的开发，有着大量的合并工作量，很大程度地被视作有益处。

	
  * 有原始的、所谓的 Gang of Four【注2】面向对象设计模式清单，但是模式清单已经扩大了，超过了这四位作者建议的清单。总之，在策略上使用这些模式被视作为一种最佳实践。

	
  * 代码审查广泛被视作是促进代码质量的、不可或缺的方法。

	
  * 结对编程把代码审查带到了下个阶段，让开发一直处于连续的审查状态。

	
  * 一键化自动开发，对于大多数组织而言，被视作重要目标；与之形成鲜明对比的是，某个劳动力用半天时间，才能让软件达到可部署状态。


上面的清单不一定是全面的，可能也不是没有争议的。你可能认为其中一条或几条甚至不是优秀的思路。然而，总的来说，这个行业已经朝着一个方向前进，一种背道而驰的视角。不论好坏，这个行业共同认为，这些都是值得达到的目标。

但是，在共同维护一种优秀思想的利益和昙花一现之间，有一条分界线。在传统智慧和普遍误解之间，有一条分界线。该怎样才能知道这些实践是真正的优秀思想，更重要的是，该怎样知道这些实践对他自己和组织是有好处的？

喔，这就是本教程的主旨（这里有个暗示------向钱看）。


### 要点


我是一名软件开发人员，我可以假设你们很多读者也是。几乎可以肯定，你是一名开发人员、一名前开发人员、或与有一定能力的开发人员共事的人。那么，我们都知道，对于软件开发人员而言，存在一种自然倾向，他们想在工作中尝试新东西，并收获宝贵的经验。<del>我们都知道，想采用最新的开发实践、语言、流程的开发人员，和想采用最新框架的开发人员之间，存在这一种天然的紧张局势，因为他们对这样做有兴趣，而开发人员想做对他们的组织或项目最有意义的事情。</del>我们都知道，想采用最新的开发实践、语言、流程和框架的开发人员（因为他们对这样做有兴趣）和想做对他们的组织或项目最有意义的事情的开发人员之间存在着一种天然的紧张局势。这只是走在该行业中的一条普遍分界线。【注3】

我对本教程的目标非常简单，是为了帮助你走过在这两种关注点之间的分界线。我想给你一种方式来看待被行业吹捧为最佳实践的东东，来鉴别采用这些实践对你的组织是否有着实际意义。还有，我想给你一种方式，让你沿着“最佳实践连续统一体”，从“我想去做因为人们说它好”变成“我们可以公正评判的习俗”，变成理想的、在某种程度上的、“我们这样做是因为它从经验上被论证过，要好于其它方法”。

有了我向你展示的启发和结构，你可以得出结论，所谓的行业最佳实践，实际上对于你的团队或组织没有意义。不错，是这样的。重要的是，你根据可测量的经验和数据做决定，而不是嘴里的词语和猜测。最重要的是要明白，所谓的最佳实践是否为真正的最佳实践。



* * *



注1：最佳实践(best practice)，是一个管理学概念，认为存在某种技术、方法、过程、活动或机制可以使生产或管理实践的结果达到最优，并减少出错的可能性。http://zh.wikipedia.org/wiki/%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5

注2：The authors of the DesignPatternsBook came to be known as the "Gang of Four." The name of the book ("Design Patterns: Elements of Reusable Object-Oriented Software") is too long for e-mail, so "book by the gang of four" became a shorthand name for it. After all, it isn't the ONLY book on patterns. That got shortened to "GOF book", which is pretty cryptic the first time you hear it. http://c2.com/cgi/wiki?GangOfFour

注3：感谢 jian 指出了我的断句错误！详情参看本文评论~
