<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            }
        });
    </script>
</head>

# 运维领域的关联分析调研

本文旨在调研运维领域中的关联分析方法，特别是使用事件序列分析关联的方法。

一般来讲，关联分析方法有几大类：基于频繁项挖掘的（Apriori, FP-growth）、基于图结构的等

## 基于频繁项挖掘的工作

Apriori 最早由 Agrawal 提出，通过多次迭代建立候选集查找频繁项。在[22]中，作者对大规模操作系统中事件序列间的相关性进行了研究，
为了方便对事件序列的相关性进行研究，作者首先将冗长的事件转化为不同的事件类型，并根据事件类型序列数据定义了 episode：
认为在时间窗口 TW 内发生的所有事件类型即为一个 episode，并记为$E_{eA}, T_{eA}$，其中$E_{eA}$为与事件𝑒A相邻的所有事件的集合， 
$T_{eA}$为对应的时间窗口。然后，文中用频繁项查找算法 Apriori 对 episode 序列中频繁项集进行搜索，而这种频繁项集的形式就被认定为
事件之间的相关性。文中利用不同 h-置信度与 Apriori 中修剪压缩比的变化曲线关系，自动求出最适宜的最小支持度，从而对频繁项集进行修剪。

HJ Lu[23]认为经典的关联规则挖掘忽略了事物发生的语境，如时间、地点等。作者认为项目关联有两种：1.事物内的频繁项关联（如，同一天内，
两个股票一起涨）；2.不同事物间的频繁项关联（如 A 股票第一天涨了后，B 股票在第四天有较大概率也涨），而传统的频繁项关联算法只局限于
查找关联 1。因此文中对Apriori 算法进行了扩展，以提出一种 Extension-Apriori 算法，将关联规则挖掘的范围从传统的单维度关联扩展到
多维的事物间关联，并研究了多维事件关联规则中支持度与置信度的计算方式。同时算法利用哈希技术过滤掉不必要的候选二项集，将所有可能的二
项集散列到一个哈希表中，减少了数据库扫描的复杂度。

但由于 Apriori 算法每一次增加频繁项集大小时都需要重新扫描整个数据集，所以当数据集很大时，算法效率较低，因此有许多研究是针对如何将 
Apriori 算法进行优化提速。如[24]研究了频繁项挖掘算法在 MapReduce 框架中的实现。文献[24]将串行的 Apriori 算法转化为分布式的 
MapReduce 版本，在每一次查找频繁项集时，使用 map 生成候选支持，并用 reduce 收集全局的候选支持。并且算法可以根据候选对象的数量与前一个 
MapReduce 阶段的执行时间，动态的收集可变长度的候选对象，极大地缩短了 Apriori 生成频繁项集的时间。 

频繁模式生长算法（FP-growth）是最早由韩家炜等人提出的利用频繁模式树进行频繁项挖掘的算法。相比 Apriori，FP-growth 只用遍历两遍数
据，且不需要产生候选序列，极大提高了挖掘效率。

因此也有许多研究人员通过 FP-growth 来挖掘序列中的频繁项。文献[25]中，作者提出了一种并行化 FP-Growth 算法的 MapReduce 方法，将大规
模的频繁项挖掘任务自动分割成独立的计算任务，并将其映射到 MapReduce 框架中。作者用提出的方法对包含网页与标签的事件序列数据库进行网页间
相关度的计算，从而实现有效的相关网页推荐。

而传统的Apriori 和FP-growth 算法都是基于最小支持度的频繁项搜索算法，因此存在以下两个问题：1.当最小支持度设置较大时，包含稀有项的频繁
项会被过滤掉；2.当最小支持度设置较小时，则会生成过多的频繁项导致计算量爆炸。对于 FP-Growth 算法，由于每个项目都有最低支持度，因此用户
很难一次为所有的项目设置适当的阈值，所以用户通常需要多次优化算法的参数，直到达到满意的结果。

基于上述问题，文献[26]提出一种MIS-Tree 结构和名为CFP-Growth 的算法，与FP-growth 不同，CFP-Growth 中所有的输入项目以最小支持度进行
降序排列，然后将所有的项目输入到树结构中，构建一个类似 FP-tree 的树状结构称为 MIS-Tree，同时测量树中各项目的支持度。然后对树中所有支
持度小于全部项目中最小支持度的项进行修剪，并对含有相同父节点的项进行合并，以保证树结构的紧凑性，得到的即为最小支持度项目树(MIS-Tree)。
最后只需要将 MIS-Tree 中每个项目作为后缀项并进行扫描就可以发现完整的频繁模式集。文中作者分别在合成数据集和真实数据集上进行测试，结果
表明该算法更加有效与快速。

```
Reference

[22]Gupta C. Event correlation for operations management of largescale IT systems[C]// Proceedings of the 9th international conference on Autonomic computing. 2012.
[23]Hongjun Lu, Ling Feng, and Jiawei Han. 2000. Beyond intratransaction association analysis: mining multidimensional intertransaction association rules. ACM Trans. Inf. Syst. 18, 4 (October 2000), 423–454.
[24]Ming-Yen Lin, Pei-Yu Lee, and Sue-Chen Hsueh. 2012. Apriori-based frequent itemset mining algorithms on MapReduce. In Proceedings of the 6th International Conference on Ubiquitous Information Management and Communication (ICUIMC ’12). Association for Computing Machinery, New York, NY, USA, Article 76, 1–8.
[25]Haoyuan Li, Yi Wang, Dong Zhang, Ming Zhang, and Edward Y. Chang. 2008. Pfp: parallel fp-growth for query recommendation. In Proceedings of the 2008 ACM conference on Recommender systems (RecSys ’08). Association for Computing Machinery, New York, NY, USA, 107–114.
[26]Y.-H. Hu and Y.-L. Chen. Mining association rules with multiple minimum supports: a new mining algorithm and a support tuning mechanism. Decis. Support Syst., 42(1):1–24, 2006.

```
