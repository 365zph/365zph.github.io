---
author: viviworld
comments: true
date: 2015-01-15 02:10:08+00:00
layout: post
link: http://www.labazhou.net/2015/01/10-things-learn-university/
slug: 10-things-learn-university
title: 你应该在大学学到的10个方面的知识
wordpress_id: 1532
categories:
- 职业
tags:
- AI
- google
- GPS
- 图灵
- 框架
- 汇编
- 物联网
- 编译器
---

原文地址（source）：[http://jj09.net/10-things-learn-university/](http://jj09.net/10-things-learn-university/)

[我去年毕业了](http://jj09.net/master-science-computer-science/)，想总结一下我的收获。在[StackOverflow Podcast #36](http://blog.stackoverflow.com/2009/01/podcast-36/)，Eric Sink说道：


<blockquote>优秀学生在课堂上学习计算机科学，然后自己编程。</blockquote>


我记得大学朋友在讨论他们第一份工作时的情景了，他们有90%的人会说类似的话：“这1个月的实习比我在大学3年学得都要多”。我不谈论我的工作了。刚开始我认为，他们很可能找了一个比我好得多的工作或实习岗位。我用了3年时间才理解了这种现象……这不是现象。他们认为，他们学了很多，因为他们能够使用框架搞定一些工作，框架在背后做了一些魔法（比如创建简单的、带有数据库的CRUD web应用程序，所有东西都是自动化的）。然而，在框架和硬件之间还有大量的技术。我注意到，很多开发人员不关心这一点。而且，没有它们你照样能够搞定工作。就像出租车司机不需要了解这个城市，只要他有GPS。我认为了解基础是有好处的。

有一些课程，能够帮你学到技术，在你找到工作后，你将不会感到烦恼了。同时，它们值得去学习，帮助你理解计算机工作原理，在我看来，将对你未来的工作有帮助。

下面是你应该在大学学习的10种技术/课程(大学是用来学习的最佳时机):



	
  1. 计算机架构：了解计算机工作原理，它们怎样表示数据（[补码](http://en.wikipedia.org/wiki/Two's_complement)【注1】、[IEEE二进制浮点数算术标准](http://en.wikipedia.org/wiki/IEEE_floating_point)【注2】）。有两本不错的书：《[计算机体系结构量化研究方法](http://www.amazon.com/Computer-Architecture-Fifth-Quantitative-Approach/dp/012383872X)》和《[计算系统的要素](http://jj09.net/a-book-that-every-programmer-should-read-the-elements-of-computing-systems/)》。

	
  2. 编译器：计算机结构的某种补充。它连接着软件和硬件。编译器的经典书籍有《[编译原理](http://www.amazon.com/Compilers-Principles-Techniques-Tools-Edition/dp/0321486811)》（又叫“龙书”）

	
  3. 算法和复杂度（O标记）：这是个有难度和有挑战的主题。需要大量时间，但是未来会得到回报。算法和计算复杂度的圣经是Cormen的书：《[算法导论](http://www.amazon.com/Introduction-Algorithms-Thomas-H-Cormen/dp/0262033844)》

	
  4. 自动控制（DFA、NFA、图灵机【注3】等）：“要认识到，语言里的字符串是表达任何问题的一种正式途径”。做为凌驾于所有软件和硬件建立之上的一种科学，这是计算机科学的首要法则。

	
  5. 汇编语言：帮助理解并行应用程序，以及出现在其中的bug。比如，由指令重新排序所引起的。

	
  6. 系统程序设计：对于云计算和虚拟机，这仍然是有用的主题，能够让你理解软件是如何与硬件交互的。

	
  7. 嵌入式设备：[物联网](http://en.wikipedia.org/wiki/Internet_of_Things)是未来，它也是有趣的（参看Jon Gallant的[博文](http://blog.jongallant.com/2014/11/iot-devs-needed.html)，他加入了微软的[物联网](http://www.labazhou.net/2014/11/iot-wont-work-without-artificial-intelligence/)团队）。

	
  8. 人工智能（AI）：每一年，设备都更加智能（包括[你的手机](http://www.wired.co.uk/magazine/archive/2012/02/start/google-ai-guy)、[医疗设备](http://mdcf.santos.cis.ksu.edu/)和[Google汽车](http://en.wikipedia.org/wiki/Google_driverless_car)）。根据比尔盖茨的预测，[AI将在未来10年爆发。](http://www.examiner.com/article/bill-gates-outlines-the-mindset-of-a-i-for-jobs-the-future)大学是学习AI基础的绝佳场所。

	
  9. 计算机网络：学习网络是不错的，数据是怎样在导线（包）中流动的，什么是DNS、CDN，我们在快速和可靠的数据交换中面临什么样的挑战和限制。推荐书目：A. Tanenbaum写的《[计算机网络](http://www.amazon.com/Computer-Networks-5th-Andrew-Tanenbaum/dp/0132126958)》。

	
  10. 计算机安全：每个人都想成为黑客。首先，你需要了解基础，还要警惕到，这个主题每年都在变化着（sha1正在被sha2取代，因为它不再“足够安全”了）。因为它变化如此之快，还没有更新及时的通用图书。然而，《[Unix與Internet安全防護─網路篇](http://www.amazon.com/Practical-Unix-Internet-Security-3rd/dp/0596003234)》仍然非常有价值。为了及时跟进安全问题，我强烈推荐你关注[Troy Hunt的博客](http://www.troyhunt.com/)（在我看来：它是互联网上最好的博客之一）。


有人会说：“图灵机？我会用到它吗？……很可能不会。”。但是，重申我在讨论[计算机科学](http://en.wikipedia.org/wiki/Computer_science)，而不是编程。没有这些知识，你照样可以生活，并作出让人惊奇的东西。就像刚才提到的出租车司机，它能够把顾客从地点A载到地点B。但是……当GPS没电了或[出错了](http://electronics.howstuffworks.com/gadgets/automotive/gps-system-wrong-direction.htm)，他能够做什么呢？如果两个街道有着同样的名字，该怎么办呢？或许GPS能够标示出来，也可能没有。还有，好的出租车司机知道哪条路更快，在某些时段他将遇到堵车，这是GPS做不到的。

我们经常不会感激在大学里学到的知识，但是它在日常工作中一直默默地帮着我们，就像[游泳和跑步对参赛拳击手的帮助一样](http://www.livestrong.com/article/466645-olympic-boxing-training-methods/)。

如今什么是酷的，那就是你能够[在线免费学习计算机科学](http://blog.agupieware.com/2014/05/online-learning-bachelors-level.html)。

总之，你是想学习计算机科学，还是只学习如何编程，这完全取决于你。我认为最好两者都了解一下。你的观点呢？你将从我的前10项增加或移除某些项吗？



	
  * 注1：二补数（2's complement）是一种用二进制表示有号数的方法，也是一种将数字的正负号变号的方式，常在计算机科学中使用。在中国大陆称作补码，台湾和香港称为二补数。[http://zh.wikipedia.org/wiki/%E4%BA%8C%E8%A3%9C%E6%95%B8](http://zh.wikipedia.org/wiki/%E4%BA%8C%E8%A3%9C%E6%95%B8)

	
  * 注2：IEEE二进制浮点数算术标准（IEEE 754）是20世纪80年代以来最广泛使用的浮点数运算标准，为许多CPU与浮点运算器所采用。这个标准定义了表示浮点数的格式（包括负零-0）与反常值（denormal number）），一些特殊数值（无穷（Inf）与非数值（NaN）），以及这些数值的“浮点数运算符”；它也指明了四种数值舍入规则和五种例外状况（包括例外发生的时机与处理方式）。[http://zh.wikipedia.org/wiki/IEEE_754](http://zh.wikipedia.org/wiki/IEEE_754)

	
  * 注3：图灵机（英语：Turing machine），又称确定型图灵机，是英国数学家阿兰·图灵于1936年提出的一种抽象计算模型，其更抽象的意义为一种数学逻辑机，可以看作等价于任何有限逻辑数学过程的终极强大逻辑机器。[http://zh.wikipedia.org/wiki/%E5%9B%BE%E7%81%B5%E6%9C%BA](http://zh.wikipedia.org/wiki/%E5%9B%BE%E7%81%B5%E6%9C%BA)


