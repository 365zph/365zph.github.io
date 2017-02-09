---
author: viviworld
comments: true
date: 2016-01-01 11:41:09+00:00
excerpt: 对 Ilya Grigorik 的采访摘录，优化网页性能：压缩、优化图片、不传输不必要的资源。渐进式渲染及 Chrome 的 DevTools、WebPageTest
  的用法。
layout: post
link: http://www.labazhou.net/2016/01/developers-what-you-should-know-about-web-performance/
slug: developers-what-you-should-know-about-web-performance
title: 开发者应该了解的 web 性能
wordpress_id: 2957
categories:
- 浏览器
- 编程
tags:
- Amazon
- chrome
- css
- DevTools
- javascript
- SpeedCurve
- TTFB
- WebPageTest
- WordPress
- 渐进式渲染
---


	
  * 原文地址（original source）：[https://medium.com/@christophelimpalair/developers-what-you-should-know-about-web-performance-550cef1040d8](https://medium.com/@christophelimpalair/developers-what-you-should-know-about-web-performance-550cef1040d8)

	
  * 作者（author）：ScaleYourCode（[@ScaleYourCode](https://twitter.com/ScaleYourCode)）





* * *



网站的快和慢有什么区别呢？

存在一种正确答案吗？

没有，很不幸，还没有。原因在于网站具备很多因素，每种因素都有可能减慢网站。因此，本文不会给你提供一份需要完成的清单，而是打算解释清楚，某些因素是怎样减慢网站的，以及相应地你能做些什么。

正如谚语所说的：


<blockquote>授人以鱼，不如授之以渔；授人以鱼只救一时之及，授人以渔则可解一生之需。</blockquote>


除了让你给脚本增加 “async” 标签，或按照特定顺序布局页面之外，我还打算解释这些修改所带来的差异。这样，你就能折腾你的应用程序，并确认哪些修改是有用的。

顺便说一句，这些提示来自于我和 Ilya Grigorik 的[一次精彩交谈](https://scaleyourcode.com/interviews/interview/20)。

介绍下 Ilya Grigorik，他是 [W3C Web Performance Working Group 的联任主席](http://www.w3.org/2010/webperf/)，Google 的 web 性能工程师。嗯，他对性能颇有见地。


### 「每个人都应该做的一件事就是加速页面载入」


正如我刚才提过的，不存在这样的事情。web 有些出乎意料地复杂。使页面载入速度降低的现象，对你而言，或许不能成为专注的正确标准！（我们稍后再细谈）

然而，有些相当重要的因素，通常会带来显而易见的不同。你之前或许碰到过，但是或许不理解它们为什么重要。


#### 1.压缩


用 [gzip](https://developers.google.com/speed/docs/insights/EnableCompression?hl=en) 压缩传输 HTML、CSS 和 JavaScript，减少了需要流经线缆的字节数。这可以显著减少下载资源的时间。浏览器渲染页面，离不开 HTML 和 CSS，因此我们想尽快下载这些资源。


#### 2.优化图片


我有个朋友，他给客户搭建 WordPress 网站，有很多网站常常上传大量图片，我最近和他聊了一次。他遇到了一个问题，客户直接把相机里的图片上传到他们的网站。

手机拍摄的照片超过 1MB。就算你用 [CSS](http://www.labazhou.net/2015/10/things-to-avoid-when-writing-css/) 调整大小，仍然需要通过线缆下载这副非常大的图片。网速慢的用户需要等待很长时间才能打开。

幸亏有应付的方法。[我有段节目](https://scaleyourcode.com/interviews/interview/19)和优化图片相关。如果你还没有看过，我强烈推荐给你。


#### 3.不要传输不必要的东东


查看不同页面里的脚本和 CSS 文件，自问一下，这些文件对于页面是不是真的需要。你很可能找到一些文件，它们被添加上去之后就再没去掉。

插件在这方面的表现，真的很糟糕。我接触的相当一部分 ebordPress 网站，载入了一大堆 CSS 文件，其中有一半文件在某些页面根本用不到！很多非 WordPress 网站也有类似现象。我早些时候检查 [scaleyourcode.com](http://scaleyourcode.com/) 上的某些页面时，也发现它们正载入一个不必要的脚本。

清除脚本或样式表，会让人害怕。如果它对于那个页面真的是必需的、只是你不记得了，该怎么怎么办？有一些工具可以帮我们确认，推荐 DevTools（在 Audits 下）。

你能看出这些优化措施之间的共同点吗？它们都减少了我们需要传输的字节数。


### 渐进式渲染（Progressive rendering）


你需要尽早将 HTML 字节给到浏览器。

比如：一个请求进来了，（理想状态下）你的数据被缓存起来，因此服务器能够快速获取。然后，浏览器开始解析数据，并在屏幕上呈现出来。

我刚才提到了，页面载入时间可能不是你需要专注的性能标准，这得感谢[渐进式渲染](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/?hl=en)。

[caption id="attachment_2965" align="alignnone" width="600"][![渐进式渲染（来源）](http://www.labazhou.net/wp-content/uploads/2016/01/1-xnaJ7WfFrx7no4UUjbgRbw-600x295.png)](http://www.labazhou.net/wp-content/uploads/2016/01/1-xnaJ7WfFrx7no4UUjbgRbw.png) 渐进式渲染（[来源](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/?hl=en)）[/caption]

页面可以庞大，不过，只要你在短时间内（最好少于 1 秒）呈现给用户一些内容，他们仍然觉得载入很快。

Amazon 在这方面就做得不错：

[caption id="attachment_2958" align="alignnone" width="600"][![Amazon 的渐进式渲染](http://www.labazhou.net/wp-content/uploads/2016/01/1-cEKyzvmWUarqtRos1SccwQ-600x166.jpeg)](http://www.labazhou.net/wp-content/uploads/2016/01/1-cEKyzvmWUarqtRos1SccwQ.jpeg) Amazon 的渐进式渲染[/caption]

对于此次 [WebPageTest](http://www.webpagetest.org/)，在 1.5 秒就得到了第一屏，但是你能看到，它没有包含所有内容。它包含的内容足以让你开始浏览页面、或查看假日交易。

然后，到 3.5 秒，另一部分载入了更多交易。到 6.5 秒，一些东西仍然在载入！事实上，整个页面载入的完成一直持续到 18 秒。你能等那么长时间吗？我表示怀疑！

如果 Amazon 专注于最慢的页面载入，那么一定有人被激怒。他们却专注于在最早的 packet 里发送最重要的字节。再进一步，他们可能在[第一个 packet 里塞满最重要的字节](https://plus.google.com/+IlyaGrigorik/posts/GTWYbYWP6xP)。我敢打赌，他们还专注于尽快地为你发送那些字节。

这就是 **TTFB** (Time To First Byte) 【注1】 的由来。

当浏览器发起一个页面请求时，它就处于等待响应的状态。TTFB 代表了它需要多长时间才能收到第一个响应的字节。这个时间不但代表了你的服务器产生响应所需要的时间，而且意味着经过线缆传输所需要的时间。

[![Time to First Byte (TTFB) ](http://www.labazhou.net/wp-content/uploads/2016/01/1-gknxv-NMukjdTu80j0JLtQ-600x450.jpeg)](http://www.labazhou.net/wp-content/uploads/2016/01/1-gknxv-NMukjdTu80j0JLtQ.jpeg)

这张图有着非常快速的 TTFB。如果你去网上逛逛，就能看到不同的 TTFB，你看到的情况类似于下图：

[![TTFB，DevTools](http://www.labazhou.net/wp-content/uploads/2016/01/1-gZo0PKbk6t-yIGaiD6pEKA-600x346.png)](http://www.labazhou.net/wp-content/uploads/2016/01/1-gZo0PKbk6t-yIGaiD6pEKA.png)

为什么会是这种情况，我们该如何最小化该时间呢？你应该专注对其优化了吗？不错的问题，我就此[准备了更多资料](https://scaleyourcode.com/blog/article/27)。

如果你有兴趣了解更多信息，那么，请参考 Steve Souders 的[精彩演讲](https://www.youtube.com/watch?v=f5_iAzS3WMQ)，谈到了用来测量的性能标准。页面载入时间不总是最好的标准。


### 能让内容更快呈现的其它因素？


既然我们有了更快的 TTFB，那么每个地方都会极速呈现吗？不一定，我们看看关键呈现路径。

关键呈现路径是浏览器为了得到 HTML、构建 DOM、得到样式信息、执行关键的 JavaScript 以及绘制内容、而不得不执行的步骤顺序。

[![关键渲染路径](http://www.labazhou.net/wp-content/uploads/2016/01/1-0VCyTAg5UsCYXLPERwTfGw-600x240.jpeg)](http://www.labazhou.net/wp-content/uploads/2016/01/1-0VCyTAg5UsCYXLPERwTfGw.jpeg)

天哪，要做的工作真不少呀。

这就是我们需要慎重对待它的原因。HTML、CSS 和 JavaScript 越多，需要的时间就越长。当载入 JavaScript 文件时，添加 async 标签，原因就在于此。

当浏览器遇到 JavaScript 时，它可能不知道这里的 JS 是否要改变 DOM。因此，它不得不假定它会改变，然后它阻止渲染，直到 JavaScript 完成了执行过程。如果增加了 async 标签，相当于向浏览器保证，该 JS 对于页面不是关键的，因此浏览器可以继续渲染，而不必等待 JS 执行完成。

如果碰到修改页面的脚本，那么是否意味着不应该异步呀？可能。尽管如此，即使你异步化了修改页面的脚本，那么从用户视角看，这种做法也是实用的。用户能够看到内容，并开始产生交互。的确，某些地方或许无法呈现，也可能需要多等一会儿。当然，这都取决于你的应用程序，因此尝试一下，看看是否满足你的需求。

关键路径对于尽可能快地接收字节如此重要，原因在于你能够越早地开始处理整个过程，就能越快地完成。关于优化关键渲染路径，请[参考这里](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path?hl=en)。


### 你该怎样测量异步（或其它优化方式）对应用程序的好与坏？


有个不错的测量工具，[WebPageTest](http://www.webpagetest.org/)。你能够得到各种有用信息，包括幻灯片视图。幻灯片视图就是我刚才用以展示 Amazon 页面的可视化过程。你可以用在你的网站上，并列比较有无异步的差异。

直到最近，DevTools 实现了自己的幻灯片视图。

打开 Chrome DevTools，点击 TimeLine -> 开启 Screenshots -> 重新载入页面。

你就能看到页面载入过程的截屏了。不错吧？

[![Chrome’s DevTools](http://www.labazhou.net/wp-content/uploads/2016/01/1-OFIPn8Ew59ykH9kif0Aqgg-600x213.jpeg)](http://www.labazhou.net/wp-content/uploads/2016/01/1-OFIPn8Ew59ykH9kif0Aqgg.jpeg)

现在，你可以：



	
  1. 切换你的网络速度（记住，不是每个人都有超快的互联网）

	
  2. 查看幻灯片视图

	
  3. 把脚本改成异步（或做出其它调整）

	
  4. 对比幻灯片


[caption id="attachment_2962" align="alignnone" width="600"][![你可以在 DevTools 里调整网速](http://www.labazhou.net/wp-content/uploads/2016/01/1-gtwBFvbS2Ut_OGUwO5_31A-600x297.jpeg)](http://www.labazhou.net/wp-content/uploads/2016/01/1-gtwBFvbS2Ut_OGUwO5_31A.jpeg) 你可以在 DevTools 里调整网速[/caption]

另一个工具是 [SpeedCurve](https://speedcurve.com/)，这是我最近无意间发现的。它由两个聪明的家伙开发：Mark Zeman 和 Steve Souders，看起来很有帮助。


### DevTools 非常优秀了，我们怎样才能更好地理解其用法呢？


难点在于增加了太多功能所不幸引起的副作用。

除了看上面的例子，我们开始学习并实践的更好方式是什么呢？对于怎样在实际网站中使用 DevTools，[Paul Lewis](https://www.youtube.com/watch?v=QU1JAW5LRKU) 和[其他人](https://www.youtube.com/watch?v=g0g4ML4nhPg)已经体验了。这里是关于修复滚动性能问题的[极好例子](https://www.youtube.com/watch?v=F6pBKoTdE24&feature=youtu.be)。


### 更多


本文只是整个采访过程的简短摘要，我们在采访中深入了大量细节，涵盖了更多重要的主题（比如 HTTP/2 有什么不同，以及我们是否仍然需要最小化和串连）。

你可以在[这里](https://scaleyourcode.com/interviews/interview/20)阅读全部摘要或收听采访。如果你需要，请参考下面的视频：[https://youtu.be/Aayh2FAYGqc](https://youtu.be/Aayh2FAYGqc)


### 注释

* 注1：TTFB，是最初的网络请求被发起到从服务器接收到第一个字节这段时间，它包含了 TCP连接时间，发送HTTP请求时间和获得响应消息第一个字节的时间。[http://baike.baidu.com/view/4538320.htm](http://baike.baidu.com/view/4538320.htm) 
