# Deep leanring or machine learning on time series with missing value

近年来一些顶会文章或者是比较重要的文章，并列出与我的工作的异同点（NIPS20的投稿）

---------

+ Recurrent Neural Networks for Multivariate Time Series with Missing Values

  Che, Z., Purushotham, S., Cho, K., Sontag, D., & Liu, Y. *(2018)*. 
  Recurrent neural networks for multivariate time series with missing values. **Scientific reports**, 8(1), 1-12. cite:550
  
  异：
  
  1. 利用历史值、预测缺失位置的值。预测值 = beta\*上一个可观测值 + (1-beta)\*历史均值，其中beta是一个可学习的参数。
  
  2. 没有利用到时间序列的动态信息（dynamic）。

  同：
  
  1. 直接将处理缺失值的操作与后续的任务结合起来，即，并不是一个单独做缺失值填充的工作，而是建立一个用于分类与回归的网络，该网络能处理缺失值

-----------

+ BRITS: Bidirectional Recurrent Imputation for Time Series 

  NIPS 2018
  
  异：
  1. 利用历史值，预测缺失位置的值。预测值 = f(历史观测值)，对时间序列的性质不做任何假设，其中f是可学习的非线性映射。
      1. t时刻存在一个观测值的时候，直接将观测xt值用于后续任务，并对xt基于历史数据做一个预测，该预测用于监督缺失值的填充。
      2. t时刻是缺失值的时候，网络直接基于历史值做预测x^t，并将该预测值用于后续任务。

  同：
  1. 直接将处理缺失值的操作与后续的任务结合起来（同上）。
  2. 在填充（或后续任务）的时候，考虑到了时间序列的动态信息（dynamic）。

----------

+ Multivariate Time Series Imputation with Generative Adversarial Networks 
  
  NIPS 2018
  
  异：
  1. 从任务的角度出发，不是一个端到端的模型。例如：对于一个预测问题，需要先训练一个网络用于数据补全，再训练一个预测网络用于预测。
  2. 模型总的架构是一个GAN，其中G与D都是由GRUI在组成的（GRUI可以接收有缺失值的时间序列与一个标志着delay的变量，
  并根据历史值输出对缺失位置进行补全）。
    1. 在一个正态分布中采集一个噪声向量z，然后送入G，输出的是一个完整的序列，G的架构应当是一个RNN
    2. 使用网络将完整与非完整的序列压缩到隐空间，并判断其相似度

  同：
  1. 在填充（或后续任务）的时候，考虑到了时间序列的动态信息（dynamic）
  
------------

+ E2GAN: End-to-End Generative Adversarial Network for Multivariate Time Series Imputation (IJCAI 2019)

  异：
  1. 从任务的角度出发，不是一个端到端的模型（同上）。
  2. 模型总的架构是一个GAN，其中G与D都是由GRUI在组成的（GRUI可以接收有缺失值的时间序列与一个标志着delay的变量，
  并根据历史值输出对缺失位置进行补全）。
    - G：先在有缺失值的位置上填充一些噪音，然后送入G，输出的是一个经过补全后的时间序列，G的架构为seq2seq
    - D：使用网络将完整与非完整的序列压缩到隐空间，并判断其相似度

  同：
  1. 在填充（或后续任务）的时候，考虑到了时间序列的动态信息（dynamic）
  
-------

+ Temporal Belief Memory: Imputing Missing Data during RNN Training 
  
  IJCAI 2018
  
  异：
  1. 提出了一种单元叫做TBM，TBM用于接收带有缺失值的序列，并对缺失位置进行填充。TBM是连接在LSTM cell之前的，
  在有缺失值的时候，将TBM的输出送入LSTM，在没有缺失值的时候，将原始的时间序列送入LSTM
  2. TBM中有两种门：missing gate(指示某个时刻是否存在缺失值), belief gate（指示是否使用上一时刻的值作为填充，
  但是使用当前时刻的其他feature的均值作为填充）。
    1. 当有一个观测值的时候，missing gate = 0，观测值直接进入LSTM
    2. 当没观测值的时候，missing gate = 1, 此时belief gate进行估算，指示是否让神经元放电(生物学的角度)
      1. 神经元不放电：belief gate = 0，向LSTM输入上一时刻的值
      2. 神经元放电：belief gate = 1, 将当前时刻的其他feature的均值送入LSTM
      
  3. BM在计算填充值的时候，没有使用时间序列的动态信息（dynamic），仅单纯使用了上一时刻的值/当前时刻的其他feature的均值作为填充.
  
  4. 他在选择填充策略的时候（选择向LSTM输入上一时刻的值 或将当前时刻的其他feature的均值送入LSTM），
  仅考虑了空缺时刻与上一次观测值之间的差值，并没有考虑任何的历史数据与时间序列动态.

  同：
  1. 直接将处理缺失值的操作与后续的任务结合起来.



