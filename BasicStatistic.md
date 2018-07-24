## 基础统计分析原理简介

**Qu Susu**，纯走心搜罗整理！！！

* [0.基础科普forMyself & you ?](#0)
* [1.相关系数类](#1)
	* [1.1皮尔森(pearson)相关系数](#1.1)
	* [1.2斯皮尔曼(spearman)相关系数](#1.2)
* [2.方差分析类](#2)
	* [2.1单因素方差分析](#2.1)
	* [2.2多因素方差分析](#2.2)
	* [2.3重复试验多因素方差分析](#2.3)
	* [2.4多元方差分析](#2.4)
	* [2.5多因素多元方差分析](#2.5)
* [3.t检验类](#3)
	* [3.1独立样本t检验](#3.1)
	* [3.2配对样本t检验](#3.2)
* [4.秩和检验/秩检验](#4)
	* [4.1曼惠特尼秩和检验](#4.1)
	* [4.2Kruskal-Wallis秩和检验](#4.2)
	* [4.3威尔科克森符号秩检验](#4.3)
* [5.列联表分析](#5)
	* [5.1卡方检验](#5.1)
	* [5.2高纬列联表分析](#5.2)
* [6.回归分析](#6)
	* [6.1逻辑回归](#6.1)
	* [6.2多元线性回归](#6.2)


<h2 id="0">0.基础科普forMyself & you ?</h2>

**参数检验 & 非参数检验**：简单来说就是当总体分布已知（给定或者假定）时用参数检验；总体分布未知时，用样本数据对总体分布形态推断。
	- 优缺点对比【暂时省略】：



<h2 id="1">1.相关系数类</h2>
[科普网址](https://blog.csdn.net/mmc2015/article/details/51942066)
**作用：** 评价两组数据之间的相关性。统计学有三大相关系数：pearson，spearman，Kendall。后面两者属于等级相关系数，也叫做“秩相关系数”，是反映等级相关程度的统计分析指标。

**实现：** 用python实现，选择是：_**有现成的包，就不自己写函数；有多个包，就测试下不同的包结果是否相同，优选较熟悉的包。**_
 
<h3 id="1.1">1.1皮尔森(pearson)相关系数</h3>
**作用&适用情况：** 通常用r或是ρ表示，是用来度量两个变量X和Y之间的线性关系的，取值范围在[-1,+1]之间。连续变量，线性相关关系的相关强度。

<h3 id="1.2">1.2斯皮尔曼(spearman)相关系数</h3>
**作用&适用情况：** 用于度量变量之间联系的强弱。在没有重复数据的情况下，如果一个变量是另外一个变量的严格单调函数，则Spearman秩相关系数就是+1或-1，称变量完全Spearman秩相关。注意这和Pearson完全相关的区别，只有当两变量存在线性关系时，Pearson相关系数才为+1或-1。

**应用：** 在机器学习中，当要预测不同的机器学习算法在同一个学习任务上的性能时，需要使用序相关系数对真实的性能排序与预测的性能排序进行比较，本文介绍了其中一种秩相关系数——斯皮尔曼等级相关性。公式：

$$
ρ=1-6∑(di)^2/n(n^2-1)
$$
其中：
- di=xi-yi表示两个排序之间的差值；
- n:表示样本的大小，即机器学习算法的数量；

---
<h2 id="2">2.方差分析类</h2>
方差分析（analysis of variance）:缩写为ANOVA，分析分类自变量对数值因变量影响的一种统计方法。

单因素方差分析（one-way analsis of variance）:研究一个分类自变量对数值因变量影响的方差分析。

双因素方差分析（two-hway analysis of variance）:研究两个自变量对数值因变量影响的方差分析。它分为只考虑主效应的双因素方差分析和考虑交互效应的双因素方差分析。


方差分析需要满足的假设条件：
- 每个样本数据都来自不同处理的独立样本；
- 样本是来自符合正态分布的群体；
- 每个样本对应总体的方差相等；



<h3 id="2.1">2.1单因素方差分析</h3>
One Way ANOVA
**作用&适用情况：** 对单因素试验结果分析，检验该因素对实验结果是否有显著性的影响。检验多个样本平均数之间的差异。

单因素方差分析所需的服从F分布的检验统计量。


<h3 id="2.2">2.2多因素方差分析</h3>




---

<h2 id="4">4.秩和检验/秩检验</h2>

当正态分布、方差齐性等不能达到t检验的要求时，可以使用非参数检验。其假设基础是：若两个样本有差异，则他们的中心位置将不同。

<h3 id="4.1">4.1Mann-Whitney-Wilcoxon Test,曼-惠特尼U检验</h3>
曼-惠特尼U检验全称为**Mann-Whitney-Wilcoxon Test**用来检验两组独立样品是否来自两组不同的样品。
https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mstats.mannwhitneyu.html


<h3 id="4.2">4.2 kruskal Wallis Test</h3>
for not normally distributed data,多个群组之间比较时，因为群组不满足正态分布而不能使用ANOVA多比较
https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mstats.kruskalwallis.html

[scipy.stats.mstats.kruskal](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mstats.kruskal.html)
[scipy.stats.mstats.kruskalwallis](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mstats.kruskalwallis.html)

<h3 id="4.3">4.3 Wilcoxon Signed-Rank Test，威尔科克森符号秩检验</h3>
威尔科克森符号秩检验又叫**Wilcoxon Signed-Rank Test**用来进行配对样品的非参数检验。
https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.wilcoxon.html#scipy.stats.wilcoxon
it tests whether the distribution of the differences x - y is symmetric about zero. It is a non-parametric version of the paired T-test.



<h2 id="5">5.列联表分析</h2>

<h3 id="5.1">5.1卡方检验</h3>

卡方检验就是统计样本的实际观测值与理论推断值之间的偏离程度，实际观测值与理论推断值之间的偏离程度就决定卡方值的大小。

---
<h2 id="6">6.回归分析</h2>

这个实现起来稍微麻烦一点点，最主要的可能是理解它的原理。
https://blog.csdn.net/u012535605/article/details/70176496?locationNum=14&fps=1

<h3 id="6.1">6.1 逻辑回归</h3>

虽然叫回归，但是实际是一种分类算法。用概率来表示分到某一类的可能性，而不是用离散的方式来表示0或1，[这个帖子举例子说明了为什么要用概率来评估属于哪一个分类](https://blog.csdn.net/wzmhong/article/details/54934453)。
调研了一下发现[statesmodels这个包](http://www.statsmodels.org/stable/py-modindex.html)是可以实现logistics regression[逻辑回归的实例](https://blog.csdn.net/zj360202/article/details/78688070)的，以及这个包可以实现很多的功能。

但我没搞懂和这个的区别scipy.stats.logistic
