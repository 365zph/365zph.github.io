---
author: viviworld
comments: true
date: 2015-07-22 22:28:06+00:00
excerpt: 这个补丁修复了一个地方，却常常破坏了很多地方。我相信有必要时不时地拒绝 bug 修复，并要求其作者重新制作补丁，以保护项目避免遭受更大的问题。
layout: post
link: http://www.labazhou.net/2015/07/a-few-valid-reasons-to-reject-a-bug-fix/
slug: a-few-valid-reasons-to-reject-a-bug-fix
title: 拒绝修复 bug 的几个正当理由
wordpress_id: 2303
categories:
- 测试
tags:
- bug
- 代码
- 代码审查
- 单元测试
- 补丁
- 重构
---


	
  * 原文地址（original source）：[http://www.yegor256.com/2015/06/22/valid-reasons-to-reject-bug-fix.html](http://www.yegor256.com/2015/06/22/valid-reasons-to-reject-bug-fix.html)

	
  * 作者（author）：[https://twitter.com/yegor256](https://twitter.com/yegor256)





* * *



当某些功能没有按预期运行时，bug 就出现了。一次 bug 修复基本上是给现有代码打一个补丁，它应该解决当前问题，以确保「该功能」按预期运行。可是，这个补丁修复了一个地方，却常常破坏了很多地方。我相信有必要时不时地拒绝 bug 修复，并要求其作者重新制作补丁，以保护项目避免遭受更大的问题。根据我的经验，对于这种拒绝，存在着一些正当理由。

[caption id="attachment_2304" align="alignnone" width="600"][![《完美犯罪（El Crimen Perfecto）》，导演：Álex de la Iglesia](http://www.labazhou.net/wp-content/uploads/2015/07/crimen-ferpecto-1024x526-600x308.jpg)](http://www.labazhou.net/wp-content/uploads/2015/07/crimen-ferpecto-1024x526.jpg) 《完美犯罪（El Crimen Perfecto）》，导演：Álex de la Iglesia[/caption]


### 它降低了代码覆盖率


这是非常常见的情景：在某个地方做了修改之后，单元测试在其它地方失败了。bug 被修复了，但是一些可能不相关的单元测试开始报告失败。由于压力或仅仅因为我们的懒惰，我们没有修复它们；我们只是删除了测试、或将它们标注为临时的「跳过」。问题被解决了，构建是干净的，那么合并该补丁，收工，对吗？错！

即使我喜欢尽可能的[偷工减料](http://www.javacodegeeks.com/2015/01/15/how-to-cut-corners.html)，但是对于这种问题，我不推荐你那样做。

单元测试的存在恰恰是为了防止我们在面临压力时去破坏代码。

很明显，存在着一些情景，比如单元测试错了，我们不得不删除它们。对于这种情况，记得要创建新的单元测试。

还有一些情景，比如 bug 必须尽快修复，保证系统线上运行，而修复所有单元测试将花费 1 个小时。这种情况强烈预示着，你已经处于一种可怕的潜在情景，那就是产品中的测试覆盖率。毫无疑问，我们不得不做出修复，并在一段时间后让测试通过。但是，对于这种情况，要确保团队在修复该 bug 之后的下一个任务就是纠正那些不好使的单元测试。我推荐阅读 Michael Feathers 编写的《[修改代码的艺术](http://www.amazon.com/gp/product/0131177052/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0131177052&linkCode=as2&tag=yegor256com-20&linkId=D2WNVUW64RHDRGSC)》，本书为该主题提供了正解。

[caption id="attachment_2305" align="alignnone" width="226"][![Michael Feathers 编写的《修改代码的艺术》](http://www.labazhou.net/wp-content/uploads/2015/07/book-legacy-226x300.jpg)](http://www.labazhou.net/wp-content/uploads/2015/07/book-legacy-226x300.jpg) Michael Feathers 编写的《修改代码的艺术》[/caption]


### 它不会重现问题


有时候整个系统挂掉，仅仅是因为某行代码里的一个小拼写错误。明显的 bug 修复就是删除这个拼写错误，如果我们关心项目质量，这就不是项目期望我们做的操作。问题不在于拼写错误，而在于缺乏单元测试，单元测试在部署阶段是可以捕捉到这个错误的。

真正问题在于，[测试代码覆盖率在代码的这个部分是缺失的](http://www.labazhou.net/2015/03/software-testing-is-a-loser-bet/)。单纯地删除拼写错误，无助于整个项目。而且，我们在伤害它------我们正在掩盖真正的问题。

不管问题多么小、不管其表现形式是多么地迷惑人，bug 修复必须包含可以首先重现该 bug 的额外测试。没有这样的测试，所谓的 bug 修复只是在浪费项目的金钱。

进一步讲，没有重现问题的单元测试，就无法保证 bug 修复不会带来更多的 bug。我甚至敢说，我们的 bug 修复越多，引起的熵【注1】就越高。减少这种不确定性的唯一方式就是用单元测试覆盖代码。没有测试，bug 修复将给代码库带来更多的无序。


### 它太大了


bug 修复不是功能；它们必须小而专注。在修复 bug 时，引入了某些重构，这是程序员自我陶醉时经常要犯的错误。结果，补丁大得难以理解。我不是反对重构；重构对于项目非常重要，属于积极的举动，但要在 bug 被修复、合并之后，专门来做重构。

请在修复 bug 的时候，不要重构代码！

创建一个新的单元测试，重现 bug，并提交。在现有的代码库里修复 bug，不管它是多么丑陋。创建新 bug，要求团队改善丑陋代码库的状况。如果感兴趣，就把这些 bug 分配给你自己。或许其他人只是对修复它们以及重构代码感兴趣。不过所有这些都会在其它的 pull request 里发生，也带着新的代码审查和新的合并。

修复那些糟糕的代码，和懒惰、不愿意没有关系。这是一项纪律，比良好意图[更加重要](http://www.javacodegeeks.com/2015/01/15/how-to-cut-corners.html)。


### 它不只解决一个问题


每次总是修复一个问题------就这么简单，没有例外。当一个 bug 修复的补丁包含了修复多个问题的代码修改时，就很难理解哪个问题被测试到了，哪个是可重现的、以及它们彼此有何关联。把多个 bug 修复整合到一次 pull request 是一种非常糟糕的实践。

不管这次修复多么简单，要确保它和其它修复分开。逐个审查代码、测试以及合并。这也增加了追溯代码修改的便利性，很容易理解谁做的此次修复、谁审查的代码、以及什么时候被合并（和部署）。



* * *






	
  * 注1：在信息论中，熵是接收的每条消息中包含的信息的平均量，又被称为信息熵、信源熵、平均自信息量。这里， 消息代表来自分布或数据流中的事件、样本或特征。（熵最好理解为不确定性的量度而不是确定性的量度，因为越随机的信源的熵越大。）[https://zh.wikipedia.org/wiki/%E7%86%B5_(%E4%BF%A1%E6%81%AF%E8%AE%BA)](https://zh.wikipedia.org/wiki/%E7%86%B5_(%E4%BF%A1%E6%81%AF%E8%AE%BA))


