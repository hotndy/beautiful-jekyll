---
layout: page
title: "Understanding Cross-Entropy Losses"
---

L=−[ylog y^+(1−y)log (1−y^)]


## 交叉熵损失函数的数学原理
我们知道，在二分类问题模型：例如逻辑回归「Logistic Regression」、神经网络「Neural Network」等，真实样本的标签为 [0，1]，分别表示负类和正类。模型的最后通常会经过一个 Sigmoid 函数，输出一个概率值，这个概率值反映了预测为正类的可能性：概率越大，可能性越大。

Sigmoid 函数的表达式和图形如下所示：
g(s)=11+e−s

![]()
<p align="center">
<img src="https://img-blog.csdn.net/20180619153839186?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlZF9zdG9uZTE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" width="500px"/>
</p>
