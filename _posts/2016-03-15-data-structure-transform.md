---
layout: post
title:  "将下载的结构化的数据转换为列数据"
date:  2016-03-15 20:04:00 +0800
categories: Python & R
tags: 数据分析 python
img: https://ooo.0o0.ooo/2017/05/27/59292b1243dc9.jpg
author: LiuKK
---


# 数据形式转换

  前段时间要做一个课程作业，需要用到各省的生产总值，到国家统计局网站上下载的数据是这样的：
  


--- | 2007 | 2008 | 2009 
---|---|---|---
北京市  | 342424.45 | 843058.34 | ……
上海市 | 343534.56 | 435024.75 | ……
…… | …… | …… | ……

但是我需要的数据是这样的：

年份 | 省份 | 产值
---|---|---
2007 | 北京市 | 233333.33
2008 | 上海市 | 233333.33
…… | …… | ……

---

用python的`pandas`包处理非常简单：

```python
import pandas as pd
chengtou=pd.read_csv('yuanshi.csv',index_col=0,encoding='gbk')
f=chengtou.stack()
f.to_csv('test.csv',encoding='gbk')
```
