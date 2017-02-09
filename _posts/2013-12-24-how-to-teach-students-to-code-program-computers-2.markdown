---
author: viviworld
comments: true
date: 2013-12-24 13:03:38+00:00
layout: post
link: http://www.labazhou.net/2013/12/how-to-teach-students-to-code-program-computers-2/
slug: how-to-teach-students-to-code-program-computers-2
title: 如何廉价地教学生编程（二）
wordpress_id: 40
categories:
- 编程
tags:
- basic
- Commodore
- 编程
- 高级语言
---

这些电脑上的BASIC比较简单，一般情况下很多老师能够学会再教。这并不是让学生为编写现代的app，这样做只是为了做得更好。他们会更开心地敲代码，教核心逻辑技能等等。对于commodore 64，电脑的架构有很好的文档。学得快的学生就可以学习机器语言编程的概念、RAM和ROM工作原理等知识。我借助Richard Mansfield的书学习6502机器语言的《面向初学者的机器语言》（[http://www.amazon.com/Machine-Language-Beginners-Richard-Mansfield/dp/0942386116](http://www.amazon.com/Machine-Language-Beginners-Richard-Mansfield/dp/0942386116)）

理解位、字节、机器指令、ram和rom等概念至关重要，有助于领悟高级编程语言。是的，长期来看，语言底层的经验能够培养出更好的程序员。实际上，甚至今天廉价的嵌入式设备还在使用一些来自于机器语言编程中的准则。

除了动辄数百美元的现代电脑，这些低成本的老式电脑能够提供极好的学习体验。或许你也教电子学。它们能够方便地与各种DIY的项目集成。因特网增强了它们，它们便宜，你可以让学生拆开来看看它们的组成。

由于老式BASIC解释器简单且缺乏许多现代语言结构，语言的关键部分能够移入到基于BASIC的某些现代语言中。网上有很多BASIC编译器，有免费的（像FreeBasic），有转换成C的（像BCX），还有独立的专业级编译器（PowerBasic）。你不认为BASIC现在还活得好好吗？

考虑个例子。看视频：[http://www.youtube.com/watch?v=D9fvdfE59_Y](http://www.youtube.com/watch?v=D9fvdfE59_Y)

在视频的4分33秒处暂停，留意那台便携式电脑上运行的、控制Chevrons令人惊奇的水下深水管道设备（ROV）软件是什么，它就是用PowerBasic写的（我自己的GUI引擎也是用PowerBasic build的）。

我在80年代从Commodore 64（TI/99）电脑学到的东西使我今天准备好了编写现代软件。除了Basic（比如机器语言），这些电脑上的低级编程使我打下了编写现代软件的基础，我用这些基础技能仅仅需要最低硬件配置就可以写出高效运行的软件。我甚至用Commodore 64（Abacus Basic编译器）初次体验了编译器的用法，还用Abacus编译器写出了我自己的Commodore下的编译器，因此我写了一个适合家庭玩的视频游戏并卖给了Compute Gazette杂志，从中挣了1500美元。

就个人而言，我认为年轻人从80年代的电脑学到的东西要比今天一般以游戏等环境来教编程的某些软件学到的多些。计算机动画和图像是复杂的工程，如果一个学生使用拖拽对象、辅以几行伪代码就ok的游戏软件包，然后他们就会认为编程是简单的，只需做很少的工作就可以完成有价值的事情。如果让学生体验Commodore 64，起初他们不会对一个简单的 PRINT “Hello”留下多深的印象，但是给时间让他们学习其原理，当他们搞清楚了这些古怪的事情，并能做一些图像，那么他们才能学到有价值的东西。

编码就是学习电脑如何把人们的命令翻译成机器命令，如何完成任务。理解图像显示器如何呈现像素、花费多少时间等简单的概念，有助于更好地认识CPU（或GPU）要做的任务以及程序员的代码究竟怎样被影响着。我今天仍然受益于早些年从Commodore 64得来的经验，我写了一些软件，比如一个低级的2D sprite引擎，一个使用OpenGL和DIBs协同的的3D图像引擎，编写图像过滤等等。和大多数使用高级编程语言的开发者不同，我是一名资深的WIN32 API程序员。就像我过去在Commodore 64经历的一样，今天我仍然接触较低级别的计算机操作系统以便于了解其威力和速度。的确如此，我从老式的Commodore 64收获良多。

木工学习班的初学者从手工工具、而不是高级工具起步，编程也这样，学生从80年代的老式家用电脑起步，可以更好地掌握电脑是如何工作的。像我这样经过那个时代训练的程序员，对于有限的硬件觉得十分正常。Atom处理器、1或2G内存对我们而言是强大无比的。今天很多程序员如果没有超强的icore处理器、或者8G、16G的内存会感到不自在。过去的程序员知道如何用最少的资源获得最大的产出。因此教学生在老式的Commodore 64上编程能够带来一些有益的知识。考虑一下，今天的典型PC有着至少1Ghz甚至更大的CPU，1Ghz是1000Mhz，Commodore 64 CPU只有1Mhz，是现代CPU的千分之一。实际上它更低，因为现代CPU有各种各样让它们更快运行的附加特性。

令人惊奇的是，一个优秀的开发团队研发了一款名叫“Geos”的、运行在Commodore 64上的GUI操作系统。Commodore 64只有64K的内存、1Mhz的CPU，却可以运行一个GUI环境。是的，编程的真正挑战是学习如何推动硬件远远超出电脑生产商所能想到的。今天很多公司受益的就是这种编程技能。

  


原文地址：[http://www.codeproject.com/Articles/699452/How-to-Teach-Students-to-Code-Program-Computers](http://www.codeproject.com/Articles/699452/How-to-Teach-Students-to-Code-Program-Computers)
