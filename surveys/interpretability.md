# Post-hoc interpretability

## 研究问题描述

+ 深度学习模型的事后（post-hoc）可解释方法

  给定一个已训练的深度神经网络模型，如何对其输出进行解释。


## 领域现状

1. 基于叠加的方法（Superimposition-based explanation）

  这类方法将网络的输出归因到网络的输入上，显式的指出网络输入中的每个维度对网络输出的贡献程度，

- 优点：直观

- 缺点：有时会生成令人误解的解释，如当网络将已知的无关输入视为重要判断依据时


  \[1\]LIME：通过对输入施加轻微的扰动，以探测黑盒模型的输出变化，优化一个可解释模型（线性模型或tree-based model）局部近似黑盒模型的预测。

  \[2\]SHAP：基于博弈理论（shapley value, a game-theory based method），计算网络输入的每一维对网络输出的贡献（也是将黑盒模型做局部近拟，使其具有可解释性）

  \[3\]saliency map：训练一个遮罩模型（masking model）以识别最影响分类器决断的输入特征。

  \[4\]Integrated Gradients：以输入特征在某个路径上的梯度积分（ Integrated Gradients ）作为该特征的重要性得分。


2. 基于例子的方法（example-based explanation）

  这类方法针对某个待解释的案例，依照某种策略生成一组案例（a set of example），这组案例一般是支持网络对待解释案例做出判断的主要依据。通过人类直观的对比这组案例与待解释的案例，总结出的差异与共同点将被视为一种直接的解释。

- 优点：易于理解

- 缺点：依赖于训练集的质量与数量

  \[10\]: 通过在训练样本上施加一个微小的扰动，观察该扰动对所训练出的模型权重的影响，以此来确定网络在对给定样本进行预测时，是哪些训练样本起到了决定性作用。

  \[11\]: 搜索给定样本在深度学习模型的每一层特征空间中的最近邻，其邻居构成的合集即为用于解释给定样本的训练集（给定样本与该集合中的样本共性即为他们获得相同标签的原因）。

-------

## 代表性论文10篇

1. 基于叠加的方法

  经典方法

  \[1\]: Marco Túlio Ribeiro, Sameer Singh, and Carlos Guestrin. 2016. "Why Should I Trust You?": Explaining the Predictions of Any Classifier. In SIGKDD. ACM, 1135–1144. (LIME)

  \[2\]: Scott M. Lundberg and Su-In Lee. 2017. A Unified Approach to Interpreting Model Predictions. In NeurIPS. 4765–4774. (SHAP)

  \[3\]: Piotr Dabkowski and Yarin Gal. 2017. Real Time Image Saliency for Black Box Classifiers. In NeurIPS. 6967–6976. (saliency map)

  \[4\]: Sundararajan, M., Taly, A., & Yan, Q. (2017, August). Axiomatic attribution for deep networks. In Proceedings of the 34th International Conference on Machine Learning-Volume 70 (pp. 3319-3328).

  其他工作

  \[5\]: Ismail, A., Gunady, M., Bravo, H., & Feizi, S. (2020). Benchmarking Deep Learning Interpretability in Time Series Predictions. Advances in Neural Information Processing Systems Foundation (NeurIPS).

  \[6\]: Giurgiu, I., & Schumann, A. (2019). Explainable failure predictions with rnn classifiers based on time series data. arXiv preprint arXiv:1901.08554.

  \[7\]: Mujkanovic, F., Doskoč, V., Schirneck, M., Schäfer, P., & Friedrich, T. (2020). timeXplain--A Framework for Explaining the Predictions of Time Series Classifiers. arXiv preprint arXiv:2007.07606.

  \[8\]: Nguyen, T. T., Le Nguyen, T., & Ifrim, G. (2020, September). A Model-Agnostic Approach to Quantifying the Informativeness of Explanation Methods for Time Series Classification. In International Workshop on Advanced Analytics and Learning on Temporal Data (pp. 77-94). Springer, Cham.

  \[9\]: Shankaranarayana, S. M., & Runje, D. (2019, November). ALIME: Autoencoder based approach for local interpretability. In International Conference on Intelligent Data Engineering and Automated Learning (pp. 454-463). Springer, Cham.

2. 基于例子的方法

  经典方法

  \[10\]: Koh, P. W., & Liang, P. (2017, July). Understanding Black-box Predictions via Influence Functions. In International Conference on Machine Learning (pp. 1885-1894).

  \[11\]: Nicolas Papernot and Patrick McDaniel. Deep k-nearest neighbors: Towards confident, interpretable and robust deep learning. arXiv preprint arXiv:1803.04765, 2018.

  其他工作

  \[12\]: Kim, B., Rudin, C., & Shah, J. A. (2014). The bayesian case model: A generative approach for case-based reasoning and prototype classification. Advances in neural information processing systems, 27, 1952-1960.

  \[13\]: Jeyakumar, J. V., Noor, J., Cheng, Y. H., Garcia, L., & Srivastava, M. (2020). How Can I Explain This to You? An Empirical Study of Deep Neural Network Explanation Methods. Advances in Neural Information Processing Systems, 33.

  \[14\]: Papernot, N., & McDaniel, P. (2018). Deep k-nearest neighbors: Towards confident, interpretable and robust deep learning. arXiv preprint arXiv:1803.04765.

  \[15\]: Ming, Y., Xu, P., Qu, H., & Ren, L. (2019, July). Interpretable and steerable sequence learning via prototypes. In Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining (pp. 903-913).

  \[16\]: Ma, D., Wang, Z., Xie, J., Guo, B., & Yu, Z. (2020, November). Interpretable Multivariate Time Series Classification Based on Prototype Learning. In International Conference on Green, Pervasive, and Cloud Computing (pp. 205-216). Springer, Cham.

  \[17\]: Keane, M. T., & Kenny, E. M. (2019, September). How case-based reasoning explains neural networks: A theoretical analysis of XAI using post-hoc explanation-by-example from a survey of ANN-CBR twin-systems. In International Conference on Case-Based Reasoning (pp. 155-171). Springer, Cham.

## 经典论文or强相关论文

  \[11\]: Nicolas Papernot and Patrick McDaniel. Deep k-nearest neighbors: Towards confident, interpretable and robust deep learning. arXiv preprint arXiv:1803.04765, 2018.

  \[13\]: Jeyakumar, J. V., Noor, J., Cheng, Y. H., Garcia, L., & Srivastava, M. (2020). How Can I Explain This to You? An Empirical Study of Deep Neural Network Explanation Methods. Advances in Neural Information Processing Systems, 33.

  **异同点**

  \[11, 13\]: 分析的是有监督分类模型中的基于案例的可解释问题，但仅能说明某样本为何被判定为某类，而不能做出反事实（counterfactual:）解释，即“某样本为何不是某类”。无法从中提取出可以用于分类的语义信息

  \[11, 13\]: 和我们的工作均从隐空间入手，分析待测样本的邻居，而我们进一步的分析了待测样本与其邻居、聚类中心样本 之间的差异，以帮助我们总结有助于区分正异常的语义信息。
