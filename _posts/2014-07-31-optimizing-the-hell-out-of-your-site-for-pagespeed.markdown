---
author: viviworld
comments: true
date: 2014-07-31 12:19:47+00:00
layout: post
link: http://www.labazhou.net/2014/07/optimizing-the-hell-out-of-your-site-for-pagespeed/
slug: optimizing-the-hell-out-of-your-site-for-pagespeed
title: 用PageSpeed优化你的网站
wordpress_id: 850
categories:
- 编程
tags:
- CDN
- google
- ImageOptim
- javascript
- jekyll
- jquery
- PageSpeed
- sprite
- varnish
- WordPress
---

### 静态资源


我写过一篇文章，是关于jekyll的[静态资源整合](http://tuananh.org/2014/07/29/static-asset-combine-with-jekyll/)的，不过这个思路与其它框架是类似的。你甚至在Wordpress里借助名叫W3TC IIRC插件就可以完成。对于主题（theme）用到的图片，使用CSS sprite技术整合到一张图片里。有很多工具可以做到这一点。

这一步是关键，因为请求的数量对页面载入有很大的影响。你在这一步之后会从PageSpeed得到一些建议。


### 使用内容分发网络（CDN）


CDN把你的内容部署到多个、地理位置分散的服务器上，从访问者的角度让你的页面载入更快。

尽量从受欢迎的CDN载入外包类库。你的访问者已经缓存了Google CDN上的jQuery，这个几率是非常高的。为什么不利用这一点呢？

CDN现在比较便宜。甚至免费选项的CloudFlare也是非常优秀的。用吧。


### 最小化CSS/JS/HTML


这也不花太多时间。CloudFlare也能做到，如果你想省事的话。


### 如果可能，就用defer，async


在可能的地方，defer和async所有的脚本。规则很简单。



	
  * 没有`defer`和`async`，HTML解析会在js代码执行的时候处于暂停状态。

	
  * `defer`会延迟脚本执行，直到HTML解析完成。

	
  * `async`不关心脚本什么时候可获取。只要脚本准备好了，就会执行。如果你有其它脚本依赖于它，你或许不想使用`async`。


如果需要把外部脚本（统计代码、广告等等）放在网站上，尽量找到它们的异步版本。大多数流行的广告网络公司为你的站点提供了异步的代码片段。

把开启了`defer`的JavaScript放在`</body`之前的底部，防止访问者的浏览器不兼容HTML5.


### 优化图片


Yahoo的[smush.it](http://smush.it/)是一个受欢迎的工具。Wordpress有插件大大简化了使用。如果你喜欢线下使用的app，[ImageOptim](https://imageoptim.com/)就不错。


### 使用静态网址生成器


jekyll不错。我在这方面经验不少。如果你想要一个现成的jekyll，去看看Octopress。还有成堆的选择。挑一个吧。


### 反向代理


如果你已经在使用一个静态网站生成器和nginx了，我就不确定一个反向代理是否好使了。根据我的基准测试，varnish在解析静态html上，大致与nginx性能相当。然而，如果你在用动态语言，比如Wordpress用的PHP，varnish会有很大帮助。根据Google分析数据看，我的一个老网站过去每天能够处理200,000个点击，在DigitalOcean只花费5美元，在线人数峰值在800人左右。如果没有varnish，这个网站将远远做不到这个程度。

我使用varnish来忽视静态资源的cookie，还有nginx前面的反向代理。


### Google的模块PageSpeed


在apache安装非常容易，在nginx安装稍微麻烦些。我强烈推荐你安装。它大大简化了你的工作。


### 结论


我做了这些调整后，在PageSpeed得到了93分，满分100；在gtmetrix得了99分，满分100.对于你要花去的半小时，结果还不错哈。如果我有更多的时间，我会做优化，目标是离PageSpeed的100分近些。

有一个PageSpeed建议，我不太理解。如果我不搞清楚，我的分数很快就停在了这个水平。


<blockquote>在不用等待下列资源载入的前提下，你网页上没有一屏内容能够被渲染好。</blockquote>


原文地址：[http://tuananh.org/2014/07/30/optimizing-the-hell-out-of-your-site-for-pagespeed/](http://tuananh.org/2014/07/30/optimizing-the-hell-out-of-your-site-for-pagespeed/)
