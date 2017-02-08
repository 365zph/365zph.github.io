---
author: viviworld
comments: true
date: 2015-01-03 12:53:20+00:00
layout: post
link: http://www.labazhou.net/2015/01/environment-variables-considered-harmful/
slug: environment-variables-considered-harmful
title: 对隐私有害的环境变量
wordpress_id: 1483
categories:
- 安全
tags:
- api
- ImageMagick
- 密钥
- 最少权限原则
---

原文地址（source）：[http://movingfast.io/articles/environment-variables-considered-harmful/](http://movingfast.io/articles/environment-variables-considered-harmful/)

为了轻松访问运行在生产环境里的代码，存储你的密钥是一项有挑战的任务。对于这些密钥，我意思是，例如用于访问第三方API的keys、用于加密/签名cookie的keys、[哈希用户密码](http://www.labazhou.net/2014/01/are-passwords-stored-in-memory-safe/)等等。如果你的生产密钥落入了坏人之手，将产生可怕的影响。你想牢牢地控制访问密钥的方式和时间。

我们很可能对怎样不去存储密钥持相同意见，那就是：在你的代码，或与你代码相同的源代码库里。通常，有太多人或第三方服务可以（潜在地）访问你的代码库，他们不需要（也不应该）知道你的生产环境密钥。

关于如何架构现代web应用程序的一个优秀文档是[The Twelve Factor App](http://12factor.net/)。它列举了每个web开发人员应该了解的12项原则（他们称之为要素）。“[Config](http://12factor.net/config)”一章提到了：“在环境里存储config”。虽然我同意操作系统环境是总体配置的好场所，但是，我还是不能推荐它用于保存隐私。

当你在环境里存储密钥时，你仍然有可能偶然地暴露它们------这恰恰是我们想避免的。

让我们仔细看一下环境和环境变量。这是任何操作系统都有的一个特性，你可以用来托管web应用，包括Linux、Mac OS和Windows。环境变量已经被用于系统配置了，被设计成从父进程向其子进程传递配置。一个子进程默认继承了来自于其父进程的、所有环境变量（被叫做环境）的拷贝。

根据环境的这些属性，问题就在于它在什么时候存储密钥：



	
  1. 环境可以被进程隐式地访问。难以追踪访问，其内容是怎样暴露的。抓取整个环境并打印出来（有利于调试）、或作为错误报告的一部分来发送是比较容易的。

	
  2. 整个环境被传递给了子进程（如果没有显式地过滤掉），这违反了[最小权限原则](http://en.wikipedia.org/wiki/Principle_of_least_privilege)【注1】。那么你的密钥就可以隐式地被用到的第三方工具（像图像处理的ImageMagick）访问。这些第三方工具用环境做些什么，这很难说，特别是在诸如崩溃的极少情况下。

	
  3. 外来的开发人员不一定意识到你的环境包含有密钥。这样做了，你的需求（严格控制访问）将与大多数开发人员的隐式期望（环境里没有特别的东西，只是普通的系统配置）不再匹配。这是一种危险的不匹配。


这样我们的解决方案一直是使用一个配置文件，有服务器配置管理软件（我们的例子中是个大厨）管理。这样，我们就能在代码库外面存储密钥，通过使用配置服务器的相同软件来管理它们。这种解决方案虽然不是最好的，但是不会把密钥暴露给子进程，这种方案需要显式地访问，也表达了开发人员应该如何与之协作。

但是不管你选择哪种方案，要当心就你如何使用密钥的不同警告。

	
  * 注1：在计算机科学以及其它领域中，最小权限原则是要求计算环境中的特定抽象层的每个模块如进程、用户或者计算机程序只能访问当下所必需的信息或者资源。赋予每一个合法动作最小的权限，就是为了保护数据以及功能避免受到错误或者恶意行为的破坏。最小权限原则也称为最少权限原则。[http://zh.wikipedia.org/wiki/%E6%9C%80%E5%B0%8F%E6%9D%83%E9%99%90%E5%8E%9F%E5%88%99](http://zh.wikipedia.org/wiki/%E6%9C%80%E5%B0%8F%E6%9D%83%E9%99%90%E5%8E%9F%E5%88%99)


