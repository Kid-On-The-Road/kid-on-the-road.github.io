---
layout: post
title: "FineReport"
subtitle: "FineReport报表软件"
categories: 报表
tags: [报表]
author: "Kid-On-The-Road"
meta: ""

---

## 下拉框

### 时间处理

- 返回某一时间区间的月份列表

```bash
//从当前日期开始,返回前一年的月份列表
UNIQUEARRAY(REVERSEARRAY(MAPARRAY(RANGE(YEARDELTA(today(),-1), today()), FORMAT(item, "yyyyMM"))))
//根据某一个时间区间返回月份列表
UNIQUEARRAY(REVERSEARRAY(MAPARRAY(RANGE(date(2014,11,1), date(2015,11,1)), FORMAT(item, "yyyyMM"))))
```

