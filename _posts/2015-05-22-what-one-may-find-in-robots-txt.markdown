---
author: viviworld
comments: true
date: 2015-05-22 14:14:06+00:00
excerpt: 对于这个意图，已知的子目录列表常常被用于 Skipfish 或 wfuzz。如果有额外的上下文信息被获取到，它可能会添加到该列表。我打算把我的列表建立在网站公开的最有价值的地方：robots.txt。在这次探索中，我碰到一些有趣的发现。
layout: post
link: http://www.labazhou.net/2015/05/what-one-may-find-in-robots-txt/
slug: what-one-may-find-in-robots-txt
title: robots.txt 探索笔记
wordpress_id: 2069
categories:
- 安全
- 网络
tags:
- Amazon
- Common Crawl
- Disallow
- Jaccard index
- Nutch
- robots
- Skipfish
- WARC
- wfuzz
- 斯诺登
---


	
  * 原文地址（original source）：[http://xn--thibaud-dya.fr/robots.txt.html](http://xn--thibaud-dya.fr/robots.txt.html)

	
  * 注：本文经过和原作者邮件确认翻译许可，未找到 twitter 地址。





* * *





### 介绍


在 web 应用程序测试的侦查阶段，测试人员（或攻击者）通常使用已知的子目录列表来暴力破解服务器，以找到隐藏资源。对于这个意图，已知的子目录列表常常被用于 Skipfish 或 wfuzz。如果有额外的上下文信息被获取到，它可能会添加到该列表。最重要的是，一旦测试完成（或者命令执行已被完成），以及一个列表或服务器配置信息被揭露，该列表就会被更新，而不会缺失任何一条。

我最近丢失了我的个人列表，决定从头再建一份。这种列表是不受时间限制的。取决于某种 web 技术的理解力，它需要定期刷新。我打算把我的列表建立在网站公开的最有价值的地方：robots.txt。在这次探索中，我碰到一些有趣的发现。

免责声明：整个练习使用了互联网允许公开访问的资源。从最坏方面说，只是互联网礼仪被破坏了。


### robots.txt


这些文件位于网站服务器主目录下，指示站点允许网络爬虫（比如 Google robots）访问哪个部分以进行索引。它们应该被机器分析、但具有人类可读性。例如：

    
    User-agent: *
    Disallow: /admin/
    Disallow: /stats/
    Disallow: /internaljobs/
    Disallow: /internaljobsbyorganization/
    Disallow: /internaljobsearch/


你或许看到了，Disallow 指令给攻击者提供了宝贵信息，哪些地方是值得查看的。另外，如果对于一个站点是这种情况，那么它就值得用于检查另一个站点。


### 抓取


为了搞到一套相关的 robots.txt 文件，有必要从主机名列表着手，如果可能的话，主机名要包含宽泛的互联网、而不要被限制为任意子集（和 [主题爬虫](http://en.wikipedia.org/wiki/Focused_crawler)【注2】 相反）。

大多数商业搜索引擎不再提供免费的解决方案。幸运的是，[Common Crawl](http://commoncrawl.org/) 项目通过 S3 提供了最近的抓取结果。

该抓取被分隔在 1GB 的文档里（解压缩后有 4GB）。（截止 2015 年 2 月份，它们超过了 33,000 条）。我写了一个脚本，从这些解压缩后的 WARC【注3】 抽取出找到的所有主机名：

    
    require 'set'
    
    URL_PATTERN = %r{
        (?:(?:https?)://)
        (?:
           (?:(?:[a-z0-9][a-z0-9\-]*)?[a-z0-9]+)
           (?:\.(?:[a-z0-9\-])*[a-z0-9]+)*
           (?:\.(?:[a-z]{2,}))
        )
        (?::\d{1,5})?
    }xin
    
    tlds = File.open("tlds-alpha-by-domain.txt").each_line.collect {|w| w.chomp.downcase}
    
    s = Set.new
    
    begin
      File.open(ARGV[0], 'rb').each_line.with_index do |line, i|
        s.merge(line.scan(URL_PATTERN).select {|f|
            # Extract TLD
            h, m, tail = f.rpartition(":")
            w = (h.include?"/") ? h : tail
            head, m, tld = w.rpartition(".")
            tlds.include? tld.downcase
          })
      end
    rescue Interrupt
    end
    puts s.to_a.join("\n")


我们得到了一份主机名列表（[TLD](http://en.wikipedia.org/wiki/Top-level_domain)【注4】根据白名单来匹配以避免误报）。然后我借助 [Burst](https://github.com/tweksteen/burst) 使用这个列表来下载 robots.txt：

    
    import socket
    import random
    import threading
    
    from burst.all import *
    from burst.exception import BurstException
    from burst.utils import chunks
    
    nthreads = 4
    slice_sz = 200
    switch_session('hosts')
    
    hosts = open("hosts").read().splitlines()
    random.shuffle(hosts)
    
    def worker(s):
      for i, h in enumerate(s):
        r = create(h + "/robots.txt")
        # Check if we have visited this host before
        for hr in history:
          if hr.hostname == r.hostname:
            break
        else:
          try:
            r()
          except (BurstException, socket.error):
            pass
    
    for ch in chunks(hosts, slice_sz):
      slices = chunks(ch, nthreads)
      jobs = []
      for s in slices:
        t = threading.Thread(target=worker, kwargs={"s": s})
        jobs.append(t)
        t.start()
      for j in jobs:
        while j.is_alive():
          j.join(1)
      save()


所有东东被分割为 chunks。一次处理一个 chunk，然后会话被保存。这样，在抓取过程中，就能查看结果。

手动使用 Burst 接口，就可以查找特定模式了：

    
    $ burst -rs hosts
    hosts >>> history.responded().filter(lambda x: "Disallow: /admin/" in x.response.content)
    {200:1563 | get.kim, rockville.wusa9.com, mars.nasa.gov, ... }


抓取的某些统计数据：59,558 个网站被抓取，59,436 个网站给我们发送了响应。这是 Common Crawl 项目结果的、极具活力的较好体现。其中，37,431 个网站响应的 HTTP 状态码为 200。其中，35,376 个网站返回了貌似合法的 robots.txt（例如，匹配至少一个标准指令）。


### 意料之外的指令


robots.txt 定义非常少。让我们排除已知指令，看看还有哪些指令：

    
    RE_COMMENT = re.compile(r'(^|\n|\r)\s*#', re.I)
    headers = [r'Disallow', "Allow", "User-Agent", "Noindex", "Crawl-delay",
               "Sitemap", "Request-Rate", "Host"]
    all_reg = [ re.compile(r'(^|\n|\r)[ \t]*' + h + r'[ \t]*:?', re.I) for h in headers]
    
    switch_session('hosts')
    
    krs = history.responded().filter(
            lambda x: x.response.status == "200" and
                      len(x.response.content) > 0)
    
    words = defaultdict(int)
    for r in krs:
      # At least one directive recognised (avoid html answers)
      for reg in all_reg:
        if reg.findall(r.response.content):
          break
      else:
        continue
      # Dump anything not matching an expected regex
      for l in r.response.content.splitlines():
        for reg in all_reg + [RE_COMMENT,]:
          if reg.findall(l):
            break
        else:
          words[l] += 1
    
    print "\n".join(
            [ str(v) + ":" + k for k,v in
                sorted(words.items(), key=lambda x: x[1], reverse=True)
            ]
          )


下面是输出结果的摘录：

    
    35:ACAP-crawler: *
    34:ACAP-disallow-crawl: /public/search/
    32:ACAP-disallow-crawl: /article_email/*
    11:Clean-param: filter&ref&sq&sqc&sqm&sst&s&id&pm&do&source&method&size&query&sorting
    [...]
    12:<!-- WP Super Cache is installed but broken. The constant WPCACHEHOME must be set in the file wp-config.php and point at the WP Super Cache plugin directory. -->
    1:/* CUSTOMIZATIONS */
    [...]
    8:Diasllow: authcallback.aspx
    1:Disalllow: /search.php
    1:Disalow: /dnd/
    1:Dissalow: /catalog/product/gallery/


有多个发现。首先，非标准指令的使用（比如，ACAP-*）。其次，某些 HTML 和 CSS [注释](http://www.labazhou.net/2014/08/the-power-of-query-comments/)也出现了（robots.txt 注释以 # 打头）。最后，我们注意到大量拼写错误的 Disallow，和其它的指令名字。当放宽那些额外的拼写来抽出 Disallow 指令时，这就显示出用处了。

我觉得有意思的、意料之外的一条指令是，来自于 www.hanoverian.co.nz 网站混用了 Apache 配置：

    
    User-agent: Googlebot
    Disallow: /*.gif$
    
    User-agent: Googlebot
    Disallow: /*.jpg$
    
    RewriteEngine on
    #Options +FollowSymlinks




### 注释


修改上面的脚本，我们再看看下面的注释：

    
    241:# block against duplicate content
    241:# block MSIE from abusing cache request
    [...]
    26:#Disallow: /video/index.jsp*
    [...]
    3:#  --> fuck off.  
    2:# dotbot is wreckless.
    2:# KSCrawler - we don't need help from you
    1:# Huge pig crawlers are eating bandwidth


我们观察到一些注释是正常的。它们貌似来自一个模板或拷贝粘贴。一些指令也被注释掉了。当抽出 Disallow 指令时，我们将重新使用它。最后，古老的网怒症爆发了。


### 隐藏模式


在我最初抽出 `Disallow` 指令时，我抽出了路径的第一部分，并做了累加，看看这样的路径被找到多少次。虽然这个列表看起来符合我的预期，但是第一条引起了我的注意：

    
    9995:plenum
    4603:search
    4038:user
    3398:wp-admin
    3135:en
    2774:admin


其它条目看起来肯定熟悉，然而我还没有听过哪个应用程序或服务器子路径中有“plenum”。查询我们的 hosts.txt 集合：

    
    hosts >>> history.responded().filter(lambda x: "plenum" in x.response.content)
    {200:1 | www.knesset.gov.il}


只有一个命中，它是[以色列国会](http://en.wikipedia.org/wiki/Knesset)网站。为什么这个网站有这么多的 Disallow 指令呢？下面是它们的 robots.txt 摘录：

    
    User-agent: *
    Disallow: /plenum/data/5510903.doc
    Disallow: /plenum/data/5697203.doc
    Disallow: /plenum/data/07822203.doc
    Disallow: /plenum/data/07822803.doc
    Disallow: /plenum/data/7111903.doc
    Disallow: /plenum/data/7714403.doc
    Disallow: /plenum/data/7714903.doc
    Disallow: /plenum/data/7715303.doc
    Disallow: /plenum/data/7118203.doc
    Disallow: /plenum/data/7118303.doc


大约 10,000 份这样的文档明确要求不要被索引。当然，这肯定有着某种厉害关系。这些文档大部分仍然可以在线访问。使用 Google 翻译服务，我们或许找到了会议记录。我这里就不引用这些文档了，不过你可以去看看。

按照同样思维，如果一个习惯在明确阻止访问某些文档上犯了错误，那么一定有其它习惯也会犯错误。另一个查询根据类似的模式被运行了，看看发生了什么。我关注于至少包含一位数字（引用次数？）的所有 Disallow 指令，并按照出现次数排序：

    
    27016:['www.yourdictionary.com']
    12651:['download.oracle.com', 'docs.oracle.com']
    9995:['www.knesset.gov.il']
    9381:['state.gov']


忽略前两条，重点看第四条。恩，state.gov 有着类似的 robots.txt。

    
    User-agent: *
    Disallow: /www/
    Disallow: /waterfall/
    [...]
    Disallow: organization/193959.pdf
    Disallow: organization/193960.pdf
    Disallow: organization/193543.pdf
    Disallow: organization/193546.pdf
    Disallow: organization/193567.pdf
    Disallow: organization/193719.pdf
    Disallow: organization/193723.pdf
    Disallow: organization/193738.pdf
    Disallow: organization/193775.pdf
    Disallow: organization/193779.pdf
    Disallow: organization/193791.pdf


刚才的一幕又发生了，大约 9,000 个文档明确要求不要被索引。然而这一次，它们不能再从服务器上找到了。幸运的是，互联网从来不会忘掉。

[![web 历史博物馆截图](http://www.labazhou.net/wp-content/uploads/2015/05/robots_txt_1.png)](http://www.labazhou.net/wp-content/uploads/2015/05/robots_txt_1.png)

涉及的大部分文档已经被存档了。但是仔细看下时间线，虽然它们通常是在不同的日期添加的，但是所有文档都在同一个日期消失了，2013 年 4 月。Edward Snowden 当时所做的[某些工作](http://en.wikipedia.org/wiki/Global_surveillance_disclosures_%282013%E2%80%93present%29)，或许是这次大规模删除背后的原因。重申，我自己不会深入这些文档细节，但是你可以自便。

回到 robots.txt 列表里次数较多的条目，我们发现了 www.createspace.com。Create Space 是一家 Amazon 公司，它帮助不知名的作者出版他们的书：

    
    Disallow: /en/community/thread/12819
    Disallow: /en/community/message/91211
    Disallow: /en/community/message/92213
    Disallow: /en/community/message/92216
    Disallow: /en/community/message/92222


大约 100 条这样的信息对于网络爬虫是隐藏的。如果我们专门看它们的内容：

[![Create Space 的 message 截图](http://www.labazhou.net/wp-content/uploads/2015/05/robots_txt_2.png)](http://www.labazhou.net/wp-content/uploads/2015/05/robots_txt_2.png)

我不打算深入该讨论的细节，但请记住，Create Space 明确要求这些信息不要被查询。


### Disallow


现在，我们回头关注下最初目标，抽出每个路径的第一部分。每次匹配将被累加，一个文件算一次。这类似于[文件频率](http://en.wikipedia.org/wiki/Tf%E2%80%93idf#Inverse_document_frequency_2)【注5】。下面是前十个：

    
    5806:wp-admin
    5398:search
    3793:admin
    3206:includes
    2805:cgi-bin
    2663:modules
    2389:xmlrpc
    2384:scripts
    2333:user
    2153:cron


这份额外结果取决于在你的正则表达式和目标（比如仅抽出字典里的名字）里包含了哪些字符。


### 列表质量


同样的实验使用 Common Crawl 的另一个子集实现。抽出主机名之后，对其它子集的对比就完成了。这两份列表的相似度用 [Jaccard index](http://en.wikipedia.org/wiki/Jaccard_index)【注6】测量。系数值介于 0 和 1 之间，其中，1 代表高相似度（相同），0 代表不共享任何元素（不相交）。对于这两个主机名文件列表，0.27 的系数值被计算出来了。这是合理的，它们有着大量不同的网站，但是一些大型网址是共享的（正则表达式捕捉了所有被找到的 URL，包括响应内容中的 URL，而不仅仅只是被抓取的 URL）。

同样的相似度被测量了，这次是根据从这两个集合中抽出的 Disallow 词语清单。下面是结果图表：

[![Disallow词语分布图](http://www.labazhou.net/wp-content/uploads/2015/05/robots_txt_3-1024x787.png)](http://www.labazhou.net/wp-content/uploads/2015/05/robots_txt_3.png)

两份列表中的前 N 个词语根据 Jaccard index 被标示出来了。刚开始，前 100 个词语有着高相似度（~0.88）。随着子集规模的增大，相似度开始减少。三条竖线被标出来了，它们代表了第一个集合内的出现次数的门槛。当至少出现 10 次的一个词被找到时，两个列表仍然有着相对较高的相似度。


### 保留多少词？


根据上面的结果，只有一定数量的、排名靠前的词语被保留到了我们的最终列表。实际上，在能发送多少请求（时间、网络限制）和找到隐藏资源所得好处之间，有一个权衡。

个人看来，我宁愿在所有时间里运行差不多没有限制的列表，也不愿意错失一个资源（如果你的 SSH keys 可以访问到 ~huang 目录，那么我不想掠过它们）。


### 限制


下面是这次练习中值得注意的一些限制。首先，用到的算法根本没有优化。明显的改进是存在的，但是本文的目标是，这种实验需要的脚本少于一百行，主要复用了已有工具。

其次，被频繁访问的主机名取决于 Common Crawl 的抓取策略。既然基于开源项目 Nutch，那么已知的偏见就不要有了。我没有阅读 Nutch 的源代码来证实这个假设。

第三，一些不相关的重复或许出现了，它们人为地增强了某些词语的分数。这对于有着多个子域名的域名，是尤为正确的。在此，我只是基于最大的域名（*.blogspot.*，*.wordpress.com 等）实现了一份黑名单。

最后，只有 Disallow 指令被分析了。其它有用的信息或许产生于其它指令的聚合中。


### 结论


正如我们所见，robots.txt 的使用不是没有影响。在最简单的情况下，它将泄露受限制的路径和你的服务器所使用的技术。不过，经过进一步的调查，有人或许发现，一些内容不应该出现在那里。

从防卫者的角度看，两个常见谬误仍然存在。第一，robots.txt 或多或少扮演着访问控制的机制。第二，它们的内容只会被搜索引擎看到、而不会被人看到。我希望这篇文章向你展示了为什么这两点是错误的，以及这种假设可能产生什么影响。



* * *






	
  * 注1：Skipfish 是一种主动的 web 应用程序安全探测工具。[https://code.google.com/p/skipfish/w/list](https://code.google.com/p/skipfish/w/list)

	
  * 注2：主题爬虫，也称为聚焦爬虫，专业蜘蛛等，是垂直搜索引擎的核心和基础。[http://liuxinglanyue.iteye.com/blog/842873](http://liuxinglanyue.iteye.com/blog/842873)

	
  * 注3：The Web ARChive (WARC) archive format specifies a method for combining multiple digital resources into an aggregate archive file together with related information. [http://en.wikipedia.org/wiki/Web_ARChive](http://en.wikipedia.org/wiki/Web_ARChive)

	
  * 注4：顶级域（或顶级域名；英语：Top-level Domain；英文缩写：TLD）是互联网DNS等级之中的最高级的域，它保存于DNS根域的名字空间中。顶级域名是域名的最后一个部分，即是域名最后一点之后的字母，例如在example.com这个域名中，顶级域是.com（或.COM），大小写视为相同。[http://zh.wikipedia.org/wiki/%E9%A0%82%E7%B4%9A%E5%9F%9F](http://zh.wikipedia.org/wiki/%E9%A0%82%E7%B4%9A%E5%9F%9F)

	
  * 注5：逆向文件频率（inverse document frequency，IDF）是一个词语普遍重要性的度量。[http://zh.wikipedia.org/wiki/TF-IDF](http://zh.wikipedia.org/wiki/TF-IDF)

	
  * 注6：Jaccard index 是用来计算相似性，也就是距离的一种度量标准。 [http://baike.baidu.com/view/9604358.htm](http://baike.baidu.com/view/9604358.htm)


