---
author: viviworld
comments: true
date: 2014-11-20 11:41:16+00:00
layout: post
link: http://www.labazhou.net/2014/11/how-to-choose-a-teaching-language/
slug: how-to-choose-a-teaching-language
title: 如何选择教学语言
wordpress_id: 1345
categories:
- 编程
- 职业
tags:
- java
- ML语言
- OCaml
- python
- Scheme
- SICP
- λ演算
---

如果你正在[教授编程课](http://www.labazhou.net/2013/12/how-to-teach-students-to-code-program-computers/)，你该用哪种语言呢？

我喜欢这个问题，因为它有很多不错的答案，彼此存在很大差异，不同的方法对于编程的理解有着不同的思考。

我在普林斯顿大学上的第一堂正式的编程课是[COS 217](http://www.cs.princeton.edu/courses/archive/fall13/cos217/)，由优秀老师[Anne Rogers](https://cs.uchicago.edu/people/amr)讲解（当时我觉得是可怕的）。这个课程采用C语言，这门课的聪明之处在于从机器开始。我们不只是学习C，还学到了用来编程的机器是如何运行的。我就是在这里首次接触到了指令计数器、堆栈帧、寄存器和分级存储，太让人振奋了。

C鼓励你从机器开始，而Scheme【注1】想让你从计算的数学基础开始。你不需要理解λ演算【注2】，这得益于Scheme的简洁核心，你可以在此之上构建丰富多彩的计算世界。其核心具有表现力，足以引入多种不同的语言，包括函数式语言与命令式语言、面向对象语言和逻辑程序设计。

经典课程是[MIT的6.001](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/)，也就是熟知的SICP，计算机程序的构造和解释。悲剧的是，这节课在MIT网站已经下线了，但是[这本书](https://mitpress.mit.edu/sicp/full-text/book/book.html)还有，即使你多年前已经完成了最后的计算机科学课程，它还是值得一读的。

MIT用基于Python的课程取代了SICP，这体现了一种较广的趋势。根据Philip Guo的一项非正式[研究](http://cacm.acm.org/blogs/blog-cacm/176450-python-is-now-the-most-popular-introductory-teaching-language-at-top-us-universities/fulltext)所强调的，很多学校现在教授Python，尤其是针对早期的入门课程。我对这个选择有着复杂的感受。Python是一门非常友好的语言，但是这种友好性也附带了一些问题。

在一定程度上我觉得是比较明显的，根据我的面试经历，应聘学生选择编码的语言就是Python。在很多场合，Python是理想的面试语言，因其简洁、可读性强的语法，在空间有限的白板上写代码，是完全可以接受的。不过我看到了，学习Python的学生经常搞不清楚这门语言的、相当粗略的语义模型。大量用Python编程的部分学生不能猜到Python的列表（list）是如何被实现的，更不要说他们有能力解释生成器或装饰器之类的、语言特性的语义了。

这里真的不是说Python不好。毕竟，存在一些伟大的工具，你可以完全不用理解其工作原理就可以把工作搞定。但是用不同的方式，Scheme和C鼓励你从底层理解发生了什么，某种教学的力量就存在于此。总之，对于早期的入门课程，特别是对于那些不打算最终成为计算机科学家或全职程序员的人来说，我认为Python是一个不错的选择。但是，对于这种情况之外使用Python，我是持保留态度的。

就个人而言， 我感到想当被鼓励的一个进展就是静态类型语言的出现，特别是ML语言【注3】做为教学语言。在过去的几年，我非常荣幸地访问了布朗大学、康奈尔大学、宾夕法尼亚大学、卡内基梅隆大学和哈佛等学校，并发表[演讲](https://blogs.janestreet.com/effective-ml-video/)，这些学校使用Ocaml和Standard ML两种方言。

ML语言已经具备了优秀理由的基础。首先，它分享了很多Scheme优雅的编程思想，即使它的核心不像Scheme那样有着迷人的简约。但是ML比Scheme有更广的延伸，因为你可以向学生展示编程里的类型化角色。尽管有着更广的延伸，[OCaml](http://ocaml.org/learn/teaching-ocaml.html)和SML属于相对简单的语言，用于教学而不是日常应用，才是最重要的。

我看到很多语言上的选择，唯一不能让我自己接受的是Java。当然，Java是广泛使用的业内语言，但不代表它就是一门优秀的教学语言。在我看来，教学语言的关键要素是简洁，我刚才提到的所有其它选择都有着某种方式的简洁：C是机器之上的最少的层；Scheme和ML是基于计算的简单数学模型；Python是易于使用的语言。

从各种角度说，Java都不简洁。尤其不容易入门，你需要告诉学生，所有细节可以忽略而不是理解。（是的，public static void main，我看到了！）它没有C的简单、透明的执行模式。像Scheme和ML核心的、优雅计算机核心演算，是根本看不到的。我能看到Java的唯一真正优势在于好找工作，好像对我来说还不能算足够的论据。

当你考虑挑选一门教学语言时，你不只是为学生挑选一些在课堂上编程的指令。你正在挑选一种智力上的思想，学生将从中看到你教给他们的所有经验。你应该认真地找到这个思想。



	
  * 原文地址：[https://blogs.janestreet.com/how-to-choose-a-teaching-language/](https://blogs.janestreet.com/how-to-choose-a-teaching-language/)

	
  * 注1：Scheme是一种函数式编程语言，是Lisp的两种主要方言之一（另一种为Common Lisp）。不同于Common Lisp，Scheme遵循极简主义哲学，以一个小型语言核心作为标准，加上各种强力语言工具（语法糖）来扩展语言本身。[http://zh.wikipedia.org/wiki/Scheme](http://zh.wikipedia.org/wiki/Scheme)

	
  * 注2：λ演算（英语：lambda calculus，λ-calculus）是一套用于研究函数定义、函数应用和递归的形式系统。[http://zh.wikipedia.org/wiki/Λ演算](http://zh.wikipedia.org/wiki/Λ演算)

	
  * 注3：ML 是一个通用的函数式编程语言，它是由爱丁堡大学的Robin Milner及他人在二十世纪七十年代晚期开发的。今天在ML家族中有好几种语言：两种主要的方言是Standard ML和Caml，其他的包括F# － 针对Microsoft .NET平台的开放研究项目。 ML中的思想影响了众多的语言，例如Haskell，Cyclone和Nemerle。[http://zh.wikipedia.org/wiki/ML语言](http://zh.wikipedia.org/wiki/ML语言)


