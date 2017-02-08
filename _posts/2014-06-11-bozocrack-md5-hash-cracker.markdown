---
author: viviworld
comments: true
date: 2014-06-11 00:33:07+00:00
layout: post
link: http://www.labazhou.net/2014/06/bozocrack-md5-hash-cracker/
slug: bozocrack-md5-hash-cracker
title: 一个傻瓜而有效的MD5破解程序-BozoCrack
wordpress_id: 752
categories:
- 软件
tags:
- BozoCracker
- cracker
- google
- hash
- md5
- ruby
- 彩虹表
---

BozoCrack是一款令人沮丧的、有效的MD5密码哈希破解程序，几乎零CPU/GPU负载。与彩虹表（Rainbow Tables）、字典或暴力破解不同，BozoCrack简单地找到纯文本密码。具体来说，它Google这个MD5哈希值，期望这个纯文本出现在搜索结果第一页的某个地方。

这应该比以前好使。


### 原理


基本用法：


<blockquote>$ ruby bozocrack.rb my_md5_hashes.txt</blockquote>


输入文件没有特定格式要求。BozoCrack自动挑选看起来像是MD5哈希值的字符串。每行不应当包含一个以上的hash值。

输出示例：


<blockquote>$ ruby bozocrack.rb example.txt
Loaded 5 unique hashes
fcf1eed8596699624167416a1e7e122e:octopus
bed128365216c019988915ed3add75fb:passw0rd
d0763edaa9d9bd2a9516280e9044d885:monkey
dfd8c10c1b9b58c8bf102225ae3be9eb:12081977
ede6b50e7b5826fe48fc1f0fe772c48f:1q2w3e4r5t6y</blockquote>




### 为了什么


为了显示一个使用文本MD5做为密码哈希机制的想法是多么地糟糕。老实讲，如果某些密码能被这个软件破解，就不要找借口了。


### 作者


BozoCrack的作者是Juuso Salonen，他是Radio Silence和Private Eye的幕后家伙。

原文地址：[https://github.com/juuso/BozoCrack](https://github.com/juuso/BozoCrack)
注1：彩虹表（Rainbow Tables）就是一个庞大的、针对各种可能的字母组合预先计算好的哈希值的集合，不一定是针对MD5算法的，各种算法的都有，有了它可以快速的破解各类密码。越是复杂的密码，需要的彩虹表就越大，现在主流的彩虹表都是100G以上。[http://zhaoxiaobu.blog.51cto.com/878176/461016](http://zhaoxiaobu.blog.51cto.com/878176/461016)
