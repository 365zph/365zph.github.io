---
author: viviworld
comments: true
date: 2014-01-18 13:29:11+00:00
layout: post
link: http://www.labazhou.net/2014/01/utf8-everywhere/
slug: utf8-everywhere
title: UTF-8 Everywhere（节译）
wordpress_id: 198
categories:
- 编程
tags:
- c++
- unicode
- utf8
- windows
---

### 文档宗旨


为了扩大使用和支持UTF-8编码，为了坚信它应该作为存放在内存或磁盘上的默认编码选择，无论商业还是其他方式，我们相信所有其它Unicode编码（通常是文本）应该被归入优化的很少发生的极端情况，也应该被主流用户无视。

特别地，我们相信API类库（处理文本的特定类库除外）不支持有些流行的UTF-16编码（在Windows里，它被错误地当作’widechar‘和’unicode‘的同义词来用）。

由于历史原因以及缺乏API对内置UTF-8的支持，这个标准还不太受欢迎，不管如何，这个文档推荐选择UTF-8用作Windows应用程序的文本存储。并且我们相信即使在这个平台，下面的内容仍然 比 内建支持的缺乏 重要。同样，我们建议永远忘掉’ANSI 代码页‘是什么以及它们的用法。在任何文本字符串混合任意数量的语言是客户的权力。

我们建议避免依赖_UNICODE定义的C++应用程序代码，这包括Windows的TCHAR/LPTSTR类型和定义在宏里的API，比如CreateWindow。我们也建议用替代方法来完成这些API具有的功能。

我们也相信，如果应用程序不应该处理文本，那么配套功能必须使得 程序无需考虑编码问题 成为可能。例如，一个文件拷贝工具集不应该为了支持非英语文件名而按照不同的方式来编写代码。[Joel关于Unicode的大作](http://www.joelonsoftware.com/articles/Unicode.html)给初学者解释得很好，但是它缺乏最重要的部分：如果一个程序员没有注意到[字符串里有什么](http://en.wikipedia.org/wiki/Opaque_data_type)，他应该如何做。

原文地址：[http://www.utf8everywhere.org](http://www.utf8everywhere.org)
