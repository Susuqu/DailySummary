# Why
- _**为什么开始这个文档呢？**_ 始于git的约定，为了更好的督促学习和get新的知识，我都会认真去读小伙伴写的帖子，有时候有疑问、有时候为了跟上思路需要自己去补充基本知识、有时候发现有些很好的东西以后会用到……反正基于这些点，我觉得需要集中记录一下，然后有空的时候可以review看看强化，所以……

# What
- _**那么在这个文档里有什么呢？**_ 笔记咯~

# Who

- _**Susu, start at 05/19**_  

---

## CNV 背景介绍

【[原始的文献来源：# Computational tools for copy number variation (CNV) detection using next-generation sequencing data: features and perspectives](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1)】
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
## 第六届数学、计算机与生命科学交叉研究青年学者论坛会议summary

今天去参加了一年一度的“第六届数学、计算机与生命科学交叉研究青年学者论坛”，感触也很多，最大的不同是发现终于很多东西我能听懂了……科研也是一个圈子，大腿抱大腿，需要不断的参加这种学术会议来更新自己的知识体系，以及借鉴别人优秀的东西。虽然全程困啊困啊，但是现在想想无数个想放弃的瞬间却最终坚持下来了依然是有收获的，因为整理了一下这几天的东西还蛮有收获的：

1.一些在招博士后的最一手的信息；
- [西安交通大学叶凯](http://info.xjtu.edu.cn/info/1019/20468.htm)
- [同济大学张勇-长期有效](http://life.tongji.edu.cn/Data/View/372)
- [UCLA-邢毅](https://github.com/Xinglab/Xinglab.github.io)
- [中山大学-骆观正](http://lifesciences.sysu.edu.cn/zh-hans/node/258)
- [北京大学-张泽民](http://cancer-pku.cn/index.php/positions/pd1/)

2.发现做蛋白结构预测的人还挺多的，这些学者的研究是更深入的，会去从生物学的背景、要阐释的科学问题的角度出发，而不是直接停留在机器学习的算法层面。之前我的认知一直觉得还蛮简单的，现在想想真是够肤浅了。ppt里有一些好的片子如果后续研究相关的内容可以借鉴。

3.偶然听到一个老师讲从GWAS结果和PPI后的基因间的上位显性作用出发来进行科学问题的解释，感觉对之前药物靶点的那个问题豁然开朗，所以真的是要经常听听别人讲才会有更好的科研进展。相关PPT的文献在endnote里已经找到。

4.很多研究者都在关注科学的前沿，追踪最新的文献动态，其实也只有这样才能做出漂亮的东西~所以看文献啊看文献，哈哈哈！

5.下面记录的就是一些被扫盲的内容了，好多前沿的概念、技术方法第一次听说，回来自己又查了查，涨知识了。

**DARTS DNN 预测可变剪接：** Deep-learning Augmented RNA-seq analysis of Transcript Splicing
[Xinglab DARTS website](https://github.com/Xinglab/DARTS)，看了下这个安装应该不是特别复杂，而且是基于python环境的，刚好也是机器学习相关的内容。产生了一个想法，是否可以用RNAseq的那批数据做一个测试看看能否鉴别出可变剪切，mark一下，后续进行一个尝试。

**表观遗传优质文章ppt：** 之前给boss做ppt的时候关于表观遗传这块一直无法找到特别好的素材、文献也不是特别有代表性，刚好这次会议有大牛介绍了相关的内容，ppt很不错，如果后续需要用到可以参考下上面相关的素材。

**RNA甲基化：MeRIP-seq** 
也是通过这个会议才了解到原来RNA还有甲基化呢，扫盲了。**什么是RNA甲基化？** RNA甲基化指发生在RNA分子上不同位置的甲基化修饰现象，常见的RNA转录后修饰方式有6-甲基腺嘌呤(N6-methyladenosine，m6A) 和5-甲基胞嘧啶(C5-methylcytidine，m5C)等。最新研究发现，m6A修饰在调控基因表达、剪接、RNA 编辑、RNA 稳定性、控制mRNA寿命和降解、介导环状RNA翻译等方面扮演重要角色。因此meRIP-seq助力解决细胞分化，生物发育、疾病发生发展，热休克反应等生物学问题。利用甲基化RNA免疫共沉淀结合高通量测序 (Methylated RNA Immunoprecipitation sequening，MeRIP-seq)技术，可以对RNA转录后甲基化修饰图谱进行全面研究，是表观转录组学研究的关键技术。这部分内容是**中山大学的骆观正**讲的，最后致谢的时候他提到了**易汉博基因科技的陈同**，然后就感慨，世界真小，生信的圈子也就这么大……

**allele specific expression (ASE)** 等位基因特异性表达（ASE）是癌症的重要特征之一，这个概念还真是第一次听说，虽然也没太懂啥意思吧。

**Gene Expression Profiling Interactive Analysis** 
这个工具首有的手机APP，然后是网页版的工具。页面做的很炫，但是只能做癌症相关数据的分析，因为她们的数据来源就是TCGA和GTEx，那这种思路其实在精神疾病中也是有应用的，而且蛮多的。
- GE-mini: a mobile APP for large-scale gene expression visualization
- [Gene Expression Profiling Interactive Analysis](http://gepia.cancer-pku.cn/index.html)

**3Disease Browser** 
一个很有意思的内容，a web server for human 3D genome structure and disease associated CR events，那么CR是指是呢？Chromosomal rearrangement (CR) event may disrupt genes and other functional structures. 其实CR就是染色体的重排。在网站上对几个**精神疾病**进行检索，结果挺有意思的，像SZ的结果记录很少，还没有ADHD的多，以及结果也不如ADHD的显著，不知道是因为数据没有收录，还是说现有发现没有对应的比较好的结果：Attention deficit hyperactivity disorder，最显著的P值是0.004692737。但是里面没有关于PTSD的疾病记录。[3D browser website](http://3dgb.cbi.pku.edu.cn/disease/) 看了下李程老师当时的ppt，这个server是有对应的文章的，如果后续有时间找来看看数据收录方式就知道是怎么回事了。

**参加会议的时候别人分享了一个工具，call SV的工具：**
- MetaSV: an accurate and integrative structural-variant caller for next generation sequencing
- [对应的github website](http://bioinform.github.io/metasv/)
ps：偶然发现这个团队对应的GitHub的仓储下也有RNACocktail那个，所以不知道是不是一个团队开发的，以及貌似这个团队是Roche？先Mark，如果以后需要call SV可以尝试。

ppt里还有一些跟大数据、遗传变异等内容相关的ppt，文献也都下载了，但目前不知道怎么加到我的ppt里，今天先记录到这里，后续有更新再补充吧。
[Image by J.Oksenberg/UCSF](https://www.ucsf.edu/news/2011/08/10431/major-genetic-study-multiple-sclerosis-reveals-dna-hot-spots-disease)

![Most diseases are controlled by multiple genes](./images/environment_epigenetic.PNG)

---
## 宏基因组 & 进化树

写这部分内容的起因是需要帮Ma bo那边调研一下MEGA这个软件怎么用，原以为应该是特别简单的一个做进化的软件，但我一查发现还有点复杂啊，以及现在很多做宏基因组的人用这个比较多，然后想做好进化树也是需要很多背景知识的，所以就在学习的过程中写写关键信息。

**但提醒自己这个只是一个扩充知识的过程，不要弄太细……没那么多时间！所以比如要做到的程度是：哪个地方需要选模型；首先需要提供什么数据；……而不是去告诉她该怎么选择模型，目前时间有限且掌握的内容有限，一定要有侧重！**

- [科普帖子—宏基因组——生信技能树](www.biotrainee.com/thread-157-1-1.html)
- [科普帖子—系统进化树基本知识——生信技能树](http://www.biotrainee.com/thread-1521-1-1.html)

因为具体也不知道mabo那边到底要干嘛，也没告诉我具体的事情，明天下午就抽时间看看[说明文档](https://www.megasoftware.net/web_help_7/helpfile.htm#hc_first_time_user.htm)就好了

--- 
## Variant 分析
### 什么是遗传变异？
所谓的遗传变异就是生物体内遗传物质发生变化而产生的可以遗传给后代的变异，生物体内的这些变异导致了生物体在不同水平上体现出遗传多样性。生物信息学中各种基因组学就是对这些遗传变异进行研究。

### 遗传变异的类型
常见的就是哪几种类型，区分的简单原则就是有几个位点改变了：SNP是单个核苷酸的改变，indel通常是50bp以下的变异，SV和CNV则要更长。（SNP 和 SNV 都是单碱基的突变，但是SNP 是多了一个频率属性的SNV，比如在群体中1%以上。）

- Synonymous SNP：如果SNP发生在编码区，根据密码子简并性 SNP 不一定会引起编码氨基酸的改变，不引起任何变化的叫做Synonymous SNP。
- Non-Synonymous SNP：引起氨基酸变化的叫做Non-Synonymous SNP。
- 错义突变：如果编码的某种氨基酸的密码子变成另一种，会导致多肽链的氨基酸种类和序列发生改变，这就是一个错义突变。
- 无义突变：当突变使一个编码氨基酸的密码子变成终止子时，则蛋白质合成进行到该突变位点时会提前终止，这时就是无义突变。

### 检验遗传变异的原理
基于高通量数据中的reads在某个位点上的碱基，同时结合概率分布、统计等进行检验。基因组结构变异的检测主要有4种思路（我看到这就想起来CYL之前写的那个帖子了，就又回去翻了翻，发现这里其实漏了一个组合的检测思路，所以实际应该是5种）：
- 双端 reads 连配 (pair-end mehtod)：首先进行mapping，然后评价双端reads的方向信息和距离是否与建库结果一致；
- reads 覆盖深度 (read-depth method)：多用于检测拷贝数变异，假设比对到基因组的覆盖深度符合泊松分布，然后检测与该分布不一致的区域。
- reads 分割法 (split-read)：首先保证双端的一个read 可以完整的唯一比对，然后把另一条read进行拆分再去进行比对。
- 从头组装 (assembly)：啥也不管直接拼，拼完了再去和参考基因组比对。

_**ps：其实我还是不太懂具体原理是啥，但至少是2次刷新对CNV检测原理的印象了，至少这次我能反应起来是有人写过帖子，知道去对比下是不是一样的~ 这就是积累的过程！**_

### 转换（Transition）和颠换（Transversion）
转换(transition)则是嘌呤被嘌呤，或嘧啶被嘧啶替代，颠换(transversion)是指嘌呤与嘧啶的变化。转换突变比颠换突变更常见，且与颠换相比在氨基酸序列上产生差异的可能性更低。一般Transition 是 Transversion 数量的2倍。


