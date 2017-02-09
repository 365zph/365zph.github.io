---
author: viviworld
comments: true
date: 2014-11-25 06:49:41+00:00
layout: post
link: http://www.labazhou.net/2014/11/coffeescript-typescript-javascript/
slug: coffeescript-typescript-javascript
title: CoffeeScript？TypeScript？还是JavaScript？
wordpress_id: 1354
categories:
- 编程
tags:
- AngularJS
- CoffeeScript
- github
- Grunt
- javascript
- jquery
- nodejs
- TypeScript
- 代码
---

原文地址（source）：[http://innoarchitech.com/coffeescript-typescript-javascript/](http://innoarchitech.com/coffeescript-typescript-javascript/)

请注意本文只是我的偏见，我努力地理解借助[CoffeeScript](http://www.labazhou.net/2014/11/how-to-write-a-simple-interpreter-in-javascript/)或TypeScript之类的编译器写JavaScript代码的理由。静态编译、强类型语言和框架，我有着这些流行的、丰富的背景。我的上一份工作就是使用TypeScript，因为我不得不使用。那是一段不快乐的时光，我将因此而离开。

我很幸运地把自己从这种困境和负担中释放出来，正在完全地使用JavaScript编写代码，我对此感到格外高兴！如果我对于这种变化的热情还不够明显，请让我向你保证，我现在更开心了。有一点很重要，我不是在暗示静态编译或强类型语言有什么错误，因为它肯定没错。它只不过不再是我的菜了。

鉴于JavaScript的动态本性以及缺乏静态类型检查，我可能编写着低质量代码，充斥着bug却不能在编译时发现，对吗？答案是毫不含糊的，不对！我从来不能这样有动力、多产、富有表现和高效。我没有编写过最少bug的高质量代码，也不能在发现bug后快速修复。或许你想知道，我是否在编写风格统一的JavaScript，它们遵循最佳实践和风格，却没有编译器？答案是，对的！我不是故意在这里鼓吹自己，而是要指出，静态编译的缺乏不一定会导致更多的bug和低质量的代码。

的确，有很多方法来确保[JavaScript](http://www.labazhou.net/tag/javascript/)代码被正确地编写、遵循推荐的风格和最佳实践。更不要说编写高质量JavaScript成为了第二天性，自然地，你倾向于遵循你学到的、同样优秀的模式。你还应该总是编写合适的单元测试，这是一种最佳实践和另一种应对bug的防御，有助于确保预期的功能。我们不要忘了，合适的代码审核也是一种最佳实践，应该去用。

那么，为什么要用这些编译器，好处又是什么呢？答案是，我也不知道。是不是应该有可以编译成Ruby和Python的RubyScript和PythonScript呢？在我看来，如果你不喜欢、或者不想编写JavaScript代码，那么你可能就不应该做一名JavaScript开发人员。它是古怪的、不完美的语言？它绝对是，但是它一直在变得更好。大部分的怪癖和遗漏在ECMAScript Harmony【注1】中提出了，比如：ES.next。

我认为使用某种编译器只有一个原因，那就是，如果你是高级专家、JavaScript大拿，不喜欢原生JavaScript，只是想简单快捷地做些东西。如果你不是刚才提到的专家，那么我真地相信你只是在伤害自己而逃避原生JavaScript。你干嘛这么问？答案是，JavaScript正变得无处不在，成为庄重的、令人惊叹的语言。它已经融入了所有的web和移动环境、使用Node.js的服务器，还有数据库（比如MongoDB），甚至最近的硬件级别的处理（比如arduino）。

我读了很多博客、newsletter、书、文章、论文、文档、MDN等与JavaScript相关的东西。它们都包含了用原生JavaScript编写的代码，我很少看到作者用CoffeeScript或类似语言呈现的代码，在极少场合碰到这些代码时，我会立即停止阅读，因为我只对JavaScript、而不是它的其它版本感兴趣。

如果你曾经计划、或者有兴趣在工作中用到基于JavaScript的数据库（比如MongoDB），那么你需要知道如何编写JavaScript。你不能用CoffeeScript来查询MongoDB，也不能没有预编译就用[CoffeeScript](http://coffeescript.org/)为Node.js编写基于服务器端的JavaScript，即使你有能力，也不能这样做。

在GitHub上，如潮水般涌来的、表面上有数百万种的JavaScript资源库和框架，该怎么样呢？大型的有jQuery、AngularJS、Underscore等等。我强烈推荐深入学习JavaScript，这样你不仅能够阅读和理解源代码，还可以调试它。是的，说到了调试，不管是你是在浏览器，还是使用Webstorm为[Node.js](http://www.labazhou.net/tag/nodejs/)调试JavaScript，都会涉及到原生JavaScript。

我最后想指出的是与其他人的协作（比如GitHub），或者找一份JavaScript工作室的工作。如果顺利的话，掌握原生JavaScript的好处应该比较明显。当你入职第一天走进严肃的JavaScript工作室、提出CoffeeScript编译器的问题，你能够想象得到这是什么情景吗？

重申，如果你是高级专家JavaScript大拿，那么编译器可能就是好的吗？尽管如此，我怀疑你会不会成为这样的大拿，如果你因为青睐某种编译器而避免学习、编写原生JavaScript的话。如果你担心静态检查和风格，可以尝试一些构建工具（比如，Grunt、Gulp、Node、NPM等）。很多插件运行非常不错。对于既定代码，使用CoffeeScript或TypeScript是为了查看编译好的JavaScript，然后模拟原生代码的输出。无论怎样，帮自己一个忙，优先掌握JavaScript。

注1：ECMAScript Harmony将会以“ECMAScript 6”发布。[http://zh.wikipedia.org/wiki/ECMAScript](http://zh.wikipedia.org/wiki/ECMAScript)
