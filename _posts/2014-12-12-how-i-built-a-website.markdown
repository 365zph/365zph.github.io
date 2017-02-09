---
author: viviworld
comments: true
date: 2014-12-12 03:04:20+00:00
layout: post
link: http://www.labazhou.net/2014/12/how-i-built-a-website/
slug: how-i-built-a-website
title: 我是如何建立网站的
wordpress_id: 1415
categories:
- 浏览器
- 编程
tags:
- chrome
- css
- Google Fonts
- HTML
- iPhone
- Modern IE
- photoshop
- xcode
- 代码
- 想法
---

原文地址（source）：[https://ccharlottespencer.wordpress.com/2014/11/03/how-i-built-a-website/](https://ccharlottespencer.wordpress.com/2014/11/03/how-i-built-a-website/)

我在学习代码上遇到过的最大问题之一就是把我的知识翻译成物理上的东西。这么多年，我看到很多开发者问“我已经学会了HTML/CSS，接下来呢？”。答案往往是：


<blockquote>“[做些东西](http://www.labazhou.net/2014/10/talk-is-cheap-make-stuff/)”</blockquote>


我是做了一些东西。这是个人网站/作品集，我想带你看看我是如何完成的。尽管我的目标是向其他人演示他们怎样才能建立网站，这也是记录我的过程和进步的绝佳方式。


### 找个想法


你的网站不需要有什么特别，它也不需要是你的最爱、发tweet、顶拳（fist bump）或每天1000个访问。它只需要成为你愿意享受其中的东西。

我确信没人坐下来就能马上魔法般地产生令人惊奇的想法。我的大部分想法出现时，我通常在睡觉或洗澡。我可以用一天时间来考虑让人激动的东西，只是一两周内不会有另一个想法。

不要试着强迫自己得到想法，这行不通，还会导致大量的沮丧情绪。从简单开始，为自己而做。我经常看到世界上的某些东东，对我自己说“_嗯，我想，我能够建立属于我自己的、更加适合我的版本_”，或“_我需要一个工具来完成这项单调的任务，因此我尽量自己开发它_”。没错，这就是起步的伟大地方。

我有一份长长的想法列表，它们都不是有奖励的、但都让我感兴趣。如果你有了想法，记下来，当你有时间去开发的时候，你就能看到你自己产生的所有好玩的想法了。

[![想法的todo清单](http://www.labazhou.net/wp-content/uploads/2014/12/ideas-trello.png)](http://www.labazhou.net/wp-content/uploads/2014/12/ideas-trello.png)


### 规划想法


你只需一支笔和一张纸。在开始我的作品集之前，我草拟出基本要点，并就我乐于使用的颜色和字体做了注解。

最终完成的作品与我的草图看起来非常不同，不过这是一个伟大的起点。我也规划了网站的很多版本，因此不要担心最终产品与你开始画的草图有什么不同。


### PhotoShop做原型


画好想法的草图后，我打开PhotoShop布局网站。有的人在写代码之前用PhotoShop进行设计，有的人喜欢直接写代码然后在浏览器里设计。选择你喜欢的方式。

[![用PS做原型](http://www.labazhou.net/wp-content/uploads/2014/12/photoshop-mock.png)](http://www.labazhou.net/wp-content/uploads/2014/12/photoshop-mock.png)


### 配置项目


我喜欢把所有想法放在桌面的同一个文件夹里。我在项目文件夹里新建一个文件夹，在里面做如下配置：

[![网站的目录结构](http://www.labazhou.net/wp-content/uploads/2014/12/filetree.png)](http://www.labazhou.net/wp-content/uploads/2014/12/filetree.png)

index.html位于目录顶层（根目录）。其它重要的文件放在“assets”文件夹。为了保持直观的结构，CSS、JavaScript和图片单独放在的另外文件夹。


### 设计HTML


没有HMTL就没有网站。它包含了出现在网站上的所有信息，而CSS只是让它们看着舒服些。

我开始设计网站每一部分的容器：header，主内容和about页。在定下来之前，我不是十分精确地知道将呈现什么内容，因此做了一些修改。没事，确保添加一些模拟内容，当应用CSS时，你就能看到它的样子了。


### 选择字体和颜色


我在草案里写有我想在项目中使用的颜色。大部分来自于我的[twitter主页](http://www.twitter.com/charlotteis)，然后是要匹配avatar（网站header里的主要图片）的颜色。

有一些优秀的工具，用来找到和创建颜色，比如[Colour](http://color.adobe.com/)和[Coolors](http://coolors.co/)。我打算站点简洁、干净，只用一两种强调色。

我还从[Google Fonts](https://www.google.com/fonts)找了两种字体。它们可以免费使用，且易于包含在项目里。我想给body里的文本和副标题应用清晰的sans-serif字体[Open Sans](https://www.google.com/fonts/specimen/Open+Sans)，像大块引用和“About”头部等较大文本，我用[Roboto Slab](http://www.google.com/fonts/specimen/Roboto+Slab)字体。

我喜欢纤细的字体，但是font-weight（鲜明度）太低的字体将不利于文本阅读，这是非常重要的。也不要使用太多字体，这会让人抓狂，也会增加网站载入的时间。你想让读者吸收的是你要表达的东西，而不是在单独一个段落里使用的15种字体，如果他们不想粗暴地关掉网页，就要决定是否等待这些字体载入。


### 用CSS做样式


我首先把[normalize.css](http://necolas.github.io/normalize.css/)添加到CSS文件夹，在HTML里做了链接。

在一种浏览器（比如Chrome）里开发网站绝不意味着在另一种浏览器（比如IE）里有着同样的表现。normalize.css就是为了尽可能多地通过提供一种“reset”来修复这种差异。它让网站在各种浏览器里良好地呈现，我相信，开发一个跨浏览器兼容的网站是至关重要的。

我首先从最重要的样式开始，像body和header的字体和字体大小。然后深入页面，不用在页面之间来回多次就能够定义好每个元素的样式。


### 可访问性


在你开发东西的时候，你应该时常为你的用户考虑。世界上的任何app、产品、印刷品、信件、海报、网站、工作台、商店以及其它东西，都被尽可能多的人使用。想理解网站为什么需要可访问性，请访问Laura Kalbag的“[Why Bother with Accessibility](http://laurakalbag.com/why-bother-with-accessibility-on-24ways/)?”。

让我的网站具有可访问性是相当简单的。我在必要的地方添加了[ARIA landmark role](http://a11yproject.com/posts/aria-landmark-roles/)【注1】，给屏幕阅读器（通常残障人士使用）指示内容类型。我确保所有的链接都可以用键盘访问，并用CSS作了突出。

接下来是网页底部的社会化图标了，我在文本里指示了每种图标链接到了什么网站。我在浏览器里作了隐藏，但是确保可以屏幕阅读器用户是可见的。

一些人夸奖我在做网站的时候考虑了可访问性。虽然这让我感到自豪，但是，如果我因为给了它本应该得到的关注而被夸奖的话，只能说明可访问性还没有得到足够考虑。如果你需要制作可访问性网站的一些优秀资源，请访问[A11Y Project](http://a11yproject.com/)。


### 测试


正如刚才提到的，一个网站在每个浏览器和设备上表现一样是非常少见的。测试是比较耗时的，甚至取决于你手头的资源，但是它相当重要。当网站准备让全世界看到时，马上测试，确保你找不到网站故障。

跨设备和浏览器测试为什么是重要的，如果你想了解，下面列出了过去24小时访问我网站的用户的数据。来自于Safari（26%）、Android（3%）、IE（2%）、Chrome（39%）、Opera（2%）。让不同的用户在你的网站有一个好的体验，是比较重要的，因此在条件允许时，要在尽可能多的不同环境下测试。

[![网站统计数据-浏览器排名](http://www.labazhou.net/wp-content/uploads/2014/12/analytics-testing.png)](http://www.labazhou.net/wp-content/uploads/2014/12/analytics-testing.png)

我使用下面浏览器的最新版本测试网站：Chrome、Firefox、Opera、Safari和IE。前四个浏览器很容易就能下载到。如果你不在Windows上，用IE测试就有点儿难了。借助Virtual Box在Mac上安装一个Windows版本，就能用IE测试了。微软自己做了一个网站，向你展示了如何零成本地测试：[Modern IE](http://modern.ie/)。

有一些工具，能够对你的网站在各种浏览器和设备上的展示进行截屏并发送给你。我问一些朋友，他们用什么工具测试，你可以在[这里](https://github.com/Charlotteis/noquestionistupid/issues/14)找到答案。[Modern IE](http://modern.ie/)也能在使用广泛的浏览器/设备上截屏，免费的。

如果你对那些可以访问网络的一堆设备没有限制，这是聪明的，但是很可能你不是这样的。我有iPad、Samsung Galaxy S3和老款的iPod Touch，难以覆盖所有种类的设备。

如果你是Mac，就能用Xcode下载iOS模拟器，基于一些iPhone和iPad版本进行测试。有个初级方法，调整浏览器大小到移动设备宽度，但是，这不是真正靠谱的可选方法。

我还测试了网站在[可阅读性](http://read-able.com/)、[良好地对比](http://www.spurapp.com/)【注2】、[校验](http://validator.w3.org/)和[可访问性](http://wave.webaim.org/)。

关于测试的最后一点是：你应该随着开发进度去测试网站。这样做的话，在项目结束、或让人沮丧、或潜在地让你变得更糟之前，你就能修复好bug。我有过一次经历，开发人员在项目结束之前不想测试他们的产品。对我而言，那时候长达数小时的痛苦的重复测试，而他们在尽量修复我报告给他们的一堆堆bug。简直一团糟，如果他们自始至终都测试网站的话，将平静很多。


### 分享，让朋友看看


我已经建立了一个网站，从中学到了很多东西。尽管如此，我知道还有一些我能够做得更好的地方。我给你分享我的代码，不只是希望你能从中学习，而且还能指出我的错误！

你可以在这里找到我个人网站的代码，在这里查看最终的网站。如果你找到了一些有问题或值得提高的地方，请告诉我。



	
  * 注1：网页亲和力（又称网络无障碍、网络可达性或网络可用性）旨于确保任何人都有办法获取放在网页上的媒体内容——无论人们是否遭遇了身体、心理或技术上的障碍，都不会妨碍人们接收作者所发布的信息。也就是让网上的内容“易于亲近”，易于获取、利用。请参考[http://en.wikipedia.org/wiki/WAI-ARIA](http://en.wikipedia.org/wiki/WAI-ARIA)和[http://zh.wikipedia.org/wiki/%E7%B6%B2%E9%A0%81%E8%A6%AA%E5%92%8C%E5%8A%9B](http://zh.wikipedia.org/wiki/%E7%B6%B2%E9%A0%81%E8%A6%AA%E5%92%8C%E5%8A%9B)

	
  * 注2：Spur是一个由设计咨询公司ZURB​​推出的简单有趣的网页设计web小应用。通过快速截取网页内容，从而帮助企业设计出更好的网站以及网络相关服务和产品。[http://www.techweb.com.cn/newsite/2011-09-19/1095284.shtml](http://www.techweb.com.cn/newsite/2011-09-19/1095284.shtml)


