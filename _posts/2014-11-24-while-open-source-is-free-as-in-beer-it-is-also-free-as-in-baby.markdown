---
author: viviworld
comments: true
date: 2014-11-24 08:02:06+00:00
layout: post
link: http://www.labazhou.net/2014/11/while-open-source-is-free-as-in-beer-it-is-also-free-as-in-baby/
slug: while-open-source-is-free-as-in-beer-it-is-also-free-as-in-baby
title: 开源是免费的，维护也是免费的
wordpress_id: 1348
categories:
- 编程
- 软件
tags:
- api
- cassandra
- github
- java
- license
- ruby
- 开源
- 熵
---

原文（source）：[http://danielcompton.net/2014/11/19/dependencies](http://danielcompton.net/2014/11/19/dependencies)

五金店

最近Zach Tellman和Factual[开源](http://blog.factual.com/how-factual-uses-persistent-storage-for-its-real-time-services)了一些资源库，他们想处理根本不存在的具体需求。在Reddit的评论里，有人[发牢骚](http://www.reddit.com/r/Clojure/comments/2mkx97/riffle_a_highperformance_writeonce_keyvalue/cm5v62y)，因为这个软件可能在1-2年内被抛弃，如果他们依赖这个软件，他们将陷入困境。我认为这种想法源于对开源软件的误导和自私的视角。

做为软件工程师，应对开软资源库、应用程序和框架，就像在一家五金店，这是非常有吸引力的。如果你有问题，而标准资源库无法解决，就拉取一个依赖项。需要工具集函数？在GitHub搜索一下，并增加一个依赖项。想发挥最近疯狂流行的单页应用程序？那就拉取另一个依赖项。需要用Ruby处理XML？只需瞬间[安装Nokogiri](http://www.nokogiri.org/tutorials/installing_nokogiri.html)，[你可以笑到最后](http://stackoverflow.com/questions/17914169/why-isnt-nokogiri-installing)。

或许这可以应付一段时间，但是漏掉了软件工程中最关键的地方：[软件随着时间而衰落](http://www.labazhou.net/2014/02/programming-laws-and-reality-do-we-know/)，也叫[熵](http://zh.wikipedia.org/wiki/熵)。软件不是以[独立系统](http://en.wikipedia.org/wiki/Isolated_system)的形式存在的，它与其它随着时间而变化的软件交互，包括你的操作系统、内存、其它外部服务、数据库、CPU、网络、IO设备（打印机、显示器）和最重要的因素---用户。这些系统被新的系统取代或更新。有时候变化是向后兼容的，有时候却不是。因此，代码被一次写完、而终身维护。使用某人的开源代码对你是个巨大帮助，因为你不必去写了。然而，随着时间的流逝，状况有所改变，熵就起了作用，代码需要维护和更新了。


### 一个资源库的供养需要一个村子的努力


除了把开源软件看做五金店，我认为更好的比喻应该是，加入一个村子去供养一个孩子。你拉取的每个依赖项需要随着时间一直维护，还有它所依赖的依赖项，[如此往复](http://en.wikipedia.org/wiki/Turtles_all_the_way_down)。这里的问题不是关于维护是否需要去做，而是谁来做。较大的社区有更多的资源和时间来做，成熟的项目已经经过了优化、良好的测试以及具有稳定的API。如果你正忙于[新生的](http://www.rust-lang.org/)、[模糊的](http://clojure.org/)或[快速变化的](http://www.ecmascript.org/)语言中，那么更多的维护将要压到你的身上。

我认为，把开源软件做为礼物献给世界的某个人，不会觉得负有为你维护软件的责任。一些项目的确声明了责任，但是不能仅仅因为有人在GitHub上发布了项目就说明责任被自动授予了。我想，更多的责任应该在于使用该项目的人。将要使用它的是你的代码，你的代码需要更新、你的代码将要崩溃。在你开始使用一个资源库或框架之前，你应该考虑以下问题：



	
  * 这个软件取决于谁？它的依赖的依赖项是什么？它们更新合理吗？资源库在用类加载器、字节码做着奇怪的操作、搞乱了运行时吗？这些情况更有可能出现在你的语言或运行时的新版本里。

	
  * 除了使用另一个或自己写，我使用这个资源库或框架能得到多少好处？

	
  * 这个资源库写得不错吗？有对代码做全面测试吗？通过测试了吗？

	
  * 作者建议你用在生产环境中了吗，或者它只是概念验证(proof of concept)或探索型想法？

	
  * 作者有过维护开源软件的经历吗？他们自己使用吗？如果我想增加一个特性或修复bug，作者乐于接受，或者它是“没有开启pull request的开源”？顺便说一句，这是不错的，意味着当你的需求偏离时，你需要维护自己的fork。

	
  * 如果它是一个数据库驱动器，它能够及时地为数据库新版本更新吗？例如，Netflix的Cassandra驱动器Astynax就[落后于](https://github.com/Netflix/astyanax/wiki/Cassandra-compatibility)Cassandra的最新版本。

	
  * 我和老板的风险容忍度怎么样？

	
  * 我有时间、且征得了老板的许可、有能力来自己维护或优化这个资源库吗？

	
  * 如果有必要，这个资源库通过安全审查了吗？

	
  * 作者有谈到API的稳定性吗？

	
  * 项目的issure tracker执行情况怎么样？作者有响应，或者他们不再参与了？

	
  * license和软件的其它部分兼容吗？

	
  * 如果它由一家商业公司提供支持和发布，他们倾向于[修改license](http://www.alittlemadness.com/2008/04/24/ext-discovers-step-2-of-the-slashdot-business-model/)或者为将来的企业客户保留重要特性吗？

	
  * 具有多个资源库实现的通用API吗，我可以在它们之间切换。在Java里，有[JPA](http://en.wikipedia.org/wiki/Java_Persistence_API)和[XQJ](http://en.wikipedia.org/wiki/XQuery_API_for_Java)之类的软件，可以避免被绑在一种资源库上。

	
  * 最近一次的重要提交是在什么时候？整个项目存活了多长时间？

	
  * 有相应的用户社区吗？有邮件列表吗？

	
  * 我正在编写的代码的预计使用周期和危险程度怎么样？


一旦你考虑清楚了这些问题，你将对所使用的资源库继承下来的风险有更好的理解，还有项目的极有可能的未来方向。如果你决定采用了，那么我建议你加入邮件列表，在GitHub上关注它，以随时关注更新变化。


### 可替代的依赖项的选择


拉取一个依赖项应该是经过深思熟虑的，可以先看看其它选择：



	
  * 如果你仅仅需要非常少量的、相对简单的代码，在license允许的前提下，只把代码拷贝到你的项目就可以了。

	
  * 确保标准资源库没有提供类似的功能。如果它只是另一种依赖项的包装库，那么你可以直接使用那种依赖项吗？

	
  * 如果为了某种数据结构而在拉取另一种依赖项，那么是否存在一种可替代的算法，你可以使用不需要这种数据结构的算法吗？

	
  * 存在一些应该你自己编写的代码吗？虽然这不总是最好的选择，有时候为了满足你的质量标准，也没有其它选择了，你需要自己来构建。

	
  * 有一个商业化的选择吗？开源是免费的【注1】，维护它也是免费的。给维护软件的其他人员支付费用，将增加他们继续为你维护的动力，这可能是很多公司最好的选择。




### 最后


开源软件对于程序员的生产力是一种巨大的恩惠，节约了人类数个世纪的努力。但是请记住，正如你[拥有自己的可用性](http://www.whoownsmyavailability.com/)，你还拥有你的软件和与此相关的一切。



	
  * 注1：[http://en.wiktionary.org/wiki/free_as_in_beer](http://en.wiktionary.org/wiki/free_as_in_beer)


