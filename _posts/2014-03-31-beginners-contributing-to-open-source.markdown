---
author: viviworld
comments: true
date: 2014-03-31 10:43:20+00:00
layout: post
link: http://www.labazhou.net/2014/03/beginners-contributing-to-open-source/
slug: beginners-contributing-to-open-source
title: 初学者指南：为开源做贡献
wordpress_id: 497
categories:
- 编程
tags:
- CocoaPods
- github
- ios
- rails
- Roboto
- rubygem
- tweet
---

当我刚开始做Rails开发者时，我认为所有的Rails gems都是魔法。一些聪明人正在制作这些牛逼的类库让我使用！我不知道这些类库有多少可以使用，我认为它们是好的。它们运行着，并做了我需要它们做的工作。它们好像如此深奥、被想出来，以致于我甚至不知道该如何为它们贡献力量，即使我想！

时至今日，我仍然没有给Rails社区贡献任何开源代码。那是因为Rails社区在开源方面非常活跃，因此找到你要贡献的东西实际上是比较困难的！当然你能够翻阅问题并试着解决，但是，老实讲，它们通常太复杂了、令人望而生畏。有这些聪明人讨论问题，你能足够优秀地解决问题是难以想象的！

快进到Mobile Makers，那时候我刚接触iOS，我第一次给开源代码做了贡献！从那以后，我做了更多，我不再害怕向甚至更多的项目贡献代码！下面是我如何迈出这一步以及在这个过程中我学到了什么：


## 它不是魔法


走出Rails社区，我很快知道了，大家对开源类库事实上有某种不信任感。当我想一直使用所有的CocoaPods时（就像Rails！），团队的高级iOS工程师总是质疑外部类库的使用，如果可能，宁愿建立我们自己的类库。

在iOS项目，有很少的iOS类库可以一直使用的，大多数项目仅仅在开始的时候使用一些类库！由于CocoaPods的出现以及删除或升级依赖项是如何容易，情况正在发生着变化，但是它还达不到Rails的级别，你的大部分项目仍然由即插即用类库构成。

意识到这些外部类库不是魔法，我的心态改变了，也让我较以前产生了巨大的改变。懂得了编写类库的那个人是一个真实的人，他会犯错，或许不会写出最优的代码，他也不能一直考虑到所有的边界情况，这让我能够轻松发现我能够做贡献的小的（或大的）地方。


## 关注就是共享


有一些人鼓励积极寻找开源项目去贡献力量，而我发现我贡献的所有项目都是实际在我自己的代码中用到的。

真相是，我没有时间为了贡献而去主动搜寻github上的问题/类库。但是，当我在自己的项目中用到一个类库时，我希望它具备X功能或那个bug Y被解决了，搞定并反馈回去是明摆的事！事实上，自从我喜欢向开源贡献力量以后，当我发现这些机会时，我是超级激动的！

这把我带到了下一个论点……


## 它是这样一种美好的感觉……


向开源贡献力量真的容易上瘾！先前知道了如何编码，让计算机实现你的愿望是不可思议的，这让你觉得你像个魔法师。但是，当你能够把其他人的“有魔力的”代码变得更好、且他们认同你能够使代码变得更好（通过merge）时，这种感觉是无法用言语表达的。它就像你刚刚变成了10级的魔法师而不是1级。


## 小的开始


此外，我把开源贡献者看做是用魔棒来作彻底改变、改进一切的魔法师，但实际情况是大多数变化都很微小。他们只是根据每个人的基本方式累计增加，并最终改变和完善了整个类库。因此不要低估小改动的力量！

下面是个例子，我最近贡献力量的过程：


### 修改一个README


我可能想把[Toast类库](https://github.com/scalessec/Toast)增加到我的iOS项目，但是他们在README没有提到有可用的CocoaPod。既然我只是想测试我项目中的类库，我想让它较为容易地移除掉。因此即使我以前使用过这个特定类库，也知道它好用，我开始为了另一个Toast类库而搜索[CocoaPod](http://cocoapods.org/)。

找了一些类库，我发现这个特定的Toast类库事实上就是CocoaPod！为了确保其他iOS开发者知道有可用的CocoaPod，我就CocoaPod安装说明提交了一个pull request到类库的README。小改动，但是希望对其他开发者有帮助！


### 增加额外相同的功能


在为[CodePath](http://thecodepath.com/)最终项目构建Android app时，我的团队想尝试当前官方Android字体---[Roboto](http://developer.android.com/design/style/typography.html)。事实表明它在并入外部字体到Android时非常繁琐，因此，我们使用名叫[RobotoViews](https://github.com/eeVoskos/RobotoViews)的类库来解决。基本上，每个view不得不经过配置才能得到Roboto的typeface。

然而，有一个我们需要的类库而RobotoViews没有包括进来---较新的Switch view。添加Switch view只需按照其它views的方式大量地拷贝/粘贴，因此它的添加不是太难，但是另一个view可以作为RobotoViews使用！

换句话说，RobotoViews的作者已经做了所有艰难的工作使得只需要修改一些地方就可以添加一个新的view。

类似的，我通过给流行的[iOS Foursquare client library](https://github.com/Constantine-Fry/Foursquare-API-v2)添加原来没有的一个额外功能来贡献力量，只是因为有了作者抽象这个过程的工作，这非常容易添加。


### 重构


当我注意到带有少量变化的三个函数有着相同的代码时，我给[ECSlidingViewController](https://github.com/ECSlidingViewController/ECSlidingViewController)添加了一个非常小的修改，来确保在滑动菜单滑出去时键盘隐藏掉。因此我重构了代码，产生一个函数，让三个函数仅仅通过传入一个不同的参数来调用它，因此将来需要改动这个函数的人只需要修改一次。

正如你看到的，我的所有开源贡献都是非常微小、容易做的！当你坚持使用外部类库时，你会看到相似的机会。因此向前走，并作出小的改动------它们是有价值的！


## 怎么做


看看这个伟大的《[RailsCast：一步一步教你如何为开源贡献力量](http://railscasts.com/episodes/300-contributing-to-open-source)》（它和非rails项目非常类似）。但是基本上，都有下面的几步：


### Fork


在Github上找到你想贡献的类库，只需点击Fork按钮！

[![github fork截图](http://www.labazhou.net/wp-content/uploads/2014/03/github-fork1.png)](http://www.labazhou.net/wp-content/uploads/2014/03/github-fork1.png)


### Clone


下一步，克隆你想fork的类库------它现在应该在你的名字下（比如：NatashaTheRobot/ECSlidingViewController），而不是原作者！

[![github clone截图](http://www.labazhou.net/wp-content/uploads/2014/03/git-clone-Screen-Shot.png)](http://www.labazhou.net/wp-content/uploads/2014/03/git-clone-Screen-Shot.png)


### Branch, Change, Push


一旦你克隆了代码库，改变为代码库文件夹。接下来，用能够反映你将要做的修改的、有意义名字来checkout一份新的分支。作出修改，push这个分支到github。

当你去你的Github profile主页，你会看到一个大大的绿色“Compare and Pull Request”按钮。看一下你的文件，确认一切ok。然后确信你给原始分支发送一个pull request（不是你fork的那个分支）。当你做完pull request之后，应该看看是不是这样！再一次，确认你刚刚给原始作者的master分支的master做了一个pull！

[![git pull request](http://www.labazhou.net/wp-content/uploads/2014/03/git-pull-request.png)](http://www.labazhou.net/wp-content/uploads/2014/03/git-pull-request.png)


### Tweet


这一步当然是可选的，但是我喜欢给作者发送tweet，告知他们变化。他们可能没有打开github的通知功能，尤其是那些最近很少改动的、比较老的代码库，因此让他们知道并展开一次沟通是比较好的。

他们或许太忙而没有merge，因此当他们回复，并告知你，在他们有空的时候再去看。你知道你的pull request不会永远悬而不决了！


### Enjoy！


真的，为开源贡献力量真的有意思，也是跟最好的人学习以及提高你自己技能的有效方法。希望这个向导能够减轻你对开源的惧怕！！！

如果你已经贡献了，请在评论里分享你的故事！

原文地址：[http://natashatherobot.com/beginners-contributing-to-open-source/](http://natashatherobot.com/beginners-contributing-to-open-source/)
