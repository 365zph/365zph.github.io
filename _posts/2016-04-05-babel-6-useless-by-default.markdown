---
author: viviworld
comments: true
date: 2016-04-05 00:35:36+00:00
excerpt: 学习 JavaScript 编程最痛苦的事情之一，就是构建系统让人头晕，你不得不让所有与编程无关的东西去运行你的代码。
layout: post
link: http://www.labazhou.net/2016/04/babel-6-useless-by-default/
slug: babel-6-useless-by-default
title: Babel 6：默认状态时，毫无用处
wordpress_id: 3277
categories:
- 编程
- 软件
tags:
- Babel
- javascript
- npm
- 用例
- 配置
---


	
  * 原文地址（original source）：[http://fourlightyears.blogspot.jp/2016/03/babel-6-useless-by-default-lesson-in.html](http://fourlightyears.blogspot.jp/2016/03/babel-6-useless-by-default-lesson-in.html)

	
  * 原文作者（author）：[Andrew Stuart ](https://www.blogger.com/profile/13104066621043790256)





* * *





## 关于怎样不去设计软件的经验


学习 JavaScript 编程最痛苦的事情之一，就是构建系统让人头晕，你不得不让所有与编程无关的东西去运行你的代码。

构建系统的复杂生态系统是怎么回事，它们如何协同运作，怎样配置并驱动它们，对于普通人而言，要理解这些事情，真的太难了，非常难。立志做开发的 JavaScript 新手程序员们，从一开始就面临着绝逼陡峭的学习曲线。如果你认为比较轻松，那么就应该爬过学习曲线，完成学习过程，并忘掉它有多么难。

因此，构建工具越易于安装和使用，就越好。理想状态下，对于普通应用场景，终端用户除了安装构建工具，并掌握其基本、甚至高级用法，就不需要再做什么了。

Babel【注1】 就是这种构建系统的核心之一，它可以把 ES2015 版本的代码编译成 ES5【注2】，而后者可以在所有浏览器运行。

[Babel 默认情况下，什么也不会做](https://babeljs.io/docs/plugins/)。即默认状态下，一无是处。想尝试一些功能吗？你必须先配置，当然，这意味着你必须开始学习如何驱动和配置 Babel。

学习一种新系统，第一步往往最痛苦、最让人迷茫、也是最耗时的。为了配置某个小地方，一大堆问题接踵而至。我真地要那样做吗？我应该修改设置吗？我为什么要这样做？它有什么用？我破坏了什么？还有更多东西要配置吗？在我看完文档之后，我手头用的是最新信息、或已经修改了系统？我发现三套操作步骤在做同样的配置，还彼此矛盾，为什么？最大的问题是，网页上的操作步骤为什么和我屏幕上显示的不一样呢？当然，「我已经按照操作步骤修改了，为什么它还不正常呢，有什么地方弄错了吗？」。所有这些问题，都源于一种愚昧的迷雾：软件是什么；软件怎样协同运行；软件的意图是什么；它为什么要那样运行。你仰天长啸、扼腕叹息，fuck，看似「简单的」兔子洞【注3】究竟有多深？每个人学习一种新技术时，都要经过这个阶段。

如果构建工具要求用户哪怕应付一个配置设定，它们就是把大量学习成本强加给了用户。在尽量完成目标时，可能要数个小时、可能（很有可能）搞不定。对于很多用户而言，认知负荷过高。用户或许都折戟于配置上，尽管开发人员觉得它太基础，简直不值一提。

反过来讲，如果构建工具不要求[用户配置什么](http://www.labazhou.net/2015/03/devops-the-problem-with-configurations/)，就已经节约了用户时间，并驱使用户取得「些许成功」。

太多的 JavaScript 构建工具认为，开发人员在意开发工具。他们认为，开发人员想理解构建工具，想学习、想配置那些构建工具，想为它们编程。我来这里不是为构建工具编程的，而是为应用程序代码编程。我希望 JavaScript 构建工具像用例那样参与进来，尽可能在默认状态下就做好预配置。

有经验的 Babel 6 用户扫清了我的顾虑，我说配置很难，但是他们说「很容易！」。你修改一个文件： .babelrc，npm 安装好你的预设，安装好你的插件，修改好你更新的 webpack config，就 ok 了！只需 60 秒，你就会爆粗口了。

有经验的开发人员忘记了，让没有经验的用户做一些需要 60 秒的任务，有多么耗时、多么困惑，你简直难以想象。

只有在优化最终生产环境代码时，配置 JavaScript 构建工具才是必要的。强迫用户提前配置每个地方，属于过早优化，浪费用户宝贵时间，把认知负荷强加给用户，使得整个 JavaScript 开发进程空前复杂、增加用户上手难度，从而扼杀他们的激情，并终止总体进程。

因此，当 Babel 6 决定，它从一开始就什么都不做，它和软件可用性的传统认知刚好相反，它提供了合理的默认设置，提供了大部分常见的用例，还有最完美的、对于安装和配置的零要求。

Babel 应该预先配置好 JavaScript 开发的基础：异步等待、装饰器（Decorator）等。它们把用户想用的所有东西放在那里。专家级的 Babel 用例被裁减到最小化。它不准备构建为可用的基础用例。我甚至不需要考虑该怎样配置 Babel，除非我在开发阶段，已经越过了其它必要的学习曲线，比如学习 ES2015 和浏览器编程。

Babel 想存在下去，想被看到、被听到、以及被讨论。不过，它像管道系统，只要你没有特殊需求，从来都不应该考虑太多。Babel 需要配置的情景，有点像厨房里的水龙头，自己动手接上热水，安装热水水箱，安装太阳能电池板，并设置好温度。不需要做其它事情。Babel 通常默默无闻。网上也不应该充斥着指导你如何配置 Babel 的博客文章，有的文章正确、有的错误、有的过期、有的还前后矛盾。开发人员应该正确地配置一次即可，因此你无需想太多。

最后，Babel 项目本身的成本，就是为还没有搞定配置的那些人提供各种支持，那些人甚至不明白要配置什么------只有某个地方无法正常运行。Babel 项目搬起石头砸自己的脚，为自己找事。Babel 开发人员应该总是关注：怎样减少或去掉配置的需求，怎样找到预配置的有效方式，以及找到办法、让人们用更少的认识就能使用 Babel。

好了，我回头打算看看怎样配置 Babel，才能使用 async 和 await。我真的希望它最初就配置好了。多么浪费时间呀。

附：顺便说一下，我的确熟悉 Babel 预设置，也有很多配置。适量的配置是不存在的。


### 注释

* 注1：Babel是一个转换编译器，它能将ES6转换成可以在浏览器中运行的代码。Babel由来自澳大利亚的开发者Sebastian McKenzie创建。他的目标是使Babel可以处理ES6的所有新语法，并为它内置了React JSX扩展及Flow类型注解支持。[http://www.infoq.com/cn/news/2015/05/ES6-TypeScript](http://www.infoq.com/cn/news/2015/05/ES6-TypeScript) 
* 注2：请参考《ES5, ES6, ES2016, ES.Next: JavaScript 的版本是怎么回事？》[http://huangxuan.me/2015/09/22/js-version/](http://huangxuan.me/2015/09/22/js-version/) 
* 注3：《爱丽丝梦游仙境》（英语：Alice's Adventures in Wonderland，通常缩短至Alice in Wonderland）是路易斯·卡罗（Lewis Carroll）出版的儿童文学作品。故事的主角爱丽丝，从兔子洞掉进一个充满奇珍异兽的梦幻世界，遇到各种懂得说话的动物。这童话1865年出版，一直深受不同年纪的读者喜爱。《爱丽丝梦游仙境》是一个典型“奇幻文学”的例子，亦是最具影响力的童话故事之一。已被翻译为174种语言出版。[https://zh.wikipedia.org/wiki/%E7%88%B1%E4%B8%BD%E4%B8%9D%E6%A2%A6%E6%B8%B8%E4%BB%99%E5%A2%83](https://zh.wikipedia.org/wiki/%E7%88%B1%E4%B8%BD%E4%B8%9D%E6%A2%A6%E6%B8%B8%E4%BB%99%E5%A2%83) 
