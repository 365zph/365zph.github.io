---
author: viviworld
comments: true
date: 2015-05-04 08:31:32+00:00
excerpt: 如果你打算坚持开发 web 应用程序，那么就采用 Ruby on Rails。它有一个非常强大的社区，他们常常处于前沿。如果你对开发 web 应用程序有兴趣，但是更想学习一门语言，那就使用
  Python 和 Django。你将得到一个多样化的社区，和来自它所处的各种行业的大量影响和支持。
layout: post
link: http://www.labazhou.net/2015/05/ruby-vs-python/
slug: ruby-vs-python
title: Ruby 和 Python
wordpress_id: 1985
categories:
- 编程
tags:
- Django
- python
- ruby
- Ruby on Rails
- rubygem
---


	
  * 原文地址（original source）：[http://learn.onemonth.com/ruby-vs-python](http://learn.onemonth.com/ruby-vs-python)

	
  * 作者（author）：[https://twitter.com/excid3](https://twitter.com/excid3)





* * *




<table >
<tbody >
<tr >

RUBY
PYTHON
</tr>
<tr >

<td >语言
</td>

<td >



	
  * 更多魔法

	
  * 由 Yukihiro Matsumoto 创建于1985年



</td>

<td >



	
  * 更直接

	
  * 由 Guido Van Rossum 创建于1991 年



</td>
</tr>
<tr >

<td >优点
</td>

<td >



	
  * 用于 web 开发的、海量的现成功能

	
  * 快速拥抱新事物



</td>

<td >



	
  * 易于学习

	
  * 多样化社区，与 Linux 和学术界有着强大纽带



</td>
</tr>
<tr >

<td >缺点
</td>

<td >



	
  * 常常难以调试



</td>

<td >



	
  * 经常非常明晰、阅读起来不太优雅



</td>
</tr>
<tr >

<td >WEB 框架
</td>

<td >



	
  * Ruby on Rails - David Heinemeier Hansson 于 2005 年开发



</td>

<td >



	
  * Django - Adrian Holovaty 和 Simon Willison 于 2003 年开发



</td>
</tr>
<tr >

<td >社区
</td>

<td >



	
  * 创新更快，但带来了需要解决的更多问题

	
  * 专注于 web



</td>

<td >



	
  *  非常稳定和多样化，但是创新较慢

	
  * 广泛应用于学术界和 Linux



</td>
</tr>
<tr >

<td >使用
</td>

<td >



	
  * Apple

	
  * Twitter

	
  * Github

	
  * Airbnb

	
  * Groupon

	
  * Shopify



</td>

<td >



	
  * Google

	
  * Pinterest

	
  * Instagram

	
  * Mozilla Firefox

	
  * National Geographic

	
  * The Washington Post



</td>
</tr>
</tbody>
</table>


### Ruby on Rails 和 Python and Django，哪个更好？


这是我们经常被重复问到的一个问题，也是一个重要的问题。你一直都有听到 Ruby 和 Python 的比较。如果你对它们不熟悉，这就成了无法回答的问题。我过去都用过，可以告诉你，虽然它们有些相似，但是它们在某些重要的地方有着差别。

做为准备，我首先通过 Python 和 Django 学习了 web 开发。开发了四年 Django 应用，之后我找到一份做 Ruby on Rails 的工作，预期这个转变是非常简单的。就是在那个时候，这两种语言和框架的差别，才变得清晰。


### 它们有着怎样的不同？




#### 语言


Ruby on Rails web 框架使用 Ruby 编程语言开发，而 Django web 框架使用 Python 编程语言开发。

很多不同点都源于此。这两种语言在视觉上是相似的，但是它们解决问题的方式却是两个世界。

Ruby 被设计为无限灵活，给程序员以力量。它允许 Ruby on Rails 做大量的小技巧，以做出优雅的 web 框架。不时地，甚至可以感觉到有魔力，但是这种灵活性常常也是毁誉参半。有时候你没有期望代码运行，它却运行了，从而给你留下很深的印象。有时候 Ruby 的魔法使得花费数个小时追踪 bug 变得异常艰难。

Python 采用更加直接的方式编程。其主要目标是让程序员对所有东西感到清晰。这牺牲了 Ruby 所拥有的某些优雅，但是在学习编码和调试问题时，有着较大优势。

显示差别的、有代表性的例子就是，你的应用程序里的时间处理。假设你想得到从现在开始算起的一个月的时间。下面是两种语言的实现。

**Ruby**

    
    require 'active_support/all'
    new_time = 1.month.from_now


**Python**

    
    from datetime import datetime
    from dateutil.relativedelta import relativedelta
    new_time = datetime.now() + relativedelta(months=1)


Python 版显示，从 datetime 和 dateutil 导入具体的功能。这相当明确，不过你可以容易地分辨出每样东西是从哪儿来的。

Ruby 版有着强大的魔法。我们导入了某个 active_support 资源库，突然之间，Ruby 中的所有 integer 就有了这些“.days“和”.from_now“方法了。它利于阅读，但是这个功能从 active_support 内部哪个地方来的就十分不清晰了。还有，用新功能匹配该语言中的所有 integer 的思想非常酷，但是它也会被滥用而引起问题。

两种方式无所谓对与错，它们只是强调着不同的地方。Ruby 演示了语言的灵活性，而 Python 演示了直接性和可读性。


#### web 框架


Django 和 Rails 都是帮你开发 web 应用程序的框架。它们有着相似的性能，因为 Ruby 和 Python 都是脚本语言。每个框架都提供了来自传统的 MVC 框架的所有概念，比如模型、视图、控制器和数据库迁移。

每个框架在你如何实现这些功能方面有着不同，但是它们核心是相似的。Python 和 Ruby 还有很多资源库，你可以使用它们来给你的 web 应用程序增加功能。Ruby 有一个名叫 Rubygems 的资源库，而 Python 的资源库叫 Package Index。


#### 社区


Python 和 Ruby 背后都拥有十分巨大的社区。社区影响着语言的方向、更新以及使用它们开发软件的方式。

Python 和 Ruby 相比，有着一个更加多样化的社区。在数学和科学方面，有着大量的科研案例，这是 Python 繁荣的领域。这些领域提供了大量支持，它将因这种势头而继续增长。Python 差不多被安装在每一台 Linux 服务器上，这使得它成为服务器端使用的最完美语言。

Ruby 的流行是从 Rails 在 2005 年诞生之后才真正开始的。[围绕 Rails 的社区成长迅速](http://www.labazhou.net/2014/06/top-8-ruby-on-rails-blog-resources/)，极其专注于 web 开发。随着时间的推移，该社区有了更多的多样化，但是它还没有达到 Python 同样级别的多样化。

[![Ruby-vs-Python](http://www.labazhou.net/wp-content/uploads/2015/05/Ruby-vs-Python-300x232.png)](http://www.labazhou.net/wp-content/uploads/2015/05/Ruby-vs-Python.png)


#### 使用


谁在用这些语言？相当多的公司。这两种语言和 web 框架在技术界传播甚广。

Python 一直被 Google、Pinterest、Instagram、National Geographic、Mozilla Firefox 和华盛顿邮报陪伴着。

Ruby 一直被 Apple、Twitter、Airbnb、Shopify、Github 和 Groupon 等公司使用着。


### 结论


你能够在 Ruby on Rails 里做的每样功能，都可以在 Python 和 Django 里做。哪种框架更好，真的不是一个能力的问题，实际上，对于你和团队而言，这是一个支持方面的问题。


### 我的经验之谈


如果你打算坚持开发 web 应用程序，那么就采用 Ruby on Rails。它有一个非常强大的社区，他们常常处于前沿。

如果你对开发 web 应用程序有兴趣，但是更想学习一门语言，那就使用 Python 和 Django。你将得到一个多样化的社区，和来自它所处的各种行业的大量影响和支持。

不管怎样，你不会走错路。你在 Python 学到的每样东西，都能被翻译为 Ruby，反之亦然。它们背后都有支持性的社区。如果你有朋友在做其中一个，就加入他们，因为你在这个过程中，可以常常向他们寻求帮助。

PS：我们将在接下来的几周里发布一个新的 Python 教程。[点击这里，抢先访问](https://onemonth.com/courses/python)！
