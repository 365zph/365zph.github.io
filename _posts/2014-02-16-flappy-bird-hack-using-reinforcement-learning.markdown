---
author: viviworld
comments: true
date: 2014-02-16 14:12:40+00:00
layout: post
link: http://www.labazhou.net/2014/02/flappy-bird-hack-using-reinforcement-learning/
slug: flappy-bird-hack-using-reinforcement-learning
title: Flappy Bird强化学习
wordpress_id: 280
categories:
- 编程
- 软件
tags:
- Flappy Bird
- javascript
- Q Learning
- 机器学习
---

## 使用强化学习来hack Flappy Bird




### hack


（译者注：原文这里是视频，请自行观看，本文不再网页呈现。视频地址：[http://www.youtube.com/embed/BV7a4rufMOg](http://www.youtube.com/embed/BV7a4rufMOg)）

本文介绍了如何hack流行游戏Flappy Bird【注1】。虽然该游戏已经从Google Play和App Store[下架了](http://news.cnet.com/8301-1035_3-57618612-94/bye-bye-flappy-bird-popular-game-grounded-by-its-creator/)，仍然阻止不了人们为网络创造非常好的复制品。人们也催生了该游戏的一些有意思的参数：“[Flappy Bird Typing Tutor](http://www.mrspeaker.net/dev/game/flappy/)”和“[Flappy Math Saga](http://www.lobe.io/flappy-math-saga/)”。

玩了多次，我看到了实践机器学习技能的机会，让Flappy Bird学习自己飞。上面的视频显示，经过真正良好训练的Flappy Bird基本上能够永远避开管道。


### 方法


最初我想在Android app上hack，计划使用[Monkeyrunner](http://developer.android.com/tools/help/monkeyrunner_concepts.html)获取屏幕截图、发生指令。但是截屏需要1-2秒，不能足够快速响应。

然后我找到了[@mrspeaker](https://twitter.com/mrspeaker)的游戏引擎，Omega500和他的[Flappy Bird版本](http://www.mrspeaker.net/dev/game/flappy/)做输入练习。我在输入组件里加了一些javascript Q Learning【注2】代码。


### 强化学习


基本原则：agent，当前的Flappy Bird，在一种状态下做出一个固定的动作。然后就处于一种新状态，并得到相应的奖励。不同的场景有用到很多的参数：方针迭代，值迭代，Q Learning等。


### Q Learning


我使用Q Learning，因为Q Learning是一种无模型的强化学习的技术。那意味着我不必为Flappy Bird建立动态模型：它上升或下降，对点击的反应，以及其它种类的东西。

[这里](http://artint.info/html/ArtInt_265.html)是一个不错的，简明的Q Learning描述。下面是算法：

[![Q Learning](http://www.labazhou.net/wp-content/uploads/2014/02/RLAlgorithm.png)](http://www.labazhou.net/wp-content/uploads/2014/02/RLAlgorithm.png)


### 状态空间


我用下面的参数离散我的空间。



	
  * 与较低管道的垂直距离

	
  * 与下一对儿管道的水平距离

	
  * Life：死亡 或 活着


[![Flappy Bird 状态空间](http://www.labazhou.net/wp-content/uploads/2014/02/StateSpace.png)](http://www.labazhou.net/wp-content/uploads/2014/02/StateSpace.png)


### 动作


对于每种状态，我有两种可能的动作：



	
  * 点击

	
  * 什么也不做




### 奖励


奖励的制定完全基于参数“Life”。



	
  * +1 如果Flappy Bird仍然活着

	
  * -1000 如果Flappy Bird死了




### 学习循环


数组Q初始化为零，我总是选择最好的动作，它会最大化我希望的奖励。为了中断连结，我选择了“什么也不做”，因为这是更为普通的动作。

第一步：观察Flappy Bird所处状态，朝着期望奖励最大化的目标做出动作。

让游戏引擎执行它的“tick”。现在，Flappy Bird处于下一个状态，s'。

第二步：观察新状态，s'和相关奖励。如果Flappy Bird活着，就+1；否则-1000.

第三步：根据Q Learning规则更新Q数组。

Q[s,a] ← Q[s,a] + α (r + γ*V(s') - Q[s,a])

alpha我选择0.7，因为我们有一个确定性的状态，我想它很难不去学习什么。折扣因子lambda是1.

第四步：设置当前状态为s'，重新开始。


### 下面的步骤


花6-7个小时训练Flappy Bird以达到足够好（150分）。开始时，通过不止一只bird来提高，把所有“学习”贡献给同一个Q数组。

另一个加快学习的方法就是让用户提供“好的”输入。马上，你就可以点击游戏让Flappy Bird跳了。但是，输入没有被学习者考虑到。

在移动手机上做！！如果谁有任何想法，请通过评论让我知道：）

译者注：对Flappy Bird有兴趣的读者，请移步果壳网，《Flappy Bird到底有多难？》试图说服你不要玩：）[http://www.guokr.com/article/437988/](http://www.guokr.com/article/437988/)

原文地址：[http://sarvagyavaish.github.io/FlappyBirdRL/](http://sarvagyavaish.github.io/FlappyBirdRL/)
注1：Flappy Bird：[http://zh.wikipedia.org/wiki/Flappy_Bird](http://zh.wikipedia.org/wiki/Flappy_Bird)
注2：Q-learning：[http://zh.wikipedia.org/wiki/Q-learning](http://zh.wikipedia.org/wiki/Q-learning)
