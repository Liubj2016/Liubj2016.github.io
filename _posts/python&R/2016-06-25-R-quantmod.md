---
layout: post  
categories: [python&R]  
title: R-quantmod包  
description: 每次都有新发现！
---


## 1.获取股票数据

1.1 获取上证指数


```r
getSymbols("^SSEC")
```

1.2 获取三一重工数据

```r
setSymbolLookup(SANY.HEAVY=list(name="600030.ss",src="yahoo"))
getSymbols("SANY.HEAVY")
```

## 2.获取期权交易数据


```r
getSymbols("AAPL")
options.expiry(AAPL)
futures.expiry(AAPL)
AAPL[options.expiry(AAPL)]
```

## 3.获取汇市数据


```r
getFX("USD/JPY")
```

## 4.获取重金属交易数据


```r
getFX(c("gold","XPD"))
```

## 5.获取美联储经济数据

```r
getSymbols('CPIAUCNS',src='FRED')
```

# 提取数据的函数

- Op(x):提取开盘价
- Hi(x):提取最高价
- Lo(x):提取最低价
- Cl(x):提取收盘价
- Vo(x):提取交易量
- Ad(x):提取调整价格
- HLC(x):提取最高价、最低价和收盘价
- OHLC(x):提取开盘价、最高、最低和收盘价

# 操作函数


```r
Stock.Open <- c(102.25,102.87,102.25,100.87,103.44,103.87,103.00)
Stock.Close <- c(102.12,102.62,100.12,103.00,103.87,103.12,105.12)
#以开盘价计算收益率
Delt(Stock.Open)
#计算开盘价和下一期收盘价的差
Delt(Stock.Open,Stock.Close,1)
```

- OpCl(x):等同于Delt(Op(x), Cl(x))
- ClCl(x):等同于Delt(Cl(x))
- HiCl(x):等同于Delt(Hi(x),Cl(x))
- LoCl(x):等同于Delt(Lo(x),Cl(x))
- LoHi(x):等同于Delt(Lo(x),Hi(x))
- OpHi(x):等同于Delt(Op(x),Hi(x))
- OpLo(x):等同于Delt(OP(x),Lo(x))
- OpOp(x):等同于Delt(Op(x))


# 计算收益率



```r
dailyReturn(x)
weeklyReturn(x)
monthlyReturn(x)
quarterlyReturn(x)
```


# 画图


```r
#主图
chartSeries(x)
#条形图
barChart(CHL)
#蜡烛图
candleChart(CHL)
#线图
lineChart(CHL)
```
