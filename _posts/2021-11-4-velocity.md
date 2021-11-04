---
layout: post
title: "velocity"
subtitle: "velocity(vm)模板引擎"
categories: 前端
tags: [velocity]
author: "Kid-On-The-Road"
meta: ""

---

### 介绍

Velocity是基于Java的模板引擎，它允许页面设计者引用Java中定义的方法。页面设计者和Java开发者能够同时使用MVC的模式开发网站，这样网页设计者能够把精力放在页面的设计上，程序员也可以把精力放在代码开发上。Velocity把Java代码从Web页面中分离， 使网站可维护性更强，同时也在Java服务器页面(JSPs)或者PHP中提供了可视化交互的选择。

Velocity能够使用模板生成Web页面,  SQL，PostScript 和其他内容。并能够生成的源代码和报表中的一个独立的单元，或者作为一个其他系统的组件。配置完成后，Velocity将提供为[Turbine](http://java.apache.org/turbine/) 页面应用框架提供模板服务。 Velocity+Turbine将提供一个模板服务，它将允许网页应用按照MVC的模式进行开发。

# 依赖

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

