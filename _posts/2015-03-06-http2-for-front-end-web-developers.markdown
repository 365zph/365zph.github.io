---
author: viviworld
comments: true
date: 2015-03-06 10:01:15+00:00
layout: post
link: http://www.labazhou.net/2015/03/http2-for-front-end-web-developers/
slug: http2-for-front-end-web-developers
title: 为前端 web 开发者准备的 HTTP2
wordpress_id: 1679
categories:
- 浏览器
- 编程
tags:
- cookie
- http
- javascript
- 优化
---


	
  * 原文地址（original source）：[https://mattwilcox.net/web-development/http2-for-front-end-web-developers](https://mattwilcox.net/web-development/http2-for-front-end-web-developers)

	
  * 作者（author）：[https://twitter.com/MattWilcox](https://twitter.com/MattWilcox)


HTTP2 【注1】将意味着我们在开发网站上的一个变化。HTTP1 的最佳实践在 HTTP2 的世界是有害的。


### 对于今天 web 上的大多数用户案例而言，是缓慢且低效的


HTTP1.x 是我们都熟悉的 HTTP 的版本。它是一项古老的协议，早在我们知道万维网【注3】会变成什么之前就被设计好了。尽管它能够发挥作用，但它只是不再有效率了，因为我们要求的比其设计初衷要复杂得多。

为了让使用 HTTP1 的网站能够在可接受的时间内载入，[我们开发了一系列的技巧](http://www.labazhou.net/2014/07/optimizing-the-hell-out-of-your-site-for-pagespeed/)：真正的 hack；从这项古老的协议中榨取性能。它们是：



	
  * Spriting：把多张图片整合到一张，使用 CSS 在特定位置只显示图片的一部分。

	
  * 合并：把多个 CSS 或 JS 文件并入一个大文件里。

	
  * 使用无 cookie 域名来提供资源文件。

	
  * 拆分：创建不同的域名或子域名，以托管图片之类的文件。


前两个技巧目标是避免多个 HTTP 请求。在 HTTP1 里，每个请求的成本较高，要耗去太多时间，每个请求要连带载入 cookie 做为请求的一部分，并且它们没有压缩。把一堆东西合并在一起，一次性搞定而不是请求不同的资源，速度要快些。

第三个技巧用来最小化需要得到资源文件的时间；cookie，如果设置了，就会在每个请求中发送被请求域名的 cookie，在这一点上增加了大量的‘浪费’空间。如果你的资源文件位于不同的、不使用 cookie 的域名，那么请求这些文件将不需要附带发送 cookie，这要更快一点儿。

最后一个技巧，拆分，是因为浏览器只允许向每个域名同时请求两个。如果你为资源文件创建了新域名，那么你把浏览器所允许的、同时请求的连接数加倍了，进而获取你的文件。这样，你就能更快地下载网站内容。实际上，拆分在过去的几年里不是太有用，因为浏览器提供商认为‘两个连接’的限制是愚蠢的，他们无视它了。


### 在支持 HTTP2 的网站上，不要应用基于 HTTP1 的最佳实践


HTTP2 差不多要来了，它基于 SPDY，它让一切都变得更有效率。这也意味着所有这些针对 HTTP1 的性能技巧都是有害的。它们将使得一个 HTTP2 站点更慢而不是更快------不要使用它们。

HTTP2 的多个请求的成本更少，因为其本身有大量的技巧。



	
  * 它能够长时间保持连接打开以供重复使用，因此每个请求将不再需要耗成本的握手了。

	
  * HTTP2 与 HTTP1 不一样，它还使用压缩，因此请求的大小显著变小，这样也更快。

	
  * HTTP2 管线化【注2】：它能够在一个连接上同时发送和接收多个请求。


所有这些意味着，陈旧的 HTTP1 技巧不仅仅是不再需要，它们实际上会让事情变得更糟。你可以下载那些对页面浏览不必要的资源文件（貌似是合并和 Spiriting 的事情），拆分引起载入减缓的 DNS 查找的问题，尽管 HTTP2 意味着你不需要把拆分放在首要位置。

总之，在你做网站的前端开发时，你知道它将应用 HTTP2，那么你需要确保你不会使用传统的 HTTP1 性能技巧，它们将损害 HTTP2 之下的网站。


### 更多资料


Daniel Stenberg 写了[一篇不错的评论文章](http://daniel.haxx.se/http2/)，更多细节请查看 [PDF 文件](http://daniel.haxx.se/http2/http2-v1.10.pdf)。



	
  * 注1：HTTP/2的目标包括异步连接复用，头压缩和请求反馈管线化并保留与HTTP 1.1的完全语义兼容。 httpbis工作小组最初考虑了Google的SPDY协议、微软的SM协议和Network-Friendly HTTP更新。Facebook对各方案进行了评价并最终推荐了SPDY协议。HTTP 2.0的首个草稿于2012年11月发布，其内容基本和SPDY协议相同。[http://zh.wikipedia.org/wiki/HTTP/2](http://zh.wikipedia.org/wiki/HTTP/2)

	
  * 注2：HTTP管线化 是将多个HTTP要求（request）整批提交的技术，而在发送过程中不需先等待服务端的回应。[http://zh.wikipedia.org/wiki/HTTP%E7%AE%A1%E7%B7%9A%E5%8C%96](http://zh.wikipedia.org/wiki/HTTP%E7%AE%A1%E7%B7%9A%E5%8C%96)

	
  * 注3：万维网并不等同互联网，万维网只是互联网所能提供的服务其中之一，是靠着互联网运行的一项服务。[http://zh.wikipedia.org/wiki/%E4%B8%87%E7%BB%B4%E7%BD%91](http://zh.wikipedia.org/wiki/%E4%B8%87%E7%BB%B4%E7%BD%91)


