---
author: viviworld
comments: true
date: 2014-06-12 03:17:22+00:00
layout: post
link: http://www.labazhou.net/2014/06/how-github-hide-email-from-spam-bots-in-profile-page/
slug: how-github-hide-email-from-spam-bots-in-profile-page
title: GitHub的个人信息页如何屏蔽垃圾邮件收集器
wordpress_id: 760
categories:
- 编程
tags:
- email
- github
- javascript
---

由于我是一名开发者，我经常使用GitHub。我爱它，胜过任何其它网站。我习惯于看我的GitHub个人信息页，因为当我看到热图上有很多绿点时，我感到非常快乐。由于我的网络有时候慢，我一直可以看到`{email}`，而不是我的邮箱地址。我想这是由于客户端在渲染。但其它的属性就不是这样，比如`name`、`location`和`website`。只有`email`属性是在客户端渲染出来的。

为什么？我Google一下，发现是为了避免垃圾邮件收集器采集邮箱地址。基本上，垃圾邮件收集器爬网站，检查邮箱地址，然后给它们发送广告和其它讨厌的邮件。你可能在这个网站看到过类似 `kumar [at] gmail [dot] com` 的邮箱地址。这种方法也是过去用来阻止垃圾邮件收集器的。

让我们看看GitHub可能是如何实现这种方法的。下面从GitHub个人信息页返回的html代码（比如：[https://github.com/visionmedia](https://github.com/visionmedia)）

    
     <a
         class="email js-obfuscate-email"
         data-email="%74%6a%40%76%69%73%69%6f%6e%2d%6d%65%64%69%61%2e%63%61"
         href="mailto:{email}">
           {email}
     </a>


你可以看到在邮箱地址的位置有个`{email}`，以及另一个属性`data-email`。 fajarkoe解释了其原理：

    
    The content of data-email is just the hexadecimal version of your email address
    "tj@vision-media.ca".
    
    It is a sequence of hexadecimal characters, where each character is of the
    form %XY, where X and Y are hexadecimal digits (0-f). For example,
    the first two hexadecimal characters in your case are %66 and %69.
    If you look at the ASCII table (http://en.wikipedia.org/wiki/ASCII),
    the symbol that corresponds to ASCII with hexadecimal number 66 is "f",
    while for hexadecimal number 69 is "i".
    
    You can use play around with this tool http://www.asciitohex.com/.


一旦页面在浏览器被渲染了，十六进制值就被转换为`ascii`：

    
    function hex2a(hexx) {
      var hex = hexx.toString();//force conversion
      var str = '';
      for (var i = 0; i < hex.length; i += 2)
          str += String.fromCharCode(parseInt(hex.substr(i, 2), 16));
      return str;
    }
    
    var $email = $('a.js-obfuscate-email');
    var hexaEmail = $email.data('email');
    hexaEmail = hexaEmail.replace(/%/g, '')
    var email = hex2a(hexaEmail);


一旦你得到了email，DOM元素里的email就被更新了：

    
    var $email = $('a.js-obfuscate-email');
    $email.attr('href', 'mailto:' + email);
    $email.text(email);


这就是全部。希望这个教程有助于你理解屏蔽垃圾邮件收集器的方法。请在下面的评论分享你的想法。

原文地址：[http://www.chennainerd.in/blog/2014/06/11/how-github-hide-email-from-spam-bots-in-profile-page/](http://www.chennainerd.in/blog/2014/06/11/how-github-hide-email-from-spam-bots-in-profile-page/)
