---
author: viviworld
comments: true
date: 2014-02-17 00:13:32+00:00
layout: post
link: http://www.labazhou.net/2014/02/knowing-what-to-build-next/
slug: knowing-what-to-build-next
title: 了解接下来开发的功能
wordpress_id: 284
categories:
- 设计
tags:
- facebook
- google
- tooltip
---

几个月前，我们开始调查哪种类型的、社会化账号的、[Buffer](https://bufferapp.com/)用户对接下来要使用的功能最感兴趣。这里有一种工具，找到哪种类型的账号最受欢迎，以及我们如何跟踪给我们发送请求的每个用户。


### 我们做了什么


下面是当前的Connect页的截图：

[![Connect page](http://www.labazhou.net/wp-content/uploads/2014/02/fn2ypewytagpgg_small.png)](http://www.labazhou.net/wp-content/uploads/2014/02/fn2ypewytagpgg_small.png)

然而，Connect页并不总是这个样子。就在几个月前，一些选项------像Facebook Group和LinkedIn Page------还没有对用户呈现。

除了隐藏不支持的选项，我们决定显示一个无法点击的按钮，当鼠标悬停的时候，显示两个新的选项：



	
  1. Learn More：链接到FAQ页的快速入口，解释了为什么特定类型账户还不支持。

	
  2. Notify Me：点击这个按钮，我们数据库中的用户email地址就被标记为“感兴趣的某账户”。


下面是一个Google+ Profile的例子（不幸的是，它仍然不被第三方app支持）：

[![Connect page](http://www.labazhou.net/wp-content/uploads/2014/02/5ck04e7rhmewq_small.png)](http://www.labazhou.net/wp-content/uploads/2014/02/5ck04e7rhmewq_small.png)


### 发生了什么


这个工具提示最后让我们大吃一惊，体现在两个维度：



	
  1. 我们通过直接链接到FAQ页主动解答了用户的疑问，该页提供了我们不支持特定账户类型的详情。

	
  2. “Notify Me”按钮让我们记下了每一个感兴趣用户的email地址，因此在我们最终腾出时间来开发这些功能的时候，就拥有了目标精准的email列表。


两周前我们为Buffer推出了支持Facebook Group功能。由于有了可爱的小“Notify Me”按钮，我们总共收集了1650个对此感兴趣用户的email地址。我们给这些人发送了邮件，得到如下结果：

	
  * 发送了1650邮件

	
  * 打开率：70%

	
  * 点击通过率：18.7%


还不错。


### 加到你的Startup里


如果你纠结于为产品的接下来功能开发什么，这个方法就是一个超级轻便的追逐兴趣的方式，你就可以得到对用户重要的精确判断。

我不是要非常热衷于此------毕竟，让大量的通知散落在产品各处，或许使得它看起来像个半成品。但是对于小的产品改进或假设检验，这是帮助做出明智决定的真正简单的方法。

原文地址：[http://blog.brianlovin.com/knowing-what-to-build-next](http://blog.brianlovin.com/knowing-what-to-build-next)
