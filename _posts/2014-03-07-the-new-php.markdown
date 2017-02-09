---
author: viviworld
comments: true
date: 2014-03-07 07:54:17+00:00
layout: post
link: http://www.labazhou.net/2014/03/the-new-php/
slug: the-new-php
title: 新的PHP
wordpress_id: 411
categories:
- 编程
tags:
- CakePHP
- CodeIgniter
- Composer
- facebook
- HHVM
- nginx
- Packagist
- php
- PHP-FIG
---

## PHP在改进和新标准上正经历着一次复兴


很多人又爱又恨的编程语言正经历着一次复兴。这不是你父母的PHP。新的PHP是一种更加成熟的语言，包括社区标准、正在增加的互操作组件（interoperable component）的吸引力，和提高性能的有激情的运转。如果你因其它语言而放弃了[PHP](http://php.net/)，或者如果你是一名忽略了PHP最近变化的老手，你值得回头再看一眼PHP。


### 语言特性


PHP 5.5（写本文时的最新稳定版本）相较于早期版本已经有了大幅的改进。最近的PHP包含了强大的新特性和有帮助的开发者工具，比如内建的web服务器，简单迭代的生成器以及命名空间。在PHP 5.4，traits【注1】被引进来解决单继承语言的代码复用，还有闭包，让你以函数风格来编写代码。其它重要的特性包括内建的FastCGI进程管理器和phpdbg debugger，以及一个新的密码哈希API，便于在PHP里哈希和安全地管理密码。


### 互操作组件


一些年前，PHP有一些大型框架（比如CakePHP、CodeIgniter等）。每个框架都是一个孤岛，提供了通常可以在其他框架找到的功能的自我实现。不幸的是，这些孤立的实现可能彼此不兼容，强迫开发者为了一个既定项目而封闭在一个特定框架里。

今天情况不同了。新的PHP社区采用包管理和组件类库来mix以及匹配最好的可获得的工具。我喜欢把它比喻为杂货铺。如果我需要使用一个远端API，我将访问通道3选取[Guzzle](https://guzzle.readthedocs.org/en/latest/)。我需要一个请求路由吗？[Symfony\Routing](http://symfony.com/doc/current/components/routing/introduction.html)、[Aura\Router](https://github.com/auraphp/Aura.Router/tree/master)、[Slim](http://slimframework.com/)、[Pux](https://github.com/c9s/Pux)和[nikic\fast-route](http://nikic.github.io/2014/02/18/Fast-request-routing-using-regular-expressions.html)在通道4。你明白了大意。新的PHP是关于使用相对优势来为你的项目提供最好地融合各个部分的互操作组件的。

开始使用PHP组件的最简单方式是安装[包依赖管理器Composer](http://getcomposer.org/)，然后再浏览[包管理仓库Packagist](http://packagist.org/)。


### 社区标准


因为新的PHP社区比较大，有无数个不同的组件，所以组件坚持一种代码风格的指导和共享接口是至关重要的。开发者以学习曲线低而开始使用新组件，组件通过共享接口可以更加容易地协同工作。

[PHP Framework Interop Group](http://www.php-fig.org/)（缩写为PHP-FIG）是框架开发者和PHP社区代表的非官方团体，但是具有威信，其目标是“在项目间讨论公共部分，并找到一起工作的方法”。PHP-FIG目前通过了4个标准：[PSR-0](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md)，[PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md)，[PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)和[PSR-3](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-3-logger-interface.md)。这些标准建议了文件、类和命名空间的约定，代码风格指导，以及一套共享接口来鼓励组件和框架相互可操作性。

PHP-FIG绝不是强制要求，但是它的建议标准被很多流行的PHP框架采用了。它的目标是令人钦佩的，它欢迎反馈。我强烈鼓励你考虑在你的PHP代码里实现PHP-FIG标准，并提交关于未来PHP-FIG建议的反馈。


### 性能


PHP下面也有令人兴奋的东东。PHP Zend Engine最近引进了内存使用优化。PHP 5.5的内存使用比之前的版本少了很多。[PHP ZEND ENGINE](http://us1.php.net/manual/en/internals2.php)也提供了内置的[FastCGI进程管理器](http://www.php.net/manual/install.fpm.php)，它通常位于反向代理后面（例如nginx），将负责进程派生和管理。这缓解了把新的PHP实例通过Apache的mod_php模块嵌入到每个Apache进程的需求。

Facebook也在它的另类开源PHP引擎 HipHop Virtual Machine（HHVM）上做了多项改进。HHVM使用一种即时编译技术来提供令人难以置信的性能，无论PHP开发者习惯哪个版本，都易于使用。和PHP Zend Engine一样，HHVM也包括FastCGI支持。HHVM在2014年早期的目标是通过前20个PHP框架的100%的单元测试，它最近宣布了未来6个月的开发[路线图](http://www.hhvm.com/blog/3743/hhvm-the-next-six-months)。要留意HHVM。我有个感觉，在接下来的几年里它将在PHP领域产生深远的影响。


### 资源





	
  * [PHP Documentation](http://php.net/docs.php)

	
  * [PHP User Groups](http://php.ug/)

	
  * [PHP Mentoring](http://phpmentoring.org/)

	
  * [PHP Framework Interop Group](http://www.php-fig.org/)

	
  * [Code Academy PHP Track](http://www.codecademy.com/tracks/php)

	
  * [PHP The Right Way](http://phptherightway.com/)

	
  * [websec.io](http://websec.io/)

	
  * [Nomad PHP](http://nomadphp.com/)


原文地址：[http://programming.oreilly.com/2014/03/the-new-php.html](http://programming.oreilly.com/2014/03/the-new-php.html)
注1：自 PHP 5.4.0 起，PHP 实现了代码复用的一个方法，称为 traits。Traits 是一种为类似 PHP 的单继承语言而准备的代码复用机制。Trait 为了减少单继承语言的限制，使开发人员能够自由地在不同层次结构内独立的类中复用方法集。 [http://www.php.net/manual/zh/language.oop5.traits.php](http://www.php.net/manual/zh/language.oop5.traits.php)
