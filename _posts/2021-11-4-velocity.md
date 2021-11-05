---
layout: post
title: "velocity"
subtitle: "velocity(vm)模板引擎"
categories: 前端
tags: [velocity]
author: "Kid-On-The-Road"
meta: ""

---

## 介绍

Velocity是基于Java的模板引擎，它允许页面设计者引用Java中定义的方法。页面设计者和Java开发者能够同时使用MVC的模式开发网站，这样网页设计者能够把精力放在页面的设计上，程序员也可以把精力放在代码开发上。Velocity把Java代码从Web页面中分离， 使网站可维护性更强，同时也在Java服务器页面(JSPs)或者PHP中提供了可视化交互的选择。

Velocity能够使用模板生成Web页面,  SQL，PostScript 和其他内容。并能够生成的源代码和报表中的一个独立的单元，或者作为一个其他系统的组件。配置完成后，Velocity将提供为[Turbine](http://java.apache.org/turbine/) 页面应用框架提供模板服务。 Velocity+Turbine将提供一个模板服务，它将允许网页应用按照MVC的模式进行开发。

开发者文档[Developer Guide](http://velocity.apache.org/engine/devel/developer-guide.html).

## 依赖

- 引入velocity

```xml
<dependency>
  <groupId>org.apache.velocity</groupId>
  <artifactId>velocity-engine-core</artifactId>
  <version>x.x.x</version>
</dependency>
```

- 在Velocity中引入Logging, SLF4J, Log4j或者服务器logger日志

```xml
<dependency>
  <groupId>org.apache.velocity</groupId>
  <artifactId>velocity-engine-commons-logging</artifactId>
  <version>x.x.x</version>
</dependency>

<dependency>
  <groupId>org.apache.velocity</groupId>
  <artifactId>velocity-engine-slf4j</artifactId>
  <version>x.x.x</version>
</dependency>

<dependency>
  <groupId>org.apache.velocity</groupId>
  <artifactId>velocity-engine-log4j</artifactId>
  <version>x.x.x</version>
</dependency>

<dependency>
  <groupId>org.apache.velocity</groupId>
  <artifactId>velocity-engine-servlet</artifactId>
  <version>x.x.x</version>
</dependency>
```

## 模板语言(VTL)

 *#*字符是VTL语句的开始，但是#字符并没有实际意义。

### 定义及赋值

```javascript
//#：定义值
//$：赋值
#set( $foo = "Velocity" )
//字符串中的变量需要被解析，则最外层用双引号包围
#set($_var1 = "home $foo")
Hello $_var1 World!
//字符串中的变量不能被解析，则最外层用单引号包围
#set($_var2 = 'home $foo')
Hello $_var2 World!
    
//默认情况下使用单引号不解析Velocity中的可用变量(可以通过改变velocity.properties中的stringliterals.interpolate=false配置来改变这种默认设置.)
//#[[]]# 语法可以使包含在其中的语句不被解析
#[[
#foreach ($woogie in $boogie)
  nothing will happen to $woogie
#end
]]#
//显示如下
#foreach ($woogie in $boogie)
  nothing will happen to $woogie
#end
```

### 注释

//单行注释

```javascript
##
```

//多行注释

```javascript
#*
*#
```

//注释块

```javascript
#**
 *
 *#
```

### 引用

#### 变量

```javascript
变量名称开头可以是如下几种：
- alphabetic (a .. z, A .. Z)
- numeric (0 .. 9)
- hyphen (“-“)
- underscore (“_”)
```

```javascript
#set( $foo = "bar" )
```

#### 属性

```javascript
//含义一：$customer.Address查询被customer标识的哈希表并返回和它相关联的Address的值。
//含义二：$customer.Address作为方法引用($customer.Address是$customer.getAddress()的一种缩写形式。)
$customer.Address
```

- 属性调用规则

```javascript
对于小写名字,例如 $customer.address, 调用的顺序是:
getaddress()
getAddress()
get(“address”)
isAddress() 
```

```javascript
对于大写的属性名字像 $customer.Address,调用的顺序是:
getAddress()
getaddress()
get(“Address”)
isAddress()
```

#### 方法

```javascript
//$customer.Address 引用和 $customer.getAddress()方法的引用效果是一样的
$customer.getAddress()
$purchase.getTotal()
$page.setTitle( "My Home Page" )
$person.setAttributes( ["Strange", "Weird", "Excited"] )
```

- 自从Velocity 1.6之后, 所有的数组引用被看成长度固定. 因此可以调用java.util.List方法。

```javascript
$myarray.isEmpty()
$myarray.size()
$myarray.get(2)
$myarray.set(1, 'test')
```

- 在Velocity 1.6支持可变参数方法. 一个方法 `public void setPlanets(String... planets)` 或者甚至是 `public void setPlanets(String[] planets)` 

```javascript
$sun.setPlanets('Earth', 'Mars', 'Neptune')
$sun.setPlanets('Mercury')
$sun.setPlanets()
```

#### 渲染

每一个引用的值(变量，属性，或者方法)都被转换为一个字符串并作为最终的输出。、

```javascript
//Velocity调用它时会调用它的'.toString()'方法转化为字符串
$foo
```

#### 索引标识符

- 使用`$foo[0]` 的符号形式或$foo.get(0)能够访问被定义的索引对象。

```javascript
$foo[0]     
$foo[$i]      
$foo["bar"]

//访问数组
$foo.bar[1].junk
$foo.callMethod()[1]
$foo["apple"][4]
```

- 通过索引来对引用进行赋值,

```javascript
#set($foo[0] = 1)
#set($foo.bar[1] = 3)
#set($map["apple"] = "orange")
```

==注意==：指定的元素被赋值给定的值。Velocity 尝试第一次 ‘set’ 方法在元素上, 然后通过’put’ 来进行赋值.

#### 正式引用标识符

```
${mudSlinger}
${customer.Address}
${purchase.getTotal()}
```

```javascript
#set($vice = "aaa")
//正常引用
$vicemaniac
//输出为
$vicemaniac
//使用正式引用标识符
${vice}maniac
//输出为
$aaamaniac
```

#### 静态引用标识符

```javascript
//$email未被定义输出为$email
<input type="text" name="email" value="$email"/>
    
//使用静态引用标识符标识引用，当变量未被定义时，引用的变量处会替换为空字符串
<input type="text" name="email" value="$!email"/>
    
//正式引用通常和静态引用配合使用
<input type="text" name="email" value="$!{email}"/>
```

### 严格引用模式

Velocity 1.6引入严格引用模式，通过设置Velocity配置属性“runtime.references.strict”为true激活严格引用模式。

```javascript
this is $foo    ## throws an exception because $foo is null
this is $!foo   ## renders to "this is " without an exception
this is $!bogus//bar被定义，foo未定义，此时会报异常
$foo                        
#set($bar = $foo)           
#if($foo == $bar)#end       
#foreach($item in $foo)#end 

//调用不存在的方法或属性会报异常
$bar.bogus          
$bar.foo.bogus      
$bar.retnull.bogus  

//判断引用是否被定义(未与其它值比较)
#if ($foo)#end                  
#if ( ! $foo)#end               
#if ($foo && $foo.bar)#end      
#if ($foo && $foo == "bar")#end 
#if ($foo1 || $foo2)#end       

//严格模式下，#if 指令可以使用 >, <, >=, <= 同时,参数 #foreach必须可以迭代的 (此特性可以在配置文件中通过foreach.skip.invalid修改). 

//调用一个null值将导致异常，可以用 ‘$!’代替 ‘$’, 类似于非严格模式
this is $foo    
this is $!foo   
this is $!bogus
```

### 模式替换

```javascript
$foo
//取值
$foo.getBar()
//或者
$foo.Bar

//赋值
$data.setUser("jon")
//或者
#set( $data.User = "jon" )

//取值
$data.getRequest().getServerName()
//或者
$data.Request.ServerName
//或者
${data.Request.ServerName}
```

### 指令

```javascript
//指令后跟文本需要用{}将指令与其它文本隔开
#if($a==1)true enough#{else}no way!#end

#set( $primate = "monkey" )
#set( $customer.Behavior = $primate )
//左边的(LHS)必须分配一个变量引用或者属性引用. 右边的(RHS)可以是以下类型:
- Variable reference
- String literal
- Property reference
- Method reference
- Number literal
- ArrayList
- Map

//实例举例：
#set( $monkey = $bill ) ## variable reference
#set( $monkey.Friend = "monica" ) ## string literal
#set( $monkey.Blame = $whitehouse.Leak ) ## property reference
#set( $monkey.Plan = $spindoctor.weave($web) ) ## method reference
#set( $monkey.Number = 123 ) ##number literal
#set( $monkey.Say = ["Not", $my, "fault"] ) ## ArrayList
#set( $monkey.Map = {"banana" : "good", "roast beef" : "bad"}) ## Map
//对于定义的ArrayList,可以使用使用$monkey.Say.get(0)访问上面第一个元素
//对于定义的Map,可以通过通过$monkey.Map.get(“banana”) 或$monkey.Map.banana访问上面实例中第一个元素,返回 ‘good’

//右边(RHS)可以使用简单的算术表达式:
#set( $value = $foo + 1 )
#set( $value = $bar - 1 )
#set( $value = $foo * $bar )
#set( $value = $foo / $bar )

//假如右边(RHS)是一个null的属性和方法引用, 它将不能分配给左边(LHS),此机制通常不能移除一个已经存在的引用
#set( $result = $query.criteria("name") )
#set( $result = $query.criteria("address") )
//如果*$query.criteria(“name”)* 返回”bill”,  *$query.criteria(“address”)* 返回null, 上面的脚本将会输出如下内容 :
The result of the first query is bill
The result of the second query is bill
```

### 条件语句

#### If / ElseIf / Else

```javascript
//*#if*指令可以包含一段文本当生成Web网页
//$foo为 true,将输出“Velocity!”。
//$foo有一个 null 值，或者它的布尔值为false,将没有输出。
#if( $foo )
   <strong>Velocity!</strong>
#end

//下面的脚本输出为Go South。
#set( $foo = 15 )
#set( $bar = 6 )
#if( $foo < 10 )
<strong>Go North</strong>
#elseif( $foo == 10 )
<strong>Go East</strong>
#elseif( $bar == 6 )
<strong>Go South</strong>
#else
<strong>Go West</strong>
#end
```

#### 关系和逻辑操作符

字符形式的逻辑运算符*eq*, *ne*, *and*, *or*, *not*, *gt*, *ge*, *lt*, 和*le*.

- ==

```javascript
//Java中==仅仅表示对象是否相等. Velocity中的等号操作符仅仅表示两个数字,字符串,或对象的比较。当两个类对象是不同时, 字符串通过调用`toString()来获取值然后进行比较`.
#set ($foo = "deoxyribonucleic acid")
#set ($bar = "ribonucleic acid")

#if ($foo == $bar)
  In this case it's clear they aren't equivalent. So...
#else
  They are not equivalent and this will be the output.
#end
```

- AND

```javascript
//与java中使用类似
#if( $foo && $bar )
   <strong> This AND that</strong>
#end
```

- OR

```javascript
//与java中使用类似
#if( $foo || $bar )
    <strong>This OR That</strong>
#end
```

- !

```javascript
//与java中使用类似
#if( !$foo )
  <strong>NOT that</strong>
#end
```

### 循环

-  #foreach

```javascript
//#foreach循环将把 $allProducts列表里面的值赋值给products . 每次遍历, $allProducts*里面的值会赋值给$product.
//$allProducts变量的内容可以是一个数组, Hashtable 或者 Array. 分配给$product变量的值可以是Java的对象和一个变量的引用. 如果$product是Java里面一个真实的Product类, 那么它的名字可以引用$product.Name/$Product.getName()方法
<ul>
#foreach( $product in $allProducts )
    <li>$product</li>
#end
</ul>
```

- 引用Hashtable 里面的key:

```javascript
<ul>
#foreach( $key in $allProducts.keySet() )
    <li>Key: $key -> Value: $allProducts.get($key)</li>
#end
</ul>
```

- 循环计数:

```javascript
<table>
#foreach( $customer in $customerList )
    <tr><td>$foreach.count</td><td>$customer.Name</td></tr>
#end
</table>
```

- 判断是否是最后一次迭代 :

```javascript
//如果想从0开始循环,需要用$foreach.index代替$foreach.count.
//$foreach.first,$foreach.last与$foreach.hasNext有类似的作用.
//可以通过 $foreach.parent或 $foreach.topmost 属性/$foreach.parent.index 或者 $foreach.topmost.hasNext)访问 #foreach外面的这些属性,.
#foreach( $customer in $customerList )
    $customer.Name#if( $foreach.hasNext ),#end
#end
```

- 设置循环次数

```javascript
//默认情况下没有设置,可以在velocity.properties配置文件里进行更改
directive.foreach.maxloops = -1
```

- 停止循环

```javascript
//通过#break指令停止循环:
## list first 5 customers only
#foreach( $customer in $customerList )
    #if( $foreach.count > 5 )
        #break
    #end
    $customer.Name
#end
```

### 引入

```javascript
//引入一个本地文件,文件内容不会经过模板引擎处理,引入的文件必须要放在根目录下
#include( "one.txt" )

//引入多个文件需用逗号隔开
#include( "one.gif","two.txt","three.htm" )

//不需要通过名字引用文件,通常使用一个变量来代替文件名
#include( "greetings.txt", $seasonalstock )
```

### 解析

```javascript
//#parse*脚本可以引用一个包含脚本的本地文件。文件内容会经过模板引擎处理,文件必须放在根目录下
#parse( "me.vm" )

//#parse脚本可以嵌套引用包含#parse的模板,准许递归调用,默认为10,可以通过`velocity.properties` 中directive.parse.max.depth来自定义设置单个文件中*#parse*引用文件个数
Count down.
#set( $count = 8 )
#parse( "parsefoo.vm" )
All done with dofoo.vm!
    

```

```javascript
//parsefoo.vm模板
$count
#set( $count = $count - 1 )
#if( $count > 0 )
    #parse( "parsefoo.vm" )
#else
    All done with parsefoo.vm!
#end
```

### Break

- #break 仅仅停止的是循环内部, 作用域内部, 而不是整个程序.

- 如果想停止一个正在执行的作用域, 可以使用某个作用域($foreach, $template, $evaluate, $define, $macro, or $somebodymacro)作为参数,如#break($macro)). 

- 通过 #break($foreach.parent)/#break($macro.topmost))访问父类

### Stop指令

*#stop* 指令停止任何正在执行的输出.

### Evaluate指令

*#evaluate*指令用来动态的计算。它可以在加载的时候适时计算一个字符串. 

```javascript
#set($source1 = "abc")
#set($select = "1")
#set($dynamicsource = "$source$select")
#evaluate($dynamicsource) 
//输出为abc,相当于将$source$select拼接为$source1
```

### Define指令

*#define*指令可以指定对某一个脚本片段的引用.

```javascript
#define( $block )Hello $who#end
#set( $who = 'World!' )
$block
//输出为
Hello World!
```

### 宏调用

*#macro* 脚本用于定义一个可重用的模板片段. 

- 直接调用宏(#d())

```javascript
#macro( d )
<tr><td></td></tr>
#end

#d()
```

- 替换#d()

```javascript
#macro( d )
<tr><td>$!bodyContent</td></tr>
#end
//名字前加#@名字后加一个内容体,并#end调用, $!bodyContent处会被替换为Hello!
#@d()Hello!#end
//直接调用将显示一个空的单元格.
#d()
```

- 参数

```javascript
//Velocimacro也可以携带许多参数 
//Velocimacro中可以放入函数体.
#macro( tablerows $color $somelist )
#foreach( $something in $somelist )
    <tr><td bgcolor=$color>$something</td></tr>
#end
#end

//调用#tablerows(例1)
#set( $greatlakes = ["Superior","Michigan","Huron","Erie","Ontario"] )
#set( $color = "blue" )
<table>
    #tablerows( $color $greatlakes )
</table>
//*$greatlakes* 代替 *$somelist*. 当 *#tablerows*被调用时, 将输出以下内容:
<table>
    <tr><td bgcolor="blue">Superior</td></tr>
    <tr><td bgcolor="blue">Michigan</td></tr>
    <tr><td bgcolor="blue">Huron</td></tr>
    <tr><td bgcolor="blue">Erie</td></tr>
    <tr><td bgcolor="blue">Ontario</td></tr>
</table>

//调用#tablerows(例2)
#set( $parts = ["volva","stipe","annulus","gills","pileus"] )
#set( $cellbgcol = "#CC00FF" )
<table>
#tablerows( $cellbgcol $parts )
</table>
//输出内容
<table>
    <tr><td bgcolor="#CC00FF">volva</td></tr>
    <tr><td bgcolor="#CC00FF">stipe</td></tr>
    <tr><td bgcolor="#CC00FF">annulus</td></tr>
    <tr><td bgcolor="#CC00FF">gills</td></tr>
    <tr><td bgcolor="#CC00FF">pileus</td></tr>
</table>
```

- Velocimacros可以携带下面的VTL元素作为参数 :

```javascript
- Reference : anything that starts with ‘$’
- String literal : something like “$foo” or ‘hello’
- Number literal : 1, 2 etc
- IntegerRange : [ 1..2] or [$foo .. $bar]
- ObjectArray : [ “a”, “b”, “c”]
- boolean value true
- boolean value false
```

当传递一个引用作为Velocimacros的参数时(需要通过名字传递). 可以传递一个方法的调用引用在方法中也可以使用方法调用.

```javascript
#macro( callme $a )
    $a $a $a
#end

#callme( $foo.bar() )
//在方法中 bar() 的结果将被调用三次.

//如果你不想使用这个特性,你就想从一个引用的方法中获取值,你可以这样做 :
#set( $myval = $foo.bar() )
#callme( $myval )
```

### 配置

在velocity的发布方包中有一个velocity.properties（位于    org.apache.velocity.runtime.defaults package下，
文件定义了velocity的配置信息org.apache.velocity.runtime.RuntimeConstants中定义了key值）

```properties
#模板编码：
input.encoding=ISO-8859-1//模板输入编码
output.encoding=ISO-8859-1 //模板输出编码

#foreach配置
directive.foreach.counter.name= velocityCount //计数器名称
directive.foreach.counter.initial.value = 1 //计数器初始值
directive.foreach.maxloops = -1 //最大循环次数，-1为默认不限制 directive.foreach.iterator.name = velocityHasNex //迭代器名称

#set配置
directive.set.null.allowed = false //是否可设置空值

#include配置
directive.include.output.errormsg.start= <!-- include error : //错误信息提示开始字符串
directive.include.output.errormsg.end = see error log --> //错误信息提示结束字符串

#parse配置
directive.parse.max.depth = 10 //解析深度

#模板加载器配置
resource.loader = file //模板加载器类型，默认为文件，可定义多个
file.resource.loader.description= Velocity File Resource Loader //加载器描述
file.resource.loader.class =Velocity.Runtime.Resource.Loader.FileResourceLoader //加载器类名称
file.resource.loader.path = . //模板路径
file.resource.loader.cache = false //是否启用模板缓存
file.resource.loader.modificationCheckInterval = 2 //检查模板更改时间间隔

#宏配置
velocimacro.library//指定宏定义文件的位置
velocimacro.permissions.allow.inline= true //是否可以行内定义
velocimacro.permissions.allow.inline.to.replace.global = false //是否可以用行内定义代替全局定义
velocimacro.permissions.allow.inline.local.scope = false //行内定义是否只用于局部
velocimacro.context.localscope= false //宏上下文是否只用于局部
velocimacro.max.depth = 20 //解析深度
velocimacro.arguments.strict= false //宏参数是否启用严格模式

#资源管理器配置
resource.manager.class= Velocity.Runtime.Resource.ResourceManagerImpl //管理器类名称
resource.manager.cache.class = Velocity.Runtime.Resource.ResourceCacheImpl //缓存器类名称

#解析器池配置
parser.pool.class= Velocity.Runtime.ParserPoolImpl //解析池类名称
parser.pool.size = 40 //初始大小

#evaluate配置
directive.evaluate.context.class= Velocity.VelocityContext //上下问类名称

#可插入introspector配置
runtime.introspector.uberspect = Velocity.Util.Introspection.UberspectImpl //默认introspector类名称

#日志配置
runtime.log  =  velocity.log

#用以指定 Velocity 运行时日志文件的路劲和日志文件名，如不是全限定的绝对路径,系统会认为想对于当前目录.
runtime.log.logsystem

#这个参数没有默认值，它可指定一个实现了org.apache.velocity.runtime.log.LogSystem.接口的自定义日志处理对象给 Velocity。这就方便将 Velocity 与你己有系统的日志机制统一起来
runtime.log.logsystem.class=  org.apache.velocity.runtime.log.AvalonLogSystem

#上面这行，是一个示例来指定一个日志记录器.
runtime.log.error.stacktrace=  false
runtime.log.warn.stacktrace=  false
runtime.log.info.stacktrace=  false

#这些是错误消息跟踪的开关.将会生成大量、详细的日志内容输出.
runtime.log.invalid.references=  true

#当一个引用无效时，打开日志输出.  在生产系统运行中，这很有效，也是很有用的调试工具.
```

### 获取字面量

#### 通用

VTL 标识符一直都是以大写或者小写的字母开始的, 所以 $2.50 不会被错误引用.

#### 屏蔽VTL中的引用

```javascript
//定义$email
#set( $email = "foo" )
```

|               | 语法         | 值        |
| ------------- | ------------ | --------- |
| 输出正确值    | $email       | foo       |
| 输出$email    | \\$email     | $email    |
| 输出\\foo     | \\\\$email   | \\foo     |
| 输出\\\$email | \\\\\\$email | \\\$email |

```javascript
//Velocity定义的引用不同于那些没有定义的引用 . 本实例中$foo定义值为gibbous.
#set( $foo = "gibbous" )
$moon = $foo
//输出结果为: $moon = gibbous — $moon将作为字符输出而$foo的地方将输出gibbous.
```

#### 转义不可用VTL引用

```javascript
//不想把${my:invalid:non:reference}当做引用
//屏蔽 `$` 或 `#`
#set( $D = '$' )
${D}{my:invalid:non:reference}
//使用[VelocityTools](http://velocity.apache.org/tools/devel/), 使用EscapeTool屏蔽:
${esc.d}{my:invalid:non:reference}
```

#### 转义VTL指令

- 通过反斜杠(“\”)字符屏蔽 VTL 指令

```javascript
## #include( "a.txt" ) renders as <contents of a.txt>
#include( "a.txt" )

## \#include( "a.txt" ) renders as #include( "a.txt" )
\#include( "a.txt" )

## \\#include ( "a.txt" ) renders as \<contents of a.txt>
\\#include ( "a.txt" )
```

- 一个单独的指令中包含多个脚本元素VTL 指令的转义. 

```javascript
#if( $jazz )
    Vyacheslav Ganelin
#end
//如果 *$jazz*为 true, 输出结果为Vyacheslav Ganelin,如果*$jazz* 为false,这里没有任何输出.

//屏蔽指令
\#if( $jazz )
    Vyacheslav Ganelin
\#end
//它将导致指令被忽略, 但是变量 *$jazz* 正常显示. 所以, 如果*$jazz* 为 true,输出结果是
 #if( true )
     Vyacheslav Ganelin
 #end
 
//如果脚本之前的元素被反斜杠转义:
 \\#if( $jazz )
   Vyacheslav Ganelin
\\#end
//如果*$jazz* 为 true,输出为
\ Vyacheslav Ganelin\
```

### 格式化问题

```javascript
//格式一
#set( $imperial = ["Munetaka","Koreyasu","Hisakira","Morikune"] )
#foreach( $shogun in $imperial )
    $shogun
#end
//格式二
#set($foo=["$10 and ","a pie"])#foreach($a in $foo)$a#end

#set( $foo = ["$10 and ","a pie"] )
#foreach( $a in $foo )
$a
#end
//格式三
#set($foo       = ["$10 and ","a pie"])
                 #foreach           ($a in $foo )$a
         #end
//以上三种格式输出结果一样
```

### 其他的特性和杂记

#### 算术操作

加减乘数的使用:

```javascript
#set( $foo = $bar + 3 )
#set( $foo = $bar - 4 )
#set( $foo = $bar * 6 )
#set( $foo = $bar / 2 )
```

求模运算符 (*%*),当两个整数相除时,结果是整数, 小数部分被丢弃:

```javascript
#set( $foo = $bar % 5 )
```

#### 范围操作符

范围操作符能够结合着 *#set* 和 *#foreach* 语句使用. 用它能够产生一个整数数组,语法结果如下:

```javascript
[n..m]
```

产生一个n到m的整数. 不论m大于或者小于n都不重要;在这个实例中这个范围就是简单的计算.

```javascript
//范围操作符的使用:
//第一个实例:
#foreach( $foo in [1..5] )
$foo
#end

//第二个实例:
#foreach( $bar in [2..-2] )
$bar
#end

//第三个实例:
#set( $arr = [0..1] )
#foreach( $i in $arr )
$i
#end

//第四个实例:
[1..3]
//输出结果为:
First example:
1 2 3 4 5

Second example:
2 1 0 -1 -2

Third example:
0 1

Fourth example:
[1..3]
```

### 高级问题:转义和!

```javascript
//当一个引用前面加上*!* 字符和*!* 字符前面加上一个 *\* 转义字符
#set( $foo = "bar" )
$\!foo
$\!{foo}
$\\!foo
$\\\!foo
//输出结果为:
$!foo
$!{foo}
$\!foo
$\\!foo

//正规 *\* 优先*$*的转义:
\$foo
\$!foo
\$!{foo}
\\$!{foo}
//输出结果为:
$foo
$!foo
$!{foo}
\bar
```

### 字符串的拼接

```javascript
#set( $size = "Big" )
#set( $name = "Ben" )
//输出结果为 ‘BigBen’. 
$size$name


//拼接字符串并传递给一个方法或定义一个新的引用
#set( $size = "Big" )
#set( $name = "Ben" )
#set($clock = "$size$name" )
//输出结果为 ‘BigBen’. 
$clock.

//在拼接中使用正式引用(正式引用解析时能够把 ‘$size’ 和’$sizeTall’ 通过 ‘{}’ 进行区分开.)
#set( $size = "Big" )
#set( $name = "Ben" )
#set($clock = "${size}Tall$name" )
//输出结果为‘BigTallBen’
$clock.
```

























