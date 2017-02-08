---
author: viviworld
comments: true
date: 2015-08-31 00:32:28+00:00
excerpt: 本文我们浏览了涵盖 CRUD 四个基本的数据库功能：比如：`CREATE TABLE`， `INSERT INTO`， `SELECT`， `UPDATE`，
  `DELETE` 和 `DROP`。当 SQL 开发人员新手在开始数据库工作、以及使用一门新语言 SQL 时，本文中的基本知识应该能为他们开个好头。
layout: post
link: http://www.labazhou.net/2015/08/beginners-guide-to-sql/
slug: beginners-guide-to-sql
title: SQL 新手指南
wordpress_id: 2424
categories:
- 编程
tags:
- CRUD
- GUI
- SQL
- 数据库
---


	
  * 原文地址（original source）：[https://blog.udemy.com/beginners-guide-to-sql/](https://blog.udemy.com/beginners-guide-to-sql/)





* * *



_注：在我们推出的免费文本教程中，有一些最受欢迎的主题，本文是某系列「入门」的一部分。_

为了跳到某些章节，请参考下面的目录表：



	
  * 介绍

	
  * 数据库的介绍

	
  * 四种基本的 SQL 操作（CRUD）

	
    * 创建数据

	
    * 读取数据

	
    * 更新数据

	
    * 删除数据




	
  * 结论




### 介绍


[SQL](https://en.wikipedia.org/wiki/SQL) 已经应用到了我们周围的各个角落，不管你信不信。操纵任何种类数据的每个应用程序都需要将数据存放在某处。无论它是[大数据](https://en.wikipedia.org/wiki/Big_data)，还是只有简单数行的数据包；无论是政府、还是创业公司；无论是横跨多台服务器的大型数据库、还是运行着自己小型数据库的手机，SQL 无处不在。

但是，SQL 是什么呢？SQL 代表结构化查询语言，通常，其发音为“ess-que-el”。SQL 是数据库语言，专门为了和数据库通信而建立的。SQL 是一门简单的语言，和英语语言类似，因为命令和英语句子有着类似的结构。那些句子组织为声明式的语句，这样 SQL 也被叫做声明式语言【注1】。

[![SQL 的新手指南](http://www.labazhou.net/wp-content/uploads/2015/08/image02-600x600.jpg)](http://www.labazhou.net/wp-content/uploads/2015/08/image02.jpg)

在可视化地编写 SQL 查询语句方面，已经有很多可用的工具了，为什么还要学习一个全新的语言呢？当你用某些 SQL 工具时，[重要的是理解 SQL 语言](http://www.labazhou.net/2015/06/10-rules-for-a-better-sql-schema/)、理解可视化工具正在做什么、以及为什么那样做。有时候，需要手动写一些 SQL 语句，不仅因为这是最快的方法，而且这更强大、经常是完成预定目标的唯一方法。


### 数据库的介绍


我们刚才提到了，SQL 是数据库语言。那么，数据库是什么？数据库是一种存储机制，被设计为用来访问存储的信息及其操作。数据库里的信息被存储在称作表（table）的对象里。表的名字是其唯一身份，由列和行构成。列包含列名、列的数据类型以及该列的其它属性。行包含该列的记录或数据。数据库里的大部分表之间会有关系（relationship）或连接（link），一对一、或一对多的关系。这也是为什么这种数据库被称作关系模型数据库。

关于描述数据库结构，最容易的方法就是把它和 Excel 电子表格做比较，它们有着诸多相似。一个数据库就是一份独立的文件。电子表格里的 sheet 就是表（table），每个 sheet 有一个名字。列和行，都和数据库一样。SQL 语言用来创建新表、更改现有表，用来获取数据、更新数据或删除数据。

比如说，我们有一份知名电影的台词大集合，存放在任意单独的文本文件里。即使我们精心组织，用 Excel 电子表格存放，我们所面临的问题仍然是存在。用这种方式存储台词，我们无法快速地从一部电影里得到所有台词，或无法得到一个角色的所有台词。如果我们把文本文件或电子表格放入数据库，并创建带有关系的表，所有问题就迎刃而解了。关系型的真正涵义是什么？关系模型【注2】是描述数据、以及这些数据实体之间的关系的方法。在我们的例子中，关系就是每个台词和表之间的联系，电影名称存放在表里、或所有角色也存放在表里。

下面是一个简化处理的例子，只有一个表做示例，表名叫「Movie_quotes」。它有四列，一个列表示台词文本、一个列表示说台词的演员角色，一个表示电影，还有年份。我们收录了八句电影台词，我们的示例表看起来像是这个样子：
<table width="100%" style="height: auto;" class=" aligncenter" >
<tbody >
<tr >

<td colspan="4" style="text-align: center;" >**Movie_quotes**
</td>
</tr>
<tr >

<td style="text-align: center;" >**Q_TEXT**
</td>

<td style="text-align: center;" >**Q_CHARACTER**
</td>

<td style="text-align: center;" >**Q_MOVIE**
</td>

<td style="text-align: center;" >**Q_YEAR**
</td>
</tr>
<tr >

<td >I’ll be back
</td>

<td >The Terminator
</td>

<td >The Terminator
</td>

<td style="text-align: center;" >1984
</td>
</tr>
<tr >

<td >I find your lack of faith disturbing.
</td>

<td >Darth Vader
</td>

<td >Star Wars
</td>

<td style="text-align: center;" >1977
</td>
</tr>
<tr >

<td >It’s a trap!
</td>

<td >Admiral Ackbar
</td>

<td >Star Wars
</td>

<td style="text-align: center;" >1983
</td>
</tr>
<tr >

<td >Never tell me the odds.
</td>

<td >Han Solo
</td>

<td >Star Wars
</td>

<td style="text-align: center;" >1980
</td>
</tr>
<tr >

<td >Do. Or do not. There is no try.
</td>

<td >Yoda
</td>

<td >Star Wars
</td>

<td style="text-align: center;" >1980
</td>
</tr>
<tr >

<td >Stupid is as stupid does.
</td>

<td >Forrest Gump
</td>

<td >Forrest Gump
</td>

<td style="text-align: center;" >1994
</td>
</tr>
<tr >

<td >My mama always said: Life was like a box of chocolates.

You never know what you’re gonna get.
</td>

<td >Forrest Gump
</td>

<td >Forrest Gump
</td>

<td style="text-align: center;" >1994
</td>
</tr>
<tr >

<td >Run, Forrest! Run!
</td>

<td >Jenny Curran
</td>

<td >Forrest Gump
</td>

<td style="text-align: center;" >1994
</td>
</tr>
</tbody>
</table>
当讨论数据库时，值得一提的是，有一种全新的数据库，在需要存储数据的人们中间，产生了一种运动，它就是 NoSQL。它们是基于文档的系统，虽然它们正在变得非常流行，直到今天仍然有大量的关系型数据库在使用中。即使 NoSQL 数据库有某种查询语言，它们很大一部分（因为它们几乎都是在 SQL 之后才发明的）仍然和 SQL 有着某种相似性。


### 四种基本的 SQL 操作（CRUD）


有很多 SQL 命令，但是，有四种通常的 SQL 操作，可以对表及其数据做一些事情：



	
  * 创建 - 把数据填充到表里。

	
  * 读取 - 从表中查询数据。

	
  * 更新 - 修改表中已有数据。

	
  * 删除 - 从表中移除数据。


这些基本 SQL 操作的首字母组成了缩写「CRUD」，它们被视作每个数据库必有的、四个基本功能或特色的基础集。

通过介绍基本特色，我们将会介绍基本的、以及最重要的 SQL 命令：`**CREATE**`, `**INSERT**`, `**SELECT**`, `**UPDATE**`, `**DELETE**`, and `**DROP**`。


#### 创建数据


首先，我们需要在数据库里创建表。创建新表，就用到了 `CREATE TABLE`。`CREATE TABLE` 语句的简单语法格式如下：

    
    CREATE TABLE table_name
    (column_1 data_type,
    column_2 data_type,
    column_3 data_type);


首先，`CREATE TABLE`关键词后面跟着表名。这是一个极好的例子，说明了 SQL 的简洁性、以及和英语的相似性。关键词后面跟着一个左圆括号，这里定义了额外的参数：列名和列的数据类型，然后跟上右圆括号。必须要提的是，所有的 SQL 语句应该以 `;` 结尾。

需要遵守的规则并不多。表名和列名必须以字母打头，后面可以跟上字母、数字、或下划线。它们的字符长度不能超过 30 个。用 SQL 保留字做为表名或列名（比如 `select`, `create`, `insert` 等）是被禁止的。

在例子中，最简单的列名可能是 `TEXT`， `CHARACTER`， `MOVIE`，和 `YEAR`。但是，问题在于这些列名都是保留字。为了避免任何可能的冲突，我们将创建以 `Q_` 做为前缀的列名。

数据类型因不同的数据库而不同，不过这里使用了最常见的类型：



	
  * `char(size)` – 固定长度字符串，用括号中的参数标明。

	
  * `varchar(size)` – 可变长度字符串，用括号中的参数标明。

	
  * `number(size)` – 数字值，括号中的参数标明了总长度。

	
  * `date` – 日期值。

	
  * `number(size, d)` – 数字值，总长度为 `size`，小数位用 `d` 表示。


数据类型规定了哪种类型的数据可以存储在指定的列里。如果 `Q_CHARACTER` 的列用于存储电影名字，那么这个指定的列就应该有一个 `varchar` （可变长度字符）的数据类型。存放电影年份的列的类型是 `number`，我们的例子中相应的列是 `Q_YEAR`。

对于期望的表结构，创建表的最终 SQL 命令如下：

    
    CREATE TABLE Movie_quotes
    (‘Q_TEXT’ varchar(200),
    ‘Q_CHARACTER’ varchar(20),
    ‘Q_MOVIE’ varchar(20),
    ‘Q_YEAR’ number(4));


这个 SQL 命令的结果将创建一个空表，各列情况如下：



	
  * `Q_TEXT` 可以接受 200 个字符长度的字符串。

	
  * `Q_CHARACTER` 可以接受 20 个字符长度的字符串。

	
  * `Q_MOVIE` 可以接受 20 个字符长度的字符串。

	
  * `Q_YEAR` 可以接受一个年份的四个数字。


[![表结构](http://www.labazhou.net/wp-content/uploads/2015/08/image03-600x600.jpg)](http://www.labazhou.net/wp-content/uploads/2015/08/image03.jpg)

接下来，用我们的电影台词数据填充这张表。有很多可用的 GUI 工具，来管理数据库中的表和数据。不过，写一个 SQL 脚本常常更快，该脚本基本上是 SQL 命令的集合，将被顺序执行。当你需要用大量数据填充表时，这种方式尤为方便。

向表插入或添加一行数据的 SQL 命令是 `INSERT`。格式如下：

    
    INSERT INTO table_name
    (column_1, column_2, ... column_n)
    VALUES (value_1, value_2, ... value_n);


为了向表插入一行数据， `INSERT` 关键字跟着 `INTO` 关键字和表名。然后是列名，放在圆括号里，用逗号隔开，这是可选的，但是，指明要插入的列，以确保正确的数据插入相应的列，这是一种良好实践。最后一部分，用 `VALUES` 关键字定义了要插入的那些数据，数据列表以圆括号结束。请注意，字符串应该放在单引号里，数字不应如此。

用来填充例子中 `Movie_quotes` 表的 SQL 脚本，如下：

    
    INSERT INTO Movie_quotes
    (Q_TEXT, Q_CHARACTER, Q_MOVIE, Q_YEAR)
    VALUES ('I’ll be back', 'The Terminator', 'The Terminator', 1984);
    INSERT INTO Movie_quotes
    (Q_TEXT, Q_CHARACTER, Q_MOVIE, Q_YEAR)
    VALUES ('I find your lack of faith disturbing.', 'Darth Vader', 'Star Wars', 1977);
    INSERT INTO Movie_quotes
    (Q_TEXT, Q_CHARACTER, Q_MOVIE, Q_YEAR)
    VALUES ('It’s a trap!', 'Admiral Ackbar', 'Star Wars', 1983);
    INSERT INTO Movie_quotes
    (Q_TEXT, Q_CHARACTER, Q_MOVIE, Q_YEAR)
    VALUES ('Never tell me the odds.', 'Han Solo', 'Star Wars', 1980);
    INSERT INTO Movie_quotes
    (Q_TEXT, Q_CHARACTER, Q_MOVIE, Q_YEAR)
    VALUES ('Do. Or do not. There is no try.', 'Yoda', 'Star Wars', 1980);
    INSERT INTO Movie_quotes
    (Q_TEXT, Q_CHARACTER, Q_MOVIE, Q_YEAR)
    VALUES ('Stupid is as stupid does.', 'Forrest Gump', 'Forrest Gump', 1994);
    INSERT INTO Movie_quotes
    (Q_TEXT, Q_CHARACTER, Q_MOVIE, Q_YEAR)
    VALUES ('My mama always said: Life was like a box of chocolates. You never know what you’re gonna get.', 'Forrest Gump', 'Forrest Gump', 1994);
    INSERT INTO Movie_quotes
    (Q_TEXT, Q_CHARACTER, Q_MOVIE, Q_YEAR)
    VALUES ('Run, Forrest! Run!', 'Jenny Curran', 'Forrest Gump', 1994);




#### 读取数据


数据库中有了存好的数据，现在我们可以查询数据，看看我们的表里存储了什么，我们还能用不同的方式过滤和分类数据。

`SELECT` 语句用于查询、或选择我们想从数据库中返回的数据。我们从非常简单的查询开始，但是 `SELECT` 有很多不同的选项和扩展，这为我们最终的需要提供了很大的灵活性。基本的 `SELECT` 语句的语法如下：

    
    SELECT column_1, column_1, ... column_n
    FROM table_name;


指出列名，决定了哪一列将被返回到结果里，以及按什么顺序。如果我们想选择所有的列，或我们不知道表中的确切列名，我们可以使用通配符 `*`，它将从数据库中选择所有列：

    
    SELECT * FROM table_name;


对于本例，显示所有数据的查询，如下：

    
    SELECT * FROM Movie_quotes;


[![数据表的数据展示](http://www.labazhou.net/wp-content/uploads/2015/08/image07-600x600.jpg)](http://www.labazhou.net/wp-content/uploads/2015/08/image07.jpg)

仅仅显示电影台词、年份的查询，如下：

    
    SELECT Q_TEXT, Q_YEAR FROM Movie_quotes;


有时候我们不想从表中返回所有数据。当表中有大量数据、或我们在搜索匹配某些标准的特定数据时，就属于这种情况。对此，我们可以使用 `WHERE` 语句。`WHERE` 语句将过滤记录，限制从数据库中获取哪些记录、以满足具体定义的标准：

    
    SELECT column_1, column_1, ... column_n
    FROM table_name
    WHERE column_name operator value;


注意，`WHERE` 语句是可选的，但是如果我们决定用到它，下面的操作符是可用的：



	
  * `=` – 等于。

	
  * `>` – 大于。

	
  * `<` – 小于。

	
  * `>=` – 大于或等于。

	
  * `<=` – 小于或等于。

	
  * `<>` – 不等于。

	
  * `BETWEEN` – 在两个值之间。

	
  * `LIKE` – 搜索一种模式。

	
  * `IN` – 针对一个列的多种可能值。


数学操作符无需解释了。`BETWEEN` 操作符搜索两个声明值的、中间的值，包括等于两端的情况。`LIKE` 模式匹配操作符是非常强大的操作符，支持选择和我们的规定类似的行。百分号 `%` 被用做通配符，以匹配任何可能字符，它可出现在具体字符串的前面或后面。

例如，为了得到来自电影《Stars Wars》中的台词，我们可以这样写：

    
    SELECT * FROM Movie_quotes
    WHERE Q_MOVIE = ‘Star Wars’;


[![数据表 select 查询](http://www.labazhou.net/wp-content/uploads/2015/08/image04-600x600.jpg)](http://www.labazhou.net/wp-content/uploads/2015/08/image04.jpg)

请注意，`WHERE` 语句是大小写敏感的，下面的 SQL 语句将不会返回结果：

    
    SELECT * FROM Movie_quotes
    WHERE Q_MOVIE = ‘STAR WARS’;


除了 `WHERE` 子句，还可组合逻辑运算符 `AND` 和 `OR`。如果我们对相同列使用多个 `AND` 逻辑操作符，那么我们应该考虑使用 `IN` 子句替代。

做为示例，我们返回来自电影《Star Wars》和《The Terminator》中的所有电影台词：

    
    SELECT * FROM Movie_quotes
    WHERE Q_MOVIE = ‘Star Wars’ AND Q_MOVIE = ‘The Terminator’;


[![数据表 select 查询](http://www.labazhou.net/wp-content/uploads/2015/08/image00-600x600.jpg)](http://www.labazhou.net/wp-content/uploads/2015/08/image00.jpg)

就上面的例子，更好的写法就是使用 `IN` 语句替代：

    
    SELECT * FROM Movie_quotes
    WHERE Q_MOVIE IN (‘Star Wars’, ‘The Terminator’);


至此，我们一直在讨论如何从数据库中过滤数据。返回的行将按照它们进入（提交到）数据库的顺序进行排序。为了控制数据显示的顺序，我们可以通过包含 `ORDER BY` 子句来过滤输出数据。`ORDER BY` 子句包含了指定分类顺序的一个、或多个列名：

    
    SELECT column_1, column_1, ... column_n
    FROM table_name
    WHERE column_name operator value
    ORDER BY column_name;


为了扩展我们刚才《Star Wars》电影台词的例子，现在按照年份排序：

    
    SELECT * FROM Movie_quotes
    WHERE Q_MOVIE = ‘Star Wars’
    ORDER BY Q_YEAR;


[![select 表，排序](http://www.labazhou.net/wp-content/uploads/2015/08/image08-600x600.jpg)](http://www.labazhou.net/wp-content/uploads/2015/08/image08.jpg)

一个列的排序，默认是按照从最低值到最高值升序排列。为了把列的排序改为降序，我们可以在列名后面加上 `DESC` 关键字：

    
    SELECT * FROM Movie_quotes
    WHERE Q_MOVIE = ‘Star Wars’
    ORDER BY Q_YEAR DESC;


[![select 表，降序排列](http://www.labazhou.net/wp-content/uploads/2015/08/image051-600x600.jpg)](http://www.labazhou.net/wp-content/uploads/2015/08/image051.jpg)

`ORDER BY` 语句不限于单个列。你可以包含逗号分隔的、列的清单来排序。返回的行将根据第一个指定列，然后按顺序根据接下来指定的列排序。切记，用来排序的列不必包含在被选择列的清单里。我们可以像这样来写查询：

    
    SELECT Q_TEXT, Q_CHARACTER, Q_MOVIE FROM Movie_quotes
    WHERE Q_MOVIE = ‘Star Wars’
    ORDER BY Q_YEAR DESC;




#### 更新数据


在我们开始插入数据之后，并没有被限制为只能读取数据。我们能够对任何行里的、任何列下的、任何数据进行修改。`UPDATE` 语句用于更新或修改记录。

`UPDATE` 的语法如下：

    
    UPDATE table_name
    SET column_name = new_value
    WHERE column_name operator value;


当我们使用 `UPDATE` 时，慎重地构造一个 `WHERE` 子句是十分重要的。`WHERE` 子句指定了哪一条记录或哪些记录应该被更新。如果我们在执行 `UPDATE` 语句时、而没有使用 `WHERE` 子句，我们将更新指定列的所有数据。

让我们看看 `Movie_quotes` 表里的电影台词。我们让所有的台词以标点符号结束，《The Terminator》除外。对于如何使用 `UPDATE` 语句，这是一个极好的例子：

    
    UPDATE Movie_quotes
    SET Q_TEXT = ‘I’ll be back!’
    WHERE Q_MOVIE = ‘The Terminator’;


之前解释了，如果我们不小心遗漏了 `WHERE` 子句，或我们故意把所有的台词行更新为「I'll be back!」。通过单单选中电影《The terminator》所在行，我们就可以更新指定行的一列数据。


#### 删除数据


当数据库被大量使用时，从数据库中移除陈旧的数据，迟早会变得有必要。我们能够只删除表中的一些行、或删除整个表。

`DELETE` 语句用于删除表中的行。该命令的语法如下：

    
    DELETE FROM table_name
    WHERE column_name operator value;


重申，和 `UPDATE` 语句一样，`WHERE` 子句指定了哪一条记录或哪些记录应该被删除。如果没有指定 `WHERE` 子句，所有的行和列将被删除：

    
    DELETE FROM Movie_quotes;


假设我们不再喜欢电影《Forrest Gump》了，想从电影中删除其台词。为了从电影中删除所有台词，我们可以编写如下 SQL 命令：

    
    DELETE FROM Movie_quotes
    WHERE Q_MOVIE = ‘Forrest Gump’;


最终，我们有了足够多的电影。我们对电影台词不再感兴趣了，我们想把兴趣移到音乐上。我们开始收集歌词。根据我们目前所学到的 SQL 知识，修改数据库是非常简单的。

首先，我们需要清空数据库里、不再感兴趣的数据。为了删除包含所有行的表，我们可以使用 `DROP TABLE` 语句。切记 `DROP TABLE` 语句不同于使用 `DELETE` 语句，和删除表里的所有记录也不同。删除表里的所有记录，会留给我们表本身及其定义的所有表结构；包括列的数据类型定义和该表的其它相关的数据库信息。`DROP TABLE` 移除了表、移除表的定义，还有所有的行。

`DROP TABLE` 语句的语法如下：

    
    DROP TABLE table_name;


为了从数据库中删除 `Movie_quotes`，我们可以这样写：

    
    DROP TABLE Movie_quotes;


现在我们的数据库是空的，准备接受新数据。我们从所有的 CRUD 过程开始，创建名为 `Song_Lyrics` 的新表，根据我们新收藏的歌曲，建立一个歌词数据库。


### 结论


本文我们浏览了涵盖 CRUD 四个基本的数据库功能：如何创建新数据、读取数据、更新我们想要修改的数据、以及最后的如何删除不想要的数据。这包含了基本的、但是最重要的 SQL 命令，比如：`CREATE TABLE`， `INSERT INTO`， `SELECT`， `UPDATE`， `DELETE` 和 `DROP`。

这些基本的 SQL 命令支持大量的数据管理，但是每个介绍到的命令都有很多选项和额外的功能，有些是本文没有介绍的，要注意这一点。总之，当 SQL 开发人员新手在开始数据库工作、以及使用一门新语言 SQL 时，本文中的基本知识应该能为他们开个好头。



* * *






	
  * 注1：声明式编程（英语：Declarative programming）是一种编程范型，与命令式编程相对立。它描述目标的性质，让电脑明白目标，而非流程。声明式编程不用告诉电脑问题领域，从而避免随之而来的副作用。而指令式编程则需要用算法来明确的指出每一步该怎么做。声明式语言包括数据库查询语言（SQL，XQuery），正则表达式，逻辑编程，函数式编程和组态管理系统。[https://zh.wikipedia.org/wiki/%E5%AE%A3%E5%91%8A%E5%BC%8F%E7%B7%A8%E7%A8%8B](https://zh.wikipedia.org/wiki/%E5%AE%A3%E5%91%8A%E5%BC%8F%E7%B7%A8%E7%A8%8B)

	
  * 注2：用于数据库管理的关系模型（英语：Relational model）是基于谓词逻辑和集合论的一种数据模型，广泛被使用于数据库之中。最早于1969年由埃德加·科德提出。[https://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E6%A8%A1%E5%9E%8B](https://zh.wikipedia.org/wiki/%E5%85%B3%E7%B3%BB%E6%A8%A1%E5%9E%8B)


