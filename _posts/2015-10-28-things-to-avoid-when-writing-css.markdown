---
author: viviworld
comments: true
date: 2015-10-28 07:56:45+00:00
excerpt: 多文件、嵌套（借助 Sass）、像素单位、设备断点。我认为他们要说的话和真正的响应式设计没有关系。他答道，「理论上我是认可的，但是移动体验成功的关键在于理解现实世界」。
layout: post
link: http://www.labazhou.net/2015/10/things-to-avoid-when-writing-css/
slug: things-to-avoid-when-writing-css
title: 写 CSS 时要避免的几个地方
wordpress_id: 2681
categories:
- 编程
tags:
- css
- ie
- Sass
- 响应式设计
- 断点
---


	
  * 原文地址（original source）：[https://medium.com/@Heydon/things-to-avoid-when-writing-css-1a222c43c28f](https://medium.com/@Heydon/things-to-avoid-when-writing-css-1a222c43c28f)

	
  * 作者（author）：[https://twitter.com/heydonworks](https://twitter.com/heydonworks)





* * *



声明：你可以不同意我在本文所写的一些观点，没有问题，我不是要代表你、代表你的公司或意识，因此请不要感到不安。继续保持你的看法即可。向那些理解演讲方法和辩证法的、绝大多数人致歉，因为本声明不适用于他们。


### 多文件


很多 web 开发貌似都和将任务分割为可管理的块或「组件」相关。对于每一个分离的 JavaScript 功能块、或 HTML 局部，我可以做一个专门文件，并把相关文件组织到文件夹里，以 javascript、html 或 controller、templates 命名。你怎么做都行。这样，你就能轻松查看文件系统，只关注包含有你当时想要编辑的代码文件即可。

这种方式不适用于 CSS。JavaScript 函数可以放在它们被调用位置的前后，HTML 模块可以在任何地方插入，只要你觉得它们适合当前文档流。另一方面，CSS 是按照时间顺序发生的。它和你声明样式的顺序，有着很大关系。由于该语言的继承和 specificity[note]CSS 的 specificity 特性或称非凡性，它是衡量一个衡量CSS值优先级的一个标准，既然作为标准，就具有一套相关的判定规定及计算方式，specificity用一个四位的数字串(CSS2是三位)来表示，更像四个级别，值从左到右，左面的最大，一级大于一级，数位之间没有进制，级别之间不可超越。[http://www.cnblogs.com/yizuierguo/archive/2009/03/16/1413721.html](http://www.cnblogs.com/yizuierguo/archive/2009/03/16/1413721.html) [/note]，你应该从一般样式（比如对 body 设置 font-family）开始，并过度到更多具体的定义。

CSS 是一个有序的、以例外为基础的语言，没有简单的方法来连贯地表示一个文件列表（通常按照字母顺序组织）。它给了你一个印象，每个 CSS 文件都是自治的，事实上却不是。

    
    - buttons.css
    - reset.css


因此你有两种选择：当你试图把一个方钉子打入圆孔时，你可以对「specificity 不应该成为 CSS 的一部分」持拒绝、抱怨的态度，或者，你用一个有着良好注释的文件，它明确地表示了继承过来层叠的弧度。specificity 不应该成为一个问题，因为大多数特定的选择器应该是你最后才编写的。

**总结**：_你不应该把 CSS 文件分割为独立文件，就像不应该把一块玻璃丢在水泥地板上一样。_


### 嵌套（借助 Sass）


我对 Sass 感到比较纠结。它的一些思想真的让我激动，比如使用循环和条件语句提高编写效率的能力。而另外一些特性就不那么好了，比如无限嵌套的声明。

我认为，很多人选择 Sass，帮助他们管理和维护 CSS，更方便阅读和编写。Sass 做为一个依赖和抽象层所带来的负面影响，就是让事情更加系统化地复杂，据说还有一些 Sass 提供的接口，比如带参数的混入（mixin）。将其用在项目中，代码的可阅读性和简短程度，就成了一种福音。

嵌套吗？那只会让问题更糟。想象一下组织最糟糕的 CSS 文件。虽然混乱，但至少是一个维度的混乱：如果你愿意，那么只有一个文件混乱。让编写蹩脚 CSS 的人（可以是任何人，很多时候也包含我）使用嵌套，相当于授权他们扩大到第二维度的混乱。太棒了！现在，混乱彻底蔓延开来。

鉴于在其它语言里，尽可能地避免嵌套结构是一种职业荣誉感的体现，那么，将这种能力用在不需要嵌套的语言里，貌似有些可笑。Hugo Giraudel 就 Sass 写了数百篇指导文章。下面是他就嵌套不得不说的话：


<blockquote>Fucking. Stop. Nesting.</blockquote>


**总结**：_你要追寻的 Sass 特性不应该是嵌套。_


### 像素单位


回溯到 IE6 的时代，我们被告诫用 em 单位设置字体大小。较新的浏览器带有缩放功能，可以更容易地按比例增加页面尺寸，但是在 IE6，你只能增加字体大小。由于用[像素](http://www.labazhou.net/2014/06/that-one-pixel/)设置的文本拒绝被放大，我们会排斥很多低版本用户。

IE6 不再是一个问题了，但是大多数操作系统和浏览器的用户仍然设置独立于缩放功能的字体大小。这应该是他们的喜好，我们应该包容。

说归说，我甚至没有打算实现这一目的。我只想向你自私的一面发出恳求：在响应式设计里使用像素来管理大小，绝对是愚蠢至极的行为。分开元素之间的尺寸，其相对性的缺乏意味着你要不得不为每个独立的断点，单独考虑每种设置。事实上，使用像素时，你甚至不得不管理字体大小和单独的、隔开元素的 margin。你本不想这样做的。

举个例子：

    
    @media (min-width: 400px) { 
      h1 { 
        font-size: 22px; 
        margin-top: 33px; 
      } 
    }


如果使用相对单位，我该怎么做呢？我不愿意的。事实上，我无需在我的媒体查询里针对任何单独元素设置字体大小和 margin。我只想让浏览器或用户根据根元素（）来决定字体大小，并用 em 或 rem 来设置我的所有其它规格。

    
    h1, h2 { margin-top: 1.5rem; } 
    h1 { font-size: 2.5em; } 
    h2 { font-size: 2em; } 
    /* all your other element styles */


然后，当我想在 min-width 断点下放大比例时，我只需要根据其它元素的比例，调整根的字体大小。我使用百分比，因为这涉及到用户喜好，如果设置为：

    
    @media (min-width: 400px) { 
      html { 
        font-size: 120%; 
      } 
    }


你的响应式设计的 90% 策略都在这里了。而且，你还能在所有同级的流元素之间设置通用的 margin，比如使用 [Lobotomized Owls](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)[note]可参考 [https://css-tricks.com/lobotomized-owls/](https://css-tricks.com/lobotomized-owls/) [/note] 的选择器：

    
    body * + * { 
      margin-top: 1.5rem; 
    }


**总之**：_拥抱相对性，收获成果。_


### 设备断点


几个月前，也就是在被爆出苹果公司在中国血汗工厂不久，我看到一名评论员发的 tweet。他们的 tweet 包含了一种风格：「_对于响应式 web 设计，所有的视口在 iOS9 上都是可用的_」。

什么？什么？

然后我想起和 Sara Soueidan 的一次谈话，她把内容断点描述成了响应式设计的「惊天秘密」。我突然想到：有很多人盯着被选定的专门设备，把它们特定的屏幕尺寸做为「响应式 web 设计」的目标------每当一家技术公司发布一款内置浏览器的设备时，都要「改变这个规划」，那么，成千上万的 web 设计师可能要骂「oh fuck me」了。想象一下！


<blockquote>“OHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKMEOHFUCKME”</blockquote>


我没有假定你是在此误解下工作的，但适用于一种情况，你有一个朋友，他需要了解真相：适应于具体设备的具体尺寸的断点，不属于响应式设计。这种行为是站不住脚的，它行不通。如果你没有针对某种设备做过调整的设计，具有完整的呈现，那一定是好运气在作怪。这真不算是一个策略。

你应该确保设计是流动的，仅仅在内容遭遇呈现问题的地方插入断点（或「tweak point」）。在这些点之间，设计应该无缝地展开或折叠，满足任何出现在这些范围内的设备尺寸的要求。

我对评论员和意见领袖说，我认为他们要说的话和真正的响应式设计没有关系。他答道，_「理论上我是认可的，但是移动体验成功的关键在于理解现实世界」_。也就是说------没有说明白！我很想知道真正的现实世界是什么样子……有一天我必须参观一下。

**总结**：_苹果不是唯一一家制作带有内置浏览器设备的厂商。真的不是。_


### Fuck CSS，大家开干吧


感谢你们容忍我对 CSS 作者的看法。如果你是 web 可访问性和音乐（谁不是呢）的粉丝，你可能乐于支持一些优秀的组织，请查看 [A11Y ROCKS](http://heydonworks.com/a11y_rocks/)。
