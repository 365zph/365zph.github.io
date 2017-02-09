---
author: viviworld
comments: true
date: 2014-11-12 03:55:01+00:00
layout: post
link: http://www.labazhou.net/2014/11/the-rarely-taught-basics-of-building-software/
slug: the-rarely-taught-basics-of-building-software
title: 很少被教的软件开发基础
wordpress_id: 1314
categories:
- 编程
- 软件
tags:
- Git
- Mercurial
- ssh
- subversion
- Ubuntu
- 时光机
---

我经常想忘掉，在没有经验的团队里开发软件有多糟糕。他们的大部分开发实践和[Hobbes关于原始人的描述](http://en.wikisource.org/wiki/Leviathan/The_First_Part#Chapter_XIII:_Of_the_Natural_Condition_of_Mankind_as_Concerning_Their_Felicity_and_Misery)类似。生活是“孤独、贫穷、肮脏、野蛮和短暂的”。就像原始人一样，这些人认识不到更好的生活是什么样子。

生活不必是这样的。我推崇的工具是软件，拷贝它们是自由的，唯一的成本就是人们需要学习该工具的时间。缺乏的是了解，人们需要知道如何使用这些工具，他们需要知道这些工具解决什么问题。最重要的是，他们需要知道这些工具是现成的。

下面是我认为基础工具的概览，它们是我认为合理的工具，缺少它们就像缺少电力和抽水马桶。悲催的是，它们都没有出现在我的计算机科学教育里。


### 备份


这适用于每个人，但是大量技术高手没有备份，我对此感到吃惊。如果你缺少备份，你将最终失去重要数据。我希望每个人在小学时就经历过硬盘坏掉的遭遇。就算丢失数据的几率很低，也要吸取备份的教训。

不管你用什么操作系统，备份总是比安装容易：



	
  * OS X有[时光机](http://support.apple.com/kb/HT1427)。

	
  * Windows有文件[File History](http://windows.microsoft.com/en-US/windows-8/how-use-file-history)。

	
  * Linux没有标准的备份方案。Ubuntu有一个备份功能，但是它有些难用，我从来没有用它尝试过还原。Ubuntu的社区维基有一些[关于备份的优秀资料](https://help.ubuntu.com/community/BackupYourSystem)。


我不能夸大备份的重要性，如果你要接受本文建议中的一条，**那就是备份**。


### 源代码控制


源代码控制记录了谁在什么时间改动了什么地方，可以轻松回退到已知良好的版本。它让每个人对他们做的修改负责，也让每个人容易地看到代码库随时间的变化情况。即使只有你一个人在维护代码，**也要使用源代码控制**！

Subversion、Git、Mercurial，你用哪种软件不重要，用任何软件都比不用强。与编程相比，这些工具学习起来没有难度。每一个流行的源代码控制软件都有与之相关的免费书籍：



	
  * [Pro Git Book](http://www.git-scm.com/book)

	
  * [Mercurial: The Definitive Guide](http://hgbook.red-bean.com/)

	
  * [Version Control with Subversion](http://svnbook.red-bean.com/)




### SSH Keys


在ssh中使用密码验证是坏习惯，SSH Keys允许你不用给远程服务器发送密码就可以身份验证。Arch Linux【注1】 wiki提供了一份优秀的SSH Keys指导。


### 避免用Root


使用sudo而非root，较容易地让你避免昂贵的错误。

人们扫描ssh服务器，并猜测普通的root密码是很常见的。为了应对这种攻击，关掉root登录，通过ssh设置/etc/ssh/sshd_config里的PermitRootLogin为no。


### 保持学习


提高开发和部署软件的经验，有无数种方法，人们每天都在创造新的工具，我只是列出了我认为绝对基础的一些工具。一个人的知识很容易停滞不前，一定要坚持从书本、朋友和同事那里学习。如果你坚持了，有一天你可能尝试开发属于自己的工具。



	
  * 原文地址：[http://geoff.greer.fm/2014/08/09/the-rarely-taught-basics-of-building-software/](http://geoff.greer.fm/2014/08/09/the-rarely-taught-basics-of-building-software/)

	
  * 注1：Arch Linux是朝向轻量（lightweight）以及简单（simple）的Linux发行版。其中“简单”（Simplicity）被定义为“避免不必要或复杂的修改”，也就是说，是由开发者角度定义，而非用户角度思考。[http://zh.wikipedia.org/wiki/Arch_Linux](http://zh.wikipedia.org/wiki/Arch_Linux)


