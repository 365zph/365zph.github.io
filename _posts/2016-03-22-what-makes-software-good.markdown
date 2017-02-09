---
author: viviworld
comments: true
date: 2016-03-22 23:40:53+00:00
excerpt: 我们这些编写软件的人，往往低估了程序界面的可用性，而考虑更多易于衡量的、客观上的质量：功能性、性能和正确性。但是，糟糕的可用性才是真正的成本。
layout: post
link: http://www.labazhou.net/2016/03/what-makes-software-good/
slug: what-makes-software-good
title: 优秀软件的要素
wordpress_id: 3243
categories:
- 编程
- 设计
tags:
- api
- 符号认知维度
- 设计十诫
---


	
  * 原文地址（original source）：[https://medium.com/@mbostock/what-makes-software-good-943557f8a488](https://medium.com/@mbostock/what-makes-software-good-943557f8a488)

	
  * 原文作者（author）：Mike Bostock（@[mbostock](https://twitter.com/mbostock)）





* * *





<blockquote>注：原文结合作者 D3 项目，现身说法，以佐证自己对于优秀软件的观点。正如作者在文末所指出的：「我无意于让读者学习 D3，我只想让你学会如何有效地探索数据、传达见解」。本文为摘录。</blockquote>


我开发过开源软件，为此花了很多时间，思考怎样做才能让软件更优秀。有一些是不可避免的事情：在 StackOverflow、GitHub 和 Slack，包括电子邮件和 twitter 消息，永远都有需要帮助的请求。好在你看到有人超越了你的想象，取得成功并作出刁炸天的软件，这和你的帮助是分不开的。

或许 [Dieter Rams](http://www.labazhou.net/2015/04/timeless-design-10-principles-of-a-good-design/) 的[优秀设计原则](https://www.vitsoe.com/us/about/good-design)【注1】，就是为软件量身定制的？


<blockquote>好的设计是革新的。
好的设计是实用的。
好的设计是美观的。
好的设计使产品易于理解。
好的设计是谨慎克制的。
好的设计是诚实的。
好的设计是长命的。
好的设计在每个细节处都维持前后一致。
好的设计是环保的。
好的设计是尽可能少的设计。</blockquote>


我曾经讨论过[宏观的东西](https://vimeo.com/106198518)，比如找到感兴趣的最小问题，用工具甄别并最小化有害的偏差，或者改变相关的技术和标准。但是宏观的东西往往因为空洞而沦为老生常谈的论调。我们都想让事情再简化一些，我们只是不知道为了达到这一目标，需要牺牲什么。

即使你在宏观方面做好了，可能还无法保证设计的成功。想法的执行和想法本身同样重要，真真知易行难。

Green & Petre 提出了[符号认知维度](https://en.wikipedia.org/wiki/Cognitive_dimensions_of_notations)【注2】，定义了一套「讨论工具」，以提高「信息人工制品（比如代码）」可用性的「论述水准」：


<blockquote>抽象层次
映射相似度
一致性
模糊
错误的概率
痛苦的心理活动
隐藏的依赖
过早地约定
渐进式评估
Role Expressiveness[note]这个维度包含两方面的意思，那就是：说你所想，想你所说（原文是：say what you mean and mean what you say）。
一段容易阅读的代码（mean what you say）不一定很容易写出来（say what you mean）。所以在考虑这个维度时，不仅仅要考虑代码是否容易阅读，也应该考虑编写过程是否也同样容易。[http://www.yslow.net/show.php?tid=943](http://www.yslow.net/show.php?tid=943) [/note]
Secondary notation
粘度
可见度</blockquote>


它还不够完美，因为没有完美的东西。考虑一下可见度，它本来是说同时看到所有代码。但是今天的代码真的少到了可以在一个屏幕上呈现吗？或许模块化会更好些？试图把某些可用性问题对照到这个或那个维度是有难度的。但是，考虑软件设计的「认知影响」，总归算是好的起点。

对于我手头的 D3 项目，我将其分解为模块，增加复用性，易于扩展，也增加了开发的乐趣，但是我仍然识别并修复了 API 中数量多得惊人的 bug。被忽视的东东，往往引发了真正的痛苦，并限制了人们要做的事情。

我们这些编写软件的人，往往低估了程序界面的可用性，而考虑更多易于衡量的、客观上的质量：功能性、性能和正确性。但是，糟糕的可用性才是真正的成本。我们需要尽早地、更好地评估可用性，让软件更加可用，并把它放在首位。

[caption id="attachment_3245" align="alignnone" width="600"][![1_5p5we6kQBUnJS7MXqzdDYg](http://www.labazhou.net/wp-content/uploads/2016/03/1_5p5we6kQBUnJS7MXqzdDYg-600x400.jpg)](http://www.labazhou.net/wp-content/uploads/2016/03/1_5p5we6kQBUnJS7MXqzdDYg.jpg) Mori Masahiro Design Studio, LLC., CC-BY-3.0[/caption]

[caption id="attachment_3244" align="alignnone" width="600"][![1_43y1tWj2XK_pM49LGR8yuQ](http://www.labazhou.net/wp-content/uploads/2016/03/1_43y1tWj2XK_pM49LGR8yuQ-600x400.jpg)](http://www.labazhou.net/wp-content/uploads/2016/03/1_43y1tWj2XK_pM49LGR8yuQ.jpg) Mori Masahiro Design Studio, LLC., CC-BY-3.0[/caption]

想把一段代码放在手里，感受其重量和材质，这是做不到的。代码是「信息人工制品」，不是物理存在的、或图形化的东西。你和 API 的交互，是通过在编辑器或命令行里操作文本完成的。

因此我们不能像评估任何工具一样来评估代码，而要看是否容易掌握它，以及使用代码时，是否具备效率和快乐。我们应该考虑代码的承担特质【注3】、甚至还有审美。

编程接口就是用户接口。另一种说法：程序员也是人。说到了这个话题，我们需要再次倾听 Rams 说的话：


<blockquote>“冷漠地对待他人和生活，是设计的头等大罪。”【注4】</blockquote>


这暗示着，优秀的文档不能成为糟糕设计的借口。你可以要求人们[阅读文档](https://en.wikipedia.org/wiki/RTFM)，但是臆测他们会通读文档并记住每个细节，是非常愚蠢的。在现实世界中，示例的清晰，软件的可破译和可调试，可能更重要些。外形必须能够表达功能。


### 优秀软件的意图


快速而准确地计算出结果，简明而优雅的标记，这都算不上。

人类的认知能力强大却有限。但是人类可以学习。如果你能把某一领域学到的东西应用到其它领域，那么这种知识将变得更加强大。D3 项目使用文档对象模型（DOM）、而不是某种具体的表示，正是此原因。某种具体的表示可能更有效率，但是当工具未来发生变化时，你就需要花时间掌握特定知识了。

**优秀的软件富有亲和力**，在你理解某个地方之前，不必理解每个地方。

**优秀的软件符合一致性**。你在某处掌握的东西，可以推演到其它地方。不自我矛盾，简化，没有多余元素。

**优秀的软件能够解释自己**。

**优秀的软件能够教东西**。它除了自动化已有任务，还提供了见解、或传达着知识，比如某种最佳实践、或某个问题的新视角。

**优秀的软件以人文本**。

注：《[永恒设计：优秀设计的 10 个标准](http://www.labazhou.net/2015/04/timeless-design-10-principles-of-a-good-design/)》也针对迪特·拉姆斯的「设计十诫」做过探讨。


### 注释

* 注1：在上世纪七十年代后期，迪特·拉姆斯开始日益关注这个令他感到“由形状、颜色和噪音所组成的混乱不堪”的世界。意识到自己也是这个世界的参与者之一，他向自己提出了一个重要的问题：“我的设计是好的设计吗？”他归纳了他认为好的设计应当满足的十条要求。（这些要求有时也被人称为“设计十诫”。）相关翻译摘自于此。[https://zh.wikipedia.org/wiki/%E8%BF%AA%E7%89%B9%C2%B7%E6%8B%89%E5%A7%86%E6%96%AF](https://zh.wikipedia.org/wiki/%E8%BF%AA%E7%89%B9%C2%B7%E6%8B%89%E5%A7%86%E6%96%AF) 
* 注2：认知维度（也称作符号认知维度，Cognitive Dimensions or Cognitive Dimensions of Notations，简称CD）是一套关于符号标记、用户界面和编程语言的设计原则。认知维度提供一种轻量级的方法来帮助分析设计，它包含了14条不同的维度来指导设计。[http://www.yslow.net/show.php?tid=943](http://www.yslow.net/show.php?tid=943) 
* 注3：承担特质：环境赋使（affordance），或称为预设用途、可操作暗示、支应性、示能性等，指一件物品实际上用来做何用途，或被认为有什么用途。也就是说在物品的某个方面，具有让人明显知道该如何使用它的特性。例如门提供“打开”的功能，椅子提供“支撑”的功能。人们得知如何使用物品有一部分来自认知心理学，另一部分来自物品的外形。[https://zh.wikipedia.org/wiki/%E6%89%BF%E6%93%94%E7%89%B9%E8%B3%AA](https://zh.wikipedia.org/wiki/%E6%89%BF%E6%93%94%E7%89%B9%E8%B3%AA) 
* 注4：此句翻译引用自 [http://www.voicer.me/archives/6251](http://www.voicer.me/archives/6251)
