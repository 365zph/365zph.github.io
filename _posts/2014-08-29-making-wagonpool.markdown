---
author: viviworld
comments: true
date: 2014-08-29 12:13:43+00:00
layout: post
link: http://www.labazhou.net/2014/08/making-wagonpool/
slug: making-wagonpool
title: 开发“Wagon Pool”
wordpress_id: 950
categories:
- 编程
tags:
- APP
- ios
- iTunes
- objective-c
- oop
- xcode
---

今年我第一次做了个app。它是一个[简单的拼车计算器](http://www.wagonpool.com/)，帮你算出某个行程每个花了多少钱。我从头开始设计、开发Wagon Pool，之前没有Objective C，Xcode或面向对象编程经验。我对此感到新鲜，我想记录一下开发的过程。如果你想学习如何开发移动应用程序，本文或许有些帮助。


### 目标


项目的期望是能够发布一些让我引以为豪的东西。我想让app简单、专注、优于同类产品。

对开发一个iOS应用程序需要什么技能，我也想深入理解，我需要学习OOP以及相应的移动开发。


### 开始


我买了一本99美分的笔记本帮助整理思路。整个过程，我用上了画图形，插画及图表。这给了我额外的心理空间，把我脑中要做的事情可视化了。

[![开发时画的草图](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-notepad.jpg)](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-notepad.jpg)


### 设计


我想让app看起来高逼格，简化计算过程。关于如何让用户输入信息，我花了很长时间考虑。我模拟了界面可以运行的八个不同方式。

[![8种手机界面的app设计](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-mockups.jpg)](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-mockups.jpg)

我选择最后一个做为出发点，因为用户不必输入或切换界面就能得到快速估价。

要开始，还需要一个简单的icon，我计划要用到的。朋友逼着我做了一个值得纪念的东东，我规划了很多想法，在512x512上看着效果不错，但是到了实际设备就难看了。经过多次调整，我找到了喜欢的样子。

[![wagon pool的logo](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-icon.jpg)](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-icon.jpg)


### 开发


开发“Wagon Pool”既有挑战、又有回报。因此很多时间都花在了这么个小app上。

Xcode在创建outlet、使用简单的方法和探索interface builder上比较方便。短期内我创建了一个工作版，然而我这边还有一些严重的问题。比如，所有东西都在ViewController里。我知道，很多代码不属于这里，但是我不知道放到什么地方。还有很多多余的代码需要我去清理。

我在iTunes University上学习[Stanford课程](https://itunes.apple.com/us/course/developing-ios-7-apps-for/id733644550)。不过，我意识到我需要加强理解OOP。

我从头到尾阅读了Matt Neuburg的《[iOS编程原理](http://www.amazon.com/iOS-Programming-Fundamentals-Objective-C-Basics/dp/1491945575/ref=sr_1_2?ie=UTF8&qid=1409103316&sr=8-2)》，这是一项无法估量的投资。前五章特别有帮助，因为它包含了iOS开发的原理。同时，我每天晚上写代码，去实践我学到的。

在我看完这本书后，仍然有很多东西需要学习。为了更好地理解MVC模式、auto layout、delegation和动画，我让自己再深入一些。


### 发布


三个月后，我注册了iOS开发者项目。我想花时间调试，学习内存管理，收到反馈。我收到了大量的反馈和建议，最大的问题在于用户无法有效控制其输入。我决定创建新模型，让用户可以在默认范围之外输入值。这让我慢了几周，不过我很开心要在V1.0版本里发布了。

[![wagon-glyphs](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-glyphs.png)](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-glyphs.png)

它是一款小app，却是让我自豪的app。去[苹果商店](https://itunes.apple.com/us/app/wagon-pool-simple-carpooling/id846135212?mt=8)下载，让我知道你的想法！

[![wagon pool的截图](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-screenshots.jpg)](http://www.labazhou.net/wp-content/uploads/2014/08/wagon-screenshots.jpg)

原文地址：[http://philipcdavis.com/notebook/making-wagonpool/](http://philipcdavis.com/notebook/making-wagonpool/)
