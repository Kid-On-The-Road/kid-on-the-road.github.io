---
layout: post
title: "JavaScript"
subtitle: "JavaScript文档"
categories: 前端
tags: [JavaScript]
author: "Kid-On-The-Road"
meta: ""

---

## 概述

​	在1995年时，由Netscape公司在网景导航者浏览器上首次设计实现而成。因为Netscape与Sun合作，Netscape管理层希望它外观看起来像Java，因此取名为JavaScript。
​	JavaScript是一种属于网络的脚本语言,已经被广泛用于Web应用开发,常用来为网页添加各式各样的动态功能,为用户提供更流畅美观的浏览效果。

运行在浏览器端的脚本编程语言，让网页与用户之间有交互的功能，让网页活起来。

### 网页中各技术的作用

| 技术       | 作用                     |
| ---------- | ------------------------ |
| HTML       | 用于网页结构制作         |
| CSS        | 用于网页美化             |
| JavaScript | 让网页与用户有交互的功能 |

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>javascript初相遇</title>
</head>
<body>
<!--所有的JS代码必须放在script标签中才可以执行-->
<script type="text/javascript">
    for (var i = 0; i < 5; i++) {
        document.write("<h1>Hello World</h1>");
    }
</script>
</body>
</html>
```

### JavaScript与Java的区别

| 特点     | Java                 | JavaScript                                 |
| -------- | -------------------- | ------------------------------------------ |
| 面向对象 | 面向对象编程         | 基于对象，不完全面向对象                   |
| 运行方式 | 编译型，生成中间文件 | 解释型，直接解析源代码                     |
| 跨平台   | 运行在虚拟机中       | 运行在浏览器，只要系统有浏览器就可以执行   |
| 数据类型 | 强类型语言           | 弱类型，同一个变量可以赋值为不同的数据类型 |
| 大小写   | 区分                 | 区分                                       |

## script标签

### 语言组成

| 组成部分    | 作用                                                         |
| ----------- | ------------------------------------------------------------ |
| ECMA Script | 所有网页脚本语言的标准，构成了JS语言的核心基础               |
| BOM         | Browser Object Model 浏览器对象模型，用来操作浏览器中对象    |
| DOM         | Document Object Model 文档对象模型，用来操作网页中各种标签和元素 |

### 标签说明

| 标签说明   | 解释                                     |
| ---------- | ---------------------------------------- |
| 标签个数   | 可以出现多个，每个标签都会依次执行       |
| 位置       | 可以出现在网页的任何位置，并且正常的执行 |
| 语句后分号 | 如果一行只有一条代码就可以省略           |

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>javascript初相遇</title>
</head>
<body>
<script type="text/javascript" src="js/out.js"></script>

<!--所有的JS代码必须放在script标签中才可以执行-->
<script type="text/javascript">
    for (var i = 0; i < 5; i++) {
        document.write("<h1>Hello World</h1>");
        if (i == 2) {
            document.write("Hello JavaScript");
        }
    }
</script>

<!--导入外部脚本：script标签必须是一个有主体的标签 -->
<script type="text/javascript" src="js/out.js"></script>
</body>
</html>
```

```javascript
document.write("外部脚本" + "<br/>");
```

### 注释

![1551946466936](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1551946466936.png) 

## 变量的定义

### 定义语法

| 数据类型 | Java中定义变量                    |
| -------- | --------------------------------- |
| 整数     | int i = 5;                        |
| 浮点数   | float f = 3.14; 或 double d=3.14; |
| 布尔     | boolean b = true;                 |
| 字符     | char c = 'a';                     |
| 字符串   | String str =   "abc";             |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>变量的定义</title>
</head>
<body>
<script type="text/javascript">
    var i = 5;  //整数
    document.write(i + "<br/>");

    var f = 3.14;  //浮点数
    document.write(f  + "<br/>");

    var b = true; //布尔
    document.write(b + "<br/>");

    //在JS中只有字符串类型，没有字符类型，字符串既可以使用单引号，也可以使用双引号。
    var c = 'a';    //字符串
    document.write(c  + "<br/>");

    var str = "abc";  //字符串
    document.write(str + "<br/>");
</script>
</body>
</html>
```

| 注意项                   | 解释                                                         |
| ------------------------ | ------------------------------------------------------------ |
| 弱类型                   | 同一个变量可以赋不同类型的值                                 |
| 在JS中的字符和字符串引号 | 在JS中只有字符串类型，没有字符类型，字符串既可以使用单引号，也可以使用双引号。 |
| var定义变量的特点        | - var关键字不是必须的，如果函数内的变量不写var，默认是全局变量。 <br />- 变量可以重复定义 <br />- 函数之外的大括号不能限制变量的范围 |

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>变量的定义</title>
</head>
<body>
<script type="text/javascript">
    var i = 5;  //整数
    document.write(i + "<br/>");

    var i = false; //布尔
    document.write(i + "<br/>");

    var f = 3.14;  //浮点数
    document.write(f  + "<br/>");
    {
        var b = true; //布尔
    }
    document.write(b + "<br/>");

    //在JS中只有字符串类型，没有字符类型，字符串既可以使用单引号，也可以使用双引号。
    c = 'a';    //字符串
    document.write(c  + "<br/>");

    var str = "abc";  //字符串
    document.write(str + "<br/>");
</script>
</body>
</html>
```

## 数据类型

| 关键字    | 说明                                               |
| --------- | -------------------------------------------------- |
| number    | 数值型(整数和浮点数)                               |
| boolean   | true/false                                         |
| string    | 包含字符和字符串，既可以使用双引号也可以使用单引号 |
| object    | 对象类型                                           |
| undefined | 未定义的类型，未知的类型                           |

### typeof操作符

作用：判断一个变量的数据类型

写法：typeof(变量名)  或  typeof 变量名

### 效果

![1571560013560](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1571560013560.png) 

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>判断变量的类型</title>
</head>
<body>
<script type="text/javascript">
    var i = 5;  //整数 number
    document.write(typeof(i) + "<br/>");

    var f = 3.14;  //浮点数 number
    document.write(typeof(f) + "<br/>");

    var b = true; //布尔 boolean
    document.write(typeof b+ "<br/>");

    var c = 'a';    //字符串 string
    document.write(typeof(c) + "<br/>");

    var str = "abc";  //字符串  string
    document.write(typeof str+ "<br/>");

    var date = new Date();   //JS内置对象，代表日期对象  object
    document.write(date + "<br/>");
    document.write(typeof date+ "<br/>");

    var n = null;  //object
    document.write(typeof n+ "<br/>");

    var u;    //undefined
    document.write(typeof u+ "<br/>");
</script>
</body>
</html>
```

## 数据类型的转换函数

### 全局函数

概念：一个函数可以在JS任何的地方调用

| 转换函数     | 作用                                                         |
| ------------ | ------------------------------------------------------------ |
| parseInt()   | 转成整数类型，如果字符串前面的部分可以转换就转换前面部分，<br />遇到第一个不能转换的字符就停止 |
| parseFloat() | 转成浮点数，转换功能同上                                     |
| isNaN()      | 判断是否为非数字，非数字返回true                             |

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>转换函数</title>
</head>
<body>
<script type="text/javascript">
    var num1 = "6.2";
    var num2 = "3.1";
    /*
    parseInt(变量名)：转成整数类型
    1. 对字符串进行转换，能转的就直接转换，不能转换的，转换前面一部分。
    2. 如果不能转换的，得到NaN = Not a Number
     */
    //document.write(parseInt(num1) + parseInt(num2)+ "<br/>");

    /*
    parseFloat(变量名)：转成小数，功能与上面的是一样的
     */
    document.write(parseFloat(num1) + parseFloat(num2)+ "<br/>");

    /*
         is Not a Number
     *  isNaN(变量名)：判断变量名是否为非数字，如果非数字，返回true，否则返回false
     *  如："abc" 返回true  "123"返回false
     */
    document.write(isNaN("abc") + "<br/>");   //true
    document.write(isNaN("123") + "<br/>");   //false
    document.write(isNaN("123a") + "<br/>");   //true
</script>
</body>
</html>
```

## 在浏览器中调试代码

### 设置断点

注：设置断点以后要重新刷新页面才会在断点停下来

![1551953129121](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1551953129121.png)

### 语法错误

![1551947495069](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1551947495069.png) 



## 常用的运算符

### 算术运算符

算术运算符用于执行两个变量或值的算术运算

![1551947559080](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1551947559080.png) 

### 赋值运算符

赋值运算符用于给JavaScript 变量赋值

![1551947658451](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1551947658451.png) 

### 比较运算符

比较运算符用于逻辑语句的判断，从而确定给定的两个值或变量是否相等。

![1551947697070](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1551947697070.png) 

数字可以与字符串进行比较，字符串可以与字符串进行比较。字符串与数字进行比较的时候会先把字符串转换成数字然后再进行比较

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>运算符</title>
</head>
<body>
<script type="text/javascript">
    var n1 = 5;
    var n2 = "5";
    var n3 = 4;
    //在比较运算符中字符串会转换成整数类型进行比较
    document.write((n1 == n2) + "<br/>");  //true
    document.write((n3 < n2) + "<br/>");  //true
    //恒等于：既比较值，又比较类型
    document.write((n1 === n2) + "<br/>");  //false
    document.write((n2 === "5") + "<br/>");  //true
</script>
</body>
</html>
```

### 逻辑运算符

逻辑运算符用来确定变量或值之间的逻辑关系，支持短路运算

![1551947786567](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1551947786567.png) 

逻辑运算符不存在单与&、单或|

### 三元运算符

![1551947843411](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1551947843411.png) 



## 流程控制

### if语句

#### if 语句

在一个指定的条件成立时执行代码。 

```
if(条件表达式) {
     //代码块;
}
```

#### if...else 语句

在指定的条件成立时执行代码，当条件不成立时执行另外的代码。

```
if(条件表达式) {
     //代码块;
 }
 else {
     //代码块;
 }
```

#### if...else if....else 语句

使用这个语句可以选择执行若干块代码中的一个。

```
if (条件表达式) {
     //代码块;
 }
 else if(条件表达式) {
     //代码块;
 }
 else {
     //代码块;
 }
```

#### 非布尔类型的表达式

| 数据类型            | 为真   | 为假 |
| ------------------- | ------ | ---- |
| number              | 非0    | 0    |
| string              | 非空串 | 空串 |
| undefined           |        | 假   |
| NaN(Not a   Number) |        | 假   |
| object              | 有对象 | null |

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>if语句</title>
</head>
<body>
<script type="text/javascript">
    /*if (0) {
        document.write("真" + "<br/>");
    }
    else {
        document.write("假" + "<br/>");
    }*/

    /*
    if ("abc") {
        document.write("真" + "<br/>");
    }
    else {
        document.write("假" + "<br/>");
    }
    */

    /*
    var u;
    if (u) {
        document.write("真" + "<br/>");
    }
    else {
        document.write("假" + "<br/>");
    }*/

    /*
    var num = parseInt("abc");  //NaN
    if (num) {
        document.write("真" + "<br/>");
    }
    else {
        document.write("假" + "<br/>");
    }
    */

    var date = null;
    if (date) {
        document.write("真" + "<br/>");
    }
    else {
        document.write("假" + "<br/>");
    }
</script>
</body>
</html>
```

### switch语句

- case后使用常量，与Java相同

```
switch(变量名) {
   case 常量值:
      break;
   case 常量值：
      break;
   default:
       break;
 }
```

- case后使用表达式

```
switch(true) {  //这里的变量名写成true
   case 表达式:     //如：n > 5
     break;
   case 表达式:
     break;
   default:
     break;
 }
```

#### 相关的方法

| window对象的方法名                  | 作用                                   |
| ----------------------------------- | -------------------------------------- |
| string  prompt("提示信息","默认值”) | 输入框<br />1. 提示信息<br />2. 默认值 |
| alert("提示信息")                   | 信息提示框                             |

#### 输入框

![1562746273460](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1562746273460.png) 

#### 信息提示框

![1562746197150](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/CSS&JSP/1562746197150.png) 

注：window对象

### 循环语句

#### while语句

当指定的条件为 true 时循环执行代码

```
while (条件表达式) {
     需要执行的代码;
 }
```

#### do-while语句：

最少执行1次循环

```
do {
     需要执行的代码;
 }
 while (条件表达式)
```

#### for 语句

循环指定次数

```
for (var i=0; i<10; i++) {
     需要执行的代码;
 }
```

#### break和continue

```
break: 结束整个循环
continue：跳过本次循环，执行下一次循环
```

## 函数

### 概述

什么是函数：类似于Java中方法，将一部分代码起名放在一个代码块中重用，供其它的代码调用。

两种函数：命名函数和匿名函数

- 命名函数：可以通过名字重复调用
- 匿名函数：通常只使用一次，后期主要用在事件处理函数中。

### 命名函数

#### <font color="red">命名函数的格式</font>

```javascript
function 函数名(参数列表) {
  代码块
  [return 返回值;]
}
```

#### 自定义函数

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>函数</title>
</head>
<body>
<script type="text/javascript">
    /*
       定义函数
      1. 函数前面没有返回类型
      2. 形参前面没有数据类型
      3. 如果函数没有返回值，不需要return，如果有加上return返回值
      4. 函数不调用不执行
     */
    function sum(m, n) {
        alert("函数被调用了");
        return m + n;
    }

    //调用函数
    var result = sum(3,5);
    document.write("结果：" + result + "<br/>");
</script>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>关于函数的重载和隐藏的数组</title>
</head>
<body>
<script type="text/javascript">
    /**
     * 在JS中没有函数的重载，后面同名的函数会覆盖前面的函数
     * 函数的形参个数与实参个数没有关系
     */
    //定义1个函数
    function sum(a) {
        alert("1个参数");
    }

    function sum(a,b) {
        alert("2个参数");
    }

    function sum(a,b,c) {
        alert("3个参数");
    }

    //调用函数
    sum(2);
</script>
</body>
</html>
```

#### 隐藏数组的执行过程

![1571707952136](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1571707952136.png)

### 匿名函数

#### 语法

```javascript
//用于事件的处理，不可重用
元素.on事件=function() {
  代码块
}
```

```javascript
//可以将匿名函数赋值到一个变量中，后期可以通过这个变量名来引用
var 变量名 = function(参数列表) {
  代码块
  [return 返回值];
}

//后期引用
变量名(参数列表)
```

#### 函数调用代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>匿名函数</title>
</head>
<body>
<script type="text/javascript">
    /*
    //可以将匿名函数赋值到一个变量中，后期可以通过这个变量名来引用
    var 变量名 = function(参数列表) {
      代码块
      [return 返回值];
    }

    //后期引用
    变量名(参数列表)
     */
    var sum = function (a, b) {
        alert("调用函数");
        return a + b;
    }

    //调用
    var result = sum(3,5);
    document.write("结果：" + result + "<br/>");
</script>
</body>
</html>
```

## 事件

### 解释

当用户在网页上进行各种操作的时候，如：鼠标点击，双击，按下键盘，鼠标移动等。就会激活各种事件，我们可以针对进行事件进行编程，实现与用户的交互功能。

### 设置事件的方式

1. 方式一：命名函数      

```html
给按钮设置单击事件，当用户点击此按钮，就会自动调用指定的函数名
<input type="button" onclick="函数名()">
```

2. 方式二：匿名函数 (代码耦合度更低)

```javascript
按钮对象.onclick = function() {
  代码
}
```

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件激活的2种方式</title>
</head>
<body>
<!--命名函数-->
<input type="button" onclick="clickMe()" value="按钮1">

<!--匿名函数-->
<input type="button"  value="按钮2" id="b2">

<script type="text/javascript">
    //命名函数
    function clickMe() {
        alert("我是按钮1");
    }

    //匿名函数：耦合度更低
    document.getElementById("b2").onclick = function () {
        alert("我是按钮2");
    }
</script>
</body>
</html>
```

### 加载完成事件

1. 事件名：onload
2. 示例：页面加载完毕以后，才执行相应的JS代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件激活的2种方式</title>
</head>
<body>
<script type="text/javascript">
    //命名函数
    function clickMe() {
        alert("我是按钮1");
    }

    //窗口全部加载完毕
    window.onload = function() {
        //匿名函数：耦合度更低
        document.getElementById("b2").onclick = function () {
            alert("我是按钮2");
        }
    }
</script>

<!--命名函数-->
<input type="button" onclick="clickMe()" value="按钮1">

<!--匿名函数-->
<input type="button"  value="按钮2" id="b2">
</body>
</html>
```

### 鼠标点击事件

1. 单击：onclick
2. 双击：ondblclick

#### 效果

![1551952995946](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1551952995946.png) 

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>单击和双击事件</title>
    <style>
        * {
            margin: 5px;
        }
    </style>
</head>
<body>
<!--name属性给服务器使用的，id属性是给浏览器使用的-->
姓名：<input type="text" name="t1" id="t1"> <br/>
姓名：<input type="text" name="t2" id="t2"> <br/>
<input type="button" value="单击复制/双击清除" id="b1">

<script type="text/javascript">
    //按钮单击事件
     document.getElementById("b1").onclick = function () {
         document.getElementById("t2").value = document.getElementById("t1").value;
     }

     //按钮双击事件
    document.getElementById("b1").ondblclick = function () {
        document.getElementById("t1").value = "";
        document.getElementById("t2").value = "";
    }
</script>
</body>
</html>
```



### 鼠标移入和移出事件

#### 事件名

1. 移入：onmouseover (over上面)
2. 移出：onmouseout 

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>鼠标的移上和移出</title>
    <style>
        body {
            background-color: black;
            text-align: center;
        }
    </style>
</head>
<body>
<img src="img/0.jpg" width="700" id="girl">

<script type="text/javascript">
    //鼠标移上
    document.getElementById("girl").onmouseover = function () {
        //修改自己的src属性
        //document.getElementById("girl").src = "img/2.jpg";
        this.src = "img/2.jpg";
    }

    //鼠标移出
    document.getElementById("girl").onmouseout = function () {
        this.src = "img/1.jpg";
    }
</script>
</body>
</html>
```

### this关键字

- 出现在控件的事件方法中：

```html 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>鼠标的移上和移出</title>
    <style>
        body {
            background-color: black;
            text-align: center;
        }
    </style>
</head>
<body>
<!--this表示img对象-->
<img src="img/0.jpg" width="700" id="girl" onmouseover="changePicture(this)">

<script type="text/javascript">
    /*
    //鼠标移上
    document.getElementById("girl").onmouseover = function () {
        //修改自己的src属性
        //document.getElementById("girl").src = "img/2.jpg";
        this.src = "img/2.jpg";
    }
    */

    //命名函数
    function changePicture(img) {
        img.src = "img/3.jpg";
    }

    //鼠标移出
    document.getElementById("girl").onmouseout = function () {
        this.src = "img/1.jpg";
    }
</script>
</body>
</html>
```

- 出现在匿名函数的代码中：

```javascript
//this相当于事件激活的对象
document.getElementById("girl").onmouseout = function () {
  this.src = "img/1.jpg";
}
```

### 得到焦点、失去焦点事件

#### 效果

![1551953586472](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1551953586472.png)

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>得到焦点和失去焦点</title>
</head>
<body>
用户名:
<input type="text" id="user" placeholder="请输入用户名"> <span id="info" style="color: red"></span>
<script type="text/javascript">
    //文本框得到焦点事件
    document.getElementById("user").onfocus = function () {
        document.getElementById("info").innerText = "";
    }
    
    //文本框得到失去焦点事件
    document.getElementById("user").onblur = function () {
        document.getElementById("info").innerText = "用户名不能为空";
    }
</script>
</body>
</html>
```

### 改变事件

#### 效果

![1551953679058](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1551953679058.png) 

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>改变事件</title>
</head>
<body>
城市：
<select id="city">
    <option value="羊城">广州</option>
    <option value="鹏城">深圳</option>
    <option value="旅游">东莞</option>
</select>
<hr/>
英文：
<input type="text" id="eng">

<script type="text/javascript">
    //选项发生变化，显示当前选中的值
    document.getElementById("city").onchange = function () {
        alert(this.value);
    }

    //文本框改变事件(在失去焦点以后激活)
    document.getElementById("eng").onchange = function () {
        this.value = this.value.toUpperCase();    //将字符串转成大写
    }
</script>
</body>
</html>
```

## 内置对象

### 数组对象

#### 创建数组的方式

注：JS中数组是一个对象

| 创建数组的方式      | 说明                           |
| ------------------- | ------------------------------ |
| new Array()         | 创建一个长度为0的数组          |
| new Array(5)        | 创建一个长度为5的数组          |
| new Array(1,2,5,20) | 指定数组中每个元素创建一个数组 |
| [4,2,10,6]          | 指定数组中每个元素创建一个数组 |

| 方法名          | 功能                    |
| --------------- | ----------------------- |
| concat()        | 拼接                    |
| reverse()       | 反转                    |
| join(separator) | 将数组连接成一个字符串  |
| sort()          | 排序                    |
| pop()           | 删除最后一个元素        |
| push()          | 添加1个或多个元素到最后 |

#### 数组的特点

1. 每个元素的数据类型可以不同
2. 数组长度是可以变化的
3. 数组中还有方法

#### 效果

![1571716039003](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1571716039003.png) 

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>数组的特点</title>
</head>
<body>
<script type="text/javascript">
    //1. 数组中每个元素的类型可以不同
    var arr = [5, 2, 10, 6];
    arr[1] = true;
    arr[2] = "abc";
    document.write(arr + "<hr/>");

    //2. 数组的长度可以变化
    arr[5] = 11;
    for (var i = 0; i < arr.length; i++) {
        document.write(arr[i] + "&nbsp;");
    }

    document.write("<hr/>");
    arr.length = 3;   //数组只剩前面3个元素
    document.write(arr + "<hr/>");

    //3. 数组中还包含方法
    //concat() 拼接1个或多个数组
    var a1 = [2, 5, 6];
    var a2 = [3, 10, 7];
    var a3 = a1.concat(a2, 99);
    document.write(a3 + "<br/>");

    //reverse() 数组进行反转
    a3.reverse();
    document.write(a3 + "<hr/>");

    //join(分隔符)：将一个数组通过分隔符拼接成一个字符串，功能与split()相反的
    var str = a3.join("^_^");
    document.write("字符串：" + str + "<hr/>");

    /*
    sort() 排序，默认是按字符串的大小排序，字符串是比较ASCII码值
    1. 大写字母 < 小写字母
    2. 数字 < 字母
    3. 先比较第1个字符，谁大谁就大。如果相同，则比较第2个，谁大谁就大，以此类推。
     */
    document.write(("ac" > "abcdefg") + "<br/>");   //true
    document.write(("x" > "ASLKDJFLASDKFJ") + "<br/>");  //true
    document.write(("28O3U" > "2834328974") + "<hr/>");  //true

    var arr = ["Rose","Jack", "newboy","Tom"];  //Jack, Rose, Tom, newboy
    document.write("排序前：" + arr + "<br/>");
    arr.sort();
    document.write("排序后：" +  arr + "<hr/>");

    //对数字进行排序，默认是按字符串的大小排序
    var arr = [1000, 35, 200, 9, 28];
    document.write("排序前：" + arr + "<br/>");
    arr.sort();
    document.write("排序后：" +  arr + "<hr/>");
    //如果按数字排序，必须指定比较器，类似于Java中Comparator，根据第一个参数小于、等于或大于第二个参数分别返回负整数、零或正整数。
    arr.sort(function (a,b) {
        return a - b;   //升序
    });
    document.write("升序：" +  arr + "<hr/>");
    arr.sort(function (a,b) {
        return b - a;   //降序
    });
    document.write("降序：" +  arr + "<hr/>");

    //pop() 删除数组中最后一个元素，并且返回这个元素
    var arr = [1000, 35, 200, 9, 28];
    document.write("删除前：" + arr + "<br/>");
    var number = arr.pop();
    document.write("被删除的数：" + number + "<br/>");
    document.write("数组：" + arr + "<hr/>");

    //push() 在数组最后添加1个或多个元素
    arr.push(66,88);
    document.write("添加后数组：" + arr + "<br/>");
</script>
</body>
</html>
```

### 日期对象

#### 创建日期对象

```
var 变量名 = new Date();
创建现在的时间，得到浏览器端的时间
```

#### 日期对象的方法

![1552052803821](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1552052803821.png)

#### 效果

![1571728073788](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1571728073788.png) 

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>日期对象</title>
</head>
<body>
    <script type="text/javascript">
        //创建日期对象
        var date = new Date();
        document.write(date + "<br/>");
        document.write("年份：" + date.getFullYear() + "<br/>");
        document.write("月份：" + date.getMonth() + "<br/>");
        document.write("第几天：" + date.getDate() + "<br/>");
        document.write("周几：" + date.getDay() + "<br/>");
        //类似于Java中System.currentTimeMillis()
        document.write("1970-1-1到现在相差的毫秒数：" + date.getTime() + "<br/>");
        //得到本地化的时间字符串
        document.write(date.toLocaleString() + "<br/>");
    </script>
</body>
</html>
```

## 使用JS修改CSS的样式

### JS操作CSS属性命名的区别

| CSS中写法 | JS中的写法 | 说明                         |
| --------- | ---------- | ---------------------------- |
| color     | color      | 一个单词是一样的             |
| font-size | fontSize   | 多个单词样式名使用驼峰命名法 |

- 一条代码修改一个样式

```
元素.style.样式名=样式值;
```

- 一条代码修改多个样式

```
元素.className = 类名;
前提：预先定义一个类名，在类名中指定一批样式。
```

### 效果

![1552049542846](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1552049542846.png) 

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>使用JS修改CSS样式</title>
    <style>
        .boy {
            font-size: 35px;
            color: blue;
            font-family: 隶书;
        }
    </style>
</head>
<body>
<p id="p1">我是女生</p>
<p id="p2">我是男生</p>
<hr/>
<input type="button" value="改女生" id="b1">
<input type="button" value="改男生" id="b2">

<script type="text/javascript">
    //使用方式一修改样式
    document.getElementById("b1").onclick = function () {
        //每句话改一个样式
        var p1 = document.getElementById("p1");
        p1.style.fontSize = "35px";
        p1.style.color = "red";
        p1.style.fontFamily = "楷体";
    }

    //使用方式二：修改类样式
    document.getElementById("b2").onclick = function () {
        //先设置一个类名
        var p2 = document.getElementById("p2");
        p2.className = "boy";
    }
</script>
</body>
</html>
```

### 网页变化

![1571716664605](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1571716664605.png) 



## BOM

### 解释

Browser Object Model 浏览器对象模型，用来操作浏览器中各种对象。

![1552052941943](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1552052941943.png)

### BOM对象

| BOM常用对象 | 作用                                                     |
| ----------- | -------------------------------------------------------- |
| window      | 代表浏览器窗口对象<br />prompt(), alert(), setInterval() |
| location    | 地址栏对象                                               |
| history     | 浏览器的历史记录对象                                     |

### location对象

作用：代表一个地址栏对象，如果给location赋值，默认是给href属性，location对象其实是window的一个属性

| 属性名 | 作用          |
| ------ | ------------- |
| href   | 跳转地址      |
| search | 得到?查询字符 |
| hash   | 得到锚点      |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>location地址栏对象</title>
</head>
<body>
<script type="text/javascript">
    /*
    属性：href
        1. 获取：得到当前访问的地址字符串
        2. 设置：可以进行页面的跳转
        var url = location.href;
        document.write("当前访问的地址是：" + url + "<br/>");
        //可以进行页面的跳转
        alert("注意，我要跳转了!");
        location.href = "http://www.itcast.cn";
     */

    /*
    属性：search
        获取：地址?后面的参数字符串
        var param = location.search;
        document.write("查询字符串：" + param + "<br/>");
     */

    /*
    属性：hash
        获取：# 锚点 的字符串
     */
    var hash = location.hash;
    document.write("锚点：" + hash + "<br/>");
</script>
</body>
</html>
```

### location常用方法

| 方法名    | 作用                                                         |
| --------- | ------------------------------------------------------------ |
| reload()  | 刷新                                                         |
| assign()  | 加载 URL 指定的新的 HTML 文档。 就相当于一个链接，跳转到指定的url，当前页面会转为新页面内容，可以点击后退返回上一个页面。 |
| replace() | 通过加载 URL 指定的文档来替换当前文档 ，这个方法是替换当前窗口页面，前后两个页面共用一个 |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>location的方法</title>
</head>
<body>
<input type="button" value="刷新" onclick="location.reload()">
<input type="button" value="跳转" onclick="location.assign('demo12_css.html')">
<input type="button" value="代替" onclick="location.replace('demo12_css.html')">
<script type="text/javascript">
    /*
    reload()：重新加载当前页面，相当于浏览器上刷新按钮，用在需要刷新页面场景。
     */
    document.write(new Date().toLocaleString() + "<br/>");

    /*
    assign() 功能与location.href是一样的，跳转到另一个页面。记录在历史记录中，可以点后退回来。
    replace() 也可以进行页面跳转，但不会记录在历史记录中。
     */
</script>
</body>
</html>
```

### history对象

#### 作用

| 方法      | 作用                                                         |
| --------- | ------------------------------------------------------------ |
| forward() | 前进，相当于浏览器上前进按钮。如果这个前进按钮不可用，这个方法也是失效的。 |
| back()    | 后退，相当于浏览器上后退按钮。                               |
| go(数字)  | 相当于前进+后退。<br />如果参数是1，表示前进1个页，如果是-1表示后退一个页面。 |

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>历史对象</title>
</head>
<body>
<a href="demo14_date.html">显示时间</a> <hr/>
<input type="button" value="前进" onclick="history.forward()">
<input type="button" value="前进" onclick="history.go(1)">
</body>
</html>
```

```html
<input type="button" value="后退" onclick="history.back()">
<input type="button" value="后退" onclick="history.go(-1)">
<hr/>
```

### window中计时器有关的方法

| window中的方法                  | 作用                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| setTimeout(函数名, 间隔毫秒数)  | 隔一段时间执行一次指定的函数，执行1次就结束了                |
| clearTimeout(计时器)            | 清除计时器，让上面的函数调用不再起作用                       |
| setInterval(函数名, 间隔毫秒数) | 每隔一段时间执行一次指定的函数，不断的执行<br />返回值：计时器 |
| clearInterval(计时器)           | 清除计时器，让上面的函数调用不再起作用                       |

### 倒计时

#### 效果

![1552053355566](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1552053355566.png) 

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>window对象与location对象的综合案例应用</title>
</head>
<body>
<h1><span id="num">5</span>秒后回到主页</h1>

<script type="text/javascript">
    var num = 5;
    //每过1秒调用一次指定的函数
    window.setInterval(function () {
         num--;
         //修改span中值
        document.getElementById("num").innerText = num;
        //判断是否为0
        if (num == 0) {
            location.href = "http://www.itcast.cn";
        }
    }, 1000);
</script>
</body>
</html>
```



### 时钟

#### 效果

![1552053500102](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1552053500102.png)

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>会动的时钟</title>
</head>
<body>
<input type="button" value="开始" id="btnStart">
<!--按钮不可用-->
<input type="button" value="暂停" id="btnPause" disabled="disabled">
<hr/>
<h1 id="clock" style="color: darkgreen"></h1>

<script type="text/javascript">
    //页面加载完毕显示当前的时间
    window.onload = function () {
        document.getElementById("clock").innerText = new Date().toLocaleString();
    }

    var timer;  //计时器

    //开始按钮
    document.getElementById("btnStart").onclick = function () {
        /*
        开始按钮不可用: 在JS代码中disabled=true 表示按钮不可用，false表示可用
         */
        document.getElementById("btnStart").disabled = true;
        //暂停按钮可用
        document.getElementById("btnPause").disabled = false;
        //每过1秒中将现在的时间显示在h1中
        timer = setInterval(function () {
            document.getElementById("clock").innerText = new Date().toLocaleString();
        },1000);
    }

    //暂停按钮
    document.getElementById("btnPause").onclick = function () {
        document.getElementById("btnStart").disabled = false;  //可用
        document.getElementById("btnPause").disabled = true;  //不可用
        //清除计时器
        clearInterval(timer);
    }
</script>

</body>
</html>
```

### <font color="red">innerHTML和innerText的区别</font>

#### 语法

| 元素的属性 | 作用                                                         |
| ---------- | ------------------------------------------------------------ |
| innerHTML  | 获得：标签内部的HTML，包含了子标签<br />设置：修改标签内部的HTML，HTML标签是起使用 |
| innerText  | 获得：标签内部的纯文本，不包含任何的标签<br />设置：设置为纯文本，HTML标签是不起使用的。 |

#### 效果

![1552053767093](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1552053767093.png)

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>innerHTML和innerText</title>
</head>
<body>
<div id="myDiv">
    <span>
        <a href="#">我是链接</a>
    </span>
</div>
<hr/>
<!--innerHTML和innerText区别-->
<input type="button" id="b1" value="得到HTML">
<input type="button" id="b2" value="得到Text">
<input type="button" id="b3" value="设置HTML">
<input type="button" id="b4" value="设置Text">

<script type="text/javascript">
    //得到HTML
    document.getElementById("b1").onclick = function () {
        alert(document.getElementById("myDiv").innerHTML);
    }

    //得到Text
    document.getElementById("b2").onclick = function () {
        alert(document.getElementById("myDiv").innerText);
    }

    //设置HTML
    document.getElementById("b3").onclick = function () {
        document.getElementById("myDiv").innerHTML = "<h1 style='color: red'>Good good Study, Day Day Up! </h1>";
    }

    //设置Text
    document.getElementById("b4").onclick = function () {
        document.getElementById("myDiv").innerText = "<h1 style='color: red'>Good good Study, Day Day Up! </h1>";
    }
</script>
</body>
</html>
```

### window中的三个对话框方法

#### 语法

![1552053909245](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1552053909245.png)

#### confirm案例演示

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>确认框</title>
</head>
<body>
<script type="text/javascript">
    //如果点确定，返回true，否则返回false
    var flag = window.confirm("真的要删除吗?");
    if (flag) {
        alert("删除成功");
    } 
</script>
</body>
</html>
```

## DOM

### 节点与DOM树

Document Object Model 文档对象模型

只要操作DOM树，就可以修改网页的内容

![1552054005396](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1552054005396.png)

### 查找节点的方法

| 获取元素的方法                             | 作用                     |
| ------------------------------------------ | ------------------------ |
| document.getElementById("id")              | 通过id得到唯一元素       |
| document.getElementsByTagName   ("标签名") | 通过标签名字得到一组元素 |
| document.getElementsByName("name")         | 通过name属性得到一组元素 |
| document.getElementsByClassName("类名")    | 通过类名得到一组元素     |

#### 效果

![1568450069477](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP高级/1568450069477.png)

#### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>查询DOM树上节点</title>
    <style>
        table {
            width: 400px;
            /*细边框样式*/
            border-collapse: collapse;
        }
    </style>
</head>
<body>
<input type="button" value="(通过标签名)给奇数行和偶数行添加背景色" id="b1"/>
<hr/>
<table border="1">
    <tr>
        <td>100</td>
        <td>100</td>
        <td>100</td>
    </tr>
    <tr>
        <td>100</td>
        <td>100</td>
        <td>100</td>
    </tr>
    <tr>
        <td>100</td>
        <td>100</td>
        <td>100</td>
    </tr>
    <tr>
        <td>100</td>
        <td>100</td>
        <td>100</td>
    </tr>
    <tr>
        <td>100</td>
        <td>100</td>
        <td>100</td>
    </tr>
    <tr>
        <td>100</td>
        <td>100</td>
        <td>100</td>
    </tr>
</table>
<hr/>

<input type="button" value="(通过name属性)选中所有的商品" id="b2"/>
<hr/>
<!--设置checked = true表示选中-->
<input type="checkbox" name="product"> 自行车
<input type="checkbox" name="product"> 电视机
<input type="checkbox" name="product"> 洗衣机
<hr/>

<input type="button" value="(通过类名)给a添加链接" id="b3"/>
<hr/>
<a class="company">传智播客</a>
<a class="company">传智播客</a>
<a class="company">传智播客</a>

<script type="text/javascript">
    //(通过标签名)给奇数行和偶数行添加背景色
    document.getElementById("b1").onclick = function () {
        var trs = document.getElementsByTagName("tr");  //得到整个表格中所有的tr
        for (var i = 0; i < trs.length; i++) {
            var tr = trs[i];   //表示其中一行
            if (i % 2 == 0) {  //偶数
                tr.style.backgroundColor = "green";
            }
            else {  //奇数
                tr.style.backgroundColor = "yellow";
            }
        }
    }

    //(通过name属性)选中所有的商品
    document.getElementById("b2").onclick = function () {
        var products = document.getElementsByName("product");
        for (var i = 0; i < products.length; i++) {
            var product = products[i];
            //设置checked = true表示选中
            product.checked = true;
        }
    }

    //(通过类名)给a添加链接
    document.getElementById("b3").onclick = function () {
        var companies = document.getElementsByClassName("company");
        for (var i = 0; i < companies.length; i++) {
            var company = companies[i];
            company.href = "http://www.itcast.cn";
        }
    }
</script>
</body>
</html>
```

### DOM树修改的方法

#### 添加元素的步骤

1. 创建这个元素
2. 将元素挂到DOM树上

#### 创建元素的方法

| 创建元素的方法                   | 作用                           |
| -------------------------------- | ------------------------------ |
| document.createElement("标签名") | 创建一个元素，参数是标签的名字 |

#### 修改DOM树的方法

| 将元素挂到DOM树上的方法    | 作用                                 |
| -------------------------- | ------------------------------------ |
| 父元素.appendChild(子元素) | 将子元素添加成父元素的最后一个子元素 |
| 父元素.removeChild(子元素) | 父元素删除指定的子元素               |
| 元素.remove()              | 删除自己                             |

#### 通过关系找节点

| 遍历节点的属性  | 说明                     |
| --------------- | ------------------------ |
| childNodes      | 得到当前元素的所有子节点 |
| firstChild      | 得到第一个子节点         |
| lastChild       | 得到最后一个子节点       |
| parentNode      | 得到当前元素的父节点     |
| nextSibling     | 得到下一个兄弟节点       |
| previousSibling | 得到上一个兄弟节点       |

## 正则表达式

### 效果

![1552051283134](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552051283134.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>验证手机号码</title>
</head>
<body>
手机号：
<input type="text" id="tel"/>
<input type="button" id="btn" value="验证"/>
<script type="text/javascript">
    /*
    如果验证通过，返回true，否则返回false。
     */
    function checkPhone() {
        /*
        1. 必须全是数字
        2. 必须是11位
        3. 以1开头，第2个数字不能是012，第3个以后的数字任意
         */
        //1. 得到文本框输入的值
        var tel = document.getElementById("tel").value.trim();
        //2. 使用上面的规则进行判断
        if (isNaN(tel)) {
            return false;
        }
        if (tel.length != 11) {
            return false;
        }
        if (tel.charAt(0) != '1') {
            return false;
        }
        if (tel.charAt(1) == '0' || tel.charAt(1) == '1' || tel.charAt(1) == '2') {
            return false;
        }
        return true;
    }

    document.getElementById("btn").onclick = function () {
        if (checkPhone()) {
            alert("验证通过");
        }
        else {
            alert("验证失败");
        }
    };
</script>
</body>
</html>
```



### 正则表达式作用

1. 简化字符串的验证，判断一个字符串是否匹配指定的规则
2. 查询和搜索字符串的作用

### 规则

| 符号   | 作用                                                     |
| ------ | -------------------------------------------------------- |
| [a-z]  | []表示1个字符，-表示一个范围。匹配所有的小写字母         |
| [xyz]  | 匹配x或y或z                                              |
| [^xyz] | 在中括号中加上^的符号表示取反，匹配除了xyz之外的任意字符 |
| \d     | 表示数字                                                 |
| \w     | 表示单词，相当于这些字符：[a-zA-Z0-9_]                   |
| .      | 匹配任意的字符，通配符。如果要匹配点号，必须要转义：\\.  |
| ()     | 代表一组，表示后面的操作符对这一组进行操作               |
| {n}    | 前面的字符出现n次   n==x                                 |
| {n,}   | 前面的字符出现大于等于n次  n<=x                          |
| {n,m}  | 前面的字符出现n到m之间的次数，包头包尾  n<=x<=m          |
| +      | 前面的字符出现1到n次                                     |
| *      | 前面的字符出现0到n次                                     |
| ?      | 前面的字符出现0到1次                                     |
| \|     | 或者，几个字符串选择1个                                  |
| ^      | 在最前面表示匹配开头                                     |
| $      | 在最后面表示匹配结束                                     |

### 举例

| 正则表达式 | 匹配字符串                                    |
| ---------- | --------------------------------------------- |
| \d{3}      | 匹配3个数字，在JS中模糊匹配，在Java中精确匹配 |
| ^\d{3}     | 匹配以3个数字开头的字符串                     |
| \d{3}$     | 匹配以3个数字结尾的字符串                     |
| ^\d{3}$    | 精确匹配3个数字                               |
| ab{2}      | 匹配abb                                       |
| ab{2,}     | 匹配abb, abbb, abbbbbbbbbbbbbbbb              |
| ab{3,5}    | abbb, abbbb,abbbbb                            |
| ab+        | ab, abbbbb                                    |
| ab\*       | a,  ab,  abbbbbbbbbb                          |
| ab?        | a, ab                                         |
| hi\|hello  | hi或hello中一个                               |
| (b\|cd)ef  | 匹配bef或cdef                                 |
| ^.{3}$     | 匹配任意的3个字符                             |
| \[^a-zA-Z] | 除了字母之外的字符                            |

### 使用正则表达式的实现

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>验证手机号码</title>
</head>
<body>
手机号：
<input type="text" id="tel"/>
<input type="button" id="btn" value="验证"/>
<script type="text/javascript">
    /*
    如果验证通过，返回true，否则返回false。
     */
    function checkPhone() {
        /*
        1. 必须全是数字
        2. 必须是11位
        3. 以1开头，第2个数字不能是012，第3个以后的数字任意
         */
        //1. 得到文本框输入的值
        var tel = document.getElementById("tel").value.trim();
        //调用正则表达式的方法，如果字符串匹配正则表达式就返回true，否则就返回false
        return /^1[3456789]\d{9}$/.test(tel);
    }

    document.getElementById("btn").onclick = function () {
        if (checkPhone()) {
            alert("验证通过");
        } else {
            alert("验证失败");
        }
    };
</script>
</body>
</html>
```

## <font color="red">创建正则表达式</font>

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>正则表达式创建</title>
</head>
<body>
<script type="text/javascript">
    //字符串，在JS中默认是模糊匹配
    var str = "1235";
    //方式一：正则表达式，找3个数字(正则表达式是做为字符串参数出现的，可以定义成变量，可以进行字符串拼接，相对更加灵活。但\等字符需要转义。)
    //var reg = new RegExp("^\\d{3}$");

    //方式二：(本身是一个正则表达式对象，\等字符不需要转义。)
    var reg = /^\d{4}$/;
    //test方法用来判断是否匹配，匹配就返回true
    document.write("是否匹配：" + reg.test(str) + "<br/>");
</script>
</body>
</html>
```

### 匹配模式

#### 创建方式

```javascript
//i:忽略大小写
new RegExp("正则表达式","匹配模式")

/正则表达式/匹配模式
```

### 代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>正则表达式匹配模式</title>
</head>
<body>
<script type="text/javascript">
    //创建字符串
    var str = "CAT";
    //创建正则表达式并且指定匹配模式 (Regular Expression 正则表达式)
    //var reg = new RegExp("cat","i");  //忽略大小写

    var reg = /cat/i;  //匹配模式

    //调用test方法判断
    var b = reg.test(str);
    //输出判断结果
    document.write(b + "<br/>");
</script>
</body>
</html>
```

