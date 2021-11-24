---
layout: post
title: "FineReport"
subtitle: "FineReport报表软件"
categories: 报表
tags: [报表]
author: "Kid-On-The-Road"
meta: ""

---

## 时间处理

- 格式化时间

```bash
FORMAT(YEARDELTA(date(2015, 11, 1), -1), "yyyyMM")
```

- 返回某一时间区间的月份列表

```SQL
//从当前日期开始,返回前一年的月份列表
UNIQUEARRAY(REVERSEARRAY(MAPARRAY(RANGE(YEARDELTA(today(),-1), today()), FORMAT(item, "yyyyMM"))))
//根据某一个时间区间返回月份列表
UNIQUEARRAY(REVERSEARRAY(MAPARRAY(RANGE(date(2014,11,1), date(2015,11,1)), FORMAT(item, "yyyyMM"))))
```

- 时间区间

```SQL
-- 分开
bill_date <= ${if(len(billDate) == 0,FORMAT(date(2015, 11, 1), "yyyyMM"),billDate)}
bill_date >= ${if(len(billDate) == 0,FORMAT(YEARDELTA(date(2015, 11, 1),-1), "yyyyMM"),billDate-100)}

-- 合并
${if(len(billDate) == 0,"and bill_date <= '" + FORMAT(date(2015, 11, 1), "yyyyMM") + "' and bill_date >= '" + FORMAT(YEARDELTA(date(2015, 11, 1),-1), "yyyyMM") + "'","and bill_date = '" + billDate + "'")}
```

## 条件属性

- 隐藏行或列

```bash
//添加如下公式
len($$$) = 0
or $$$ = 0
```

## 过滤

- 条件为空不过滤

```bash
if(len($agentCode) = 0, nofilter, $agentCode)
```

