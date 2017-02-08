---
author: viviworld
comments: true
date: 2015-06-05 00:38:00+00:00
excerpt: 在创建新表和数据仓库时，要做很多决定。一些在当时似乎无关紧要的地方，却让你和用户在数据库的生命期内感到痛苦。我们和成千上万的人们以及他们的数据库一道工作，经历了长期的读写查询，我们差不多看到了每种情况。下面是创建免去痛苦模式的
  10 条规则。
layout: post
link: http://www.labazhou.net/2015/06/10-rules-for-a-better-sql-schema/
slug: 10-rules-for-a-better-sql-schema
title: 更好的 SQL 模式的 10 条规则
wordpress_id: 2130
categories:
- 编程
tags:
- json
- SQL
- SSOT
- utc
- uuid
- 数据库
---


	
  * 原文地址（original source）：[https://www.periscope.io/blog/better-sql-schema.html](https://www.periscope.io/blog/better-sql-schema.html)

	
  * 作者（author）：[https://twitter.com/PeriscopeData](https://twitter.com/PeriscopeData)





* * *



在创建新表和数据仓库时，要做很多决定。一些在当时似乎无关紧要的地方，却让你和用户在数据库的生命期内感到痛苦。

我们和成千上万的人们以及他们的数据库一道工作，经历了长期的读写查询，我们差不多看到了每种情况。下面是创建免去痛苦模式的 10 条规则。


### 1.只使用小写字母、数字和下划线


不要在数据库、模式、表或列名中使用点（dot）、空格、或连接号【注1】。点用于标示对象，通常以 `database.schema.table.column` 的方式。

对象名称中包含点将引起混淆。类似地，在对象名字里使用空格将迫使你在查询语句中添加不必要的引号：

    
    select "user name" from events
    
    -- vs
    
    select user_name from events


如果在表或列名里有大写字母，查询语句将难以书写。如果所有字母都是小写的，人们将不必记住 `users` 表是 `Users` 还是 `users`。

当你最终修改数据库或把你的表复制到仓库时，你不需要记住哪个表是大小写敏感的。


### 2.使用简单的、自说明的列名


如果 `users` 表需要 `packages` 表的外键，就把键命名为 package_id。避免使用简短、晦涩的名字，比如 `pkg_fk`；其他人不知道它代表什么。自说明的名字让其他人更容易理解模式，随着团队规模的增加，这对于维护效率至关重要。

不要为[多态的数据](http://en.wikipedia.org/wiki/Polymorphism_%28computer_science%29)使用有歧义的名字。如果你发现自己创建了形如 `item_type` 或 `item_value` 的列，那么你最好使用带有具体名字的、更多的列，比如 `photo_count`、`view_cout`、`transaction_price`。

这样，列的内容就可以常从模式中获悉，而不用依赖于当前行的其它值。

    
    select sum(item_value) as photo_count
    from items
    where item_type = 'Photo Count'
    
    -- vs
    
    select sum(photo_count) from items


不要把包含表的名字做为列名的前缀。通常，让用户表包含形如 `user_birthday`、`user_created_at`、`user_name` 的列，没有多少帮助。

避免使用 `column`、`tag` 和 `user` 之类的保留字做为列名。你将不得不在查询中使用额外的引号，不这么做将让你对错误信息感到困惑。如果保留字出现在列名应该出现的地方，数据库会极大地错误理解查询。


### 3.使用简单的、自说明的表名


如果表名由多个单词组成，就使用下划线隔开这些单词。`package_deliveries` 要比 `packagedeliveries` 更容易阅读。

如有可能，使用一个单词而不是两个单词：`deliveries` 更易于读。

    
    select * from packagedeliveries
    
    -- vs
    
    select * from deliveries


不要给表加前缀来暗示模式。如果你需要把表分组为范围，就把这些表放入一个模式。`store_items`、`store_transactions`、`store_coupons` 之类的表名，和加了前缀的列名一样，通常不值得额外敲键盘。

我们推荐表名使用复数（例如 `packages`），连接表（join table）名字的两个单词都用复数（例如 `packages_users`）。单数的表名更有可能偶尔与保留字相撞，并且在查询语句中通常有着较低的可读性。


### 4.主键为整数


即使你在用 UUID，它也没有意义（比如对于连接表来说），添加标准的 `id` 列、自增整数序列。这种 key 使得某些查询更加容易，比如[仅仅选取一组数据的第一行](https://www.periscope.io/blog/4-ways-to-join-only-the-first-row-in-sql.html)。

如果导入的任务需要复制数据，这种 key 将成为救命稻草，因为你能够删除特定行：

    
    delete from my_table
    where id in (select ...) as duplicated_ids


避免多列主键。它们在尽量编写有效查询时难以推断，且难以修改。要使用整数主键、多列 unique 约束、一些单列索引代替。


### 5.与外键保持一致


有很多关于主键和外键的命名风格。我们推荐，最受欢迎的是，任何表 `foo`，都要拥有一个名叫 `id` 的主键，所有的主键命名为 `foo_id`。

另一种受欢迎的风格使用全局唯一键名，表 `foo` 有个名叫 `foo_id` 的主键，所有外键也叫 `foo_id`。如果你使用缩写（`users` 表的主键用 `uid`），会引起混淆或命名冲突，故不要缩写。

无论你选择什么风格，就保持下去。不要在有的地方使用 `uid`，在另外地方使用 `user_id` 或 `users_fk`。

    
    select *
    from packages
      join users on users.user_id = packages.uid
    
    -- vs
    
    select *
    from packages
      join users on users.id = packages.user_id
    
    -- or
    
    select *
    from packages
      join users using (user_id)


还要留意不能明显匹配表的外键。名叫 `owner_id` 的列名或许是 `users` 表的外键，或许不是。把列名取为 `user_id`，如有必要，取为 `owner_user_id`。


### 6.把时间存储为 Datetime


不要把日期保持为 Unix 时间戳或字符串：而是把它们转化为 datetime。虽然 SQL 的 date 数学函数不是最好的，但是你自己处理时间戳甚至更难。使用 SQL date 函数要求每次查询都把时间戳转化为 datetime：

    
    select date(from_unixtime(created_at))
    from packages
    
    -- vs
    
    select date(created_at)
    from packages


不要在单独的列里存储年、月、日。这使得每一条时间序列【注2】查询非常难以编写，将阻碍大多数刚入门的 SQL 用户使用表格中的日期信息。

    
    select date(created_year || '-' 
      || created_month || '-' 
      || created_day)
    
    -- vs
    
    select date(created_at)




### 7.UTC，一直都是 UTC


使用某种时区而非 [UTC](http://en.wikipedia.org/wiki/Coordinated_Universal_Time) 将引起永无止境的问题。[优秀的工具](http://www.labazhou.net/2015/02/principles-of-an-ideal-database-client/)（包括 [Periscope](https://www.periscope.io/?src=p63_0)）具备所有你需要的、将数据从 UTC 转换成当前时区的功能。在 Periscope 里，添加 `:pst` 就轻松地将 UTC 转换成 Pacific Time：

    
    select [created_at:pst], email_address
    from users


数据库的时区应该是 UTC，所有的 datetime 列应该是去除了时区的类型（没有时区的时间戳）。

如果你的数据库的时区不是 UTC，或者你的数据库既有 UTC、又有非 UTC 的 datetime，那么时间序列的分析难度将大为增加。


### 8.单一的真实数据来源


对于一条数据，应该有且只有一个真实来源【注3】。视图和汇总应该打上标签。这样，数据的使用人员将明白，在他们使用的数据和真实数据之间存在差异。

    
    select *
    from daily_usage_rollup


留下废弃的 `user_id`、`user_id_old`、`user_id_v2` 之类的列，将变成混淆的、永无止境的源头。在日常维护中，要确信 drop 掉了已被抛弃的表、和弃用的列。


### 9.更喜欢没有 JSON 列的表


你肯定不想要非常宽的表。如果有很多列，且它们有的按顺序命名（比如 `answer1`、`answer2`、`answer3`），今后你就会痛苦。

把这种表拆分成没有重复列的模式，这种模式的形态将特别容易查询。例如，获取 `survey` 表的、完成的答案的数目：

    
    select
      sum(
        (case when answer1 is not null
          then 1 else 0 end) +
        (case when answer2 is not null
          then 1 else 0 end) +
        (case when answer3 is not null
          then 1 else 0 end)
      ) as num_answers
    from surveys
    where id = 123
    
    -- vs
    
    select count(response)
    from answers
    where survey_id = 123


对于分析查询，从 JSON 列提取数据，能够极大地降低查询效率。虽然在生产环境有很多理由使用 JSON 列，但那不是针对分析的。强势地把 JSON 列转换为更简单的数据类型，让分析更加容易、更加快捷。


### 10.不要过度规范化


日期、邮编和国家，不需要让它们自己的表带有主键查询。如果你带了，每次查询将包含有少量的相同连接。这会给数据库创建大量重复的 SQL，以及大量额外工作。

    
    select
      dates.d,
      count(1)
    from users
      join dates on users.created_date_id = dates.id
    group by 1
    
    -- vs
    
    select
      date(created_at),
      count(1)
    from users
    group by 1


表是有着它们大量自己的数据的第一类对象。其它数据都应该是更加重要的对象上的、另外的列。


### 期待更好的模式！


有了这些规则武装，你的下一个表或仓库对于你和新团队成员而言，在队伍壮大时，将更易于查询。如果你不同意或有更多的规则方面的建议，请邮件周知我们 [hello@periscope.io](mailto:hello@periscope.io)。我们乐于听到你的声音！



* * *






	
  * 注1：连接号（－，〜），表示连接、起止、流程的符号。“两个相关的名词构成一个意义单位，中间用连接号。”、“相关的时间、地点或数目之间用连接号，表示起止。”、“相关的字母、阿拉伯数字等之间，用连接号，表示产品型号。”、“几个相关的项目表示递进式发展，中间用连接号。”[http://zh.wikipedia.org/wiki/%E8%BF%9E%E6%8E%A5%E5%8F%B7](http://zh.wikipedia.org/wiki/%E8%BF%9E%E6%8E%A5%E5%8F%B7) 请注意：连接号和连字号是不同的：[http://zh.wikipedia.org/wiki/%E8%BF%9E%E5%AD%97%E5%8F%B7](http://zh.wikipedia.org/wiki/%E8%BF%9E%E5%AD%97%E5%8F%B7)

	
  * 注2：时间序列是用时间排序的一组随机变量，国内生产毛额（GDP）、消费者物价指数（CPI）、台湾加权股价指数、利率、汇率等等都是时间序列。
时间序列的时间间隔可以是分秒（如高频金融数据），可以是日、周、月、季度、年、甚至更大的时间单位。[http://zh.wikipedia.org/wiki/%E6%99%82%E9%96%93%E5%BA%8F%E5%88%97_(%E7%B6%93%E6%BF%9F%E5%AD%B8)](http://zh.wikipedia.org/wiki/%E6%99%82%E9%96%93%E5%BA%8F%E5%88%97_(%E7%B6%93%E6%BF%9F%E5%AD%B8))

	
  * 注3：In Information Systems design and theory Single Source Of Truth (SSOT) refers to the practice of structuring information models and associated schemata such that every data element is stored exactly once (e.g., in no more than a single row of a single table). [http://en.wikipedia.org/wiki/Single_Source_of_Truth](http://en.wikipedia.org/wiki/Single_Source_of_Truth)


