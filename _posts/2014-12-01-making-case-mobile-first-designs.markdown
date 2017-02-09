---
author: viviworld
comments: true
date: 2014-12-01 13:46:20+00:00
layout: post
link: http://www.labazhou.net/2014/12/making-case-mobile-first-designs/
slug: making-case-mobile-first-designs
title: 为移动优先设计辩护
wordpress_id: 1378
categories:
- 网络
- 设计
tags:
- css
- GPS
- HTML
- 内容优先
- 浏览器
- 移动优先设计
---

原文地址（source）：[http://www.sitepoint.com/making-case-mobile-first-designs/](http://www.sitepoint.com/making-case-mobile-first-designs/)

你知道今天移动流量（比如智能手机等）在网站PV的占比达到了30%吗？差不多是2年前的3倍了。同期，桌面访问下降到了60%（[这里是数据的测量标准](http://gs.statcounter.com/faq#methodology)）。

[![web平台的占比](http://www.labazhou.net/wp-content/uploads/2014/12/web-platform-statcounter-global-stats.png)](http://www.labazhou.net/wp-content/uploads/2014/12/web-platform-statcounter-global-stats.png)

除了PV，再看看消费的时间，[由comScore出具的报告](http://www.comscore.com/Insights/Blog/Major-Mobile-Milestones-in-May-Apps-Now-Drive-Half-of-All-Time-Spent-on-Digital)显示，移动平台在时间消费上的占比达到了60%。

[![主要的内容种类在各平台上的时间消费比例](http://www.labazhou.net/wp-content/uploads/2014/12/leading-content-categories.jpg)](http://www.labazhou.net/wp-content/uploads/2014/12/leading-content-categories.jpg)

我可以分享更多的数字来支持这个观点，但是你们能够在[这里](http://techcrunch.com/2013/07/03/mobile-data-use-to-grow-300-globally-by-2017-led-by-video-web-traffic-says-strategy-analytics/)和[这里](http://www.prnewswire.com/news-releases/strategy-analytics-handset-data-traffic-to-grow-over-300-by-2017-to-21-exabytes-214113401.html#prettyPhoto)看到更多的数据下降趋势。这些数字只是表明了**web使用模式的变化是多么地快速**。

Luke Wroblewski[早在2011年](http://www.lukew.com/resources/mobile_first.asp)就讨论过移动优先设计的必要性，在2012年[分享了一些早期数据](http://www.lukew.com/ff/entry.asp?1597)，这远远早于我们看到web使用模式上大迁移的时间。两年过去了，[智能手机和平板引人注目地取代了PC](http://techcrunch.com/2013/06/24/it-device-sales-to-rise-6-to-2-4b-in-2013-driven-by-android-tablets-smartphones-pcs-continue-decline/)，甚至在工作场所，大部分设计师和开发者仍然坚持用传统方式设计------针对大屏桌面------仍然在讨论优雅降级和渐进增强的区别。


### 传统桌面优先的方式已经过时了


如果你在处理web设计策略时，仍然主要考虑大屏，那么是时候好好考虑一下了。原因如下：



	
  * **用户正在迁移到移动端**。如今除了你的网站在桌面表现如何，越来越多的用户更加关注移动体验。不管你的网站是关于商务，还是提供信息和内容，用户无论何时何地，都需要能够访问它、使用它。正如本文第一段的数据所展示的，那很可能来自于移动设备。

	
  * **桌面用来创建内容，移动用来消费**。移动设备是大部分访问者今天消费内容的主要方式。桌面继续被使用，主要用于创建内容或“工作”------这过于错综复杂而无法在移动设备上完成。即便如此，[很多转向用移动设备工作的公司也在变化着](http://techcrunch.com/2013/06/24/it-device-sales-to-rise-6-to-2-4b-in-2013-driven-by-android-tablets-smartphones-pcs-continue-decline/)。你能够在[这个优秀的报告（PDF）](http://www.exacttarget.com/sites/exacttarget/files/deliverables/etmc-2014mobilebehaviorreport.pdf)里读到更多关于移动用户行为。

	
  * **移动设备和浏览器已经进化了**。对于web开发，桌面和移动体验的主要不同，过去常常在于移动浏览器非常基础，无法支持很多主要的开发特性，导致我们采取优雅降级的方法。如今情形不同了。移动浏览器进化了。优雅降级和渐进增强不再是移动上的主要策略。为了处理各种浏览器支持情况的巨大不同，这种原则成为一种方式。当今，移动设备具有与桌面电脑性能差不多的CPU和GPU。现代的基于WebKit的移动浏览器比IE8好很多了！因此你不必再为移动设备简化什么了。真正的限制在于屏幕空间和下载带宽。

	
  * **web的本质是用户体验，而不是设计**。做为设计师和开发人员，我们经常纠结于 我们的工具让我们做出多么美好的东西------不管它只是在摆弄图表、动画和媒体查询。web与我们无关，它甚至与HTML、CSS、JavaScript或我们使用的其它工具也无关。_它是连接人与人的_。你的网站真的不需要漂亮的图表、渐隐效果的表单、或最新的CSS3特性来创建精致的用户体验。




### web的未来是移动


在过去的几年里，我们体验互联网的方式发生了天翻地覆的变化，那时候你是从为桌面设计开始的，到了如今，就像一只脚牢牢地长在了过去。它让你无法前进，这意味着你的网站将很快过时。尽管如此，对于一些人来说（嘿，你可以重做网站，多赚一些钱），这可能是好消息，我们当中的大部分人更喜欢推出优秀的、最新的作品------这会得到欣赏。下面是移动优先方法对你的帮助：



	
  * **你最好保持前瞻性**。再次强调，回头看看本文前面的数据。

	
  * **它让你关注人、关注用户体验、关注内容**。因为设备的限制，移动用户可用屏幕空间不超过桌面的20%。为了确保你的网站仍然表达出所需要的信息，你被迫关注核心，你不得不精确地知道谁是你的目标用户，确切地知道你想让他们体验什么。

	
  * **它让你对扩展功能做出改变**。想想触摸屏，想想GPS。它们和其它类似扩展功能，已经成为今天移动体验的一部分。我们将看到它们很快进入桌面空间。明确地为移动设备设计，它为你打开了可能性，改变这些‘扩展的’功能来创建丰富的情景感知网站。它给了你打破常规的空间，而不是坚持桌面世界的陈旧概念和功能。

	
  * **更干净的设计，更干净的代码。**移动优先方法是极简化的。不必做涵盖了所有杂七杂八的大型设计，而是添加媒体查询，在小屏幕上有选择地显示或隐藏元素，从最少开始，仅仅添加绝对需要的元素------差不多是禅的方法。想了解更多，请看Jeremy Girard[在Smashing Magazine网站上叙述](http://www.smashingmagazine.com/2013/03/05/building-a-better-responsive-website/)他的公司是怎样执行移动优先设计、以及它是怎样帮助他们的。




### 什么在阻碍你？


如你所见，我对移动优先设计有着明显的偏见。因此我不得不绞尽脑汁，尽量搞清楚为什么其他人没有这样的激情。我只总结了两点。



	
  * **习惯**。我们只是习惯了陈旧的设计方式。从大屏开始，‘让它包罗万象’；然后为小屏遗留一部分。我们不想努力去改变，我们不愿相信它是必需的，甚至不愿相信这是可能的。移动优先设计迫使你重新思考整个设计和开发策略。你从少开始，少的空间，少的内容。难度真的不小。还有，我们不得不考虑像手势、触摸和GPS之类的细节，而不是过去的鼠标控制和点击。

	
  * **客户**。是的，客户。他们在设计上有最终话语权。有些客户还要求基于Flash的网站、而非HTML。有些客户想要花哨的图片和图表。一些客户不喜欢你呈现给他们的极简的、移动优先设计。但是，做为设计师/开发者，弄清楚什么对于网站和客户才是最好的、并向他们解释清楚，这是你的工作。当然，如果他们的网站流量都来自于桌面而不是移动端，那么务必做一个基于桌面的设计。但是如果他们正看到增长的移动访问量，那么提高你的谈判技巧，告诉他们移动优先的意义。


[![各平台数字媒体花费的时间](http://www.labazhou.net/wp-content/uploads/2014/12/digital-media-time.jpg)](http://www.labazhou.net/wp-content/uploads/2014/12/digital-media-time.jpg)


### 总结


移动优先设计不但让你的网站应对已经发生在移动空间的爆炸式增长，而且迫使你这个设计师和开发者关注于用户。

移动优先设计不只是针对新网站的。即使你已经有一个桌面版了，它也是可以遵循的好方法。在为移动设计过程中，你不得不分清楚什么是核心，什么是优先考虑的，你真正想在屏幕上呈现什么，还有你想让用户如何与网站互动。这些见解也为优化桌面网站的方法提供了指导。

虽然我一直在说“移动”优先，但要注意，这个原则不是真地限制在“移动”设备上。它涉及到了更好的可用性、更好地利用屏幕实际使用面积、页面元素和代码------[我们应该总是优先考虑它们，不过它们经常被掩盖在奢华之下](http://www.labazhou.net/2014/09/designing-a-homepage/)。

少即是多，简单的就是更好的。与极简化有几分相似。但更多是因为它把关注点带回到了人本身，而不是技术细节。
