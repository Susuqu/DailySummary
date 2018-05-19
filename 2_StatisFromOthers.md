# Why
_**为什么开始这个文档呢？**_ 始于git的约定，为了更好的督促学习和get新的知识，我都会认真去读小伙伴写的帖子，有时候有疑问、有时候为了跟上思路需要自己去补充基本知识、有时候发现有些很好的东西以后会用到……反正基于这些点，我觉得需要集中记录一下，然后有空的时候可以review看看强化，所以……

# What
_**那么在这个文档里有什么呢？**_ 笔记咯~

# Who

_**Susu, start at 05/19**_  

---



## CNV 背景介绍【[原始的文献来源：# Computational tools for copy number variation (CNV) detection using next-generation sequencing data: features and perspectives](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1)】
### variants种类：
Genomic variation is comprised of single nucleotide variants (SNVs), small insertions or deletions (indels), copy number variations (CNVs), and large structural variants (SVs); these variants range from single base changes to large chromosomal-level alterations [[1](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#CR1)]

### CNV定义：
- 文章原文：CNV refers to a type of intermediate-scale SVs with copy number changes involving a DNA fragment that is typically greater than one kilobases (Kb) and less than five megabases (Mb) [[2](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#CR2)].
- 百度百科：拷贝数目变异（拷贝数变异，CNV）也称拷贝数目多态（拷贝数多态性，CNP），是一种大小介于1 KB至3 MB的DNA片段的变异，在人类基因组中广泛分布其覆盖的核苷酸总数大大超过单核苷酸多态性（单核苷酸多态性，SNP）位点的总数，并就CNV在动物基因组中的研究进行了展望。

### 传统的CNV检测方式：
employs cytogenetic technologies, such as karyotyping and fluorescence _in situ_ hybridization (FISH) [[9](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#CR9)].
细胞遗传学技术，如核型分析和荧光原位杂交FISH

### 技术发展后的CNV检测方式：
随着芯片和测序技术的发展，逐渐发展出了不同的工具（基于不同的算法原理）用于鉴别CNV，这篇综述主要呈现了37种工具的检测策略，共可以归纳为：通过NGS数据鉴定CNV的5种策略——paired-end mapping (PEM), (2) split read (SR), (3) read depth (RD), (4) _de novo_ assembly of a genome (AS), and (5) combination of the above approaches (CB)。


### 目前我们在使用的检测CNV的方式为：
- GATK（最终使用的）；
- CNVkit（尝试过的，但没有最终使用）；



### call CNV的原理：
call CNV的方法就是通过基因组不同区域的Read Depth数来确定，但是具体用了的统计学模型看不懂


知乎上看了一个帖子：CNV因为绝大部分是打在noncoding区上的，而WES测序的方式是noncoding区的信息丢失；其次，WES在捕获过程中，探针可能会对序列有偏好性，导致reads的覆盖度的波动非常大，而这些波动很容易被误判为CNV，所以假阳性特别高。因此针对不同的测序方式要选择合适的算法才可以准确的call 出CNV。



### call CNV的工具：
- CNVkit, 2014年发表在_PLOS Computational Biology_杂志上：
	- [official website](http://cnvkit.readthedocs.io/en/stable/)
	- [生信菜鸟团](http://www.bio-info-trainee.com/2859.html)，但我看这个链接上写的cnvkit主要是对肿瘤配对样本的wes来寻找cnv啊，所以我们服务器上也用这个，合适么？


---
## 统计相关
“三种常用的误差线，标准差（s.d.），标准误（s.e.m）还有置信区间（CI）”，我以前只知道：标准差和标准误这两个。有一个疑问是，既然文章对比了有差别，那么这3种描述误差线的指标分别在什么情况下使用更合适呢？

样本和总体之间的一些参数对比：
![样本和总体之间的一些参数对比](./images/static_table.PNG)


---

今天去参加了一年一度的“第六届数学、计算机与生命科学交叉研究青年学者论坛”，感触也很多，最大的不同是发现终于很多东西我能听懂了……科研也是一个圈子，大腿抱大腿，需要不断的参加这种学术会议来更新自己的知识体系，以及借鉴别人优秀的东西。


