---
author: viviworld
comments: true
date: 2015-10-08 06:19:31+00:00
excerpt: 'mailto: 做为一种 URL，尽管没有过去那么流行了，有时候仍然是最好的方式------差不多也是最容易的------能够让用户通过 web
  应用程序发送 email。'
layout: post
link: http://www.labazhou.net/2015/10/js-mailto-urls/
slug: js-mailto-urls
title: '用 JavaScript 实现 mailto:'
wordpress_id: 2605
categories:
- 编程
tags:
- email
- gmail
- javascript
- outlook
- URL
---


	
  * 原文地址（original source）：[http://xion.io/post/code/js-mailto-urls.html](http://xion.io/post/code/js-mailto-urls.html)

	
  * 作者（author）：[https://twitter.com/Xion__](https://twitter.com/Xion__)





* * *



`mailto:` 做为一种 URL，尽管没有过去那么流行了，有时候仍然是最好的方式------差不多也是最容易的------能够让用户通过 web 应用程序[发送 email](http://www.labazhou.net/2015/01/email-the-good-parts/)。它们通常和 `<a>` 标签一起创建，像是普通而有规律的链接：

    
    <a href="mailto:john.doe@example.com">Send email</a>


根据操作系统和浏览器的设置，点击这种链接会调用不同的邮件客户端。以前，如果某个用户从没用过本地的 email 应用程序（例如：Outlook），这会带来很多困扰，但如今浏览器做得越来越好，可以给出一些选择。通常包括流行的邮件提供商所支持的各种 web 应用程序。这样，用户就能选择，比如说 Gmail，今后所有的 `mailto:` 链接将把用户带往「写邮件」的界面。

鉴于其发展，那些 URL 可能就不再像以前那么古怪了 :-) 不管怎样，我认为有一点是值得做的，为了让它们妥善地应付手头的任务，我们可以对一些 `mailto:` 稍作手脚。


### 用 JavaScript 触发


在上面的例子中，我直接把 `mailto:` 做为 URL 放在了某些 HMTL 标记里。然而，这种 URL 和许多其它 URL 在很大程度上有着同样的表现，支持很多 http:// 之类的 URL 的同样功能：

    
    function sendEmail(address) {
        window.location.href = 'mailto:' + address;
    }


可以看到，调用 `sendEmail` 函数，等同于点击 `mailto:` 的链接。然而，多加这么一步，或许足以挡住那些收集 email 地址的网络爬虫。抵挡效果主要取决于我们在实际调用时所混淆该参数 address 的程度。

更重要的是，这种函数只是更加复杂逻辑里的一部分。唯一的限制在于，要约束 `window.open` 在哪里、在什么时候打开另一个浏览器窗口。也就是说，当用户触发了一个 UI 的动作时（按钮点击就是一个好例子），它必须以直接响应的方式调用。


### 自定义


对于最简单的形式，`mailto:` 这种 URL 并不太有趣，因为它们的唯一参数就是单一接收者的 email 地址。幸运的是，参数还有其它功能：可以自定义 email 的其它参数，比如标题（`subject`）、甚至还有正文（`body`）。

所有这些参数都用一种方式完成，和更有代表性的 http:// 这种 URL 的请求字符串参数一样，这多少让人感到吃惊。在接收者的 email 地址后面，我们可以跟上一个问号，然后加上一些由 & 分隔的键值对：

    
    <a href="mailto:john.doe@example.com?subject=Hi&amp;body=Hello%20John!">
      Say hello to John!
    </a>


更具编程的实现也是可以的。但是，我们需要记住，为了把参数安全地放入 URL 内部，需要正确地转义输入值。`encodeURIComponent` 函数就能满足：

    
    function getMailtoUrl(to, subject, body) {
        var args = [];
        if (typeof subject !== 'undefined') {
            args.push('subject=' + encodeURIComponent(subject));
        }
        if (typeof body !== 'undefined') {
            args.push('body=' + encodeURIComponent(body))
        }
    
        var url = 'mailto:' + encodeURIComponent(to);
        if (args.length > 0) {
            url += '?' + args.join('&');
        }
        return url;
    }


理论上，任意数量的 email `headers` 都能用这种方式指定。然而，支持程度因浏览器不同而不同，特别要提到的是，某些 `headers`（比如 `bcc:`）最终要考虑一定的安全、或隐私情况。就我个人看，除了 `subject=` 和 `body=`，我不推荐你使用其他参数，包括可能附加的 `cc=`，也就是 `cc:header`。
