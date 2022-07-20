---
layout: post
title: "Apache POI"
subtitle: "Apache POI文档"
categories: 报表
tags: [Apache POI]
author: "Kid-On-The-Road"
meta: ""

---

## 依赖

```
//Apache POI(处理office2003)
implementation 'org.apache.poi:poi:4.1.2'
//Apache poi-ooxml(处理office2007)
implementation 'org.apache.poi:poi-ooxml:4.1.2'
//Apache poi-ooxml-schemas(将Excel表格数据提取出来组成一个list，解决读取Excel时报错的问题)
implementation 'org.apache.poi:poi-ooxml-schemas:4.1.2'
```

注:依赖同时存在时版本需一致

## POI结构

```
HSSF－提供读写MicrosoftExcelXLS格式档案的功能
XSSF－提供读写MicrosoftExcelOOXMLXLSX格式档案的功能
HWPF－提供读写MicrosoftWordDOC格式档案的功能
HSLF－提供读写MicrosoftPowerPoint格式档案的功能
HDGF－提供读MicrosoftVisio格式档案的功能
HPBF－提供读MicrosoftPublisher格式档案的功能
HSMF－提供读MicrosoftOutlook格式档案的功能
```
