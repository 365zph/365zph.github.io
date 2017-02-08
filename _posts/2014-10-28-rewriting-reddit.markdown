---
author: viviworld
comments: true
date: 2014-10-28 09:54:27+00:00
layout: post
link: http://www.labazhou.net/2014/10/rewriting-reddit/
slug: rewriting-reddit
title: 重写Reddit
wordpress_id: 1164
categories:
- 编程
tags:
- api
- Django
- HTML
- lisp
- python
- reddit
- web.py
---

<blockquote>2012年注：本文首发于2005年。发布之后，Django上线了一个RemovingTheMagic项目，提出了我的一些质疑（尽管我本人发现它仍然不可用），[web.py](http://webpy.org/)促进了FriendFeed的[tornado.web](http://www.tornadoweb.org/)和Google的[gae.webapp](https://developers.google.com/appengine/docs/python/gettingstarted/usingwebapp)以及其它项目（尽管如此我仍然喜欢web.py），本文引起了Reddit流量的永久井喷，仍然没有真正地停止增长。</blockquote>


在[reddit.com](http://reddit.com/)过去的一周里，我们用Python代替Lisp重写了网站。这周我们做了很多工作（透露：我们使用了我开发的[web.py](http://webpy.org/)类库）。其他人熟悉Lisp（整个站点用它编写），他们喜欢Python（他们用它重写了整个站点），然而他们决定，在这个项目中喜欢Python多一些。Python版本的网站需要更少的代码，运行更快、代码更容易阅读和维护。

根据在[reddit博客](http://reddit.com/blog/2005/12/night-of-living-python.html)上的评论，比Lisp更好的东东的想法，表面上对一些人是不可思议的。Lisp爱好者们很快着手尽量找到变换语言背后的真正原因。

有人认为这里面一定有不同寻常的干预，由于“貌似没有切换到低等语言的其它原因。”又有人觉得其它事情必须在发生着：“这会是……一个谎言？扔掉竞争力？貌似Paul Graham没有在他的文章里暗示这个策略呀……”还有人附和道：“我认为这是恶作剧。”也有人提出，作者只是想更多地“走捷径、hack和伪装手法。”

当然，它们都是极端的情况。其它人猜测一定有来自外部的压力。“我猜，要么是类库，要么是雇佣新员工。”有人总结到：“一些投资商想要任何程序员都能维护的产品。我希望他给你支付了好多钱。”

Lisp新闻组comp.lang.lisp对于这次切换感到失望，他们为了表明自己是多么地正确，最近正[计划把reddit写成Lisp的一个竞争者](http://groups.google.com/group/comp.lang.lisp/browse_frm/thread/f560fdfb211aa8cb/c0159fbbc6496def)。

这些说法当中，稍微中肯的提到Lisp的价值在于能够创建[新的语言结构](http://reddit.com/blog/2005/12/night-of-living-python.html#113382802678872391)，这对于简单的web应用程序而言，是不必要的，因为结构已经被建好了。不过，这也不是真实的。web.py完全从零起步，用到了各种“新的语言结构”（linguistic constructs）------甚至更好------这些结构具有语法，让它们具有合理的可读性。当然，Python不是Perl 6，因此你不能增加任意语法，不过你经常能够找到把事情搞定的聪明方法。

另一方面，Python有它自己的问题。最大的问题在于它有很多web应用程序框架，但是都不太好。Python爱好者只是注意到了第一句，而明显忽视了第二句，因为当我告诉他们我正在用自己的类库时，通常的反应是“我认为Python不需要另一个web应用程序框架”。是的，Python需要更少的web应用程序框架，但是它也需要不是太糟糕的框架。

貌似最有前途的框架就是[Django](http://djangoproject.com/)了，我们最初的确想用它重写reddit。做为有经验的Python程序员，我尽量帮助其他人解脱出来。

从外面看Django貌似优秀：良好外观的网站、极具才能和天赋的开发者，表面过剩的、优秀功能。开发者和社区是非常有帮助的，也对补丁和建议作出响应。所有正确的目标都在他们的哲学文档和FAQ得以支持。然而不幸的是，它们好像完全没有达到自己的期望。

Django声称它是“松耦合”的，却要求你的代码符合Django的风格。Django坚持你的代码执行本身，或是通过命令行工具，或是借助正确的环境变量和Python路径做特定的服务器处理程序调用。当你开始项目时，Django默认为代码生成了嵌套四层的文件夹，而你能够移动一些文件，我在搞清楚移动哪一个以及如何移动上遇到了麻烦。

Django的哲学是“明确优于隐式”，但是它却有各种魔法。你在一个文件创建的数据库模型，神奇地出现在有着不同名字的Django模块内部的某个地方。当模型功能被调用时，新东东被添到了它的变量里，旧的数据被移除了。（我被告知，他们目前正在修复这两个问题。）

Django的另一个目标是“较少的代码”，至少对你而言。但是Django却充满了代码。在Django里有10个不同的文件夹、而每个文件夹内部又有一些文件夹。当你根据Django教程开始实际地建立网站时，你已经导入了django.core.meta, django.models.polls，django.conf.urls.defaults.*，django.utils.httpwrappers.HttpResponse和django.core.extensions.render_to_response。任何人应当记住它们，不是明确的，尤其是好像没有原理或如何命名的指导原则。上面的三个模块被开始的脚本自动插入了，但是你仍然需要为你想使用的每个函数记住这些名字。

不过，Django最重要的问题在于，它的开发者貌似未能设计出得体的API。他们肯定是有能力的Python程序员------他们的代码用到了各种奇怪的手法。他们肯定能写出可运行的代码------它们有各种有趣的功能。但是，他们好像不能把代码构造成其他人可用的方式。

他们的API是丑陋的，定期地丢失重要功能：数据库API通过计算下划线来构造查询，但是没有专门的语法来处理JOIN，模板系统需要4个大括号包围每个变量，却不能做任意种类的计算，表单API需要15行来处理表单，却不能自动生成模板。

我尽力修复这些问题了------Django社区相当支持------但是任务让我退缩了。我只是精神上做不到，更不要说 不得不为我自己的创业去实际开发自己的应用程序的、时间限制。

因此，Lisp和Django是不足的，我们带着[web.py](http://webpy.org/)离开了。我想说，web.py认识到了这些错误，在设计的时候就避免了它们，不过真相是，web.py在出现这些问题之前已经被编写了，并设法避免了它们。

我写web.py的方式是简单的：我想象着事情应该如何运行，然后我让它们成为现实。有时候让它运行需要很多代码。有时候它只需要一点儿代码。但是不管怎样，这些事实对于用户是不可见的------它们只需要完美的API。

那么应该如何运行呢？第一个原则是，代码应该清晰简单。如果你想输出文本，你就调用web.output。如果你想得到表单输入，你就调用web.input。没有特别难记的东东。

第二个原则，web.py应该适合你的代码，而不是其它方式。web.py里的每个函数都是完全独立的，你想用哪个就用哪个。你可以把文件随意放在任何地方，web.py乐于定位到它。如果你想把一块代码做为web应用程序运行，你可以调用web.run，你不要把代码放在不可思议的地方，让web.py运行。

第三个原则是，web.py默认应该做web所认为的正确的事情。这意味着正确地区分GET和POST。它代表了简单、同一性会跳转到标准链接。它代表了含有正确HTTP头的、可读的HTML。

我所担心的是，有太多你需要的原则。它们对我来说，好像非常简单和明显，甚至我乐意篡改它们，但是其它Python的web应用程序框架却没有和它比肩的。（如果你知道有，请告诉我，我乐于收回上面的话。我想不是这样的。）在此之前，貌似我被迫做了一件本不愿意做的、可怕的事情：向世界又提交了一个Python web应用程序框架。

原文地址：[http://www.aaronsw.com/weblog/rewritingreddit](http://www.aaronsw.com/weblog/rewritingreddit)
