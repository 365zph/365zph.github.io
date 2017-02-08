---
author: viviworld
comments: true
date: 2014-04-12 14:20:34+00:00
layout: post
link: http://www.labazhou.net/2014/04/how-to-detect-the-software-your-visitors-have-installed/
slug: how-to-detect-the-software-your-visitors-have-installed
title: 如何检测你的访问者安装了什么软件
wordpress_id: 536
categories:
- 编程
- 软件
tags:
- Adobe
- flash
- javascript
- jquery
- Office
- photoshop
- 字体
---

## 使用flash&jQuery的快速概念证明




<blockquote>访问这里的demo：[http://johnmcl.github.io/software-detect-js/](http://johnmcl.github.io/software-detect-js/)</blockquote>


为特定用户的意图和需求量身定制使用网站的体验，无论是让你的网站具有更好的移动友好性，还是让它与用户的地理位置更加相关，都能够收获巨大的回报。

而大部分网站能够检测用户的浏览器和操作系统，或根据用户IP地址来获得他们的大致位置，大部分网站在直接吸引用户上可以做得更好。

有一些不太明显的技术让你能够更进一步。一个是在用户载入网页时，检测用户电脑上安装了什么软件。

下面是原理：无论你何时安装任何主流软件包，你通常最后会在你的系统上得到一堆新字体。这些字体差不多总是有唯一性，不仅仅是软件包，还有软件包的具体版本。通过用户浏览器抽出这种“字体签名”，就能帮你检测用户安装到电脑上的软件种类------这不需要任何额外的用户许可。

访问到了用户字体，和他们相应安装的软件，意味着你能预先知道他们可能在你的网站寻找什么。例如，你能为 已经安装了设计软件的用户 重新排列你公司网站上的工作列表，以显示设计师/用户体验工程师职位。如果你支持多种格式的下载，你可以仅仅显示你知道的、用户能够打开的那些格式。或者，如果你能够检测用户有一个Photoshop或Office的过期版本，你可以加入Microsoft或Adobe推广程序，运行Office 365和Creative Cloud上面的广告。

有一些通过用户浏览器来抽取用户已经安装字体的方法。最简单的方式是借助一个小巧的flash脚本来返回字体列表。我，就我个人而言，使用font-detect-js。然而，稍下点儿功夫，你也能够不用flash就搞定。你可以仅仅依靠jQuery&CSS，试着渲染、测量在一个隐藏div内的字体。Lalit Patel在《JS/CSS Font Detect》文章有讨论。

一旦你有了用户字体列表，把列表映射回他们安装的软件就相当容易了。很多厂商列出了与他们软件绑定的字体。下面是一些例子：



	
  * [Apple iWork](http://support.apple.com/kb/ht5379)

	
  * [Microsoft Office 97, 2000, XP, 2003](http://support.microsoft.com/kb/837463)

	
  * [Microsoft Office 2007](http://support.microsoft.com/kb/924623)

	
  * [Microsoft Office 2008](http://www.microsoft.com/typography/fonts/product.aspx?PID=147)

	
  * [Microsoft Office 2010](http://support.microsoft.com/kb/2121313)

	
  * [Microsoft Office 2013](http://support.microsoft.com/kb/2800393)

	
  * [Adobe CS3 (2)](http://blogs.adobe.com/typblography/2007/04/cs3_bundled_fon.html)

	
  * [Adobe CS4](http://www.adobe.com/type/browser/fontinstall/cs4installedfonts.html)

	
  * [Adobe CS5 (2)](http://www.adobe.com/type/browser/fontinstall/cs5installedfonts.html)

	
  * [Adobe CS6](http://www.adobe.com/type/browser/fontinstall/cs6installedfonts.html)

	
  * [Adobe Photoshop Elements 8](http://techinch.com/blog/what-fonts-are-included-with-photoshop-cs4-cs5-and-elements-8)

	
  * [Adobe Creative Cloud](http://www.adobe.com/products/type/creative-cloud-fonts.html)


在一些情况，你也能够检测用户是否注册了他们的Adobe产品。那是因为做为注册的交换，Adobe会给用户分配免费字体，比如'Hypatia Sans'，'Adobe Text'或'Garamond Premier'。

这里有一个简单的demo，可以检测是是否安装了一些软件：[http://johnmcl.github.io/software-detect-js/](http://johnmcl.github.io/software-detect-js/)

你也能够在Github下载、贡献这个项目，这里：[https://github.com/johnmcl/software-detect-js/](https://github.com/johnmcl/software-detect-js/)

原文地址：[https://medium.com/p/b436a0e031ac](https://medium.com/p/b436a0e031ac)
