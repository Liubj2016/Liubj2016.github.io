---
layout: post
title:  "【sklearn】预处理"
date:  2017-04-26 20:04:59 +0800
categories: Learn
tags: 机器学习 translate
img: https://ooo.0o0.ooo/2017/05/27/59292b1243dc9.jpg
author: LiuKK
---


# 1、预处理
## 1.1.1 标准化

如果一个特征的方差量级远大于其他特征，它就可能主导整个学习过程，使得算法不能从其它特征学到东西。在`preprocessing`模块中，`scale`函数可以将一个特征（数量型）快速标准化（均值为0， 方差为1）。
>例子：


```python
from sklearn import preprocessing
import numpy as np
X = np.array([[ 1., -1.,  2.],
              [ 2.,  0.,  0.],
              [ 0.,  1., -1.]])
X_scaled = preprocessing.scale(X)
X_scaled
```




    array([[ 0.        , -1.22474487,  1.33630621],
           [ 1.22474487,  0.        , -0.26726124],
           [-1.22474487,  1.22474487, -1.06904497]])




```python
X_scaled.mean(axis=0)
```




    array([ 0.,  0.,  0.])




```python
X_scaled.std(axis=0)
```




    array([ 1.,  1.,  1.])



## 1.1.2  将特征缩放到一个范围
大部分情形下我们希望将特征缩放到0，1之间，用`MinMaxScaler`与之前标准化的区别就是，可以保留稀疏数据中的0. 
>例子：


```python
X_train = np.array([[ 1., -1.,  2.],
                    [ 2.,  0.,  0.],
                    [ 0.,  1., -1.]])
min_max_scaler = preprocessing.MinMaxScaler()
X_train_minmax = min_max_scaler.fit_transform(X_train)
X_train_minmax
```




    array([[ 0.5       ,  0.        ,  1.        ],
           [ 1.        ,  0.5       ,  0.33333333],
           [ 0.        ,  1.        ,  0.        ]])



## 1.1.3 处理类别数据
比如一个人可能有以下数据`["男", "女"], ["中国", "日本", "美国"], ["用ie", "用firefox", "用chrome", "用其它"]`，这些类别特征虽然可以很容易用数字编码，但是这些用整数（离散型）编码的很难被算法用来学习，因为它们大部分都只接受连续型数据。   
一种常用的方法就是进行`独热编码`，它将类别特征中m个可能的值转换为m个二值特征，每条数据只有一个有效。
>例子：


```python
enc = preprocessing.OneHotEncoder()
enc.fit([[0, 0, 3],
                 [1, 1, 0],
                 [0, 2, 1],
                 [1, 0, 2]])
```




    OneHotEncoder(categorical_features='all', dtype=<type 'numpy.float64'>,
           handle_unknown='error', n_values='auto', sparse=True)




```python
enc.transform([[0, 1, 3]]).toarray()
```




    array([[ 1.,  0.,  0.,  1.,  0.,  0.,  0.,  0.,  1.]])



## 1.1.4 缺失值的处理
由于很多原因，我们的数据会有缺失值（NaN）,必须对这些值进行处理，因为分类器只能接受连续型数值数据。最简单的方法就是删除有缺失值的记录，这只能在有缺失数据的记录较少时使用，因为这样很可能会同时删除一些有价值的数据，所以常用的方法就是根据已有数据进行插值（`Imputer`类）（用均值，中位数，出现频率最高的数等等）。
>例子：


```python
import numpy as np
from sklearn.preprocessing import Imputer
imp = Imputer(missing_values='NaN',strategy='mean', axis=0)
print(imp.fit_transform([[1, 2], [np.nan, 3], [7, 6]]))
```

    [[ 1.  2.]
     [ 4.  3.]
     [ 7.  6.]]


## 1.1.5 生成多项式特征
有时在考虑模型时需要使用非线性模型，这时使用`PolynomialFeatures`，
>例子：将$(X_{1}, X_{2})$转换为$(1, X_{1}, X_{2}, X_{1}^2, X_{1}X_{2}, X_{2}^2)$


```python
import numpy as np
from sklearn.preprocessing import PolynomialFeatures
X = np.arange(6).reshape(3, 2)
X
```




    array([[0, 1],
           [2, 3],
           [4, 5]])




```python
poly = PolynomialFeatures(2)
poly.fit_transform(X)
```




    array([[  1.,   0.,   1.,   0.,   0.,   1.],
           [  1.,   2.,   3.,   4.,   6.,   9.],
           [  1.,   4.,   5.,  16.,  20.,  25.]])



## 1.1.6 将函数变成转换器
有时我们需要把一个现成的函数对数据的每列使用，当然我们可以使用匿名函数而避免用循环，还有一种方法就是用转换器，之前的例子中可以看到，在sklearn中转换器可以方便的对列或者行使用。
>例子：


```python
import numpy as np
from sklearn.preprocessing import FunctionTransformer
transformer = FunctionTransformer(np.log1p)
X = np.array([[0, 1], [2, 3]])
transformer.transform(X)
```




    array([[ 0.        ,  0.69314718],
           [ 1.09861229,  1.38629436]])


