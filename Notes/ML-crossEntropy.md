---
layout: page
title: "Understanding Cross-Entropy Losses"
---

L=−[ylog y^+(1−y)log (1−y^)]


## 交叉熵损失函数的数学原理
我们知道，在二分类问题模型：例如逻辑回归「Logistic Regression」、神经网络「Neural Network」等，真实样本的标签为 [0，1]，分别表示负类和正类。模型的最后通常会经过一个 Sigmoid 函数，输出一个概率值，这个概率值反映了预测为正类的可能性：概率越大，可能性越大。

Sigmoid 函数的表达式和图形如下所示：

---------------------

本文来自 红色石头Will 的CSDN 博客 ，全文地址请点击：https://blog.csdn.net/red_stone1/article/details/80735068?utm_source=copy 
