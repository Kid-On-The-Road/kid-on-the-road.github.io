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

 当一个用户访问页面时,Velocity模板 将在你的Web页面中搜索所有的*#*字符, 然后认为它是VTL语句的开始，但是#字符并没有实际意义。

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
    
//默认情况, 这种特征使用单引号不解析Velocity中的可用变量. 你也可以通过改变velocity.properties  中的stringliterals.interpolate=false配置来改变这种默认设置.或者,  #[[don’t parse me!]]# 语法准许模板设计者很容易的使用大量的语句块,而这些语句块中的变量不会被解析. 它特别有用尤其在避免有大量的指令上地方或者其他无效的内容(不想被解析的)VTL.
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

```tex
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
//$customer.Address查询被customer 标识的哈希表返回和它相关联的Address 的值。
//$customer.Address也能被一个方法引用;($customer.Address是$customer.getAddress()的一种缩写形式。)
$customer.Address
$purchase.Total
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

- 自从Velocity 1.6, 所有的数组引用被看这固定长度列表. 这意味着你能够调用java.util.Lis方法在数组引用。所以， 假如你有一个引用在数组上 ( 假定这里有一个字符数组后三个字)，你能够这样做:

```javascript
$myarray.isEmpty()
$myarray.size()
$myarray.get(2)
$myarray.set(1, 'test')
```

- 在Velocity 1.6支持可变参数方法. 一个方法 `public void setPlanets(String... planets)` 或者甚至是 `public void setPlanets(String[] planets)` (假如你使用Java 5 JDK), 现在可以接受任何数量的参数时调用的模板.

```javascript
$sun.setPlanets('Earth', 'Mars', 'Neptune')
$sun.setPlanets('Mercury')
$sun.setPlanets()
```

#### 渲染

每一个引用的值(变量，属性，或者方法)都被转换为一个字符串并作为最终的输出。假如这里有一个对象表示为*$foo* (例如一个整数对象), 当Velocity调用它时，Velocity会调用它的`.toString()` 方法转化为字符串.

#### 索引标识符

- 使用`$foo[0]` 的符号形式能够访问被定义的索引对象。这个形式和通过get调用一个对象是相同的例如`$foo.get(0)`, 提供了一种简单的语法操作。

```javascript
$foo[0]     
$foo[$i]      
$foo["bar"]
```

- 这相同的语法也能够使用在Java数组上因为由于Velocity封装了数组在访问对象上提供了一个`get(Integer)方法,它能返回一个特殊的元素。`相同的语法可以在任何`.get的地方使用，`例如:

```javascript
$foo.bar[1].junk
$foo.callMethod()[1]
$foo["apple"][4]
```

- 一个引用也能够通过索引来进行赋值, 例如:

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
//如果你构建一个语句*$vice*被使用作为一个基础语句的单词。它的目的允许有人选择基础单词产生这种结果: “Jack is a pyromaniac.” 或者 “Jack is a kleptomaniac.”。使用简写标识符将不满足这种需求。
//它是含糊不清的, Velocity认为它是*$vicemaniac*, 而不是*$vice*. 发现变量*$vicemaniac，*没有赋值，它将返回 *$vicemaniac*.
Jack is a $vicemaniac.
//使用正式标识符能够解决这种问题,现在Velocity能够识别$vice, 而不误认为$vicemaniac. 正式引用经常被使用在引用指向邻近文本的模板中.
Jack is a ${vice}maniac.
```

#### 静态引用标识符

- 当Velocity遇到一个没有定义的引用时，正常的是输出图像引用. 例如, 假如下面的引用是VTL模板的一部分.

```javascript
<input type="text" name="email" value="$email"/>
```

- 当它初始化时, 变量 *$email*应用并没有值, 但是你宁愿”$email”是一个空白文本字段 . 使用静态引用标识符避免这种正规的行为; 通过在你的VTL模板中使用*$!email*代替$email。上面的实例可以改成下面这种形式:

```javascript
<input type="text" name="email" value="$!email"/>
```

- 现在当初始化时如果*$email*没有值, 一个空的字符串将输出代替”$email”。

- 正式应用和静态引用经常一起使用，就像下面实例一样.

```javascript
<input type="text" name="email" value="$!{email}"/>
```

==注意==：正式应用和静态引用经常一起使用，就像下面实例一样.

```javascript
<input type="text" name="email" value="$!{email}"/>
```

### 严格引用模式

Velocity 1.6引入严格引用模式，通过设置Velocity配置属性“runtime.references.strict”为true激活严格引用模式。

- 下面的实例中 $bar被定义了但是 $foo却没有被定义,所有这些语句将抛出异常:

```javascript
$foo                        
#set($bar = $foo)           
#if($foo == $bar)#end       
#foreach($item in $foo)#end 
```

- 调用一个并不存在的方法或属性时，也会产生异常。在下面的实例中 $bar对象定义一个属性 ‘foo’ 返回一个字符串 , ‘retnull’ 将返回null.

```javascript
$bar.bogus          
$bar.foo.bogus      
$bar.retnull.bogus  
```

- 一个引用使用 #if 或者#elseif 指令没有任何方法或属性,假如它并没有和其他值进行比较,这种引用是准许的.这种方式通常用来判断一个引用是否被定义. 在下面的实例中$foo 并没有定义但是它也不会抛异常.

```javascript
#if ($foo)#end                  
#if ( ! $foo)#end               
#if ($foo && $foo.bar)#end      
#if ($foo && $foo == "bar")#end 
#if ($foo1 || $foo2)#end        
```

- 严格模式在 #if 指令中可以使用 >, <, >= or <=. 同时,参数 #foreach必须可以迭代的 (这种特性可以被属性指令.foreach.skip.invalid修改). 不过,在严格模式下没有定义的引用也将抛异常。

- Velocity试图调用一个null值将导致异常. 对于简单的调用在这个实例中你可以用 ‘$!’代替 ‘$’, 这种类似于非严格模式。请记住，当你使用严格引用调用不存在的变量时会出现异常。例如, 下面的$foo 在上下文中值为null

```javascript
this is $foo    ## throws an exception because $foo is null
this is $!foo   ## renders to "this is " without an exception
this is $!bogus ## bogus is not in the context so throws an exception
```

### 模式替换

```javascript
$foo
//取值
$foo.getBar()
## 也可以写成
$foo.Bar
//赋值
$data.setUser("jon")
## 也可以写成
#set( $data.User = "jon" )
//取值
$data.getRequest().getServerName()
## 也可以写成
$data.Request.ServerName
## 也可以写成
${data.Request.ServerName}
```

### 指令

- 指令一直以 `#开始`. 像引用一样,指令的名字可能是相等的通过`{` 和 `}` 符号. 这是好的方式在指令后跟文本. 例如下面的程序有一个错误:

```javascript
#if($a==1)true enough#elseno way!#end
//在这个实例中, 使用方括号把'#else'与其他行分开.
#if($a==1)true enough#{else}no way!#end
```

- *#set* 指令被用来设定一个引用的值. 这个值能够被分配一个变量引用或者属性引用,这种情况发生在括号中, 如下实例:

```javascript
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

//注意: 对于定义的ArrayList 实例元素可以使用ArrayList 类里面定义的方法, 例如，访问上面第一个元素使用$monkey.Say.get(0).相似的, 对于Map实例, 元素通过 { } 操作符来定义你能够使用Map类中定义的方法. 例如, 访问上面实例中第一个元素通过$monkey.Map.get(“banana”) 并且返回 ‘good’, 甚至可以使用 $monkey.Map.banana来返回一样的值.
//RHS也能使用简单的算术表达式:
#set( $value = $foo + 1 )
#set( $value = $bar - 1 )
#set( $value = $foo * $bar )
#set( $value = $foo / $bar )

//假如RHS是一个null的属性和方法引用, 它将不能分配给LHS.
#set( $result = $query.criteria("name") )
The result of the first query is $result
#set( $result = $query.criteria("address") )
The result of the second query is $result
//如果*$query.criteria(“name”)* 返回”bill”,  *$query.criteria(“address”)* 返回null, 上面的 VTL将输出如下内容 :
The result of the first query is bill
The result of the second query is bill
```

### 条件语句

#### If / ElseIf / Else

Velocity中 *#if* 指令可以包含一段文本当生成Web网页时,例如:

```javascript
//假如 $foo 为 true, 它将输出为: “Velocity!”。相反的, 假如 $foo 有一个 null 值，或者它的布尔值为false, 这个语句的结果为false,这里将没有输出。
#if( $foo )
   <strong>Velocity!</strong>
#end

//下面这个实例中, $foo大于10，所以第一个两个比较是false。下一个$bar和6相等, 所以显示true, 所以输出 Go South。
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

这里也有字符形式的逻辑运算符如 *eq*, *ne*, *and*, *or*, *not*, *gt*, *ge*, *lt*, 和*le*.

- ==

```javascript
//Velocity 使用等号决定两个变量之间的关系.
//注意 *==* 语法和Java中的语法是不同,Java中==仅仅表示对象是否相等. Velocity中的等号操作符仅仅表示两个数字,字符串,或对象的比较。当两个类对象是不同时, 字符串是通过调用`toString()来获取的然后来比较`.
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
//*#if()* 指令结果为true 假如 *$foo* 和*$bar*都为true. 如果 *$foo*为false,表达式的结果为 false; *$bar*将不会计算. 如果 *$foo* 为 true,Velocity模板将计算*$bar*的值; 如果 *$bar*为 true, 然后整个表达式为true输出 **This AND that** . 如果 *$bar*为 false,如果表达式为false这里将没有输出.
#if( $foo && $bar )
   <strong> This AND that</strong>
#end
```

- OR

```javascript
//如果*$foo*为 true, Velocity模板不需要计算*$bar*; 不管*$bar* 是否为 true 或 false, 这整个表达式为true,**This OR That** 将被输出. 如果 *$foo* 为 false, 然而, *$bar*必须需要计算. 在这个实例中, 如果 *$bar* 也为 false,这表达式结果为 false 这里没有任何输出. 另一方面, 如果*$bar* 为 true, 然而整个表达式为true, 输出的结构是 **This OR That**
#if( $foo || $bar )
    <strong>This OR That</strong>
#end
```

- NOT

```javascript
//这里, 如果*$foo*为 true, 然后*!$foo*计算结果为false,这里没有输出。如果 *$foo*为 false, 然而 *!$foo*计算结果为true 输出结果为 **NOT that** . 注意不要把它和静态引用 *$!foo* which混淆，它们是不同的。*（ifeve.com校对注：一个!在前，一个在后）*
#if( !$foo )
  <strong>NOT that</strong>
#end
```

==注意==：当你希望在*#else* 指令后面包含一个文本你需要把else放在一个大括号 里面来表示它与后面的文本是不同的. (任何指令都能被放在括号里面, 通常用在*#else*中).

```javascript
#if( $foo == $bar)it's true!#{else}it's not!#end</li>
```

### 循环

-  #foreach

```javascript
//*#foreach*循环将把 *$allProducts*列表里面的值赋值给products . 每次遍历, *$allProducts* 里面的值将赋值给*$product*.
//*$allProducts* 变量的内容是一个数组, Hashtable 或者 Array. 分配给*$product* 变量的值是Java的对象和一个变量的引用. 例如, 假如 *$product*是Java里面一个真实的Product类, 它的名字能够被引用 *$product.Name* 方法(ie: *$Product.getName()*).
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
//如果你想从零开始的#foreach循环, 你可以使用 $foreach.index 代替$foreach.count.
//$foreach.first 和 $foreach.last 也提供了$foreach.hasNext方式.
//访问 #foreach外面的这些属性, 你能够引用它们通过 $foreach.parent或 $foreach.topmost 属性 (e.g. $foreach.parent.index 或者 $foreach.topmost.hasNext).
#foreach( $customer in $customerList )
    $customer.Name#if( $foreach.hasNext ),#end
#end
```

- 设置循环次数

```javascript
//默认情况下没有设置 (可以指定一个值 0 或者更小的), 可以设置一个数字在`velocity.properties` 的配置文件里面. This is useful as a fail-safe.
# The maximum allowed number of loops.
directive.foreach.maxloops = -1
```

- 停止循环

```javascript
//停止一个foreach 循环在你的模板中, 你可以使用 #break指令在任何时候停止循环:
## list first 5 customers only
#foreach( $customer in $customerList )
    #if( $foreach.count > 5 )
        #break
    #end
    $customer.Name
#end
```

### 引入

- *#include*脚本元素准许设计者引入一个本地文件, 然后插入到你#include 指令所在的地方。文件的内容不经过模板引擎处理. 由于安全的原因,这个文件仅仅能够放在 TEMPLATE_ROOT(根目录)下面.

```javascript
#include( "one.txt" )
```

* #include* 指定指向的文件放在括号之内. 假如包含多个文件,通过逗号进行分开.

```javascript
#include( "one.gif","two.txt","three.htm" )
```

- 被引用的文件不需要通过名字引用; 实际上，通常使用一个变量来代替文件名。当你请求输出标准页面时非常方便。下面实例展示了文件名和变量.

```javascript
#include( "greetings.txt", $seasonalstock )
```

### 解析

- *#parse*脚本元素准许模板设计者引用一个包含VTL的本地文件。Velocity将解析其中的VTL并输出里面的元素。

```javascript
#parse( "me.vm" )
```

-  *#parse*可以被看着携带一个变量而不是模板. 任何被 *#parse* 指令引用的模板必须放在TEMPLATE_ROOT(根目录)下面. 不像 *#include*指令, *#parse* 仅仅携带了一个参数.

- VTL模板中*#parse*应用的文件能够够嵌套引用包含*#parse*的模板. 默认为 10, 用户可以通过`velocity.properties` 中directive.parse.max.depth来自定义设置单个文件中*#parse*引用文件个数. (注意: 如果 `velocity.properties`文件中*directive.parse.max.depth*没有设置, Velocity默认为10.) 准许递归调用, 例如,如果`dofoo.vm` 模板包含下面的语句:

```javascript
Count down.
#set( $count = 8 )
#parse( "parsefoo.vm" )
All done with dofoo.vm!
```

- 如果你引用`parsefoo.vm模板`, 它可以包含下面的VTL文件:

```javascript
$count
#set( $count = $count - 1 )
#if( $count > 0 )
    #parse( "parsefoo.vm" )
#else
    All done with parsefoo.vm!
#end
```

“Count down.” 之后的被显示, Velocity能够解析`parsefoo.vm`, 把count设置为8. 当count大于0, 它将显示 “All done with parsefoo.vm!” . 本实例中, Velocity将返回 `dofoo.vm` 并输出 “All done with dofoo.vm!” 语句.

### Break

*#break*指令停止任何正在执行的作用域中的输出. 执行作用域是本质上是 with content (i.e. #foreach, #parse, #evaluate, #define, #macro, 或者 #@somebodymacro) 或者 任何”root” 作用域(例如. template.merge(…), Velocity.evaluate(…) or velocityEngine.evaluate(…)). 不像#stop, #break 它仅仅停止的是循环内部, 作用域内部, 而不是整个程序.

如果你希望停止一个正在执行的作用域, 你可以使用作用域控制引用(例如. $foreach, $template, $evaluate, $define, $macro, or $somebodymacro) 作为一个参数#break. (例如. #break($macro)). 它将停止输出所有的到指定的一个. 在同一类型的嵌套范围内, 你能够访问它的父亲通过 $<scope>.parent 或者 $<scope>.最高的和传递这些到#break 代替(例如. #break($foreach.parent) o或者 #break($macro.topmost)).

### Stop指令

*#stop* 指令停止任何正在执行的输出。这是真实的即使嵌套另一个模板通过 #parse 指令或者位于一个velocity macro. 合并输出将包括所有的内容到遇到 #stop 指令的位置. 它是很方便的随时终止模板解析.出入调试的目的, 你可以提供一个将被写到stop命令执行前日志 (DEBUG 级别, 当然是)消息参数 (例如. #stop(‘$foo 并不在内容中’) ).

### Evaluate指令

*#evaluate*指令用来动态的计算。它可以在加载的时候适时计算一个字符串. 例如一个字符串可能被用来国家化或者包括一部分数据库模板.

下面的实例将显示`abc`.

```javascript
#set($source1 = "abc")
#set($select = "1")
#set($dynamicsource = "$source$select")
## $dynamicsource is now the string '$source1'
#evaluate($dynamicsource) //相当于将$source$select拼接为$source1
```

### Define指令

*#define*指令可以指定对VTL一个块的引用.

下面的实例将显示: `Hello World!`.

```javascript
#define( $block )Hello $who#end
#set( $who = 'World!' )
$block
```

### 宏调用

*#macro* 脚本元素准许模板设计者定义一个可重用的VTL模板片段. Velocimacros(宏调用)被广泛用在简单和复杂的场景中.Velocimacro可以用来保存用户的点击次数和最少的板式错误, 提供一个简单的概念介绍。

Velocimacros能够定义在Velocity模板的行内，意味着在同一个网页上它不可以使用其他的Velocity模板。定义一个Velocimacro并在所有模板中共享,这使它具有明显的优势: 它避免了在各个页面中重复定义Velocimacro, 减少工作量并且可以避免错误, 这种也可以通过改变一个地方而达到其他地方一起修改的目的.

- 直接调用宏(#d())

```javascript
#macro( d )
<tr><td></td></tr>
#end
//上个实例中Velocimacro被定义为*d*, 它可以像其他VTL方式一样被调用:
#d()
```

- 替换#d()

```javascript
#macro( d )
<tr><td>$!bodyContent</td></tr>
#end
//名字之前需要加上#@ 加上一个内容体,同时以#end调用, 当Velocity加载时遇见 $!bodyContent会进行显示:
#@d()Hello!#end
//下面的调用方式将一直显示一个空的单元格.
#d()
```

- 参数

```javascript
//Velocimacro也可以携带许多参数 — 甚至是不带参数, 如同第一个实例中, 参数是可选项– 但是当Velocimacro执行时, 它必须调用和你定义的方法的参数匹配. 被执行的Velocimacros要多于上面定义的. 下面实例所示一个Velocimacro携带两个参数一个是color和一个数组.
//任何可以被放到VTL模板中都可以作为Velocimacro的函数体.  *tablerows* 是Velocimacro的一个 *foreach*语句. 这里有两个 *#end*语句被定义在*#tablerows*中; 第一个是属于 *#foreach*, 第二个是属于Velocimacro .
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

- **Velocimacro Arguments**Velocimacros可以携带下面的VTL元素作为参数 :

```javascript
- Reference : anything that starts with ‘$’
- String literal : something like “$foo” or ‘hello’
- Number literal : 1, 2 etc
- IntegerRange : [ 1..2] or [$foo .. $bar]
- ObjectArray : [ “a”, “b”, “c”]
- boolean value true
- boolean value false
```

当传递一个引用作为Velocimacros的参数时,注意引用是通过名字传递的. 这意味着它们的值是在Velocimacro中已经生成了. 这个特性准许你传递一个方法的调用引用在方法中也可以使用方法调用. 例如, 当我们调用下面的Velocimacro将显示

```
     #macro( callme $a )
         $a $a $a
     #end

     #callme( $foo.bar() )
```

在方法中 bar() 的结果将被调用三次.

第一次看到这个特性会发现很惊奇, 当你仔细的思考Velocimacros背后的动机–消除VTL中公共的重复使用 –它变的有意义. 它准许你做一些事情,比如传递一个对象的状态, 例如在Velocimacro中重复生成有颜色的表格对象.

如果你不想使用这个特性,你就想从一个引用的方法中获取值,你可以这样做 :

```
     #set( $myval = $foo.bar() )
     #callme( $myval )
```

**Velocimacro Properties**在 `velocity.properties` 文件中准许灵活的实现Velocimacros. 这里也提供了开发者文档[Developer Guide](http://velocity.apache.org/engine/devel/developer-guide.html).

`velocimacro.library` – 一个通用的和其他依赖包分开的 Velocimacro模板依赖包. 默认, Velocity看起来想一个单独的 函数库: *VM_global_library.vm*. 配置模板的路径用来使用找到Velocimacro 函数库.

`velocimacro.permissions.allow.inline` – 这个属性的值可以是true或者false, 决定是否可以在模板中定义Velocimacros. 默认情况是, true, 准许模板设计者可以自行定义Velocimacros.

`velocimacro.permissions.allow.inline.to.replace.global` -它的值可以设定为true或者false, 这个设置准许用户指定一个模板中定义的Velocimacro能代替全局定义, 它在启动的时候被 `velocimacro.library属性`加载. 默认是, `false`, 避免在启动时候模板中定义的Velocimacros成为全局Velocimacros.

`velocimacro.permissions.allow.inline.local.scope` – 这个属性可能值为true 或者 false, 默认为 false, 控制 定义的Velocimacros对定义中的模板是可见的.简而言之, 如果这个属性设置为 true, 一个模板能够定义能够被定义的模板使用的VMs内 . You can use this for fancy VM tricks – if a global VM calls another global VM, 在行内的作用域内, 一个模板能够定义一个私有的实现第二个VM,它能被第一个VM调用. 但是对其他模板没有影响.

`velocimacro.library.autoreload` – 这个属性控制Velocimacro依赖包自动加载. 这个默认是的是`false`.当把属性设置为 `true,`当Velocimacro被执行时它将检查Velocimacro是否改变, 它重载很有必要的.它准许你改变和测试Velocimacro 不需要重庆你的应用和服务器容器, 仅仅像你可以用普通的模板. 这个模式需要关闭缓存才起作用(e.g.`file.resource.loader.cache = false` ). 这个特征主要用于开发模式, 而不是生产模式.

### 获取字面量

VTL使用了特殊字符,例如 *$* 和 *#*, 做为关键字, 所以一些使用者关注在模板中怎么使用这些字符.这章将讨论转义字符 .

**Currency(通用)**
你这样写是没有问题的 “I bought a 4 lb. sack of potatoes at the farmer’s market for only $2.50!” 像上面提到的一样, VTL 标识符一直都是以大写或者小写的字母开始的, 所以 $2.50 不会被错误引用.

**Escaping Valid VTL References(屏蔽VTL中的引用)**
你可能遇到这种情况,在Velocity中不想有一个引用输出. 屏蔽特殊的字符是输出特殊字符的最好的方式, 你可以使用反斜杠字符,当遇见这些特殊的字符是VTL引用的一部分时. [*](http://velocity.apache.org/engine/devel/user-guide.html#escapinginvalidvtlreferences)

```
#set( $email = "foo" )
$email
```

假如在你的Velocity 模板中遇到一个 *$email*,它将在上下文中查询并输出正确的值. 上实例中将输出 *foo*, 因为*$email* 已经被定义了.如果 *$email*is没有被定义, 它将输出*$email*.

加入 *$email* 已经定义了 (例如, 它的值为 *foo*), 但是你想输出 *$email*. 这里有几种方式可以实现, 最简单的方式是使用转义字符. 请看下面实例:

```
## The following line defines $email in this template:
#set( $email = "foo" )
$email
\$email
```

输出

```
foo
$email
```

如果,由于某种原因, 你需要在它之前添加一个反斜杠, 你需要按照下面实例做:

```
## The following line defines $email in this template:
#set( $email = "foo" )
\\$email
\\\$email
```

输出结果

```
\foo
\$email
```

注意 *\* 字符绑定到*$* 左边的字符. 左边绑定规则导致 *\\\$email* 输出为*\$email*. 比较下面实例看看*$email*是否被定义.

```
$email
\$email
\\$email
\\\$email
```

输出

```
$email
\$email
\\$email
\\\$email
```

注意Velocity定义的引用不同于那些没有定义的引用 . 本实例中*$foo* 定义值为*gibbous*.

```
#set( $foo = "gibbous" )
$moon = $foo
```

输出结果为: *$moon = gibbous* — *$moon*将作为字符输出而$foo的地方将输出*gibbous*.

**Escaping Invalid VTL References(转义不可用VTL引用)**
有时候你可能会遇到这种情况,当你的Velocity解析你的模板时遇见了一个你从来都没有打算把它当着引用的不可用的引用. 屏蔽特殊的字符, 最好的方式是你能够处理把握这种情况,在这种情况下, 反斜杠可能会失败. 你可以使用简单的方式来屏蔽关于 `$` 或 `#`问题, 你可能仅仅是替换一下:

```
${my:invalid:non:reference}
```

可以想这样

```
#set( $D = '$' )
${D}{my:invalid:non:reference}
```

你也可以通过Java代码把  `$` 或 `#`字符串指令放到你的文本中  (例如 `context.put("D","$");`)来避免在你的模板中添加额外的 #set() 指令. 或者, 你也可以使用[VelocityTools](http://velocity.apache.org/tools/devel/), 你可以使用EscapeTool:

```
${esc.d}{my:invalid:non:reference}
```

有效的和无效的VTL 指令使用同样的方式进行转义的; 在指令章节将对此进行详细描述.

**Escaping VTL Directives(转义VTL指令)**
VTL 指令能够被屏蔽通过反斜杠(“\”) 字符和疲敝VTL引用方式是一样的.

```
## #include( "a.txt" ) renders as <contents of a.txt>
#include( "a.txt" )

## \#include( "a.txt" ) renders as #include( "a.txt" )
\#include( "a.txt" )

## \\#include ( "a.txt" ) renders as \<contents of a.txt>
\\#include ( "a.txt" )
```

需要特别关心的是转义在一个单独的指令中包含多个脚本元素VTL 指令(例如在一个 if-else-end语句). 这里是一个典型的VTL if语句:

```
#if( $jazz )
    Vyacheslav Ganelin
#end
```

如果 *$jazz*为 true, 输出结果为

```
Vyacheslav Ganelin
```

如果*$jazz* 为false,这里没有任何输出. Escaping 脚本元素修改输出结果. 考虑下面实例:

```
\#if( $jazz )
    Vyacheslav Ganelin
\#end
```

它将导致指令被忽略, 但是变量 *$jazz* 正常显示. 所以, 如果*$jazz* 为 true,输出结果是

```
 #if( true )
     Vyacheslav Ganelin
 #end
```

如果脚本之前的元素被反斜杠转义:

```
\\#if( $jazz )
   Vyacheslav Ganelin
\\#end
```

在本实例中, 如果*$jazz* 为 true,输出为

```
\ Vyacheslav Ganelin
\
```

为了了解这一点,注意 `#if( arg ) 如果在新的一行结束时,输出时将省略这一行`. 另外,  `#if()` 的语句块将紧跟着 ‘\’,  在`#if()之前加入两个'\\'`. 最后的 \和文本在不同的行因为在 ‘Ganelin’之后有一个新行, 所以最终\\, `#end` 之前的部分是程序体.

如果*$jazz*是 false, 输出结果为

```
\
```

注意一些执行将被中断如果元素没有属性被转义.

```
\\\#if( $jazz )
    Vyacheslave Ganelin
\\#end
```

这里 *#if* 被转义, 但是这里保留一个 *#end* 标签; 多余的标签将导致解析错误.

### VTL: Formatting Issues(格式化问题)

虽然VTL的用户使用指南中经常显示换行符和空格,VTL显示如下

```
#set( $imperial = ["Munetaka","Koreyasu","Hisakira","Morikune"] )
#foreach( $shogun in $imperial )
    $shogun
#end
```

上面实例和下面实例是等效的, Geir Magnusson Jr. 写给用户的邮件来说明这点完全无关:

```
Send me #set($foo=["$10 and ","a pie"])#foreach($a in $foo)$a#end please.
```

Velocity可以去掉多余的空格. 前面的指令可以写成:

```
Send me
#set( $foo = ["$10 and ","a pie"] )
#foreach( $a in $foo )
$a
#end
please.
```

or as

```
Send me
#set($foo       = ["$10 and ","a pie"])
                 #foreach           ($a in $foo )$a
         #end please.
```

在这些实例中输出结果将是一样的.

### Other Features and Miscellany(其他的特性和杂记)

#### Math(算术操作)

Velocity中内置了一个算术函数,这些函数你可以在VTL模板中进行调用 .下面的实例分别展示加减乘数的使用:

```
#set( $foo = $bar + 3 )
#set( $foo = $bar - 4 )
#set( $foo = $bar * 6 )
#set( $foo = $bar / 2 )
```

当两个整数相除时,结果是整数, 小数部分被丢弃. 模板中也可以使用求模运算符 (*%*).

```
#set( $foo = $bar % 5 )
```

#### Range Operator(范围操作符)

范围操作符能够结合着 *#set* 和 *#foreach* 语句使用. 用它能够产生一个证书数组,它的语法结果如下:

```
[n..m]
```

产生一个n到m的整数. 不论m大于或者小于n都不重要;在这个实例中这个范围就是简单的计算.下面的实例展示了范围操作符的使用:

```
第一个实例:
#foreach( $foo in [1..5] )
$foo
#end

第二个实例:
#foreach( $bar in [2..-2] )
$bar
#end

第三个实例:
#set( $arr = [0..1] )
#foreach( $i in $arr )
$i
#end

第四个实例:
[1..3]
```

输出结果为:

```
First example:
1 2 3 4 5

Second example:
2 1 0 -1 -2

Third example:
0 1

Fourth example:
[1..3]
```

注意范围操作符仅仅产生数组当结合 *#set* 和 *#foreach* 指令, 正如在第四个例子中展示的.

网页设计者关系一个制作标准大小的表格, 有些情况下没有足够的数据填充表格, 将发现范围操作符特别有用.

### Advanced Issues: Escaping and !(高级问题:转义和!)

当一个引用前面加上*!* 字符和*!* 字符前面加上一个 *\* 转义字符, 这种引用需要一种特殊的处理方式. 注意正规的转义符和特殊的\之后紧跟 *!*实例的不同:

```
#set( $foo = "bar" )
$\!foo
$\!{foo}
$\\!foo
$\\\!foo
```

输出结果为:

```
$!foo
$!{foo}
$\!foo
$\\!foo
```

对比这个正规 *\* 优先*$*的转义:

```
\$foo
\$!foo
\$!{foo}
\\$!{foo}
```

输出结果为:

```
$foo
$!foo
$!{foo}
\bar
```

### Velocimacro Miscellany(杂记)

这一章节是关于Velocimacros一些小疑问.本章节以后还会经常改变 , 所以它很值得你关注.

Note : 贯穿整个章节, ‘Velocimacro’ 将被简写成 ‘VM’.

**Can I use a directive or another VM as an argument to a VM?**Example : `#center( #bold("hello") )`

No. 一个指令不是一个可用的指令参数, 出于实用的目的, 一个VM是一个指令.

*然而…*, 这里有很多事情你需要做. 一个容易的解决方案是利用编译器 ‘doublequote’ (“) 输出显示它的内容. 你可以想下面方式来做

```
#set($stuff = "#bold('hello')" )
#center( $stuff )
```

You can save a step…

```
#center( "#bold( 'hello' )" )
```

在这个实例中参数是在VM中计算的,而不是在调用时 . 简而言之, the argument to the VM的参数传递到VM中进行计算 . 它准许你这么操作:

```
#macro( inner $foo )
  inner : $foo
#end

#macro( outer $foo )
   #set($bar = "outerlala")
   outer : $foo
#end

#set($bar = 'calltimelala')
#outer( "#inner($bar)" )
```

输出结果为

```
Outer : inner : outerlala
```

因为 “#inner($bar)” 的计算发生在 #outer()的内部, 所以 $bar 的值是在 #outer() 内部进行赋值的.

这是一种有意的保护功能 – 参数通过名字传递到VMs, 所以你能够传递VMs像状态引用,例如

```
#macro( foo $color )
  <tr bgcolor=$color><td>Hi</td></tr>
  <tr bgcolor=$color><td>There</td></tr>
#end

#foo( $bar.rowColor() )
```

rowColor()被重复调用,而不是仅仅调用一次.为了避免这种情况, 在VM外面执行方法, 并把值传递给VM.

```
#set($color = $bar.rowColor())
#foo( $color )
```

**Can I register Velocimacros via #parse() ?****Yes! This became possible in Velocity 1.6.**

如果你使用之前的版本, 你的Velocimacros必须第一次使用之前就已经被定义 .它的意思是有的当你使用  #macro()之前都已经被定义了.

这是很重要的如果你试图 #parse() 一个包含#macro() 指令模板. 因为 #parse() 在运行时才被调用,解析时 解析器决定是否在你的模板中 VM-looking 元素是一个 VM, #parse()-ing 设置 VM 声明并不向期望那样工作. 为了避开这一点, 可以使用 `velocimacro.library来使`Velocity启动时重新加载VMs.

**What is Velocimacro Autoreloading?**这个属性用在开发模式下,  而不是生成环境 :

```
velocimacro.library.autoreload
```

默认是false. 当设置为true时

```
<type>.resource.loader.cache = false
```

( <type> 是你使用资源的名字, 例如 ‘file’) 然后Velocity将自动加载已经修改的Velocimacro依赖包文件当你配置该选项时, 所以你不比清空你的服务器(或者引用的)或者通过其他方式来是Velocimacros重载.

这里是一个简单的配置文件设置.

```
    file.resource.loader.path = templates
    file.resource.loader.cache = false
    velocimacro.library.autoreload = true
```

在生产环境不能使用这种配置.

### String Concatenation(字符串的拼接)

开发者经常会问一个很普通的问题,就是怎么去拼接两个字符串?是不是类似于Java里面的’+’*?.* 

为了实现在VTL中两个字符串的拼接VTL, 你仅仅需要把它们放在一起. 你需要把他们放在一起当你需要的时候, 请看下面实例.

在一个有规则的 ‘schmoo’ 模板 (当你添加一个有规则的内容时) :

```
       #set( $size = "Big" )
       #set( $name = "Ben" )

      The clock is $size$name.
```

输出结果为 ‘The clock is BigBen’. 这里有更多有趣的实例, 例如当你想拼接字符串并传递给一个方法时, 或者定义一个新的引用,你只需要这样做

```
      #set( $size = "Big" )
      #set( $name = "Ben" )

      #set($clock = "$size$name" )

      The clock is $clock.
```

它们的输出结果是一样的. 作为最后一个实例, 当你想在你的引用中添加一个 ‘static’字符串时 , 你需要使用正式的引用 :

```
      #set( $size = "Big" )
      #set( $name = "Ben" )

      #set($clock = "${size}Tall$name" )

      The clock is $clock.
```

现在输出的是 ‘The clock is BigTallBen’。正式引用解析能够把 ‘$size’ 和’$sizeTall’ 通过 ‘{}’ 进行区分开.

























