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
3. **mode collapse**: meaning that GANs have the tendency to only generate a subset of the original dataset.

4. kill -STOP 1234 将该进程暂停，如果要让它恢复到后台，用kill -CONT 1234。[ref1](https://www.cnblogs.com/kexinxin/p/9939119.html), [ref2](https://www.jianshu.com/p/d4190447736e) 

5. [修复VS Code无法跳转问题](https://www.cnblogs.com/longjiang-uestc/p/11515571.html)

6. [python 内置异常总结](https://www.cnblogs.com/nmb-musen/p/10856023.html)
    ```python
    # 用法
    if something_True_or_False:
        raise ValueError # or other Error
    ```
  
7. Tensorflow1中关于TensorArray的用法
    ```python
    # 改动TensorFlow源码的时候，使用以下语句
    i_list = tensor_array_ops.TensorArray(size=0, dtype=dtype, dynamic_size=True, name='i_list', clear_after_read=True)
    # 当在其他环境中时，tensor_array_ops -> tf

    # 使用
    self.j_list.write(_step, value).mark_used()
    '''
    def write(self, index, value, name=None):
      """Write `value` into index `index` of the TensorArray.

      Args:
      index: 0-D.  int32 scalar with the index to write to.
      value: N-D.  Tensor of type `dtype`.  The Tensor to write to this index.
      name: A name for the operation (optional).

      Returns:
      A new TensorArray object with flow that ensures the write occurs.
      Use this object all for subsequent operations.
    '''
    # 上述语句的返回需要被使用，当没有被使用的时候会在log中生成一个warning，解决方案是在write()后使用方法：mark_used()
    ```

8. 在对LSTM/GRU的更新过程做数学上的推导的时候，遇到问题，$W * \[h_{t-1}, x_t\] + b$中的$concat$操作如何在数学上分析？其中shape of W: \[hidden_dim, hidden_dim + data_dim\](10, 11), shape of h: \[hidden_dim, 1\](10, 1), shape of x: \[data_dim, 1\](1,1), shape of b: \[hidden_dim, 1\](10, 1)

    在代码中，向量为行向量，因此上述公式在代码中的实现为：$\[h_{t-1}, x_t\] * W + b$, 其中shape of W: \[hidden_dim + data_dim, hidden_dim\](11, 10), shape of h: \[1, hidden_dim\](1, 10), shape of x: \[1, data_dim\](1,1), shape of b: \[1, hidden_dim\](10, 1)。
  
    上述的式子$W * \[h_{t-1}, x_t\] + b$由于存在$concat$操作，而难以使用数学分析，此时可以使用$W' * h_{t-1} + u * x_t + b$代替，其中W': \[hidden_dim, hidden_dim\], u: \[hidden_dim, 1\], W = \[W', u\]
    
    ```python
    h = np.arange(10).reshape(1,10) # [1, 10]
    input = np.arange(1).reshape(1,1) # [1, 1]
    print('h shape {}, input shape: {}, concat shape: {}'.format(h.shape, input.shape, np.concatenate([h, input], axis=1).shape))
    res = np.matmul(np.concatenate([h, input], axis=1), w_i) + b_i
    res1 = np.matmul(h, w_i[0:10, :]) + np.matmul(input, w_i[-1, :].reshape(1, 10)) + b_i
    pprint(res)
    pprint(res1)
    pprint(res == res1)
    ```
    output
    ```python
    h shape (1, 10), input shape: (1, 1), concat shape: (1, 11)
    array([[ 1.61824865, -4.07500279,  1.56455836,  1.2925876 , -2.16892738,
            -2.38041244, -2.28631814,  2.84973208, -4.34229152, -1.44608608]])
    array([[ 1.61824865, -4.07500279,  1.56455836,  1.2925876 , -2.16892738,
            -2.38041244, -2.28631814,  2.84973208, -4.34229152, -1.44608608]])
    array([[ True,  True,  True,  True,  True,  True,  True,  True,  True,
             True]])
    ```
