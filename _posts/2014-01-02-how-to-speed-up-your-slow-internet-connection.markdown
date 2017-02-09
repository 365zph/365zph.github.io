---
author: viviworld
comments: true
date: 2014-01-02 02:03:34+00:00
layout: post
link: http://www.labazhou.net/2014/01/how-to-speed-up-your-slow-internet-connection/
slug: how-to-speed-up-your-slow-internet-connection
title: 怎么加速缓慢的网络连接
wordpress_id: 115
categories:
- 浏览器
- 网络
tags:
- chrome
- ddwrt
- firefox
- ie
- 路由器
---

对于大部分人来说，家庭网络连接比十年前快了很多，除了今天某些地方5M连接速度好像非常快了。不要放弃互联网视频------你可以做一些事情来最大化性能，很多地方不用花一分钱！


### 第一步：一个好的路由器


不过，首先需要注意的地方，需要花一点钱：好的路由器。

你的ISP可能给你提供了一个基本的无线路由器，或许你在黑色星期五抢的价值30美元的路由器，它很可能不会使连接发挥全部潜力。投资一款有质量的路由器会改变很多。

找一个能够提供包优先和QoS功能【注1】的路由器，你就可以选择哪个程序和电脑可以优先占用可获得的带宽，还可以限制它们。比如，你不想让bt下载一整天全速运行。

对于DIY类型，像[Tomato USB](http://tomatousb.org/)、[DD-WRT](http://www.dd-wrt.com/site/index)等第三方路由器防火墙值得一看。只要路由器有兼容芯片组，你就可以刷自定义防火墙，增加大量功能（包括QoS）而不用花大钱从商店里搞到那些饱受摧残的路由器。有些公司甚至卖预装好DDWRT的路由器。


### 第二步：


技术上的设置也可以试试，包括更改DNS，运行一下Gibson Research的 [DNS benchmark tool](https://www.grc.com/dns/benchmark.htm)，它会很快显示出向你电脑响应最快的DNS。假定你了解如何访问路由器管理界面，你可以忽略下面的，插入它列出的两个最好的DNS，就可以节约几毫米的lookup时间。

另外，缓存代理服务器也可以加速冲浪。Squid不错，可以自由选择------你不必准备一个空闲的Linux机器。有[windows可执行程序](http://squid.acmeconsulting.it/)，这得感谢Acme Consulting团队。

如果不是多个终端同时连接，ol的[WinGate](http://www.wingate.com/)也是不错的选择，免费版最多支持3个并发连接，还比安装Squid简单。

为什么要用缓存代理呢？它能够加速经常被使用的资源的访问速度，每个终端都能获益。


### 第三步：浏览器


现在该看看浏览器了？所有主流浏览器甚至比他们去年版本改进不少，但哪一款是最好的呢？没有适合所有人的浏览器，因此最好的做法就是保持开放心态，多试试。

例如，[Opera](http://www.opera.com/)平滑的[越野模式](https://www.geek.com/android/chrome-for-android-beta-gets-data-compression-boost-1541977/)（注2）能够让我们在糟糕的网络连接情况下体验到更快速度。模式开启时，你请求的网页首先被压缩，然后被Opera的远程代理服务器优化。图片质量会被降低，不可能事事如意，不过速度上去了，这些牺牲是值得的。

[Google Chrome](http://google.com/chrome)也提供了很多提升速度的功能。Chrome后端[预先获取](http://www.geek.com/news/google-chrome-13-adds-instant-pages-and-print-preview-1408839/)它认为你将要访问的内容，它也非常擅长预测你将要点击哪里，只是它想给你惊喜而没有事先告诉你，毕竟Google知道太多太多Chrome用户的浏览习惯。

[IE 11](http://www.geek.com/apps/whats-new-in-internet-explorer-11-1551121/)提供了类似的预测浏览、预先加载功能，使得访问大部分流行网站的速度和Chrome不分伯仲。

如果你喜欢自己动手，[Firefox](http://getfirefox.com/)或许是最好的选择。大量有用的扩展、可供测试的、长长的about:config页（仅仅确保做的改动对tab生效）帮助浏览器在缓慢网络连接时提升性能。


### 最后……


另一个值得关注的软件就是好的下载工具了。如果你经常下载大文件，你可以考虑安装有计划选定功能的软件。[Free Download Manager](http://www.freedownloadmanager.org/)不错，和[JDownloader](http://www.jdownloader.org/download/index)一样------仅仅需要确保搞到支持计划选定功能的扩展。

如果还要找加速的高级办法，你就要考虑租用一个VPS了。它们能够[极大地缩短传输时间](http://www.extremetech.com/computing/84240-faster-torrenting-with-a-vps-seedbox)，它们并不总是你想象的那么贵。

原文地址：[http://www.geek.com/apps/how-to-speed-up-your-slow-internet-connection-1580989/](http://www.geek.com/apps/how-to-speed-up-your-slow-internet-connection-1580989/)

注1：QoS：[http://zh.wikipedia.org/wiki/QoS](http://zh.wikipedia.org/wiki/QoS)
注2：越野模式：[http://www.cnbeta.com/articles/238282.htm](http://www.cnbeta.com/articles/238282.htm)
