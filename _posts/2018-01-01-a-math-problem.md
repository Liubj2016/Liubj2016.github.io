---
layout: post
title:  "一个简单的数学问题"
date:  2018-01-01 15:11:00 +0800
categories: Learn
tags: 随机过程
img: https://raw.githubusercontent.com/Liubj2016/Liubj2016.github.io/master/images/Martingale.png
author: LiuKK
---

# 一个简单的数学问题

有这样一段代码，求返回值的期望值：


```python
import numpy as np

def RB():
    S = 0.0
    while S<=1:
        S += np.random.rand()
    return S
```

## 蒙特卡洛模拟的方法


```python
np.mean([RB() for i in range(10000)])
```




    1.3580820141627414



可以看到模拟一万次的结果，S的期望值大概是1.358，那么怎么求出它具体是多少呢？（求出解析解）


```python
np.exp(1)/2
```




    1.3591409142295225



## 随机过程的方法

![image](https://raw.githubusercontent.com/Liubj2016/Liubj2016.github.io/master/images/M1.png)

>In probability theory, optional stopping theorem (or Doob's optional sampling theorem) says that, under certain conditions, the expected value of a martingale at a stopping time is equal to the expected value of its initial value.

![image](https://raw.githubusercontent.com/Liubj2016/Liubj2016.github.io/master/images/M2.png)

## wald's equation

![image](https://raw.githubusercontent.com/Liubj2016/Liubj2016.github.io/master/images/wald.png)
