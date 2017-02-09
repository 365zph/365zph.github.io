---
author: viviworld
comments: true
date: 2014-10-18 08:00:15+00:00
layout: post
link: http://www.labazhou.net/2014/10/why-dont-you-use-bootstrap/
slug: why-dont-you-use-bootstrap
title: 为什么你不用Bootstrap？
wordpress_id: 1124
categories:
- 编程
- 设计
tags:
- bootstrap
- jquery
- Ruby on Rails
---

背景：我供职于[Forward Partners](http://www.forwardpartners.com/)，它是电子商务创业公司的孵化器。我们提供独特的资金组合，和来自于我们------专家------的产品、设计、市场、前后端开发、人才和筹款的帮助。在他们取得足够成长、开始招募自己团队之前，由我负责构想阶段的工作。

---------------

创业公司为了把想法以最快的、最有效率的方式从概念变成产品，常常使用现成的框架，比如Ruby on Rails，jQuery和Bootstrap。我将解释，在为早期构想阶段的业务开发网站的时候，为什么我不选择使用Bootstrap。


### 我在什么时候使用Bootstrap


在一些场合，Bootstrap是非常有用的。如果你需要快速构建一个原型、管理界面或内部的app，那么Bootstrap在打造专业界面和直观感觉上是非常棒的。或者你可能在构建网站前端、考虑浏览器兼容性和数不胜数的设备尺寸上缺乏经验，Bootstrap会帮到你------在一定程度上。


### 构想阶段业务和新员工


为了高效使用Bootstrap、更好地理解它，你需要花时间通读文档，深挖源代码，搞清楚为了你的需求要如何自定义。当你已经掌握它了，Bootstrap会是一个极好的工具，可被用来开发高度自定义和可维护的站点，然而，你需要花费大量的时间才能到达这个级别。这是我们业务所不具备的奢侈。

通常，构想阶段的业务将是与我们一起工作的创始人（可能是合伙创始人）完成适应市场的产品。与我们的开发者工作时，我们必须输出易于更新的、可维护的代码库，最重要的是，一旦业务开始取得增长，要能够被他们自己的开发者接手。我无法想象新手将来能够或想高效地使用Bootstrap。


### 我认为Bootstrap存在的问题


有人已经详细地写过他们为什么不用Bootstrap，因此我挑选了一些符合我对该主题的感受的摘录。这可以解释，你决定在项目中使用Bootstrap之前，你该如何思考这个框架：


<blockquote>当Bootstrap有了自定义接口时，它不是你想用它开发你想要的任何东东的、一个装有砖块、木板、墙和门的箱子。Bootstrap更像是一种抵押。抵押是好东西。你没有时间存钱，用现金购买你的房子。你需要抵押来得到头上的屋顶。当你没有资源从头开发UI时，就使用Bootstrap来搞到一些UI，这是非常类似的。
------《[Bootstrap Bankruptcy](http://matthewcopeland.me/blog/2013/11/04/bootstrap-bankruptcy/)》</blockquote>


Bootstrap没有遵循最佳实践或好的语义，有太多的臃肿代码、过多的class名字和标签：


<blockquote>我讨厌过多的class、非语义的class搞乱我的标签。我想让我的网站干净、易读，在我产生标签时尽可能少些阻碍。
------《[你不需要Bootstrap](http://www.labazhou.net/2014/10/you-dont-need-bootstrap/)》</blockquote>


我们的设计师努力输出最符合业务的布局，不应该被我们选择用在前端的什么框架束缚住。Bootstrap借助4个预定义的breakpoint应用一个12列的布局，此范围之外的操作都不是直接的。做为一个前端专业人士，用自定义breakpoint来实现适应内容的自定义设计是更快的，而不是一个又一个地覆盖框架代码里的class。

下面的摘录适合那些没有太多前端经验的开发者：


<blockquote>Twitter Bootstrap快速、易于实现，结果，创新经常受到妥协。对抗传统的创新设计难以在Bootstrap的结构化环境下实现，况且你有严格的时间限制。
------《[5 reasons not to use Bootstrap](http://www.zingdesign.com/5-reasons-not-to-use-twitter-bootstrap/)》</blockquote>


[![自定义设计遭遇Bootstrap的扁平化](http://www.labazhou.net/wp-content/uploads/2014/10/custom-design-bootstrap.jpg)](http://www.labazhou.net/wp-content/uploads/2014/10/custom-design-bootstrap.jpg)

Vanilla Bootstrap已经完全地测试了浏览器和设备，关于什么支持、什么不支持也有大量的文档。然而，如果你在其之上开发了一个自定义设计，你将把自己推向浏览器怪癖和bug的境地，Bootstrap则解决了这些问题。你不得不明白如何阻止或应对它们，一个前端专业人士将能够从头开发几乎完全跨浏览器兼容的、自定义实现。

本文不是要帮你决定在项目里用不用Bootstrap，而是解释我为什么不在Forward Partners使用它。总之，我在少量场景下使用，自定义的线上站点除外。

原文地址：[http://fourword.fourkitchens.com/article/you-dont-need-bootstrap](http://fourword.fourkitchens.com/article/you-dont-need-bootstrap)
