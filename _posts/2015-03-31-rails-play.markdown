---
author: viviworld
comments: true
date: 2015-03-31 23:57:16+00:00
layout: post
link: http://www.labazhou.net/2015/04/rails-play/
slug: rails-play
title: Rails Play
wordpress_id: 1789
categories:
- 编程
- 设计
tags:
- CRUD
- github
- Rails Play
- RailsBricks
- ruby
- Ruby on Rails
- rubygem
---


	
  * 原文地址（original source）：[http://nicoschuele.github.io/railsplay/](http://nicoschuele.github.io/railsplay/)

	
  * 作者（author）：[https://twitter.com/NicoSchuele](https://twitter.com/NicoSchuele)




## 快速轻松打造体验 Rails 的场所


GitHub 地址：[https://github.com/nicoschuele/railsplay](https://github.com/nicoschuele/railsplay)

你曾想尝试一个新的 gem 或体验新的 Rails 特性？Rails Play 应运而生了。它创建一个 Ruby on Rails 场所，包含一些模型、种子数据（seed data）、控制器和基本的 CRUD 视图。需要你开始做的所有工作都浓缩到了一条简单的命令：`rplay -n`。


### 体验的重要性


有一件事，我尽量给[我指导的](http://www.nicoschuele.com/training)人反复强调：在隔离的环境体验功能以达到学习的目标。这种方法也被 [Justin Weiss](https://twitter.com/justinweiss) 在其 [Rails 实践的书](https://www.justinweiss.com/practicing-rails/)中推荐过。本质上，使得完美准则应用到 Rails 编程，这是一种惯例。

在学习 Rails 时，把功能隔离到狭小区域，在大型项目之外尝试它们。这意味着开发、开发和更多的开发测试应用。一遍又一遍地从 `rails new` 开始，使用脚手架来生成模型、控制器和视图、准备数据库和填充数据将变得单调乏味，分散你学习的精力。这就是我为什么要做 Rails Play。


### Rails Play 能为你做什么？


Rails Play 简单地创建一个带有少量模型、关联、控制器和 [CRUD](http://en.wikipedia.org/wiki/Create,_read,_update_and_delete) 视图，非常类似 `rails generate scaffold` 所做的事情。在此基础上，它运行 `bundle install`，迁移数据库并用初始数据填充。好了，功能不多，但是它消除了一种阻力------为了体验新的 gem 或想尝试某个 Rails 特性，而去创建又一个测试应用。

Rails Play 不是一个应用开发工具。你不应该把它用做启动新项目。如果你想寻找类似工具，请参考 [RailsBricks](http://railsbricks.net/)，它是功能丰富的 Rails 应用开发工具。


### 安装 Rails Play，开始体验


为了安装 Rails Play，你只需要把 [Ruby](http://www.labazhou.net/2013/12/is-ruby-dying/) 安装到你的机器上。从命令行运行 `gem install railsplay`，就可以了。


#### 用 Rails Play 创建新的 Rails 应用


创建应用：

    
    rplay -n


运行你的 Rails 服务器：

    
    cd railsplay
    rails server


将浏览器指向 [http://localhost:3000](http://localhost:3000)。


#### 给你的应用命名


只需在 -n 选项之后指定应用的名字：

    
    rplay -n MyAppName


注意：用到了Rails 应用命名约定。


#### 跳过 bundle 安装和数据库配置


你还可以选择不让 `bundle install`、`rake db:migrate` 和 `rake db:seed` 在应用创建之后自动运行。如果你想改变 Rails 版本或向 Gemfile 增加其它 gem，这是非常有用的。

    
    rplay -n --skip-bundle


或

    
    rplay -n MyAppName --skip-bundle




### 想贡献代码或提建议吗？


如果你喜欢这个工具并且有想法、评论或疑问，只需在 GitHub 上[打开一个新 issue](https://github.com/nicoschuele/railsplay/issues) 或 [直接给我留句话](http://nicoschuele.com/contact)。

希望你们喜欢！
