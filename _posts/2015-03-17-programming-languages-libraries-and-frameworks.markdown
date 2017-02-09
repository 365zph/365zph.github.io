---
author: viviworld
comments: true
date: 2015-03-17 08:55:46+00:00
layout: post
link: http://www.labazhou.net/2015/03/programming-languages-libraries-and-frameworks/
slug: programming-languages-libraries-and-frameworks
title: 编程语言、资源库和框架
wordpress_id: 1715
categories:
- 编程
tags:
- api
- jquery
- module
- 机器码
- 框架
- 汇编
- 资源库
---


	
  * 原文地址（original source）：[http://blog.alexdevero.com/programming-languages-libraries-and-frameworks/](http://blog.alexdevero.com/programming-languages-libraries-and-frameworks/)

	
  * 作者（author）：[https://twitter.com/AlexDevero](https://twitter.com/AlexDevero)


当你想学习新的编程语言时，你会突然面临诸多挑战。你应该学习哪种语言，它应该提供什么功能等等。有很多方式限制了你从一堆现有编程语言中选择。比如你可以看下稍后的更新，或者参考某种[使用统计](http://githut.info/)。你还可以在 [Stack Overflow](http://stackoverflow.com/) 之类的网站上提问，或询问你的朋友和同事。让我们考虑不同的选择吧……直接去学资源库和框架，而不是语言。


### 编程语言是什么


编程语言是人们设计用来和机器（计算机）沟通指令的人造语言。它通常由两部分组成。第一部分是语法------指令的形式，第二种是语义------这些指令应该怎样被机器（计算机）解释。编程语言用于创建程序，以控制机器的行为或表达算法。依据你使用的条件，编程语言可被分成各种类别。

两种经常用到的类别是低级和高级编程语言。在第一个例子中，词语“低”指介于这种语言和机器语言之间的、有限的或不存在的大量抽象。可把它看做更接近于硬件。通常指机器码或汇编语言。

机器码的例子：


<blockquote>b8 21 0a 00 00
a3 0c 10 00 06
b8 6f 72 6c 64
a3 08 10 00 06</blockquote>


汇编语言的例子：


<blockquote>section .text
global _start ;must be declared for linker (ld)
_start: ;tells linker entry point
mov edx,len ;message length
mov ecx,msg ;message to write
mov ebx,1 ;file descriptor (stdout)
mov eax,4 ;system call number (sys_write)
int 0x80 ;call kernel</blockquote>


另一方面，[高级](http://en.wikipedia.org/wiki/High-level_programming_language)语言有着来自于[低级](http://en.wikipedia.org/wiki/Low-level_programming_language)语言的强烈抽象，更容易使用和阅读。你可能至少已经听到过这种类型的语言。比如，今天使用最多的语言，它可以是 PHP、Python、ECMAScript、C++、Java 或 Ruby。

Ruby 的例子：


<blockquote>for current_iteration_number in 1..10 do
puts "Hello world, this is number #{current_iteration_number}."
end</blockquote>


JavaScript 的例子：


<blockquote>for (var i = 0, j = 10; i < j; i++) {
console.log(“Hello world, this is number” + i + “.”)
}</blockquote>




### 什么是资源库


编程里的资源库的定义可以是：供程序使用的预编译的、永久的例行程序的集合。这些例行程序，有时候叫做模块（module），可以包含配置数据、文档、消息模板、子例行程序、类、值或类型说明。一个资源库最大的优点以及使用它们的理由，是可复用行为的能力。当你使用一个资源库时，程序获得了资源库内部实现的行为、而不必实现行为本身。

今天都有哪些资源库？恩，范围相当宽广，没有限制。今天的明星是 jQuery、Underscore.js、Raphael、YUI 或 typeface.js。


### 什么是框架


框架是一种真正的或概念性的结构，创建的目的是为开发程序提供支持或指导，把这种结果扩展为有用的东西。框架可以包含各种工具、代码库、编译器，还有与项目开发或某个具体问题的解决方案绑在一起的应用程序接口（[API](http://blog.alexdevero.com/introduction-to-apis/)）。你可以把框架想象为现成的包（速食汤）。

当前最流行框架的例子可以是多功能的 web 开发（HTML、CSS 和 JavaScript）方面的 Twitter 的 Bootstrap、ZURB 的 Foundation、Front-end Boilerplate 或 Themosis。对于 PHP，你可以使用 CakePHP、Symfony、Laravel、Nette 或 PhalconPHP。对于 Ruby，它可以是 Ruby on Rails、Lotus、Padrino 或 Sinatra。


### 学习编程语言或框架（资源库）


我在文章开头问到的问题是，你是应该学习一种编程语言，抑或学习框架。首先，我为编程语言百分百地投票，因为在你将关注缩小在框架或资源库之前，你应该了解原理。然而，比遵循任何建议更重要的是，理解你学习新框架目标背后的潜在意图。

如果你只使用某些特定的框架、或你只想完成某些具体目标，那么你或许不想学习整个语言及其逻辑。还有，学习需要投入时间和努力，尤其是对于语言而言。如果你不能长期投入，这种投入就变成了资源浪费（心理和生理）。就在最近，我不得不改变这种观点。

总之，如果你想快速搞定工作、而不用雇佣和从来不用回头看，更聪明的选择就是拾起你选择的框架或资源库，学习所有必要的东东，然后继续前进。这是我要推荐的最佳实践吗？绝对不是。尽管如此，做为一名 web 开发人员和设计师，我经常看到某人为了短期目标而创建的代码------仅仅学习刚刚够的东西以完成工作------没有处于很好的状态，甚至没有考虑过遵循最佳实践。

结果，刚开始的步骤常常是清理代码，并将其带入维护级别。换句话说，大量时间被花在了不必要的地方。鉴于此，我经常告诫人们要“忍受”学习新语言的痛苦，包括在编程之前的、对于最佳实践的理解。还有，如果你不是开发将被更多人（个人网站、业余项目）使用的东西，就可以随意在语言和原理上倾倒垃圾。

对于剩下的想做长期方式或想法的人们而言，最好去学习你选择的语言，掌握原理、体验最佳实践。区别将立即显现。与短期方式的结果相比，你的代码将更加整洁、快速、简洁以及易于维护。重要的问题好像变成了你的意图或下一个未来步骤是什么。回答这个问题将有助于你选择应该从事的正确方式------语言或框架/资源库。


### 结论


如果你想开发东东（编程方面的），你可以根据项目要求选择编程语言，或采用现成的框架或资源库、而不必具有合适的知识。对于只想完成工作而从来不会再回头看的人们，第一个选择是更加耗时和不必要的。第二选择将是剩下的人所喜欢的，人们乐于尝试。

然而，两种选择将产生影响。跳过学习部分将增加错过某些东西的可能性，如果不是全部，它将是与编程语言相关的最佳实践，这能够让代码在某个时间点之后[更难以维护或理解](http://www.labazhou.net/2014/11/why-your-code-is-so-hard-to-understand/)。你选择的每个捷径都有自己的影响，你最好三思并明智地选择。那么，你想学习整套语言，还是仅需的“刚刚够的东西”？
