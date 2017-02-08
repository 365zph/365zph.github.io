---
author: viviworld
comments: true
date: 2013-12-28 08:46:27+00:00
layout: post
link: http://www.labazhou.net/2013/12/say-welcome-to-someone-who-repalces-you/
slug: say-welcome-to-someone-who-repalces-you
title: 如何给接手你工作的下一个家伙（或女士）说”欢迎！“
wordpress_id: 74
categories:
- 编程
tags:
- 注释
- 程序员
---

这里有一些方式：

在每个代码文件最上面插入30，50，甚至1000空行；
------为了增加影响，在最后增加一行注释：某天可以移除上面的空行。
------最好的注释：上面那些行数是给将来给‘更聪明’、‘更有效率’的代码保留的。

你可以不到处加注释，但是应该随处放置一些”hey“、”new guy“、”考虑在这里添加注释“之类的话。写一个只在第4个月份的第3个星期二才运行的Do\While循环，或者当‘Blue’从列表选出来时，要增加一行注释”需要把‘Blue’加到列表中“（尽可在那儿写一行Application.DoEvents()，如果你高兴）（技术上说，这是有破坏性的。因此使用一个计数器来遍历一个最大的数，我想到了1000000）

放置30多个或300多个”Start“类文件，.NET先调用一次，然后生成并调用第二个，接着第三个，一直到第N个。最后一个类的顶部加行注释：每天重新开始。或者弄一个介于1和N之间的随机数选择器，然后调用随机的类，带上注释：”希望最终的第N个类能够被调用“。（技术上也是不妥的，因此使用计数器避免访问刚从调用过的文件。

放一个文件名为”CriticalComponentTester.exe“的可执行程序，至少能弹出一个写有“喝杯咖啡，然后开始测试，伙计（或女士）！”的窗口。

在最重要的程序文件顶部加注释：接手别人的代码就像接管一艘海盗船，开启寻宝之旅吧！地图？地图呢！？

原文地址：[http://www.codeproject.com/Lounge.aspx?msg=4727990#xx4727990xx](http://www.codeproject.com/Lounge.aspx?msg=4727990#xx4727990xx)
