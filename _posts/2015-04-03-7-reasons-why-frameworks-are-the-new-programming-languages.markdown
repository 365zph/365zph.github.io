---
author: viviworld
comments: true
date: 2015-04-03 07:01:45+00:00
layout: post
link: http://www.labazhou.net/2015/04/7-reasons-why-frameworks-are-the-new-programming-languages/
slug: 7-reasons-why-frameworks-are-the-new-programming-languages
title: 框架成为新的编程语言的 7 种理由
wordpress_id: 1813
categories:
- 编程
tags:
- api
- bug
- GUI
- IDE
- javascript
- 框架
- 视觉化语言
---


	
  * 原文地址（original source）：[http://www.infoworld.com/article/2902242/application-development/7-reasons-why-frameworks-are-the-new-programming-languages.html](http://www.infoworld.com/article/2902242/application-development/7-reasons-why-frameworks-are-the-new-programming-languages.html)

	
  * 作者（author）：[https://twitter.com/peterwayner](https://twitter.com/peterwayner)





* * *





<blockquote>感谢强大的工具、对速度的需求、和编程本身的变迁，下一次乏味的战争将终结于框架 API、而非语法。</blockquote>


在 1980 年代，掀起一场乏味战争的最简单方法，就是赞扬你钟爱的编程语言是最棒的。C、Pascal、Lisp、Fortran？程序员们花费数个小时来详细解释关于精巧制作一条 if-then-else 语句的特定方式为什么优于你的方式。

那是过去的事情了。今天，涉及语法和结构的战争基本结束了，因为世界已经汇总了一些简单标准。在 C、Java 和 JavaScript 里，分号、花括号等之间的差异不大。关于类型和闭包的有趣争论仍然存在，但是大部分是毫无意义的，因为自动化在缩小差距。如果你不想定义数据类型，那么有一种可能，计算机将能准确推断出你的意思。如果你的老板想用 JavaScript、而你喜欢 Java，那么交叉编译器【注1】将把所有静态类型的 Java 代码转化成可以在浏览器运行的最小化的 JavaScript。当技术做后盾时，为什么还有战争呢？

今天，有趣的战斗发生在框架上。当我在约翰·霍普金斯大学和其他院系成员规划一门新课程时，[框架成了讨论的重点](http://www.labazhou.net/2014/03/why-source-code-is-a-must/)。Angular 优于 Ember？Node.js 就是一切吗？

我们设计了一份调查课程，将探索最重要的软件包的架构，这是互联网的基础。这是行动的中心，这份调查课程的价值在于探索围绕着当今互联网的、最重要的软件包的架构。

从这个意义上说，框架就是新的编程语言。它们就是当代代码被建立起来的最新思想、哲学和实用性。有些昙花一现，不过大部分成为了编程的、新的基本构成要素。下面是助长这种框架趋势的七个方面，使得框架成为滋生乏味战争的新的最爱。


### 大部分代码正和 API 串在了一起


过去编写软件，意味着调用你对编程语言的所有技能，以最大化压榨代码。掌握指针、函数和作用域是讲得通的------代码质量取决于做正确的事情。如今自动化处理了这方面的大多数事情。如果你在代码里遗留了无用的语句，不要担心，编译器会去掉无用代码。如果你让指针吊着，垃圾回收器可能会找到它。

还有，如今编码实践也不同了。大部分代码现在都是一长串 API 调用。偶尔有一些 API 调用之间的数据重组，但是，甚至这些工作通常也有其它 API 来完成。幸运的一些人在为我们机器的核心编写更聪明的、位拆裂【注2】、指针杂耍之类的代码，但是我们大部分人工作于更高的层次。我们在 API 之间简单地运行管道。

鉴于此，理解 API 的表现以及能做什么，就显得更加重要。它接受哪种数据结构？当数据集增长较大时，算法表现如何？类似这样的问题，与关于语法或语言的问题比起来，更加集中在今天的编程里。的确，有大量工具简化了某种语言从另一种语言调用一个程序。比如，把 C 资源库 链接到 Java 代码，变得相应简单了。理解 API 才是重要的。


### 站在巨人的肩膀上，是值得的


假设你已经成为了 Erlang 或另一种新语言的信徒。你认为，它为编写文档、没有 bug 的应用提供了最好的平台。这是优秀的观点，但是你要花费数年才能把可获得的 Java 或 PHP 重写为你最新选择的语言。你的代码最终可以显著变得更好，但是值得花这些额外的时间吗？

框架让我们对来到我们面前的那些艰难工作做出了改变。我们或许不喜欢他们选择的架构，我们或许争论于实现细节，但是停止抱怨、找到和差异共存的方式才是更有效的。继承框架代码库里的所有精华和糟粕，是如此地容易。用你喜欢的新语言、自己编写所有东西，而不采用某种更受欢迎的框架，这种强悍的方式和简单地遵循框架作者及其 API 比起来，不会让你快速享受到新选择的乐趣。


### 理解架构是做什么的，而非语法


由于大部分编码都是串起 API 调用，因此没有太多优势去学习语言的特质了。当然，你可以成为关于 Java 是如何初始化对象内的静态字段的专家，但是如果能够搞清楚如何发挥 Lucence、JavaDB 或其它一堆代码的威力，那才是更好的。为了深入理解 Objective-C 编译器的优化程序，你要花费数月，但是学习最新的 Apple 核心资源库的来龙去脉，你将真正让代码优秀。你将更深入地学习框架吹毛求疵的细节，而不是框架所依托的语言的语法。

我们的大部分代码在资源库的内部循环中花费了大量时间。搞清楚语言细节的正确性可以起到帮助，但是了解资源库内部发生了什么可以获得显著的回报。


### 算法主导


学习一门语言有助于你应付隐藏在变量里的数据，不过只是把你带到了更远的地方。真正要克服的是，确保算法正确，它们通常被框架定义和实现了。

很多程序员明白，重新实现标准算法和数据结构是危险的，也是浪费时间的。你可能让它更符合需求，但是你要冒着犯微妙错误的风险。框架已经广泛测试过多年了。它们代表了软件基础设施的集体投资。当弄明白“go off the grid”【注3】是什么意思时，将其他人的辛苦劳动扔在一边，用你自己的双手搭建一个算法小屋------其实，没有太多这种例子。

正确的做法是学习框架，学习如何使用它们来发挥你的最大优势。如果你选择了错误的数据结构，那么你就把一个线性工作变成了耗时的、输入大小的二次函数。一旦你这样做了，将是一个大麻烦。


### 纠正语法的编译器和聪明的 IDE


我应该在代码块的最后一个语句后面加上分号吗？分号是“分隔符”，还是“终止符”？语言设计者们花了大量时间来制作实施这些规则的分析器------猜猜怎样------我不关心。我关心的时候大概是在10年前，但是现在的 IDE 为我做了这部分工作。它们一直在身后看着我，当我搞砸的时候就告诉我。我让它们替我去考虑，把时间花在考虑关于代码方面的大问题。IDE 是苦力、是处理这些琐碎细节的编程助理。

自动化已经把我们从编程语法的单调乏味中拯救了。当然，它们不能为我们做所有工作。我们仍然需要具备部署那种标点符号的模糊思维。但是大部分时候，语言的这种细节已经不重要了。

IDE 不仅对框架有帮助，还有一些小细节。它们提醒我们函数调用的参数，它们甚至检查数据是否为正确的类型。然后，我们应该知道使用哪种函数、如何将它们组合在一起。当语法不是太紧要时，这就是我们精力需要集中的地方------更高级的方法和函数，将有助于更方便地找到解决方案。


### 语法和视觉化语言一起消失


虽然已经预言很多年了，但是它在某些代码------尽管不是全部------仍在缓慢地发生着。某些编程继续着非常文字式，但是有些正变得更加视觉化【注4】，这意味着潜在的计算机语言不是太重要。

GUI 构建器是最容易看到这个现象的地方。你可以整日整夜地拖拉用户界面部件，而不用担心它是 C、Java 或其它语言。细节在视觉化盒子里被编码。

AndroidBuilder 使得拖拉更多的布局成为可能，它将忠实地编写 XML 以及需要让代码运行的 Java 小代码。很难讨论视觉化语言未来会成为什么样子，尤其是在它们多次未能意识到该预言之后，但是当它们成长时，工具将增加更多视觉化。这意味着语言没那么强大或重要了。


### 代码即法律（code is law）


计算机语言有着极大的不可知论者。它们被设计为开放、接受和几乎无限延展的。它们意欲做你想要的任何事情。当然，有时候由于语法，你需要使用一些额外的字符，但是这些是很少的击键。之后，它主要是 if-then-else，再加上偶尔的聪明约束。所有这些语言将帮助你用想得到它们的方式、得到你想要的结果。如果有一些苛责的话，那么它们应该被设计为尽可能保持你的代码没有 bug，不要限制你能做的事情。

框架的威力就在这里，这就是设计师可以决定什么被允许、什么本质上要禁止。如果设计师不想让某些东西发生，那么神奇的函数调用将从 API 中消失。如果设计师喜欢这种想法，那么通常会有多个函数调用以及许多支持工具。这就是哈弗法学院教授 Larry Lessig 【注5】为什么喜欢说“代码即法律”的原因。

框架为它们所处的互联网角落建立规则，一旦你选择它们，就必须生活在规则之下。一些博客平台鼓励通过 Ajax 调用与其它博客链接。这就是你必须谨慎调查、聪明选择的原因。这就是框架最终主导我们生活方方面面的原因，甚至包括我们不在编程的那些短暂时光。



* * *






	
  * 注1：交叉编译器（英语：Cross compiler）是指一个在某个系统平台下可以产生另一个系统平台的可执行文件的编译器。交叉编译器在目标系统平台（开发出来的应用程序序所运行的平台）难以或不容易编译时非常有用。[http://zh.wikipedia.org/wiki/%E4%BA%A4%E5%8F%89%E7%B7%A8%E8%AD%AF%E5%99%A8](http://zh.wikipedia.org/wiki/%E4%BA%A4%E5%8F%89%E7%B7%A8%E8%AD%AF%E5%99%A8)

	
  * 注2：位拆裂 (Bit Banging)：一种利用微控制器的通用端口仿真串行接口标准(I²C、SPI等)的技术。[http://en.wikipedia.org/wiki/Bit_banging](http://en.wikipedia.org/wiki/Bit_banging)

	
  * 注3：off the grid：不使用水、电、信用卡，不上社交网络，以避免留下记录；愿意用自己做的东西而愿使用现成的。[http://www.urbandictionary.com/define.php?term=off+the+grid](http://www.urbandictionary.com/define.php?term=off+the+grid)

	
  * 注4：视觉化程式设计语言（Visual programming language，以下简称VPL），又称‘图形化编程语言’、‘视觉化程式编成语言’。系使用者利用图形化元素进行程式设计；相异于文字式程式设计。VPL以视觉表达为基础，利用‘文法’或是某种‘辅助标记’进行图形与文字的排列。许多VPL建基于‘方块与箭头’的概念之上，以方块或屏幕上的物件为本体，以箭头相连接，以直线段与弧线段代表相互之间的关系。[http://zh.wikipedia.org/wiki/%E8%A6%96%E8%A6%BA%E5%8C%96%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%E8%AA%9E%E8%A8%80](http://zh.wikipedia.org/wiki/%E8%A6%96%E8%A6%BA%E5%8C%96%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%E8%AA%9E%E8%A8%80)

	
  * 注5：[http://en.wikipedia.org/wiki/Lawrence_Lessig#.22Code_is_law.22](http://en.wikipedia.org/wiki/Lawrence_Lessig#.22Code_is_law.22)


