---
author: viviworld
comments: true
date: 2016-02-18 08:47:23+00:00
excerpt: 做为工程师和设计师，我忙于业余项目，从中学到了新技术，技能得到了提升，还锻炼了我的创新能力。通过开发业余项目，我明白了，保持在最后期限完成事情的激情）。本文讨论一些有价值的独立项目管理技能。
layout: post
link: http://www.labazhou.net/2016/02/how-to-ship-side-projects/
slug: how-to-ship-side-projects
title: 怎样交付业余项目
wordpress_id: 3095
categories:
- 编程
tags:
- api
- DRY
- Google Analytics
- jquery
- nvALT
- Simplenote
- Slack
- 业余项目
- 命令行
- 想法
---


	
  * 原文地址（original source）：[http://blog.andyjiang.com/how-to-ship-side-projects/](http://blog.andyjiang.com/how-to-ship-side-projects/)

	
  * 原文作者（author）： Andy Jiang（[@andyjiang](https://twitter.com/andyjiang)）





* * *



做为工程师和[设计师](http://blog.andyjiang.com/everyone-is-a-designer/)，我忙于业余项目，从中学到了新技术，技能得到了提升，还锻炼了我的创新能力。通过开发业余项目（[稍微有用的](http://www.andyjiang.com/sw)和[天马行空的](http://bottomofproducthunt.com/)），我明白了，保持在最后期限完成事情的激情，十分重要（我的 GitHub 代码库常常沦为鬼城，因为我还没定下来采用什么技术、或构思好最终的用户流程）。本文讨论一些有价值的独立项目管理技能，是它们让我保持专注、并一直前行。


### 为什么？


[![prSqGTW](http://www.labazhou.net/wp-content/uploads/2016/02/prSqGTW.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/prSqGTW.gif)

首先，要自问为什么？你致力于业余项目背后的动机是什么？为了学习新技术和框架吗？为了做一些供人们使用的东西吗？或只是为了挑衅你的朋友，是吧，[Jake](https://twitter.com/jpetey75)？

你的目标塑造了你开展业余项目的方法。举个例子，如果你想学习新技术，那么，你或许不应该就交付完整产品开展优化。反过来，如果你想开发供人们使用的东东，就要选择你最擅长的技术了。

对我而言，就是为了挑衅 Jake，因此我坚持使用 [Koa](http://koajs.com/)，以及超级臃肿的 [jQuery](https://jquery.com/)（开玩笑呢，尽管不太对）。


### 记下来！


[![写下来](http://www.labazhou.net/wp-content/uploads/2016/02/anigif_enhanced-buzz-28755-1376341683-4.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/anigif_enhanced-buzz-28755-1376341683-4.gif)

每个人都要被白天各个时间段里的灵感所侵扰。养成一个习惯，把随时萌生的每个潜在想法记下来（有时候想法甚至不完整，却是一种启发：写下一句话，以激励自己将其考虑成熟）。从考虑想法、到便捷地回忆起来，要确保整个过程尽可能顺畅。

一些人喜欢给他们自己发送邮件、或在 Slack 上和 [Slackbot](https://www.slack.com/) 聊天。

我使用 [nvALT](http://www.macworld.com/article/2047073/nvalt-review-makes-writing-and-finding-plain-text-notes-simple.html)（免费、文本式的 Mac app，我使用快捷键，就可新建空白的笔记），后端是 [Simplenote](http://simplenote.com/)（也免费；它们提供了 iPhone app，我可以在路上使用）。单就想法（idea），我有一个巨大的条目（还有一个单独的”blog idea“条目）：

[![nvALT 截图](http://www.labazhou.net/wp-content/uploads/2016/02/UgOo2yA-600x378.png)](http://www.labazhou.net/wp-content/uploads/2016/02/UgOo2yA.png)

它们甚至不需要写得太具体！嗯，能让你回忆起来即可。

这意味着，当你清晨或晚上空闲时，就可以查阅你的笔记了。然后，你就能挑出你最喜欢的、或深有感触的想法，并着手规划出来。


### 一次只做一件事


[![uYdtfYY](http://www.labazhou.net/wp-content/uploads/2016/02/uYdtfYY.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/uYdtfYY.gif)

业余项目的风险在于总想兼顾到各个方面。你开始做线框图、编写服务器路由逻辑，同时还考虑着用例。不要这样做！频繁切换各种情景和做决定，将导致精神和情绪疲劳，最终减慢你的速度。

一次只做一件事情。这意味着先做产品经理，并回答如下问题：



	
  * 目的和最终目标是什么？

	
  * 主要的用例是什么？（理想情况下，你应该仅从一个用例开始）

	
  * 为了开发这个项目，我手头可用的工具有哪些？

	
  * 你的目标用户是谁，怎样才能到达网上用户？

	
  * 我应该为这个项目取什么名字？


_注：对我而言，选择一个聪明有趣的名字，常常促使我付出十分之一的时间。正因如此，我愿意用 1-2 天时间思考名字。如果我找不到合适名字，我就取个模糊的项目名字，期望以后碰到更理想的。_

产品管理方面的其它任务包括：



	
  * 考虑完美的用户流程

	
  * 建立粗略的、看似合理的原型，等等。

	
  * 研究 API、文档等，准备好所需材料，当你着手开发时，各种资源都容易找到。

	
  * 当你做工程师和设计师的工作时，计划要宏观一些。


由于我有一份全职工作，在晚上到家时，很容易忽视这些重要的步骤。为了使我目标明确，我喜欢添加 Google 日历的事件，在说明（description）里写上需要完成的、言简意赅的任务：

[![Google 日历新建事件](http://www.labazhou.net/wp-content/uploads/2016/02/wYA6WNF-600x252.png)](http://www.labazhou.net/wp-content/uploads/2016/02/wYA6WNF.png)

写到日历事件后，我就能放空思想去做其它事情，当到了提醒时间，我就能快速切换到记录的任务中。


#### 提醒：大胆地缩小范围


我喜欢针对交付进行优化，因此，大胆地缩小范围就显得重要了。这种哲学通常指引我先编写资源库或命令行界面[note]命令行界面（英语：command-line interface，缩写：CLI）是在图形用户界面得到普及之前使用最为广泛的用户界面，它通常不支持鼠标，用户通过键盘输入指令，计算机接收到指令后，予以执行。也有人称之为字符用户界面（CUI）。[https://zh.wikipedia.org/wiki/%E5%91%BD%E4%BB%A4%E8%A1%8C%E7%95%8C%E9%9D%A2](https://zh.wikipedia.org/wiki/%E5%91%BD%E4%BB%A4%E8%A1%8C%E7%95%8C%E9%9D%A2) [/note]，而不是开发带有前端 UI 的 web 服务（尽管我做的很多东东最终只是命令行界面）。

考虑最终产品应该怎样运行、尤其是终端用户和最终项目交互的数百种方式的优缺点，所产生的认知开销，常常破坏你的激情，使项目生产力停滞不前。把项目分成更小的块儿来考虑，就显得重要了：你想让工程师怎样和你的资源库交互？你想让 App 开发者怎样和你的 API 交互？

这种方式意味着，你正在把问题分解为越来越小的块儿，比起你一下子解决各种问题，常常更加可控。


### 站在用户角度考虑问题


[![站在用户角度考虑问题](http://www.labazhou.net/wp-content/uploads/2016/02/2aQlQOj.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/2aQlQOj.gif)

用户（不管是你本人、还是你想象中的特定人群）使用项目的方式，应该决定了项目的结构。关于使用 Storyboard 规划设计等，已经有很多文献提到了，这里不展开论述。

注意，这些用户流程能为操纵必要数据提供指导，方便用户完成他们的工作。

你在开发某个资源库吗？[最小化的必要参数是什么](http://www.labazhou.net/2014/01/mvp-minimum-viable-product/)，你的用户用最少的调用，就能满足需求吗？

API 该怎么做？开发者用你的 API 要完成什么样的工作？关于提供哪些路由或暴露哪些参数，你是如何决定的？

web app 还是原生 app？为了直观、便利地引导用户，UI 需要连通吗？

如果是 web app 的实际设计方面，那么对于最终产品的样子，我通常保持宽松的想法。但是不到最后一刻，我不会编写任何 CSS 或 `margin: 0 auto;`。还有，我重度依赖 [Twitter 推出的 Bootstrap](http://getbootstrap.com/)，因为娴熟和便捷。

此时，我就把工程任务分解为一个个 TODO 了，然后把它们记下来（通常以 [GitHub issue](https://github.com/lambtron/snoobear/issues/1) 的形式）。当我动手开发时，我不必再挂念那些决定，它们会影响我的状态。


### 先写代码，再重构


[![写代码](http://www.labazhou.net/wp-content/uploads/2016/02/jxj02uq.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/jxj02uq.gif)

如果你曾有过不得不写一篇文章或博文的经历，那么你会明白，有时候写东西没那么容易。关于写作，我收获了一些有帮助的经验，即：不要同时写和改。

写作（创造内容）和修改（润色和移除内容）的行为，将用到大脑的两个部分。同时进行这两个行为，会取得相反效果：虽然过了三个小时、喝了两杯咖啡，但是你仍然推敲着同一个句子。

写代码也是如此。如果你的目标是交付，那么谁会在意（至少现在不会）你因拷贝代码而违法了 DRY 原则。把第十个 callback 放在一个 400 行代码的 index.js 文件里，开干吧，当你切换到「修改」状态时，再考虑重构吧。

如果你对持续优化、或维护代码感兴趣，那么在未来，你可以重新查看、整理、并提高可读性。


### 附：了解你的用户


如果你打算把你的业余项目展示给其他人，那么，添加一些粗略的追踪供以后分析，是大有裨益的。我推荐用 [Segment](https://www.segment.com/) 和 [Google Analytics](https://www.google.com/analytics/)（均免费！）。

你就可以测评 app 中的流量和使用情况了，还能看到流量从哪儿来（如果是 web app 的话）。你还能配置关键转化事件，进而测量你的漏斗模型，看看用户是在哪个环节离开的、等等，这样你就能改善产品了。

如果你想深入数据分析，并有决心使你的业余项目取得增长，这里推荐[一篇关于营销栈($9/月)的文章](http://robsobers.com/9-dollar-marketing-stack-step-by-step-setup-guide/)。

声明：我供职于 [Segment](https://www.segment.com/)。


### 交付！


[![d940007b8ecb3e32ab19214ce09ba0a7.700x394x5](http://www.labazhou.net/wp-content/uploads/2016/02/d940007b8ecb3e32ab19214ce09ba0a7.700x394x5.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/d940007b8ecb3e32ab19214ce09ba0a7.700x394x5.gif)

我想说，这是产品开发声明周期最困难的阶段，这时候你已经开发了 90%，大部分运行正常，还算看得过去。需要强调一下，这最终取决于你的目标。如果你只是开发让朋友使用的东西，就展示给他们寻求反馈。否则，如果你试着让它出现在 [Product Hunt](https://www.producthunt.com/) 上，就多花一周，精心打磨设计、编写测试、确保数据分析都符合预期。

我在开发东西时，用户通常出现在脑海中。我会搞清楚目标用户在网上哪些地方闲逛（他们一般使用什么工具、浏览哪些论坛、[阅读哪些 reddit 子板](http://blog.andyjiang.com/snoobear-easily-manage-multiple-reddit-submissions/)、他们位于 Slack 的哪个频道、他们阅读哪种 newsletter 或博客），然后在那里分享最终产品。如果我在意客户开发，那么我会试着获取尽可能多的反馈。

主要结论就是，考虑你的动机，然后进行优化。如果你为了交付而优化，就要格外留意规划、研究、设计和开发，有助于保持专注，更重要的是，保持激情，激情能帮助你推出最终产品并呈现给用户。
