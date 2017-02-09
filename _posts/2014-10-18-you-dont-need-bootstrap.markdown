---
author: viviworld
comments: true
date: 2014-10-18 05:10:11+00:00
layout: post
link: http://www.labazhou.net/2014/10/you-dont-need-bootstrap/
slug: you-dont-need-bootstrap
title: 你不需要Bootstrap
wordpress_id: 1121
categories:
- 编程
- 设计
tags:
- bootstrap
- CMS
- css
- drupal
- javascript
- Sass
---

[![Bootstrap](http://www.labazhou.net/wp-content/uploads/2014/10/bootstrap.png)](http://www.labazhou.net/wp-content/uploads/2014/10/bootstrap.png)

有人听到我说对Bootstrap没有好感，是不会感到惊奇的。Four Kitchens【注1】为在各种Drupal活动上的响应式web设计和公司所做培训的其中一个目标，就是为开发者提供他们需要的工具，而不要使用Bootstrap或其它类似的工具。我希望澄清 我觉得Bootstrap对于大多数网站是错误的工具 的原因，以及你能够用什么来替代。


### 1.反设计模式


首先，Bootstrap支持太多的反设计模式。反设计模式是一种看似不错的设计思想，经常被复制，但是对于一个网站来说，通常是糟糕的思想。首先，Bootstrap没有给你一个真正的响应式设计。根据 我们正在把网站建立到手机、平板和桌面上的思想，它应当有4个breakpoint。这与基于内容建立网站、不管用什么设备浏览都要确保站点可用性，是相反的。关于设备如何不能适应这种离散类别的一个好例子就是三星的Galaxy Mega，它既是一个较大的智能手机，又是一个小平板。设计应该兼顾到这种设备，即使它不是一个明确的平板或智能手机。

基于class的网格系统通常也是一个问题，因为我们正在限制自己。网格应该适应内容本身，而不是对class的结构产生影响。我们不应当使用breakpoint来限制我们做一个12列的布局。我们应该围绕内容设计网站，产生让人尖叫的移动优先的布局。一句话：我们值得拥有更好的。


### 2.你应当使用自己的设计


Bootstrap网站看起来都一样，它们都用到了相同的前端代码。甚至这些主题使用了很多你或许不需要的样式。不过对于你的网站而言，你应该用尽可能少的CSS来做你的设计。当你从一开始就只能用你自己代码的时候，为什么你应该覆盖一些东西呢？


### 3.更好的标签


我讨厌过多的class、非语义的class搞乱我的标签。我想让我的网站是干净的、易读的，在我产生标签时尽可能少些阻碍。除了对于干净标签的期望，还有不想使用这种基于class的系统的若干理由。很多CMS，包括Drupal在内，都用自己的观点和方法来输出标签和class，把Bootstrap贯穿在标签里，这是非常痛苦的。是的，它管用，不过，有很多方法。但是，这比你从头就产生自定义CSS要花费更多的时间和精力。


### 4.Saas


在我的论点里，这是一个关键点，我通常得到如下反应，“是的，但是我需要制作快速原型，从第一天起我就没有时间自己写CSS。”在[Sass](http://sass-lang.com/)社区开始制作可插拔扩展、以支持使用100%的自定义代码之前，刚才说的没错。不仅仅你能用自定义代码，而且从第一天起你就在根据原型编写可发布的代码。[Team Sass](https://github.com/Team-Sass/)已经做了大量工作以支持[custom grid](https://github.com/Team-Sass/Singularity)、[media query](https://github.com/Team-Sass/breakpoint)和极度容易的[样式](https://github.com/Team-Sass/color-schemer)。你可以的，这些工具使之成为可能。


### Bootstrap的适用范围


我强烈建议不要使用Bootstrap，永远不要提倡在一个线上网站使用。话虽如此，它也不全是不好的，它是一群优秀的工程师和设计师向世界贡献的一些伟大思想。首先，它是学习的一种好方式，可以看看一些有趣的样式和JavaScript是如何被使用的。如果你是前端工作的新手，或者想在一个基础的层级看看响应式网站设计是如何运行的，那么签出代码。这是学习一些前端例子如何运行的不错的方法。还有，如果你正在开发一个后端管理页面，只在内部使用，那么Bootstrap就是一个伟大的工具，你不必做全部的设计就拥有了UI块。由于这种代码不需要极好的性能，不管其设计是不是从其它UI元素偷来的，这都没有关系，Bootstrap就是最好选择。


### 总结


不要使用Bootstrap。真的，不要用。你可以做得更好，设计得更好，代码写得更好。像Sass之类的CSS预处理器让你得到需要的快速原型，在这一点上，Sass的社区工具就是你的黄油面包。



	
  * 原文地址：[http://fourword.fourkitchens.com/article/you-dont-need-bootstrap](http://fourword.fourkitchens.com/article/you-dont-need-bootstrap)

	
  * 注1：Four Kitchens正是原文的网站。


