---
layout: lay_post
title: "机器学习算法-分类-LogisticRegression(逻辑回归)"
date: 2016-11-23
categories: 分类算法
tags: 机器学习
author: lvyafei
summary:
published: true
---

* 目录
{:toc #meuid}

## 0.概述

监督学习问题分为“回归”(regression)和“分类”(classification)问题。LinearRegression(线性回归)属于"回归"问题，而LogisticRegression(逻辑回归)属于"分类"问题。
<!-- more -->

## 1.LogisticRegression(逻辑回归)

现在我们正在从回归问题切换到分类问题。不要被“逻辑回归”的名字混淆，它被命名为历史原因的方法，实际上是一种分类问题的方法，而不是回归问题。

**Sigmoid Function(S函数):**

![S函数](/images/算法/逻辑回归/S函数.png)

我们的假设应该满足：

![函数范围](/images/算法/逻辑回归/函数范围.png)

逻辑回归的假设函数：

![逻辑回归函数](/images/算法/逻辑回归/逻辑回归函数.png)

针对分类问题，当假设函数预测的值达到一定概率后就判定为指定类别，预测值为:

![预测函数概率](/images/算法/逻辑回归/预测函数概率.png)

**Decision Boundary(决策边界):**

决策边界控制分类的界限，当预测函数值大于0.5就分类为1，当预测函数的值小于0.5就分类为0。针对S函数，当S函数中的X大于0是S函数就结果就大于0.5，相反则小于0.5。
0.5就是决策边界，改变这个边界将影响到分类的结果。

当边界为0.5时，在逻辑函数里面就是假设函数为0的情况。

![预测分类](/images/算法/逻辑回归/预测分类.png)

**Cost Function(代价函数):**

![逻辑回归代价函数](/images/算法/逻辑回归/逻辑回归代价函数.png)

对数函数模型:

![对数函数](/images/算法/逻辑回归/对数函数.png)

代价函数分析:

![逻辑回归-代价函数](/images/算法/逻辑回归/逻辑回归-代价函数1.png)

![逻辑回归-代价函数](/images/算法/逻辑回归/逻辑回归-代价函数.png)

精简版代价函数:

![逻辑回归-代价函数](/images/算法/逻辑回归/逻辑回归-代价函数2.png)

![逻辑回归-代价函数](/images/算法/逻辑回归/逻辑回归-代价函数3.png)

向量化:

![逻辑回归-代价函数](/images/算法/逻辑回归/逻辑回归-代价函数向量化.png)

**Gradient Descent(梯度下降):**

![逻辑回归-梯度下降](/images/算法/逻辑回归/逻辑回归-梯度下降.png)

**多分类:One-vs-all**

![逻辑回归-多分类](/images/算法/逻辑回归/逻辑回归-多分类.png)

我们先是选择一类，然后将所有的其它分到一个单一的二类。我们这样做是反复的，对每一种情况下应用二元逻辑回归，然后使用返回的最高值作为我们的预测的假设

## 2.Regularization(正则化)

正则化是设计来解决过度拟合的问题。

**正则化线性回归-梯度下降**

![逻辑回归-正则化代价函数](/images/算法/逻辑回归/逻辑回归-正则化代价函数.png)

![逻辑回归-正则化代价函数1](/images/算法/逻辑回归/逻辑回归-正则化代价函数1.png)

**正则化逻辑回归-代价函数**

![逻辑回归-正则化代价函数2](/images/算法/逻辑回归/逻辑回归-正则化代价函数2.png)

**正则化逻辑回归-梯度下降**

![逻辑回归-正则化梯度下降](/images/算法/逻辑回归/逻辑回归-正则化梯度下降.png)

## 3.广义线性模型

逻辑回归与多重线性回归实际上有很多相同之处，最大的区别就在于它们的因变量不同，其他的基本都差不多。正是因为如此，这两种回归可以归于同一个家族，即广义线性模型（generalizedlinear model）。

这一家族中的模型形式基本上都差不多，不同的就是因变量不同。

1.如果是连续的，就是多重线性回归；

2.如果是二项分布，就是Logistic回归；

3.如果是Poisson分布，就是Poisson回归；

4.如果是负二项分布，就是负二项回归。

Logistic回归的因变量可以是二分类的，也可以是多分类的，但是二分类的更为常用，也更加容易解释。所以实际中最常用的就是二分类的Logistic回归。

Logistic回归的主要用途：

寻找危险因素：寻找某一疾病的危险因素等；

预测：根据模型，预测在不同的自变量情况下，发生某病或某种情况的概率有多大；

判别：实际上跟预测有些类似，也是根据模型，判断某人属于某病或属于某种情况的概率有多大，也就是看一下这个人有多大的可能性是属于某病。

Logistic回归主要在流行病学中应用较多，比较常用的情形是探索某疾病的危险因素，根据危险因素预测某疾病发生的概率，等等。例如，想探讨胃癌发生的危险因素，可以选择两组人群，一组是胃癌组，一组是非胃癌组，两组人群肯定有不同的体征和生活方式等。这里的因变量就是是否胃癌，即“是”或“否”，自变量就可以包括很多了，例如年龄、性别、饮食习惯、幽门螺杆菌感染等。自变量既可以是连续的，也可以是分类的。