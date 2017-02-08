---
author: viviworld
comments: true
date: 2014-11-10 06:05:56+00:00
layout: post
link: http://www.labazhou.net/2014/11/how-to-write-a-simple-interpreter-in-javascript/
slug: how-to-write-a-simple-interpreter-in-javascript
title: 如何用JavaScript编写简单的解释器
wordpress_id: 1299
categories:
- 编程
tags:
- CoffeeScript
- javascript
- 函数
- 汇编
- 编译器
- 解释器
---


	
  * 原文地址：[http://www.codeproject.com/Articles/345888/How-to-write-a-simple-interpreter-in-JavaScript](http://www.codeproject.com/Articles/345888/How-to-write-a-simple-interpreter-in-JavaScript)


[源码下载-2.9KB](http://www.codeproject.com/KB/scripting/345888/Calculator.zip)


### 编写解释器和编译器


编写解释器或编译器是编程方面最有教育意义的任务之一，因为你可以熟悉代码解释和求值过程。你可以更深入地掌握哪些任务在后台运行、以及语言设计背后的决定方面的见解。

本文向你展示如何为一种简单语言编写用于计算器应用程序的解释器，以呈现此过程的基本概观。

本文假设你具备了中级编程经验和基本熟悉JavaScript。


### 背景




#### 解释器、编译器和转换编译器的区别


本文，我们将创建解释器，而非编译器。我们的程序将要把一些代码做为输入，并立即计算。

如果我们在写编译器，我们将把源语言里的输入代码转换成某种较低级的目标语言的代码，比如MSIL，或汇编语言，甚至机器代码。

转换编译器除了源语言和目标语言都是同样等级的抽象之外，其它地方与编译器相似。在客户端的web编程世界里，标准例子就是[CoffeeScript](http://coffeescript.org/)，它转换编译为JavaScript。


#### 传统的语言代码解释过程


大多数编译器在多个步骤的过程中解释代码，涉及到[词法分析](http://zh.wikipedia.org/wiki/%E8%AF%8D%E6%B3%95%E5%88%86%E6%9E%90)、[预处理](http://zh.wikipedia.org/wiki/%E9%A2%84%E5%A4%84%E7%90%86%E5%99%A8)、[分析](http://zh.wikipedia.org/wiki/%E8%AA%9E%E6%B3%95%E5%88%86%E6%9E%90%E5%99%A8)、[优化](http://en.wikipedia.org/wiki/Program_optimization)和最终的[代码生成](http://en.wikipedia.org/wiki/Code_generation_(compiler))，或，解释器提到的计算。


##### 词法分析


词法分析器将字符串做为输入，然后输出token列表。比如，有如下代码：

    
    (12 + 4) / 6


词法分析器将把它分割成各个独立的部分，称作token，输出的列表形如：

    
    [
      ["operator", "("],
      ["number", 12],
      ["operator", "+"],
      ["number", 4],
      ["operator", ")"],
      ["operator", "/"],
      ["number", 6]
    ]


这个过程通常相对简单。稍有字符串操作经验的人都可以比较快速地用他们的方式建立词法分析器。


##### 分析


分析器把词法分析器产生的token列表做为输入，根据某种语法规则进行分析，并输出表现语法结构的分析树。

    
    {
      operation: "/",
      left: {
        operation: "+",
        left: 12,
        right: 4
      }
      right: 6
    }


这往往是这个过程中最难的部分。


##### 计算


求值器接收词法分析器产生的分析树，并计算。求值器通常递归遍历分析树。对于上面的语法树的例子，求值器可能首先计算高于"/"操作符优先级的、left操作数，然后是right操作数，然后返回"/"的结果。

对left操作数求值，语法树将简化为：

    
    {
      operation: "/",
      left: 16,
      right: 6
    }


计算出的最后结果：

    
    2.6666666666666665




### AEL：算术语言


在我们可以开始编写解释器之前，我们需要理解即将正在解释的语言，我只是假装、然后引出AEL，算术表达式语言（Arithmetic Expression Language）的缩写。

这种语言由一系列算术表达式编写，包括数字、算术操作符+（加）、-（减法和负数）、*（乘法）、/（除法）、%（模）、^（求幂），还有用于分组的()。

解释器将按照它们出现的顺序，计算出每个表达式的值，打印出每个结果。例如，给出下面的输入：

    
    3
    2 ^ 8
    (12 % 7) * (3 + 2)
    19 / -9


解释器将输出：

    
    3
    256
    25
    -2.111111111111111


AEL还允许你使用=操作符定义变量赋值。其左边是标识符，右边是算术表达式。带有赋值的语句没有返回值，因此解释器不会打印出相应的行。

例如，

    
    hoursPerDay = 24
    minutesPerHour = 60
    minutesPerDay = minutesPerHour * hoursPerDay
    minutesPerDay
    minutesPerDay * 60


输出：

    
    1440
    86400


AEL将有两个预定义变量：pi和e，各自代表的值为3.141592653589793和2.718281828459045。

最后，AEL还支持定义函数。函数赋值也使用=操作符，但是左边参数必须是带有圆括号的标识符，包含了零个或多个、由逗号分割的参数名称。一旦定义好了，写出标识符的名字，带上包含了零个或多个、由逗号分割的算术表达式的、小括号，函数就能被调用了。

例如，

    
    toDegrees(radians) = radians * 180 / pi
    toDegrees(2 * pi)
    
    cylinderVolume(r, h) = pi * r ^ 2 * h
    cylinderVolume(2, 4)


输出：

    
    360
    50.26548245743669


既然我们了解这种语言了，那么我开始编写解释器。

可以参考，我在线上分享的AEL解释器的实现。


### 第一步：词法分析


词法分析器接收文本输入，返回token列表。这里的lex函数的样子看起来是这样的：

    
    var lex = function (input) {
      var tokens = [];
      //some magic goes here
      return tokens;
    };


我们有了一些不同类型的token。有定义为字符组的+-*/^%=(),操作符，有数字，有我们的词法分析器将忽略的空格，有任意字符串定义的、不包含操作数、数字或空格的标识符。

    
    var isOperator = function (c) { return /[+\-*\/\^%=(),]/.test(c); },
    isDigit = function (c) { return /[0-9]/.test(c); },
    isWhiteSpace = function (c) { return /\s/.test(c); },
    isIdentifier = function (c) { return typeof c === "string" && !isOperator(c) && !isDigit(c) && !isWhiteSpace(c); };


我们将建立简单的循环来扫描输入文本。用变量c表示当前的字符，建立名叫advance的函数来遍历、一次处理一个字符、并返回下一个字符，用addToken函数把一个token附加到token列表。

    
    var tokens = [], c, i = 0;
    var advance = function () { return c = input[++i]; };
    var addToken = function (type, value) {
      tokens.push({
        type: type,
        value: value
     });
    };
    while (i < input.length) {
      c = input[i];
      //...
    }


如果c是空格，我们只需忽略并继续后面操作。如果c是操作符，就把操作数token添加到列表，并继续后面操作。

    
    if (isWhiteSpace(c)) advance();
    else if (isOperator(c)) {
      addToken(c);
      advance();
    }


为了简单起见，我们将定义一个数字做为数字列，可以附加小数点和另一个数字列。

每个其它字符都是标识符。

    
    else if (isIdentifier(c)) {
      var idn = c;
      while (isIdentifier(advance())) idn += c;
      addToken("identifier", idn);
    }


为了防止一些奇怪的东东抛给我们：

    
    else throw "Unrecognized token.";


在我们做完扫描输入之后，我们将增加一个区分结束的token。然后我们就完成了。

    
    addToken("(end)");
    return tokens;




### 第二步：分析器


有很多不同的编写分析器的策略。最常用的一种策略就是编写一个[法科斯范式](http://zh.wikipedia.org/wiki/%E5%B7%B4%E7%A7%91%E6%96%AF%E8%8C%83%E5%BC%8F)和[递归下降](http://en.wikipedia.org/wiki/Recursive_descent_parser)(recursive descent)【注1】。本文，我们将使用有些不同于平常的、操作符优先分析的策略，使用Douglas Crockford描述的[自顶向下](http://javascript.crockford.com/tdop/tdop.html) [操作数优先](http://en.wikipedia.org/wiki/Operator-precedence_parser)的技巧文章。

操作数优先分析的过程如下：



	
  * 把每个带有左约束力（binding power）的操作token与操作函数结合。

	
  * 如果操作符操作其左侧的token（例如+），就把它和左侧的指称函数结合（下面简写为led）。如果操作符没有操作左侧的token（比如一元运算符-），就把它和一个空的指称函数结合（下面简写为nud）。标识符和数字也有与其结合的nud函数。


基于此，就可以开始生成语法树了。为了呈现运行过程，下面的例子我使用算术表达式。

    
    12 + 4 / 6


分析器函数从执行第一个token（12）的nud开始，返回了本身：

    
    { type: "number", value: 12 }


它变成了左侧，我们把它传入下一个token（+）的led，递归调用分析器函数来分析剩下的token。

    
    {
      type: "+",
      left: { type: "number", value: 12 },
      right: //parse remaining tokens
    }


我们重新开始调用剩下token中的第一个token（4）的nud，返回本身。

    
    { type: "number", value: 4 }


这变成了我们传入下一个token（/）的左侧，将递归调用分析器函数来分析剩下的token。

    
    {
      type: "+",
      left: { type: "number", value: 12 },
      right: {
        type: "/"
        left: { type: "number", value: 4 },
        right: //parse remaining tokens
      }
    }


我们调用剩下的token（6）的第一个token的nud，它返回本身。这是token列表的结尾，因此分析树完成了。

    
    {
      type: "+",
      left: { type: "number", value: 12 },
      right: {
        type: "/"
        left: { type: "number", value: 4 },
        right: { type: "number", value: 6 }
      }
    }


如果我们交换+和/，我们将看到约束力是如何演变的。/有比+更高的约束力，因此它将更加紧密地绑定到操作数。

    
    12 / 4 + 6


我们重复之前的步骤：

    
    {
      type: "/",
      left: { type: "number", value: 12 },
      right: //parse remaining tokens
    }


但是这一次，在我们调用了4的nud之后，我们将看到前面的token，而+比/的优先级低。这意味着我们将把4绑在右侧，然后把整个当前数传递给led+，最终的语法树如下：

    
    {
      type: "+",
      left: {
        type: "/",
        left: { type: "number", value: 12 },
        right: { type: "number", value: 4 }
      },
      right: { type: "number", value: 6 },
    }


现在我们对分析过程有了一些理解，可以开始编写分析器了。分析器接收词法分析器产生的token，返回分析树，因此parse函数的样子看起来是这样的：

    
    var parse = function (tokens) {
     var parseTree = [];
     //some magic
     return parseTree;
    };


我们需要某种符号（symbol）表来结合符号和约束力，nud或led，我们需要一个函数来结合相应符号下的token。

    
    var symbols = {},
    symbol = function (id, nud, lbp, led) {
      var sym = symbols[id] || {};
      symbols[id] = {
        lbp: sym.lbp || lbp,
        nud: sym.nud || nud,
        led: sym.led || led
      };
    };
    
    var interpretToken = function (token) {
      var sym = Object.create(symbols[token.type]);
      sym.type = token.type;
      sym.value = token.value;
      return sym;
    };


我们需要一种方式来看到当前token以及继续下一个token。

    
    var i = 0, token = function () { return interpretToken(tokens[i]); };
    var advance = function () { i++; return token(); };


现在我们可以根据上面描述的方式编写表达式函数了，用来生成表达式的分析树。

    
    var expression = function (rbp) {
      var left, t = token();
      advance();
      if (!t.nud) throw "Unexpected token: " + t.type;
      left = t.nud(t);
      while (rbp < token().lbp) {
        t = token();
        advance();
        if (!t.led) throw "Unexpected token: " + t.type;
      left = t.led(left);
     }
     return left;
    };


我们现在创建用于定义操作符的infix和prefix函数：

    
    var infix = function (id, lbp, rbp, led) {
      rbp = rbp || lbp;
      symbol(id, null, lbp, led || function (left) {
        return {
          type: id,
          left: left,
          right: expression(rbp)
        };
      });
    },
    prefix = function (id, rbp) {
      symbol(id, function () {
        return {
          type: id,
          right: expression(rbp)
        };
      });
    };


现在我们以声明的形式定义所有的算术操作符。注意，幂操作符 (^)具有比左约束力小的右约束力。这是因为[幂是右结合的](http://en.wikipedia.org/wiki/Associative_property#Notation_for_non-associative_operations)。

    
    prefix("-", 7);
    infix("^", 6, 5);
    infix("*", 4);
    infix("/", 4);
    infix("%", 4);
    infix("+", 3);
    infix("-", 3);


有一些只是为分隔和划界而存在的操作符，他们用不着prefix和infix函数，因此，把它们添加到符号表就已足够了。

    
    symbol(",");
    symbol(")");
    symbol("(end)");


圆括号的nud仅仅返回它里面什么，数字的nud仅仅返回本身：

    
    symbol("(", function () {
      value = expression(2);
      if (token().type !== ")") throw "Expected closing parenthesis ')'";
      advance();
      return value;
    });
    symbol("number", function (number) {
        return number;
    });


标识符和=操作符的nud更加复杂，因为他们有基于上下文的行为：

    
    symbol("identifier", function (name) {
      if (token().type === "(") {
        var args = [];
        if (tokens[i + 1].type === ")") advance();
        else {
          do {
            advance();
            args.push(expression(2));
          } while (token().type === ",");
          if (token().type !== ")") throw "Expected closing parenthesis ')'";
        }
        advance();
        return {
          type: "call",
          args: args,
          name: name.value
        };
      }
      return name;
    });
    infix("=", 1, 2, function (left) {
        if (left.type === "call") {
          for (var i = 0; i < left.args.length; i++) {
            if (left.args[i].type !== "identifier") throw "Invalid argument name";
          }
          return {
            type: "function",
            name: left.name,
            args: left.args,
            value: expression(2)
          };
        } else if (left.type === "identifier") {
          return {
            type: "assign",
            name: left.value,
            value: expression(2)
          };
        }
        else throw "Invalid lvalue";
    });


现在所有的难点已经搞定了，整合到一起吧。

    
    var parseTree = [];
    while (token().type !== "(end)") {
      parseTree.push(expression(0));
    }
    return parseTree;




### 第三步：求值器


求值器接收分析器生成的分析树，对每一项求值，并输出值。我们的evaluate函数的样子形如：

    
    var evaluate = function (parseTree) {
      var parseNode = function (node) {
      //magic goes here
      };
      var output = "";
      for (var i = 0; i < parseTree.length; i++) {
        var value = parseNode(parseTree[i]);
        if (typeof value !== "undefined") output += value + "\n";
      }
      return output;
    };


它直接定义了操作数和所有预定义变量和函数的行为：

    
    var operators = {
        "+": function(a, b) {
            return a + b;
        },
        "-": function(a, b) {
            if (typeof b === "undefined") return -a;
            return a - b;
        },
        "*": function(a, b) {
            return a * b;
        },
        "/": function(a, b) {
            return a / b;
        },
        "%": function(a, b) {
            return a % b;
        },
        "^": function(a, b) {
            return Math.pow(a, b);
        }
    };
    
    var variables = {
        pi: Math.PI,
        e: Math.E
    };
    
    var functions = {
        sin: Math.sin,
        cos: Math.cos,
        tan: Math.cos,
        asin: Math.asin,
        acos: Math.acos,
        atan: Math.atan,
        abs: Math.abs,
        round: Math.round,
        ceil: Math.ceil,
        floor: Math.floor,
        log: Math.log,
        exp: Math.exp,
        sqrt: Math.sqrt,
        max: Math.max,
        min: Math.min,
        random: Math.random
    };
    var args = {};


现在我们能够继续求值器了，我们可以搞定的。ParseNode函数递归遍历和求值分析树。

    
    var parseNode = function (node) {
      if (node.type === "number") return node.value;
      else if (operators[node.type]) {
        if (node.left) return operators[node.type](parseNode(node.left), parseNode(node.right));
        return operators[node.type](parseNode(node.right));
      }
      else if (node.type === "identifier") {
        var value = args.hasOwnProperty(node.value) ? args[node.value] : variables[node.value];
        if (typeof value === "undefined") throw node.value + " is undefined";
        return value;
      }
      else if (node.type === "assign") {
        variables[node.name] = parseNode(node.value);
      }
      else if (node.type === "call") {
        for (var i = 0; i < node.args.length; i++) node.args[i] = parseNode(node.args[i]);
        return functions[node.name].apply(null, node.args);
      }
      else if (node.type === "function") {
        functions[node.name] = function () {
          for (var i = 0; i < node.args.length; i++) {
            args[node.args[i].value] = arguments[i];
          }
          var ret = parseNode(node.value);
          args = {};
          return ret;
        };
      }
    };




### 整合


现在我们可以打包，把这些块放到唯一的calculate函数里。

    
    var calculate = function (input) {
      try {
        var tokens = lex(input);
        var parseTree = parse(tokens);
        var output = evaluate(parseTree);
        return output;
      } catch (e) {
        return e;
      }
    };




### 接下来要做什么


你可以把很多东西增加到语言里，让它更有用、或只是看看运行过程。一些补充相当容易，一些非常难。


#### 简单的





	
  * 试着添加你自己预定义的函数。

	
  * 变更约束力数值，以观察表达式求值方式的改变。

	
  * 支持数字里的科学计数法，或让二进制、十六进制的使用成为可能。




#### 中级难度





	
  * 允许更多类型的数据操作，比如字符串、布尔值和数组。

	
  * 允许多语句和条件返回值的函数。

	
  * 用一种编译器或转换编译器接收分析树，并以另一种语言输出，以此取代求值器。

	
  * 做一个包管理器，支持你从其它文件导入代码。




#### 高级难度





	
  * 实现优化，让计算机更加有效率和快速。

	
  * 让函数成为一等公民，并支持闭包。

	
  * 让所有数据最后被求值。


如果你知道如何搞定这些技术，你就可以开始为你自己领域的具体语言编写解释器和编译器了。

	
  * 原文地址：[http://www.codeproject.com/Articles/345888/How-to-write-a-simple-interpreter-in-JavaScript](http://www.codeproject.com/Articles/345888/How-to-write-a-simple-interpreter-in-JavaScript)

	
  * 注1：参考左递归里提到的：[http://zh.wikipedia.org/wiki/左遞歸](http://zh.wikipedia.org/wiki/左遞歸)


