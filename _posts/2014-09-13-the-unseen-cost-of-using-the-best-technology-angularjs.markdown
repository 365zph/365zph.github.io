---
author: viviworld
comments: true
date: 2014-09-13 05:58:36+00:00
layout: post
link: http://www.labazhou.net/2014/09/the-unseen-cost-of-using-the-best-technology-angularjs/
slug: the-unseen-cost-of-using-the-best-technology-angularjs
title: 使用最好技术的不可见成本：AngularJS
wordpress_id: 1062
categories:
- 编程
- 软件
tags:
- Adsense
- ajax
- AngularJS
- Clicktale
- google
- javascript
- SEO
- 程序员
---

很多企业家都对 使用最好的技术代表着什么 存在盲区：他们认为这更像是新技术将提供的功能，需要多长时间完成编码，以及是否值得。

他们常常忽略了基于公司能力去选择前沿技术的后果，而是雇佣、做SEO、兼容很多浏览器和集成通用插件。

我们雇佣的前端工程师建议了AngularJS，在做了研究之后，发现Google支持它，我们决定尝试。Ember.js貌似太新而没有太多的最新文档，我们听说，即便Backbone.js已经非常普遍了，AngularJS与Backbone.js相比，是更加优雅的解决方案。

这个决定让我们感到高兴，但是我们对于随之而来的、没有预料到的、很多不同问题感到吃惊，在我们首次决定使用AngularJS时，并没有小心权衡。下面是你采用AngularJS之前应该考虑的一些地方，而实际上适用于任何新的前沿技术。


### 1）低版本浏览器


AngularJS不支持低于8的IE版本。目前，我们的网站不支持IE8和IE9，我们仍然在尽量解决中。搞清楚IE10当中的bug花了不少时间。所有IE用户占到了25%流量，IE8和IE9大约占到了这部分流量的80%。还不能使用我们网站的用户是相当多的，严重影响了我们的转化率。

面向IE8和IE9这些低版本浏览器编程已经足够困难了，在那些浏览器很少能处理好CSS怪异现象的前提下，增加一个新的前沿前端技术也就成了相当巨大的障碍。


### 2）SEO


如果你有完全用AngularJS实现的app，那意味着相当有可能你的源代码只是JavaScript文件。Google还没有找到抓取动态内容的有效方法，如果你不做出一些调整，你可就要倒霉了。

我们有了存在于AngularJS SPA（单页应用程序）之外的“混合”页面，它们是Django（我们在用Python框架）里的普通页面，内容是可被爬虫抓取的。这些页面只在一个地方调用了AngularJS，那就是搜索框，当你搜索的时候，AngularJS会被调用。

这意味着我们有必要让一堆附属内容散落在中央AngularJS的app周围。

这也意味着在页头和页尾的某些代码需要被复制，因此当我们想增加一个类库或标签时，我们需要在两个地方增加。


### 3）Adsense、Clicktale以及很多类库都不能直接使用了


Adsense不能在载入动态内容的网站运行。事实上，做个变通方案，是可以让它成为可能（iFrame等等）的，但是违反了服务条款（TOS：terms of service）。这意味着，AngularJS以及使用了Ajax的任何东东，都不能直接使用Adsense了。

我稍微休息一会儿：是的，世界上最重要的在线广告领导者还没有找到一种在动态载入内容的网页上呈现广告的简单方法。而AngularJS是新兴的、通过Ajax载入动态内容的，肯定不可以了，Google也没有找到有效的解决方案也是让我颇受震动的。

Adnsense不能正常运行是因为它要等到DOM被构造好以后，才能基于网页内容实例化广告。它是在网页载入完成之后才执行的，但是对于AngularJS之类的“单页应用程序”，你从来不需要重新载入一个页面，所有内容都是动态载入的，在“页面”直接实现了无缝切换。

花了一整天找到的解决方案就是使用Doubleclick For Publishers【注2】，一个不同的Google产品，通过它来载入Adsense。一旦新的“页面”被载入，我们不得不“刷新”广告区域。这是个小伎俩，却是有效的。

真的花了好长时间才搞定的。

与Clicktale类似，我们使用软件监视用户会话并找到可用性问题。对于普通网页，你只需一段代码，但是对于我们的网站，我们不得不使用它们的特定API。

本来5分钟的事情，以色列的技术团队来来回回搞了一周。


### 4）程序员


很多程序员对新技术不了解，因此当雇人的时候，你不会有太多选择。

在我们发起了重要的合作伙伴关系的那一天，前端程序员离职了，我们才碰到了这个问题。我们招到了某个员工的一个白俄罗斯朋友，他实际上有对AngularJS贡献过源代码。他们从他的日程上抽出时间作为对我们的个人支持。但是我们说到的大部分人没有AngularJS经验，通常的反应会是“是的，我们正打算学习呢，因为它绝对是未来，但是我们还没有这方面的专家。”


### 总结


总之，在你面临使用AngularJS之类的新技术的选择时，你需要考虑的因素有很多，决不仅仅是“它是一个不错的框架”。你需要考虑招到人有多大难度，这个人要了解该框架，像SEO之类业务的其它方面的后果、广告集成以及跨浏览器兼容。

我们对AngularJS非常满意，因为我们有资金和时间来开发长期内可持续的功能，不过，它一定不适合每一个人。

当前沿技术引发的所有潜在复杂问题出现时，做为一家公司，要确信你有能力搞定。



	
  * 原文地址：[http://davidlitwak.com/the-unseen-cost-of-using-the-best-technology-angularjs](http://davidlitwak.com/the-unseen-cost-of-using-the-best-technology-angularjs)

	
  * 注1：Clicktale成立于2006年，相对于偏统计的流量分析工具，Clicktale偏向定性，它可以告诉使用者为什么网站转化率上升了，用户体验上升了？而不是简单的流量多少，流量产生时间和流量渠道。主要是因为Clicktale能够录制网站访客行为，将访客的一举一动全都录制下来，并且通过播放器完整地展示。除了视频录制，还包括热力图、转化漏斗、表单分析等强大功能。Clicktale追踪数据的技术属于Javascript标记，类似市场上通用的跟踪，例如Adobe Sitecatalyst, google analytics, 百度统计，CNZZ等，代码安装非常简单和方便。[http://www.clicktale.com](http://www.clicktale.com)

	
  * 注2：DoubleClick for Publishers(DFP)是Google的第三方广告托管解决方案，前身为Google Ad Manager，集成DoubleClick的DFP产品之后推出正式的DFP系统。[https://www.google.com/dfp/](https://www.google.com/dfp/)


