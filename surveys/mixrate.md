# Deep leanring or machine learning on time series with mixed sampling rate

----

+ Autoregressive Convolutional Neural Networks for Asynchronous Time Series: **ICML 2019**

  异：
  1. 处理的是多维时间序列数据
  2. 针对非同步数据，并未和我们一样，训练一个能够用于多种采样率的模型，而是将[多维时间序列，序列指示剂，采样间隔]合并成为多维时间序列，然后输入到网络中
  3. 使用类似自回归模型的算法，对时间序列模型进行预测
  4. 使用cnn进行序列学习

  同：
  1. 没什么相同的
-----------
+ Hierarchical Deep Generative Models for Multi-Rate Multivariate Time Series: **ICML 2018**

  异：
  1. 针对L种不同采样率的数据，并未和我们一样，训练一个能够用于多种采样率的模型，而是：
      1. 用RNN将不同采样率的时间序列中的每一个值，embedding到隐空间，h
      2. 基于深度马尔科夫模型，建模上述隐空间变量的生成模型
      3. 利用Auxiliary connections，提取不同采样率的时间序列的长程/短程记忆，即序列间的关系
  2. 该工作基于一种生成模型，通过模拟数据的生成过程，来建模若采样率数据之间的关系
  3. 针对非同步数据，并未和我们一样，训练一个能够用于多种采样率的模型

  同：
  1. 都设置了某种机制，用于分别提取了时间序列中的long/short term dependency，该文章使用的方法类似于我们所采用的跳连机制
----------------
+ INTERPOLATION-PREDICTION NETWORKS FOR IRREGULARLY SAMPLED TIME SERIES: **ICLR 2019**

  异:
    1. 对于D种不同采样率的时间序列，先设立一个均匀的参考时间线，然后利用插补网络（ INTERPOLATION NETWORKS ）在上述的参考时间线上进行插补，将不同采样率的时间序列插补成均匀采样的时间序列
    2. 再提取多维时间序列之间的关联关系（建模多维时间序列）
    3. 上一步的输出被送入后续的预测网络中进行进一步的训练（以预测、分类等任务为训练目标）
    4. 针对非同步数据，并未和我们一样，训练一个能够用于多种采样率的模型

  同:
    1. 都设置了某种机制，用于分别提取了时间序列中的long/short term dependency

