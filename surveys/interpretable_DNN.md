# interpretable DNN paper list

key words: Self-explaining models, 

## DNN


1. 
> [<sup>1</sup>](#refer-anchor-1) the recently-proposed layer-wise relevance propagation (LRP) algorithm from Wojciech Samek's group [28], [29] uses the fact that the individual neural network units are differentiable to decompose the network output in terms of its input variables. It is a principled method that has a close relationship to Taylor decomposition and is applicable to arbitrary deep neural network architectures [30]
>
>> - [28] A. Binder, G. Montavon, S. Bach, K. Müller and W. Samek, "Layer-wise relevance propagation for neural networks with local renormalization layers", CoRR, vol. abs/1604. 00825, 2016
>> 
>> - [29] A. Binder, S. Bach, G. Montavon, K.-R. Müller and W. Samek, Layer-Wise Relevance Propagation for Deep Neural Network Architectures, Springer, 2016.
>> 
>> - [30] G. Montavon, S. Lapuschkin, A. Binder, W. Samek and K.-R. Müller, "Explaining nonlinear classification decisions with deep taylor decomposition", Pattern Recognition, vol. 65, pp. 211-222, 2017.

2. Alvarez-Melis, D., & Jaakkola, T. S. (2018, December). Towards robust interpretability with self-explaining neural networks. In Proceedings of the 32nd International Conference on Neural Information Processing Systems (pp. 7786-7795).

> We achieve this with a regularization scheme that ensures our model not only looks like a linear model, but (locally) behaves like one.
> we start with a simple linear regression model and successively generalize
it towards the class of self-explaining models. 
> We progressively generalize the model in the following subsections and
discuss how this mechanism of interpretation is preserved.

3. 
> [<sup>2</sup>](#refer-anchor-2) Examples of self-explainable models include simple linear
> models, or specific nonlinear models, e.g. neural networks with
> an explicit top-level sum-pooling structure [143], [111], [28],
> [206], [25]. In all of these models, each summand is linked
> only to one of a few input variables, which makes attribution
> of their prediction on the input variables straightforward.
>
>> [25] W. Brendel and M. Bethge, "Approximating CNNs with bag-of-local-features models works surprisingly well on imagenet", Proc. 7th Int. Conf. Learn. Represent., 2019.
>> [28] R. Caruana, Y. Lou, J. Gehrke, P. Koch, M. Sturm and N. Elhadad, "Intelligible models for healthcare: Predicting pneumonia risk and hospital 30-day readmission", Proc. 21th ACM SIGKDD Int. Conf. Knowl. Discovery Data Mining, pp. 1721-1730, 2015.
>> [111] M. Lin, Q. Chen and S. Yan, "Network in network", Proc. Int. Conf. Learn. Represent. (ICLR), 2014.
>> [143] B. Poulin et al., "Visual explanation of evidence with additive classifiers", Proc. 21st Nat. Conf. Artif. Intell. 18th Innov. Appl. Artif. Intell. Conf., pp. 1822-1829, 2006.
>> [206] B. Zhou, A. Khosla, A. Lapedriza, A. Oliva and A. Torralba, "Learning deep features for discriminative localization", Proc. IEEE Conf. Comput. Vis. Pattern Recognit. (CVPR), pp. 2921-2929, Jun. 2016.

4. Agarwal, R., Frosst, N., Zhang, X., Caruana, R., & Hinton, G. E. (2020). Neural additive models: Interpretable machine learning with neural nets. arXiv preprint arXiv:2004.13912.

> In this paper, we make restrictions on the structure of neural networks, which yields a family of models called Neural
> Additive Models (NAMs), that are inherently interpretable while suffering little loss in prediction accuracy when applied to tabular data.
> 
> ...
> 
> NAMs belong to a larger model family called Generalized Additive Models
(GAMs)


## RNN

5. 
> [<sup>2</sup>](#refer-anchor-2) extensions of LRP have been proposed
> to deal with the special LSTM blocks in recurrent neural
> networks [11], [9]
>
>> [9] L. Arras et al., "Explaining and interpreting LSTMs" in Explainable AI: Interpreting Explaining and Visualizing Deep Learning, Cham, Switzerland:Springer, vol. 11700, pp. 211-238, 2019.
>> [11] L. Arras, G. Montavon, K.-R. Müller and W. Samek, "Explaining recurrent neural network predictions in sentiment analysis", Proc. 8th Workshop Comput. Approaches to Subjectivity Sentiment Social Media Anal., pp. 159-168, 2017.


6. Marcinkevičs, R., & Vogt, J. E. (2021). Interpretable Models for Granger Causality Using Self-explaining Neural Networks. ICLR 2021.

> We extend self-explaining neural network models (Alvarez-Melis & Jaakkola, 2018) to
> time series analysis. The resulting autoregressive model, named generalised vector autore-gression (GVAR), is interpretable and allows exploring GC relations between variables, signs of Granger-causal effects, and their variability through time.



# Reference: List of Surveys
<div id="refer-anchor-1"></div>
- [1] Chakraborty, S., Tomsett, R., Raghavendra, R., Harborne, D., Alzantot, M., Cerutti, F., ... & Gurram, P. (2017, August). Interpretability of deep learning models: a survey of results. In 2017 IEEE smartworld, ubiquitous intelligence & computing, advanced & trusted computed, scalable computing & communications, cloud & big data computing, Internet of people and smart city innovation (smartworld/SCALCOM/UIC/ATC/CBDcom/IOP/SCI) (pp. 1-6). IEEE.

<div id="refer-anchor-2"></div>
- [2]Samek, W., Montavon, G., Lapuschkin, S., Anders, C. J., & Müller, K. R. (2021). Explaining Deep Neural Networks and Beyond: A Review of Methods and Applications. Proceedings of the IEEE, 109(3), 247-278.




