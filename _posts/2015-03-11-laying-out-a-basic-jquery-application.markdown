---
author: viviworld
comments: true
date: 2015-03-11 01:09:29+00:00
layout: post
link: http://www.labazhou.net/2015/03/laying-out-a-basic-jquery-application/
slug: laying-out-a-basic-jquery-application
title: 设计一个基本的 jQuery 应用程序
wordpress_id: 1695
categories:
- 编程
tags:
- javascript
- jquery
---


	
  * 原文地址（original source）：[http://programmar.io/article/1424961126](http://programmar.io/article/1424961126)

	
  * 作者（author）：[https://twitter.com/_jsmth](https://twitter.com/_jsmth)


我理解，jQuery 现在是、也已经是一个增长的 JavaScript 框架了。因此我想搞清楚什么才是设计 jQuery 应用程序的最好方法。现在我知道，你们所有程序员热爱整洁精悍的代码，还有谁不是这样想的吗？因此这就是我尽量在我写的东西里所实现的（代码层面）。


### 开始



    
    var programmarApplication = function() {
    
    };


和你想写的任何函数一样，最好这样开始：

    
    var applicationName


然后将其赋值给一个函数。我喜欢采用驼峰式命名变量名字，这意味着用 `aplicationName`，而不是 `application-name` 或其它不同的格式，但是只要你遵从一致性，可以按照自己的喜好来。


### 把信息解析成函数


为什么要这样做？继续在应用程序里使用 jQuery 也是可以的，但是 jQuery 著名的 `$('.element')` 选择器应该被赋给来自函数的 jQuery 的值。这是因为如果你这样做了，稍后想把 jQuery 改成其它值，你就可以保持相同的 `$('.element')` 选择器。

我们这样做：

    
    var programmarApplication = (function($) {
    
    })(jQuery);


如你所见，我们手动把 jQuery 的值赋给了‘`$`‘字符。因此如果你想修改成 `£('element')`，也是可以的！


### 开始你的 jQuery 应用程序


如果你扔出刚才的代码，你或许意识到它没有做什么，这可能是因为你没有告诉应用程序做什么。因此我们想要做的第一件事就是返回我们所能调用的一组方法。我想完成的第一个方法就是 `start` 方法。

    
    var programmarApplication = (function($) {
    
      return {
        'start': ignition,
      };
    
    })(jQuery);


现在我们有了 `start` 方法，但是它实际上做了什么呢？如果你运行：


<blockquote>programmarApplication.start();</blockquote>


它运行或者尝试去运行 `ignition` 函数的时候做了什么，我说尝试是因为我们还没有创建它，因此继续搞定！

    
    var programmarApplication = (function($) {
    
        var ignition = function() {
            console.log("This is the ignition function");
        };
    
        return {
            'start': ignition,
        };
    
    })(jQuery);


或许你能猜到我调用 `ignition` 函数的理由，当你想开车时时，要做的第一件事就是把发动机打着。因此，当你运行一个应用程序时，这就是第一件事。

这个应用程序用来处理在程序开始运行之后的所有函数，不过它还用来设计页面上某些元素的事件 handler，我打算为两者举些例子。


### 应用程序启动时，运行一个函数


从这里开始的理由很简单，很容易让你搞清楚。因此我们需要做的、或应该做的，就是首先创建一个新的函数，它是我们想在应用程序的 `start` 里运行的。现在请多加留意，我将举个真实的例子。假如你想在网站拥有自定义消息，函数运行 `start` 时，你想创建这个消息的 HTML。

    
    var programmarApplication = (function($) {
    
        var html = '<div class="message"></div>';
    
        var buildHTML = function() {
            var $body = $('body');
            $body.prepend(html);
        };
    
        var ignition = function() {
            buildHTML();
        };
    
        return {
            'start': ignition,
        };
    
    })(jQuery);


好的，咱们一步一步来解释，我们已经解释了如何实现 `ignition` 函数，因此到了这里之后，会发生什么呢？嗯，我们调用了名叫 `buildHTML` 的函数，你可以在 `ignition` 函数的上面看到它的定义。这个创建 HTML 的函数只是抛出了一些 HTML，这样我们可以稍后在网站上访问到，我们将其预置到 `body` 内部元素的前面。

我们想做的下一个事情就是点击一个按钮，获取到输入框的值，并把它放在我们刚刚预置在 `document` 顶部的消息容器里。


### 访问事件 handler


事件 handler 就是 `click`、`mouseover`、`mouseout`、`focus`、`blur` 等之类的东西。有一些特点，访问这些 handler 形如：

    
    var programmarApplication = (function($) {
    
        var inputSelector = '.input';
        var buttonSelector = '.btn';
        var messageClass = 'message';
        var messageSelector = '.' + messageClass;
        var html = '<div class="' + messageClass + '"></div>';
    
        var buildHTML = function() {
            var $body = $('body');
            $body.prepend(html);
        };
    
        var populateMessage = function() {
            var $input = $(inputSelector);
            var inputValue = $input.val();
            var $messageCont = $(messageSelector);
    
            $messageCont.html(inputValue);
            $messageCont.show();
        };
    
        var ignition = function() {
            var $document = $(document);
    
            buildHTML();
    
            $document.on('click', buttonSelector, populateMessage);
        };
    
        return {
            'start': ignition,
        };
    
    })(jQuery);


好了，基本的应用程序已经写好。你能看到我使得变量更加可伸缩，我是通过将其分解到不同的层来解决的，然后我就可以使用每一层做为可复用的选择器。这更加易于阅读，而且如果我想修改我创建的消息的 `class` 的名称，也是可以的。

    
    var messageClass = 'anotherClassName';


就是这么简单。


### 最后一件事


如果你把这段代码放到你的网站，你将注意到它仍然无法运行，这是因为你需要启动应用程序，我喜欢使用的方式是 jQuery 的载入函数：

    
    (document).ready(function() {
    programmarApplication.start();
    });


全部搞定！

    
    var programmarApplication = (function($) {
    
        var inputSelector = '.input';
        var buttonSelector = '.btn';
        var messageClass = 'message';
        var messageSelector = '.' + messageClass;
        var html = '<div class="' + messageClass + '"></div>';
    
        var buildHTML = function() {
            var $body = $('body');
            $body.prepend(html);
        };
    
        var populateMessage = function() {
            var $input = $(inputSelector);
            var inputValue = $input.val();
            var $messageCont = $(messageSelector);
    
            $messageCont.html(inputValue);
            $messageCont.show();
        };
    
        var ignition = function() {
            var $document = $(document);
    
            buildHTML();
    
            $document.on('click', buttonSelector, populateMessage);
        };
    
        return {
            'start': ignition,
        };
    
    })(jQuery);
    
    $(document).ready(function() {
        programmarApplication.start();
    });


我希望本文有助于你稍微理解 jQuery 应用程序、以及如何把你的 jQuery 脚本写成更加可伸缩和可扩展的程序。

谢谢。
