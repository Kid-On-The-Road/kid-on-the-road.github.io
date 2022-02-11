---
layout: post
title: "Bootstrap"
subtitle: "Bootstrap文档"
categories: 前端框架
tags: [Bootstrap]
author: "Kid-On-The-Road"
meta: ""

---

## Bootstrap框架

### 解释

1.	一个前端的框架，提高前端的开发效率，制作出更加专业，漂亮的页面。
2.	基于html、css、js技术，只要有这个基础就可以使用Bootstrap

![1552204201045](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552204201045.png)

bootstrap中文官网：http://www.bootcss.com

### Bootstrap的优势

1.	自 Bootstrap 3 起，框架包含了贯穿于整个库的移动设备优先的样式。
2.	Bootstrap支持所有的主流浏览器。如：Internet Explorer、 Firefox、 Opera、 Google Chrome、Safari。
3.	只要您具备 HTML 和 CSS 的基础知识，您就可以开始学习 Bootstrap。
4.	Bootstrap 的响应式 CSS 能够自适应于台式机、平板电脑和手机。

![1552204315056](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552204315056.png)



## <font color="red">响应式设计</font>

### 软件开发的三层架构

1. 表示层
2. 业务层
3. 持久层(数据访问层DAO = Data Access Object)

### 响应式布局特点

同一个网页在不同的设备上自动适配屏幕的分辨率和宽度

### bootstrap支持四类设备

| 四类设备 | 类名的前缀 |
| -------- | ---------- |
| 微型设备 | xs         |
| 小型设备 | sm         |
| 中型设备 | md         |
| 大型设备 | lg         |

## Bootstrap的使用

### Bootstrap包含的内容

1. 设置全局 CSS 样式；基本的 HTML 元素均可以通过 class 设置样式并得到增强效果。

2. 无数可复用的组件，包括字体图标、下拉菜单、导航、警告框、弹出框等更多功能。
3. jQuery 插件为 Bootstrap 的组件赋予了“生命”。

### 下载

<http://www.bootcss.com>，下载用于生产环境的Bootstrap

![1552205574995](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552205574995.png)

### 目录结构

![1571800208661](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1571800208661.png) 

![1552205695507](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552205695507.png)

### 压缩版与标准版的介绍

- 标准版：bootstrap.js 文件比较大，可读性比较强。
- 压缩版：文件比较小，可读取性差，占资源少。

功能上是一样的

## <font color="red">创建Bootstrap的模板</font>

### 步骤

1. 复制解压出来的三个文件夹到项目中：css, js, fonts
2. 复制jquery框架：jquery-3.2.1.min.js复制到js目录下
3. 复制："起步->基本模板"中代码到网页，修改网页的内容。

- 此模板文件只要创建1次即可，以后可以重用。

### 代码

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">
</head>
<body>
<h1>你好，世界！</h1>
<hr/>

<!-- 2. 导入jQuery.js文件 (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
<script src="js/jquery-3.2.1.min.js"></script>

<!-- 3. 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
<script src="js/bootstrap.min.js"></script>
</body>
</html>
```



## <font color="red">栅格系统</font>

### 组成

	Bootstrap 提供了一套响应式、移动设备优先的流式栅格系统，随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多12格。栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。

![1552206012518](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552206012518.png)

### 两种容器

| 两种容器的类样式名 | 说明                                             |
| ------------------ | ------------------------------------------------ |
| container          | 固定宽度的容器，在不同的设备上显示不同的固定宽度 |
| container-fluid    | 在所有的设备上都以100%宽度显示                   |

### 效果

![1552206063236](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552206063236.png)

### 代码

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>两种容器</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">

    <style>
        div {
            border: 1px solid red;
            height: 100px;
        }
    </style>
</head>
<body>
<div class="container">
    固定宽度的容器
</div>

<div class="container-fluid">
    100%宽度
</div>
</body>
</html>
```

### 设备查询@media

	通过不同的设备类型和条件定义样式表规则。设备查询让CSS可以更精确作用于不同的设备类型和同一设备的不同条件。设备查询的大部分特性都接受min和max用于表达“大于或等于”和“小于或等于”。打开文件：bootstrap.css，可以看到以下代码：

```css
.container {
  padding-right: 15px;
  padding-left: 15px;   左右内边距是15px
  margin-right: auto;   水平居中
  margin-left: auto;
}
@media (min-width: 768px) {  设备大于或等于768px
  .container {
    width: 750px;  容器的宽度是750px
  }
}
@media (min-width: 992px) {  设备大于或等于992px
  .container {
    width: 970px;   容器的宽度是970px
  }
}
@media (min-width: 1200px) {   设备大于或等于1200px
  .container {
    width: 1170px;    容器的宽度是1170px
  }
}
```

- 结论：如果设备的宽度发生变化，容器的宽度也会发生变化

### 栅格系统有关的类样式名

| 栅格系统         | 描述                                                         | 类似于表格 |
| ---------------- | ------------------------------------------------------------ | ---------- |
| .container       | 固定宽度的容器                                               | table      |
| .container-fluid | 始终显示100%宽度                                             | table      |
| .row             | 一行，必须放在容器中                                         | tr         |
| .col-xx-n        | 一列，一列占多个格子<br />xs: 微型<br />sm: 小型<br />md: 中型<br />lg: 大型<br />如：<br />col-md-4 在中型设备上一列占4个格子<br />col-lg-3 在大型设备上一列占3个格子 | td         |

### 栅格的参数

![1552206304153](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552206304153.png)

### 示例1：基本结构

	在中型设置上显示：2行3列

![1552206379296](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552206379296.png)

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">

    <style>
        .row div {
            border: 1px solid red;
            height: 100px;
        }
    </style>
</head>
<body>
<!--容器-->
<div class="container">
    <!--    行-->
    <div class="row">
        <div class="col-md-4">
            中型设备
        </div>
        <div class="col-md-4">
            中型设备
        </div>
        <div class="col-md-4">
            中型设备
        </div>
    </div>

    <div class="row">
        <div class="col-md-4">
            中型设备
        </div>
        <div class="col-md-4">
            中型设备
        </div>
        <div class="col-md-4">
            中型设备
        </div>
    </div>
</div>

<!-- 2. 导入jQuery.js文件 (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
<script src="js/jquery-3.2.1.min.js"></script>

<!-- 3. 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
<script src="js/bootstrap.min.js"></script>
</body>
</html>
```

### 示例2：一行超过12格

	如果1行超过12格：多出来的列就放在下一行

![1552206420279](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552206420279.png)

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">

    <style>
        .row div {
            border: 1px solid red;
            height: 100px;
        }
    </style>
</head>
<body>
<!--容器-->
<div class="container">
    <!--    行-->
    <div class="row">
        <div class="col-md-4">
            中型设备
        </div>
        <div class="col-md-4">
            中型设备
        </div>
        <div class="col-md-4">
            中型设备
        </div>
        <div class="col-md-4">
            中型设备
        </div>
        <div class="col-md-4">
            中型设备
        </div>
    </div>
</div>

<!-- 2. 导入jQuery.js文件 (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
<script src="js/jquery-3.2.1.min.js"></script>

<!-- 3. 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
<script src="js/bootstrap.min.js"></script>
</body>
</html>
```



### 示例3：不同屏幕的适配

	在微型，小型，中型设备上显示不同的列数

![1552206467393](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552206467393.png)

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">

    <style>
        .row div {
            border: 1px solid red;
            height: 100px;
        }
    </style>
</head>
<body>
<!--容器-->
<div class="container">
    <!--    行-->
    <div class="row">
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
    </div>
</div>

<!-- 2. 导入jQuery.js文件 (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
<script src="js/jquery-3.2.1.min.js"></script>

<!-- 3. 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
<script src="js/bootstrap.min.js"></script>
</body>
</html>
```

### 示例4：显示和隐藏块

	在微型设备上隐藏，在小型设备上显示

![1552206514114](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552206514114.png)

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">

    <style>
        .row div {
            border: 1px solid red;
            height: 100px;
        }
    </style>
</head>
<body>
<!--容器-->
<div class="container">
    <!--    行-->
    <div class="row">
        <div class="col-md-4 col-sm-3 col-xs-6 visible-sm">
            我只在小型设备上显示
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6 hidden-xs">
            我在微型设备上隐藏
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
        <div class="col-md-4 col-sm-3 col-xs-6">
            col-md-4 col-sm-3 col-xs-6
        </div>
    </div>
</div>

<!-- 2. 导入jQuery.js文件 (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
<script src="js/jquery-3.2.1.min.js"></script>

<!-- 3. 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
<script src="js/bootstrap.min.js"></script>
</body>
</html>
```

## 全局CSS样式：按钮

### 效果

![1552206592422](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552206592422.png) 

![1552206627547](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552206627547.png) 

### 代码

```html
<div class="container">
    <h2>普通按钮</h2>
    <input type="button" value="这是按钮" class="btn btn-default">
    <input type="reset" value="重置按钮" class="btn btn-default">
    <a href="#" class="btn btn-default">这是链接</a>
    <hr/>

    <h2>有颜色按钮</h2>
    <input type="button" value="这是按钮" class="btn btn-primary">
    <input type="reset" value="重置按钮" class="btn btn-success">
    <a href="#" class="btn btn-danger">这是链接</a>
    <hr/>
    <h2>不同大小</h2>
    <input type="button" value="这是按钮" class="btn btn-primary btn-lg">
    <input type="reset" value="重置按钮" class="btn btn-success btn-sm">
    <a href="#" class="btn btn-danger btn-xs">这是链接</a>
    <hr/>
</div>
```

## 全局CSS样式：图片

### 响应式图片

	通过为图片添加 .img-responsive 类可以让图片支持响应式布局。其实质是为图片设置了 max-width: 100%;、height: auto; 和 display: block; 属性，从而让图片在其父元素中更好的缩放。

### 图片形状

![1552207355159](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207355159.png)

### 效果

![1552207365241](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207365241.png)

### 代码

```html
<h2>响应式图片</h2>
<img src="img/01.jpg" class="img-responsive">
<hr/>
<img src="img/01.jpg" class="img-responsive img-circle">
<hr/>
<img src="img/01.jpg" class="img-responsive img-rounded">
<hr/>
<img src="img/01.jpg" class="img-responsive img-thumbnail">
```

## 全局CSS样式：表单

### 效果

![1552207576823](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207576823.png) 

### 表单

![1552207596169](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207596169.png)

### 代码

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>添加联系人</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">
</head>
<body>
<div class="container">
<h2>添加联系人</h2>
<form style="max-width: 400px">
    <div class="form-group">
        <!-- label一个标签, for 表示给哪个表单项使用的 等于表单项的id-->
        <label for="username">姓名</label>
        <input type="text" class="form-control" id="username" placeholder="请输入姓名">
    </div>

    <div class="form-group">
        <label>性别</label>
        <input type="radio" name="sex" id="male" checked="checked"><label for="male">男</label>
        <input type="radio" name="sex" id="female"><label for="female">女</label>
    </div>

    <div class="form-group">
        <label for="birthday">生日</label>
        <input type="date" class="form-control" id="birthday">
    </div>

    <div class="form-group">
        <label for="edu">学历</label>
        <select id="edu" class="form-control">
            <option value="本科">本科</option>
            <option value="硕士">硕士</option>
        </select>
    </div>

    <div class="text-center">
            <input type="submit" value="注册" class="btn btn-primary">
            <input type="button" value="退出" class="btn btn-danger">
    </div>
</form>
</div>
<!-- 2. 导入jQuery.js文件 (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
<script src="js/jquery-3.2.1.min.js"></script>

<!-- 3. 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
<script src="js/bootstrap.min.js"></script>
</body>
</html>
```

## 全局CSS样式：表格

### 效果

![1552207670959](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207670959.png)

### 表格的类样式

![1552207696806](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207696806.png)

### 不同行的颜色

![1552207726252](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207726252.png)

### 代码

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">
</head>
<body>

<div class="container">
    <h2>七龙珠</h2>
    <table class="table table-bordered table-hover table-condensed">
        <tr class="success">
            <th>编号</th>
            <th>姓名</th>
            <th>性别</th>
            <th>电话</th>
        </tr>
        <tr>
            <td>1302</td>
            <td>贝吉塔</td>
            <td>男</td>
            <td>19509869504</td>
        </tr>
        <tr>
            <td>5940</td>
            <td class="danger">孙悟空</td>
            <td>男</td>
            <td>13938475687</td>
        </tr>
        <tr>
            <td>6841</td>
            <td>龟仙人</td>
            <td>男</td>
            <td>18501029504</td>
        </tr>
    </table>
</div>

<!-- 2. 导入jQuery.js文件 (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
<script src="js/jquery-3.2.1.min.js"></script>

<!-- 3. 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
<script src="js/bootstrap.min.js"></script>
</body>
</html>
```

## 组件：字体图标

### 效果

![1552207778505](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207778505.png) 

### 代码

```html
<h2>字体图标</h2>
<!--文字就是类名-->
<span class="glyphicon glyphicon-heart" style="font-size: 40px;color: red"></span>我心依旧
<span class="glyphicon glyphicon-camera" style="font-size: 40px;color: blue"></span>我心依旧
<span class="glyphicon glyphicon-tint" style="font-size: 40px;color: green"></span>我心依旧
```

## 组件：导航条

### 效果

![1552207828085](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207828085.png)

### 导航条

	什么是导航条：导航条是在您的应用或网站中作为导航页头的响应式基础组件。它们在移动设备上可以折叠（并且可开可关），且在视口（viewport）宽度增加时逐渐变为水平展开模式。

### 组成

	整个导航条就是一个nav标签，nav与div功能相同，它是一个语义标签。

![1552207898669](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207898669.png)

### 属性说明

![1552207925499](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552207925499.png)

### 代码

```html
<nav class="navbar navbar-default">
    <div class="container-fluid">

        <!-- 商标和折叠按钮 -->
        <div class="navbar-header">
            <!--折叠按钮-->
            <button type="button" class="navbar-toggle collapsed" data-toggle="collapse"
                    data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
                <span class="glyphicon glyphicon-list"></span>
            </button>
            <a class="navbar-brand" href="#">
                <span class="glyphicon glyphicon-piggy-bank"></span>
            </a>
        </div>

        <!-- 链接 和 表单 -->
        <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">


            <ul class="nav navbar-nav">
                <li class="active"><a href="#">国内游</span></a></li>
                <li><a href="#">出境游</a></li>
                <li><a href="#">地沟游</a></li>
                <li><a href="#">印度神游</a></li>

                <!--下拉菜单-->
                <li class="dropdown">
                    <!--<span class="caret"></span>表示向下箭头-->
                    <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button"
                       aria-haspopup="true" aria-expanded="false">港澳游<span class="caret"></span></a>
                    <ul class="dropdown-menu">
                        <li><a href="#">澳门威尼斯</a></li>
                        <li><a href="#">Another action</a></li>
                        <li><a href="#">Something else here</a></li>
                        <!--separator 水平分隔线-->
                        <li role="separator" class="divider"></li>
                        <li><a href="#">Separated link</a></li>
                        <li role="separator" class="divider"></li>
                        <li><a href="#">One more separated link</a></li>
                    </ul>
                </li>
            </ul>

            <!--搜索表单-->
            <form class="navbar-form navbar-right">
                <div class="form-group">
                    <input type="text" class="form-control" placeholder="输入关键字">
                </div>
                <button type="submit" class="btn btn-default">
                    <span class="glyphicon glyphicon-search"></span>
                    搜索
                </button>
            </form>

        </div><!-- /.navbar-collapse -->
    </div><!-- /.container-fluid -->
</nav>
```

## 组件：缩略图

### 解释

	扩展 Bootstrap 的 栅格系统，可以很容易地展示栅格样式的图像、视频、文本等内容。

### 缩略图的类

![1552208034281](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552208034281.png)

### 标准缩略图

![1552208095025](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552208095025.png)

### 自定义缩略图

![1552208114924](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552208114924.png)

### 代码

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">
</head>
<body>

<div class="container">
    <div class="row">
        <div class="col-xs-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="img/02.jpg">
            </a>
        </div>
        <div class="col-xs-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="img/02.jpg">
            </a>
        </div>
        <div class="col-xs-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="img/02.jpg">
            </a>
        </div>
        <div class="col-xs-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="img/02.jpg">
            </a>
        </div>
    </div>

    <div class="row">
        <div class="col-sm-6 col-md-4">
            <div class="thumbnail">
                <img src="img/03.jpg">
                <div class="caption">
                    <h3>我是女生</h3>
                    <p>Donec id elit non mi porta gravida at eget metus. Nullam id dolor id nibh ultricies vehicula ut id elit.</p>
                    <p><a href="#" class="btn btn-primary" role="button">原价</a> <a href="#" class="btn btn-default" role="button">折后价</a></p>
                </div>
            </div>
        </div>

        <div class="col-sm-6 col-md-4">
            <div class="thumbnail">
                <img src="img/03.jpg">
                <div class="caption">
                    <h3>我是女生</h3>
                    <p>Donec id elit non mi porta gravida at eget metus. Nullam id dolor id nibh ultricies vehicula ut id elit.</p>
                    <p><a href="#" class="btn btn-primary" role="button">原价</a> <a href="#" class="btn btn-default" role="button">折后价</a></p>
                </div>
            </div>
        </div>

        <div class="col-sm-6 col-md-4">
            <div class="thumbnail">
                <img src="img/03.jpg">
                <div class="caption">
                    <h3>我是女生</h3>
                    <p>Donec id elit non mi porta gravida at eget metus. Nullam id dolor id nibh ultricies vehicula ut id elit.</p>
                    <p><a href="#" class="btn btn-primary" role="button">原价</a> <a href="#" class="btn btn-default" role="button">折后价</a></p>
                </div>
            </div>
        </div>

        <div class="col-sm-6 col-md-4">
            <div class="thumbnail">
                <img src="img/03.jpg">
                <div class="caption">
                    <h3>我是女生</h3>
                    <p>Donec id elit non mi porta gravida at eget metus. Nullam id dolor id nibh ultricies vehicula ut id elit.</p>
                    <p><a href="#" class="btn btn-primary" role="button">原价</a> <a href="#" class="btn btn-default" role="button">折后价</a></p>
                </div>
            </div>
        </div>
    </div>
</div>

<!-- 2. 导入jQuery.js文件 (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
<script src="js/jquery-3.2.1.min.js"></script>

<!-- 3. 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
<script src="js/bootstrap.min.js"></script>
</body>
</html>
```

## JavaScript插件：轮播图

### 轮播图

	Javascript插件必须要使用到jQuery框架
	
	这个组件用于轮播显示一组图片，类似于旋转木马，页面加载就自动运行，也可以通过点击左右的两个箭头向左或向右翻页。

![1552208196569](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552208196569.png)

### 类样式名

![1552208216074](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552208216074.png)

### 相关的属性

![1552208233886](https://raw.githubusercontent.com/Kid-On-The-Road/Resources/main/笔记图片/JSP正则&bootstrap/1552208233886.png)

### 代码

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="utf-8">
    <!-- 使用最新的内核来解析当前网页-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!--
    设置视口参数：默认网页宽度等于设备的宽度，初始缩放比1:1
    视口概念：在浏览器中虚拟的一个网页容器，可以随着设备的不同进行缩放
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- 1. 导入Bootstrap的样式 -->
    <link href="css/bootstrap.css" rel="stylesheet">
</head>
<body>

<div class="container">

    <div id="carousel-example-generic" class="carousel slide" data-ride="carousel" data-interval="1000">
        <!-- 1. 指示器：指的小圆点 -->
        <ol class="carousel-indicators">
            <!--active表示激活的-->
            <li data-target="#carousel-example-generic" data-slide-to="0" class="active"></li>
            <li data-target="#carousel-example-generic" data-slide-to="1"></li>
            <li data-target="#carousel-example-generic" data-slide-to="2"></li>
        </ol>

        <!-- 2. 图片部分 -->
        <div class="carousel-inner" role="listbox">
            <div class="item active">
                <!--图片-->
                <img src="img/03.jpg">
                <!--标题-->
                <div class="carousel-caption">
                    花木兰
                </div>
            </div>

            <div class="item">
                <img src="img/04.jpg">
                <div class="carousel-caption">
                    毛玻璃
                </div>
            </div>

            <div class="item">
                <img src="img/05.jpg">
                <div class="carousel-caption">
                    10块钱3件
                </div>
            </div>
        </div>

        <!-- 3. 左右按钮 -->
        <a class="left carousel-control" href="#carousel-example-generic" role="button" data-slide="prev">
            <span class="glyphicon glyphicon-chevron-left" aria-hidden="true"></span>
        </a>
        <a class="right carousel-control" href="#carousel-example-generic" role="button" data-slide="next">
            <span class="glyphicon glyphicon-chevron-right" aria-hidden="true"></span>
        </a>
    </div>

</div>
<!-- 2. 导入jQuery.js文件 (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
<script src="js/jquery-3.2.1.min.js"></script>

<!-- 3. 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
<script src="js/bootstrap.min.js"></script>
</body>
</html>
```

## 页面加载动画

```html
<div class="modal fade" id="loadingModal">
    <div style="width: 200px;height:20px; z-index: 20000; position: absolute; text-align: center; left: 50%; top: 50%;margin-left:-100px;margin-top:-10px">
        <div class="progress progress-striped active" style="margin-bottom: 0;">
            <div class="progress-bar" style="width: 100%;"></div>
        </div>
        <h5>请稍后...</h5>
    </div>
</div>
```

```js
//显示
$("#loadingModal").modal('show');
//隐藏
 $("#loadingModal").modal('hide');
//使点击空白处遮罩层不会消失
$("#loadingModal").modal({backdrop:'static'});
//按Tab键遮罩层不会消失 ，默认值为true
$("#loadingModal").modal({keyboard:false});
//也可以一起运用
//backdrop 为 static 时，点击模态对话框的外部区域不会将其关闭。
//keyboard 为 false 时，按下 Esc 键不会关闭 Modal。
$('#loadingModal').modal({backdrop: 'static', keyboard: false});
```

