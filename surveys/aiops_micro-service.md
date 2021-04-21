# 微服务框架下的多源异构数据异常检测 - 调研

[裴丹团队的主页](https://netman.aiops.org/publications/)

[2020 AIOPS workshop](https://aiopsworkshop.github.io/accepted_papers/index.html)

## 一些笔记

在相关工作中，所要检测的异常如何定义，是一个关键的问题。<a href='#lundetecting2019'>本文提到</a>"error messages", "performance degradations"与"trace structure and response time anomalies"本身就是几种不同的异常类型，融合多种数据将有助于我们探测更多种类的异常。

## 相关论文

### 关于多源数据融合的文章

- **Multi-Source Anomaly Detection in Distributed IT Systems**
	
	Jasmin Bogatinovski, Sasho Nedelkoski
	
	知乎解析：[link](https://zhuanlan.zhihu.com/p/347051870)
	
	2020 AIOPS workshop
	
	联合使用了日志与trace数据做异常检测
	
	
- **Multi-source Distributed System Data for AI-Powered Analytics**

	Sasho Nedelkoski, Jasmin Bogatinovski, Ajay Kumar Mandapati, Soeren Becker, Jorge Cardoso, Odej Kao
	
	European Conference on Service-Oriented and Cloud Computing, ESOCC 2020: Service-Oriented and Cloud Computing
	
	开发了一个用于捕捉多源（三种）数据的一个分析平台，对这个test bed做了描述
	
	

- **An Intelligent Anomaly Detection Scheme for Micro-Services Architectures With Temporal and Spatial Data Analysis**

	Yuan Zuo; Yulei Wu; Geyong Min; Chengqiang Huang; Ke Pei
	
	IEEE Transactions on Cognitive Communications and Networking ( Volume: 6, Issue: 2, June 2020)
	
	联合使用日志（时间数据）和调用链数据query trace（空间数据）做特征提取与融合，并构建one-class classifier
	
	
### 微服务架构下的异常检测

#### 基于调用链数据

- **Observing and Controlling Performance in Microservices**

	学术毕业论文：André Pascoal Bento
	
	讲使用trace数据，建模系统中微服务之间的依赖关系，并建立为图模型，然后计算出每个依赖关系之间的应答响应时间
	

- Unsupervised Detection of Microservice Trace Anomalies through Service-Level Deep Bayesian Networks

	Ping Liu; Haowen Xu; Qianyu Ouyang; Rui Jiao; Zhekang Chen; Shenglin Zhang; ...
	
	2020 IEEE 31st International Symposium on Software Reliability Engineering (ISSRE)
	
	**基于微服务trace数据，检测意外的调用关系或者意外的调用响应时间**
	

- Anomaly Detection from System Tracing Data Using Multimodal Deep Learning

	Sasho Nedelkoski; Jorge Cardoso; Odej Kao
	
	2019 IEEE 12th International Conference on Cloud Computing (CLOUD)
	
	从**trace数据**中解析多模态数据以进行学习，多模态指“service response time in the form of real-valued data”， “causal relationships with other related services repre-
	sented as a sequence of textual labels.”

	我们提出了一种用于序列学习的深度学习模型，利用单模态顺序文本数据在跟踪中对服务之间的因果关系进行建模。我们展示了响应时间作为跟踪中的第二种数据类型的重要性，以及对其建模的挑战。通过引入一个模型，我们扩展了单模态体系结构，该模型利用多模态跟踪数据作为文本和实值序列的组合。我们表明，多模态方法可以用于建模正常的系统行为和检测异常，不仅考虑到服务的因果关系，而且还考虑它们在跟踪内的响应时间。此外，我们使用该模型来检测依赖的和并行的任务，以重构执行路径。


- Self-Supervised Anomaly Detection from Distributed Traces

	Jasmin Bogatinovski; Sasho Nedelkoski; Jorge Cardoso; Odej Kao
	
	2020 IEEE/ACM 13th International Conference on Utility and Cloud Computing (UCC)
	

- MicroRCA: Root Cause Localization of Performance Issues in Microservices

	Li Wu; Johan Tordsson; Erik Elmroth; Odej Kao
	
	NOMS 2020 - 2020 IEEE/IFIP Network Operations and Management Symposium
	

- Anomaly Detection and Classification using Distributed Tracing and Deep Learning

	Sasho Nedelkoski; Jorge Cardoso; Odej Kao
	
	2019 19th IEEE/ACM International Symposium on Cluster, Cloud and Grid Computing (CCGRID)


- <a name='lundetecting2021'>1</a>Detecting anomalies in microservices with execution trace comparison

	Lun Meng, Feng Ji, Yao Sun, TaoWang
	
	Future Generation Computer Systems, Volume 116, March 2021, Pages 291-301

	本文所建立的调用树中包含了两种调用关系——本地调用（两个微服务位于同一个主机，彼此之间进行调用）、远程调用（两个微服务不在同一个主机，远程调用）。
	
	本文提出了一种基于调用链数据的异常检测方法，拟检测的异常分为两种：1) 调用关系异常：调用关系本身并不是一成不变的，调用关系会因为调用时的参数而发生动态变化，但是某些异常会导致微服务调用不常见的异常的调用总是与已有的调用关系不同，因此可以被检测出来；2) 调用响应异常：这种异常不会破坏调用关系，但是会直接影响服务迟延，因此也是异常。
	
	为解决调用关系异常，本文**首先**收集软件测试期间的调用链数据用于合成应用运行时的tarce tree，注意由于trace tree会因为调用携带的参数不同而不同，因此在软件测试阶段收集（几乎）所有情况的调用关系数据是有必要的。**然后**将实时的调用链数据与刚才的baseline之间计算最小编辑距离（baseline中有多种调用baseline，因此需要与每一个baseline计算他们之间的距离，取距离最小的baseline作为正常模板，并计算anomaly score），以作为anomaly score。
	
![image](https://user-images.githubusercontent.com/16149619/115551293-6ae81980-a2dd-11eb-97fa-11709d15d3ad.png)
	
	调用时间在物理资源充分的情况下，一般是不会有大的波动的，因此，调用时间的激增就可以被视为一个调用时间异常。为了识别_激增_，本文使用coefficient of variation（CV）来表示一次请求的响应时间异常程度。此时的trace数据被用一个$M*N$的metrix表示，其中第m行第n列表示，在第i次用户请求时，第j个组件（微服务）的响应情况。然后借助PCA对矩阵进行分解，用来识别导致异常的微服务。这里没太看懂。

![image](https://user-images.githubusercontent.com/16149619/115550685-b9e17f00-a2dc-11eb-9094-980b220a86f3.png)
![image](https://user-images.githubusercontent.com/16149619/115550693-bea63300-a2dc-11eb-8f08-d44732ca1b41.png)

	
	
- Midiag: A Sequential Trace-Based Fault Diagnosis Framework for Microservices
	
	Lun Meng, Yao Sun, Shudong Zhang
	
	International Conference on Services Computing, SCC 2020: Services Computing – SCC 2020 pp 137-144
	
	
- MicroRAS: Automatic Recovery in the Absence of Historical Failure Data for Microservice Systems

	Li Wu; Johan Tordsson; Alexander Acker; Odej Kao
	
	2020 IEEE/ACM 13th International Conference on Utility and Cloud Computing (UCC)
	
------------

#### 基于日志数据

- 基于日志解析的大规模微服务架构软件系统异常检测

	Anomaly Detection of Large Scale Microservice Architecture Software System Based on Log Parsing

	邰丽媛, 田春岐 ：同济大学计算机科学与技术系，上海;
	王 伟 ：华东师范大学数据科学学院，上海;
	
- Root-Cause Metric Location for Microservice Systems via Log Anomaly Detection

	Lingzhi Wang; Nengwen Zhao; Junjie Chen; Pinnong Li; Wenchi Zhang; Kaixin Sui
	
	2020 IEEE International Conference on Web Services (ICWS)	
	
	
- Anomaly Detection of Large Scale Microservice Architecture Software System Based on Log Parsing

	Liyuan Tai, Chun-qi Tian, W. Wang


------------

#### 基于时间序列数据

- Localizing Failure Root Causes in a Microservice through Causality Inference 
	
	Yuan Meng; Shenglin Zhang; Yongqian Sun; Ruru Zhang; Zhilong Hu; Yiyin Zhang, ...
	
	2020 IEEE/ACM 28th International Symposium on Quality of Service (IWQoS)
	
	**基于微服务KPI数据的关联推断方法**
	
	我们设计了一种新的PCTS(路径条件时间序列)算法，在充分利用传播延迟的情况下学习监控指标的依赖图。在PCTS中，我们首先采用改进的PC[10]学习时间序列中每个点的因果图。然后生成两个时间序列之间的边，生成失效因果图。
	
	我们提出了一种新的基于时间原因的随机漫步(TCORW)方法。在TCORW中，我们成功地整合了三种类型的信息:(1)监测指标的因果关系;(2)度量的异常信息，包括发生时间和异常程度;(3)基于领域知识获得的度量优先级
	
	结合PCTS和TCORW，我们提出了一个新的框架——微原因，来推断微服务失败的前N个根本原因。据我们所知，这是在微服务中定位故障根源的第一个工作。


- Performance Diagnosis in Cloud Microservices using Deep Learning
	
	Li Wu, Jasmin Bogatinovski, Sasho Nedelkoski, Johan Tordsson and Odej Kao
	
	2020 AIOPS workshop
	
	**多源时间序列的异常检测与根因定位**——我们从多个数据源收集数据，包括应用程序、操作系统和网络，以提供由不同根源(如软件bug、硬件问题、资源争用等)引起的性能问题的罪魁祸首。我们的系统被设计成**与应用程序无关的**，不需要应用程序使用仪器来获取数据。相反，我们收集应用程序和运行时系统本身报告的指标。
	
	本文提出了一种应用不可知系统，以细粒度定位微服务性能下降的罪魁祸首，不仅包括产生性能问题的异常服务，还包括与服务异常相关的罪魁祸首指标。我们的方法首先通过构建服务依赖图来发现潜在的罪魁祸首服务，然后应用自动编码器根据重构错误的排序列表来识别异常服务指标。
	
	我们采用两阶段方法进行异常检测和根本原因分析(系统概述在第3节中描述)。在第一阶段，我们根据基于图的方法[16]对导致故障的服务进行建模。这使我们能够通过识别导致错误服务性能下降的根本原因(异常度量)来查明引发性能下降的潜在错误服务。第二阶段，对潜在故障的推断，是基于以下假设:故障行为的最重要症状与正常运行时的值存在显著偏差。在任何时间点测量每个症状的个体贡献，从而导致观察到的行为与正常行为之间的差异，从而可以定位最可能反映故障的症状。有了这个假设，我们的目标是在正常系统行为下模拟症状值
	


- TELESTO: A Graph Neural Network Model for Anomaly Classification in Cloud Services
	
	Dominik Scheinert and Alexander Acker
	
	2020 AIOPS workshop
	
	**多维时间序列的异常分类任务**，即不仅只识别正异常，还是被异常的种类

	我们提出了一种通过训练分类模型来识别再次出现的异常的方法。利用系统度量数据，如CPU利用率、已分配内存或磁盘I/O统计数据，并将这些数据建模为多元时间序列，我们的模型能够识别异常类型特定的模式，并为它们分配各自的异常标签。

	我们提出的模型架构TELESTO利用一种新颖的图神经网络架构，在空间和时间维度上利用多变量时间序列建模为图。它不受维度变化的影响，优于其他两种常用的图神经网络方法。

--------------
	
## Dataset

1. ToN IoT-The role of heterogeneity and the need for standardization of features and attack types in IoT network intrusion datasets


2. https://zenodo.org/record/3549604#.YEGfWI5LiUk
	
	一个公开数据集，里面包括AIOPS常见的三种数据
	

	
3. test bed搭建：

	framework：OpenStack, Kolla-Ansible(dockerized environment)/k8s
	For the **metrics** collection across the physical nodes in the infrastructure, we utilize [Glances](20),
	
	OpenStack introduces a small but powerful library called [*osprofiler*](21) that is used by all OpenStack projects and their Python clients to generate **traces**.
	
	The **log** files are distributed over the infrastructure and they are grouped in directories by the OpenStack projects (e.g., nova, neutron, glance, etc.) at the wally nodes.
	
	anomaly injection: (ref) Multi-source Distributed System Data for AI-Powered Analytics
	
	To generate workloads and inject faults into the infrastructure we used [Rally](25)	

### Trace data
	
1. Azure Public dataset: composes of two datasets representing two representative traces of the virtual machine of Microsoft Azure
	
	[link](5)
	
2. Alibaba’s cluster data is a collection of two datasets from real-world production

	[link](2, 14, 28)
	
3. Google’s collection of two tracing datasets originates from parts of Google cluster management software and systems

	[link](10)
	
### metric data

1. A plethora of available collections of datasets containing metric data can be found in Stonybrook

	[link](31)

2. [Numenta](1) predominantly contains datasets
from streaming and real-time applications, while [Harvard](9), [ELKI](8), [LMU](15) store network intrusion data.


### log data

1. The [CFDR resource](3) stores links or 19 log datasets grouped in 11 data collections.

2. The second resource is the [loghub data resource](35).
	

------------------

## 没啥用的文章

- **MicroMon: A Monitoring Framework for Tackling Distributed Heterogeneity**

	Babar Khalid, Nolan Rudolph, Ramakrishnan Durairajan, Sudarsun Kannan
	
	12th {USENIX} Workshop on Hot Topics in Storage and File Systems (HotStorage 20).
	
	没啥用，描述了一种在微服务上运行的监视系统，主要应对的是微服务系统的软件/硬件异质性问题，提高监视系统的吞吐量
	
- **Advancing Monitoring in Microservices Systems**

	Marcello Cinque; Raffaele Della Corte; Antonio Pecchia
	
	2019 IEEE International Symposium on Software Reliability Engineering Workshops (ISSREW)
	
	没啥用，描述了一种在微服务上运行的监视系统
	
- **学位论文：ANOMALY DETECTION IN CLOUD-NATIVE SYSTEMS**

	Surace, Pino' (2019)
	
	没啥用，讲了一些云原生应用中的组件综述，以及如何用简单的ML方法利用微服务中的时间序列做异常检测
	
- Artificial Intelligence for IT Operations (AIOPS) Workshop White Paper

	Jasmin Bogatinovski, Sasho Nedelkoski, Alexander Acker, Florian Schmidt, Thorsten Wittkopp, Soeren Becker, Jorge Cardoso, Odej Kao

	white paper for the AIOPS 2020 workshop at ICSOC 2020
