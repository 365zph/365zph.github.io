---
author: viviworld
comments: true
date: 2014-12-27 14:15:00+00:00
layout: post
link: http://www.labazhou.net/2014/12/redirect-web-page/
slug: redirect-web-page
title: 怎样重定向网页
wordpress_id: 1466
categories:
- 编程
tags:
- Flask
- HTML
- https
- javascript
- nodejs
- php
- python
- ruby
- WordPress
- 代码
---

原文地址（source）：[http://css-tricks.com/redirect-web-page/](http://css-tricks.com/redirect-web-page/)

网页重定向是指，当网页访问某个特定的URL的时候，它变成了一个不同的URL。例如，一个人在浏览器里访问“website.com/page-a”，他们却被重定向到“website.com/page-b”。如果我们想把某个页面重定向到一个新的地址、修改网站的URL结构、移除URL中“www.”的部分、甚至把用户完全重定向到另一个网站（在此不一一列举），那么这是非常有用的。

假如我们想迁移网站，并关闭旧网站。然而，我们不想让旧网站上的所有网页都出现可怕的“404 Not Found”。这些旧链接就需要重定向到新网站上的同样内容。

举个例子：我们想让`old-website.com/blog/post`重定向到`new-website.com/blog/post`，所有其它的posts都是使用相同的URL格式。如果我们的重定向能反馈给搜索引擎，说这个变化是永久的，便于它们相应地更新索引，就太好了。

我们该怎么操作呢？在此之前，我们需要学习一点儿HTTP知识。


### HTTP响应码


每当我们输入一个URL或从浏览器发出请求时，我们都正在使用超文本传输协议（HTTP）。虽然它在科幻的警察电影里像是个非常酷的名字，但是，它实际上是我们请求服务器上CSS、HTML和图片之类的资源的过程。在我们发送请求之后，这些资源会给出响应，类似“嘿，我在这里，来了！”（响应码是 `HTTP 200 OK`）。有很多不同种类的HTTP响应码，最熟悉的可能是 `404 Not Found`；带有网页能够返回404状态，我们请求的任何其它资源也能返回404，无论它是一张图片，还是其它种类的资源。

每个HTTP响应都被归类为具体的三位数字，因此 `404 Not Found`是4XX数字，以澄清它是一个客户端错误，而200是2XX类别，表示某种成功信息。我们这里要谈的是3XX类别的HTTP响应，比如`301 Moved Permanently`或`302 Found`，因为它们是专为重定向而设的状态码。根据我们选择的方式，我们不必知道这些代码、但是对于其它响应码是必要的。

对于我们这种情况，我们将使用301重定向，因为一些web浏览器或代理服务器将缓存这种类型，让这些旧页面不能访问，在这个例子，恰恰是我们想要的。

那么我们在重定向到网页时，要具体怎么做呢？


### HTML重定向


或许最简单的重定向到另一个URL的方式就是使用Meta Refresh标签了。我们把这个meta标签放在HTML页顶部的``里：

    
    <meta http-equiv="refresh" content="0; URL='http://new-website.com'" />


content属性是在浏览器重定向到新网页之前的延迟，这里我们设为0秒。注意，我们无需设置HTTP状态码，但是重新检查上面引号的、奇怪的开始和结束（引号嵌套引号，因此它们需要不同的种类和匹配）。

虽然这种方法是重定向网页的最简单方法，但是它有一些缺点。根据W3C指出的，一些浏览器不能正常指出这种Meta refresh标签。在A页面载入、且没有重定向到页面B之前，用户可能看到了一个flash。它还使得低版本浏览器上的回退按钮失效。这不是理想的解决方法，它根本不被鼓励使用。

更加安全的选择可能是使用JavaScript重定向网站。


### JavaScript重定向


用JavaScript重定向到另一个URL相当简单，我们只需改变`window`对象的`location`的属性：

    
    window.location = "http://new-website.com";


虽然JavaScript有点儿奇怪，还是有很多方式来实现：

    
    window.location = "http://new-website.com";
    window.location.href = "http://new-website.com";
    window.location.assign("http://new-website.com");
    window.location.replace("http://new-website.com");


更不用提你只用`location`了，因为window对象是隐式的（implied）。否则就用`self`或`top`。

通过`location`对象，我们可以做很多优雅的工作，比如重新载入页面、改变URL的path和源。

存在一些问题：



	
  1. JavaScript需要被开启、下载并执行，才能起作用。

	
  2. 搜索引擎对此有何反应，尚不清楚。

	
  3. 没有涉及到状态码，因此你不能够利用重定向的信息。


我们需要的是服务器端解决方案，帮助我们向搜索引擎和浏览器发送301响应。


### Apache重定向


或许重定向网页的最常见方式是向Apache web服务器的'.htacess'添加特定规则。然后就可以让服务器来处理了。

'.htaccess'是个文档，让我们给运行在服务器上的软件Apache发送指令。为了把用户重定向到新网站，我们产生一个新的.htaccess文件（或编辑现有文件），将其添加到旧网站的根目录。添加的规则如下：

    
    Redirect 301 / http://www.new-website.com


访问旧网站任何页面的用户都将被重定向到新网站。如你看到的，我们把HTTP响应码放在了重定向规则的前面。

需要指出的是，这种方法只在支持`mod_rewrite`的Linux服务器上生效，mod_rewrite是一个Apache模块，通过检查具体的模式，来重定向被请求服务器上的URL，如果模式匹配了，它将以某种方式修改这个请求。大部分主机商默认支持它，不过如果有问题，最好和他们联系下。如果你想找更多关于mod_rewrite的信息，[这里是个不错的教程](http://code.tutsplus.com/tutorials/an-in-depth-guide-to-mod_rewrite-for-apache--net-6708)。在CSS-Tricks网站，还有很多关于[.htaccess的文章](http://css-tricks.com/snippets/htaccess/)。

回到刚才的例子，如果我们使用上面的代码，访问“old-website.com/blog/post”的用户将被发送到“new-website.com”，这不太友好，因为他们未能看到要找的页面。我们添加如下规则，确保将所有的博文重定向到正确的地址：

    
    RedirectMatch 301 /blog(.*) http://www.new-website.com$1


或者我们可能想重定向非常个别的页面。可以添加如下规则：

    
    Redirect 301 /page.html http://www.old-website/new-page.html


对于错误，我们能够把用户重定向到我们的404页面（可能塞满了双关语和gif图）：

    
      RewriteEngine on
      RewriteCond %{REQUEST_FILENAME} !-f
      RewriteCond %{REQUEST_FILENAME} !-d
      RewriteRule .* 404.html [L]


首先我们检查mod_rewrite是否支持，然后开启，如果文件或目录没有被找到，我们就把404页面送到用户面前。这种方式比较优雅，他们看到的页面内容将来自于`404.html`文件，同时请求的URL保持不变。

如果你对于杂乱的'.htaccess'文件感到不舒服，而且安装了WordPress，那么[这个俏皮的扩展](https://wordpress.org/plugins/redirection/)为我们搞定一切。


### Nginx重定向


如果你的服务器用[Nginx](http://nginx.org/)做[web服务器](http://www.labazhou.net/2014/04/nweb/)，那么你可以在'nginx.conf'文件添加server块来处理这些重定向请求。

    
    server {
      listen 80;
      server_name old-website.com;
      return 301 $scheme://new-website.com$request_uri;
    }


我们又使用了301 HTTP响应，借助`scheme`变量，我们将根据原始网站使用的方式来请求`http://`或`https://`。为了更好地实践Nginx相关技术，最好多看看[HTML5 Boilerplate nginx.conf](https://github.com/h5bp/server-configs-nginx/blob/master/nginx.conf)。``


### Lighttpd重定向


对于运行着[Lighttpd](http://www.lighttpd.net/)的服务器来说，先导入`mod_redirect`模块，然后使用`url.redirect`：

    
    server.modules  = (
      "mod_redirect"
    )
    
    $HTTP["host"] =~ "^(www\.)?old-website.com$" {
      url.redirect = (
        "^/(.*)$" => "http://www.new-website.com/$1",
      )
    }




### PHP重定向


在PHP里，我们使用header函数，简单易懂：

    
       header('Location: http://www.new-website.com');   exit;


必须在任何标记或任何种类的内容之前设置好，尽管如此，还是有一个小小的不足。这个函数默认将发送302重定向响应，告诉每个人，被访问的内容只是临时被挪走了。考虑到我们的具体案例，我们需要永久地把文件迁移到新网站，因此我们将不得不用301重定向代替：

    
      header('Location: http://www.new-website.com/', true, 301);   exit();


可选的参数`true`将用一个相同类型的报文信息来取代前面一个相似的报文信息，后面的301将强制指定HTTP响应的值。


### Ruby on Rails重定向


[Rails项目](http://rubyonrails.org/)里，对于任何controller来说，我们借助`redirect_to`和 `:status`选项来设置 `:moved_permanently`。这样，我们就覆写了默认的302状态码，用Moved Permanently取代了：

    
    class WelcomeController < ApplicationController   def index     redirect_to 'http://new-website.com', :status => :moved_permanently 
      end
    end


在Rails 4里，有一种更容易的方式来处理这些请求，我们可以在routes.rb文件添加redirect，它将自动发送一个301响应:

    
    get "/blog" => redirect("http://new-website.com")


如果我们想把博客上的每篇文章重定向到新网站的文章上，可以用下面的代码来取代上面的：

    
    get "/blog/:post" => redirect("http://new-website.com/blog/%{post}")




### .NET 重定向


我以前从来没有用.NET框架写过任何东西，不过微软开发者网络上[有篇清晰的文档](http://msdn.microsoft.com/en-us/library/t9dwyts4(v=vs.110))。


### Node.js重定向


下面是非常快捷的本地设置，呈现了Node是怎样重定向的。首先，我们include http模块，创建新服务器，后面跟上`writeHead()`方法：

    
    var http = require("http");
    
    http.createServer(function(req, res) {
      res.writeHead(301,{Location: 'http://new-website.com'});
      res.end();
    }).listen(8888);


如果你创建了名叫index.js新文件，把上面的代码粘贴进去，在命令行运行 `node index.js`，你将发现网站的本地版本重定向到了new-website.com。但是为了重定向/blog下的所有文章，我们需要借助Node方便的url模块，从请求中解析URL：

    
    var http = require("http");
    var url = require("url");
    
    http.createServer(function(req, res) {
      var pathname = url.parse(req.url).pathname;
      res.writeHead(301,{Location: 'http://new-website.com/' + pathname});
      res.end();
    }).listen(8888);


使用`res.writeHead()`方法，我们能够把请求中的pathname附加到URL字符串的后面。它就可以重定向到新网站的相同路径了。为JavaScript欢呼！


### Flask重定向


有了基于[Python](https://www.python.org/)的[Flask](http://flask.pocoo.org/)框架，我们可以简单地创建路由，用redirect函数指向子页面，而301必须在末尾传进来，因为默认被设置成了302：

    
    @app.route('/notes/')
    def thing(page):
      return redirect("http://www.new-website.com/blog/" + page, code=301)


如果你知道重定向到一个网页的其它技巧，请添加到下面的评论里，我将后续更新。
