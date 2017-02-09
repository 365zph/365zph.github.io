---
author: viviworld
comments: true
date: 2014-10-29 08:35:08+00:00
layout: post
link: http://www.labazhou.net/2014/10/living-the-future-of-technical-writing/
slug: living-the-future-of-technical-writing
title: 实践的、技术写作的未来
wordpress_id: 1166
categories:
- 杂项
- 职业
tags:
- Apress
- Asciidoc
- Atlas
- Git
- github
- Markdown
- O’Reilly
- 写作
---

## Pro Git（第二版）令人惊奇的冒险和最终工具链


大约六年前Apress要我为正在编写却延期了的一本书上提供帮助，书名是《Pro Git》。最终原作者决定不再继续编写了，我从头重新编写这本书，后来在2009年8月份出版。对于前三章，我在Word里写，把文档发给编辑，随后再得到划有红线的版本。

写了前三章之后，我打算放弃。因为我提出，我们要转向Markdown，用于写作和技术编辑阶段，然后仅仅为了拷贝编辑通过的内容再返回到Word。当书完工后，我再次把所有内容挪到Markdown，才能发布到我创建的网站上。我很幸运，原作者让Apress授权本作品的创作共用协议。

一年后，Apress还发布了Kindle版，尽管书一发布就有人根据开源内容制作了Kindle兼容版本。


### Pro Git，第二版


这本书做得还不错，印刷四年后，Apress找到我做另一个版本。在那段时间，我的公司GitHub已经从4名员工、数千个用户的网站，一跃成为了巨人公司，线上托管了数百万的代码仓库，员工超过200名。不仅仅是GitHub改变了很多，而且工具本身也有了显著的变化。我认为很可能到了翻新内容的时候了。

现在你可以[在线](http://git-scm.com/book)阅读第二版（还有第一版），或者下载PDF、ePUB或Mobi（Kindle）格式，便于在你喜爱的设备上阅读，我想，要分享的一个有趣的事情就是这个版本是如何从五年前的第一版产生而带来的不同。


### Pro Git第二版的写作


在过去的几年，实际上我开始翻新Gro Git好几次了。主要是因为我对工具链方面感兴趣。当时我启动了一个名叫[Git Scribe](https://github.com/schacon/git-scribe)的项目，意欲论证工具链的类型，我希望我可以用它编写Pro Git。Scribe工具提供了比较容易的方式安装工具链，它处理特定格式的Asciidoc的书，并以此生成好看的HTML、PDF、ePUB和Mobi电子书。虽然这个项目后来死掉了，我们最终用上了O'Reilly的Atlas平台，而Scribe项目让我把Asciidoc摆在了第一位。


### Asciidoc


我把大部分Pro Git转换成了Asciidoc。Markdown的问题在于它太简单了，它还没有定义诸如表格格式、交叉引用、索引、编号、源代码示例等等。所有这些，Asciidoc都以一种容易编写的格式做到了。

因此我把所有内容从Markdown迁移到了Asciidoc，还留意到了一些出版商也是这样做的。O'Reilly开始允许用Asciidoc编写书了，因为它能够容易地生成Docbook，我相信《Pragmatic Programmers》在那之前就用到了一种简单的标记语言。

所有这些最为重要的是Asciidoctor的崛起。在我改版我的Git网站（git-scm.com)时，我想为Git使用Asciidoc的man-page源，以制作漂亮的线上版本，我想用Ruby实现。我的朋友和GitHub同事Nick Hengeveld为Asciidoc编写了优秀的解析与格式程序，可以帮我实现。最终其他一些GitHub爱好者（Ryan Waldron和Jeremy McAnally）参与进来，把Asciidoc.rb变成了Asciidoctor，最终被奇才Dan Allen接手，他把这个项目带到了一个全新的高度。

由于Asciidoctor很普遍了，我可以用我的Asciidoc格式的书做真正有价值的事情了，只是没有以前简单。


#### GitHub


写作工作流的最大变化之一就是现在的GitHub比以前好很多了。如今我们可以Pull Request来浏览和评论、章节规划的发行里程碑、用于简单审核和抽查的普通diff、用于编写和Asciidoc预览的Atom文本编辑器。

[![review](http://www.labazhou.net/wp-content/uploads/2014/10/review.png)](http://www.labazhou.net/wp-content/uploads/2014/10/review.png)

我们使用的工作流，很可能是任何一个曾经写过技术方面的书、尤其有过合著经历的人，都非常嫉妒的。

我们想怎么写就怎么写，把问题要点附加到每章的里程碑上，然后每个人决定我们要做什么，开始写什么。我们能够为我们在做的工作单元（通常是一个章节）建立一个分支，开始写作并推送到GitHub分支上。我们在Slack上交流，我们当中有人一提交变化，就能得到即时更新。我们几乎瞬时打开Pull Request，通常在合并之前有一个我们想要完成的工作清单，因此你可以说出每个分支的状态（[例子](https://github.com/progit/progit2/pull/89)）。

当分支长时间运行后，我们将把主分支合并进去，以保持更新，确保冲突从来都不是大的问题，即使有大规模的结构变化，比如把章节拆分到多个文件里。

代码审查通过Pull Request来完成------我们可以就任意一行介绍性的文字留下评论，并能在那儿或在聊天里沟通。

我能够安装[Asciidoc Atom](https://github.com/asciidoctor/atom-asciidoc-preview)代码审查插件，当我在写作的时候，就可以获取我正在编写的文本的在线生成视图，包括侧边栏提示，包括我添加、修改或删除了什么、我在哪个分支、合并冲突帮助工具、禅模式（zen mode）等。让人惊叹的写作环境。

[![asciidoc atom插件](http://www.labazhou.net/wp-content/uploads/2014/10/asciidoc-atom.png)](http://www.labazhou.net/wp-content/uploads/2014/10/asciidoc-atom.png)

不仅如此，而且我们做了大部分协作，分隔开的9个时区和编辑能够在任何时间看里程碑页，以了解我们整本书的进度。

如果你编写过技术方面的书，而没有在现代GitHub上用Asciidoc写，那么你花费的时间将是你需要的10倍。


#### Atlas


不但这本书的编写和协作比第一版容易些，而且预览的确更容易了。

[caption id="attachment_1170" align="alignnone" width="600"][![O'Reilly的Atlas开发系统](http://www.labazhou.net/wp-content/uploads/2014/10/pro-git-atlas.png)](http://www.labazhou.net/wp-content/uploads/2014/10/pro-git-atlas.png) O'Reilly的Atlas开发系统，可在数分钟内制作一本精美的电子书。[/caption]

多亏了数年前在O'Reilly Media，我与Tim O'Reilly、Laura Baldwin以及其他人关于这种工具链如何变得更好展开过讨论，我受邀体验了他们正在开发的、让其更加容易的平台。我们都认同把Asciidoc格式的作品变成’git push‘、变成PDF是如何伟大。实际上他们最终开发好了，感谢他们让我参与了试用。

你可以看到那几个月我在他们[论坛的活跃程度](http://forum.atlas.oreilly.com/users/schacon/activity)，每次我都提到了他们在数天、甚至数小时内修复的地方。除此之外，这次开发还生成了如此美丽的输出，对于章节预览，当我在Asciidoc源里加了注释和修改时，我不用再建立PDF、下载下来，预览。

幸运的是，他们还有用于服务的API，你能够独立地开发不同的分支。这意味着我能够写一个在Pro Git仓库监听post-receive钩子的服务，拽下修改，推送到Atlas，并自动启动一个构建。它会轮询什么时候所有构建完成、把它们迁移到我自己的AWS S3 bucket上、更新为新的progit.org网站以及git-scm.com网站上的内容和链接。

还有，我能够为Pro Git被翻译成的每种语言做这些工作。这意味着在不久的将来，如果你访问[Pro Git](https://progit.org/)网站或[git-scm.com](http://git-scm.com/)网站，你就能下载最后勘误合并之后数分钟内的最新版本的、专业级的电子书，包括任何语言。点击’合并‘按钮之后，我或者语言维护者不用做任何工作。

现在在这个星球上，我基本上有最简单的和最复杂的多语言电子书产品和发布安装。


#### 开源


第一版和第二版之间的另一个有趣的区别在于，由于我不想把Markdown转换成Word、再转换成Markdown，我们都认为，我能总体上编写这本书，然后“丢过墙（throw it over the wall）”给Apress，而Apress将做Word转换、拷贝编辑、然后把修改发给我。这意味着与之前相比，Ben和我都能更加容易地开源这本书。

本书目前有[在线完整版](http://git-scm.com/book/)，包括本书的所有格式，但是距离付印可能还有几个月的时间。在这段时间里，我们确保得到了一堆微小的拷贝编辑和技术校正（我们在最初的24小时内已经得到了一些），在Apress印刷之前将能够合并进去。也就是说，在实际印刷本书之前，我们能够找到并修复勘误，这相当让人感叹。

实际上我们讨论过，以开放的形式编写整本书 或者 在重新开放之前一直等到差不多完工。最后，我们选择了后者，尽管我仍然不敢确定前者还不是最好的选择。我们觉得，在这个过程中，处理来自整个社区的意见可能有太多的争论，我们宁可更基础地拥有内容，但是走其它路线或许是有趣的。下次可能这样吧。


#### 翻译


这次显著不同的最后一个地方是处理作品的翻译。在开源第一版时，我完全不记得考虑过翻译。我不记得拥有我的第一个翻译作品，但是在我发布之后，速度还算迅速，因为发布之后不久，我重建了目录，把所有文件都放在了一个’en‘的目录里。

[![Pro Git在线电子书](http://www.labazhou.net/wp-content/uploads/2014/10/pro-git-book.png)](http://www.labazhou.net/wp-content/uploads/2014/10/pro-git-book.png)

这本书发布五年里，它被全部翻译成了至少10种语言（Deutsch, 简体中文, 正體中文, Français, 日本語, Nederlands, Русский, 한국어, Português and Čeština），部分章节被翻译成了另外的20种语言。我决定把它们存放在主仓库的子目录里，为它们处理Pull Request，这意味着有写权限的人不得不合并它们。这也意味着基本上，我不得不合并所有文件，即使我几乎看不懂任何语言。最终，过了几年，我对于坚持Pull Request感到不太爽，令人吃惊的[Jean-Noël Avila](https://github.com/jnavila)接手了，从那以后管理着这些翻译工作。

有了这一次，我们能够学到以前遇到的问题，尽量让它对每个人简单。这次我们正在把每份翻译做为progit组织下的一个独立的仓库，为每个仓库添加语言具体的维护人员。这意味着，你可以在ZH版本里用中国的官话提交一个问题，我们也不会完全被搞晕了。如果维护人员不再响应了，而其他人有兴趣，我们可以把他们添加为新的维护人员。

感谢Atlas，每份翻译都将有自己的自动构建过程，而不是一直到现在都存在的、让每个人在本地运行自己的构建。


#### 总结


我相信这个过程对于技术出版的中期未来至少是短暂的。在GitHub上写书，用Asciidoc这种更简单的格式，更容易地与你的编辑、合著者协作，开源内容，拥抱强大的翻译社区，以及Asciidoc或Atlas之类的自发布工具。

总体上我也相信，所有这些对于出版行业有着非常严肃和有趣的涵义，我将在未来的文章里深入地谈谈。

原文地址：[https://medium.com/@chacon/living-the-future-of-technical-writing-2f368bd0a272](https://medium.com/@chacon/living-the-future-of-technical-writing-2f368bd0a272)
