# Data Augmentation (Specifically for rhythmic time series, e.g. ECG, EEG, etc..)

一般来讲，针对ECG/EEG数据的分类、异常检测等任务，都存在严重的数据不平衡问题。这些数据增强方法一般用于丰富样本较少的类别。
大量的工作集中于使用GAN/VAE等生成模型建立数据的分布，然后从分布中生成采样。以下的方法是一些在显空间数据上进行数据增强的简单方法。

+ ECG arrhythmia classification using a 2-D convolutional neural network
  
  Jun, T. J., Nguyen, H. M., Kang, D., Kim, D., Kim, D., & Kim, Y. H. *(2018)*. ECG arrhythmia classification using a 2-D convolutional neural network. **arXiv preprint** arXiv:1804.06812. cite: 45
  
  首先将ECG数据转换为2D的图像数据（128\*128），然后使用CNN对数据进行分类。其数据增强方法是原始数据使用一定策略进行裁剪
  （如裁剪top right / top left部分等）

+ Comparing feature-based classifiers and convolutional neural networks to detect arrhythmia from short segments of ECG

  Andreotti, F., Carr, O., Pimentel, M. A., Mahdi, A., & De Vos, M. *(2017, September)*. 
  Comparing feature-based classifiers and convolutional neural networks to detect arrhythmia from short segments of ECG. **In 2017 Computing in Cardiology (CinC)** (pp. 1-4). IEEE. cite: 53
  
  数据集中存在一个噪音类别（个人理解是由于设备等原因噪声的噪音，无法将其分配到具体发的ECG类别中）
  将这些噪音附加到原始数据上以生成新的样本
  
+ ECG Arrhythmias Detection Using Auxiliary Classifier Generative Adversarial Network and Residual Network
  
  Wang, P., Hou, B., Shao, S., & Yan, R. *(2019)*. ECG arrhythmias detection using auxiliary classifier generative adversarial network and residual network. **IEEE Access**, 7, 100910-100922. cite: 3
  
  文章本身提出的方法是基于GAN的，但在related work中提及了一些无需深度网络的传统增强方法
  
+ A novel data augmentation method to enhance deep neural networks for detection of atrial fibrillation
  
  Cao, P., Li, X., Mao, K., Lu, F., Ning, G., Fang, L., & Pan, Q. *(2020)*. A novel data augmentation method to enhance deep neural networks for detection of atrial fibrillation. **Biomedical Signal Processing and Control**, 56, 101675. cite: 4
  
  文章本身所提出的增强方法仅适用于ECG数据（需要提取数据的QPV段等），但在related work中提及了一些通用的增强方法
  
+ Convolutional recurrent neural networks for electrocardiogram classification

  Zihlmann, M., Perekrestenko, D., & Tschannen, M. *(2017, September)*. Convolutional recurrent neural networks for electrocardiogram classification. **In 2017 Computing in Cardiology (CinC)** (pp. 1-4). IEEE. cite: 82
  
  两种增强方法：**1）**在ECG中使得一段数值为0，以模拟ECG信号的丢失（设备接触不良等），仅适用于ECG数据（而且需要确认与数据集原始的分布是否一致，如原始数据集并不存在这种情况，则也许会导致性能下降）。
  **2）**模拟ECG数据中过高或者过低的新心率（感觉与BeatGAN中的目的一致）
  
+ Rotational data augmentation for electroencephalographic data
  
  Krell, M. M., & Kim, S. K. *(2017, July)*. Rotational data augmentation for electroencephalographic data. **In 2017 39th Annual International Conference of the IEEE Engineering in Medicine and Biology Society (EMBC)** (pp. 471-474). IEEE. cite: 12
  
  本文说的是EEG数据的增强，EEG数据由于采集器放置在人脑上的位置不同，而会产生数据偏移。
  但其方法仅是将EEG采集器以多种角度放置并采集数据以作为增强数据。
  
+ A Novel Deep Learning Approach With Data Augmentation to Classify Motor Imagery Signals
  
  Zhang, Z., Duan, F., Sole-Casals, J., Dinares-Ferran, J., Cichocki, A., Yang, Z., & Sun, Z. *(2019)*. A novel deep learning approach with data augmentation to classify motor imagery signals. **IEEE Access**, 7, 15945-15954. cite: 28
  
  首先将数据进行分解，分解为多个子序列（如IMF1，IMF2，IMF3等），原始序列可以视为多个子序列的加和。
  新的数据通过随机组合上述的子序列并将其加和来创造（IMF1(2)+IMF2(3)+IMF3(1)）
  
+ An Amplitudes-Perturbation Data Augmentation Method in Convolutional Neural Networks for EEG Decoding

  Zhang, X. R., Lei, M. Y., & Li, Y. *(2018, August)*. An amplitudes-perturbation data augmentation method in convolutional neural networks for EEG decoding. **In 2018 5th International Conference on Information, Cybernetics, and Computational Social Systems (ICCSS)** (pp. 231-235). IEEE. cite: 2
  
  针对EEG数据，将数据用STFT转换到频域，然后在振幅中增加一些扰动（采样自高斯噪声），在转换回来到原始域。
  
+ Data Augmentation for EEG-Based Emotion Recognition with Deep Convolutional Neural Networks

  Wang, F., Zhong, S. H., Peng, J., Jiang, J., & Liu, Y. *(2018, February)*. Data augmentation for eeg-based emotion recognition with deep convolutional neural networks. **In International Conference on Multimedia Modeling** (pp. 82-93). Springer, Cham.
  
  在图像处理中使用两种基本的数据增强方法：几何变换和噪声添加。包括位移，比例，旋转/反射等在内的几何变换并不直接适合于扩大我们的EEG数据。与图像相比，EEG信号是随时间变化的连续信号。即使执行了特征提取，其特征仍然是时间序列。因此，如果我们旋转或移动EEG数据，则时域特征将被破坏。为避免此问题，我们进一步考虑使用噪声添加方法来增强EEG样本。
	
