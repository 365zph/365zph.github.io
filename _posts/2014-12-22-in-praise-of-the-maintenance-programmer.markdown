---
author: viviworld
comments: true
date: 2014-12-22 09:33:16+00:00
layout: post
link: http://www.labazhou.net/2014/12/in-praise-of-the-maintenance-programmer/
slug: in-praise-of-the-maintenance-programmer
title: 歌颂程序维护人员
wordpress_id: 1456
categories:
- 编程
- 职业
tags:
- bug
- 团队
- 程序员
---

原文地址（source）：[http://visualstudiomagazine.com/articles/2014/12/01/in-praise-of-the-maintenance-programmer.aspx](http://visualstudiomagazine.com/articles/2014/12/01/in-praise-of-the-maintenance-programmer.aspx)


<blockquote>当然，构建新应用程序的开发人员是非常优秀的人群。但是，编程世界里真正的英雄却是维护和扩展现有应用程序的开发人员们。</blockquote>


追溯到1984年，我刚刚毕业，准备受聘于开发人员的职位。我被一家跨国公司雇佣了……很快被安排到了现有应用程序的维护小组。在当时，这个决定貌似合情合理。现在回顾起来，真的很蠢。实际上，一个更好的描述应该是“疯狂至极”。

维护比新的开发工作要更加艰难。把我这种刚毕业的、“乳臭未干”的开发人员放在维护现有应用程序的工作上，就像让刚毕业的医学院学生为总统做脑部手术---有理智的人都不会这样干的。我当时维护的现有应用程序在支撑着公司；另一方面，在开发的应用程序与公司运作关系不大（尽管它们对公司的未来有一定影响）。

开发中的系统与生产环境上的系统的区别，取决于一个关键特征：如果开发中的系统崩溃了，没人会在意的。另一方面，如果你搞砸了生产环境上的系统，很多人都会来找你，而他们以前都懒得留意到你（我们不想问，我是怎样知道的）。

我现在明白了把我放在维护位置上的、逻辑上的真实原因了：公司IT部门需要很多“手和脚”。毕竟，IT部门75%的时间花在了维护上，因此推测出，他们在维护上需要的人数是开发所需人数的三倍。但是，把几乎没有实际工作经验的人放在需要工作经验的应用程序上，是行不通的。

“手和脚”的解释也解释不了 为什么新开发项目中的开发人员被普遍地视作英雄。退回到那时候，忙于新项目的人们相较于程序维护人员，有着更高的地位……我敢打赌这是真的。根据“提供的价值”，程序维护人员比开发程序员有着更多的价值。程序维护人员基于现有代码库开发，结果，与任何新开发小组可能管理的功能相比，程序维护人员用较少成本交付了更多功能。


### 程序维护人员的技能


当我最后转向新的开发工作后，实际上我丢掉了一些技能，而这些技能对于程序维护人员的工作是必备的。做维护工作，我差不多是个程序员，我还是历史学家和侦探。

例如，当我做维护时，收到了被分配的问题，去追踪一个bug，它偶尔引起我们的程序崩溃，随之留下一些脏数据。这个bug首次出现在4年前（比我加入公司还要早得多）。这个bug潜伏了一段时间，但是上周它再次出现了。

因为我是程序员，我扫了一眼代码，但是，由于我是第三或第四个被分配到这个问题（我还缺乏经验）的人，[貌似我不太可能发现 前任开发人员都没有发现的问题](http://www.labazhou.net/2014/11/why-your-code-is-so-hard-to-understand/)。如果它不是代码，我推测它一定是数据……这让我根据bug报告的时间进行了划分。最终的曲线比较有意思：刚开始bug出现得相当频繁（3-4次/天），到了如今，频率逐渐减少，这个bug每个月只出现几次。

根据这些证据，我得出了结论，在bug首次出现之前，一定发生了什么，而该bug导致数据库埋下了脏数据。当应用程序处理到脏数据时，程序就崩溃了，然后有人介入并修复数据。当我向组内其他人员（他们比我在公司的时间要长得多）演示这个分析时，他们立即定位到了问题：在bug首次出现之前、已经被运行的一个数据转换程序。有了这个信息，我们能够找到其余的脏数据，并修复该bug。

程序维护人员一直是这样做的：局部侦探、局部历史学家，偶尔地扮演成开发人员。他们也是软件考古学家（深挖打了拙劣补丁的代码层）和精神病专家（搞清楚比你先来的开发人员的动机）。

当我最终做新开发工作时，我很开心得到“提拔”，因为在维护小组待过之后，目前这份工作是如此地轻松。或许这是你调入开发的真正理由：随着年龄的增长，你开始失去优势，你没有被下放；相反，你被调到了不能做任何有害事情的工作上------新的开发工作。
