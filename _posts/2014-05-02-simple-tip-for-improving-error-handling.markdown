---
author: viviworld
comments: true
date: 2014-05-02 01:02:21+00:00
layout: post
link: http://www.labazhou.net/2014/05/simple-tip-for-improving-error-handling/
slug: simple-tip-for-improving-error-handling
title: 关于改善你的Objective-C应用程序错误处理的简单建议
wordpress_id: 625
categories:
- 编程
tags:
- api
- objective-c
---

Objective-C多数时候倾向于用错误对象代替异常。如果某个地方失败了，错误将被包含在一个合法的指针里，否则它就是nil。如果你不关心错误，你可以在几乎所有API里传入nil。然而，如果你和一个很大的代码库或一个团队工作，或者如果你想写一个不错的健壮应用程序，你应当小心地处理所有错误。过去我的惯例是强迫调用者传入一个合法指针而不是NULL。它简单得就像放置一些断言。这里是当我想强迫调用者处理错误检查时，要做的。

下一步就是确保调用者实际上处理错误或者适当地冒泡。那是完全不同的处理，但至少我们这样子开始了。


<blockquote>

>     
>     - (BOOL)fetchProfilePictureWithError:(NSError * __autoreleasing *)error
>     {
>         NSParameterAssert(error != NULL);
>         NSParameterAssert(*error == nil);
>     
>         // do the fetch
>     }
> 
> 
</blockquote>


它看起来非常严格，但我的经验认为早点儿加强错误处理比晚点儿要好，这种模式已经帮了我很多忙。

原文地址：[http://vombat.tumblr.com/post/84271655634/simple-tip-for-improving-error-handling-in-your](http://vombat.tumblr.com/post/84271655634/simple-tip-for-improving-error-handling-in-your)
