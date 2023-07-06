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