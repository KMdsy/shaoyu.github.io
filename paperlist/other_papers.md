<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      processEscapes: true
    }
  });
</script>

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

# 一些经典的论文

## VAEs

+ Auto-Encoding Variational Bayes

  提出VAE
  
  
+ Wasserstein Auto-Encoders

  提出WAE
  

+ ICLR20 - FROM VARIATIONAL TO DETERMINISTIC AUTOENCODERS
  
  Github: [Link](https://github.com/ParthaEth/Regularized_autoencoders-RAE-)
  
  Some code and its explaination: [Link](http://ameroyer.github.io/projects/2019/08/20/VQVAE.html)
  
  **解决的问题**: 建模数据的隐空间分布模型，提出RAE（Regularized Autoencoder）。
  
  **创新与独特**: RAE无需假设数据的隐空间分布符合任何先验分布。
  
  **采用的方法**
  1. 将传统VAE中，从先验分布中采集随机数据送入decoder的操作，视为一种decoder的正则项，用于辅助学习一个平滑的分布。
  2. 将数据的隐空间分布视为拥有某均值与固定方差的一个未知分布，得到数据隐空间表达后，再估计一个后验的数据分布。
  
  **为何选择/如何应用**: 本文的方法作为一种强大的数据分布估计方法，不预设任何先验分布，在其他复杂的异常检测任务上能够对数据进行建模。
  
  **数据集**
  1. MNIST
  2. CIFAR
  3. CELEBA（人像属性数据集）

  
  
+ NIPS18 - Gaussian Process Prior Variational Autoencoders

  提出GPVAE，即隐空间变量遵从高斯过程，而非一个时不变的分布。
  
  
+ ICLR19 - INTERPRETABLE DISCRETE REPRESENTATION LEARNING ON TIME SERIES

  提出SOM-VAE, [Github](https://github.com/ratschlab/SOM-VAE)

  > High-dimensional time series are common in many domains. Since human cognition is
  > not optimized to work well in high-dimensional spaces, these areas could benefit from
  > interpretable low-dimensional representations. However, most representation learning
  > algorithms for time series data are difficult to interpret. This is due to non-intuitive mappings
  > from data features to salient properties of the representation and non-smoothness over time.
  > To address this problem, we propose a new representation learning framework building on
  > ideas **from interpretable discrete dimensionality reduction and deep generative modeling.**
  > This framework allows us to learn discrete representations of time series, which give rise to
  > smooth and interpretable embeddings with superior clustering performance. **We introduce
  > a new way to overcome the non-differentiability in discrete representation learning and
  > present a gradient-based version of the traditional self-organizing map algorithm that is
  > more performant than the original.** Furthermore, to allow for a probabilistic interpretation of
  > our method, we integrate a Markov model in the representation space. This model uncovers
  > the temporal transition structure, improves clustering performance even further and provides
  > additional explanatory insights as well as a natural representation of uncertainty.
  > We evaluate our model in terms of clustering performance and interpretability on static
  > (Fashion-)MNIST data, a time series of linearly interpolated (Fashion-)MNIST images, a
  > chaotic Lorenz attractor system with two macro states, as well as on a challenging real world
  > medical time series application on the eICU data set. Our learned representations compare
  > favorably with competitor methods and facilitate downstream tasks on the real world data.
  >
  > ...
  >
  > *Time series from the data space [green] are encoded
  > by a neural network [black] time-point-wise into the latent space. The latent data manifold is approximated
  > with a self-organizing map (SOM) [red]. In order to achieve a discrete representation, every latent data point
  > ($z_e$) is mapped to its closest node in the SOM ($z_q$). A Markov transition model [blue] is learned to predict
  > the next discrete representation ($z_q ^{t+1}$) given the current one ($z_q ^{t}$). The discrete representations can then be
  > decoded by another neural network back into the original data space.*
  

  
+ NIPS17 - Neural Discrete Representation Learning

  Github: [Link](https://github.com/nakosung/VQ-VAE), [A useful blog](http://ameroyer.github.io/projects/2019/08/20/VQVAE.html)
  
  **解决的问题**: 学习数据的隐空间离散化表示，该离散化表示可以用于压缩编码、生成更清晰的图像等。
  
  **创新与独特**：第一个学习数据离散表示的工作。
  
  **采用的方法**
  1. 首先将数据使用encoder映射到隐空间，然后学习数据在隐空间的类别分布([categorical distribution](https://zhuanlan.zhihu.com/p/59550457))，
  然后使用一个编码表对连续的隐空间表示做近似，得到离散化的表示，该离散化的表示载送入decoder进行数据还原（文章主要着笔与图像的生成，文章中使用pixelCNN作为decoder，该结构接收离散化的表示作为输入。文章也介绍了音频的生成，即序列生成。）。
  
  2. 进行隐空间离散化的主要方式是，将一个D维的向量通过查表操作，量化到距离他最近的一个数值上。而该表也将在训练中更新，使其能够更加接近真实值。
  
  3. 本文的大量笔墨用在如何对这个网络进行更新上，因为查表的量化操作是无法进行梯度计算的。
  
  **为何选择/如何应用**
  1. 本文所提出的方法能够更逼真的重建样本，媲美BigGAN.
  
  2. 所提出的方法适用于建模离散数据，而大多数的真实世界数据均为离散化的。
  
  **数据集**
  1. CIFAR10, ImageNet
  
  2. VCTK dataset(语音分类数据集)
  
  3. action sequence(deepMind的视频序列数据集)
  
  
+ IJCAI19 - CLVSA A Convolutional LSTM Based Variational Sequence-to-Sequence Model with Attention for Predicting Trends of Financial Markets

  提出CLVSA，还没读
  




## Anomaly detection

  > The work that is the most related to ours is **AnoGAN (Schlegl et al., 2017)**.
  >
  > ...
  >
  > **Bergmann et al. (2019)** compare standard AE reconstructions techniques
  > to AnoGAN, and observes that AnoGAN’s performances on anomaly localizations tasks are
  > poorer than AE’s due to the mode collapse tendency of GAN architectures. Interestingly, updates on
  > AnoGAN such as **fast AnoGAN (Schlegl et al., 2019)** or **AnoVAEGAN (Baur et al., 2018)** replaced
  > the gradient descent search of the optimal z with a learned encoder model, yielding an approach
  > very similar to the standard VAE reconstruction-based approaches, but with a reconstruction loss
  > learned by a discriminator, which is still prone to mode collapse (Thanh-Tung et al., 2019).
  
  **AnoGAN (Schlegl et al., 2017)** Thomas Schlegl, Philipp Seeböck, Sebastian M Waldstein, Ursula Schmidt-Erfurth, and Georg
  Langs. Unsupervised anomaly detection with generative adversarial networks to guide marker
  discovery. In International Conference on Information Processing in Medical Imaging, pp. 146–157. Springer, 2017.
  
  **Bergmann et al. (2019)** Paul Bergmann, Michael Fauser, David Sattlegger, and Carsten Steger. Mvtec ad—a comprehensive real-world 
  dataset for unsupervised anomaly detection. CVPR, 2019.
  
  **fast AnoGAN (Schlegl et al., 2019)** Thomas Schlegl, Philipp Seeböck, Sebastian M. Waldstein, Georg Langs, and Ursula Schmidt-
  Erfurth. f-anogan: Fast unsupervised anomaly detection with generative adversarial networks.
  Medical Image Analysis, 54:30 – 44, 2019. ISSN 1361-8415. doi: https://doi.org/10.1016/j.
  media.2019.01.010.
  
  **AnoVAEGAN (Baur et al., 2018)** Christoph Baur, BenediktWiestler, Shadi Albarqouni, and Nassir Navab. Deep autoencoding models
  for unsupervised anomaly segmentation in brain MR images. CoRR, abs/1804.04488, 2018.
  
-----
  
  
