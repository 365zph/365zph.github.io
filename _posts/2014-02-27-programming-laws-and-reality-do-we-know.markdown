---
author: viviworld
comments: true
date: 2014-02-27 00:04:29+00:00
layout: post
link: http://www.labazhou.net/2014/02/programming-laws-and-reality-do-we-know/
slug: programming-laws-and-reality-do-we-know
title: 编程法则和现状：我们明白自认为明白的东西吗？
wordpress_id: 355
categories:
- 编程
- 软件
tags:
- 团队
- 技术债务
---

<blockquote>当面对复杂数据时，编程格言是如何经得起考验的？

软件工程领域的知名专家[Capers Jones](https://en.wikipedia.org/wiki/Capers_Jones)，已经建立了涵盖20,000个项目的范围广泛的项目记录数据库，大部分都是大型的。有了这些数据支持，他经常写文章讨论，哪些活动和方法在实践中发挥着作用，以及如果可能，它们实际上提供多少提升幅度，它们的成本有多少。在这篇客座编辑里，他非正式地评价了一些编程和业务上的流行“法则”在面对软件开发现状时，是如何发挥作用的。</blockquote>




### Boehm第二法则




<blockquote>原型显著减少了需求和设计错误，特别是用户错误。</blockquote>


由[Barry Boehm](https://en.wikipedia.org/wiki/Barry_Boehm)提出的这个法则是有数据支持的。需要说明的是，原型大概占到规划的系统规模的10%。对于1,000个功能点的应用程序，原型大概会有100个功能点，容易构建。对于100,000个功能点的大型应用程序，原型本身会是一个具备10,000个功能点的大型系统。这得出一个结论，如果可能的话，大型系统最好采用增量式开发的方式。


### Brooks的法则




<blockquote>给一个延期的软件项目增加人手会让项目更延期。</blockquote>


[Fred Brooks](https://en.wikipedia.org/wiki/Fred_Brooks)的法则在计算机领域是非常知名的。在一定程度上它有证据支持。应用程序越大，无论怎样，挽救进度延期都要越困难。对于少于五人团队规模的小项目，增加一个有经验的人不会拉长进度，但是增加一个新手就会拉长。对于超过100人团队规模的大型应用程序，这些项目几乎总是由于糟糕的质量控制和变化控制而延期。增加人手会因为培训和复杂的沟通渠道而趋于减缓进度。


### Conway的法则




<blockquote>任何一款软件都会体现生产它的组织结构。</blockquote>


数据趋于支持该法则。需要说明的是，每个软件的组件规模都要考虑匹配被安排这部分工作的团队大小。由于很多团队包含八个人，这就意味着再大的系统或许也要被分解成能够安排给八个人一个部门的组件，这对于应用程序的总体架构可能不是最优的。


### Cunningham的技术债务法则




<blockquote>开发过程中为了节省资金或时间的捷径和草率将导致称之为“技术债务”的后续费用，它或许超过了前期节约的费用。</blockquote>


观察的数据支持这个基本概念，早期的捷径导致昂贵的后续修复。Ward Cunningham的[技术债务概念](http://www.drdobbs.com/architecture-and-design/interview-with-ward-cunningham/240000393)是一个伟大的隐喻，但不是一个伟大的标准。技术债务忽视了由于糟糕的质量而被取消的项目。既然35%的大型项目根本不可能完工，这就是一个严重的疏漏了。这些失败的项目成本巨大，但是技术债务为零，因为他们从来不会发布。技术债务也忽略了诉讼成本和因为糟糕的质量而损失的付款。我在一桩因质量控制引起的诉讼中担任内行的目击者，判给原告的损失是修复本身bug带来的技术债务费用的1,000倍。


### Hartree的法则




<blockquote>软件项目一旦启动，日程安排在完工之前是个常量。</blockquote>


对于缺少规划的、普通或拙劣的项目，观察的数据支持[Douglas Hartree](https://en.wikipedia.org/wiki/Douglas_Hartree)法则。对于使用了早期风险分析的项目，和由有效方法组成的顶级团队，这个法则就不是有效的。换句话说，该法则适用于90%的项目，而不是顶级的10%。


### Jones的编程语言实用性法则




<blockquote>每10年，所有被开发的软件程序中的90%的程序，只用到了 当时可使用的编程语言的10%。</blockquote>


我最初阐述了这个规律。它受1965到2014年数据流的支持。编程语言的流行程度非常短暂，从最初的流行爆发到开始消退貌似平均不超过3.5年的周期。没有人知道这个现象出现的原因。一些语言，比如用在Apple上的Objective C已经持续很多年了。编程语言来来去去的原因不得而知，语言持续的原因也不得而知。


### Jones的软件缺陷排除法则




<blockquote>排除缺陷效率高于95%的项目，比排除缺陷效率低于90%的项目 要更快、更便宜。</blockquote>


来自于20,000个项目的观察数据支持这个法则。只使用测试的项目，通常其缺陷排除效率低于90%，由于拉长测试间隔常常导致延期。同样的项目，在测试之前使用检查和静态分析，其缺陷排除效率能够达到99%，通常按时或提前完成，首先要假定合理的日程规划。糟糕的缺陷排除效率是日程后移的主要原因。


### Lehman/Belady的软件进化法则




<blockquote>软件必须持续更新，否则它的用处变得越来越少。

软件的熵或复杂度随时间而增加。</blockquote>


IBM的[Meir Lehman博士](https://en.wikipedia.org/wiki/Meir_M._Lehman)和[Laszlo Belady博士](https://en.wikipedia.org/wiki/Laszlo_Belady)提出的法则来自于对公司的OS/360操作系统的长期研究。他们已经分别被我确认了。第一个法则直觉上明显，第二个则不然。为了修复bug和小优化而持续进行的修改随着时间的增长而增加循环复杂度，最终增加软件的熵或混乱。做为回报，这将放慢维护工作，或需要额外的维护人员，除非取代或重组发生。软件翻修和重组能够反转熵。


### Senge的法则




<blockquote>越快就越慢。</blockquote>


[Peter Senge](https://en.wikipedia.org/wiki/Peter_Senge)注意到，通常业务企图加快项目提交的进度，却往往放慢了进度。这种现象在软件领域也是如此。当尽量加快项目时，会犯下包括忽视检查和压短测试的一般错误。它们拉长了软件开发，而不是缩短。草率的需求收集和回顾，越过设计直接编码，忽略严重的问题，都会发生意外，进而放慢项目进度。为了优化软件开发进度，质量控制是有价值的，包括测试之前的检查和静态分析。


### Wirth的法则




<blockquote>软件性能变慢的速度 要大于 硬件变快的速度。</blockquote>


在大型机时代，[Niklaus Wirth](https://en.wikipedia.org/wiki/Niklaus_Wirth)提出了这个法则，那时候他好像为大型机工作。然而，对于网络处理器和并行计算，这个法则貌似不太准确。


### Yannis的法则




<blockquote>编程生产力每六年翻倍。</blockquote>


我的数据显示，编程生产力和醉汉走路类似，某种程度上是因为应用程序规模越来越大。然而，如果你砍去需求、设计，只看纯代码工作，这个法则可能更为真实。毫无疑问，Java，Ruby，Go，C#之类的现代语言比汇编和C之类的老语言有着更好的编码性能。主要因素是对于一个已知的应用程序，对于可复用的功能，现代语言需要更少的、独特的代码。

原文地址：[http://www.drdobbs.com/architecture-and-design/programming-laws-and-reality-do-we-know/240166164](http://www.drdobbs.com/architecture-and-design/programming-laws-and-reality-do-we-know/240166164)
