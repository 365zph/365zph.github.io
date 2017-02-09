---
author: viviworld
comments: true
date: 2014-04-04 14:23:53+00:00
layout: post
link: http://www.labazhou.net/2014/04/better-way-track-javascript-errors/
slug: better-way-track-javascript-errors
title: 追踪JavaScript错误的较好方法
wordpress_id: 513
categories:
- 软件
tags:
- chrome
- ios
- javascript
- Telemetry
---

JavaScript是令人惊奇的；你正在建立数年前没人考虑过的（[或许除了Jeff](http://blog.codinghorror.com/the-principle-of-least-power/)）、令人惊奇的、创新的web应用程序。但是随着应用程序的规模变大，它们越来越复杂、难以调试，也难以理解。加上不太好的JavaScrtip错误管理，和随意的浏览器实现，我们需要去面对：


<blockquote>TypeError: e is undefined. scripts.js. line 1.</blockquote>


我们开始修复这个问题------无缝追踪客户端错误，用足够多的信息来真正地修复它们！为了完成这一目标，我们没有把自己束缚在JavaScript错误对象的限制里。我们建立了自己的事件追踪系统来捕捉与你的应用程序、网络处理和用户在网页上正在做什么有关的、感兴趣的上下文。结合DOM和浏览器的环境，给你一个更为完整的错误重放。我们称之为Error Telemetry，它对于你的应用程序而言，有点儿像一个黑盒：

[![Telemetry-Timeline](http://www.labazhou.net/wp-content/uploads/2014/04/Telemetry-Timeline.png)](http://www.labazhou.net/wp-content/uploads/2014/04/Telemetry-Timeline.png)

我们早期客户已经运行了数月，在建设{Trac:js}本身的时候------我们对它运行效果是非常激动的。它帮助我们解决了iOS7下Chrome的肮脏的特定bug，在我们的API显示了未期望的行为。我们非常兴奋地邀请你免费试用。

web充满了错误的JavaScript。让我们对此做个了断吧。让我们找到、并修复我们的bug。让我们把web变成一个更好的地方。

[让我们开始吧](https://my.trackjs.com/signup)。

原文地址：[http://trackjs.com/blog/better-way-track-javascript-errors/](http://trackjs.com/blog/better-way-track-javascript-errors/)
