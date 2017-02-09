---
author: viviworld
comments: true
date: 2013-12-29 08:21:09+00:00
layout: post
link: http://www.labazhou.net/2013/12/the-typography-and-layout-behind-the-new-signal-vs-noise-redesign/
slug: the-typography-and-layout-behind-the-new-signal-vs-noise-redesign
title: Signal VS Noise排版及布局的再设计
wordpress_id: 89
categories:
- 设计
tags:
- 37signals
- blog
- rails
- rework
- SvN
- 排版
---

自从1999年起我们就通过Sinanl VS Noise分享着进展和公司价值观，这也是《Getting Real》和《rework》的发源地。对于读者来说，它是37signal的一手材料。然而我们从2005年起一直没有给与足够的重视。

[![1s061-History-of-SvN](http://www.labazhou.net/wp-content/uploads/2013/12/1s061-History-of-SvN.jpg)](http://www.labazhou.net/wp-content/uploads/2013/12/1s061-History-of-SvN.jpg)

因此我决定着手这次十分必要的再设计。在大修计划中，我把重点放在创造一个漂亮、清晰、专注的阅读体验。


### 设计之外


“blog”有着临时性、看过就忘了的特点。在SvN（译者注：指Signal Vs Noise，下同），我们花费时间写作、编辑文章。因此除了像一个“blog”，我把心思放在了享有终身权的出版上。整个再设计过程围绕排版文章和外在设计。

除了考虑其他的blog，我花了一周时间学习书、杂志，当然还有 [Bringhurst](http://www.amazon.com/Elements-Typographic-Style-Robert-Bringhurst/dp/0881792063)。捕捉body文本的真谛是第一步------也定下了基调。

或许这就是我，但是网上也能看到“13px sans-serif”之类的东东，它们看起来就像“我的Rails程序从数据库里吐出来的”。我想让你阅读文章，而不是屏幕上渲染的文本。[设置一个舒服的尺寸](http://informationarchitects.net/blog/100e2r/)，为了增加人们的触感而增加的美丽衬线，用Acta设置摘要，Freight Sans和sans-serif 是极好的搭配。


### 让你看到真正的内容


企业的blog往往夹杂着其产品图片。我不想直接扔给你新的工作机会，也不想你还没看多少内容就要求你订阅RSS。这些需求催生出以下布局：内容优先，其他通通靠后。

[![1063-SvN-Sketch](http://www.labazhou.net/wp-content/uploads/2013/12/1063-SvN-Sketch.jpg)](http://www.labazhou.net/wp-content/uploads/2013/12/1063-SvN-Sketch.jpg)

我经常听到移动端体验比桌面端更倾向于集中式。我大致认同，但是移动设备和纸质书有着硬性的相似点：始终如一的版面大小，而桌面端浏览器则不然。
特别是从出版变迁到网络的设计师，比较留恋被限定的页面大小。我们非常庆幸手机上是这样，而桌面浏览器各种各样的尺寸让我们犯晕。尽管如此，我还是对保持桌面浏览器文本每行65-70个字符的舒适宽度抱有乐观，而不用考虑浏览器变多长。我绝对坚持内容在顶部------不能被筛选器、设置、搜索条或广告包围。窗口的空白并不意味着你必须要填充满。


### 开始行动（Responsive as I go）


SvN 程序，我找遍了所有的view，同时重构标签（[Noah](http://37signals.com/svn/writers/noah)修复了被我搞坏的代码，谢谢Noah）。设计每一页时，我在手机端和桌面端调整样式的次数是相等的。为应答view写个性化的Sass @mixins 极大提提高了效率。

    
    section.comments {
      border-top: 2px solid #CCC;
      border-bottom: 2px solid #CCC;
      margin: 1.5em auto 0;
      padding: 1em 0;
      width: 100%;
    
      @include respond-to(768) {
        width: 660px;
    
        h2 { font-size: 1.35em; }
      }
    }


正如[JZ提到的](http://37signals.com/svn/posts/3271-easy-retina-ready-images-using-scss)，由于太多的@media查询实例不完美，最好替换成清晰代码。


### 开放式设计


我分享了很多的东西，包括波形背后的概念、语言、新的[writer page](http://37signals.com/svn/writers/)，和我们新的文章编辑器。它或许只是一个blog，但它是我们的blog。我们将继续让它变得更好，还有我们其他官方站点。我们会继续以开放形式做设计。

原文地址：[http://37signals.com/svn/posts/3285-the-typography-and-layout-behind-the-new-signal-vs-noise-redesign](http://37signals.com/svn/posts/3285-the-typography-and-layout-behind-the-new-signal-vs-noise-redesign)
