---
author: viviworld
comments: true
date: 2015-06-07 08:23:43+00:00
excerpt: Material Design 里的 FAB 设计是基于用户经常执行某个动作为前提，因此它应该以持续的、高级按钮的形式，被给予一种重要的状态。Google
  的 Material Design 是一种棒极了的、统一的、有准则的设计语言，但是 FAB 却名不副实。
layout: post
link: http://www.labazhou.net/2015/06/material-design-why-the-floating-action-button-is-bad-ux-design/
slug: material-design-why-the-floating-action-button-is-bad-ux-design
title: Material Design：为什么悬浮响应按钮是糟糕的 UX 设计
wordpress_id: 2139
categories:
- 软件
tags:
- gmail
- google
- Google Photos
- Material Design
- 用户体验
---


	
  * 原文地址（original source）：[https://medium.com/tech-in-asia/material-design-why-the-floating-action-button-is-bad-ux-design-acd5b32c5ef](https://medium.com/tech-in-asia/material-design-why-the-floating-action-button-is-bad-ux-design-acd5b32c5ef)

	
  * 作者（author）：[http://www.teoyusiang.com/](http://www.teoyusiang.com/)





* * *



Material Design 是 Google 一年前推出的一种设计语言，代表着该公司在跨设备和平台上创造统一用户体验的大胆尝试。它注重大胆的色彩、自由且遵循阴影的使用，以指示 UI 层和平滑的动画，为 Android（和某些 iOS 上的 Google 应用）提供非常优秀的用户体验。

然而，自从 Material Design 去年推出以来，有一个地方在困扰着我：**悬浮响应按钮**（Floating Action Buttons，本文简写为 FAB）。

[caption id="attachment_2140" align="alignnone" width="495"][![悬浮式响应按钮](http://www.labazhou.net/wp-content/uploads/2015/06/floating-action-button.png)](http://www.labazhou.net/wp-content/uploads/2015/06/floating-action-button.png) 悬浮式响应按钮 | Image credit: Google[/caption]

[根据 Google 的建议](http://www.google.com/design/spec/components/buttons-floating-action-button.html#)，FAB 是悬浮在 UI 上的圆形按钮，用于”进阶操作“【注1】。它们用来调用响应按钮，代表着用户在特定屏幕上最想操作的单个行为。

由于 Material Design 大胆的视觉风格，FAB 十分突出，而难以忽视------问题就出在这里。

**在理想条件下，FAB 貌似提供了优秀的用户体验，然而，FAB 的广泛使用相对于 app 的整体用户体验，或许是有害的。下面是一些原因。**


### 它们带走了身临其境的体验


FAB 在视觉上十分突出------它们总是位于屏幕上每个其它 UI 元素的顶层。这样，增加一个 FAB，将自动导致用户体验少了一些身临其境，尤其是影响到了那些想提供身临其境体验的 app（或屏幕）。

举个例子，新版 Google 相册。

[caption id="attachment_2145" align="alignnone" width="506"][![Google’s Photos app ](http://www.labazhou.net/wp-content/uploads/2015/06/google-photos.png)](http://www.labazhou.net/wp-content/uploads/2015/06/google-photos.png) Google’s Photos app | Image credit: Google[/caption]

该应用打开后，是相册的视图，带着一个悬浮搜索按钮。不过问题在于，当我打开相册应用时，我只是想……浏览我的照片。

这个搜索按钮就这样分散了用户身临其境浏览照片的体验，后者恰恰是该应用摆在首位的主要目的。当然，聪明的照片搜索是 Google 相册这款 app 的独特功能。但是，这意味着它应该是 app 里的顶层的、持续出现的 FAB 吗？（我不觉得）

具有讽刺意味的是，Google 同意我的看法。在 Material Design 教程的 FAB 一节，Google 解释道，「不是每个屏幕都需要一个 FAB」。它接着说「主要响应是触碰相册中的图片，因此不需要按钮。」哦。


### 它们过于突出、起了阻碍的影响


这或许就像同一枚硬币的另一面，但是或许更重要的，FAB 的阻碍影响有另一种暗示。FAB 占据了屏幕上的面积，**有效地遮挡了内容**。

但是，FAB 只是一个小圆按钮，对吧？它能遮挡多少内容呢？

如果你看 Google 相册 app 的截屏，你就意识到，用于搜索的 FAB 遮挡了图片缩略图 50%------明确地说，大到足以盖住一两张脸。当你每次想看屏幕最后一行的第四张缩略图时，还需要额外的滚动。这甚至还不是最糟糕的情况。

[caption id="attachment_2141" align="alignnone" width="281"][![FAB 遮挡了内容](http://www.labazhou.net/wp-content/uploads/2015/06/google-gmail-inbox.png)](http://www.labazhou.net/wp-content/uploads/2015/06/google-gmail-inbox.png) FAB 遮挡了内容，收藏按钮和时间戳 | Image credit: dumazy[/caption]

有个名叫 dumazy 的用户，在 [Graphic Design Stack Exchange 网站提出了他遇到的问题](http://graphicdesign.stackexchange.com/questions/50412/how-do-i-keep-my-floating-action-button-from-blocking-other-components)，是关于 FAB 遮挡了 app 屏幕上的“收藏”星星，还有时间戳。这表明了所有带有列表视图的 app 都会面临的问题，当列表的最后一个条目不能进一步滚动时，它就更是问题了。

这意味着 FAB 宽度的、整个列不得不做出牺牲（通过重新调整星标按钮等），以支持屏幕合适的可用性。

虽然它看起来不是那样的，FAB 占用了比建议的尺寸、更多的屏幕空间。


### 进阶操作或许不那么经常用到


在做 UX 设计时，记住 80/20 法则是有用的，它指出用户在 80% 的时间里将使用 20% 的功能。换句话说，大部分努力应该放在用户大多数时间在用的少量元素上。

从理论上看，FAB 实际上就是那样做的。但是如果“进阶动作”没有被用户经常用到，该怎么办呢？

拿 Google Gmail 做例子。

[caption id="attachment_2142" align="alignnone" width="495"][![Goole Gmail 应用](http://www.labazhou.net/wp-content/uploads/2015/06/google-gmail.png)](http://www.labazhou.net/wp-content/uploads/2015/06/google-gmail.png) Google’s Gmail app | Image credit: Google[/caption]

Gmail app 的 FAB 是撰写按钮，表明用户执行的主要动作是写邮件。

不过，这是真的吗？

[多项](http://venturebeat.com/2014/01/22/65-of-all-email-gets-opened-first-on-a-mobile-device-and-thats-great-news-for-marketers/)[研究](https://litmus.com/blog/48-of-emails-are-opened-on-mobile-gmail-opens-down-20-since-tabs)[表明](http://www.emailmonday.com/mobile-email-usage-statistics)，现在至少 50% 的邮件是通过移动设备阅读的，但是没有数据显示同样的情况转移到撰写邮件上。换句话说，我们日常体验更可能证实，大部分忙碌的移动用户倾向于使用他们的邮件应用阅读邮件。

可能有少量用户在移动设备上回复邮件，但是仅仅发生在打开了一封邮件之后（注意，这意味着他们将绕过 FAB）。这种用户行为，就像不太完美的虚拟键盘的输入机制和自动纠错所导致的，意味着用户执行的主要动作，实际上是阅读（和回复）邮件，而非撰写新邮件。

因此，“写邮件” FAB 有什么作用呢？在少数情况下，当用户立即想用这个应用写邮件时，它可以让用户愉悦。但是其它场合，它只是占用了屏幕空间，遮挡了星星按钮和时间戳，因带有明显的红色而持续地分散注意力。


### 我们需要 FAB 吗？或者说，我们想要 FAB 吗？


当然，不是所有应用程序里的 FAB 降低了使用 Material 应用的体验。有一些极好的例子，FAB 意义非凡，因此增强了那些应用的 UX。

[caption id="attachment_2143" align="alignnone" width="496"][![Google’s Maps on iOS](http://www.labazhou.net/wp-content/uploads/2015/06/google-maps.png)](http://www.labazhou.net/wp-content/uploads/2015/06/google-maps.png) Google’s Maps on iOS[/caption]

Google 地图是 FAB 使用得当的极好例子。用户在地图上执行的主要动作是找到方向，因此用 FAB 做这样的事情就太棒了。

但是考虑到地图是一种非常特殊的情况，用户感兴趣的内容差不多位于屏幕中央（就是你的蓝色方向点的位置）。然而，在大多数应用里，网格或列表视图意味着，用户需要和位于屏幕每个地方的内容进行交互，包括 FAB 通常放置的地方。

还有，上面的截屏只说出了一部分情况：在实际使用中，这些 FAB 在用户滚动（大部分时间里）时，仍然呆在那里。正如 [Google](http://www.labazhou.net/2014/05/google-is-breaking-the-internet/) 在 Material Design 里多次强调的，动态图形设计【注2】和 UI 设计一样重要。在移动内容的情况下，动态图形的缺乏------在屏幕空间的持续保持------催生了一种更高级的分心，这是截图几乎显示不出来的。

当优秀的 FAB 实现的例子少之又少时，就提出了一个问题：我们需要 FAB 吗？

当我们谈了应用里的 FAB 的缺点，我们可以将其总结为一个简单的认识：用户在应用里不仅仅只是执行动作，他们也消费内容（没有比这花的时间多了）。

Material Design 里的 FAB 设计是基于用户经常执行某个动作为前提，因此它应该以持续的、高级按钮的形式，被给予一种重要的状态。但是在很多应用里，用户关注于消费内容（多得不能再多了）：在 Google 相册 app 里，用户想浏览照片；在 Gmail app 里，用户想阅读他们的邮件；在 Facebook app 里，用户想查看他们朋友的动态。

FAB 是这样一种设计哲学（至少算作一种设计上的选择），使理想的内容消费从属于执行动作。我们需要自问：这样一种折衷是必需的吗？事实上，这样的折衷是想要的吗？

当 FAB 导致大部分时间里 UX 消失时，当难以搞清楚 app 里的单个最常使用的动作时，当需要探索迂回的方法（类似于滚动时消失，或列出不同位置的元素）时，我想说，答案是非常响亮的 不。

Google 的 Material Design 是一种棒极了的、统一的、有准则的设计语言，但是 FAB 却名不副实。



* * *






	
  * 注1：本文参考了《Material Design 中文版》，尽量借用里面的专有名词，地址：[http://design.1sters.com/material_design/material-design/introduction.html](http://design.1sters.com/material_design/material-design/introduction.html)。搜索关键词，形如”[promoted action site:http://design.1sters.com/material_design/](https://www.google.com/webhp?sourceid=chrome-instant&rlz=1C5CHFA_enCN584CN585&ion=1&espv=2&ie=UTF-8#q=promoted%20action%20site%3Ahttp%3A%2F%2Fdesign.1sters.com%2Fmaterial_design%2F)“

	
  * 注2：Motion Graphics簡單來說就是動態的圖像設計，它具備一切平面圖像設計所需的基本元素，不同的是加入了時間的概念，它的特點是，可以結合多種素材（插畫、相片、影片、音樂等）去創作、時間短暫、風格強烈、能快速抓住觀眾的注意力。[http://vikingbar.org/2014/11/%E4%B8%8B%E4%B8%80%E5%80%8B%E4%B8%96%E4%BB%A3%E7%9A%84%E5%9C%96%E5%83%8F%E8%A8%AD%E8%A8%88%EF%BC%9Amotion-graphics/](http://vikingbar.org/2014/11/%E4%B8%8B%E4%B8%80%E5%80%8B%E4%B8%96%E4%BB%A3%E7%9A%84%E5%9C%96%E5%83%8F%E8%A8%AD%E8%A8%88%EF%BC%9Amotion-graphics/)


