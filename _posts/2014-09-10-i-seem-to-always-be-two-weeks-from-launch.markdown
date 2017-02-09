---
author: viviworld
comments: true
date: 2014-09-10 02:50:21+00:00
layout: post
link: http://www.labazhou.net/2014/09/i-seem-to-always-be-two-weeks-from-launch/
slug: i-seem-to-always-be-two-weeks-from-launch
title: 貌似离发布总还有两周
wordpress_id: 1053
categories:
- 编程
- 软件
tags:
- 37signals
- AngularJS
- bug
- Codebase
- javascript
- nodejs
- Ruby on Rails
- SEMrush
---

貌似不管我做什么、计划什么和开发什么……我总是离发布[Workado](http://workado.com/)还有两周时间。我一直在思考、甚至在说，这就是现在起3个月内最好的阶段。

这违背了我对大部分人说的话：


<blockquote>“先发布，然后再规划后面的。”</blockquote>


幸运的是，它还没有回来在后面咬我。来自Groove的Alex Turnball[记录了](http://groovehq.com/blog/feature-release-dates)当它尽量提供未来功能的发布日期时，它是如何伤害了他在一些客户面前的名声的。我没有给我们实际上要发布的工作设置期限，因为那个故事以及我认为它总是错误的。

尽管如此，我确实相信，距离发布第一个web应用程序还有两周是合理的。相较于基于业务的服务，还有一个完全不同的故事，比如《[I was able to launch last week after 7 days](http://justinmcgill.net/one-week-startup-how-i-went-from-idea-to-launch-in-7-days/)》。

下面是确实没有根据计划进行的简短情况，我希望有人在某些地方能够吸取我的经验，以克服他们自己的一些延期。


### 找到合适的开发人员


Workado是我为[upswinginteractive.com](http://upswinginteractive.com/)团队使用而开发的一套系统，已经投入使用3年了，不过直到去年，我决定把它做成可让公众获取的独立工具。自然地，我找最初参与的开发人员谈了，他表示感兴趣。

尽管如此我们还是意识到，这个工具将来需要实时更新和更多的客户端接口，这意味着我需要精通JavaScript的人。他是一个Ruby on Rails家伙，因此这行不通。

当所有这一切都搞清楚时，我正在准备内容和营销策略。随后我不得不转换思路，找到具有SaaS经验而且精通JavaScript的、物有所值的开发人员。我尽量通过当地渠道和我的圈子寻找这个人，但是运气不佳。公平起见，最初我希望找到一名对此感兴趣的合作伙伴/合伙人，但是很快知道情况不是这样的。

最终，我[求助于oDesk](http://justinmcgill.net/how-i-use-odesk-to-manage-freelancers-and-virtual-assistants/)。我找到一个不错的、对Node.js（后端）和AngularJS（前端）都真正了解的、加拿大开发人员。我本打算支付高价的，我只是觉得他的经验和技能比较值。从长期看，我希望某种意义上，这种支付不会让我失去公平。

现在是2月份，最初的版本预估要花费5周。


### 发布一个Beta版


的确足够了，开发都在按计划进行。到了第5周，我们有了一个可运行的工具。我把整个upswinginteractive.com团队转向了这个环境。

很明显，我们未能在这个时间点发布这个工具，用任务（我们还没有任务模板）在这个系统里获取客户要花很长时间。一些地方和你期望的不一样（下拉的活动列表）。我们不得不调整一些地方让这个工具更加直观，需要一个新手引导等等。

此时的挑战在于，这个开发人员已经着手他的下一个工作，他将一直忙到4月底。他有自己的优先级和要支付的账单，我理解，但是这不代表这件事没有搞砸。


### 自由职业者的挑战


当这个开发人员在5月份空闲的时候，我想我们将在5月中旬发布。这是我的第一个“距离发布还有两周”的时刻。

然而，他仅仅空闲了一周，就有了另一份工作，一直持续到6月份的第一周。

在这段时间，我开始寻找另外的开发人员。在周转不开的日子里，我设法雇佣了3个不同的开发人员。一个我比较熟，但是它有另外的工作，因此没法用。另外两个来自于oDesk的自由职业者，但是不顺手，因为他们没有linux经验，学习时间太长。

幸运的是，我的开发人员想起了其他人，让他过来帮助我在6月中旬搞定。


### 尴尬的bug


我计划在7月7号发布。然而，直到7月中旬，下一个里程碑还没有发布到服务器上，还产生了一些新bug，发现了一些其它bug，我们还经历了持续几天的服务器宕机。

[caption id="attachment_1051" align="alignnone" width="400"][![尴尬的bug](http://www.labazhou.net/wp-content/uploads/2014/09/startup-quote.jpg)](http://www.labazhou.net/wp-content/uploads/2014/09/startup-quote.jpg) 如果你对产品的第一个版本没有感到愧疚，就说明你发布得太晚了。[/caption]

我没有把这个引用的句子定在软木板上，仍然没有让我在当前条件下发布这款工具感到舒服的方法。

我在SEMrush准备了一个博客，但是我不得不暂停了，因为我们没有在7月分发布。8月5号是新的发布日期！

期望不要延期了。

我们来到了9月9号。尽管如此，我还是高兴地通报一下，只有4个未解决的bug，准备发布之前需要解决掉。下面是我们在[Codebase](https://www.codebasehq.com/)上的发布里程碑的截图：

[![codebase上的里程碑截图](http://www.labazhou.net/wp-content/uploads/2014/09/tickets.jpg)](http://www.labazhou.net/wp-content/uploads/2014/09/tickets.jpg)

这意味着我真正觉得我会在即将到来的9月23号发布了。


### 结论




<blockquote>开发投入的时间越多，发布的可能性就越低。
------Jason Fried（37 signals）</blockquote>


这句话对我而言是非常重要的，因为我知道我现在就处于这个节点，项目正在“延期”。尽管如此，我还是在这段时间学到了很多。我享受大部分体验（bug和延期除外），我知道有了这个经验，将对未来的SaaS app发布有帮助。

在它发布的时候（数周之后……），我打算记录发布之前和发布之后我所做的工作。可以在这个博客的微系列里看到，保险起见，请订阅，在右边输入你的email，便于微系列上线的时候收到通知。

原文地址：[http://justinmcgill.net/i-seem-to-always-be-two-weeks-from-launch/](http://justinmcgill.net/i-seem-to-always-be-two-weeks-from-launch/)
