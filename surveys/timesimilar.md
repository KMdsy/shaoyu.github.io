# Time series similarity learning

-----

+ NIPS19 - Learning Representations for Time Series Clustering

流程
1. 本质上是在隐空间内学习一个利于分簇的表征，然后利用该表征结合传统的聚类方法，做聚类任务
    1. 使用auto-encoder的结构，求得时间序列在隐空间中的表达
    2. 为了使得encoder出的结果更适合于执行聚类任务，使用k-means建模了隐空间中的数据（本质上是无监督的优化类间距离与类内距离），这个过程中使用了可微分的k-means loss
    3. 为了使得encoder更具有表征能力，添加了一项任务，即分类任务，使用一个子网络来分类encoder编码的真实数据与假数据。
2. 使用UCR聚类任务评估效果

我认为的缺点
1. K-means的隐空间建模能力远弱与GMM

----------------

+ KDD19 - NeuralWarp: Time-Series Similarity with Warping Networks

流程
1. 本质上是将DTW的思想引入到了隐空间，并将DTW中的dynamic programming搜索最优对齐的过程，替换为了一个可学习的矩阵，从而将DTW的思想融入深度学习中。
    1. 将显空间的时间序列$X(T)$用过auto-encoder映射到隐空间中的$Z(N\*T)$，然后通过一个网络用于学习给定的一个时间序列对之间的对齐方式
    2. 学习的目标函数是：最小化同类时间序列对的latent dtw距离，同时最大化不同类时间序列对的latent dtw距离。
    3. 通过学习可得到一个用于在隐空间做对齐的神经网络，且网络的输出为给定的时间序列对的距离
2. 通过分类任务评估性能

我认为的缺点
1. 有监督学习

---------------

+ ICLR19 - SOM-VAE: INTERPRETABLE DISCRETE REPRESENTATION LEARNING ON TIME SERIES [code]

流程
1. 本质上是在隐空间建立了一个SOM（self-organized map）并为SOM的节点建立了markov model，以提供可解释的表征（从概率与拓扑的角度，其中SOM提供了隐空间表达的拓扑结构，markov model提供了概率模型）
    1. 首先将时间序列使用auto-encoder重建
    2. 然后在隐空间使用SOM进行拟合，将隐空间的数据点建模为具有K个节点的SOM
    3. 将隐空间中的每个数据点归类到与其最近的SOM节点上，再依托数据建立Markov model
    4. 网络通过重建误差/隐空间表达与SOM节点之间的距离/可观察数据的转移概率 共同优化
2. 使用MNIST和FASION-MNIST做聚类任务

我认为的缺点
1. 没想好

--------------------

+ ICML19 workshop - Warping Resilient Time Series Embeddings

流程
1. 本质上是通过神经网络来学习一种对显空间时间序列的翘曲不敏感的隐空间表达
    1. 首先定义了两种时间序列的翘曲方法，用于为原始的时间序列生成一些翘曲后的样本
    2. 使用两个auto-encoder分别学习左翘曲后的时间序列的隐空间表达，和右翘曲后的时间序列隐空间表达。
    3. 使用一项loss函数，使得在显空间做了翘曲的样本在隐空间的表达尽可能相近
    4. 网络的输出就是一个对翘曲不敏感的embedding
2. 使用一部分UCR做分类任务

我认为的缺点
1. 仅对时间序列的翘曲不敏感，但对更复杂的时间序列的表征能力可能会很弱

----------------

+ KDD19 workshop - A Formally Robust Time Series Distance Metric [code]

流程
1. 本质上是想寻求一种对数据污染更加鲁棒的显空间距离度量方法，聚焦于一个分类问题，
所谓小污染指：在class i的样本x上增加一个小的污染序列k，一种鲁棒的距离度量方法能够做到：d(x_i, x_i+k) < d(x_i, x_j)，
其中x_j是class j的样本 
2. 通过将6中鲁棒性与精确性具有不同性质的距离度量方式统一到0-1的距离度量范围后，将6中距离方法结合起来，生成一种新的距离度量方式
3. 使用UCR做分类任务

其实我们的方法一定程度上也在解决这种对污染序列的鲁棒性，而我们使用的是auto-encoder来过滤污染序列对原始序列在隐空间上的影响的。

-----------

+ IJCAI19 - Similarity Preserving Representation Learning for Time Series Clustering [code]

流程
1. 本质上是提出一种能够保留时间序列在显空间相似度的embedding方法
2. 给定一个数据集D，包含N个样本，首先在显空间中利用DTW（或其他算法）建立其他们的距离矩阵（N*N）
3. 然而当N很大的时候，建立这样一个距离矩阵是费时的，所以他提出，部分观察的距离矩阵足以估计出完整的距离矩阵，因此在计算样本xi的时候，并不将其与其他N-1个样本进行距离计算，而是将其与随机采样的K个样本进行距离计算
4. 得到了距离度量矩阵的时候，通过解一个具有近似最优解的优化目标，从而获得样本的低维表示

我认为的缺点：
1. 当时间序列在显空间的相似度能够揭示数据的簇时，该方法有效，但当显空间的距离度量无法区分数据内在的性质的时候，该方法将会失效

-----------

+ NIPS18 - Autowarp: Learning a Warping Distance from Unlabeled Time Series Using Sequence Autoencoders

流程
1. 假设数据在auto-encoder映射下的隐空间中，能够embedding出时间序列的内在特性，并进行部分的分簇。
2. 将显空间中的四个常用的距离度量参数化为一个距离度量族，其参数为alpha/beta/gamma
    1. 首先将数据通过auto-encoder压缩到一个隐空间
    2. 然后通过优化alpha/beta/gamma以在距离度量族里寻找一个恰当的距离度量，能够使得数据在显空间中的相似性关系与在隐空间中的近似。（这个过程通过latent betaCV——一种无需GT的聚类性能衡量方法，来评估显空间中的相似性与隐空间中的相似性关系是否近似）
3. 本工作的目标还是求得一个显空间的恰当的距离度量方式，并以隐空间的欧氏距离度量生成的簇信息作为参考，以避免了没有GT的困境
4. 通过聚类任务评估性能

我认为的缺点
1. 过于依赖隐空间所提供的分簇信息，当隐空间表达不足以支持分簇的时候，该方法近乎失效。
2. 两段式的算法，寻找距离度量的优化过程与auto-encoder的优化过程分离，可能会导致性能不佳

-------

### 其他

+ KDD 17 workshop - DECADE: A deep metric learning model for multivariate time series

    主要解决多维时间序列计算DTW距离的问题，主要方法：先将高维数据映射到隐空间，然后在隐空间计算每一维数据对应所有其他维度的alignment path，然后定义了一种新的对齐方法expected alignment，其本质是对mdtw中所有可能的alignment path上的距离做平均。
    
    该方法是有监督学习，最小化同类见的距离，最大化不同类之间的距离

+ NIPS 16 - Graphical Time Warping for Joint Alignment of Multiple Curves

    DTW在图像等数据上的推广，本文提出DTW的dynamic programming过程可以视为graph上的network flow problem，并使用max flow algorithm进行求解。利用上述问题转换方法，解决了图像（可视为多维时间序列）上像素之间的距离度量问题。

+ KDD17 - Tripoles: A New Class of Relationships in Time Series Data

    定义了一种在三个时间序列之间的关系，该关系有利于发现时间序列中的新特性（如新的全球气象类型等）

+ ICML17 - Soft-DTW: a Differentiable Loss Function for Time-Series

    提出smoothed formulation of DTW，是一种可微分的DTW求解方式，这使得DTW能够嵌入到深度学习的框架中










