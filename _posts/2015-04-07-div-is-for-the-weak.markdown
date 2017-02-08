---
author: viviworld
comments: true
date: 2015-04-07 06:23:41+00:00
layout: post
link: http://www.labazhou.net/2015/04/div-is-for-the-weak/
slug: div-is-for-the-weak
title: DIV 是给弱者准备的
wordpress_id: 1831
categories:
- 网络
tags:
- css
- HTML
---


	
  * 原文地址（original source）：[http://www.studiowolf.com/blog/div-is-for-the-weak/](http://www.studiowolf.com/blog/div-is-for-the-weak/)

	
  * 作者（author）：[https://twitter.com/TimSluis](https://twitter.com/TimSluis)





* * *





<blockquote>译者注：当我向作者 Tim Sluis [征询翻译许可](https://twitter.com/TimSluis/status/585183559897456640)时，他的答复里提到了“你注意到了这是个玩笑的事实，对吧？”。</blockquote>


我们非常高兴地宣布，我们，Studio Wolf 的狼群中队，将要在前端 [web 开发](http://www.labazhou.net/2014/08/the-hidden-danger-of-html-frameworks/)中设定一种新趋势。我们是第一家在代码里完全转向列表元素的公司，专门使用`<ul>`和`<li>`，不再使用`<div>`、`<h1>`、`<p>`等元素。

    
    <ul>
       <li>Hello world!</li>
    </ul>


为什么？原因很简单：



	
  * 老实讲，网页除了列表嵌套列表，就没有什么了；

	
  * 我们有 CSS 和 class。它们按你想要的方式为每个列表项设置样式。不需要额外的标签；

	
  * Google 钟情于列表；

	
  * 真的太简单了。


让我们向你展示一个不错的清晰例子：

    
    <!doctype html>
    <html lang="en">
    
        <head>
            <meta charset="utf-8">
            <meta name="viewport" content="width=device-width, initial-scale=1">
    
            <title>We love UL</title>
            <meta name="description" content="">
            <meta name="author" content="">
        </head>
    
        <body>
    
            <ul class="wrappers">
    
                <li>
                    <ul class="containers">
                        <li>
                            <ul class="grid">
                                <li class="navigation">
                                    <ul class="items">
                                        <li href="#">Home</li>
                                        <li href="#">Products</li>
                                        <li href="#">About us</li>
                                        <li href="#">Contact</li>
                                    </ul>
                                </li>
    
                                <li class="header">
                                    <ul class="slides">
                                        <li>We love lists.</li>
                                        <li>W3C is shitty.</li>
                                        <li>Div is for the weak.</li>
                                    </ul>
                                </li>
                            </ul>
                        </li>
                    </ul>
                </li>
    
                <li>
                    <ul class="containers">
                        <li>
                            <ul class="grid">
    
                                <li class="aside">
    
                                    <ul class="content">
                                        <li class="h2">This is my sidebar.</li>
                                        <li class="p">Aliquam et rutrum tortor, nec pellentesque massa. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Donec bibendum dui dui, in feugiat nibh posuere ut. Phasellus vel imperdiet sapien.</li>
                                    </ul>
    
                                </li>
    
                                <li class="article">
    
                                    <ul class="content">
                                        <li class="h2">This is my content.</li>
                                        <li class="p">Aliquam et rutrum tortor, nec pellentesque massa. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Donec bibendum dui dui, in feugiat nibh posuere ut. Phasellus vel imperdiet sapien.</li>
                                    </ul>
                                </li>
    
                            </ul>
                        </li>
                    </ul>
                </li>
    
            </ul>
    
        </body>
    
    </html>


web 大拿、web 忍者、专家们，以前都没有执行这种优秀的思想，我们对此感到震惊。尽管采用这种新的编码方式吧。我们非常肯定，世界上其他人将很快效仿。
