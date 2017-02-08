---
author: viviworld
comments: true
date: 2014-04-29 13:46:35+00:00
layout: post
link: http://www.labazhou.net/2014/04/we-are-all-wrong-about-software-design/
slug: we-are-all-wrong-about-software-design
title: 关于软件设计，我们都错了
wordpress_id: 613
categories:
- 编程
tags:
- CoffeeScript
- emacs
- linux
- Mac
- MySql
- ORM
- Postgres
- ruby
- TDD
- Vim
---

我们都错了。当开始讨论观点时，这就是事情本身的样子。每个人有他或她自己的信念，它由该领域的多年经验、令人沮丧的代码、书、成功等等形成。所有这些背景是如何归结为一个统一理论的？它们只是还不可以。

你一直被告诉在工作中找到正确的工具。但什么是正确的工具呢？你决定的，根据你的实践知识。

我爱Ruby因为我觉得它自然，但是其他开发者讨厌这种语言。我喜欢干净的代码，其他人不关心。我赞成RSpec和Capybara，其他人喜欢Test::Unit。CoffeeScript 和 plain JavaScript， ERb 和 HAML，Postgres 和 MySQL. Vim 或 Emacs? Mac 或 Linux? TDD 或 不用TDD, 任何一个呢?

有了这些分割，我们不能把人们从教条中解放出来，但仅仅产生了一个相反观点的粉丝。

相对论也可以被应用到软件设计。我需要多少级的[间接寻址](http://en.wikipedia.org/wiki/Indirection)才能完成一定的工作？好吧，看情况。它取决于各种不错的理由，但是主要在于你的判断。对你来说是优秀的，然而对于其他人却是让人失望的。

我们可以讨论折衷方案，但是请不要把你的成功产品当做你在代码方面是正确的资格。

我在[Litmus](https://litmus.com/)工作，一家盈利丰厚的公司。如果我把下面的代码放在一个模板里，你会因为我的员工就发现它是合理的吗?

    
    <%
      require 'mysql2'
    
      client = Mysql2::Client.new({
        host: 'host',
        username: 'username',
        database: 'database'})
    
      rows = client.query(%{SELECT * FROM previews
        ORDER BY created_at DESC
        LIMIT 5})
    %>
    
    <ul>
    <% rows.each do |row| %>
      <li><%= row.fetch(:title) %></li>
    <% end %>
    </ul>


嗨，是的！谁需要那些像控制器和ORM的高级抽象，谁完全需要框架！那种结构是为[太空架构师](http://www.joelonsoftware.com/articles/fog0000000018.html)（architecture astronauts）准备的。离开我的草坪！看看我，我是个实用主义者。我通过 破坏了我工作的亿万富翁的软件 证明了这一点。

这不是一个论据，只是废话。

原文地址：[http://lucaguidi.com/2014/04/28/we-are-all-wrong-about-software-design.html](http://lucaguidi.com/2014/04/28/we-are-all-wrong-about-software-design.html)
