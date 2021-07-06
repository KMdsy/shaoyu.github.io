# Causal Discovery

总结用于因果发现的各种包，以及github上star较多的Repositories

## ToolBox

1. gCastle, URL: https://github.com/huawei-noah/trustworthyAI/tree/master/gcastle
  ```
  gCastle是华为诺亚方舟实验室自研的因果结构学习工具链，主要的功能和愿景包括：

  1. 数据生成及处理: 包含各种模拟数据生成算子，数据读取算子，数据处理算子（如先验灌入，变量选择，CRAM）。
  
  2. 因果图构建: 提供了一个因果结构学习python算法库，包含了主流的因果学习算法以及最近兴起的基于梯度的因果结构学习算法。
  
  3. 因果评价: 提供了常用的因果结构学习性能评价指标，包括F1, SHD, FDR, TPR, FDR, NNZ等
  ```


2. Causal Discovery Toolbox, URL: https://github.com/FenTechSolutions/CausalDiscoveryToolbox

  ```
  The Causal Discovery Toolbox is a package for causal inference in graphs and in the pairwise settings for Python>=3.5. 
  Tools for graph structure recovery and dependencies are included. The package is based on Numpy, Scikit-learn, Pytorch and R.
  ```
  
3. URL: https://github.com/jakobrunge/tigramite

  ```
  Tigramite 是一个因果时间序列分析 python 包。它允许从高维时间序列数据集有效地重建因果图，并对获得的因果依赖进行建模，
  以进行因果中介和预测分析。因果发现基于适用于离散或连续值时间序列的线性和非参数条件独立性测试。
  
  包含的因果发现方法：PCMCI、PCMCIplus、LPCMCI
  
  包含的独立性测试方法：ParCorr、GPDC / GPDCtorch、CMIknn、CMIsymb
  ```

4. causalDisco: an R package with tools for causal discovery on observational data, URL: https://github.com/annennenne/causalDisco

  ```
  causalDisco 包括时间 PC的实现，这是 PC 算法的时间版本。
  ```
  
5. Causal Discovery Tools for Time Series Applications - A Collection of Tutorials, URL: https://github.com/savinims/DATAS_Causal_Discovery

  ```
  为大气科学家数据分析工具 (DATAS) 网关的一部分，编写的教程侧重于大气科学应用。数据：https://datasgateway.colostate.edu/
  
  本资料库中解释的方法侧重于观察性研究，其中不进行受控实验（例如，气候中的有针对性的建模研究）来确定原因和影响。
  这些方法允许您识别需要使用我们现有的特定应用领域知识进一步验证的“潜在”关系。
  
  方法包括：二元格兰杰因果检验、PC稳定算法的时间序列扩展
  ```


## Related work with code

1. TCDF: Causal Discovery with Attention-Based Convolutional Neural Networks, URL: https://github.com/M-Nauta/TCDF.

  ```
  时间因果发现框架 (TCDF) 是在 PyTorch 中实现的深度学习框架。给定多个时间序列作为输入，TCDF 发现这些时间序列之间的因果关系并输出因果图。
  它还可以根据其他时间序列预测一个时间序列。TCDF 使用基于注意力的卷积神经网络结合因果验证步骤。通过解释卷积网络的内部参数，TCDF 还可以发现因果之间的时间延迟。
  ```
  
2. Amortize Causal Discovery: Learning to Infer Causal Graphs from Time-Series Data, URL: https://github.com/loeweX/AmortizedCausalDiscovery. 

  ```
  通过 Amortized Causal Discovery，我们学习从具有不同潜在因果图但共享动态的样本中推断因果关系。这使我们能够跨样本进行泛化，从而通过增加训练数据大小来提高我们的性能。
  ```
  
3. Causal Discovery from Nonstationary/Heterogeneous Data: Skeleton Estimation and Orientation Determination. IJCAI 2017. URL: https://github.com/Biwei-Huang/Causal-Discovery-from-Nonstationary-Heterogeneous-Data

4. Causal Discovery in Heavy-Tailed Models, URL: https://github.com/nicolagnecco/causalXtreme
5. Differentiable Causal Discovery from Interventional Data, URL: https://github.com/slachapelle/dcdi
6. Generalized Score Functions for Causal Discovery. KDD, 2018. URL: https://github.com/Biwei-Huang/Generalized-Score-Functions-for-Causal-Discovery
  ```
  具有广义得分函数的贪婪等价搜索的因果结构学习（适用于混合连续和离散数据、具有高斯或非高斯分布的数据、线性或非线性因果机制以及具有多维的变量。）
  ```
7. Learning the Causal Structure of Copula Models with Latent Variables. UAI. 2018. URL: https://github.com/cuiruifei/CopulaFactorModel
8. Data Generating Process to Evaluate Causal Discovery Techniques for Time Series Data, at the Causal Discovery & Causality-Inspired Machine Learning Workshop at NeurIPS 2020. URL: https://github.com/causalens/cdml-neurips2020
9. Process Mining Meets Causal Machine Learning: Discovering Causal Rules from Event Logs, URL: https://github.com/zahradbozorgi/CausalRulesDiscovery
10. 
