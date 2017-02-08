---
author: viviworld
comments: true
date: 2014-11-11 13:45:42+00:00
layout: post
link: http://www.labazhou.net/2014/11/the-cost-of-features/
slug: the-cost-of-features
title: 特性的代价
wordpress_id: 1308
categories:
- 杂项
- 软件
tags:
- Ag
- cassandra
- dash
- firefox
- ie
- nodejs
- unix哲学
---

忠告：这是一个汽车的类推。

下图展示了几款车型过去数年的重量变化：

[![几种汽车车型的车身重量逐年变化图](http://www.labazhou.net/wp-content/uploads/2014/11/car-weights.png)](http://www.labazhou.net/wp-content/uploads/2014/11/car-weights.png)

这么多年，这些汽车重量就高了不少。这种趋势不仅仅体现在汽车上。波音737-100在1968年首航时、不载人的重量有30吨，一架现在的737-900却有44吨，甚至战斗机重量也增加了。喷火战斗机（Spitfire）MkIA【注4】空载1,953kg，七年后，[Mk24重量达到3,247kg](http://en.wikipedia.org/wiki/Supermarine_Spitfire_variants:_specifications,_performance_and_armament#Dimensions.2C_performance_and_armament)。

重量增加是一件坏事吗？通常不是。设计师不会无理由地增加重量。汽车比过去更加安全，它们更加舒适，有更多的特性：空调、助力转向、自动变速器、气囊。同样，一架现代737在运送更多乘客和货物的同时，可以飞得更远。更重的喷火战斗机因为拥有更大的发动机，可以携带更多的武器和燃油。这是一项交易：特性越多，所以重量越大。

为什么我在讨论机身和汽车呢？

下面这些图展示了某些流行开源项目的[代码行数](http://en.wikipedia.org/wiki/Source_lines_of_code)。先看[httpd](http://httpd.apache.org/)：

[![httpd代码行数逐年变化图](http://www.labazhou.net/wp-content/uploads/2014/11/httpd-lines-of-code.png)](http://www.labazhou.net/wp-content/uploads/2014/11/httpd-lines-of-code.png)

[Node.js](http://nodejs.org/)（稍微有点不同）

[![node.js代码行数逐年变化图](http://www.labazhou.net/wp-content/uploads/2014/11/node-js-lines-of-code.png)](http://www.labazhou.net/wp-content/uploads/2014/11/node-js-lines-of-code.png)

[Cassandra](http://cassandra.apache.org/)：

[![cassandra代码行数逐年变化图](http://www.labazhou.net/wp-content/uploads/2014/11/cassandra-lines-of-code.png)](http://www.labazhou.net/wp-content/uploads/2014/11/cassandra-lines-of-code.png)

这些例子不是故意挑选出来的，我在其它项目上算了算，发现它们都占用了大量空间，并增加了页面载入时间。数据相当清晰了：[软件项目](http://www.labazhou.net/category/software/)在随着时间的进行而变大。这不应当让很多开发人员感到吃惊。Zawinskin's Law数个世纪前就被创立了。

但是，为什么汽车、机身和软件在增加呀？我们应当天真地期待它们当中至少有一些随着时间而收缩。

我不知道答案，不过我的确有一些臆测。工程学参与了交易。其它所有条件相同的情况下，代码越多，意味着bug越多。当然，其它所有条件是不同的。特性越多，意味着代码越多。通过复杂缓存层次化、索引和有效率的数据结构提高性能，就需要更多的代码。让软件可靠、分布式、可伸缩将产生海量代码。直到最近，网页上的圆角效果所需要的代码数量还是怪里怪气的。

因此我们有增加代码的正当理由了，不过，这不足以引起软件膨胀。当我们随着时间的进行添加代码的时候，通过移除足够多的代码来阻止膨胀。我们为什么不那样做呢？一些理由涌上心头：



	
  * **损害依赖它的软件**。要移除的特性可能不受用户欢迎，而其它软件或许依赖于它。

	
  * **不满意的用户**。移除只有1%用户的特性，肯定要招致不满邮件潮水般地涌来。10,000个用户意味着100封愤怒的邮件，同时，它让其他99%用户的疑惑，他们的宠物特性是不是接下来要移除的。

	
  * **移除代码没有意思**。如果你的代码是整洁的，那么它也是琐碎无聊的。如果你的代码丑陋不堪，那么它就是巨大的伤痛。不管怎样，开发新东西更有趣。

	
  * **给同事的印象不够深刻**。“我移除了一些旧代码”很少能够站起来带着自豪感说出来。人们不喜欢吹嘘移除特性或旧代码。


因此移除代码是一项艰巨的任务。但是我们该怎样阻止软件项目被它们自己的体积压垮呢？我能给出的最佳答案就是：你阻止不了。只要你敲入git init，你就输了战争。为什么？

我们再看看汽车，汽车公司在设计汽车方面有巨大的预算，但是他们不会减少重量，他们有不同的战略：随着一种车型在重量、功能和价格上的增加，厂商就可以引进更小的车型。本田思域（Civic）是本田在美国市场最小的汽车。十年前，他们引入了飞度（Fit）。大众的Polo代替了旧Golf的角色。

类似的过程也在软件上发生着。随着一款软件越来越复杂和膨胀，较新的项目将取代老款软件。Firefox取代了Netscape和Internet Explorer。在Debian和Ubuntu里，[dash](http://en.wikipedia.org/wiki/Debian_Almquist_shell)取代了[bash](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29)。Nginx、Node.js和其它软件正在吞噬httpd的领地。

我上面说过，工程学参与了交易：代码多是因为特性、性能和可伸缩性。如果朝相反方向做同样的交易，会怎么样？回到汽车：如果你为了降低重量而移除了特性，你会得到什么？甚至符合现代排放和安全要求，开发一款与30年前小型汽车同等重量的汽车也是可能的，结果就是[路特斯Elise](http://en.wikipedia.org/wiki/Lotus_Elise)（Lotus Elise）【注1】。它并不适合每个人，但它绝对是汽车行业壮举。

有没有遵循同样模式的[软件项目](http://www.labazhou.net/category/software/)呢？人们使用现代语言、资源库和技术开发过只做好一件事的一款小众软件吗？那就是Unix哲学【注2】，但是当我试图举例的时候，却想不了太多。甚至[Ag](https://github.com/ggreer/the_silver_searcher)【注3】已经开始吸收了更多功能（尽管如此，这仍然没有让它变慢）。

本文太长了，我没有任何主要结论能总结出来，因此我就写到这里。我这是失礼的举动，不过它没有发布在《纽约人》上。顺便提醒一下：这篇结构混乱的文章甚至和科学都靠不上。我将钻研深挖这个话题，不过我最近在忙于[工作](https://floobits.com/)。乐观地讲，我从来没有这么富有成效，请看我的[GitHub的状态图](http://geoff.greer.fm/images/Screen%20Shot%202013-03-05%20at%205.26.38%20PM.png)。



	
  * 原文地址：[http://geoff.greer.fm/2013/03/06/the-cost-of-features/](http://geoff.greer.fm/2013/03/06/the-cost-of-features/)

	
  * 注1：莲花汽车是一家以制造性能跑车为主的小厂家。所以这些汽车就必须要有自己的特色。由于莲花历年来的坚持，莲花所生产的汽车有着一个最重要的特征，就是在保证最高的驾驶乐趣前提之下，取消一切舒适性装备，这其中包括助力设备（例如转向助力，油门、刹车、离合器踏板的助力）。还有一点就是莲花坚持自己的汽车就是赛车，所以一切性能指标都是围绕着赛道进行的。这样就有最最坚硬的悬挂，最最吃力的转向系统，最最沉重的踏板，以及最最不舒适的驾乘体验。（对于普通消费者来说是这样）有一位杂志记者在试驾过莲花汽车几分钟之后，就因为手上无力而退出测试。

	
  * 注2：Unix哲学是一套基于Unix操作系统顶级开发者们的经验提出的软件开发的准则和哲学。[http://zh.wikipedia.org/wiki/Unix哲学](http://zh.wikipedia.org/wiki/Unix哲学)

	
  * 注3：一种与ack类似的代码搜索工具，更关注于速度。

	
  * 注4：《喷火传奇》[http://www.afwing.com/intro/spitfire/1.htm](http://www.afwing.com/intro/spitfire/1.htm)


