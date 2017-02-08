---
author: viviworld
comments: true
date: 2015-01-06 02:31:44+00:00
layout: post
link: http://www.labazhou.net/2015/01/write-you-a-haskell/
slug: write-you-a-haskell
title: 编写属于自己的Haskell
wordpress_id: 1493
categories:
- 编程
tags:
- Haskell
- 写作
- 函数式
- 编译器
---

原文地址（source）：[http://dev.stephendiehl.com/fun/](http://dev.stephendiehl.com/fun/)

在2014年，我写了一篇短教程，是关于用Haskell开发一种可以编译成LLVM的、小型命令式语言。我对于教程貌似取得的效果感到非常开心，从那么多人那里得到的热烈反响让我深受鼓励。

我在2015年能够写什么样的最有影响力的主题，对此做了深入思考；决定在今年继续努力，完成另一个基于项目的《根据首要原则开发一种简单的函数式编程原则》。

这是一个不平凡的主题，不幸的是，它没有得到太多重视，开发这种现代函数式语言的知识，没有在很多程序员中得到扩散。可获得的资源常常在讨论高深的理论，而完全掩盖了工程细节（engineering details）。我想写一个基于项目的、涵盖工程细节的教程，在最后给读者留下一个功能齐全的玩具语言，它可以扩展到其它项目。

我们[将开发一种名叫“Fun”的小型函数式语言](http://www.labazhou.net/2014/11/how-to-write-a-simple-interpreter-in-javascript/)，这是局部的Haskell 2010玩具语言；支持：分析器、类型引用、数据类型、模式匹配、脱糖（desugaring）、typeclass【注1】、高阶类型(higher-kinded type)、monadic IO【注2】、任意阶多态性、record、Core language、STG中间语言、惰性求值、解释器、内置代码生成器、运行时和optimization passes。

相对于我的大部分作品，本教程是预先编辑的、粗糙删减的版本，我一直在完善。编译器本身截止2014年12月份也是完整的，但是每一章（共28章）都是逐月完成的，这样我就能[根据读者和测试人员的反馈逐步完善文字](http://www.labazhou.net/2014/10/living-the-future-of-technical-writing/)。关于运行时和代码生成的后面几个章节多少有些复杂、篇幅较长。

（译者注：下面是教程，有兴趣的可以学习~）



	
  * 注1：In computer science, a type class is a type system construct that supports ad hoc polymorphism. [http://en.wikipedia.org/wiki/Type_class](http://en.wikipedia.org/wiki/Type_class)

	
  * 注2：为了引入 IO 操作，各种函数式语言八仙过海各显神通。Monad 就是 Haskell 给出的方案。并且 Monad 并不仅仅是 IO 操作的抽象，它更是多种类似操作之间共性的抽象。[http://zhuoqiang.me/what-is-monad.html](http://zhuoqiang.me/what-is-monad.html)

	
  * 注3：惰性求值（Lazy Evaluation），又称惰性计算、懒惰求值，是一个计算机编程中的一个概念，它的目的是要最小化计算机要做的工作。[http://zh.wikipedia.org/zh-cn/惰性求值](http://zh.wikipedia.org/zh-cn/惰性求值)


