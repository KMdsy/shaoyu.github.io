# 微服务框架下的多源异构数据异常检测 - 调研

[裴丹团队的主页](https://netman.aiops.org/publications/)

[2020 AIOPS workshop](https://aiopsworkshop.github.io/accepted_papers/index.html)

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
	
	

	

	

	

**conclusion:** 
目前来讲，已有的工作包括联合使用trace与log数据，此外也有kpi+log的工作，但是三者相结合，或者kpi+trace的工作还没有。所有的工作大体处于较为基础的阶段，即对缺失数据、可解释方法、数据特性等研究的还不够

**需要做的事情：**
1. 需要了解云原生系统的内部结构，对日志数据、调用链数据的生成与特性有明确的认知与归纳。方法，从开源代码入手，尝试搭建一个微服务测试平台，尝试做数据收集的实验。

2. 先能够了解清楚每个数据的特性，尝试复现一个多源异构数据异常检测的工作。

3. 从复现过程与系统搭建过程中考虑适当的应用场景，联合利用服务性能指标数据（KPI，时间序列）、微服务日志（非结构化文本数据）、调用链数据进行异常检测。

4. 将上述场景下的可解释的异常检测作为工作的重点。

**数据**

1. https://zenodo.org/record/3549604#.YEGfWI5LiUk
	
	一个公开数据集，里面包括AIOPS常见的三种数据
	

	
2. test bed搭建：

	framework：OpenStack, Kolla-Ansible(dockerized environment)/k8s
	For the **metrics** collection across the physical nodes in the infrastructure, we utilize [Glances](20),
	
	OpenStack introduces a small but powerful library called [*osprofiler*](21) that is used by all OpenStack projects and their Python clients to generate **traces**.
	
	The **log** files are distributed over the infrastructure and they are grouped in directories by the OpenStack projects (e.g., nova, neutron, glance, etc.) at the wally nodes.
	
	
	
	
	
	
	anomaly injection: (ref) Multi-source Distributed System Data for AI-Powered Analytics
	
	To generate workloads and inject faults into the infrastructure we used [Rally](25)
	
	
----
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


- Detecting anomalies in microservices with execution trace comparison

	Lun Meng, Feng Ji, Yao Sun, TaoWang
	
	Future Generation Computer Systems, Volume 116, March 2021, Pages 291-301
	
	
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
	
### Dataset

- ToN IoT-The role of heterogeneity and the need for standardization of features and attack types in IoT network intrusion datasets


### 没啥用的文章

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
