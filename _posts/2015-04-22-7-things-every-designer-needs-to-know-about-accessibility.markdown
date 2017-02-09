---
author: viviworld
comments: true
date: 2015-04-22 13:08:02+00:00
excerpt: 可访问性使有障碍的人能够对网络进行感知、理解、导航、交互以及贡献。让你的产品成为符合 Section 508 和 Web 内容无障碍指南（简称 WCAG）【注1】的最小化标准的“设计准备”
layout: post
link: http://www.labazhou.net/2015/04/7-things-every-designer-needs-to-know-about-accessibility/
slug: 7-things-every-designer-needs-to-know-about-accessibility
title: 关于可访问性的 7 个地方（For 每个人）
wordpress_id: 1901
categories:
- 设计
tags:
- ARIA
- Color Safe
- css
- Dribbble
- Evernote
- gmail
- icon
- LinkedIn
- Salesforce
- WAI
- WCAG
- 占位符
- 可访问性
- 表单
---


	
  * 原文地址（original source）：[https://medium.com/salesforce-ux/7-things-every-designer-needs-to-know-about-accessibility-64f105f0881b](https://medium.com/salesforce-ux/7-things-every-designer-needs-to-know-about-accessibility-64f105f0881b)

	
  * 作者（author）：[https://twitter.com/jessehausler](https://twitter.com/jessehausler)





* * *



可访问性使有障碍的人能够对网络进行感知、理解、导航、交互以及贡献。设想这样一个世界，开发人员了解可访问性的方方面面。你设计，他们开发……非常完美。在那个世界里，只有设计本身使有障碍的人在使用产品上遇到困难。

为了让你的产品成为符合 [Section 508](http://www.section508.gov/section-508-standards-guide) 和 [Web 内容无障碍指南（简称 WCAG）](http://www.w3.org/TR/WCAG20/)【注1】的最小化标准的“设计准备”，这些指南将包含你需要知道的主要方面。剩下的就取决于开发和质量测试了。


### 1.可访问性不是创新的阻碍


可访问性不会迫使你做出丑陋、单调或杂乱的产品。在你考虑设计时，它将引入一组需加以考虑的约束。这些设计约束将给你新的想法，以探索面向所有用户的、通往更好产品的道路。

当你通读这些指南时，要记得我们不是为了设计同行而设计。

[![this-is-so-meta](http://www.labazhou.net/wp-content/uploads/2015/04/this-is-so-meta.png)](http://www.labazhou.net/wp-content/uploads/2015/04/this-is-so-meta.png)

为将要和你的产品交互的、形形色色的用户而设计。

[![为每个人设计](http://www.labazhou.net/wp-content/uploads/2015/04/design-for-everyone.png)](http://www.labazhou.net/wp-content/uploads/2015/04/design-for-everyone.png)

用户包含了盲人、色盲或弱视，他们有聋子或听力困难的人，临时或永久的移动性障碍的人，或者是认知障碍的人。为年轻人、老人、有影响力的人、普通用户和只享受有质量体验的人设计。

拥抱这些可访问性指南，还有设计约束。要创造让人尖叫的产品，它们就是挑战的一部分。


### 2.不要把颜色做为信息传送的唯一视觉方式


对于那些不能从一种颜色区分另一种颜色或有困难的人们，是有帮助的。这包含了色盲（12 名男性中有 1 名，200 名女性中有 1 名）、弱视（30 个人中有 1 个）或盲人（188 人中有 1 个）。

使用颜色高亮或补充已经可见的东东。

这个例子以灰度模式呈现，你能说出错误状态下有几个表单域吗？

[![灰度显示的错误状态表单](http://www.labazhou.net/wp-content/uploads/2015/04/form-fields-in-error-1.png)](http://www.labazhou.net/wp-content/uploads/2015/04/form-fields-in-error-1.png)

看到该灰度模式下的人说的答案是 1 个，“人类验证”表单域。这是因为其内部带有叹号的三角标记标示出了错误的地方。

现在看看以颜色呈现出来的同样屏幕。在错误状态下有多少个表单域？

[![颜色显示的错误状态表单](http://www.labazhou.net/wp-content/uploads/2015/04/form-fields-in-error-2.png)](http://www.labazhou.net/wp-content/uploads/2015/04/form-fields-in-error-2.png)

有了颜色，答案变成了，“共有 4 个”。

有很多可接受的方式使得这个表单视觉上具备可访问性。你可以把红色的三角图标放到所有的错误表单域里。你可以使用文本来说明或解释为什么某个表单域有错误。你可以使用提示、粗边框、粗体文本、下划线、斜体等。选择是无限的，但是唯一的规则是不要只用颜色。

你是如何设计注册表单，以致于颜色不是呈现错误表单域的唯一视觉方式？


### 3.在文本和背景之间保证有足够的对比。


[根据 WCAG 指出的](http://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)，文本及其背景的对比度至少在 4.5 到 1 之间。如果你的字体至少在 24 px 或 19 px 粗体，那么最小可降到 3 到 1。

该指导有助于弱视、色盲或恶化视力的人阅读你屏幕上的文本。

这意味着，当文本是 24 px、19 px 粗体、或更大时，你能在白色背景上使用的最小灰度是 #95959。

[![大号字体](http://www.labazhou.net/wp-content/uploads/2015/04/big-text-1.png)](http://www.labazhou.net/wp-content/uploads/2015/04/big-text-1.png)

对于小一些的字体，你能在白色背景上使用的最小灰度是 #76767。如果你有一个灰色的背景，文本需要更深一些。

[![正常的字体](http://www.labazhou.net/wp-content/uploads/2015/04/normal-text.png)](http://www.labazhou.net/wp-content/uploads/2015/04/normal-text.png)

有一些不错的、包括 [Color Safe](http://colorsafe.co/) 在内的工具，帮你找到用于设计的可访问性调色板。还有 [WebAIM’s Color Contrast Checker](http://webaim.org/resources/contrastchecker/)，用来测试你已经选中的颜色。

处于禁用状态的 Logo 或元素不在此标准之列。这包括不可点击的按钮或菜单项。用于表单域的占位符或 ghost 文本**不**应该排除在该标准之外。

下面是来自某个流行博客站点的例子，其文本对比度低于标准。只有巨大的字母”M“的对比度满足标准。

[![medium的对比度演示](http://www.labazhou.net/wp-content/uploads/2015/04/medium-contrast-standards.png)](http://www.labazhou.net/wp-content/uploads/2015/04/medium-contrast-standards.png)

下面 BBC 的例子显示了及格的色彩组合的UI。既然它们的最小灰度是 #76767，那么你能分清它们正积极地通过了对比度吗？

[![BBC通过的颜色组合](http://www.labazhou.net/wp-content/uploads/2015/04/bbs.png)](http://www.labazhou.net/wp-content/uploads/2015/04/bbs.png)

我和 Salesforce 设计系统团队一起工作，并以此为荣，他们在 Salesforce 移动应用上遵循了色彩对比指南。

[![Sailesforce通过的颜色](http://www.labazhou.net/wp-content/uploads/2015/04/passing-colors-in-salesforce.png)](http://www.labazhou.net/wp-content/uploads/2015/04/passing-colors-in-salesforce.png)

探索使用高对比度的色彩组合。做过这种训练的设计师常常惊叹于他们是多么地喜欢高对比度设计。我非常自信你也想找到使用最小化可允许的对比，它不会分散对你产品的注意力。

更多关于色彩对比的信息，可参看 [Projectors Don’t Lie](https://medium.com/salesforce-ux/projectors-dont-lie-b85ef628b04) 和 [Accessible Interface Design](https://medium.com/salesforce-ux/accessible-interface-design-d80e95cbb2c1)。


### 4.为键盘焦点提供视觉焦点标示


让我们先感谢一下已经给予了现代 web 设计师的 reset 样式表和所有的工具集。没有 reset 样式表，在不同设备和浏览器上创建一致性体验就变得非常困难。

让我们再谴责一下 reset 样式表，因为它对于在互联网传播最广的可用性错误负有责任。

    
    :focus {outline: 0;}


这一行 CSS 使得视力正常的用户几乎不可能只使用键盘访问网站。幸运的是，自从最初的 reset CSS 发布之后，包括 [Eric Meyer](http://meyerweb.com/eric/thoughts/2011/01/03/reset-revisited/) 在内的很多知名网站已经更新了，去掉了不加样式的 :focus 伪类。

没有样式的焦点意图是足够高尚的：移除默认的焦点样式，是为了设计师和开发人员用他们网页样式的视觉和配套来取代。足以容易到不喜欢 IE 或 Firefox 下的灰色虚线边框、或 Chrome 下的蓝色光晕。

[![IE、Firefox、Chrome下的焦点样式](http://www.labazhou.net/wp-content/uploads/2015/04/default-visual-focus.png)](http://www.labazhou.net/wp-content/uploads/2015/04/default-visual-focus.png)

问题是，大多数网站没有创建他们自己的焦点样式。这些焦点指示符，对于键盘用户的成功有着基础作用，却在 web 上严重缺席了。

做为体验一个常常没有提供视觉焦点的网站的、一种快速练习，打开一个标签，访问为公司制作[移动站点](http://www.labazhou.net/2014/12/making-case-mobile-first-designs/)的网页。重复按下 TAB 键浏览这个页面。当你浏览时，你能看到一个视觉焦点指示器吗？或许你在页面上的某些链接上看到了而不是全部？考虑下这种效果是如何影响那些只使用键盘和 web 交互的人们的。

如果你是 Mac 用户，你可能需要开启 系统偏好设置 > 键盘 > 快捷键 下的全键盘控制。它位于底部。

[![Mac下的全键盘设置](http://www.labazhou.net/wp-content/uploads/2015/04/mac-preferences-keyboard.png)](http://www.labazhou.net/wp-content/uploads/2015/04/mac-preferences-keyboard.png)

如果你移除了默认焦点，请用一些“更好的”样式取代你的浏览器所提供的样式。

在下面的例子，BBC 使用一个色条来指示哪个部分的链接拥有焦点。

[![BBC的导航焦点色条](http://www.labazhou.net/wp-content/uploads/2015/04/bbc-color-bar.png)](http://www.labazhou.net/wp-content/uploads/2015/04/bbc-color-bar.png)

Twitter 使用默认焦点和显示键盘焦点提示的组合。icon 也从灰色变成了绿色。这是三种独立的视觉，为键盘用户标示了焦点。

[![twitter的焦点样式](http://www.labazhou.net/wp-content/uploads/2015/04/twitter-keyboard-focus.png)](http://www.labazhou.net/wp-content/uploads/2015/04/twitter-keyboard-focus.png)

在提供你自己的焦点状态时，要确保移除了默认状态，这样你就不会出现下面例子中的情况，Chrome 的蓝色矩形覆盖掉了该菜单的蓝色区块。


### 5.当心表单。


最近几年我们已经体验了表单域的退化。由于更加极简的方式，现代设计已经抛弃了传统的识别属性和用于交互的承担特征【注2】。今天的表单，缺乏两种特定项，它们对于可访问性是至关重要的：清晰定义的边界和可见的标签。


#### 没有边框的表单


下面是一个传统文本输入框的例子。它有着定义好的边界的矩形。它还填充了颜色，但是不必去填写。还有一个可见标签，在该例子中，它位于输入框左侧。

[![表单的输入框](http://www.labazhou.net/wp-content/uploads/2015/04/form-label.png)](http://www.labazhou.net/wp-content/uploads/2015/04/form-label.png)

明确定义了边界的表单域，对于移动性障碍和认知障碍的人是重要的。明白点击目标的位置和尺寸，对于使用标准的或[自适应指示设备](http://iuadapts.indiana.edu/technology/hardware/mice/index.html)的人也是重要的。存在认知障碍的用户，对于没有普通视觉指示的表单域，可能难以找到和交互。

下面的例子是来自于一款流行的记录笔记的应用。

[![流行的笔记应用](http://www.labazhou.net/wp-content/uploads/2015/04/search-notes.png)](http://www.labazhou.net/wp-content/uploads/2015/04/search-notes.png)

屏幕上只有一个输入框。你能够猜出表单域的边界吗？点击“search notes”这句话的某个地方，才会把你放入输入框里面。

下面的例子来自于一个流行博客平台的、没有边界的表单域。这个页面有两个输入框。我为了进入“Tell your story...“文本域，我应该点击屏幕哪个地方呢？

[![Medium的添加文章表单](http://www.labazhou.net/wp-content/uploads/2015/04/medium-form-fields.png)](http://www.labazhou.net/wp-content/uploads/2015/04/medium-form-fields.png)

下面是同样的屏幕，为了显示文本域边界，而添加了蓝色矩形。如果你点击这个区域的下面区域，什么也不会发生。

[![Medium的添加文章表单（焦点）](http://www.labazhou.net/wp-content/uploads/2015/04/medium-form-fields-2.png)](http://www.labazhou.net/wp-content/uploads/2015/04/medium-form-fields-2.png)

下面是另一个记录笔记的设计例子。它没有使用传统的输入框视觉，而给有障碍的用户提供了更多的信息。笔记的标题位于两条水平线之间，用户点击底部两条线之间的任何地方，就可以开始敲入他们的笔记。

[![非标准但好用的表单](http://www.labazhou.net/wp-content/uploads/2015/04/note-taking-form.png)](http://www.labazhou.net/wp-content/uploads/2015/04/note-taking-form.png)

你能够为这些设计师们想到其它方案吗？你是怎样设计记录笔记或博客发布的应用的？


#### 没有标签的表单


标签用于告诉用户对应域的目的，当焦点位于输入框内部时，说明它们的用处，甚至在填完输入框之后，仍然保持着。占位符文本对于视觉化标签而言，属于表现不够好的替代。

它们通常具有低对比度。下面的 7 个例子，只有 1 个例子有着足够的对比度，符合我们需要的 4:5:1 的比率。

[![对比度的7个例子](http://www.labazhou.net/wp-content/uploads/2015/04/form-label-focus.png)](http://www.labazhou.net/wp-content/uploads/2015/04/form-label-focus.png)

占位符文本消失了。在下面的例子，我应该在文本输入框填写什么呢？对于 JetBlue【注3】的例子，我应该输入用户名、邮箱地址、还是我的 TrueBlue 号码？对于 Caviar 的例子，我应该通过敲入我喜欢的食物、首选餐厅还是我的邮箱，才能“Get Started”呢？价格域是最小的和最大的、上和下、或者前后颠倒？

[![Trueblue的注册表单](http://www.labazhou.net/wp-content/uploads/2015/04/trueblue-form.png)](http://www.labazhou.net/wp-content/uploads/2015/04/trueblue-form.png)

和上面呈现的价格域相比，下面是更具可访问性的设计方式。我们将看到标签、最小和最大、甚至在我们填好之后。

[![价格输入框](http://www.labazhou.net/wp-content/uploads/2015/04/price-field.png)](http://www.labazhou.net/wp-content/uploads/2015/04/price-field.png)


### 6.避免组件识别危机




<blockquote>Q: 一个菜单在什么时候就不再是菜单了？
A：当它是一个非模态对话时。</blockquote>


这个问题是当今最大的 web 可访问性方面的问题核心。为了完全理解这一点，请思考 W3C [对于设计模式的 Authoring Pratices](http://www.w3.org/TR/wai-aria-practices/#aria_ex)。对于今天普通的、包括表单、模型、自动完成、树、标签页集合等在内的设计模式，这是一份如何开发一种可访问性版本的指导。

这些模式的每一种，都有一个具体的、期望的 HTML 语义、键盘行为和可访问的富因特网应用程序（[ARIA](http://www.w3.org/WAI/intro/aria.php)）属性用法的集合。这些 ARIA 属性指导屏幕阅读器用户，当使用键盘时，该怎样与组件交互。当用户和组件互动时，它们还提供了状态更新。例如，它们指导用户通过使用方向键在列表中向上、向下移动来实现交互。

满足不起眼的自动补全输入提示。

[![自动补全](http://www.labazhou.net/wp-content/uploads/2015/04/autocomplete.png)](http://www.labazhou.net/wp-content/uploads/2015/04/autocomplete.png)

下面是相同的输入提示，但是每个列表项前面有个 icon。

[![输入提示](http://www.labazhou.net/wp-content/uploads/2015/04/typeahead.png)](http://www.labazhou.net/wp-content/uploads/2015/04/typeahead.png)

这些都是必要的、完全相同的 UI 模式。用户敲入一个输入框。经过输入文字过滤后的一组结果出现在下面。然后用户能够使用方向键或鼠标，从列表中定位或选择其中一项。

下面是带有识别危机的自动补全的例子。用户不仅可以从列表中过滤或选择一项，而且他们能通过点击铅笔或垃圾箱图标来选择编辑或删除每一项。这两个按钮的添加让这里的自动补全产生了识别危机。

[![非模态对话的菜单](http://www.labazhou.net/wp-content/uploads/2015/04/menu.png)](http://www.labazhou.net/wp-content/uploads/2015/04/menu.png)

这部分地引起了可访问性问题，因为它破坏了自动补全的、标准键盘交互模型。辅助技术常常不能传达识别、操作和混乱组件的状态，因为 W3C 的 Web 可访问性倡议（WAI）还没有对传播这种 UI 定义一个说明。

对于菜单也有同样的规则。下面的例子来自 Virgin America，视觉上非常类似，只有右侧的下拉列表是一个真正的“菜单”。左边的下拉列表是一个非模态对话。

[![非模态对话菜单对比](http://www.labazhou.net/wp-content/uploads/2015/04/non-modal-dialog.png)](http://www.labazhou.net/wp-content/uploads/2015/04/non-modal-dialog.png)

菜单是给用户提供一个选择列表的小工具。如果我们在每行提供了多种选择，正如左侧的那个例子，那么它就不再是菜单了。键盘交互从使用方向键变成了使用 TAB 键。它改变了键盘焦点的处理方式，以及当下拉列表关闭后该何去何从。

和上面自动补全的例子不一样，幸运的是，非模态对话有可访问性。了解它们之间的区别和对用户体验的影响。理解少量的设计变化是怎样导致用户交互模型变化的。这使你能够为产品选择合适的模式。


### 7.不要让人们悬停才能找到东西


这个原则主要面向运动障碍相关的人群。它包含具有视力的、只使用键盘的用户、和使用诸如 [Dragon NaturallySpeaking](http://www.nuance.com/dragon/index.htm) 语音识别工具【注4】和网页交互的人们。键盘用户和 Dragon 之类的辅助技术，依靠于屏幕上可见的可操作项。如果一个链接或按钮不能被 Dragon 看到，它也将不能被口头上“点击”。如果只使用键盘的用户不能看到页面上存在的按钮，我们怎能期望他们导航到最终出现的空白区域呢？

下面是一个来自于带有 Dragon NaturallySpeaking 的 Gmail 截屏，显示了覆盖着带有供识别的数字的超链接。用户现在能够大声说出一个数字来激活一个链接。如果链接只有在区域被悬停时才会出现，那该怎么办？我们将有数字出现在空白旁边。

[![Dragon NaturallySpeaking 的 Gmail 截屏](http://www.labazhou.net/wp-content/uploads/2015/04/gmail-dragon.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/04/gmail-dragon.jpeg)

我理解，在悬停状态下隐藏可操作项的实践是怎样流行起来的。它是计算机科学家艾伦·凯【注5】提出的、精心构建的启发式可用性的解决方案。


<blockquote>“简单的东西就要有简单的设计，而碰到复杂的情况时也应该能应付。”
------艾伦·凯</blockquote>


我是这种启发式的忠实信奉者，但是它应该以一种让复杂成为用户可能应付的方式，包括那些有障碍的人们。不幸的是，对于可访问性，很多东西都变成了下面的句子，它不是引用艾伦·凯的话：


<blockquote>“主要的东西应该是可见的，第二位的东西应该悬停时才可见。”</blockquote>


不要在悬停状态隐藏操作和信息，而要探索更多可包含的替代方式。



	
  * 把第二位的操作放在菜单里（或非模态对话），不要使用悬停状态隐藏这种触发。

	
  * 降低第二位图标的对比度，在悬停时要加深它们。

	
  * 对于较大的悬停，使用矩形项做为触发。对于启动充满内容的悬停，信息图标比起空白，算是更好的触发项。


举个 LinkedIn 的例子。下面是我的个人首页截屏。

[![LinkedIn个人主页名片-1](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-1.png)](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-1.png)

下面是我把鼠标放到个人卡片之后的情形：

[![LinkedIn个人主页名片-2](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-2.png)](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-2.png)

突然有了视觉上的指示，我可以单个编辑这个页面上的域，包括我的名字、头衔、之前的工作、教育、甚至我的首页照片。做进一步体验，当我悬停到我的头衔上时，文本变成了蓝色，说明我打算点击了。

[![LinkedIn个人主页名片-3](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-3.png)](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-3.png)

这种设计可能引起某些用户群体的可访问性问题，下面是解决方案。我让更小的铅笔出现在域的旁边。它们总是可见的。

[![LinkedIn个人主页名片-4](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-4.png)](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-4.png)

当我在一个域上悬停时，蓝色才出现。

[![LinkedIn个人主页名片-5](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-5.png)](http://www.labazhou.net/wp-content/uploads/2015/04/linkedin-profile-banner-5.png)



当出现这种解决方案时，设计师做出的反应是问：


<blockquote>“有点儿多，不是吗？”</blockquote>


或许吧，不过它是这个问题的唯一可能的解决方案。而且，它只出现在我自己的个人首页里。一个人要花多少时间看自己的 LinkedIn 首页？这种级别的“量级”对于通用的可访问性，是公平的折衷吗？如果我们不喜欢这个铅笔的特定使用，那么我们还能提供其它的承担特征吗？

下面是来自 Evernote 的另一个例子。这是笔记的列表视图。当用户的鼠标悬停一行时，四个可操作的图片出现了。

[![evernote的笔记列表](http://www.labazhou.net/wp-content/uploads/2015/04/evernote-icon.png)](http://www.labazhou.net/wp-content/uploads/2015/04/evernote-icon.png)

对于这个例子，我愿意让设计师探索总是显示这四个图标的情况。一种可能的解决方案将是一直显示这些图标。它们可以是白色行里的绿色，或反过来。

[![evernote的笔记列表-2](http://www.labazhou.net/wp-content/uploads/2015/04/evernote-icon-2.png)](http://www.labazhou.net/wp-content/uploads/2015/04/evernote-icon-2.png)

这种解决方案也可以称作“多”，但请记住我们不是为设计师而设计。我们是为形形色色的人设计，他们有着不同的需求和使用计算机的不同技能。



* * *



从表面看，把这些限制用到你对组件、悬停状态和视觉设计上，好像限制了你的创新。如果有一些的话，这些指南将推动你创新的限制，因为你会发现视觉上令人愉悦的设计能够适用于更加宽泛的用户群体。

有了正确的关注，你将发现任何设计挑战都是以满足你的主管、市场团队、Dribbble 关注者和所有用户的方式来达成，包括有障碍的人们。



* * *



**作者简介**

Jesse Hausler 是可访问性领域、有着 12 年经验的老兵。他目前是 Salesforce 的重要可访问性专家，在这里已经四年了。特别感谢 [Cordelia McGee-Tubb](https://twitter.com/cordeliadillon)，是他才有了本文用到的让人尖叫的插图。



* * *






	
  * 注1：网页亲和力（又称网络无障碍、网络可达性或网络可用性）旨于确保任何人都有办法获取放在网页上的媒体内容——无论人们是否遭遇了身体、心理或技术上的障碍，都不会妨碍人们接收作者所发布的信息。也就是让网上的内容“易于亲近”，易于获取、利用。[http://zh.wikipedia.org/wiki/網頁親和力](http://zh.wikipedia.org/wiki/網頁親和力)

	
  * 注2：环境赋使（affordance），或称为预设用途、可操作暗示、支应性、示能性等，指一件物品实际上用来做何用途，或被认为有什么用途。也就是说在物品的某个方面，具有让人明显知道该如何使用它的特性。例如门提供“打开”的功能，椅子提供“支撑”的功能。人们得知如何使用物品有一部分来自认知心理学，另一部分来自物品的外形。[http://zh.wikipedia.org/wiki/%E6%89%BF%E6%93%94%E7%89%B9%E8%B3%AA](http://zh.wikipedia.org/wiki/%E6%89%BF%E6%93%94%E7%89%B9%E8%B3%AA)

	
  * 注3：捷蓝航空是美国一家廉价航空公司，由捷蓝航空公司（JetBlue Airways Corporation，NASDAQ：JBLU）拥有。主要营运美国内陆航线和来往加勒比海、巴哈马和百慕大的国际航线。[http://zh.wikipedia.org/wiki/%E6%8D%B7%E8%97%8D%E8%88%AA%E7%A9%BA](http://zh.wikipedia.org/wiki/%E6%8D%B7%E8%97%8D%E8%88%AA%E7%A9%BA)

	
  * 注4：Dragon NaturallySpeaking是一个语音识别软件包。Dragon NaturallySpeaking让忙碌的专业人士创建文档、报告、电子邮件、填写表格和工作流程，而这一切只需要说就可以完成。[http://baike.baidu.com/view/8438264.htm](http://baike.baidu.com/view/8438264.htm)

	
  * 注5：艾伦·科提斯·凯伊（英语：Alan Curtis Kay，1940年5月17日－），美国计算机科学家，在面向对象编程和窗口式图形用户界面方面作出了先驱性贡献，他是Smalltalk的最初设计者。[http://zh.wikipedia.org/wiki/%E8%89%BE%E4%BC%A6%C2%B7%E5%87%AF](http://zh.wikipedia.org/wiki/%E8%89%BE%E4%BC%A6%C2%B7%E5%87%AF)


