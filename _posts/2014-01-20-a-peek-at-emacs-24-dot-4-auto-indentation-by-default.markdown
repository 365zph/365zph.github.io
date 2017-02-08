---
author: viviworld
comments: true
date: 2014-01-20 09:17:40+00:00
layout: post
link: http://www.labazhou.net/2014/01/a-peek-at-emacs-24-dot-4-auto-indentation-by-default/
slug: a-peek-at-emacs-24-dot-4-auto-indentation-by-default
title: 一窥Emacs 24.4：默认自动缩进
wordpress_id: 207
categories:
- 软件
tags:
- emacs
- ruby
---

我过去写过一篇关于[electric-indent-mode](http://emacsredux.com/blog/2013/03/29/automatic-electric-indentation/)的文章，它被加进了Emacs 24.1。在Emacs 24.4，用户可见的最显著变化之一就是它开启了这一功能。这是Emacs朝着“现代化”迈开的一大步，也是最近几次默认设置变化较大的一次。让我们借助一些Ruby例子来看看这个模式是如何工作的（|代表光标位置）。没有electric-indent-mode:

    
    def something|


在敲回车之后，会得到：

    
    def something
    |


有electric-indent-mode:

    
    def something|


在敲回车之后，会得到：

    
    def something
      |


还不错吧？

electric-indent-mode有个问题，它和一些（多数是第三方）模式（yaml-mode, slim-mode等）兼容不好。我猜测这一状况过段时间会得到解决，但是现在你仅仅需要disable该模式：

    
    (add-hook 'yaml-mode-hook (lambda () (electric-indent-local-mode -1)))


注意electric-indent-local-mode被引入了Emacs 24.4。

如果你想对electric-indent模式做详细了解的话，可以看看electric-indent-functions 和 electric-indent-chars的文档。

原文地址：[http://emacsredux.com/blog/2014/01/19/a-peek-at-emacs-24-dot-4-auto-indentation-by-default/](http://emacsredux.com/blog/2014/01/19/a-peek-at-emacs-24-dot-4-auto-indentation-by-default/)
