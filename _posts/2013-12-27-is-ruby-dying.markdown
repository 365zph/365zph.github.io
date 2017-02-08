---
author: viviworld
comments: true
date: 2013-12-27 01:02:24+00:00
layout: post
link: http://www.labazhou.net/2013/12/is-ruby-dying/
slug: is-ruby-dying
title: Ruby将死？
wordpress_id: 58
categories:
- 编程
tags:
- nodejs
- R
- ruby
- rubygem
- 编程
---

最近我在用nodejs，和同事沟通了nodejs比ruby占用了更大的比例。我认为在为新项目选择语言、开发框架时，语言的流行程度是重要的乱点。

gem从过去到现在的发布日期图表可以帮助得到答案。rubygems（译者注：指[http://rubygems.org](http://rubygems.org)）网页只显示了大部分流行gem的数据，但是我真正有兴趣的是查看最近的进展。我的理论是，如果开发者对不同gem的贡献减缓了，那么语言的受欢迎度也就有了。


### 获取数据


经过一番搜罗，我找不到能够找到格式化的数据以便将来放在图表里。既然如此，我想抓取这个网站的数据。nodejs cheerio（###http://matthewmueller.github.io/cheerio/）做为我选择的工具。通过运行 gem list --remote，它就能返回一个gem列表。幸运的是，每个gem有一个简单URL的主页。比如，Rails的主页是http://rubygems.org/gems/rails

    
    var request = require('request'),
        cheerio = require('cheerio'),
        bytes = require('bytes'),
        sys = require('sys'),
        fs = require('fs'),
        exec = require('child_process').exec;
    
    console.log('program begin: ' + new Date());
    fs.openSync('out.csv', 'w');
    
    exec("gem list --remote", { maxBuffer: 20000*1024 }, processGems);
    
    function processGems(error, stdout, stderr){
        var gems = stdout.split("\n");
        console.info('total gems parsed: ' + gems.length);
        gems.forEach(function(gem){
            gem = gem.substring(0, gem.indexOf(' '));
            console.info('crawling gem: ' + gem);
            request({
                uri: 'https://rubygems.org/gems/' + gem,
            }, getContent);
        });
    }
    
    function parseSize(size){
        size = size.replace(' ', '');
        size = size.replace(/\)|\(/g, '');
        size = size.toLowerCase();
        try{
            size = bytes(size);
        }
        catch(e){
            console.error('unable to parse :' + size);
        }
        return size;
    }
    
    function escape(s){
        if (s.indexOf('"') != -1) {
            s = s.replace(/"/g, '""');
        }
        if (s.match(/"|,/)) {
            s = '"' + s + '"';
        }
        return s;
    }
    
    function getContent(error, response, body){
        if (error && response.statusCode != 200) {
            console.error(error);
            console.error(response);
            return;
        }
        console.info(response.request.href + ' complete, status: ' + response.statusCode);
    
        var $ = cheerio.load(body),
            gem = $('div.title h2 a').text(),
            latest = $('div.versions ol li').last(),
            version = $(latest).children('a').text(),
            date = $(latest).children('small').text(),
            size = $(latest).children('span.size').text(),
            line;
        line = escape(gem) + ',' +
            escape(version) + ',' +
            escape(date) + ',' +
            parseSize(size) + '\n';
        fs.appendFile('out.csv', line);
    }




###  抽取数据


抽取出来的数据文件有2.7M，可以从这里（译者注：链接已无法打开）找到。这还不是我想要的能够做成图表的格式。我规划的图表：Y轴是每天发布的次数，X轴是发布日期。因此我需要两列，一列是发布日期，另一列是当天的发布次数。下面的nodejs能够将数据按照我想要的格式导入csv文件。

    
    var __ = require('lodash'),
        moment = require('moment'),
        csv = require('csv'),
        fs = require('fs');
    
    fs.openSync('releasedate.csv', 'w');
    
    csv()
        .from.path(__dirname+'/gems.csv', { delimiter: ',', escape: '"' })
        .to.array( function(data){
            var csv = '';
            var grouped = __.groupBy(data, function(gem) {
                return gem[2];
            });
    
            var array = []
            for(var gem in grouped) {
                array.push({
                    date: escape(gem),
                    unixtime: moment(gem, 'MMM D, YYYY').valueOf(),
                    released: grouped[gem].length
                });
            }
            arraySorted = __.sortBy(array, 'unixtime');
            arraySorted.forEach(function(gem){
                csv += gem.date + ',' + gem.released + '\n'; 
            });
            fs.appendFile('releasedate.csv', csv);
        } );
    
    function escape(s){
        if (s.indexOf('"') != -1) {
            s = s.replace(/"/g, '""');
        }
        if (s.match(/"|,/)) {
            s = '"' + s + '"';
        }
        return s;
    }




### R图


【注1】非常棒！图表搞定了。我最初的想法是用Excel，但是我很快发现Excel的数据不能超过255行。这肯定不行了，65k的数据，我只能启动R。下面两行代码就能生成我想要的折线图，这让我想起了为什么我喜欢R。

    
    data<-read.csv('releasedate.csv')
    plot(zoo(data$Released,as.Date(data$Date,"%m/%d/%y")),xlab="Release Date",ylab="Releases",main="RubyGems Release Date Trend")


最终下面的折线图显示了我寻找的趋势：

[![rubygems按日发布的gems次数统计图](http://www.labazhou.net/wp-content/uploads/2013/12/trend.png)](http://www.labazhou.net/wp-content/uploads/2013/12/trend.png)

开始我有些吃惊，和我想象的“慢”不一样。仔细考虑一下，院里开发者仍然在使用gem：



	
  1. Ruby讨论组非常钟情且有强大的号召力。

	
  2. 有丰富的在线学习资源

	
  3. Rails大大降低了网站开发的门槛


你们觉得如何呢？Ruby死了吗？过去你用Ruby，如今你开始用其他语言了？想看评论，请移步到 [Hackernews](https://news.ycombinator.com/item?id=6959355)。



原文地址：[http://jmoses.co/2013/12/21/is-ruby-dying.html](http://jmoses.co/2013/12/21/is-ruby-dying.html)
