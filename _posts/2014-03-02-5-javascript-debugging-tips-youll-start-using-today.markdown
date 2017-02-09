---
author: viviworld
comments: true
date: 2014-03-02 06:25:33+00:00
layout: post
link: http://www.labazhou.net/2014/03/5-javascript-debugging-tips-youll-start-using-today/
slug: 5-javascript-debugging-tips-youll-start-using-today
title: 你今天开始使用的5种JavaScript debugging技巧
wordpress_id: 365
categories:
- 测试
- 编程
tags:
- Audits
- chrome
- javascript
- YSlow
- 断点
---

我过去一直用[printf debugging](http://stackoverflow.com/a/189570/269666)，好像常常很快就可以解决我的bug。

有时候需要更好的工具，下面是一些，我确定你会发现它们的好处：


### 1.debugger


我[以前提到过](http://berzniz.com/post/68001735765/javascript-hacks-for-hipsters)，你能够在代码里用“debugger”声明来强迫产生一个断点。

需要一个有条件的断点吗？仅仅把它放在if语句里：

    
    if (somethingHappens) {
        debugger;
    }


需要记得上线之前移除它们。


### 2.Node变化时中断


有时候DOM仅仅有自己的行为。奇怪的变化发生时，很难找到问题的根源。

Chrome Developer Tools有一个超级有用的技巧来调试。这就是“Break on…”，通过右击“Elements” tab下的某个DOM节点，你就能找到它。

断点可以设置为：当节点被移除、节点属性发生变化或一个子节点发生变化时。

[![chrome break on](http://www.labazhou.net/wp-content/uploads/2014/03/chorme-break-on.png)](http://www.labazhou.net/wp-content/uploads/2014/03/chorme-break-on.png)


### 3.Ajax断点


XHR断点，或我的叫法Ajax断点，允许在期望的Ajax调用产生时产生中断。

当调试你的web app的网络时，这是一款令人惊奇的工具。

[![ajax  断点](http://www.labazhou.net/wp-content/uploads/2014/03/ajax-break-on.png)](http://www.labazhou.net/wp-content/uploads/2014/03/ajax-break-on.png)


### 4.模拟不同的移动设备


Chrome增加了有趣的移动模拟工具，让你的生活更加轻松。

在除了Console tab之外的其他任何tab点击esc键就可以找到，选择你想模拟的设备。

你不会得到一个真实的iPhone，但是规程尺寸、触摸事件和用户代理都为你模拟好了。

[![chrome模拟设备](http://www.labazhou.net/wp-content/uploads/2014/03/emulate-device.png)](http://www.labazhou.net/wp-content/uploads/2014/03/emulate-device.png)


### 5.用Audits提高你的网站


[YSlow](http://developer.yahoo.com/yslow/)是一个伟大的工具。Chrome在开发者工具下提供了类似的工具，叫Audits。

快速测试你的网站，得到用于优化的有用的、实际的建议。

[![chrome audits，类似slow](http://www.labazhou.net/wp-content/uploads/2014/03/chrome-audits.png)](http://www.labazhou.net/wp-content/uploads/2014/03/chrome-audits.png)

还有吗？

如果没有这些工具，我无法想象该如何开发。我一找到就公布出来，敬请期待。

原文地址：[http://berzniz.com/post/78260747646/5-javascript-debugging-tips-youll-start-using-today](http://berzniz.com/post/78260747646/5-javascript-debugging-tips-youll-start-using-today)
