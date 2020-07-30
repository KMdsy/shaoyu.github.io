<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      processEscapes: true
    }
  });
</script>

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

# Some notes

### 2020.07.27

1. **posterior collapse**: where the latents are ignored when they are paired with a powerful autoregressive decoder — typically observed in the VAE framework, i.e., the latents are ignored as the decoder is powerful enough to model x perfectly.个人理解是某些VAE的decoder的重建能力过于好导致重建误差很小，最后模型不能很好的最小化prior相关的loss item。

2. 关于self-supervised learning中的附加任务：
    1. 一种常用且简单的任务：对原始数据$x$做一定的transformation($t$)，即$t(x)$，然后训练一个附加任务，即区分这些transformation的种类。    
        **目的**：训练神经网络辨别图片是否为自然的。(To predict such transformations, a model should distinguish between what is semantically natural or not, and consequently, it
        learns high-level semantic representations of inputs.)
    2. 当仅使用了transformation后的数据$t(x)$而没有将对应的self-supervised learning task加入到loss中，则该方法退化为**数据增强**。
        
        **目的**：提高网络的通用性，即对多种变化后的样本，都能够提取出差不多的语义信息
        
        > This conventional data augmentation aims to improve upon
        > the generalization ability of the target neural network f by
        > leveraging certain transformations that can preserve their semantics,
        > e.g., cropping, contrast enhancement, and flipping.
        
        **缺点**：另一方面，如果transformation修改了数据中的语义，则转换的不变属性可能会干扰语义表示学习（请参阅第3.2节中的表1）。
        
        > On the other hands, if a transformation modifies the semantics,
        > the invariant property with respect to the transformation
        > could interfere with semantic representation learning
