---
author: viviworld
comments: true
date: 2014-01-03 03:48:35+00:00
layout: post
link: http://www.labazhou.net/2014/01/six-essential-drupal-interview-questions/
slug: six-essential-drupal-interview-questions
title: 6个必备的Drupal面试题
wordpress_id: 122
categories:
- 编程
- 职业
tags:
- cvs
- drupal
- module
- pitch
---

你正在招聘Drupal开发工程师吗？你知道如何甄别好的开发工程师吗？

我的一个客户让我列出问题清单，通过讨论这些问题来评估应聘者的技能水平。我列出了涵盖全面Drupal开发经验的6个问题，经过20分钟的面试你就清晰地了解应聘者的Drupal水平。


### 1.你经常向客户推荐哪些module？


在问问题之前，你先看看drupal.org上面[Drupal module用法](http://drupal.org/project/usage)的网页。应聘者应该能够提到一定数量的前30个的module。

让应聘者逐个解释推荐的理由，他们应该能给你一个冠冕堂皇的说法。如果他们推荐一个特别冷门的module，就问它支持的程度。

问题如下：



	
  * 你为什么推荐那个module？

	
  * 那个module支持力度如何？

	
  * 那个module有过一些不足吗？




### 2.Drupal的缓存工作原理？


关于Drupal的一个普通吐槽（多数是无事实依据的）就是，”Drupal太慢了“。你想雇佣一名理解Drupal内建缓存系统及其限制的开发人员。例如，Drupal 6在用户登录的情况下，block cache不会加速网页。

让应聘者给出加速Drupal缓存的一些额外解决方案，它们或许包含Boost module，Varnish，Squid，Memcache和Pressflow。问问他们是否曾经在Drupal缓存中遇到过。

问题如下：



	
  * 你有其他加速Drupal的方法吗？

	
  * 你曾经遇到过Drupal缓存的问题吗？

	
  * 你是如何解决的？




### 3.View是做什么的，你如何使用它？


对于Drupal 6 搭建的网站，View是一个实实在在的必需品，开发者理解如何有效使用也是必需的。Earl Miles在[View项目页](http://drupal.org/project/views)写了一个非常棒的摘要。

问题如下：



	
  * 举个项目中需要使用view的例子。




### 4.如何处理升级？


频繁升级Drupal安装和贡献的module是常有的事，应聘者应该提到：



	
  * 备份网站

	
  * 切换成维护模式

	
  * 下载module新版本

	
  * 解压

	
  * 运行update.php

	
  * 测试网站

	
  * 关掉维护模式


理想情况下，应聘者会提到生成一个开发环境来最小化故障时间。在升级一个module（上面描述的）和Drupal minor版本升级之间有个比较大的区别在于需要更小心地打补丁。Drupal major版本升级，通常数年发生一次，属于另外一个话题了。


### 5.展示一下你用Drupal做的网站


如果你在招一名管理项目所有环节的，从需求到编码、到主题设计的开发人员，一定要确认你对他之前的作品满意。对于这些网站，要了解他们在每个项目中的角色，随变看看，确认它们是否仍然运行！

问题如下：



	
  * 你在这个项目的角色是什么？

	
  * 你是和哪些雇主/同事一起完成这些项目的？

	
  * 客户满意吗？

	
  * 我能从客户那儿得到一封表扬信吗？




### 6.你给Drupal提交了多少补丁？


感谢协作开源编程，任何人都能提交补丁或贡献module。能力强的应聘者会找到现存代码库的一些问题，并作出相应补丁。

希望他们已经把这些变化贡献给了Drupal。让他们给出Drupal用户名，你检查一下！

问题如下：



	
  * 你贡献过哪些module？

	
  * 你的Drupal CVS用户名是什么？


还有问题吗？

我希望这些问题对你有帮助。你有一些针对Drupal开发者的常用面试问题吗？发到下面的评论里！

原文地址：[http://www.davetech.com/blog/six_essential_drupal_interview_questions](http://www.davetech.com/blog/six_essential_drupal_interview_questions)
