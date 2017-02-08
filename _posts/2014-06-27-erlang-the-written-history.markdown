---
author: viviworld
comments: true
date: 2014-06-27 15:14:21+00:00
layout: post
link: http://www.labazhou.net/2014/06/erlang-the-written-history/
slug: erlang-the-written-history
title: Erlang：写作的历史
wordpress_id: 803
categories:
- 编程
tags:
- erlang
- Haskell
- java
- O’Reilly
- 写作
---

Erlang现在25岁了。我从最开始就接触了Erlang，看着它从一个想法成长为一个拥有大量用户的、完全成熟的编程语言。

我写了第一个Erlang编译器，教了第一门Erlang课程，和我的同事合写了第一本Erlang书。早期成功的Erlang公司之一是我创办的，涉及了该语言及其应用程序的各个开发阶段。

在2007年，我写了《[Programming Erlang](http://shop.oreilly.com/product/9781934356005.do)》（[官网](http://www.pragprog.com/)）------自从《Concurrent Programming in Erlang》（Prentice Hall, 1993）出版，已经过去14年了------我们的用户正迫切需要一本新书。因此在2007年，我咬紧牙关开始写作。我非常幸运，Dave Thomas做了我的编辑，他教我很多写作方面的东东。第一版是相当有野心的，我想描述该语言的每一个地方和主要类库，还有示例代码和实际运行着的、真实世界的例子。因此这本书包含有可运行的代码，比如SHOUTcast服务器，因此你能够向设备添加音乐，以及一个全文索引系统。

《Programming Erlang》第一版刺激了一批活动，这本书卖的很好。它是通过Pragmatic Press Beta出版过程发布的。这个beta出版过程很棒，作者可以从读者那里很快得到反馈。读者下载一个未完成的书的、PDF版，开始阅读并就文本进行评论。既然这本书本来就是未完成的，他们就可以影响到书的剩余部分。当书的完成度有70%的时候，就能以beta形式发布了。

第一天，超过800人买了这本书，第二天在书的勘误页多了大约1000个评论。怎么会有这么多错误呢？我的五百页的书，貌似每页就有4条。这让我大吃一惊。Dave和我像奴隶一样，辛苦地修复了错误。尽管我知道当这本书完成的时候，我要花费一个两周的假期。

在最初的PDF版发布数月之后，最终版准备好了，我们开始发布纸质版。

一个奇怪的现象发生了------Prags已经出版了一本Erlang书，有传言说它卖得很好。很快我开始听到谣言，O'Reilly正在寻找作者，我的很多朋友被联系到，询问他们是否对编写Erlang书有兴趣。

真是奇怪，当你想写书的时候，你找不到出版商。但是，当一个已证实的出版商想出版关于某个特定话题的一本书的时候，它却找不到作者。

下面是2007年以后的时间线



	
  * 2007 - [Programming Erlang ](http://shop.oreilly.com/product/9781934356005.do)- Armstrong - (Prag Press)

	
  * 2009 - [ERLANG Programming ](http://shop.oreilly.com/product/9780596518189.do)- Cesarini and Thompson - (O'Reilly)

	
  * 2010 - [Erlang and OTP in Action](http://www.manning.com/logan/) Logan - Merritt and Carlsson - (Manning)

	
  * 2013 -[ Learn You Some Erlang for Great Good ](http://shop.oreilly.com/product/9781593274351.do)- Hebert - (No starch press)

	
  * 2013 - [Introducing Erlang: Getting Started in Functional Programming](http://shop.oreilly.com/product/0636920025818.do) - St. Laurent (O'Reilly)

	
  * 2013 - [Programming Erlang](http://shop.oreilly.com/product/9781937785536.do) - 2'nd edition - Armstrong - (Prag Press)

	
  * 2014 - Designing for Scalability with Erlang/OTP - Cesarini and Vinoski - (O'Reilly)


不仅仅Erlang得到了关注，像Haskell之类的语言需要去竞争，因此Bryan O'Sullivan, John Goerzen 与 Don Stewart合著的《[Real World Haskell](http://shop.oreilly.com/product/9780596514983.do)》在2008年出版了，Miran Lipovaca在2011年跟着出版了《[Learn You a Haskell for Great Good](http://shop.oreilly.com/product/9781593272838.do)》。

我的Erlang书好像打破了沉默，O'Reilly跟着的《Erlang Programming》和《Real World Haskell》，鼓舞了Starch出版社，《Learn You a Haskell for Great Good》鼓舞了《Learn You Some Erlang for Great Good》，轮子开始转起来了。


### 快进到2013年


Prags联系到我，”你的书想补充吗？“，补充什么？这本2007年的书有一些过时了。Erlang核心变化了一点，但是类库已经变化了，用户群有了增长。但是，对于第二版而言，最重要的是当时市场上已经有其它四本书了。

我在第一版的目标一直是”描述所有“、”记录没有被记录的所有点“。我想要一本覆盖全面的书，我想要一本同时面向初学者和高级用户的书。

现在，当然是不可能的。面向初学者的书有大量的、高级用户不想看的解释。面向高级用户的文字，初学者理解起来有困难，或再糟糕点儿，不可能理解。

当我想着手第二版时------我想------”我不得不做的所有工作就是扫一遍示例，确保它们运行良好.“我也想过，要去掉一些相当烦人的附录，去掉一些古怪的章节，增加一个关于类型系统的章节，我是这样想的。

结果没有成为这样子，我的编辑，曾经给予我帮助的Susannah Pfalzer，可能了解这一点，只是没有告诉我。

这个过程我写了七个新章节，去掉了一些相当烦人的附录和旧的章节。

第二版最大的不同是对于目标群体的重新定位。还记得我说过，第一版目标是高级用户和初级用户。现在市场上有四本具备竞争力的书了。Fred Hebert的书面向初次使用的用户是非常棒的，带有美丽的手绘卡通。Francesco and Simons在OTP上做得好，因此我要重新定位这本书，集中在一个小众群体。

那么是谁呢？在写第二版时，我们花了大量时间聚焦在目标用户上。当前七章准备好的时候，我们给14位评论家发送了这些章节。他们当中有3个高级用户------精通Erlang的程序员，他们对Erlang不了解的东西应该刻在了茶叶后面。我们也找了4个完全的初学者------会用Java编程但是不懂Erlang，剩下的全是中等用户：他们已经做了一年Erlang，不过仍然在学习中。我们把这本书扔给了他们，看看会有什么效果。

最吃惊的是：一些真正的初学者不理解我们写的东西，某些想法只是”太陌生“了。我很惊奇，天呀！当你25年来一直与Erlang生活、呼吸、做梦、睡觉时，你知道Erlang的家底，你认为这是理所当然的。

因此我丢弃了这些家伙不能理解的文字，重新开始。我的一个评论者（一个完全的初学者）有问题，我重新写这些文字，他们再读，他们仍然不能理解。”这都是什么人呀，白痴或者其它？我正在拼命解释所有东西而他们仍然不能理解！“我（再次）丢弃了重写的这些文字，给他们发送了第三版。

好了！他们理解了！快乐的日子再次到来了！有时候新想法只是”太陌生“而不能领会。但是到目前为止我对于我要增加多少解释已经了然于胸：大约比我想的多出30%，毕竟，如果你写了一本书，你不想让买了这些书的人因为它太难而读不下去。

我也从[Bruce Tate](http://en.wikipedia.org/wiki/Bruce_Tate)那里得到了建议------Bruce写了《10分钟学习600种语言》（在[Seven Languages in Seven Weeks](http://shop.oreilly.com/product/9781934356593.do)）。如果你给Bruce提供啤酒，友好地询问，那么他会是一个不错的人，带有刻薄的德克萨斯口音。Bruce可以在10秒内给任何人教任何语言，因此他是评论你的书的、不错的人选。

那些高级用户反映如何呢？我的书长了30%，针对转换那些已经看到希望、想放弃邪路的Java程序员，给他们带来Erlang编程的乐趣，但是高级用户呢？

抛弃了高级用户------他们甚至不会买这本书，因为他们无论如何都懂的。因此我扼杀了我的孩子，放弃了很多没有人曾看到过的高级资料。我的目标是把这些忽略的高级材料放在一个网站上。

我还从[Francesco Cesarini](http://www.oreilly.com/pub/au/3373)那里得到了一个不错的提醒：”他们喜欢练习题。“因此我差不多在每章的后面增加了练习题。

因此没有理由不去抓住一个Erlang编程的课程：每章后面有练习题！

原文地址：[http://www.josetteorama.com/erlang-the-written-history/](http://www.josetteorama.com/erlang-the-written-history/)
