---
author: viviworld
comments: true
date: 2014-04-27 08:14:10+00:00
layout: post
link: http://www.labazhou.net/2014/04/build-make-no-more/
slug: build-make-no-more
title: 构建工具 ------Make，不需太多
wordpress_id: 608
categories:
- 编程
- 软件
tags:
- Ant
- DSL
- Grunt
- javascript
- Make
- PSake
- ruby
---

整个周末我不得不更新我网站上的一些CSS，导致我更新了一些LESS文件。我用于这个网站的模板使用Grunt，这迫使我通过npm下载了整个因特网。而我需要做的全部就是把一个text-indent设置为0.

如果你从来没有见过Grunt，下面是个例子：

    
    module.exports = function(grunt) {
    
        grunt.initConfig({
            jshint: {
                options: {
                    jshintrc: '.jshintrc'
                },
            all: [
                'Gruntfile.js',
                'asselts/js/*.js'
            ]
        }


我发现它命名考究，就像游戏《Halo》【注1】里的丑陋小怪兽。

当然，你不必使用Grunt。事实上，[Grunt已经死了](http://www.100percentjs.com/just-like-grunt-gulp-browserify-now/)。现在是Gulp的时代：

    
    var gulp = require('gulp');
    
    var coffee = require('gulp-coffee');
    var concat = require('gulp-concat');
    var uglify = require('gulp-uglify');
    var imagemin = require('gulp-imagemin');
    
    var paths = {
      scripts: ['client/js/**/*.coffee', '!client/external/**/*.coffee'],
      images: 'client/img/**/*'
    };
    
    gulp.task('scripts', function() {
      // Minify and copy all JavaScript (except vendor scripts)
      return gulp.src(paths.scripts)
        .pipe(coffee())
        .pipe(uglify())
        .pipe(concat('all.min.js'))
        .pipe(gulp.dest('build/js'));
    });


但是如果你不喜欢JavaScript，你很可能从事Rake，它就是Ruby：

    
    task :default => [:test]
    
    task :test do
      ruby "test/unittest.rb"
    end


如果你喜欢Ruby但不想安装它，如果你在Windows，就用PSake：

    
    properties {
      $testMessage = 'Executed Test!'
      $compileMessage = 'Executed Compile!'
      $cleanMessage = 'Executed Clean!'
    }
    
    task default -depends Test
    
    task Test -depends Compile, Clean {
      $testMessage
    }
    
    task Compile -depends Clean {
      $compileMessage
    }
    
    task Clean {
      $cleanMessage
    }
    
    task ? -Description "Helper to display task info" {
    	Write-Documentation
    }


如果你不喜欢Ruby，可以安装Java，使用Gradle。它是Groovy，[有65章的文档](http://www.gradle.org/docs/current/userguide/userguide.html)，还有一些附录防止你没有东西可读。

    
    buildscript {
        project.ext.kotlinVersion = "0.7.270"
    
        version = "0.1-SNAPSHOT"
    
        repositories {
            mavenCentral()
            maven {
                url 'http://oss.sonatype.org/content/repositories/snapshots'
            }
        }
        dependencies {
            classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$ext.kotlinVersion"
        }
    }
    
    apply plugin: 'kotlin'
    apply plugin: 'maven'
    apply plugin: 'maven-publish'
    
    repositories {
        mavenLocal()
        mavenCentral()
        maven {
            url 'http://oss.sonatype.org/content/repositories/snapshots'
        }
    }


如果你喜欢Rake，不喜欢Ruby，但是喜欢JavaScript，试试[Jake](http://www.cappuccino-project.org/blog/2010/04/introducing-jake-a-build-tool-for-javascript.html)。

最后，如果你真的没有更好的了，挑一个你喜欢的基于XML的构建工具，比如Ant、NAnt或MSBuild。

    
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <ItemGroup>
        <Compile Include="helloworld.cs" />
      </ItemGroup>
      <Target Name="Build">
        <Csc Sources="@(Compile)"/>
      </Target>
    </Project>


当然，你应当只是从使用Make开始

    
    all: hello
    
    hello: main.o factorial.o hello.o
    	g++ main.o factorial.o hello.o -o hello
    
    main.o: main.cpp
    	g++ -c main.cpp
    
    factorial.o: factorial.cpp
    	g++ -c factorial.cpp
    
    hello.o: hello.cpp
    	g++ -c hello.cpp
    
    clean:
    	rm -rf *o hello




### Make之上的DSL


如果你看了上面的所有例子，它们只是根据你的语言选择的、在Make之上的DSL。甚至有些情况，只是一些语法糖【注2】。它们仍然集中在同样的核心概念：



	
  * 原始的

	
  * 目标

	
  * 任务


还有，强迫我们在书写形式上转录一个构建系统的复杂度。

对于每种新的构建工具，我们要做的一切仅仅是增加另一种语法来学习，另一系列要下载、配置和安装的工具和插件。为了什么？只是为了一点儿更好的语法？没有花一点点时间考虑在所有这些新“发明”之后，我们留下了什么？当然，一些语言和平台或许需要特定技术的任务，但是所有这些新的构建工具和语法都是必需的吗？

我认为Gradle的口号对于描述所有这些不同的构建工具，多少有些合适：‘自动化的进化’。是的，我们已经进化了，因为我们从tab、行进化到了XML，然后进化到了，恩，哦，tab、行和花括号。


### Make，不需要太多


如果你准备开发另一个构建工具，仔细考虑你将比现存构建工具提供哪些好处。只是增加另一套自定义的DSL和语法不会真正地解决任何问题。

我认为在构建自动化上可能有创新。我们对于软件如何构建、必要的需求已经有了大量的现存认识，我们已经看到了使用配置的约定的好处，我们已经创造了强大的分析工具。综合这些因素，我感觉有一个巨大的潜能来创造一个构建工具，它更关注可发现性，而不是我们不得不明确声明我们想做什么。

因此，请不要太多的Make。

原文地址：http://hadihariri.com/2014/04/21/build-make-no-more/
注1：http://baike.baidu.com/subview/83715/13362635.htm
注2：语法糖（Syntactic sugar），也译为糖衣语法，是由英国计算机科学家彼得·约翰·兰达（Peter J. Landin）发明的一个术语，指计算机语言中添加的某种语法，这种语法对语言的功能并没有影响，但是更方便程序员使用。通常来说使用语法糖能够增加程序的可读性，从而减少程序代码出错的机会。http://baike.baidu.com/view/1805428.htm
