# objective
- BLSTM-DT-XG, a model to detect Botnet attacks in IoT network traffic. this model is divided into two segments - 
	- hybrid BLSTM-decision tree segment, which identifies whether an instance of captured network traffic is an instance of IoT botnet attack or not
	- xg boost segment, which classifies the identified attack instance into various subclasses of attacks, i.e., "DDoS", "DoS", "reconnaissance" and "theft".
- the study uses NF-BoT-IOT, the Netflow version of the UNSW BoT-IoT dataset containing IoT traffic data for instances of botnet attacks with specific subclass of the attack mentioned
- unique features of the study: the study focuses not only on accurate detection of attacks among the vast amount of network traffic collected, but also on precise identification of the type of Botnet attack deployed and observed. The study also emphasizes on a reduced dimensionality of dataset required to ensure quick analysis of network traffic, while maintaining the same level of performance in terms of accuracy. 
- feature selection: we identified important and influential features using kendall feature selection test, where the test was performed separately for the two segments of the classification model. 

# feature selection
## all features
- list of all the features provided in the dataset
	- IPV4_SRC_ADDR
	- IPV4_DST_ADDR
	- L4_SRC_PORT
	- L4_DST_PORT
	- PROTOCOL
	- TCP_FLAGS
	- L7_PROTO
	- IN_BYTES
	- OUT_BYTES
	- IN_PKTS
	- OUT_PKTS
	- FLOW_DURATION_MILLISECONDS
## reason for feature selection
