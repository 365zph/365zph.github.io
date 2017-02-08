---
author: viviworld
comments: true
date: 2015-09-16 02:36:30+00:00
excerpt: web 标准的全部意义，从过去到现在，都是向前兼容------无论过去的和现在的浏览器和设备，还是尚未发明的所有优秀设备，都只是为世人创造内容。
layout: post
link: http://www.labazhou.net/2015/09/youre-welcome-cutting-the-mustard-then-and-now/
slug: youre-welcome-cutting-the-mustard-then-and-now
title: 符合标准，永不过时
wordpress_id: 2502
categories:
- 网络
tags:
- HTML
- WaSP
- 响应式设计
- 浏览器
- 渐进式增强
- 移动优先设计
---


	
  * 原文地址（original source）：[http://www.zeldman.com/2015/09/01/youre-welcome-cutting-the-mustard-then-and-now/](http://www.zeldman.com/2015/09/01/youre-welcome-cutting-the-mustard-then-and-now/)

	
  * 作者（author）：[https://twitter.com/zeldman](https://twitter.com/zeldman)





* * *



BBC 对「[符合标准](http://responsivenews.co.uk/post/18948466399/cutting-the-mustard)」【注1】做过超前思考的实践，在提供内容给请求的 web 设备之前，先就某些功能做些测试。每当有年轻开发人员提到这件事时，我就想起了在 The Web Standards Project(WaSP) 【注2】的项目团队和我发明了该思想的情景。按 web 纪元，那应该是 100 万年前的事情了；按人类纪元，应该是 14 年前了，因此，除了我和一些锯齿状的白头发人、以及《[网站重构：应用Web标准进行设计](http://book.douban.com/subject/1230451/)》第一版的读者，没人能够记得。但是我喜欢你们，因此我乐于讲这段故事。

在那些黑暗的日子里，对于 web 开发人员而言，为同一个网站创建的版本数量不低于 4 个，这很常见------针对每种浏览器做一个版本，然后再投入广泛使用。还有一个经典（互补）的做法，那就是发送服务器端请求，搞清楚是哪种浏览器在访问网站内容，随后把配置有该用户浏览器特定怪癖（quirk）、独有标签、和符合标准的网站版本，发送给用户。

这种做法称为「浏览器检测」（browser detection）。一些可访问性方面的拥护者对此有过质疑，除此之外，互联网泡沫时代【注3】没有时间、也不会在意这些拥护者。

但是，在 The Web Standards Project(WaSP) ，我们这些人努力调整了其方向。我们说过，浏览器应该支持相同的标准、而非竞相发明新的 HTML 标签和脚本语言。我们说过，设计师、开发人员和内容生产的人们，应该制作一个可让每个人访问的网站。在我们说的世界里，你无需检测浏览器，因为每个浏览器和设备都能读取 HMTL，都能够得体地呈现你的网站内容。（你就能分享更多的内容，因为你可以把时间放在创造内容上，而不用为相同站点做多个版本。）

为了加速这一进程，我们在 2001 年发起了一场浏览器升级运动。那些参与的人们（[这里有参与的示例](http://www.distributed.net/Webstandards)）使用我们的代码和内容，向用户发送消息，每个平台上、相对符合标准的浏览器都可以获取，并邀请他们试用。如果更多的人使用相对符合标准的浏览器，那么我们就能促使更多设计师和开发人员来创建符合标准的网站（而不是怪癖）。正如更多设计师和开发人员所做的那样，他们激烈地与仍未解决的、不符合标准的难题对抗，使我们能够说服浏览器厂商，让厂商在那些具体的领域里改善其标准的遵从情况。一点一滴、一步一个脚印，我们能够、也将会创造这一壮举。

在 2001 年那次浏览器升级运动中，核心代码是浏览器检测方面的、功能检测的第一个实例。下面是其工作原理。在创建一个合法网页之后，你把该脚本插入你文档的 `head` 标签、或全局 JavaScript 文件里：

    
    if (!document.getElementById) {
        window.location =
    "http://www.webstandards.org/upgrade/"
    }


我们曾经为标记（markup）的各种细节提供了示例。在 HTML4、或 XHTML1 Transitional 文档里，它是这样的：

    
    <script type="text/javascript" language="javascript">
    <!-- //
    if (!document.getElementById) {
        window.location =
    "http://www.webstandards.org/upgrade/"
    }
    // -->
    </script>


在 STRICT 文档里，你要么使用一个全局的 .js 文件，要么插入下面代码：

    
    <script type="text/javascript">
    <!-- //
    if (!document.getElementById) {
        window.location =
    "http://www.webstandards.org/upgrade/"
    }
    // -->


你还可轻松地把访问者引导到你网站上的升级页面：

    
    if (!document.getElementById) {
        window.location =
    "http://www.yourdomain.com/yourpage.html"
    }


非 WaSP 成员（在当时），[J. David Eisenberg](http://www.oreilly.com/pub/au/799)、[Tantek Çelik](http://tantek.com/)、[Jim Heid](http://www.jimheid.com/) 贡献了技术建议，也给了道义支持。WaSP 的系统管理员 [Steven Champeon](https://twitter.com/schampeo)，他也是[渐进式增强](http://alistapart.com/article/understandingprogressiveenhancement)的发明者，使[渐进式增强](http://www.labazhou.net/2014/12/making-case-mobile-first-designs/)运转起来------他本意不是要这么做的，为他祈祷。（Steve 相信，所有的 web 内容应该总是被所有的人和设备获取；因此，在原则上，他不喜欢这场升级运动，尽管该运动具有两个目的，要么促进真正符合标准的浏览器面世，要么让前端设计和开发人员、把 hack 的无礼世界改变为稳定专业的工艺品。看看我刚才说了什么？我脑子里仍然十分尊敬地在谈论着 Steve。）

在这种改变中，web 开发人员测试功能时，发现了基本的 DOM 意识、或意识的缺乏，这还是第一次，他们没有再像以前那样，像个瘾君子似的企图针对每个可能的浏览器特性和版本号进行测试。如果你认同的话，它就像是今天「符合标准」的祖父母一辈人。也可以这样打个比方，为内容设置断点的智能响应式设计的做法，而不是为每一个[可能已经出现的设备](https://twitter.com/zeldman/status/639078683639214080)设置合适的断点（包括所有那些还没有发明出来的设备）。

这让我们想起来，web 标准的全部意义，从过去到现在，都是向前兼容------无论过去的和现在的浏览器和设备，还是尚未发明的所有优秀设备，都只是为世人创造内容。欢迎你的加入。

向 [John Morrison](https://twitter.com/localcelebrity) 致敬。



* * *






	
  * 注1：用以描述无法满足一定标准。[http://www.urbandictionary.com/define.php?term=Doesn%27t+Cut+the+Mustard](http://www.urbandictionary.com/define.php?term=Doesn%27t+Cut+the+Mustard)

	
  * 注2：The Web Standards Project (WaSP) was a group of professional web developers dedicated to disseminating and encouraging the use of the web standards recommended by the World Wide Web Consortium, along with other groups and standards bodies. [https://en.wikipedia.org/wiki/Web_Standards_Project](https://en.wikipedia.org/wiki/Web_Standards_Project)

	
  * 注3：互联网泡沫（又称科网泡沫或dot-com泡沫）是指由1995年至2001年间与信息技术及互联网相关的投机泡沫事件。这一时期的标志是通常被称为“.com”的互联网公司不断成立。公司可以简单地通过在他们名字上添加“e-”前缀或是“.com”的后缀来使其股票价格增长，某作者称其为“前缀投资”。[https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%AF%E7%B6%B2%E6%B3%A1%E6%B2%AB](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%AF%E7%B6%B2%E6%B3%A1%E6%B2%AB)


