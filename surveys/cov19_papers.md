# 调研：关于流感预测

## 数据

+ [CDC关于2017-18流感季节预测比赛的数据与官方指导文件](https://predict.cdc.gov/post/59973fe26f7559750d84a843)

+ [CDC上关于流感预测的方法介绍](https://www.cdc.gov/flu/weekly/flusight/index.html)

+ [学术网站Aminer整理的COVID19数据、信息、知识](https://aminer.cn/data-covid19/?lang=zh)

+ [COVID19的相关知识图谱](https://covid-19.aminer.cn/kg/?lang=zh)

+ [COVID-19 Data Repository by the Center for Systems Science and Engineering (CSSE) at Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19)

+ [丁香园](http://www.dxy.cn/)

+ [WHO](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports/)

+ [Statistical reports of COVID-19 cases and mortality rate of Hungary](https://www.worldometers.info/coronavirus/country/hungary/)

+ [Novel Coronavirus (COVID-19) Cases](https://github.com/CSSEGISandData/COVID-19)

+ [COVID-19 Lockdown dates by country](https://www.kaggle.com/jcyzag/covid19-lockdown-dates-by-country)

+ [Hannah Ritchie](https://ourworldindata.org/coronavirus-source-data)

+ [Covid-19 in India](https://www.kaggle.com/sudalairajkumar/covid19-in-india)



## 论文

### SURVEY

- Artificial Intelligence Against Covid-19: An Early Review, IZA Discussion Paper. cite: 22

- Role of intelligent computing in COVID-19 prognosis: A state-of-the-art review，Chaos, Solitons & Fractals. cite: 3

- Applications of machine learning and artificial intelligence for Covid-19 (SARS-CoV-2) pandemic: A review，Chaos, Solitons & Fractals. cite: 3

- Forecasting Models for Coronavirus (COVID-19): A Survey of the State-of-the-Art, teahrXiv. cite: 2

- Automated Detection and Forecasting of COVID-19 using Deep Learning Techniques: A Review，arXiv. cite: 1

- Deep learning methods for forecasting COVID-19 time-Series data: A Comparative study, Chaos, Solitons & Fractals. cite: 0

- Review of Big Data Analytics, Artificial Intelligence and Nature-Inspired Computing Models towards Accurate Detection of COVID-19 Pandemic Cases and Contact Tracing, International Journal of Environmental Research and Public Health. cite: 0

- COVID-19 Open Source Data Sets: A Comprehensive Survey, medRxiv. cite: 0

### paper

做疫情预测的工作主要有三大类方法：

1. 基于经典的传染病模型的方法，或基于这些模型进行改动，此类方法考虑了传染病的多种因素，例如R0、人口流动等。经典传染病模型包括：sub-epidemic wave model，extended susceptible-infected-removed model(eSIR)， Susceptible-Infectious-Recovered-Dead model(SIDR), SEIRD model(susceptible individuals, asymptomatic infected, symptomatic infected, recovered, and deceased)
2. 经典的时间序列方法、机器学习方法或变体，包括：logistic growth model，ARIMA，Wavelet-based model等
3. 基于循环神经网络等方法，输入网路的数据为时间序列，包括：LSTM, GRU, RNN 及其变种，如stacked-RNN(LSTM/GRU), multi-layer RNN(LSTM/GRU)
4. 基于外部知识/信息的方法，外部信息包括：社交网络信息，搜索引擎指数如baidu search index，地区气候信息，空间信息（某地区距离疫情震中的距离等），智能表中的人体健康数据等。此类方法结合了外部信息，能够更精确的刻画疫情的发展态势，且在官方数字滞后的情况下，还能做出比较准确的预测。此类信息还应用了基于RNN等结构，提取时间序列的动态。部分论文提出将深度学习方法与传统传染病模型结合，刻画疫情传播态势。

#### Traditional models (ARIMA, logistic regression, epidemic model and so on)

本节中的论文大致按照 “基于传染病模型的方法” -> "基于传统时间序列与机器学习方法" 的顺序排列。由于相关工作中包含了大量在预印本网站上发表的论文，因此将正式发表与未正式发表的论文分开了。

##### peer-reviewed papers

Real-time forecasts of the COVID-19 epidemic in China from February 5th to February 24th, 2020, Infectious Disease Modelling
+ 数据：daily reported cumulative confirmed cases for the 2019-nCoV outbreak for each Chinese province from the National Health Commission of China.
+ 模型：generalized logistic growth model, the Richards growth model, and a sub-epidemic wave model.
+ cite: 182

Short-term Forecasts of the COVID-19 Epidemic in Guangdong and Zhejiang, China: February 13–23, 2020，J Clin Med
+ 数据：the cumulative cases for 34 provinces, including municipalities, autonomous regions, and special administrative regions， reported case data each day at 12 pm (GMT-5) from the initial date of reporting, 22 January 2020, to 13 February 2020.
+ 模型：**The generalized logistic growth model (GLM)** and the **Richards model extend the simple logistic growth model** with an additional scaling parameter， **sub-epidemic model**
+ cite: 61

Extended SIR Prediction of the Epidemics Trend of COVID-19 in Italy and Compared With Hunan, China，Frontiers in medicine
+ 数据：publicly available dataset of COVID-19 provided by the Johns Hopkins University. This dataset includes many countries' daily count of confirmed cases, recovered cases, and deaths. As time-series data, it is available from 22 January 2020.
+ 模型：An **infectious disease dynamic extended susceptible-infected-removed (eSIR) model**， The basic reproductive number was estimated using **Markov Chain Monte Carlo methods**
+ cite: 24

Data-based analysis, modelling and forecasting of the COVID-19 outbreak,  PloS one
+ 数据：publicly available data from the 11th of January 2020 to the 10th of February 2020.
+ 模型：Susceptible-Infectious-Recovered-Dead (SIDR) model
+ cite: 148

A fractional-order model for the novel coronavirus (COVID-19) outbreak，Nonlinear Dynamics，Springer.
+ 数据：Italy’s data from February 24 to April 7, reported by WHO. We consider the number of the infected (I) and deceased (D) individuals
+ 模型：**fractional-order** susceptible individuals, asymptomatic infected, symptomatic infected, recovered, and deceased **(SEIRD)** model.
+ cite: 3

Reconstructing and forecasting the COVID-19 epidemic in the United States using a 5-parameter logistic growth model, Global health research and policy, pp. 252020.
+ 数据：mulative cases of COVID-19 in the U.S. from January 22 to April 6, 2020
+ 模型：5-parameter logistic growth model
+ cite: 2

Estimation of COVID-19 prevalence in Italy, Spain, and France, Science of The Total Environment, Volume 729, 10 August 2020, 138817, ELSEVIER
+ 数据：The prevalence data of COVID-19 was taken from the 
+ 模型：ARIMA
+ cite: 43

Real-time forecasts and risk assessment of novel coronavirus (COVID-19) cases: A data-driven analysis, Chaos, Solitons & Fractals, Volume 135, June 2020, 109850, ELSEVIER
+ 数据：the daily figures of confirmed cases for five different countries, namely Canada, France, India, South Korea, and the UK. The datasets are retrieved by the Global Change Data Lab1).
+ 模型：hybrid ARIMA-WBF(Wavelet-based forecasting model) model
+ cite: 40


COVID-19 virus outbreak forecasting of registered and recovered cases after sixty day lockdown in Italy: A data driven model approach，Journal of Microbiology, Immunology and Infection.
+ 数据：COVID-19 infected patient data has extracted from the Italian Health Ministry website includes registered and recovered cases from mid February to end March.
+ 模型：seasonal ARIMA
+ cite: 34

Prediction of Number of Cases of 2019 Novel Coronavirus (COVID-19) Using Social Media Search Index，IJERPH
+ 数据：Baidu Search Index in Social Media，Number of New Suspected Infection Cases
+ 模型：一个函数模型，自变量为Baidu Search Index，因变量为确诊数量，该函数的参数通过Subset selection，Forward selection，Ridge regression，Lasso regression和Elastic net来估计
+ cite: 16

Time series modelling to forecast the confirmed and recovered cases of COVID-19, Travel Medicine and Infectious Disease, ELSEVIER
+ 数据： the number of confirmed and recovered COVID-19 cases in the world from 21-Apr-2020 up to 30-Apr-2020,
+ 模型：**Autoregressive time series models** based on **two-piece scale mixture normal distributions**, called TP–SMN–AR models(includes the symmetric Gaussian and asymmetric heavy-tailed non-Gaussian autoregressive time series models. )
+ cite: 10

Prediction of the COVID-19 Pandemic for the Top 15 Affected Countries: Advanced Autoregressive Integrated Moving Average (ARIMA) Model, JMIR public health and surveillance
+ 数据：We have collected the case data for each day at given stipulated times, from January 21, 2020, to April 24, 2020. 
+ 模型：ARIMA
+ cite: 10

ALGORITHM OF HYBRID GMDH-NETWORK CONSTRUCTION FOR TIME SERIES FORECAST，Electronics and Control Systems
+ 数据： the data of the COVID-19 pandemic, collected by Johns Hopkins University.
+ 模型：Hybridization is achieved through the use of various neurons: **classical, nonlinearAdaline, R-neuron, W-neuron, Wavelet-neuron**.
+ cite: 0



##### preprint paper (not peer-reviewed)

Prediction of COVID-19 Spreading Profiles in South Korea, Italy and Iran by Data-Driven Coding, medRxiv, 2020.
+ 数据：the  number  of  infected  cases,  thecumulative  number  of  infected  cases,  the  number  of  recovered  cases,  and  death  tolls,  forindividual cities and regions in South Korea, Italy and Mazandran, from February 19, 2020,to March 6, 2020. 
+ 模型：the set of parameters of the augmented Susceptible-Exposed-Infected-Removed **(SEIR)** model
+ cite: 3


Evaluation of the incidence of COVID-19 and of the efficacy of contention measures in Spain: a data-driven approach, medRxiv, 2020.
+ 数据：we  feed  the  model  with  the  available  data  as  of  February  28th,  2020. We consider that each province (there are 52 in Spain, see appendix B) is represented by a subpopulation.
+ 模型：Stochastic  SEIR-meta population  models  
+ cite: 1

Epidemic analysis of COVID-19 in China by dynamical modeling, MedRxiv，2020
+ 数据：01/20到02/09的NHC的公开数据，我们预测了5个不同区域的流行高峰和可能的结束时间。
+ 模型：generalized SEIR model 
+ cite: 154


 Explicit Modeling of 2019-nCoV Epidemic Trend based on Mobile Phone Data in Mainland China， medRxiv, 2020
+ 数据：daily outbreak data of 2019-nCoV Pneumonia in 334 prefecture-level cities in mainland China from January 11to February 2,2020. China Unicom mobile phone database is used to obtainthe inter-city  human  mobility.Household Registered Population at 2017 year-end derived from census data wasused to approximate  the number of local residentsineach city during 2020 Spring Festival
+ 模型：the proposed modification of SIR model
+ cite: 5

AutoSEIR: Accurate Forecasting from Real-time Epidemic Data Using Machine Learning, medRxiv, 2020
+ 数据：各个地区的疫情数据，以及多个地区的封锁日期信息。
+ 模型： In this paper we propose a novel approach to epidemiological parameter fitting and epidemic forecasting, based on an **extended version of the SEIR compartmental model** and on **an auto-differentiation technique for partially observable ODEs** (Ordinary Differential Equations). 
+ cite: 0

An epidemiological forecast model and software assessing interventions on COVID-19 epidemic in China [R software], medRxiv, 2020
+ 数据：the COVID-19 data collected from the public website DXY.cn
+ 模型：Markov SIR infectious disease process
+ cite: 18

Covid-19 spread: Reproduction of data and prediction using a SIR model on Euclidean network， arXiv, 2020
+ 数据：the COVID-19 data，the distance from the epicenter.
+ 模型： Susceptible-Infected-Removed (SIR) model，Euclidean network
+ cite: 16

Forecasting the Worldwide Spread of COVID-19 based on Logistic Model and SEIR Model，medRxiv, 2020
+ 数据：Coronavirus COVID-19 Global Cases published by the Center for Systems Science and Engineering (CSSE) of Johns Hopkins University
+ 模型：Logistic Model and SEIR Model
+ cite: 9


Analysis and Prediction of COVID-19 Pandemic in Pakistan using Time-dependent SIR Model，arXiv, 2020
+ 数据：The data used in this paper is taken from the John Hopkins University dashboard
+ 模型：The **time-dependent Susceptible-Infected-Recovered (SIR)** model
+ cite: 5


A data driven analysis and forecast of an SEIARD epidemic model for COVID-19 in Mexico, arXiv, 2020
+ 数据：COVID-19 data in Mexico(infected, asymptomatic, recovered)
+ 模型：**SEIARD mathematical model**(susceptible (S(t)), exposed (E(t)), infected (I(t)), asymptomatic (A(t)), recovered (R(t)) and dead (D(t)).)
+ cite: 5


Simple model for Covid-19 epidemics - back-casting in China and forecasting in the US, medRxiv, 2020
+ 数据：mulative cases of COVID-19 in the U.S. from January 22 to April 6, 2020
+ 模型：Logistic Model
+ cite: 0


Application of ARIMA and Holt-Winters forecasting model to predict the spreading of COVID-19 for India and its states， medRxiv
+ 数据： the publicly available dataset from Kaggle as a perspective to India and its five states such as Odisha, Delhi, Maharashtra, Andhra Pradesh and West Bengal.
+ 模型： In this paper, the **ARIMA** (Auto regressive integrated moving average) and **Holt-Winters time series exponential smoothing** are used to develop an efficient 20- days ahead short-term forecast model to predict the effect of COVID-19 epidemic.
+ cite: 0


Data-driven Simulation and Optimization for Covid-19 Exit Strategies， arXiv, 2020
+ 数据
+ 模型： We have therefore built a pandemic simulation and forecasting toolkit that combines a **deep learning estimation of the epidemiological parameters** of the disease in order to predict the cases and deaths, and a **genetic algorithm** component searching for optimal trade-offs/policies between constraints and objectives set by decision-makers. 
+ cite: 1


Kalman Filter Based Short Term Prediction Model for COVID-19 Spread， medRxiv, 2020
+ 数据：this article is written after various studies and analysis on the latest data on COVID-19 spread, which also includes the demographic and environmental factors. 
+ 模型：After gathering data from various resources, all data are integrated and passed into different **Machine Learning Models** to check the fit. **Ensemble Learning Technique,Random Forest**, gives a good evaluation score on the test data.
+ cite: 1


Spatiotemporal Dynamics, Nowcasting and Forecasting of COVID-19 in the United States，arXiv，2020
+ 数据：data from the reported confirmed COVID-19 infections and deaths at the county level，Health Department Website in each state or region, the New York Times (NYT, 2020), the COVID-19 Data Repository by the Center for Systems Science and Engineering at Johns Hopkins University (CSSE, 2020), and the COVID Tracking Project (Atlantic, 2020).
+ 模型：a class of nonparametric **space-time models**，we consider the exponential families of distributions
+ cite: 4



-----

#### Deep learning and other methods

本章大致按照 “融合模型（深度学习与传统传染病模型/时间序列模型的结合  或  时间序列信息与其他信息的结合，其他信息包括：气候信息、社交媒体信息、人体健康数据等）” -> “仅利用时间序列信息的深度学习模型” 来排列。 

##### peer-reviewed papers

Forecasting Brazilian and American COVID-19 cases based on artificial intelligence coupled with climatic exogenous variables， Chaos, Solitons & Fractals，Volume 139, October 2020, 110027， ELSEVIER
+ 数据：收集的数据集涉及到2020年4月28日在巴西和美国五个州发生的COVID-19累积案例。对于巴西语境，该数据集是从API（应用程序接口）[37]中收集的，该API 检索来自巴西所有27个州卫生局的有关COVID-19病例的每日信息。美国而言，该数据集是从约翰·霍普金斯大学系统科学与工程中心（CSSE）提供的Github上的“ COVID-19数据存储库”中收集的[38]。
+ 模型：此外，本文还结合了气候外源输入，以多日预报策略评估了AI模型。In this paper, **Bayesian regression neural network, cubist regression, k-nearest neighbors, quantile random forest, and support vector regression**, are used stand-alone, and coupled with the recent **pre-processing variational mode decomposition (VMD)** employed to decompose the time series into several intrinsic mode functions.
+ cite: 1

Time Series Analysis and Forecast of the COVID-19 Pandemic in India using Genetic Programming， Chaos, Solitons & Fractals Volume 138, September 2020, 109945。ELSEVIER
+ 数据：印度的COVID19数据
+ 模型： it has been found that the proposed **GEP(Genetic Evolutionary Programming )-based models** use simple linkage functions and are highly reliable for time series prediction of COVID-19 cases in India.
+ cite: 7

Modified SEIR and AI prediction of the epidemics trend of COVID-19 in China under public health interventions, Journal of Thoracic Dosease
+ 数据：Migration index based on the daily number of inbound and outbound events by rail, air and road traffic，most updated COVID-19 epidemiological data， The 2003 SARS epidemic data between April and June 2003 across the whole of China retrieved from an archived news-site
+ 模型：Modified SEIR model，artificial intelligence (AI) approach, trained on the 2003 SARS data (LSTM)
+ cite: 199

Predicting COVID-19 in China Using Hybrid AI Model， IEEE Transactions on Cybernetics，IEEE
+ 数据：most of the data mainly come from the national and provincial health commissions and include the numbers of people who are infected, suspected, cured, and have died. data for NLP are obtained from dxy.com [36], social media, and news media.
+ 模型：**improved susceptible-infected (ISI) model** ，the **natural language processing (NLP) module** and the **long short-term memory (LSTM) network** are embedded into the ISI model to build the hybrid AI model for COVID-19 prediction.
+ cite: 7

Learning from Large-Scale Wearable Device Data for Predicting Epidemics Trend of COVID-19，Discrete Dynamics in Nature and Society，Hindawi
+ 数据：日常测量包括RHR，活动和睡眠时间，这是生理异常检测的基础。
+ 模型：we propose a framework, which is based on the **heart rate and sleep data collected from wearable devices**, to predict the epidemic trend of COVID-19 in different countries and cities. In addition to a physiological anomaly detection algorithm defined based on data from wearable devices, **an online neural network** prediction modelling methodology combining both detected physiological anomaly rate and historical COVID-19 infection rate is explored.
+ cite: 4


COVID-19 Pandemic Prediction for Hungary; A Hybrid Machine Learning Approach， Mathematics, MDPI
+ 数据：The actual dataset includes the daily cases and the number of deaths from 4 March to 28 April. 
+ 模型： The hybrid machine learning methods of **adaptive network-based fuzzy inference system (ANFIS)** and **multi-layered perceptron-imperialist competitive algorithm (MLP-ICA)** are proposed to predict time series of infected individuals and mortality rate. 
+ cite: 4

Forecasting the prevalence of COVID-19 outbreak in Egypt using nonlinear autoregressive artificial neural networks, Process Safety and Environmental Protection, ELSEVIER
+ 数据：埃及卫生和人口部报告的关于COVID-19确诊病例的官方数据被用于本研究，研究时间为2020年3月1日至5月10日
+ 模型：ARIMA，NARANN（非线性自回归人工神经网络）
+ cite: 2


Multiple Ensemble Neural Network Models with Fuzzy Response Aggregation for Predicting COVID-19 Time Series: The Case of Mexico, Healthcare, dblp, 2020
+ 数据：我们有一个来自COVID-19确诊病例和死亡病例的数据集，其中包括墨西哥的12个州和该国的总数据
+ 模型：a multiple **ensemble neural network** model with fuzzy response aggregation for the COVID-19 time series is presented. Ensemble neural networks are composed of a set of modules, which are used to produce several predictions under different conditions. The modules are simple neural networks. **Fuzzy logic** is then used to aggregate the responses of several predictor modules
+ cite: 1


Predicting the growth and trend of COVID-19 pandemic using **machine learning and cloud computing**, Internet of Things, Elsevier
+ 数据：Hannah Ritchie, https：//ourworldindata.org/coronavirus-source-data。
+ 模型：We show that using iterative weighting for fitting Generalized Inverse Weibull distribution, a better fit can be obtained to develop a prediction framework. 
+ cite: 15


COVID-19 Outbreak Prediction with Machine Learning, SSRN
+ 数据： Data were collected from https://www.worldometers.info/coronavirus/country for five countries, including Italy, Germany, Iran, USA, and China on total cases over 30 days.
+ 模型：Among a wide range of machine learning models investigated, two models showed promising results (i.e., **multi-layered perceptron, MLP, and adaptive network-based fuzzy inference system, ANFIS**).Paper further suggests that real novelty in outbreak prediction can be realized through integrating machine learning and SEIR models.
+ cite: 11


A Methodological Approach for Predicting COVID-19 Epidemic Using EEMD-ANN Hybrid Model，Internet of Things，Elsevier, 2020
+ 数据：The cumulative global data of daily level information by country were retrieved from the Center for Systems Science and Engineering (CSSE) at the Johns Hopkins University GitHub repository (https://github.com/CSSEGISandData/COVID-19) accessed on 19/05/2020. This study focuses only on the number of global cumulative confirm cases of COVID-19, the number of cumulative death and recover cases from the period January 22, 2020, to May 18, 2020,
+ 模型： The primary objective of this study is to propose **a hybrid model that incorporates ensemble empirical mode decomposition (EEMD) and artificial neural network (ANN) for predicting the COVID-19 epidemic**. A real-time COVID-19 time series data has been used on the window periods January 22, 2020, to May 18, 2020. The time-series data first decomposed using EEMD to produce sub-signals and make original data denoised, and ANN architecture has built to train the denoised data.
+ cite: 0


Partial derivative Nonlinear Global Pandemic Machine Learning prediction of COVID 19，Chaos, Solitons & Fractals，Volume 139, October 2020, 110056，ELSEVIER
+ 数据：benchmark dataset Indian COVID-19 dataset obtained from https://www.kaggle.com/sudalairajkumar/covid19-in-india. 
+ 模型：we propose **a partial derivative regression and nonlinear machine learning (PDR-NML)** method for global pandemic prediction of COVID-19. We used a Progressive Partial Derivative Linear Regression model to search for the best parameters in the dataset in a computationally efficient manner. Next, a Nonlinear Global Pandemic Machine Learning model was applied to the normalized features for making accurate predictions. 
+ cite: 1



Prediction and analysis of COVID-19 positive cases using deep learning models: A descriptive case study of India，Chaos, Solitons & Fractals, Volume 139, October 2020, 110017，ELSEVIER
+ 数据： Ministry of Health and Family Welfare (Government of India) [9]. 
+ 模型：Recurrent neural network (RNN) based long-short term memory (LSTM) variants such as **Deep LSTM, Convolutional LSTM and Bi-directional LSTM** are applied on Indian dataset to predict the number of positive cases. 
+ cite: 3



Composite Monte Carlo decision making under high uncertainty of novel coronavirus epidemic using hybridized deep learning and fuzzy rule induction, Applied Soft Computing, Volume 93, August 2020, 106282, ELSEVIER
+ 数据：The data come from mainly two sources: one source is known to be deterministic in nature which is harvested from CDCP in the form of time-series starting from 25 Jan 2020 to 25 Feb 2020.
+ 模型：  **Composite Monte-Carlo (CMC) simulation** is a forecasting method which extrapolates available data which are broken down from multiple correlated/casual micro-data sources into many possible future outcomes by drawing random samples from some probability distributions. In this paper, a case study of using **CMC that is enhanced by deep learning network and fuzzy rule induction** for gaining better stochastic insights about the epidemic development is experimented. Instead of applying simplistic and uniform assumptions for a MC which is a common practice, a deep learning-based CMC is used in conjunction of fuzzy rule induction techniques. 
+ cite: 25


Statistical Explorations and Univariate Timeseries Analysis on COVID-19 Datasets to Understand the Trend of Disease Spreading and Death，Sensors Volume 20  Issue 11, MDPI
+ 数据： we used datasets from 1 January 2020, to 22 April 2020. 
+ 模型：vanilla, stacked, and bidirectional LSTM models，  multilayer LSTM models
+ cite: 0



Covid-19 Predictions Using a Gauss Model, Based on Data from April 2，  Physics  Volume 2  Issue 2， MDPI
+ 数据：多个国家的感染曲线
+ 模型：We study a **Gauss model (GM)**, a map from time to the bell-shaped Gaussian function to model the deaths per day and country, as a simple, analytically tractable model to make predictions on the coronavirus epidemic. **Justified by the sigmoidal nature of a pandemic**, i.e., initial exponential spread to eventual saturation, and an agent-based model，we apply the GM to existing data, as of 2 April 2020, from 25 countries during first corona pandemic wave and study the model’s predictions. 
+ cite: 6


Artificial Neural Network Modeling of Novel Coronavirus (COVID-19) Incidence Rates across the Continental United States,  IJERPH  Volume 17  Issue 12, MDPI
+ 数据：In this study, we compiled a database of 57 candidate variables that may predict county-level cumulative disease incidence as a dependent variable. From January 22 to April 25, 2020, cumulative numbers of confirmed cases of COVID-19 across the continental United States were collected at the county level from USAFacts (usafacts.org) and normalized by populations. The counties (n = 3109) were considered as samples that represent the status of the disease in the US. In this study, socioeconomic (such as household income, income inequalities, and unemployment rate), behavioral (such as smoking), environmental (such as temperature, precipitation, and air pollution), topographic (such as altitude, and terrain slope), and demographic (such as proportions of age groups, race, gender, and access to primary care) factors were prepared at the county level and were used as explanatory variables.
+ 模型：feature selection + ANN
+ cite: 1



Time series forecasting of COVID-19 transmission in Canada using LSTM networks, Chaos, Solitons & Fractals Volume 135, June 2020, 109864, ELSEVIER
+ 数据：The data set also includes number of fatalities and recovered patients by the end of each day. The dataset is available in the time series format with date, month and year so that the temporal components are not neglected. 
+ 模型：Bi-LSTM
+ cite: 22


Modeling and prediction of COVID-19 in Mexico applying mathematical and computational models，Chaos, Solitons & Fractals，Volume 138, September 2020, 109946，ELSEVIER
+ 数据：The data used comes from the "Daily Technical Report" [18] issued by the Mexican Ministry of Health.
+ 模型：**Gompertz and Logistic models**，An **ANN model** with seven neurons in the hidden layer and using a TANSIG function
+ cite: 9




##### preprint paper (not peer-reviewed)

A machine learning methodology for real-time forecasting of the 2019-2020 COVID-19 outbreak using Internet searches, news alerts, and estimates from mechanistic models，arXiv, 2020
+ 数据：(a) official health reports from Chinese Center Disease for Control and Prevention (China CDC), (b) COVID-19-related internet search activity from Baidu, (c) news media activity reported by Media Cloud, and (d) daily forecasts of COVID-19 activity from GLEAM
+ 模型：****Augmented ARGONet，***
+ cite: 14


Examining COVID-19 Forecasting using Spatio-Temporal Graph Neural Networks， arxiv, 2020
+ 数据：the NewYork Times (NYT)COVID-19 dataset1, the Google COVID-19 Aggregated Mobility Research Dataset, and the Google Community Mobility Reports2. The Aggregated Mobility Research Dataset helps us understand the quantity of movement, while the Community Mobility Reports helps us understand the dynamics of various types of movement.
+ 模型：the proposed approach learns from **a single large-scale spatio-temporal graph**, where nodes represent the region-level human mobility, spatial edges represent the human mobility based inter-region connectivity, and temporal edges represent node features through time.
+ cite: 1


Prediction of the COVID-19 Epidemic Trends Based on SEIR and AI Models， medRxiv, 2020
+ 数据：The epidemic data，The urban migration indexThe population density, per capita GDP and other urban data of all provinces in China，the distance from each province to Wuhan，The average temperature of each province
+ 模型： We proposed an **SEIR(Susceptible-Exposed- Infectious-Removed) model** to analyze the epidemic trend in Wuhan and use the **AI model** to analyze the epidemic trend in non-Wuhan areas. 
+ cite: 0


Novel Spatiotemporal Feature Extraction Parallel Deep Neural Network for Forecasting Confirmed Cases of Coronavirus Disease 2019， medRxiv, 2020
+ 数据：Experimental data were collected from Germany, Italy, and Spain regarding six factors: the daily number of newly confirmed cases, deaths, and recovered cases and the accumulated number of confirmed cases, deaths, and recovered cases.
+ 模型： This study proposed a novel **deep neural network framework, COVID-19Net**, which parallelly combines a **convolutional neural network (CNN) and bidirectional gated recurrent units (GRUs)**. Three European countries with severe outbreaks were studied Germany, Italy, and Spain to extract spatiotemporal feature and predict the number of confirmed cases.
+ cite: 0


Hawkes process modeling of COVID-19 with mobility leading indicators and spatial covariates, medRxiv, 2020
+ 数据：Covid-19 daily cases and deaths reported by The New York Times， Google mobility index reports， County-level demographic covariates
+ 模型：**Hawkes process** with **spatio-temporal** covariates for modeling COVID-19 case and death data.
+ cite: 0



COVID-19 Epidemic Analysis using Machine Learning and Deep Learning Algorithms, medRxiv, 2020
+ 数据：The day to day prevalence data of COVID-2019 from January 22, 2020, to April 1, 2020,The dataset consists of daily case reports and daily time series summary tables.
+ 模型：polynomial regression (PR)，SVR，DNN，LSTM
+ cite: 5


An Improved Method for the Fitting and Prediction of the Number of COVID-19 Confirmed Cases Based on LSTM，arXiv 2020 
+ 数据：Novel Coronavirus (COVID-19) Cases：https://github.com/CSSEGISandData/COVID-19， COVID-19 Lockdown dates by country: https://www.kaggle.com/jcyzag/covid19-lockdown-dates-by-country.
+ 模型：LSTM，然后根据standard deviation of last n days来调整预测的结果，以体现地区性的疫情发展趋势的差异性
+ cite: 0


Predicting the epidemic curve of the coronavirus (SARS-CoV-2) disease (COVID-19) using artificial intelligence，medRxiv, 2020
+ 数据：publicly available datasets of World Health Organization and Johns Hopkins University
+ 模型：then have used recurrent neural networks **(RNNs)** with gated recurring units **(Long Short-Term Memory – LSTM units)** to create 2 Prediction Models. Information collected in the first t time-steps were aggregated with a fully connected (dense) neural network layer and a consequent regression output layer to determine the next predicted value.
+ cite: 1


Worldwide and Regional Forecasting of Coronavirus (Covid-19) Spread using a Deep Learning Model, medRxiv, 2020
+ 数据：time series data of daily reports of Chinese Centre for Disease Control and Prevention from 10 January 2020 to 3 April 2020 [4]. The data includes the total number of daily new cases of Covid-19, the total number of deaths and the total number of recoveries in China. (Europe and Middle East, worldwide...)
+ 模型：The proposed deep learning architecture consists of **Long Short Term Memory (LSTM) layer, dropout layer, and fully connected layers** to predict regional and worldwide forecasts. 
+ cite: 0


COVID-19 Pandemic Prediction for Hungary; a Hybrid Machine Learning Approach， medRxiv, 2020
+ 数据：Dataset is related to the statistical reports of COVID-19 cases and mortality rate of Hungary which is available at: https://www.worldometers.info/coronavirus/country/hungary/. Figure
+ 模型：this study proposes a hybrid machine learning approach to predict the COVID-19 and we exemplify its potential using data from Hungary. The hybrid machine learning methods of **adaptive network-based fuzzy inference system (ANFIS)** and **multi-layered perceptron-imperialist competitive algorithm (MLP-ICA)** are used to predict time series of infected individuals and mortality rate.
+ cite: 4



Forecasting Covid-19 dynamics in Brazil: a data driven approach， arXiv, 2020
+ 数据：covid-19 time series
+ 模型：Then, our main approach consists in **an initial clustering of the world regions** for which data is available and where the pandemic is at an advanced stage, based on a set of **manually engineered features** representing a country's response to the early spread of the pandemic. A **Modified Auto-Encoder network** is then trained from these clusters and learns to predict future data for Brazilian states. These predictions are used to estimate important statistics about the disease, such as peaks.
+ cite: 0



Artificial Intelligence Forecasting of Covid-19 in China, arXiv, 2020
+ 数据：the confirmed cases of Covid-19 across China which were collected from January 11 to February 27, 2020 by WHO.
+ 模型：**a modified stacked auto-encoder** for modeling the transmission dynamics of the epidemics. We used the **latent variables in the auto-encoder and clustering algorithms** to group the provinces/cities for investigating the transmission structure.
+ cite: 62
-----







