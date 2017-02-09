---
author: viviworld
comments: true
date: 2015-03-03 00:05:38+00:00
layout: post
link: http://www.labazhou.net/2015/03/how-i-build-1qad-in-48-hours/
slug: how-i-build-1qad-in-48-hours
title: 我是如何在48小时内创建1QAD网站的
wordpress_id: 1659
categories:
- 编程
tags:
- cron
- Dropbox
- email
- firebase
- Heroku
- json
- MailChimp
- RSS
---


	
  * 原文地址（original source）：[http://blog.piotry.me/how-i-build-1qad-in-48-hours/](http://blog.piotry.me/how-i-build-1qad-in-48-hours/)

	
  * 作者（author）：[https://twitter.com/yordaKhof](https://twitter.com/yordaKhof)




## 我是如何hack了4种免费工具来创建每日邮件发送app的。


本文是关于如何创建[One Quote A Day's](http://onequoteaday.io/)（1QAD）每日引用邮件服务的。


### 挑战


手头有数据库或名言（quote）和邮箱地址列表，我的任务就是每天给这些列表发送带有名言的邮件。名言应该按他们在数据库的顺序或状况进行读取。


### 理解挑战


让我们把问题分解为简单的任务：



	
  1. 在某处存放名言

	
  2. 在某处存放邮箱地址

	
  3. 创建一个重复任务，把一句名言放到邮件模板

	
  4. 发送邮件模板到邮件列表


**存放名言**：名言本身需要被放在某处。Dropbox、S3、我们自己的服务器；选择有很多。一旦确定好了，每句名言的URL不得不被记在某个地方。它可以放在一个json文件、或者你自己服务器等等。

**存放邮箱地址**：你可以存放在一个自定义的json文件、数据库、或使用[mailchimp](http://mailchimp.com/)。

**重复任务**：很多极客愿意开发自己的计划任务（cron）来发送邮件。cron在linux世界应该广泛，用于定期的重复任务。尽管如此，问题在于如果采用这种方法，你不得不控制邮件模板的输出。它将是纯html，而不是所期望的输出。

**发送邮件**：同样，很多极客将考虑使用自己的系统来发送邮件。问题在于你没有一种非常灵活的方法，来发送邮件的自定义模板文件。


### 解决方案


据我研究，最基础的信息是mailchimp提供了名叫“RSS to Email”的活动（campaign）功能。这意味着，只要有了RSS地址，对于每条新的RSS条目，mailchimp将自动给列表发送一封邮件。

Mailchimp还提供了最简单的、创建自定义邮件模板的方式。

搞定！

Mailchimp ping我的服务器---运行在Heroku上【注1】---针对特定URL每天一次。

当ping的时候，该URL将生成一个动态的、带有当天名言的RSS输出。

这些名言被存放在公开的dropbox目录里，他们的URL存放在firebase【注2】。为什么？因为dropbox免费，firebase也是免费 :) firebase还帮我存储了一个`start_date`的值。如果`start_date`是昨天，那么我就需要为今天读取数据库中的第一条名言。

扼要重述：



	
  1. 名言存放在dropbox，通过firebase访问

	
  2. 邮箱列表在mailchimp里动态更新

	
  3. 使用mailchimp的“RSS to Email”的活动功能，来重复发送email


我写的所有东西都在我的服务器 `/rss` 端点（endpoint）里，它们将生成RSS文件。60行的代码，0美元的花费。



	
  * 注1：Heroku是一个支持多种编程语言的云平台即服务。在2010年被Salesforce.com收购。Heroku作为最开始的云平台之一，从2007年6月起开发，当时它仅支持Ruby，但后来增加了对Java、Node.js、Scala、Clojure、Python以及（未记录在正式文件上）PHP和Perl的支持。基础操作系统是Debian，在最新的堆栈则是基于Debian的Ubuntu。[http://zh.wikipedia.org/wiki/Heroku](http://zh.wikipedia.org/wiki/Heroku)

	
  * 注2：Firebase也是类似的云服务，不同于Dropbox的文件，Firebase同步的是数据，服务对象是网站开发者，帮助他们开发具有实时（Real-Time）特性的应用。[http://www.csdn.net/article/2014-10-22/2822221-google-acquires-firebase](http://www.csdn.net/article/2014-10-22/2822221-google-acquires-firebase)


