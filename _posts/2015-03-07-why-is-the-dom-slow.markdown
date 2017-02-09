---
author: viviworld
comments: true
date: 2015-03-07 13:38:43+00:00
layout: post
link: http://www.labazhou.net/2015/03/why-is-the-dom-slow/
slug: why-is-the-dom-slow
title: 为什么DOM是慢的？
wordpress_id: 1681
categories:
- 浏览器
- 编程
tags:
- AngularJS
- css
- javascript
- jquery
- ReactJS
---

原文地址（original source）：[https://news.ycombinator.com/item?id=9155564](https://news.ycombinator.com/item?id=9155564)

有时候我想写一篇宏大的、详实的博文，来全面提供下这个话题的数据。不幸的是，我把这方面的数据通通留在了我的前东家（Google）那儿，我还没有时间编写代码以编译新数据。

简单地说，DOM 不慢。添加和删除 DOM 节点属于一些指针交换，与设置 JS 对象里的属性有着很大的不同。

然而，layout 是慢的。只要你接触到 DOM，你就对整个树做了些许改动，它会告诉浏览器它需要确定哪里重新绘制。当 JS 把控制权交还给浏览器后，它会调用它的layout算法（或更加技术性地讲，它调用 CSS 重算算法，然后layout、然后重绘、然后重新组合）来重新绘制屏幕。layout 算法相当复杂 ------为了理解某些规则，可以阅读 CSS 说明------这意味着它经常不得不做一些非局部决定。

更糟糕的是，layout 在处理某些属性时，是同步触发的。像`getComputedStyleValue()`，`getBoundingClientWidth()`，`.offsetWidth`，`.offsetHeight` 等属性是很容易碰到的。完整列表请参考这里（很可能过期了几年了）：[http://gent.ilcore.com/2011/03/how-not-to-trigger-layout-in-webkit.html](http://gent.ilcore.com/2011/03/how-not-to-trigger-layout-in-webkit.html)

鉴于此，很多 [Angular](http://www.labazhou.net/2014/09/the-unseen-cost-of-using-the-best-technology-angularjs/) 和 JQuery 代码慢得愚不可及。一次 layout 将摧毁你在移动设备上的整个框架预算。当我测量 2013 年的 Google Instant 时，它在移动设备上的一次查询中引发了 13 次 layout，锁住屏幕的时间差不多有 2 秒。（从那以后速度得到了提升）

React 对于加速 layout 没有帮助，如果你想要移动 web 浏览器上的平滑动画效果，你将需要借助其它技巧，比如限制你在一个框架里做的所有操作，这些操作可以在 GPU 里执行。但是需要确保的是，每一次更新网页状态时，最多有一次 layout 操作。这经常是基于现状的一种改善。

（通常的免责：这都是 2014 年初的情况了，不过浏览器变化太快，它可能与目前不同也未可知。主流 JS 框架的大多数目前可怜的性能，都是因为它们建立在一种假设上，那就是浏览器性能是针对于2008年，而不是现在。）
