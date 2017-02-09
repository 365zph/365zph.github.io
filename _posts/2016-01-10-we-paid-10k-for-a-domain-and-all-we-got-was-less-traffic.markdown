---
author: viviworld
comments: true
date: 2016-01-10 12:44:36+00:00
excerpt: 关于整个 Google Apps 的次级域名工作原理，要提前多做研究，搞清楚它对你的配置有多大负面影响。在切换域名时，确保你看懂了 Google
  文档，并准确理解在你切换之前、要做的事情会产生怎样的潜在影响。
layout: post
link: http://www.labazhou.net/2016/01/we-paid-10k-for-a-domain-and-all-we-got-was-less-traffic/
slug: we-paid-10k-for-a-domain-and-all-we-got-was-less-traffic
title: 一万美元买个域名，换来的却是低流量
wordpress_id: 2998
categories:
- 编程
- 网络
tags:
- email
- Google Apps
- https
---


	
  * 原文地址（original source）：[https://medium.com/swlh/we-paid-10k-for-a-domain-and-all-we-got-was-less-traffic-536554ca50d8](https://medium.com/swlh/we-paid-10k-for-a-domain-and-all-we-got-was-less-traffic-536554ca50d8)

	
  * 作者（author）：Crew（[@pickcrew](https://twitter.com/pickcrew)）





* * *



[caption id="attachment_2999" align="alignnone" width="600"][![By Angus Woodman | Originally appeared on the CREW blog.](http://www.labazhou.net/wp-content/uploads/2016/01/1-YhHJQaBBgER2lTn5JzF-Ng-600x100.jpeg)](http://www.labazhou.net/wp-content/uploads/2016/01/1-YhHJQaBBgER2lTn5JzF-Ng.jpeg) By [Angus Woodman](https://twitter.com/angusw) | Originally appeared on the CREW blog.[/caption]

一年半前，我们公司从 ooomf [更名为](http://backstage.crew.co/story/) Crew。

我们要找的名字，除了可以真正地拼读，还要和我们公司做的事情关联起来。

当然，随着我们公司名字的变化，我们也想拥有 crew.com 域名，不幸的是，[一家流行的服装零售商](http://gap.com/)已经注册了，因此我们不得不选择另一个域名。

最终，我们想到了一个域名：


<blockquote>“pickcrew.com”</blockquote>


不错，很直接，还是一个 .com 域名，比较适合我们。但对我而言，它更像是「Pit Crew」[note]指 F1 赛场的后勤维修团队[/note]（很可能是因为我看了太多的摩托车赛事）。

随后，一名有爱的绅士和我们取得了联系，他有一个更短的域名，还是我们的粉丝，只要价格合适，我们就能拿到。新域名是：


<blockquote>“crew.co”</blockquote>


我们之前没有考虑过 .co 域名，但是你懂的：当机会来敲门时，很可能是时候改变你的初衷了。

[![1-xC9buFyUdZXBY-mum4_R5g](http://www.labazhou.net/wp-content/uploads/2016/01/1-xC9buFyUdZXBY-mum4_R5g-600x450.gif)](http://www.labazhou.net/wp-content/uploads/2016/01/1-xC9buFyUdZXBY-mum4_R5g.gif)


### 我们想改变域名的原因


除了想要一个更为干净、简单的域名（它真地使用了我们公司的名字）之外，我们对于收到的如下邮件感到不爽：

[![email 中的称呼](http://www.labazhou.net/wp-content/uploads/2016/01/1-yLGOrHwlYOK40w-K4xmACQ.png)](http://www.labazhou.net/wp-content/uploads/2016/01/1-yLGOrHwlYOK40w-K4xmACQ.png)

我想，上图就是在冰冷的 email 里常见的问题。但是，我们私下也听到过，和我们公司关系很近的一个人说道：


<blockquote>“How’s Pick Crew going?”
“Umm…”</blockquote>


我们觉得，当弃用「ooomf」后，我们已经引起了各种名字混淆的噩梦。显然，不是这样的。

对于 crew.co，就不会引起公司名称方面的错误。虽然我们不过于依赖域名带来流量，但是一个简短好听的名字，不必时不时地去说清楚，总归是个好事。


### 我们决定其价值为一万美元的方式


为了这个闪亮的新域名，我们需要给出公平的价格，因此开始研究最近的一些类似交易。

[![域名交易列表](http://www.labazhou.net/wp-content/uploads/2016/01/1-sDWCVXLw6XbeHs9g9EdrWQ-600x457.png)](http://www.labazhou.net/wp-content/uploads/2016/01/1-sDWCVXLw6XbeHs9g9EdrWQ.png)

根据上面的数字，我们打算给出的价格是一万美元。我们预先达成共识，这个价格很公平了，拒绝任何形式的讨价还价。

下面是我们发送的实际 email：

[![email 截图](http://www.labazhou.net/wp-content/uploads/2016/01/1-GlLrWhOXDgh2SC4H2kBVg-600x197.png)](http://www.labazhou.net/wp-content/uploads/2016/01/1-GlLrWhOXDgh2SC4H2kBVg.png)

成交。太棒了，新域名。

我们先冷静一下，看看我的新 email 地址：[angus@crew.co](mailto:angus@crew.co?subject=I%20like%20antelopes%20and%20getting%20caught%20in%20the%20rain)

啊，看着就舒服。（你自己试着发个邮件，我应该会有回信的！）


### 痛苦时刻：迁移域名的前后经过


如果你曾经迁移过带有一定流量的域名，你将理解它有多么折腾。

从 ooomf 切换到 Crew 算作大折腾了，因为我们同时改变了公司名字和域名。为了一切顺利，我们周日晚上都在公司集合，一个白板接着一个白板地列出带有旧域名的相关地方，然后开始核实。工作量巨大，但是我们搞定了，吃完蛋糕，就下班了。

难道切换域名就这么简单……它有多难呢？


### 加起来，有很多个 $5 ------我们的第一个错误


我们使用 Google Apps 管理 email 和云端文档（很可能你也这么做）。每个人、每个月的成本为 $5。既然启用了新域名，我们不得不为每个人创建新的 Google Apps 账号。当然，我们仍然需要旧账号，email、日历历史、登录以及其它东西，即使我们删除旧 email 之后，他们也是需要记住的。

现在，我们这 20 个人有了另外的 email 地址。$5 x 20/月 x 12月 = $1200/年，这是为了我们不再使用的 email 地址付出的代价！

我们本可以设置新账号，绑定好旧账号别名（这让我们节省 $1200），但是上次尝试之后，一些奇怪的事情发生了，我们不得不保持谨慎。

现在我们需要把新旧账号颠倒过来，给新账户设置别名，绑定到旧账户。迁移所有东西花了不少时间，我做为实验对象，弄丢了我以前的日历历史。现在我都不知道在 2014-10-24，我和谁开会了。真该死。

教训：关于整个 Google Apps 的次级域名工作原理，要提前多做研究，搞清楚它对你的配置有多大负面影响。


### 301 跳转：在你跳转之前，多检查两次。


真正有经验的人都会对你说：当你迁移网站时，请使用 301 跳转（嘿，我想，在我失去贞洁之前，我已经做了 301）。

如果你和我不太一样，那么你可能没有把少年时期的周五晚上花在阅读 html 状态码上，让我稍作解释：当你在浏览器敲入地址时，浏览器会从服务器得到一堆不同的状态。

200，表示「嘿，伙计，感谢你的来访，这是你需要的页面。」

301，表示「哦，对不起，伙计，那个页面已经提着行李，永远地离开了。」

302，表示「哦，对不起，伙计，那个页面今晚在某个地方崩溃了。」

（旁注：是的，web 服务器真的能够像你的大学室友一样聊天。）

301 和 302 两个状态的兄弟，都知道重定向地址，因此你仍然能够访问到你请求的页面。然而，二者存在非常重要的不同：

在 301 下，网站的 Google 搜索信用评级（比如链接权重）会跟着重定向，但是在 302 下就不会了。

因此，当把网站转移到新地址时，你不得不使用 301 跳转。当我们从 pickcrew.com 重定向到 crew.co 时，我们也是这样做的。

然而，你或许没有意识到（不幸的是，还有一些地方逃过了我们的预测），302 能够偷偷溜进得体的、干净的 301 跳转，从而破坏美味的 Google 信用评级。

对于我们具体的案例，当我们从 pickcrew.com 切换到 crew.co 时，我们也决定利用这次机会，从 http 切换到 https。就是这个「s」几乎害死我们。

我们首先注意到，我们的搜索流量遭受了巨大打击：

[![搜索流量的锐减](http://www.labazhou.net/wp-content/uploads/2016/01/1-VsVMqSiaCdoufI9CKCV5Lg-600x280.png)](http://www.labazhou.net/wp-content/uploads/2016/01/1-VsVMqSiaCdoufI9CKCV5Lg.png)

仔细分析，我们监控到了跳转，并有如下发现：


<blockquote>「这就是我们截图里出现的问题所在，但是由于当时我太惊讶而忘记截屏了。由两次跳转组成的一条链：首先是 301，随后是 302.」</blockquote>


再看下 Google 关于请求地址改变的文档，我们找到了：

[![google 对于网站迁移的介绍](http://www.labazhou.net/wp-content/uploads/2016/01/1-C7ExKKvESwzkEygEF8Bb1Q-600x105.png)](http://www.labazhou.net/wp-content/uploads/2016/01/1-C7ExKKvESwzkEygEF8Bb1Q.png)

我们当时（现在仍然）不确定，这两个问题当中，是哪个引起了流量问题。

好像都不适合我们，因为我们的 301 跳转是从 http 到 https，而非 http 到 http（以 302 方式跳转到 https）。

对于我们不太确定已经理解的东西，我们不再浪费时间研究了，而是匆忙返回到 http://，以确保它是纯洁的、原始的 301。

[流量（慢慢地）回升了](http://www.labazhou.net/2015/07/top-5-ways-to-increase-your-website-traffic/)。

[![google 流量回升](http://www.labazhou.net/wp-content/uploads/2016/01/1-GJoxchk9p8HQBPzvcESxjA-600x164.png)](http://www.labazhou.net/wp-content/uploads/2016/01/1-GJoxchk9p8HQBPzvcESxjA.png)

教训：在切换域名时，确保你看懂了 Google 文档，并准确理解在你切换之前、要做的事情会产生怎样的潜在影响。



* * *



在迁移中，当我们出现鲁莽导致的错误时，对于我们公司没有产生多少长期危害。拥有一个清晰、简单的域名，要胜过某个月流量的负面影响。

如果要说点儿什么的话，肯定算上前车之鉴了：使流量多样化！

一次 web 修改就能破坏单一的流量源。它可以是一次糟糕的跳转，或者你的头号来路源站突然被关闭了。

如果你期望业务能够持久，你应该对这些事情做好准备。主要的 web 业务不应该依赖于一小部分无法控制的因素。
