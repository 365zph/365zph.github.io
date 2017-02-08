---
author: viviworld
comments: true
date: 2014-05-06 01:02:09+00:00
layout: post
link: http://www.labazhou.net/2014/05/improving-the-url-bar/
slug: improving-the-url-bar
title: 改善地址栏
wordpress_id: 640
categories:
- 安全
tags:
- Canary
- chrome
- google
- https
- ios
- safari
- URL
- 钓鱼
---

iOS已经隐藏URL的路径名有一段时间了，但是Chrome Canary【注1】在 “behind flag”提供了类似功能。

我根本就没有参与Chrome实验版的开发，不过我有超过140字的建议……


### 我们面临一个真正的安全问题


我最近收到一封来自我的域名注册商的邮件，告诉我spritecow.com快到期了。我点开了这个链接，输入我的用户名，打算输入我的密码。我扫了一眼URL，它是HTTPS，不错，里面有注册商的URL，好极了。然后我仔细看了看，意识到它根本不是注册商的URL。我差点被钓鱼。

我一直有收到钓鱼邮件，但是这次几乎让我中招。它伪装得很好，它全部使用相同的字符。当我访问这个链接时，我的地址栏填满了，这是符合预期的，我使用的域名注册商没有极好的URL。它使用前端装载（front-loading，【注2】）URL的通常伎俩。如果我差点中招的话，想必缺乏认识的用户也会完蛋。

[![钓鱼网站网址在谷歌浏览器的截图](http://www.labazhou.net/wp-content/uploads/2014/05/chrome-url-bar-1-1024x196.png)](http://www.labazhou.net/wp-content/uploads/2014/05/chrome-url-bar-1.png)

上面是[我的银行网站的网页](http://www.halifax.co.uk/creditcards/?WT.seg_3=Common/promotion/credit_cards/hlinke/credit0-crdtcard-lnke-crdtcard00)；下面是一个[对应的钓鱼网页](http://www.halifax.co.uk.creditcards.wt.seg_3.common.credit0-crdtcard-lnke-crdtcard00.this.evil.jakearchibald.com/creditcards/?WT.seg_3=Common/promotion/credit_cards/hlinke/credit0-crdtcard-lnke-crdtcard00)。

部分地址是银行的词语。它教会我不要期望所有网页都是HTTPS（thankfully the online-banking bits are【译者注：难以理解，略过不译】），也不要期望可怕的URL，但是浏览器能够做一些更好的工作来拯救我。

找个不做技术的人，向他们出示他们使用的银行网站，问 关于URL告诉他们在银行网站的事情。根据我的经验，大部分用户不理解哪部分URL是安全的特征。浏览器已经开始把URL的这些部分加粗了，但是根据你从上面截图看到的，那还不够。


### 隐藏掉令人讨厌的地方


iOS7 Safari提供了有意思的功能：

[![iOS 地址栏](http://www.labazhou.net/wp-content/uploads/2014/05/ios-url-bar.png)](http://www.labazhou.net/wp-content/uploads/2014/05/ios-url-bar.png)

……Chrome Canary版本的“behind flag”，chrome://flags/#origin-chip-in-omnibox，提供了类似的功能：

[![chrome-url-bar-2](http://www.labazhou.net/wp-content/uploads/2014/05/chrome-url-bar-2-1024x145.png)](http://www.labazhou.net/wp-content/uploads/2014/05/chrome-url-bar-2.png)

修改：我想指出这是一个实验。这是Canary的“behind flag”的情况，和还在公众实验阶段的功能一样。它绝不是最终设计，在Canary的“behind flag”下存在，不代表它一定会出现在稳定版。

对我来说，这是非常明显的（只要[这个bug被修复](https://code.google.com/p/chromium/issues/detail?id=369853)），如果有扩展的验证证书就更加明显了。

[![chrome-url-bar-3](http://www.labazhou.net/wp-content/uploads/2014/05/chrome-url-bar-3-1024x186.png)](http://www.labazhou.net/wp-content/uploads/2014/05/chrome-url-bar-3.png)

浏览器阻止显示URL里的用户名/密码部分，因为它降低了钓鱼的难度。这是一个自然的进步。


### URL之死？


不，这不代表URL死了。URL是网络的分享按钮，它比任何其它平台都要好。可链接性和可分享性是网络的重点，我们必须永远不失去它，这些改变不会失去它。

在iOS，通过点击地址栏，URL仍然可以访问到；或者在Canary实验版，通过点击地址栏，快捷键⌘-L。设计良好的URL在审美上让人愉快地分享，因此有意义URL的需求不会消失。

对于普通大众，URL是令人厌烦的。它是协议、域名和路径。它是一个终端命令，向用户输出的是一个丑陋的UI。我们应当在不损害可分享性的前提下，集中精力在URL的安全上。

原文地址：[http://jakearchibald.com/2014/improving-the-url-bar/](http://jakearchibald.com/2014/improving-the-url-bar/)



	
  * 注1：[https://www.google.com/intl/zh-CN/chrome/browser/canary.html](https://www.google.com/intl/zh-CN/chrome/browser/canary.html)

	
  * 注2：front-loading，[http://www.urbandictionary.com/define.php?term=Frontloading&defid=5299926](http://www.urbandictionary.com/define.php?term=Frontloading&defid=5299926)


