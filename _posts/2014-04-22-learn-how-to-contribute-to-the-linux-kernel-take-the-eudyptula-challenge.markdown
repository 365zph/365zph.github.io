---
author: viviworld
comments: true
date: 2014-04-22 01:39:33+00:00
layout: post
link: http://www.labazhou.net/2014/04/learn-how-to-contribute-to-the-linux-kernel-take-the-eudyptula-challenge/
slug: learn-how-to-contribute-to-the-linux-kernel-take-the-eudyptula-challenge
title: 学习如何向Linux内核贡献代码，接受Eudyptula挑战
wordpress_id: 592
categories:
- 编程
tags:
- email
- Eudyptula
- linux
- 内核
---

[![Little Penguin（小企鹅），Linux内核](http://www.labazhou.net/wp-content/uploads/2014/04/Little-Blue-Penguin-_Eudyptula-minor_-Adelaide_Zoo.jpg)](http://www.labazhou.net/wp-content/uploads/2014/04/Little-Blue-Penguin-_Eudyptula-minor_-Adelaide_Zoo.jpg)

如果你想为Linux内核贡献代码、但不确定从哪里开始，Eudyptula挑战会是检验你编程技能和学习如何参与内核社区的一种伟大的方法。

该挑战大约一个月前出现在线上[http://eudyptula-challenge.org/](http://eudyptula-challenge.org/)，由一个匿名黑客（或黑客们）创办，以Little Penguin（小企鹅）【注1】命名，为了让更多开发者参与到Linux内核。它是模仿Matasano Crypto Challenge建立的------集中48小时的练习，培训参与者密码系统如何建立以及如何被攻击。而Eudyptula挑战不是一个教程，小企鹅说，但是通过完成该挑战你就可以较好地了解整个内核贡献过程的运转情况。

挑战参与者通过给[Little](mailto:little@eudyptula-challenge.org)发送电子邮件来报名，他会给参与者发送一系列由Linux内核开发者派发的编程任务。参与者一次收到一个任务，且必须在小企鹅发送下一个任务之前完成。该挑战没有获胜者，不过那些成功完成挑战的、所有20个任务的参与者就会成为Linux内核贡献者。

我们最近通过与小企鹅的邮件沟通对该挑战有了更多的了解。你能够在http://eudyptula-challenge.org/给小企鹅发送一封（非HTML）邮件来报名。

**Eudyptula挑战是什么？**

Eudyptula挑战是面向Linux内核的一系列的编程练习。这些练习从一个非常简单的“Hello World”内核模块开始，逐步增加复杂程度。

**你为什么发明了这个挑战？**

有一次喝了一整夜的酒，冒出了一个想法。如果Linux内核要生存的话，它需要新的程序员来修复一整夜的豪饮后、所新增加的所有bug。

**什么时候开始，持续多长时间？**

你可以在任何时候开始。只需根据网站上关于如何加入的操作说明，你的任务就会发送过来。目前有20个不同的任务要完成。如果你全部完成了，一组新的任务眼下正为了满足已经完成挑战的人，他们要求的也越多。

**每一步都是通过电子邮件吗？没有一个可用的web表单？**

是的，内核开发都是通过电子邮件运作的，因此安装一个邮件客户端来正确地发送Linux内核补丁是所有内核开发者需要学习的技能。还有，提交补丁、代码以及通过电子邮件对review做出响应的来来回回的过程，就真真切切地发生在所有内核开发者身上。这个挑战尽可能接近地复制Linux内核开发体验。

**谁应当参加挑战？**

对与Linux内核相关的、一组不同任务的编程感兴趣的每一个人。

**在我参与之前我需要掌握什么？**

为了参与，你需要对C有深入的了解。这个挑战不是一个教程，没有如何完成任务的提示，也没有去哪里找到更多信息的指南，它需要你自己的大量投入。

**如果我完全是Linux内核开发新手，该挑战将教会我如何贡献吗？**

是的，大量任务是关于获取 应用到Linux内核树本身的 补丁。挑战结束后，你将具备如何向内核贡献代码的技能和理解。

**有获胜者吗？我如何才能完成？**

没有“获胜者”，因为没有定时突然出现的一堆任务。很多人已经完成了当前的任务组，新人正在每天报名参加。

据说Linux基金会可能为每一个完成挑战的人准备了一个“奖品”。只有你不得不完成挑战才能自己发现奖品是什么。

**完成该挑战 意味着 我有资格成为一名内核维护人员吗？**

你将有资格指出你喜爱的维护人员引起的、与内核开发相关的任何问题。那通常比作为一名内核子系统维护人员要有趣得多。

**这会让我的简历更有竞争力吗？它有助于找工作？**

它不会伤害你的简历，但是我怀疑有人知道这是什么。为了找工作，外面有很多Linux内核开发者的工作，如果你完成了所有这些任务，没有理由你不能轻松找到一个全职工作。

**为什么你认为已经看到了该挑战的强烈反响？我们听说你已经有2,000个参与者了。**

这个挑战产生了大量反响，远远超出了我的想象。目前有超过2,400个人在参与挑战，每天还有更多的报名。

很多时候，人们只是在涉及内核编程时，他们不知道想做什么。这种类型的任务强迫他们在内核源代码树里的大量不同地方探索。没有一个特定的任务，大多数人不会去研究内核的这些区域是如何运行的。

**我还听说一个大学编程小组组织了一个黑客节日，他们的会员在周末要接受挑战，这是怎么回事？**

该挑战仍然以个体为基础，因此大学小组忙着他们自己的任务。他们有一个10人小组，在同样的地点工作。没有开发者能够在一个周末完成所有的任务，但是看起来他们在试图这样做时度过了一段快乐时光。

原文地址：[http://www.linux.com/news/featured-blogs/200-libby-clark/770112-learn-how-to-contribute-to-the-linux-kernel-take-the-eudyptula-challenge](http://www.linux.com/news/featured-blogs/200-libby-clark/770112-learn-how-to-contribute-to-the-linux-kernel-take-the-eudyptula-challenge)
注1：[http://zh.wikipedia.org/wiki/小蓝企鹅](http://zh.wikipedia.org/wiki/小蓝企鹅)
