---
layout: post
title: "Agent-based modelling of reactive vaccination of workplaces and schools against COVID-19"
date:   2022-05-26
tags: [covid_nature-communications]
comments: true
author: minty
---

​	随着针对Covid-19的疫苗接种在某些国家停滞不前，增加疫苗的可及性和分配可能有助于控制传播。在这里，我们研究了针对检测到病例的学校和工作场所的反应性疫苗接种的影响，该模型基于代理模型，该模型占据了COVID-19的自然历史，疫苗特征，人口统计学，行为变化和社会疏远。在大多数情况下，与使用相同剂量的非反应性策略相比，反应性疫苗接种导致病例的减少更高。这些结果提供了关键信息，以计划自适应疫苗接种。

<!-- more -->

## 方法

**Agent-based SEIR model**. 

图a代表不同size的workplace、不同type的school的个数，用于Synthetic population.

图b代表不同网络的联系，黄圈内的是密切接触者，红色是小阳人。绿色是与小阳人同单位/家庭，不是密切接触且打了疫苗的。

图C是常规的covid transmission图。如果与传染性人接触，易感人士可能会被感染并进入expose状态（E）。在平均潜伏期$1/\epsilon=3.7days$之后，它们变得具有感染性，形成亚临床感染（ISC），和临床感染（IC）。从E输入ISC或IC之前，个人首先进入A前段，平均持续2.1天。无症状感染者的传播率下降了51%。参数及其值总结在补充表1中。

文中用到了疫苗保护率这一数值，主要影响S->I的阶段和E(V)->I的过程，整个状态图和日常的covid论文类似，没什么变化。

**TTI**

一但某人阳了，那他的家人就被隔离，其他的熟人、零星接触的人分别以一定的概率（table 3）被隔离。无症状感染者在10天后正常的话出院，如果在10天内正常的话可以以13%的概率选择提前离开。文章还讨论了两种情形，一种严一种松。在Supplyment中有详细介绍。



![54901d22cb04a75e5a73d225f05bbaf](C:\Users\weimy\AppData\Local\Temp\WeChat Files\54901d22cb04a75e5a73d225f05bbaf.png)



**Vaccination strategies.**

这部分比较重要，在国内没使用过，可以分析一波作为政策之一。这部分需详细解释，慢慢来。

![e7ab4320a70d3d2cbec903ad09d2a57](C:\Users\weimy\AppData\Local\Temp\WeChat Files\e7ab4320a70d3d2cbec903ad09d2a57.png)

## 致谢

感谢 [Jekyll](https://www.jekyll.com.cn/) 提供的技术支持才能有这个博客。

感谢 [LOFFER ](https://fromendworld.github.io/LOFFER/document/)提供的原始模板，我在其上进行的二次开发。

