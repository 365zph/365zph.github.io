---
author: viviworld
comments: true
date: 2014-08-19 04:01:21+00:00
layout: post
link: http://www.labazhou.net/2014/08/how-to-learn-vim/
slug: how-to-learn-vim
title: 如何学习Vim
wordpress_id: 919
categories:
- 软件
tags:
- github
- iTerm2
- powerline
- StackOverflow
- tmux
- Vim
- zsh
---

我已经学习Vim多年了。下面是我推荐开始学习Vim的一些建议。


### 如果你不想学，就不要去学Vim


我深爱Vim，无法想象一整天用其它编辑器去写代码的情景，但是我从来不推荐谁去选择它。为什么？你不得不想选择它。我不能强迫谁；他们会恨它的。我能做的、最好的就是告诉人们我为什么喜欢它，让他们明白，它实际上是一个非常不错的编辑器。

因此如果你还没有兴趣去学，就不要让任何人强迫你。你不得不真正喜欢学习Vim，否则你永远不可能学到精通的境界。


### 学到过得去的程度


第一步要学到刚刚能够勉强维持的水平。起初这就像被虐待。在你开始学得更快之前，你一定是缓慢的。因此你需要在工作之外花些时间，这样你的工作效率就不会受影响。

我开始使用Vim时，我知道打开一个文件，向上、下、左、右移动，知道如何切换进/出编辑模式，如何删除，如何退出Vim，就这些。很明显，你不得不坚持多学一些，否则它就不值得了，不过你不得不从某个地方开始。


### 尽可能多地坚持使用


如果你坚持使用它，某些命令就变成了肌肉记忆，这是好的，因为你可以只是在脑子里记住了如此多的命令。如果你尽可能多使用，更多的命令就变成了第二本能，这样你可以关注越来越多的命令。


### 拥抱Vim，尽可能长时间地使用它


当你每天投入工作的时候，你精力充沛，不要打开你平常的编辑器，而是调出Vim。想用多长时间就用多长时间。如果你想了，或真的想去用另一款编辑器，不要着急，这一天的剩余时间再去用。当你有进步了，你会发现自己想用Vim的时间正越来越长，最终你用Vim时的产出才更多。


### 不要关闭方向键，只是尽量不要使用


会有个学派对你说，你需要关闭Vim里的方向键，使用h、j、k、l键移动。实际上这是我用过的方法，不过只是我想这样做的。

要我说，你怎么舒服就怎么来。如果保留方向键让你舒服，那么无论如何，都要保留。不过，一定尽可能多地忍住不用方向键。

现在我相当精通了，我后来打开了方向键，我还开启了鼠标滚动和点击。这样做的理由是，我不想完全疏离同事，因为他们会用我的电脑看代码。


### 坚持做笔记


我认为学习过程中做笔记是相当重要的。我现在仍然就我需要记住的东西做笔记，我想随后研究，并完善我的Vim配置。做笔记的范围：



	
  * 关于你不知道的

	
  * 关于让你沮丧的

	
  * 关于你需要记住的

	
  * 你碰到的任何问题




### 尽量学会使用Vim文档


有一块我本人不擅长。我倾向于在线研究，在[StackOverflow](http://stackoverflow.com/questions/24345331/vim-real-tab-characters-start-at-column-8-i-cant-move-all-the-way-left)提问，但是Vim有不错的文档（只是你要习惯），它就内置在Vim里。你只需运行 :h 命令，就可以学到关于Vim的不错的资料。


### 享受欢乐


尽量不要沮丧。学习Vim应该是充满乐趣的，甚至是一个冒险。


### 让Vim更好


默认设置下的命令行和Vim与其它文本编辑器相比，看起来不太漂亮。我认为你的编辑器应该是美丽的，你应该乐于使用并以此为荣。尝试一些不同颜色的scheme，确保你有语法着色。我推荐[Solarized](http://ethanschoonover.com/solarized)颜色scheme。我也推荐使用[iTerm2](http://iterm2.com/)（有上面提到的鼠标滚动和点击）[zsh](http://www.zsh.org/)，[oh my zsh](https://github.com/robbyrussell/oh-my-zsh)，[tmux](http://tmux.sourceforge.net/)和[powerline](https://github.com/Lokaltog/powerline)。


### 慢慢地创建你的Vim配置


你可以完全拷贝其他人的Vim配置，但是很难知道每个细节做了什么，做自己的配置也是很难的。仅仅从基本的Vim开始，慢慢添加东西到你的vimrc和插件里。


### dotfiles的版本控制


在数年里，你会对配置做出大量修改，所有dotfiles和配置具有一个版本控制的历史是真正不错的。如果你托管在github，你可以与其他人分享，你从来不会丢失。这让安装一台新电脑也变得容易了。这里是[我的dotfiles](https://github.com/aharris88/dotfiles)。


### 找到一个使用Vim的朋友


我最好的、也可能是最难的建议，就是找到一个使用Vim的、或至少支持你使用Vim的朋友。

我参加奥格登【译者注：美国的一个城市】的[Startup Weekend](http://startupweekend.org/)，在我们组有个家伙，[Corey Woodcox](https://twitter.com/cwoodcox)一直在使用Vim。我第一次意识到这是可行的，我完全独自一个人这样。得知有人实际上在使用、且热爱使用Vim，是非常酷的。他也在Twitter上为我解答了一些问题。

当你的朋友不屑你的编辑器选择，而且你或许不能让他们信服，是非常让人沮丧的。另一方面，有一个使用Vim的朋友，在你学习的早期阶段可以极大地鼓励你。


### 永远坚持学习


学习Vim吧，祝你好运。这应该是一次充满乐趣的旅行！

原文地址：[http://www.adamwadeharris.com/how-to-learn-vim/](http://www.adamwadeharris.com/how-to-learn-vim/)
