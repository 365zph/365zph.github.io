---
author: viviworld
comments: true
date: 2014-05-15 23:56:06+00:00
layout: post
link: http://www.labazhou.net/2014/05/improve-your-terminal/
slug: improve-your-terminal
title: 完善你的终端
wordpress_id: 676
categories:
- 软件
tags:
- github
- sublime
- terminal
- Vim
- vimtutor
- 终端
---

我相信人们小心使用终端的主要促成因素之一就是其默认的文本和颜色。好消息是，这非常容易搞定。

经历下面的一些变化，你最终会看到如下的、一个有爱的终端：

[![终端主题 oh-my-zsh ](http://www.labazhou.net/wp-content/uploads/2014/05/lovely-terminal-1024x776.png)](http://www.labazhou.net/wp-content/uploads/2014/05/lovely-terminal.png)


### Oh my Zshell！


[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)是经常使用终端的用户的、必备工具。它简化了样式主题的使用难度，不过提供了更加多样的功能。

如果你相信该工具的作者，那么你可以直接通过运行`curl -L http://install.ohmyz.sh | sh `来安装。默认配置将安装在 `~/.zshrc`。

如果你想手动安装，从[github repo](https://github.com/robbyrussell/oh-my-zsh)签出。


### 挑选主题


我个人使用ys主题，它显示了你当前目录，git分支和状态、在你敲入每个命令之前的、当前输入。这让你一眼看到目前的状况，当你发起一个长时间运行的命令时，允许你看它到底花了多长时间。

![oh-my-zsh 的ys主题](http://www.labazhou.net/wp-content/uploads/2014/05/ys-line-header-1024x63.png)

为了安装你选择的主题，改变你的 ~/.zshrc去包含ZSH_THEME=ys。


### 字体和颜色


除了你的主题，你还应当设置你的默认字体、颜色和终端背景颜色。你可以非常容易地搞定，在终端偏好设置里，Terminal > Preferences...，去修改 文本(Text) 和 窗口(Window) 下的选项。

挑选字体是相当重要的，它必须是等宽字体，一些较好的选择是Monaco, Source Code Pro, Inconsolata。我个人使用Inconsolata。

其次，你真正应当考虑,把字体大小设置为又大又好看的样子，我用18px。你会长时间盯着终端，不愿让眼睛离开。

背景透明度看起来或许酷酷的，它明确阻碍了你集中工作的能力，它是毫无价值的，因此请设置成100%不透明。

最后，我个人喜欢在行之间增加额外的空间，我发现这有助于阅读，因此我设置行间距为1.5，字符间距为1.05。不过这取决于你的个人喜好和你选择的字体。

对于开发者来说，终端是做开发的最佳场所

有如此多的开发工作需要处处运行一个命令行工具，以致于你也想一直保持在终端里。不要使用一个GUI程序来管理你的git repo，它们比你自己运行git命令要慢。花点儿时间学习，一旦你掌握了，你节约的时间将赢回付出的学习时间。

所以我从最后一个非终端的开发工具，文本编辑器（我用Sublime Text 2）解放出来。我一直在学vim，我写这篇文章就是在vim上写的。它很棒。如果你有兴趣学习vim，运行 vimtutor，通读它的每日课程，很快就能驾驭这个强大的工具。

当我能够得心应手地使用vim后，我会写一篇个性化vim的教程，尽管我还要花数周时间才能达到那个状态。

关于你如何配置终端，有任何偏好设置或想法吗？请在下面的评论分享它们。

原文地址：http://www.gelatindesign.co.uk/blog/post/improve-your-terminal
