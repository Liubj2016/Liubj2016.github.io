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

令 $x_{1}, x_{2}, ... , x_{n} \sim Unif(0, 1), S_{0} = 0, S_{n} = x_{1}+x_{2}+ ... + x_{n} $，定义停时 $ \tau = inf(n\geq 0 : S_{n}>1)$。现在要求$E[S_{n}]$，可以证明$S_{n}-n/2$是一个鞅。
要证明 $S_{n}-\frac{n}{2}$是一个鞅，即$$E[S_{n+1}-\frac{n+1}{2} | F_{n}] = S_{n}-\frac {n}{2}$$
$$E[\Delta  | F_{n}] = 0$$
$$\Delta =  (S_{n+1}-\frac {n+1}{2})-(S_{n}-\frac {n}{2}) = S_{n+1}-S_{n}-\frac {1}{2} = x_{n+1}-\frac {1}{2}$$
即要证明：
$$E(x_{n+1}-\frac {1}{2}) = 0$$
显然：
$$E(x_{n+1}) = \frac {1}{2}$$

根据`optional stopping theorem`，可以得到：
$$E[S_{\tau}- \frac {\tau}{2}] = S_{0}$$
即：
$$E[S_{\tau}] = \frac {E[\tau]}{2}$$
所以求出$E[\tau]$即可（即循环次数的期望）。

>In probability theory, optional stopping theorem (or Doob's optional sampling theorem) says that, under certain conditions, the expected value of a martingale at a stopping time is equal to the expected value of its initial value.

要求一个函数$f()$，使得$f(S_{\tau | n})+\tau | n$，且$f(x)=0$。根据鞅的性质以及边界条件，解常微分方程（ODE）:$f(x) = 1+\int_{x}^{1}f(t)dt$，得到$f(x) = e^{1-x}1_{x<=1}$，根据$f(S_{0}) = E[f(S_{\tau ^ n})+\tau ^ n]$，则$E[\tau] = f(S_{0})=f(0)=e$，最终结果就是$\frac {e}{2}$。

## wald's equation

根据wald's  equation ，当$x_{n}$独立同分布的时候，有$$E[x_{1}+x_{2}+...+x_{N}] = E[N]*E[x_{1}]$$
我们知道在$E[x_{1}] = \frac {1}{2}$，所以现在只需要求$E[N]$，在第二次停止的概率为1／2，在第三次停止的概率为1／3，在第n次停止时$S_{n}>1$，前n-1次都小于等于1，这个概率为$\frac {(n-1)}{n}* \frac {1}{(n-1)!}$，则次数的期望和为$1+1+1/2!+1/3!+...$，$e^{x}$在$x=0$处泰勒展开，可以得到$1+1+1/2!+1/3!+...=e$，可以得到结果$\frac {e}{2}$。
