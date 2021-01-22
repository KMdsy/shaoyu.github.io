<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

# Quasi-periodic time series

## 研究问题描述

+ 准周期时间序列的异常检测问题

该问题可以拆解为两部分：准周期时间序列建模、异常检测。本调研主要针对准周期时间序列建模进行调研

+ 数学描述

给定一个准周期时间序列的一组周期样本$\bf{x}_1, ..., \bf{x}_N$，其中$\bf{x}_i$为一个周期内的时间序列片段，如何对$\bf{x}_i$进行建模，
即如何从$\bf{x}_i$中提取出表征向量$\bf{v}_i$用于后续的任务（如：异常检测、分类、预测，等）

## 领域现状

+ 基于手工设计的特征的

这类方法依赖手工设定的特征，提取时间序列的统计特征与形状特征。这类方法往往仅能用于特定种类的数据，如ECG数据，而缺乏可拓展性。具体包括:

1. 基于统计特征的

  [1]: 设计了7种统计特征用于描述时间序列
  
  [2]: 对ECG数据进行Recurrence Quantiﬁcation Analysis，以提取出15种特征用于后续的任务

+ 无需手工设计特征的

此类方法无需手工设计特征提取方法，而是自适应的从原始时间序列中学习时间序列的动态。

1. 基于频率域特征的：

  [3]: 将ECG数据进行小波变换（DWT）后，联合使用三种降维方法（LDA，ICA，PCA）对DWT结果进行降维，最后送入SVM或PNN（probabilistic neural network）进行判别

  [4]: 提出了一种基于序列数据DFT的周期性点异常检测算法

  [5]: 调研了用于准周期时间序列异常检测的10种频率域特征提取方法及其特性

2. 基于形态学特征的：

  [6]: 使用Triadic Motif Field Images描述准周期序列中所包含的motifs，然后借助VGG-16作为特征提取器对TMF images进行特征提取以支持异常检测。

3. 基于深度学习的：

  [7]: 针对ECG信号首先利用STFT提取频域特征，然后计算每个频带的AMDF，用以解析ECG中的长短期依赖，进一步的借助LSTM建模长短期依赖并做正异常检测。

  [8]: 提出一种Hybrid Attentional LSTM-CNN Model，它结合了LSTM与CNN，分别用于提取准周期时间序列中的趋势变化与局部特征变化。

  [9]: 利用LSTM网络构建了一个时间序列预测模型，并使用多维高斯分布拟合该预测模型的预测误差。通过判断预测误差是否属于所学习的高斯分布来进行异常检测。

  [10]: 使用由LSTM构建的seq2seq模型建模正常时间序列，并使用重建误差作为异常分数。

  [11]: 利用分别利用LSTM与CNN对ECG数据进行特征提取与融合，并利用MLP作为分类器以检测异常心音

---------------

## 代表性论文10篇
1. 基于手工设计的特征

[1]: Ma, J., Sun, L., Wang, H., Zhang, Y., & Aickelin, U. (2016). Supervised anomaly detection in uncertain pseudoperiodic data streams. ACM Transactions on Internet Technology (TOIT), 16(1), 1-20.

[2]: Desai, U., Martis, R. J., Acharya, U. R., Nayak, C. G., Seshikala, G., & SHETTY K, R. A. N. J. A. N. (2016). Diagnosis of multiclass tachycardia beats using recurrence quantification analysis and ensemble classifiers. Journal of Mechanics in Medicine and Biology, 16(01), 1640005.

2. 无需手工设计特征的

[3]: Martis, R. J., Acharya, U. R., & Min, L. C. (2013). ECG beat classification using PCA, LDA, ICA and discrete wavelet transform. Biomedical Signal Processing and Control, 8(5), 437-448.

[4]: Erkuş, E. C., & Purutçuoğlu, V. (2020). Outlier detection and quasi-periodicity optimization algorithm: Frequency domain based outlier detection (FOD). European Journal of Operational Research.

[5]: Iskhakova, A. O., Alekhin, M. D., & Bogomolov, A. V. (2020). Time-frequency transforms in analysis of non-stationary quasi-periodic biomedical signal patterns for acoustic anomaly detection. Информационно-управляющие системы, (1), 15-23.

[6]: Zhang, Y., & Chen, X. (2020). Anomaly Detection in Time Series with Triadic Motif Fields and Application in Atrial Fibrillation ECG Classification. arXiv preprint arXiv:2012.04936.

[7]: Ngo, D., & Veeravalli, B. (2015, November). Design of a real-time morphology-based anomaly detection method from ECG streams. In 2015 IEEE International Conference on Bioinformatics and Biomedicine (BIBM) (pp. 829-836). IEEE.

[8]: Liu, F., Zhou, X., Cao, J., Wang, Z., Wang, T., Wang, H., & Zhang, Y. (2020). Anomaly Detection in Quasi-Periodic Time Series based on Automatic Data Segmentation and Attentional LSTM-CNN. IEEE Transactions on Knowledge and Data Engineering.

[9]: Thill, M., Däubener, S., Konen, W., & Bäck, T. (2019). Anomaly Detection in Electrocardiogram Readings with Stacked LSTM Networks. In ITAT (pp. 17-25).

[10]: Malhotra, P., Ramakrishnan, A., Anand, G., Vig, L., Agarwal, P., & Shroff, G. (2016). LSTM-based encoder-decoder for multi-sensor anomaly detection. arXiv preprint arXiv:1607.00148.

[11]: Dissanayake, T., Fernando, T., Denman, S., Sridharan, S., Ghaemmaghami, H., & Fookes, C. (2020). A robust interpretable deep learning classifier for heart anomaly detection without segmentation. IEEE Journal of Biomedical and Health Informatics.

## 经典论文or强相关论文

[8]: Liu, F., Zhou, X., Cao, J., Wang, Z., Wang, T., Wang, H., & Zhang, Y. (2020). Anomaly Detection in Quasi-Periodic Time Series based on Automatic Data Segmentation and Attentional LSTM-CNN. IEEE Transactions on Knowledge and Data Engineering.

[9]: Thill, M., Däubener, S., Konen, W., & Bäck, T. (2019). Anomaly Detection in Electrocardiogram Readings with Stacked LSTM Networks. In ITAT (pp. 17-25).

[10]: Malhotra, P., Ramakrishnan, A., Anand, G., Vig, L., Agarwal, P., & Shroff, G. (2016). LSTM-based encoder-decoder for multi-sensor anomaly detection. arXiv preprint arXiv:1607.00148.

[11]: Dissanayake, T., Fernando, T., Denman, S., Sridharan, S., Ghaemmaghami, H., & Fookes, C. (2020). A robust interpretable deep learning classifier for heart anomaly detection without segmentation. IEEE Journal of Biomedical and Health Informatics.

### 异同点

[8]: 提出的方法是有监督的，无法很好的适用于标签不足或标签不精确的现实情况。且缺少可解释性，无法定位异常所在的位置。

[9, 10]: 所提出的方法缺乏可解释性

[11]: 所使用的解释方法仅能够显示出数据对模型输出的贡献，而不能指出异常的段。





