---
author: viviworld
comments: true
date: 2015-09-08 01:17:37+00:00
excerpt: 在 Appbot，我们看到了大量的 app 图标（icon），然而在 app 测评方面，为我们提供了很多见解。过去我已经研究了很多东西，包括 app
  的描述、截图、取名及国家。其中，常常让我真正感兴趣的是 app 的图标，我偶然发现了一个牛逼的 Ruby 资源库 Miro，它可以从一副图片提取出支配色（dominant
  color）。
layout: post
link: http://www.labazhou.net/2015/09/the-colors-of-an-app-icon/
slug: the-colors-of-an-app-icon
title: app 图标的色彩
wordpress_id: 2452
categories:
- 设计
tags:
- APP
- Appbot
- Google Maps
- Google Play
- icon
- ios
- Miro
- OS X
---


	
  * 原文地址（original source）： [https://medium.com/its-an-app-world/the-colors-of-an-app-icon-b5e8805958d7](https://medium.com/its-an-app-world/the-colors-of-an-app-icon-b5e8805958d7)

	
  * 作者（author）：[https://twitter.com/stuartkhall](https://twitter.com/stuartkhall)





* * *



[![app 图标的色彩](http://www.labazhou.net/wp-content/uploads/2015/09/1_1-9I0aoDNEuOLFiN2M1_WA-600x436.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_1-9I0aoDNEuOLFiN2M1_WA.png)

在 [Appbot](https://appbot.co/)，我们看到了大量的 app 图标（icon）【注1】，然而在 app 测评方面，为我们提供了很多见解。

过去我已经研究了很多东西，包括 [app 的描述](http://blog.appbot.co/writing-a-great-app-store-description/)、[截图](http://blog.appbot.co/app-store-screenshots-of-the-rich-and-famous/)、[取名](http://stuartkhall.com/posts/what-makes-a-successful-app-store-name)及[国家](http://blog.appbot.co/app-store-top-charts-by-country/)。其中，常常让我真正感兴趣的是 app 的图标，但是，如何更好地研究才是有效的？对此，我一直没有好的思路。

最近，我偶然发现了一个牛逼的 Ruby 资源库 [Miro](https://github.com/jonbuda/miro)，它可以从一副图片提取出支配色（dominant color）。

找出 app 的支配色，得到了一些真正有意思的结果。


### 方法


[caption id="attachment_2459" align="alignnone" width="600"][![Google Maps Icon](http://www.labazhou.net/wp-content/uploads/2015/09/1_qpDTTegRcnEz9ToH_bPHCA-600x292.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_qpDTTegRcnEz9ToH_bPHCA.png) Google Maps Icon[/caption]

接下来，我根据标准的[网页颜色](https://en.wikipedia.org/wiki/Web_colors)【注2】（加上黄色）匹配最接近的每种网页颜色。将其分组为大致的名字。



	
  * #02601e -> Green

	
  * #a8120c -> Maroon

	
  * #0c44de -> Blue

	
  * #bdbfc0 -> Silver

	
  * #f4b510 -> Yellow

	
  * #717973 -> Gray

	
  * #24721b -> Green

	
  * #2d0d0e -> Black


[caption id="attachment_2456" align="alignnone" width="600"][![Colors Of Google Maps](http://www.labazhou.net/wp-content/uploads/2015/09/1_xl823nKUdhQcT4wyR5SmNg-600x597.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_xl823nKUdhQcT4wyR5SmNg.png) Colors Of Google Maps[/caption]

忽略黑色、白色和灰色，根据四种最普通的颜色，我将它们绘制到色轮（Color Wheel）上。

大尺寸的图标代表了该图标包含的那种颜色的、更大的比例。


### 前 200 个免费的 iOS app


把前 200 个免费的 iOS app 绘制在色轮上：

[![前 200 个免费的 iOS app的色轮分布](http://www.labazhou.net/wp-content/uploads/2015/09/1_3WUIs4yXvHbGmQpUCOVIrw-600x583.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_3WUIs4yXvHbGmQpUCOVIrw.png)

我们可以看到蓝色和红色 app 图标的分布群，还有散开的绿色。粉色和紫色比例较低，Snapchat 拥有黄色。


### 前 200 个付费 iOS app


前 200 个付费 iOS app 和免费的差异：

[![前 200 个付费 iOS app的色轮分布](http://www.labazhou.net/wp-content/uploads/2015/09/1_dpurS0NLb3TQT_WtUCBdRQ-600x596.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_dpurS0NLb3TQT_WtUCBdRQ.png)

和免费比起来，虽然有着类似的蓝色、红色和绿色的分组，但是付费 app 通常使用更多的颜色，大部分图标只使用一种颜色的情况较少，这导致了在我们的色轮上分布着更多小图标。


### 最新的 100 个 iOS app


在写作本文时，我接着绘制了发布到 App Store 的、最新的前 100 个 iOS app。我们猜测，这将比上图更能代表 App Store 总体的、更有代表的比例。

[![最新的 100 个 iOS app的色轮分布](http://www.labazhou.net/wp-content/uploads/2015/09/1_fVzu4u7YwtNOJX9Bg9RKtA-600x593.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_fVzu4u7YwtNOJX9Bg9RKtA.png)

这和前 200 个付费 iOS app 的色轮图，有着非常相似的结果。


### 前 200 个 iOS 社交媒体图标


所有的社交网络 app 都是蓝色的，对吧？Twitter、Facebook 等。

[![前 200 个 iOS 社交媒体图标的色轮分布](http://www.labazhou.net/wp-content/uploads/2015/09/1_xp3f5J9tp6tw5KGmpaa6kw-600x588.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_xp3f5J9tp6tw5KGmpaa6kw.png)

结果显示，群分布和所有类别的图都相似，只是绿色有更多的比例。


### 前 200 个 iOS 游戏


[![前 200 个 iOS 游戏的色轮分布](http://www.labazhou.net/wp-content/uploads/2015/09/1_zdT4BORM1h7HxdjNRY8OJg-600x583.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_zdT4BORM1h7HxdjNRY8OJg.png)

很多游戏比起应用程序而言，有着更多复杂的图标。这可以从使用的颜色伸展上更多地看到。


### 前 200 个免费的 Mac app


常常有个感觉，在我的 OS X dock 上，90% 的 app 是蓝色的，但是下图和你想的一样吗？

[![前 200 个免费的 Mac app的色轮分布](http://www.labazhou.net/wp-content/uploads/2015/09/1_XCqPVN9Sfdu7l-hdo2GMiQ-600x591.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_XCqPVN9Sfdu7l-hdo2GMiQ.png)

上图显示了在 Mac 上蓝色比例和 iOS 类似，还有很多使用红色和绿色的图标。


### 按照排行榜排名排序


来自 MacStories 的 Graham 给我提了一个好建议，根据排行榜来绘制 app 的支配色。我尝试了排行前 100 名的免费 app。

[![按照排行榜排名排序的色轮分布](http://www.labazhou.net/wp-content/uploads/2015/09/1_wrnfZvIClNmEt-pLJw36YQ-600x571.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_wrnfZvIClNmEt-pLJw36YQ.png)

图标越大的，排行也就越高。


### 在 Google Play 上排名靠前的免费 app


发布了本文的原始版本后，很多人请求我提供 Google Play 的对比。我的结果来自于澳大利亚的 App Store。

[![在 Google Play 上排名靠前的免费 app的色轮分布](http://www.labazhou.net/wp-content/uploads/2015/09/1_zcZG_rb-vHBmN_3bDWaeIA-600x580.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_zcZG_rb-vHBmN_3bDWaeIA.png)

对我而言，看起来非常相似:)


### Google Play 上排名靠前的免费游戏


和 iOS 做对比。

[![Google Play 上排名靠前的免费游戏的色轮分布](http://www.labazhou.net/wp-content/uploads/2015/09/1_cbnzWVz8nRlXQlyMeUeWcQ-600x592.png)](http://www.labazhou.net/wp-content/uploads/2015/09/1_cbnzWVz8nRlXQlyMeUeWcQ.png)


### 你应该为图标选择什么颜色？


归根结底，真的要看你的 app了，[它是做什么的以及你的目标群体](http://www.labazhou.net/2014/04/how-to-build-an-app-preface/)。然而，你或许适合这三种分类的其中一个。


#### 墨守成规


你喜欢随大流，就选蓝色或红色。


#### 我喜欢与众不同


或许你可以选择绿色，而不是最流行的，但是你不要太有伤风化。


#### 叛逆型


你嘲笑那些墨守成规的人，鄙视那些自认为与众不同的人。那么，请选择粉色或紫色，使用它们，就像它们是你自己的一样。

如果你喜欢本文，请帮我多多推荐。然而，在你阅读本文时，为什么不看看我们的 [Appbot](https://appbot.co/) 呢:)

感谢阅读！



* * *






	
  * 注1：图示（Icon），亦作图标，广义上指所有有指示作用的标志，在中文中一般指电脑屏幕的桌面上用来指示用户运行各种操作的图像，作为字符显示的重要辅助。图标的大小多数都是一个正方形的像素矩阵，从 16×16 到 256×256 等不同大小。亦有一些系统可以使用矢量的图标，甚或一些大至 512×512 的图像矩阵。[https://zh.wikipedia.org/wiki/%E5%9C%96%E6%A8%99](https://zh.wikipedia.org/wiki/%E5%9C%96%E6%A8%99)

	
  * 注2：网页颜色（Web Colors）是在互联网上制作网页时，表示各种颜色的方法。颜色可以用三组十六进制数字表示，部分常用颜色也可以用英语名称表示。此外还有直接使用多组十进制表示的方法。[https://zh.wikipedia.org/wiki/%E7%BD%91%E9%A1%B5%E9%A2%9C%E8%89%B2](https://zh.wikipedia.org/wiki/%E7%BD%91%E9%A1%B5%E9%A2%9C%E8%89%B2)


