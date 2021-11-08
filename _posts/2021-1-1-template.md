---
layout: post
title: "模板"
subtitle: "博客文档编写语法示例"
categories: Template
tags: [Template]
author: "Kid-On-The-Road"
meta: ""

---

### 顶部

- 博客

```
---
layout: post

title: Another test markdown

subtitle: Each post also has a subtitle

categories: 模板

tags: [模板]
---
```

- 完整

```bash
---
layout: post
title: Welcome to Jekyll!
subheading: A awesome static site generator.
author: Jeffrey
categories: Template
tags: [Template]
banner:
  video: https://vjs.zencdn.net/v/oceans.mp4
  loop: true
  volume: 0.8
  start_at: 8.5
  image: https://bit.ly/3xTmdUP
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
sidebar: []
---
```

### 代码片段

```bash
{% highlight ruby %}

{% endhighlight %}
```

{% highlight ruby %}

{% endhighlight %}

````
```java

```
````

```java

```

### 标颜色

```
 [Markdown][1]
```

 [Markdown][1]

### 列表

#### 有序列表

```
1. Item 1
2. A second item
3. Number 3
4. Ⅳ
```

1. Item 1
2. A second item
3. Number 3
4. Ⅳ

#### 无序列表

```
* An item
* Another item
* Yet another item
* And there's more...
```

* An item
* Another item
* Yet another item
* And there's more...

#### 引用

```
> 
```

> 

### 阴影

```
` `
```

` 阴影`

### 斜体

```
*can* 
```

*can* 

### 网址

```html
[MarkItDown][3]
或
[MarkItDown](http://www.markitdown.net/)
或
 <http://www.markitdown.net/>
```

[MarkItDown][3]
或
[MarkItDown](http://www.markitdown.net/)
或
 <http://www.markitdown.net/>

```
[1]: http://daringfireball.net/projects/markdown/
[2]: http://www.fileformat.info/info/unicode/char/2163/index.htm
[3]: http://www.markitdown.net/
[4]: http://daringfireball.net/projects/markdown/basics
[5]: http://daringfireball.net/projects/markdown/syntax
```

[1]: http://daringfireball.net/projects/markdown/
[2]: http://www.fileformat.info/info/unicode/char/2163/index.htm
[3]: http://www.markitdown.net/
[4]: http://daringfireball.net/projects/markdown/basics
[5]: http://daringfireball.net/projects/markdown/syntax

### 视频

```
![video](//www.html5rocks.com/en/tutorials/video/basics/devstories.webm)
```

![video](//www.html5rocks.com/en/tutorials/video/basics/devstories.webm)

### 图片

```
![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)
```

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

- 居中

```
![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .center-block :}
```

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .center-block :}

### 表格

#### 右对齐

```
| | | |
| ----: | --------------: | ---------: |
| | | |
| | | |
```

|      |      |      |
| ---: | ---: | ---: |
|      |      |      |
|      |      |      |

#### 左对齐

```
|: :|||
|:------ |:------ |:-------- |
| | | |
| | | |
```

| : :  |      |      |
| :--- | :--- | :--- |
|      |      |      |
|      |      |      |

#### 无头

```
|--|--|
| | |
| | |
```

| --   | --   |
| ---- | ---- |
|      |      |

#### 示例图片

```
![example image][my-image]
```

![example image][my-image]

```
[my-image]: http://www.unexpected-vortices.com/sw/rippledoc/example-image.jpg 
```

[my-image]: http://www.unexpected-vortices.com/sw/rippledoc/example-image.jpg

### 特殊媒体链接

```
[![](https://i.imgur.com/bc9HOJU.png)](https://www.youtube.com/watch?v=kCHGDRHZ4eU)
```

[![](https://i.imgur.com/bc9HOJU.png)](https://www.youtube.com/watch?v=kCHGDRHZ4eU)

