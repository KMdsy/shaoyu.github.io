# WWW 2021 (2021.04.19)

[paper list](https://www2021.thewebconf.org/program/papers/)

## anomaly detection / Failure detection

- Few-shot Network Anomaly Detection via Cross-network Meta-learning
  
  **Authors:** Kaize Ding (ASU), Qinghai Zhou (UIUC), Hanghang Tong (UIUC) and Huan Liu (ASU).

  **Abstract:** Network anomaly detection aims to find network elements (e.g., nodes, edges, subgraphs) with significantly different behaviors from the vast majority. 
  It has a profound impact in a variety of applications ranging from finance, healthcare to social network analysis. Due to the unbearable labeling cost, existing 
  methods are predominately developed in an unsupervised manner. Nonetheless, the anomalies they identify may turn out to be data noises or uninteresting data instances 
  due to the lack of prior knowledge on the anomalies of interest. Hence, it is critical to investigate and develop few-shot learning for network anomaly detection. 
  In real-world scenarios, few labeled anomalies are also easy to be accessed on similar networks from the same domain as the target network, while most of the existing 
  works omit to leverage them and merely focus on a single network. Taking advantage of this potential, in this work, we tackle the problem of few-shot network anomaly 
  detection by (1) proposing a new family of graph neural networks -- Graph Deviation Networks (GDN) that can leverage a small number of labeled anomalies for enforcing 
  statistically significant deviations between abnormal and normal nodes on a network; (2) equipping the proposed GDN with a new cross- network meta-learning algorithm 
  to realize few-shot network anomaly detection by transferring meta-knowledge from multiple auxiliary networks. Extensive experimental evaluations demonstrate the 
  efficacy of the proposed approach on few-shot or even one-shot network anomaly detection.
  
- MSTREAM: Fast Anomaly Detection in Multi-Aspect Streams

  **Authors:** Siddharth Bhatia (National University of Singapore), Arjit Jain (IIT Bombay), Pan Li (Purdue University), Ritesh Kumar (IIT Kanpur) and Bryan Hooi (National University of Singapore).

  **Abstract:** Given a stream of entries in a multi-aspect data setting i.e., entries having multiple dimensions, how can we detect anomalous activities in an unsupervised 
  manner? For example, in the intrusion detection setting, existing work seeks to detect anomalous events or edges in dynamic graph streams, but this does not allow us 
  to take into account additional attributes of each entry. Our work aims to define a streaming multi-aspect data anomaly detection framework, termed MSTREAM which can 
  detect unusual group anomalies as they occur, in a dynamic manner. MSTREAM has the following properties: (a) it detects anomalies in multi-aspect data including both 
  categorical and numeric attributes; (b) it is online, thus processing each record in constant time and constant memory; (c) it can capture the correlation between 
  multiple aspects of the data. MSTREAM is evaluated over the KDDCUP99, CICIDS-DoS, UNSW-NB 15 and CICIDS-DDoS datasets, and outperforms state-of-the-art baselines.

- SDFVAE: Static and Dynamic Factorized VAE for Anomaly Detection of Multivariate CDN KPIs

  **Authors:** Liang Dai (Institute of Information Engineering, Chinese Academy of Sciences), Tao Lin (Communication University of China), 
  Chang Liu (Institute of Information Engineering, Chinese Academy of Science & University of Chinese Academy of Sciences), 
  Bo Jiang (School of Electronic Information and Electrical Engineering, Shanghai Jiao Tong University), 
  Yanwei Liu (Institute of Information Engineering, Chinese Academy of Sciences), Zhen Xu (INSTITUTE OF INFORMATION ENGINEERING,CAS) and 
  Zhi-Li Zhang (University of Minnesota).
  
  **Abstract:** Content Delivery Networks (CDNs) are critical for providing good user experience of cloud services. CDN providers typically collect various 
  multivariate Key Performance Indicators (KPIs) time series to monitor and diagnose system performance. State-of-the-art anomaly detection methods mostly use 
  deep learning to extract the normal patterns of data, due to its superior performance. However, KPI data usually exhibit non-additive Gaussian noise, which 
  makes it difficult for deep learning models to learn the normal patterns, resulting in degraded performance in anomaly detection. In this paper, we propose 
  a robust and noise-resilient anomaly detection mechanism using multivariate KPIs. Our key insight is that different KPIs are constrained by certain time-invariant 
  characteristics of the underlying system, and that explicitly modelling such invariance may help resist noise in the data. We thus propose a novel anomaly 
  detection method called SDFVAE, short for Static and Dynamic Factorized VAE, that learns the representations of KPIs by explicitly factorizing the latent 
  variables into dynamic and static parts. Extensive experiments using real-world data show that SDFVAE achieves a F1-score ranging from 0.92 to 0.99 on both 
  regular and noisy dataset, outperforming state-of-the-art methods by a large margin.
  
- NTAM: Neighborhood-Temporal Attention Model for Disk Failure Prediction in Cloud Platforms

  **Authors:** Chuan Luo (Microsoft Research), Pu Zhao (Microsoft Research), Bo Qiao (Microsoft Research), Youjiang Wu (Microsoft Azure), 
  Hongyu Zhang (The University of Newcastle), Wei Wu (Leibniz University Hannover), Weihai Lu (Microsoft Research), Yingnong Dang (Microsoft Azure), 
  Saravanakumar Rajmohan (Microsoft Office), Qingwei Lin (Microsoft Research) and Dongmei Zhang (Microsoft Research).
  
  **Abstract:** With the rapid deployment of cloud platforms, high service reliability is of critical importance. An industrial cloud platform contains 
  a huge number of disks and disk failure is a common cause of service unreliability. In recent years, many machine learning based disk failure prediction 
  approaches have been proposed, which can predict disk failures based on disk status data before the failures actually happen. In this way, proactive actions 
  can be taken in advance to improve service reliability. However, existing approaches treat each disk individually and do not explore the influence of 
  the neighboring disks. In this paper, we propose Neighborhood-Temporal Attention Model (NTAM), a novel deep learning based approach to disk failure 
  prediction. When predicting whether or not a disk will fail in near future, NTAM is a novel approach that not only utilizes a disk's own status data, but 
  also considers its neighbors' status data. Moreover, NTAM includes a novel attention-based temporal component to capture the temporal nature of the disk 
  status data. Besides, we propose a data enhancement method, called Temporal Progressive Sampling (TPS), to handle the extreme data imbalance issue. We 
  evaluate NTAM on a public dataset as well as two industrial datasets collected from around 9 million of disks in an industrial public cloud platform. Our 
  experimental results show that NTAM significantly outperform state- of-the-art competitors. Also, our empirical evaluations indicate the effectiveness of 
  the neighborhood-ware component and the temporal component underlying NTAM and the effectiveness of TPS. More encouragingly, we have successfully applied 
  NTAM and TPS to Company M's public cloud platform and obtained practical benefits in industrial practice.
  
  

## Time series

- Network of Tensor Time Series

  **Authors:** Baoyu Jing (University of Illinois at Urbana-Champaign), Hanghang Tong (University of Illinois at Urbana-Champaign) and Yada Zhu (IBM Thomas J. Watson Research Center).
  
  **Abstract:** Co-evolving time series appears in a multitude of applications such as environmental monitoring, financial analysis, and smart transportation. 
  This paper aims to address the following three challenges, including (C1) how to effectively model its multi-mode tensor structure at each time step; 
  (C2) how to incorporate explicit relationship networks of the time series; (C3) how to model the implicit relationship of the temporal dynamics. We propose a 
  novel model called Network of Tensor Time Series, which is comprised of two modules, including Tensor Graph Convolutional Network (TGCN) and Tensor Recurrent 
  Neural Network (TRNN). TGCN tackles the first two challenges by generalizing Graph Convolutional Network (GCN) for flat graphs to tensor graphs, which captures 
  the synergy between multiple graphs associated with the tensors. TRNN leverages tensor decomposition to balance the trade-off between the commonality and 
  specificity of the co-evolving time series. The experimental results on five real-world datasets demonstrate the efficacy of the proposed method.

- Radflow: A Recurrent, Aggregated, and Decomposable Model for Networks of Time Series

  **Authors:** Alasdair Tran (Australian National University), Alexander Mathews (Australian National University), Cheng Soon Ong (CSIRO) and Lexing Xie (Australian National University).
  
  **Abstract:** We propose a new model for networks of time series that influence each other. Graph structures among time series is found in diverse domains, 
  such as web traffic influenced by hyperlinks, product sales influenced by recommendation, or urban transport volume influenced by the road network and weather. 
  There has been recent progress in modeling graphs and time series, respectively, but an expressive and scalable approach for a network of series does not yet 
  exist. We introduce Radflow, a novel model that embodies three main ideas: the recurrent structure of LSTM to obtain time- dependent node embeddings, 
  aggregation of the flow of influence from other nodes with multi-head attention, and multi-layer decomposition of time series. Radflow naturally takes 
  into account dynamic networks where nodes and edges appear over time, and it can be used for prediction and data imputation tasks. On four real-world datasets 
  ranging from a few hundred to a few hundred thousand nodes, we observe Radflow variants being the best performing model across all tasks. We also report that 
  the recurrent component in Radflow consistently outperforms N-BEATS, the state-of-the-art time series model. We show that Radflow can learn different trends 
  and seasonal patterns, that it is robust to missing nodes and edges, and that correlated temporal patterns among network neighbors reflect influence strength. 
  We curate WikiTraffic, the largest dynamic network of time series with 360K nodes and 22M time-dependent links spanning five years---this dataset provides an 
  open benchmark for developing models in this area, and prototyping applications for problems such as estimating web resources and optimizing collaborative 
  infrastructures. More broadly, Radflow can be used to improve the forecasts in correlated time series networks such as the stock market, or impute missing 
  measurements of natural phenomena such as geographically dispersed networks of waterbodies.
  
  
## micro-service / cloud native

- MicroRank: End-to-End Latency Issue Localization with Extended Spectrum Analysis in Microservice Environments

  **Authors:** Guangba Yu (Sun Yat-Sen University), Pengfei Chen (Sun Yat-sen University), Hongyang Chen (Sun Yat-sen University), Zijie Guan (Tencent), 
  Zicheng Huang (Sun Yat-sen University), Linxiao Jing (Sun Yat-sen University), Tianjun Weng (Sun Yat-Sen University), Xinmeng Sun (Sun Yat-Sen University) 
  and Xiaoyun Li (Sun Yat-sen University).
  
  **Abstract:** With the advantages of strong scalability and fast delivery, microser-vice has become a popular software architecture in the modern ITindustry. 
  Most of microservice faults manifest themselves in terms of service latency increase and impact user experience. The explosion in the number of service 
  instances and complex dependencies among them make the application diagnosis extremely challenging.To help understand and troubleshoot a microservice system,
  the end-to-end tracing technology has been widely applied to capturethe execution path of each request. However, the tracing data are not fully leveraged by 
  cloud and application providers when con-ducting latency issue localization in the microservice environment.This paper proposes a novel system ,named MicroRank, 
  which analyzes clues provided by normal and abnormal traces to locateroot causes of latency issues. Once a latency issue is detected by the Anomaly Detector 
  in MicroRank, the cause localization procedure is triggered. MicroRank first distinguishs which traces are abnormal. Then, MicroRank's PageRank Scorer module 
  uses the abnormal and normal trace information as its input and differentials the importance of different traces to extended spectrum techniques . Finally, 
  the spectrum techniques can calculate the ranking list based on the weighted spectrum information from PageRank Scorer to locate root causes more effectively. 
  The experimental evaluationson a widely-used open-source system and a production system show that MicroRank achieves excellent results not only in one root 
  cause situation but also in two issues that happen at the same time. Moreover,MicroRank makes 6% to 22% improvement in recall in localizing root causes 
  compared to current state-of-the- art methods.


## Augmentation

- Graph Contrastive Learning with Adaptive Augmentation

  **Authors:** Yanqiao Zhu (Institute of Automation, Chinese Academy of Sciences), Yichen Xu (Beijing University of Posts and Telecommunications), 
  Feng Yu (Alibaba), Qiang Liu (RealAI and Tsinghua University), Shu Wu (Institute of Automation, Chinese Academy of Sciences) and 
  Liang Wang (Institute of Automation, Chinese Academy of Sciences).
  
  **Abstract:** Recently, contrastive learning (CL) has emerged as a successful method for unsupervised graph representation learning. Most graph CL methods first 
  perform stochastic augmentation on the input graph to obtain two graph views and maximize the agreement of representations in the two views. Despite the prosperous
  development of graph CL methods, the design of graph augmentation schemes—a crucial component in CL—remains rarely explored. We argue that the data augmentation
  schemes should preserve intrinsic structural and attribute information of graphs, which will force the model to learn representations that are insensitive to 
  perturbation on unimportant nodes and edges. However, most existing methods adopt uniform data augmentation schemes, like uniformly dropping edges and uniformly 
  shuffling features, leading to suboptimal performance. In this paper, we propose a novel graph contrastive representation learning method with adaptive augmentation 
  that incorporates various priors for topological and semantic aspects of the graph. Specifically, on the topology level, we design augmentation schemes based on 
  node centrality measures to highlight important connective structures. On the node attribute level, we corrupt node features by adding more noise to unimportant 
  node features, to enforce the model to recognize underlying semantic information. We perform extensive experiments of node classification on a variety of real-world 
  datasets. Experimental results demonstrate that our proposed method consistently outperforms existing state-of-the-art methods and even surpasses some supervised 
  counterparts, which validates the effectiveness of the proposed contrastive framework with adaptive augmentation.
  
  
