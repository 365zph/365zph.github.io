---
author: viviworld
comments: true
date: 2015-10-01 03:41:51+00:00
excerpt: 这些项目不会给用户提供他们需要的东西。这些用户尝试之后，然后才发现它们的用处让人惊奇。这些项目真正伟大之处，不是因为他们给了用户想要的东西，而是因为他们给了用户所不知道的、却是他们需要的东西。
layout: post
link: http://www.labazhou.net/2015/10/giving-the-users-what-they-want/
slug: giving-the-users-what-they-want
title: 你给了用户想要的吗？
wordpress_id: 2572
categories:
- 编程
tags:
- facebook
- google
- 停机问题
- 可计算性
- 想法
- 爆炸原理
---


	
  * 原文地址（original source）：[https://bitcoinrevolt.wordpress.com/2015/09/30/giving-the-users-what-they-want/](https://bitcoinrevolt.wordpress.com/2015/09/30/giving-the-users-what-they-want/)





* * *



我的一篇文章写了下面这句话：


<blockquote>大部分用户只是说，他们想要「这」。只要他们得到了他们想要的东西，他们就不想听技术方面的东西。</blockquote>


如果编程是一种翻译活动，即把一套程序的、不可执行的用户描述，翻译为可执行的描述，那么很容易就说明，你翻译的准确性是无法证明的。

把一个程序翻译成另一个程序，甚至也是不可能确定其准确程度的。判断两个程序的均等，成了不可判定的问题。这就简化到了一个事实，即[停机问题](https://en.wikipedia.org/wiki/Halting_problem)【注1】是不可判定的。

因此，「只要这是他们想要的」本质上也是不可判定的，因为你不可能证明你的筹划是准确的。「他们知道、且有能力表达清楚他们想要的」，所有这种假设，本身就已经是不可判定的要求了。[你只是猜测，然后做你的事情](http://www.labazhou.net/2015/04/code-is-ux/)，然后他们看你做的结果，他们不会把他们想要的告诉你，而是把他们不想要的告诉你。

换句话说，你的方式有些不切实际，因为没有考虑到被可计算性【注2】所强加给的基本约束。我们对世界的理解充其量不过是图灵完备的【注3】。在这个理解中，[可判断性](https://en.wikipedia.org/wiki/Entscheidungsproblem)【注4】是不可能被解决的。

给用户想要的东西，这种策略是完全不可能的。你充其量只能修复他们不想要的东西。如果你的销售策略建立在这种不可能之上------考虑到[爆炸原理](https://en.wikipedia.org/wiki/Principle_of_explosion)【注5】------你完全不可能达到你心里想要达到的目标。处于这种环境下的、所有形式的预算，都是完全行不通的。你不会去做那些比如你愿意做的事情，因为那是不可能被完成的。

甚至更重要的是，我们领域里的进展从没被预定过，伟大项目从来也不是通过给用户想要的东西来启动的。大部分用户之前从来没有见过 Google 搜索、或 Facebook。因此，这些项目不会给用户提供他们需要的东西。这些用户尝试之后，然后才发现它们的用处让人惊奇。这些项目真正伟大之处，不是因为他们给了用户想要的东西，而是因为他们给了用户所不知道的、却是他们需要的东西。


### 注释

* 注1： 停机问题（英语：halting problem）是逻辑数学中可计算性理论的一个问题。通俗地说，停机问题就是判断任意一个程序是否会在有限的时间之内结束运行的问题。该问题等价于如下的判定问题：给定一个程序P和输入w，程序P在输入w下是否能够最终停止。停机问题在图灵机上是不可判定问题。这是最早提出的决定性问题之一。[https://zh.wikipedia.org/wiki/%E5%81%9C%E6%9C%BA%E9%97%AE%E9%A2%98](https://zh.wikipedia.org/wiki/%E5%81%9C%E6%9C%BA%E9%97%AE%E9%A2%98)
* 注2：在计算机科学中，可计算性理论（Computability theory）作为计算理论的一个分支，研究在不同的计算模型下哪些算法问题能够被解决。相对应的，计算理论的另一块主要内容，计算复杂性理论考虑一个问题怎样才能被有效的解决。[https://zh.wikipedia.org/wiki/%E5%8F%AF%E8%AE%A1%E7%AE%97%E6%80%A7%E7%90%86%E8%AE%BA](https://zh.wikipedia.org/wiki/%E5%8F%AF%E8%AE%A1%E7%AE%97%E6%80%A7%E7%90%86%E8%AE%BA)
* 注3：在可计算性理论里，如果一系列操作数据的规则（如指令集、编程语言、细胞自动机）可以用来模拟单带图灵机，那么它是图灵完备的。这个词源于引入图灵机概念的数学家艾伦·图灵。虽然图灵机会受到存储能力的物理限制，图灵完全性通常指“具有无限存储能力的通用物理机器或编程语言”。[https://zh.wikipedia.org/wiki/%E5%9C%96%E9%9D%88%E5%AE%8C%E5%82%99%E6%80%A7](https://zh.wikipedia.org/wiki/%E5%9C%96%E9%9D%88%E5%AE%8C%E5%82%99%E6%80%A7)
* 注4：一个语言L，是一个集合，且其补集为\bar{L} 。当L是图灵机可识别时，语言L则称为半可判定。当语言L不是图灵机可识别，则为不可判定语言。当且仅当L和\bar{L}都是图灵机可识别的时候，L才能称为可判定语言。[https://zh.wikipedia.org/wiki/%E5%8F%AF%E5%88%A4%E5%AE%9A%E6%80%A7](https://zh.wikipedia.org/wiki/%E5%8F%AF%E5%88%A4%E5%AE%9A%E6%80%A7)
* 注5：爆炸原理，也叫做“Ex falso quodlibet”或“ex contradictione (sequitur) quodlibet”，是经典逻辑中陈述从矛盾中可以得出任何事物的规则。用更加形式化的术语，从形如 P ∧ ¬P 的任何命题，可以推导出任何任意的 A。 “爆炸”指称接受一个单一的矛盾到一个系统中会导致整体定理的“爆炸”。[https://zh.wikipedia.org/wiki/%E7%88%86%E7%82%B8%E5%8E%9F%E7%90%86](https://zh.wikipedia.org/wiki/%E7%88%86%E7%82%B8%E5%8E%9F%E7%90%86)
