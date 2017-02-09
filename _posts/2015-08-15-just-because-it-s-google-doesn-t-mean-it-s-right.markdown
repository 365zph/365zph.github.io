---
author: viviworld
comments: true
date: 2015-08-15 13:59:01+00:00
excerpt: 如果数据使用不当，就会成为极具破坏力的工具，比如 Google 最近关于iOS 上  Google+ 的、移动 web 插页式广告的试验。
layout: post
link: http://www.labazhou.net/2015/08/just-because-it-s-google-doesn-t-mean-it-s-right/
slug: just-because-it-s-google-doesn-t-mean-it-s-right
title: Google 不总是对的
wordpress_id: 2384
categories:
- 杂项
tags:
- APP
- google
- ios
- 插页式广告
---


	
  * 原文地址（original source）：[https://medium.com/@alexaustin/just-because-it-s-google-doesn-t-mean-it-s-right-5fe27b912f28](https://medium.com/@alexaustin/just-because-it-s-google-doesn-t-mean-it-s-right-5fe27b912f28)

	
  * 作者（author）：[https://twitter.com/illustriousalex](https://twitter.com/illustriousalex)





* * *



[我热爱数据，以及用数据所讲述的故事](http://www.labazhou.net/2015/05/data-verb/)。可能有很多。在 Branch 两月一次的董事会之前，实际上我在期盼着周末，因为我能够连续坐 48 小时，通过想象和情节来编写我们的商业故事。

不幸的是，如果数据使用不当，就会成为极具破坏力的工具，比如 Google 最近关于iOS 上 Google+ 的、移动 web 插页式广告的试验。如果你还没有看到这篇文章，[可以从这里看到](http://googlewebmastercentral.blogspot.co.uk/2015/07/google-case-study-on-app-download-interstitials.html)。那篇文章已经产生了很多流量，因此评估其有效性才是公平的。

[![Google+ 的、移动 web 插页式广告的试验](http://www.labazhou.net/wp-content/uploads/2015/08/full-page-interstitial-338x600.png)](http://www.labazhou.net/wp-content/uploads/2015/08/full-page-interstitial.png)



为了描述错误的地方，让我为这次试验的总结先做一次快速摘要，便于我们能够理解一致：

_**问题描述**_：69% 的用户到达插页式广告页面后，会放弃该网站；9% 的用户点击了 app，22% 的用户继续停留在移动网站上。

_**假设**_：当前的插页式广告把人赶走了

_**试验**_：关闭插页式广告

_**测量反馈**_：iOS 总的安装量浮动为 -2%，单日移动网站总的用户增加了 17%。

文章作者从这些数据得出结论，插页式广告应该被移除。下面是置顶评论：


<blockquote>「换句话说，没有人喜欢下载 app 的插页式广告，因此不要这样做。」</blockquote>


就我个人而言，我讨厌这些普通的插页式广告（因此我乐于看到它们被移除），不过，这是一次真正糟糕的试验。他们根据收集到的这些数据得出来这样的结论是不正确的。对于此次调整所带来的直接影响，测量反馈只是排在第二位和第三位的代理，也可被很多不同的、完全不相关的因素影响（这次试验当中的、受欢迎的 Google+ 文章）。比如，iOS 安装总量中，有多少是和插页式广告正相关的？貌似它在 App Store 流量中的占比非常小，这样其它 app 安装源的噪音就很容易淹没掉这次试验的信号。

整篇文章最让人不爽的地方，在于该试验没有关联到任何业务目标上。Google+ 如何测量产品成功？顺便提一句，按照文中提到的，貌似团队认为移动网站上的单日 UV 的价值等同于 iOS 上 app 的安装量。在 Branch，关于将移动 web 流量转化为 app，我运作过数以千计的 app，请相信我，我能够向你担保，任何有着正常理智的人从来不会认为，移动 PV 等同于 app 安装。

为了正确地操作这次试验，首先，你需要理解你的目标是什么。总之，大多数业务已经发现，移动 web 用户的留存、转化比例不等同于原生 app 用户的比例。随便问个同时拥有移动网站和 app 的人，你将能听到同样的情形。这就是让人厌烦的插页式广告出现在重要位置的原因。每个人都在尽力把毫无价值的移动 web 流量转化为高价值的 app 用户，且不计成本。对于某些 app，对于用户的终极目标就是完成一次购买。对于其他人而言，其目标就是上传一张照片。换句话说，为了这次试验行得通，你不得不挑选一种向下漏斗标准做比较。

其次，你的试验需要仅仅比较能够看到插页式广告的最初来源的流量。你不能只是局限于发生在那天的、关键事件的总体数量，因为他们可能起源于很多地方。你需要将其归因于你正在测试的清晰渠道。简单地说，你需要比较这两个数字：



	
  1. 从插页式广告的 PV 到移动网站+移动 app 上关键指标的基线转化。

	
  2. 从没有插页式广告的 PV 到移动网站+移动 app 的、同样的关键指标的转化。


最后，这次试验需要一个时间组件，这样你就能比较一个用户的总体时间价值。众所周知，原生 app 用户有更多的留存，因此你需要针对每次划分的总体留存来测量总体影响。

在 Branch，我们创建了全栈的、可追踪的、深度链接的[智能 app banner](https://dev.branch.io/recipes/app_download_banner/)，支持公司运行这些种类的试验，以真正地测量对流量及其业务的直接影响。我们免费提供这种服务，因此我的建议是，你自己运行这种测试。不要使用 Google 博客文章里的数据来做任何商业上的决定。
