---
author: viviworld
comments: true
date: 2014-02-19 08:39:41+00:00
layout: post
link: http://www.labazhou.net/2014/02/introducing-bing-code-search-for-c-sharp/
slug: introducing-bing-code-search-for-c-sharp
title: Bing的C#代码搜索介绍
wordpress_id: 321
categories:
- 编程
- 软件
tags:
- Bing
- c++
- StackOverflow
- visual studio
- 代码搜索
- 微软
- 搜索引擎
---

假定要逐行读取一个文件，并处理这些行。今天，我们差不多要打开浏览器，访问我们习惯的搜索引擎，输入经过斟酌的、便于搜索引擎理解我们要解决问题的一些关键词。

理想情况下，我们能找到高质量的、带有示例的官方文档，或来自于某个顶级论坛的或一堆问答类型网站的、投票较高的主题。然后我们扫过结果，试着辨别出与我们相关的，再做一些复制/粘贴的工作。

我们想让这一切变得更加可访问性，想让你为了完成被安排的工作而更加容易地找到相关代码示例。


### 力求完美


我们想给你更好的体验。为了这个目标，Visual Studio，Bing和微软研究院成立团队开展了一项把代码搜索带往下一个层次的DevLabs实验。

当你发现自己正寻找一个代码示例时，你是可以因此而改变的，直接通过智能感知触发Bing代码搜索新体验。

[![bing代码搜索](http://www.labazhou.net/wp-content/uploads/2014/02/bingcodesearch1.thumb_.png-550x0.png)](http://www.labazhou.net/wp-content/uploads/2014/02/bingcodesearch1.thumb_.png-550x0.png)

那会触发类似于Peek Definition【注1】的宽阔的内联体验，聚焦到code-search。键入你要完成的任务，比如‘read a file line by line’，敲回车，就得到根据你的代码调整过的结果了。

[![bing代码搜索](http://www.labazhou.net/wp-content/uploads/2014/02/bingcodesearch2.thumb_.png-550x0.png)](http://www.labazhou.net/wp-content/uploads/2014/02/bingcodesearch2.thumb_.png-550x0.png)

上述场景背后，那个请求紧紧依靠Bing基于上下文片段帮助我们理解请求的完整意思。我们使用像项目类型的元数据，语义上下文（使用新的C#/VB编译器服务，称为‘[Roslyn](http://msdn.microsoft.com/en-us/vstudio/roslyn.aspx)’！），和一些少量的微软研究院的魔法。

这些东东和请求改变着Bing的大量搜索索引和关键词分析，并追踪到可能包含你从中受益的、高质量示例的潜在页面。

在那些页面里，我们根据大量的句法和语义学的代码指标来隔离、排列相关代码示例。

这时你就方便地在Visual Studio里看到了经过排序的结果，围绕着你的代码，还有我们设计的示例质量评估和来源（便于你深挖）。

[看看这个视频的体验演示](http://research.microsoft.com/apps/video/dl.aspx?id=208961)


### 改变互联网


这项新技术实现 事实上 可以使用整个互联网做为它的源。然而，我们发现，和一些拥有丰富在线代码示例的顶级网站合作，足够给很多高端用户的任务提供答案，这样我们可以专注努力。

我们与[MSDN](http://msdn.microsoft.com/), [StackOverflow](http://www.stackoverflow.com/), [Dotnetperls](http://www.dotnetperls.com/) 和 [CSharp411](http://www.c-sharpcorner.com/)合作，直接将一些好的代码示例提交到Visual Studio。


### DevLabs意味着实验


为了早日向公众开放，我们选择优先解决一个问题的子集。特别地，Bing代码搜索只面向C#，我们将来设法将此方法扩展到更多的语言。

确认你从[Visual Studio Gallery页上获取了扩展](http://aka.ms/bingcodesearch)，使用它，让我们知道你在想什么！编程愉快！

Visual Studio, Bing 和 微软研究院团队

原文地址：[http://blogs.msdn.com/b/visualstudio/archive/2014/02/17/introducing-bing-code-search-for-c.aspx](http://blogs.msdn.com/b/visualstudio/archive/2014/02/17/introducing-bing-code-search-for-c.aspx)
注1：Peek Definition：[http://iteches.com/archives/36374](http://iteches.com/archives/36374)
