# 监视时间序列（特别是针对运维的监控时间序列数据）

总结几个点：1
1. 数据集名称与链接
2. 数据集背景：数据集的描述对象是什么
3. 数据集任务：该数据集采集的时候的原始任务是什么
4. 数据集格式（可选的）

### 运维监控时间序列的特征




## 运维时间序列

1. [计算机服务器的运行状况监视和预测](https://catalog.data.gov/dataset/health-monitoring-and-prognostics-for-computer-servers)
	
	+ 描述：关键任务系统的诊断解决方案需要一种全面的方法来主动检测和隔离故障，推荐和指导基于状况的维护措施，
	并实时估算关键组件和相关子系统的剩余使用寿命。一个主要的挑战是将预测的优势扩展到包括计算机服务器和其他电子组件。
	预测能力的关键推动因素是监视与执行组件和子系统的运行状况有关的时间序列信号。时间序列信号使用模式识别进行实时处理，
	以进行主动异常检测和剩余使用寿命估算。将提供使用模式识别技术来早期检测已知会导致电子系统故障的多种机制的示例，
	包括：环境问题；软件老化；传感器降级或故障；硬件组件的退化；机械，电子和光学互连的性能下降。
	预后模式分类有助于大幅提高组件的可靠性裕度和系统可用性目标，同时减少昂贵的“无故障”事件的来源，
	这些事件已成为重要的保修成本问题。

	+ 任务：anomaly detection, time series prediction

	+ [google link](https://datasetsearch.research.google.com/search?query=monitoring%2C%20time%20series&docid=cp3L%2BCfAjd47GckZAAAAAA%3D%3D)

2. [Numenta异常基准（NAB）](https://www.kaggle.com/boltzmannbrain/nab)

	+ 描述：58个时间序列数据文件的NAB语料库旨在为流异常检测中的研究提供数据。它由真实世界和人为的时间序列数据组成，
	其中包含标记的异常行为时期。数据是有序的，带有时间戳的单值指标。除非另有说明，否则所有数据文件均包含异常。
	大多数数据来自各种来源，例如AWS服务器指标，Twitter量，广告点击指标，流量数据等。
	
	+ 任务：anomaly detection, prediction
	
	+ [google link](https://datasetsearch.research.google.com/search?query=cpu%2C%20time%20series&docid=iXJXcx2EBRKHZSc8AAAAAA%3D%3D)
	
	
	
3. **挺好的数据集**企业级应用程序运维 

	[原始数据](https://www.kaggle.com/anomalydetectionml/rawdata), 
	[feature data](https://www.kaggle.com/anomalydetectionml/features)
	
	+ 描述：一个企业级软件的运维时间序列，原始数据链接中是没有正常、异常标签的原始数据，数据更加详细。features中是经过处理和标签后的数据，
	将原始数据中的同一时刻的数据全都拼接在了一起，形成了非常高维度的数据。
	
	+ 任务：异常检测
	

4. Azure 服务器CPU时间序列 [link](https://www.kaggle.com/amcs1729/azure-data)

	+ 描述：某个Azure服务器的CPU运转时间序列，单维时间序列。
	
	+ 任务：时间序列预测


5. 应用程序运维 [link](https://www.kaggle.com/wolfgangb33r/usercount)

	+ 描述：某个应用程序在一段时间内的一些统计信息，
	**数据包括：** 时间戳、距离上次记录时间内的用户访问次数、距离上次记录时间内产生的会话次数、距离上次记录时间新增的用户数、
	距离上次记录时间内的应用崩溃次数。
	
	+ 任务：回归、预测



6. 服务器运维日志，运维日志 [link](https://www.kaggle.com/kartikjaspal/server-logs-suspicious)
	
	+ 描述：服务器攻击数据集，记录了1. 攻击时间和持续时间，2. 源IP和目的IP，3. 数据包，字节，流和标志，4.类型，ID和标签/类
	
	+ 任务：分类、异常检测



7. [电梯设备的运维数据集](https://zenodo.org/record/3653909#.X0hlBMhLiUk)

	+ 描述：华为慕尼黑研究中心的公开（匿名）预测性维护数据集。来自各种IoT传感器的数据集，用于电梯行业的预测性维护。
	该数据可用于电梯门的预测维护，以减少计划外的停机并最大程度地延长设备使用寿命。数据集包含操作数据，
	该数据以时间序列的形式在建筑物的高峰和夜间电梯使用中以4Hz采样（16:30到23:30之间）。对于电梯轿厢门，
	我们考虑的系统是：机电传感器（门球轴承传感器），环境（湿度）和物理（振动）。

	+ 任务：预测（无标签）

	+ 形式：time series，无标签，维度为3，有相关论文引用

	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=lvVz38vzKrmGqZ48AAAAAA%3D%3D)


8. **挺好的数据集**  大数据平台运维数据集 [link](https://zenodo.org/record/3549604#.X0hpFMhLiUk)

	+ 描述：[相关论文](https://link.springer.com/chapter/10.1007/978-3-030-44769-4_13), OpenStack是一个云操作系统，
	它控制整个数据中心内的大型计算，存储和网络资源池，所有这些资源均通过具有通用身份验证机制的API进行管理和配置。
	出于生成数据的目的，它包含一个名为wally-113的控制节点和四个计算节点：wally-122，wally-123，wally-124
	和wally- 117。它已部署在群集的裸机节点上，每个节点具有16 GB的RAM，3个1TB磁盘和2个1Gbit以太网NIC。
	将三个硬盘组合到软件RAID 5中以实现数据冗余。
	**工作负载与故障类型：**  1. Create and delete server; 2. Create and delete image; 3. Create and delete network; 
	**数据：** 1. Metrics:  CPU, MEM and load of the machine (either controller or the compute nodes). 2. Logs: 每个物理主机与上面的项目所生成的日志 3. Traces:  It generates one trace per request, that goes through all involved services, and builds a tree of calls which captures a workflow of service invocations, request types: HTTP, RPC, DB API, Driver.
	
	+ 任务：异常检测
	
	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=Vac33QBm10kwUw0FAAAAAA%3D%3D)
	
9. 智能手机上的恶意软件与恶意活动记录 [link](http://bigdata.ise.bgu.ac.il/sherlock/)
	
	+ 描述：该数据集本质上是一个庞大的时间序列数据集，几乎涵盖了可以从Samsung Galaxy S5智能手机进行采样的每种软件
	和硬件传感器的类型，而无需root特权。数据集包含超过100亿条数据记录中的6,000亿个数据点。
	我们提供了明确的标签（时间戳和描述），可以准确捕获设备上的恶意软件何时执行其恶意活动。通过这些标签，您可以将数据集用作机器学习算法的基准。
	**数据包括：**呼叫/ SMS日志、位置、WiFi信号强度、网络统计信息、其他...（参见数据集描述页面）
	
	+ 任务：恶意活动检测、恶意软件检测
	
	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=5CKm58KTxK6n3a22AAAAAA%3D%3D), [other link](https://www.impactcybertrust.org/dataset_view?idDataset=1258)

10. 视频应用的服务质量检测数据集 [link](https://zenodo.org/record/3459164#.X0h2bMhLiUk)
	
	+ 描述：场景为在用户设备上使用LTE网络访问一个基于GStreamer的MPEG-DASH视频软件时的应用服务质量。
	用户首先要从分布式DASH服务器上下载MPEG-DASH视频文件，过程中收集下述的信息：
	1. Date: date when the data is collected;
	2. Player: type of the player (in this case it is always "GStreamer");
	3. Num: identifier of the player;
	4. URLVid: URL of the MPD file;
	5. Latency: latency experienced by the player;
	6. BW: bandwidth experienced by the player;
	7. Quality: chosen DASH video representation;
	在实验过程中，其他播放器运行以在类似CDN的服务器上生成逼真的媒体流流量。 这些玩家通过遵循Poisson或Pareto分布开始游戏。
	
	+ 任务：时间序列预测，网络承载能力预测
	
	+ [google link](https://zenodo.org/record/3459164#.X0h2bMhLiUk)	
	
11. 加密劫持攻击时间序列数据集 [link](https://www.kaggle.com/keshanijayasinghe/cryptojacking-attack-timeseries-dataset)

	+ 描述：加密劫持是未经授权使用他人的计算机来开采加密货币。加密挖矿代码在后台运行，
	因为毫无戒心的受害者会正常使用他们的计算机。他们可能会注意到的唯一迹象是性能降低或执行滞后。
	最近，由于服务器的强大计算能力和许多配置不当的服务器设置，攻击者已将目标从个人计算机转移到云服务器。
	尽管已经设计了许多统计方法来进行密码劫持攻击检测，但是设计具有低计算开销的实时检测器仍然是主要问题之一。
	另一方面，对新检测算法和技术的评估在很大程度上依赖于设计良好的数据集的存在。
	**数据包括：**三个csv文件（异常、正常、完整），每个文件分别有关于服务器的多种指标（CPU, MEM, DISK）
	
	+ 任务：异常检测（但是好像没有给出异常的形式、对应每个时间戳的标签）

	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=Ylcq22ZqJG16NqBSAAAAAA%3D%3D)
	
12. **不错的数据集** Antarex HPC (High Performance computer) 故障数据集 [link](https://zenodo.org/record/2553224#.X0iokshLiUk)

	+ 描述：Antarex数据集包含在进行故障注入时从位于苏黎世联邦理工学院的同名实验HPC系统收集的跟踪数据，目的是对HPC系统进行基于机器学习的故障检测研究。
	为了获取数据，我们执行了基准测试应用程序，并同时通过专用程序在特定时间在系统中注入了错误，从而触发了应用程序行为的异常。我们的数据集中涵盖了广泛的故障，
	从硬件故障到配置错误，最后是由其他过程的干扰导致的性能异常。这是通过作者开发的FINJ故障注入工具实现的。
	**数据集包含两种类型的数据：** 一种类型的数据是指一系列CSV文件，每个文件都包含一组通过LDMS HPC监视框架采样的系统性能指标。
	另一种类型是指日志文件，详细描述数据集中每个时间点的系统状态（即当前正在运行的基准测试应用程序或已注入的故障程序）。
	这种结构使研究人员可以对数据集进行广泛的研究。而且，由于我们是通过流式传输连续数据收集数据集的，
	因此基于该数据集的任何研究都可以轻松地以在线方式在真实的HPC系统上重现。
	**数据集分为两部分：**第一部分仅包括与CPU和内存相关的基准测试应用程序和故障程序，而第二部分则仅与硬盘驱动器相关。
	
	+ 数据描述：注入异常用的脚本也在数据集中可以找到
	
	+ 任务：异常检测
	
	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=8mGvdORXdb72rgUVAAAAAA%3D%3D)
	



## 一般的监视数据

1. [生物量监测数据集, TIME SERIES CHANGE DETECTION FOR BIOMASS MONITORING](https://catalog.data.gov/dataset/scalable-time-series-change-detection-for-biomass-monitoring-using-gaussian-process)
	
	+ 描述：生物量监测，特别是检测某个地理区域的生物量或植被变化，对于研究系统的碳循环至关重要，并且在理解气候变化及其影响方面具有重要意义。
	
	+ 任务：time series change point detection
	
	+ [google link](https://datasetsearch.research.google.com/search?query=monitoring%2C%20time%20series&docid=tv%2FEXqiscaRktAxXAAAAAA%3D%3D)
	

2. 网络流量
https://www.kaggle.com/crawford/computer-network-traffic

3. 水泵故障
https://www.kaggle.com/nphantawee/pump-sensor-data

4. SLA管理
https://www.kaggle.com/imenbenyahia/clearwatervnf-virtual-ip-multimedia-ip-system?select=bono-io.read_kbytes_sec.csv


5. 基于多传感器数据的液压试验台的状态评估 [link](https://www.kaggle.com/jjacostupa/condition-monitoring-of-hydraulic-systems)

	+ 描述：该数据集是通过液压试验台实验获得的。该试验台由一个主要工作装置和一个辅助冷却过滤回路组成，它们通过油箱[1]，[2]连接。该系统周期性地重复恒定的负载循环（持续时间为60秒），
	并在定量改变四个液压组件（冷却器，阀门，泵和蓄能器）的状态的同时，测量压力，体积流量和温度等过程值。

	+ 任务：异常检测、分类、预测
	
	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=pCOC5zkeO5a8CSeGAAAAAA%3D%3D)
	
	
6. 工业流水线刀片磨损情况数据集 [link](https://www.kaggle.com/inIT-OWL/one-year-industrial-component-degradation?select=01-04T184424_001_mode1.csv)

	+ 好像没有明确label，需要联系作者
	


## 其他有趣的数据集

1. 边缘计算数据集
边缘服务器的位置与用户的位置
https://www.kaggle.com/salmaneunus/edge-computing-edge-servers?



2. [交易欺诈检测数据集](https://www.kaggle.com/ntnu-testimon/paysim1)

	+ 描述：PaySim基于从一个非洲国家/地区实施的移动货币服务的一个月财务日志中提取的真实交易样本来模拟移动货币交易。原始日志是由一家跨国公司提供的，该公司是移动金融服务的提供商，该服务目前在全球14个以上的国家/地区中运行。
	
	+ 任务：交易欺诈检测
	
	+ 形式：raw data, 包含交易金额、交易客户、初始余额与新余额、标签（是否为欺诈交易）
	
	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=LUidW2DnXG%2BT%2FEA2AAAAAA%3D%3D)


3. Data for: A study on leading machine learning techniques for high order fuzzy time series forecasting [link](https://data.mendeley.com/datasets/xc6c8xr564/1)
	
	+ 描述：14个子数据集的合集，具体参见 [link](https://www.sciencedirect.com/science/article/pii/S095219761930226X#fig5)
	
	+ 任务：时间序列预测
	
	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=6GYYktv0MMeQl5jGAAAAAA%3D%3D)
	
	
4. BPI挑战 [link](https://www.narcis.nl/dataset/RecordID/uuid%3Ac3e5d162-0cfd-4bb0-bd82-af5268819c35/Language/EN)

	+ 描述： **The challenge is to design a (draft) predictive model, which can be used to implement in a BI environment.** 
	**The purpose of this predictive model will be to support Business Change Management in implementing software releases** 
	**with less impact on the Service Desk and/or IT Operations.** We have prepared several case-files with anonymous 
	information from Rabobank Netherlands Group ICT for this challenge. The files contain record details from an ITIL 
	Service Management tool called HP Service Manager. We provide you with extracts in CSV with the Interaction-, 
	Incident- or Change-number as case ID. Next to these case-files, we provide you with an Activity-log, related to 
	the Incident-cases. There is also a document detailing the data in the CSV file and providing background to the 
	Service Management tool.
	
	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=ICMC800RzMnUdhDMAAAAAA%3D%3D)


5. 	主机网络流量时间序列2019/01 [link](https://zenodo.org/record/2669079#.X0i2AMhLiUk)

	+ 描述：数据集于2019年 1 月在一个月的时间内收集。收集IP流的观察点位于大学校园网络的边界。校园大学网络可使用
	16 CIDR IPv4网络范围，并且包含从连接宿舍的部分（通过服务器部分）到包含大学管理人员的工作站的部分在内的各种网络部分。
	用于创建数据集的原始IP流的大小超过860GB。我们数据集中的主机由其源IPv4地址标识。  
	
	+ 数据集包含以下变量：

		- 聚合 -使用均值/最大/最小聚合函数从一小时不相交的窗口中聚合的五分钟总体积中创建
			- 流数（FL） -给定源IP的流数 
			- 数据包数（PKT） -给定源IP的数据包数
			- 字节数（BYT） -给定源IP的数据包数
			- 流量持续时间（DUR） -平均流量持续时间（以秒为单位）
		- 不重复计数  -使用均值/最大值/最小值聚合函数，在一小时不相交的窗口中聚合的五分钟窗口中每个变量的不重复值计数
			- 对等体数（PEER） -给定源IP的不同通信对等体数
			- 端口数（PORTS） -给定源IP的不同目标端口数
			- 协议数（PROTO） -给定源IP的不同通信协议数
			- AS号数量（AS） -给定源IP的不同目标AS号数量
			- 国家数量（CTRY） -给定源IP的不同目标国家/地区的数量
		- 标签
			- 范围（RNG） -主机所属的网络范围（匿名）
			- 单位（UNT） -拥有网络范围的管理单位
			- 子单位（SUB-UNT） -该单位的子单位
			
	+ 但是好像没有规定具体的任务，label都是主机所属的单位，难道是分类
	
6. 用于应用程序级监视的不同多核处理器对运行时开销的影响的比较 [link](https://zenodo.org/record/7619#.X0i4jMhLiUk)

	+ 描述：连续运行的软件系统需要应用程序级监视，以在运行时保持其性能和可用性。软件系统的性能监视需要将时间序列
	数据存储在监视日志或流中。这样的监视可能会导致被监视系统的大量运行时开销。在本文中，我们评估了多核处理器对
	Kieker应用程序级监视框架的开销的影响。我们将监控开销分为三部分，并使用微基准对受控实验室进行广泛的实验，
	以量化在受控和可重复条件下监控开销的这些部分的结果。我们的实验表明，通过异步写入监视日志，可以在多核处理器上进
	一步减少Kieker框架已经很低的开销。
	
	+ 提供了某个实验在多个CPU上的记录，包括AMD, Intel, T6360, 任务未知
	
	
7. 大型RAID磁盘系统的磁盘替换日志文件示例，用于进行预测性维护分析 [link](https://zenodo.org/record/2580162#.X0i568hLiUk)

	+ 描述：在一个磁盘系统中更换其中的一个磁盘，并记录系统的日志文件。观察磁盘热插拔对系统运行的影响。
	
	+ 官方提供的一些观察
		
		1. 随着时间的流逝，错误会在分组的群集中发生，从而可以进行预测性维护。
		2. 时间和空间上的粒度：热磁盘交换不会干扰RAID系统中的系统可用性。 全机架交换可以。 更糟糕的是，通过在某个特
		定时间购买完整的，庞大的系统，一家公司将在系统生命周期的最后走向创伤性事件。 在较小的时间间隔内安装较小的系
		统组件（阅读：机架）不会危及操作的连续性。
		
		
8. Application Detection through Rich Monitoring Data [link](https://springernature.figshare.com/articles/Artifact_for_Taxonomist_Application_Detection_through_Rich_Monitoring_Data/6384248)
	
	+ 描述：The related study develops a technique named 'Taxonomist' to identify applications running on supercomputers,	
	using machine learning to classify known applications and detect unknown applications. 
	**The technique uses monitoring data such as CPU and memory usage metrics and hardware counters collected from** 
	**supercomputers. The aims of this technique include providing an alternative to 'naive' application detection** 
	**methods based on names of processes and scripts, and helping prevent fraud, waste and abuse in supercomputers.**
	
	+ 任务：应该是分类，还有可能是one-class classification
	
	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=95bGlb7wMSmRtTfiAAAAAA%3D%3D)
	
9. 局域网网络稳定性 - 测量无线与基于以太网的局域网的响应时间 [link](https://www.kaggle.com/garystafford/ping-data)

	+ 描述：目的是在连接到Internet时捕获并可视化LAN网络的时序变化。为此，以10秒为间隔从网络上的一系列IoT收集设备收集ping
	响应时间。定时是从2.4 GHz无线和100 Mbps以太网收集的。测量了从设备到本地Internet路由器以及Internet上第一跳服务器的时间。
	时间序列数据中的间隙表示LAN中断或路由器访问Internet的能力中断。
	ping实用程序使用ICMP协议的强制性ECHO_REQUEST数据报ECHO_RESPONSE从主机或网关获取ICMP 。
	
	+ 没有给定label，但是应该是一个分类问题
	
	+ [google link](https://datasetsearch.research.google.com/save?query=coronavirus%20covid-19&docid=J1jGnseIcAjUTiedAAAAAA%3D%3D)
	
	
----


SMAP (Soil Moisture Active Passive satellite) and MSL (Mars
Science Laboratory rover) are two public datasets from NASA [6].
Kyle Hundman, Valentino Constantinou, Christopher Laporte, Ian Colwell, and
Tom Soderstrom. 2018. Detecting Spacecraft Anomalies Using LSTMs and
Nonparametric Dynamic Thresholding. In Proceedings of the 24th ACM SIGKDD
International Conference on Knowledge Discovery &#38; Data Mining (KDD ’18).
ACM, New York, NY, USA, 387–395.
	
