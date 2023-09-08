---
tags:
  - rough
---
The main contributions of this article are as follows.  
1) A single hidden-layered LAE is proposed for feature dimensionality reduction. This method reduces the dimensionality of large-scale IoT network traffic data and produces a low-dimensional latent-space feature rep resentation at the hidden layer without loosing useful intrinsic network information. 

2) A deep BLSTM is proposed for network traffic classifi cation. This method analyzes the long-term interrelated changes in low-dimensional feature set produced by LAE to distinguish botnet attack traffic from benign traffic in IoT networks.

3) Extensive experiments are performed with the Bot-IoT data set to validate the effectiveness of LAE-BLSTM in binary and multiclass classification scenarios.  

4) The performance of state-of-the-art optimisation algorithms was investigated and compared to ensure effi cient feature dimensionality reduction and botnet attack detection in IoT networks.  

given name to our framework as BiLSTM-DT-XG  

**Unique features**: Compressing the given features and identifying the critical factor is the major aim of our study. In this, we propose a cascading model for classification and detecting the bot attacks with multi-class representation. The model is experimented on popular bot datasets. We also compare our work with the other popular network models. The dynamic recurrent feature of the CFBPNN model with forwarding and backward connections helps in reconnecting several layers of networks and tracing the impact of the variable in each layer. 

**Factor analysis**: We analyze the most critical factors among the given variables and retrieve the best sub-set; we use a co-relation-based subset evaluation technique resulting in the seven best features. Such feature optimization is not available in the existing literature.  

**Risk factor analysis**: We use time series-based techniques to develop prediction models. We implement Nonlinear Auto-Regressive eXogenous (NARX) model to find the impact of the evaluated subset on the target variable and trace the risk factors with a time gap.  
  
**Performance**: Our method has established a relationship with the raw data using multiple levels of abstraction. We have identified the seven best features among 126 given input and target values and analyzed the critical factors affecting the attack classes. This model is useful for developing a prevention technique using the co-related feature set.

---
The increasing reliance on computer networks necessitates the need for synchronized timekeeping, which is achieved through the Network Time Protocol (NTP). However, NTP servers have become frequent targets of Distributed Denial of Service (DDoS) attacks, posing significant threats to network and system integrity. To address this problem, an extensive analysis and comparative study of 26,085 responses from 209 stratum 1 and 346 stratum 2 NTP servers were conducted over an 18-day period, with data collected at three intervals each day.

The study aimed to provide valuable insights into performance variations and distribution of key parameters between the two strata. By understanding these differences, a better understanding of NTP server behavior could be achieved, leading to stronger security measures against potential attacks. Additionally, the study proposed an LSTM-based detection model designed specifically for identifying DDoS attacks against NTP servers.

Drawing on the comprehensive empirical analysis of server responses from both strata, the proposed detection model offers organizations the capacity to successfully defend against NTP DDoS attacks. By combining the insights gained from the comparative analysis with the capabilities of the LSTM model, the integrity and dependability of network systems can be upheld effectively.

To validate the efficacy of the proposed model, it was trained and tested on the CICDDoS2019 public dataset provided by the Canadian Institute of Cybersecurity. The model exhibited perfect classification results across various test sets, demonstrating its high accuracy and reliability.

The findings and contributions of this research project provide a substantial advancement in the field of NTP server security. The comparative analysis sheds light on the performance variations and distribution patterns of NTP servers, enabling network administrators to make informed decisions and implement tailored security measures. Moreover, the LSTM-based detection model empowers organizations to proactively identify and mitigate potential DDoS attacks on NTP servers, thereby safeguarding the overall network infrastructure.

The outcomes of this research project have significant implications for improving the security and resilience of computer networks and systems. By effectively addressing the vulnerabilities associated with NTP servers, organizations can ensure uninterrupted network synchronization, maintain data integrity, and enhance overall cybersecurity posture.

---
- leap
	- all zero
- version
	- nist uses 3
	- rest use 2
- stratum
	- all are categorized as stratum 1 except for NPL UK
- precision
	- nist has highest precision = -29
	- ptb = -25
	- npl uk = -20
	- npl = -18
- poll
	- npl uk = 0
	- npl = 3
	- ptb = 3
	- nist = 13
- rootdelay
- delay
- rootdisp
- reftime
	- npl has lowest
	- nist has higher
	- npl uk has highest

When several prominent Stratum 1 NTP servers from around the world are compared, we can analyse their differences in their functionalities and their infrastructure in a comprehensive fashion. The servers from NIST, NPL India, NPL UK and PTB Germany compared in this study