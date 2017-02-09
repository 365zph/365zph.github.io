---
author: viviworld
comments: true
date: 2014-05-14 01:57:53+00:00
layout: post
link: http://www.labazhou.net/2014/05/why-bad-scientific-code-beats-code-following-best-practices/
slug: why-bad-scientific-code-beats-code-following-best-practices
title: 为什么糟糕的科学代码战胜了遵循“最佳实践”的代码
wordpress_id: 659
categories:
- 编程
tags:
- api
- 程序员
---

我刚刚读了“[科学代码的低品质](http://techblog.bozho.net/?p=1423)”，它声称科学家写的代码比有“软件工程师”参与的代码要更糟糕些。

我所处的工作环境有十多年了，那里由具有数学或物理学背景的人统治，他们经常缺少“软件工程师”的认识。

最大的麻烦总是由大多数把自己定位成程序员的人造成的。我愿意承认我至少造成了一堆麻烦，至今没有清理完。也有一些其它的大麻烦，代码幸运地被浪费了，这意味着对我老板的伤害被限制到了浪费在我自己工资上，没有给其他人的生产效率带来负面影响。

多数情况，我承认有些忏悔。我宁可尽力保持事情足够简单，我不认为我已经做到了，在过去的5-6年里，有些事情让很多人很好笑地看着我，他们已经把一天最美好的时光花在了我的带有小聪明的产品处理上。

我认识一些没有明确忏悔过的程序员。人们觉得他们滑稽，他们却认为自己是对的，其他每个人都是疯子。

同时，那些“不是”程序员、但更多是个数学家、物理学家、算法设计者，科学家的那些人，你给他们列举了如下种类的罪状：



	
  * 很长的函数

	
  * 糟糕的命名(m, k, longWindedNameThatYouCantReallyReadBTWProgrammersDoThatALotToo)

	
  * 访问所有的地方------全局/singleton，“神器（God Objects）”等

	
  * 崩溃（空指针，边界错误），由工具集/大规模测试来大量减少

	
  * 在类似bug上完全缺乏兴趣（差不多依赖工具减少）

	
  * 不合适地勉强使用聪明程序员写的类库，包含了过多的操作符、模板和东东


你看，我可以处理这种事情了。我很少碰到问题，如果有人想让我帮忙调试代码，以找出这些家伙正在试图做什么。我是指在软件意义上。算法上或许我帮不上忙。但是我通常知道 他们想让什么变量传递给什么函数。

软件工程师不全是这样，他们的罪行可以完整归类如下：

	
  * Multiple/virtual/high-on-crack继承

	
  * 主要由一些瘦封装器以及一些函数指针/虚函数组成的、可能在中断处理（interrupt handlers）内部或不在内部的7到14个堆栈块（stack frames）

	
  * 文件在多个文件夹传播

	
  * 使用来自地狱的动态结构查找文件夹名字，这些名字由运行时的各种片段拼凑而成，等等。

	
  * 动态加载和其它grep-defeating技术

	
  * 一大群不易辨认的名字，比如DriverController, ControllerManager, DriverManager, ManagerController, controlDriver ad infinitum---彼此互相调用

	
  * Templates调用带有声明的、期望可见的重载函数，在那个地方template被定义了，也可能没有定义。

	
  * Decorators、metaclasses、代码生成等等


后果是你不知道谁调用了什么或为什么调用，调试器充其量能用，IDE和grep正慢慢、可怕地死去等。在眼泪不由自主地从你的眼睛流出来之前，你确实得放弃搞清楚的打算。

当然这是一个显而易见的夸张，不是每个人一直是一个罪犯，比如，我原则上是一名“程序员”而不是“科学家”，我强烈认为毕竟我有一个积极的生产力，只是你产生了那个想法。

科学代码能够从更好的“软件工程师”那里受益吗？或许是，但是我不会相信软件工程师会带来那些好处！

思想简单，无忧无虑，几近不称职可能比向地狱铺一条高速公路的强劲的、好的计划要好些。计算机之外的“真正世界”充满了这样的例子。

哦，恐怕一个真正残忍的观察太过真实而无法忽略：懒惰是很多麻烦的根源。一个科学家要操心他自己的学科，因此他没有时间去不必要地复杂化代码。很多程序员在工作上没有真正的实质---他们的工作是琐碎的---因此他们手头有太多的时间，他们习惯了思索“API 设计”，因此庞然大物就出现了。

（事实上，当工作从技术上远离琐碎/或在社会上，程序员可怕的训练把他们的关注从当前责任移走的时候------该死的事情实际上是工作，易用、有效/便宜，等？------取而代之的是，他们宣称除了着手于超出信任的复杂化可怕的API，什么也不用负责任。同时，从功能上讲，事情很少起作用。）

原文地址：[http://www.yosefk.com/blog/why-bad-scientific-code-beats-code-following-best-practices.html](http://www.yosefk.com/blog/why-bad-scientific-code-beats-code-following-best-practices.html)
