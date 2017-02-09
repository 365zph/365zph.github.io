---
author: viviworld
comments: true
date: 2016-01-20 07:28:18+00:00
excerpt: 我们有相当一部分人用 PHP、ASP 等语言做网站，貌似把 JavaScript 当成了一种补充。然而，随着 NodeJS 的流行以及浏览器的发展，JavaScript
  已经冲到了现代前端 web 开发的最前线。
layout: post
link: http://www.labazhou.net/2016/01/making-the-most-of-the-javascript-language/
slug: making-the-most-of-the-javascript-language
title: 充分发挥 JavaScript 语言的优势
wordpress_id: 3020
categories:
- 编程
tags:
- javascript
- nodejs
- ReactJS
- Underscorejs
- 头等函数
- 闭包
---


	
  * 原文地址（original source）：[http://thenorthcode.net/2016/01/15/making-the-most-of-the-javascript-language/](http://thenorthcode.net/2016/01/15/making-the-most-of-the-javascript-language/)

	
  * 作者（author）：    Rob Bollons（[@RobBollons](https://twitter.com/RobBollons)）





* * *



尽管我在生产环境中使用 JavaScript 长达 8 年之久了，但是，直到最近 2 年，我才开始学习如何正确地编写 JavaScript 代码，根据我对人们的理解，很多开发者都有类似经历。我们有相当一部分人用 PHP、ASP 等语言做网站，貌似把 JavaScript 当成了一种补充。然而，随着 NodeJS 的流行以及浏览器的发展，JavaScript 已经冲到了现代前端 web 开发的最前线。

我想在本文分享一些东西，我觉得它们是当今每个开发者都应该充分发挥 JavaScript 优势的技术点。我不是要列出一份详尽的清单，而是尽量遵循我所认为的重要程度进行论述。

JavaScript 诞生于混乱的年代，因此一些好的和坏的特性就构成了这门语言。当你用 JavaScript 和其它语言开发软件时，你会尝到痛苦的教训，然后不得不回头维护（或扩展）所谓的应用程序。没有这个经历，你将很难理解我要说的内容。下面谈谈我所接受的惨痛教训。


### 1.改变头等函数


头等函数【注1】将一门编程语言变成了成年人的乐高积木。简而言之，有了头等函数，意味着 JavaScript 能够把函数做为参数传递，还能做为另一个函数的返回值、并赋给变量。这意味着你用很少的代码就能实现非常强大的功能，尤其在函数式编程中。举个实际例子：

    
    var myArray = [1, 2, 3, 4, 5, 6]
     
    var add = function (a, b) {
      return a + b;
    };
     
    var getTotal = function (arr) {
      return arr.reduce(add, 0);
    };
     
    getTotal(myArray); // => 21


在第 7 行，我们将一个匿名函数赋给了 `getTotal` 变量。在第 8 行，我们把 `add` 函数做为参数传给了 `reduce` 函数。我们就可以创建更高层次的通用函数，避免了不必要的重复（符合 DRY 原则【注2】）。我们还能实现复合函数【注3】，在例子中，我们把 `add` 函数做为 `reduce` 的参数，组成了复合函数。


### 2.学习 Array 的原生方法


我不单单要讨论 `Array.prototype.push` 或 `Array.prototype.splice`。映入脑海的还有一些更有用的函数：



	
  * [Array.prototype.every](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)

	
  * [Array.prototype.filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

	
  * [Array.prototype.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

	
  * [Array.prototype.join](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

	
  * [Array.prototype.reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)

	
  * [Array.prototype.reverse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)


和第一个例子一样，你可以在复合函数中使用它们，并组装出某些更加通用、但功能强大的、更高级的函数。大部分应用程序都要涉及数据集的操作，为了取得这些数据，你需要明白有哪些可用的工具，这是及其宝贵的。


### 3.使用 ES6（ES2015）


箭头函数、let & const、解构、尾调用优化和模板字符串，都属于 ES6 的一些不错的特性。我个人设法避免使用 `class` 关键字，因为它鼓励类和构造函数的继承，它们更容易引发误用和副作用。

ES6 特性为编写 JavaScript 引入了一种相当新颖的方式，多研究一些细节、探索这些特性，或许是本文的一个部分，我下周可能还会有后续文章。

在浏览器/NodeJS 环境（当写代码时）使用大部分的 ES6 特性，需要用到转码器，相应工具可以访问 [https://babeljs.io/](https://babeljs.io/)。做为一名 web 开发者，我习惯使用 babel 和 browserify，用一条简单命令将 ES6 风格的代码转换成 ES5 的风格：

    
    npm install -g browserify babelify
    browserify -t babelify es6code.js > es5code.js


如果我们用 ES6 重新编写第一个例子中的代码，可能是如下代码：

    
    const myArray = [1, 2, 3, 4, 5, 6]
    const add = (a, b) => a + b;
    const getTotal = (arr) => arr.reduce(add, 0);
     
    getTotal(myArray); // => 21


代码看起来简洁、直观，这应该足以引起你对 ES6 的兴趣了。但要牢记一点，某些和引擎相关的 ES6 特性，可能无法通过转码器。


### 4.理解绊脚石：作用域、闭包和类型转换




#### 作用域


描述这个问题的最好方式就是借助一段代码，我打算借鉴 Douglass Crockfords 《[JavaScript 语言精粹](http://www.amazon.com/exec/obidos/ASIN/0596517742/wrrrldwideweb)》上的一个类似例子，因为它非常贴切：

    
    var foo = function () {
      var a = 2,
          b = 4;
    
      var bar = function () {
        var b = 9,
            c = 14;
        // Here: a is 2, b is 9 and c is 14
    
        a = a + b + c;
        // Here: a is 25, b is still 9 and c is still 14
      };
    
      // Here: a is 2, b is 4 and c is undefined
    
      bar();
      // Now: a is 21, b is still 4 and c is still undefined
    };


可以看到，你声明变量的位置，和内部函数怎样被定义、以及内部函数怎样引起变量 a 改变其值，存在着关系。对变量声明保持清晰的认识，有助你编写更加可靠的软件。对于函数，要清晰地定义输入和可预期的输出，并尽可能明了。


#### 闭包


闭包是 JavaScript 里保持私有变量的一种绝妙方式，不过，貌似也成了被误解的根源。基本上说，闭包支持你从内部函数去访问外部函数的作用域（又称作用域），类似于上面作用域例子中的 a。就这么简单。有意思的是，当你从外部函数返回一个函数、而内部函数可以访问外部函数的作用域时，内部函数将一直保留外部函数的作用域，哪怕过了整个外部函数的生命期。听起来有些复杂，举个例子：

    
    var outer = function () {
      var a = 1; // variables declared outside of the 'inner' function declaration
      var b = 2;
      
      return function inner() {
        return a; // return 'a' that was defined in the outer function.
        // return b; // We could also access 'b' if we felt like it.
      };
    };
    
    var inner = outer(); // the outer function returns the inner function
    inner(); // => 1 // the inner functions still remembers that 'a' was defined as '1' from the outer function




#### 类型转换


由于 JavaScript 貌似荒谬的类型转换，而带来了很多笑话。为了避免所有让人讨厌的地方，最好使用可信任的 `===`，它会在你所期望的大部分情况下，做严格的对象比较。只有一种情况要不好使，当你比较独立的对象字面量时，即使它们具有完全相同的属性和结构，它们也不是相等的，因为它们具有两个完全独立的对象。对于这种情况，只比较对象的每个属性就可以了，像 Underscorejs 之类的资源库就提供了上述情况的深度比较的方法。


### 5.避免类继承


这或许存在争议，因为软件行业的现状就用到了类继承。我敢说，你用类继承写过某个不错的应用程序，但是，如果你这样做了，那么你可能没有发挥 JavaScript 的优势。借助更加有用的方法，你就能用 JavaScript 写出更加轻量、可维护的应用程序。应用程序逃不掉修改的命运，如果你使用类继承的模式，那么当你用到服务于另一个需求的某个对象时，你将不得不继承随之而来的所有东东。当你想做单元测试时，就更加恶心了，你最终不得不为基类模拟出一整套需求，而你的目标只是为了测试高于继承链之上的简单属性。最好扔掉设计蓝图，根据数据流和对象、而非种类，开始思考你的程序。用这种方式思考，可以极大改善程序的可测试性、可维护性和简洁性。


### 6.坚持学习，不要失去信心


很多人抱怨 JavaScript 发展太快，有太多的坑，不过，这只是因为人们没有学习这门语言，没有专注于框架。JavaScript 肯定有一些糟粕，但是它也有一些精华，如果你想拥抱正面的东西，那么你就能充分发挥它的优势。我主要做 C# 开发，但是自从我开始正确地[学习 JavaScript ](http://www.labazhou.net/2014/12/learn-javascript-if-you-want-to-land-a-web-development-job/)之后，它就变成了我的首选语言，因为它具备高度灵活的特点。如果你打算一试，那么 JavaScript 就是踏入函数式编程的入门语言，尤其在和 ReactJS 一起使用时。老实讲，我强烈推荐使用 JavaScript 进行函数式编程。

我希望本文有助于传播 JavaScript 优秀的福音，鉴于 JavaScript 的成功，我也想说句公道话，希望其它语言能从中寻找灵感、而不只是维持现状。



* * *



**传送门**：阮一峰《[ECMAScript 6简介](http://es6.ruanyifeng.com/)》


### 注释

* 注1：头等函数（first-class function）是指在程序设计语言中，函数被当作头等公民。这意味着，函数可以作为别的函数的参数、函数的返回值，赋值给变量或存储在数据结构中。 有人主张应包括支持匿名函数（函数字面量，function literals）。在这样的语言中，函数的名字没有特殊含义，它们被当作具有函数类型的普通的变量对待。1960年代中期，克里斯托弗·斯特雷奇在“functions as first-class citizens”中提出这一概念。[https://zh.wikipedia.org/wiki/%E5%A4%B4%E7%AD%89%E5%87%BD%E6%95%B0](https://zh.wikipedia.org/wiki/%E5%A4%B4%E7%AD%89%E5%87%BD%E6%95%B0)
* 注2：一次且仅一次（once and only once，简称OAOO）又称为Don't repeat yourself（不要重复你自己，简称DRY）或一个规则，实现一次（one rule, one place）是面向对象编程中的基本原则，程序员的行事准则。旨在软件开发中，减少重复的信息。[https://zh.wikipedia.org/wiki/%E4%B8%80%E6%AC%A1%E4%B8%94%E4%BB%85%E4%B8%80%E6%AC%A1](https://zh.wikipedia.org/wiki/%E4%B8%80%E6%AC%A1%E4%B8%94%E4%BB%85%E4%B8%80%E6%AC%A1) 
* 注3：在数学领域，两个函数的复合函数指一个将第一个函数作用于参数，然后再将第二个函数作用于所得结果的函数。[https://zh.wikipedia.org/wiki/%E5%A4%8D%E5%90%88%E5%87%BD%E6%95%B0](https://zh.wikipedia.org/wiki/%E5%A4%8D%E5%90%88%E5%87%BD%E6%95%B0) 
