---
author: viviworld
comments: true
date: 2014-08-30 11:39:02+00:00
layout: post
link: http://www.labazhou.net/2014/08/the-power-of-query-comments/
slug: the-power-of-query-comments
title: 查询注释的力量
wordpress_id: 965
categories:
- 编程
tags:
- github
- Marginalia
- MySql
- ORM
- rails
---

当人们使用框架的时候，他们经常依赖ORM生成查询。然而，由于他们自己没有显式地编写查询，当这些查询出现在MySQL日志里时，难以追踪其来源。

我发现真正有用的一种方式是添加查询语句注释，并包含查询来源。

例如：


<blockquote>SELECT * FROM users /*application:webapp,category:chill,route:users#get,all*/;</blockquote>


这让我们快速地找到生成查询的地方。在GitHub，我们使用[Marginalia Gem](https://github.com/basecamp/marginalia)注入这些注释。Marginalia还让你注入自己的成分。

要添加的、有用的注释成分就是请求id，这意味着你能够匹配日志中的慢查询请求以用于调试。

原文地址：[http://samlambert.com/posts/the-power-of-query-comments/](http://samlambert.com/posts/the-power-of-query-comments/)
