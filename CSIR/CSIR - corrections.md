---
tags:
  - csir
---
## abstract
In order to maintain synchronized time across computer networks, Network Time Protocol is essential. However, because of their weaknesses, NTP servers are frequently the target of DDoS assaults, which pose serious threats to the integrity of networks and systems. To solve this problem we conducted an extensive analysis and comparative study of 26,085 responses obtained from 209 stratum 1 and 346 stratum 2 NTP servers with continuous collection of data over a period 18 days, recording in three intervals a day. This study provides valuable insights into the variations in performance and distribution of essential parameters between these two strata. By exploring and understanding these differences, we enhance our understanding of NTP server behavior and strengthen the security measures against potential attacks. Building further on the insights gathered from the comprehensive empirical analysis of the server responses from two strata, we propose a LSTM-based detection model made specifically for detecting Distributed Denial of Service (DDoS) attacks against NTP. This can give organizations the capacity to defend against NTP DDoS attacks successfully and uphold the integrity and dependability of their network systems when combined with the comparative analysis's insights. The suggested deep learning model trained and tested on the CICDDoS2019 public dataset provided by the Canadian Institute Cybersecurity shows perfect classification results for a variety of test sets. 

## ntp application industries
NTP is widely used across many different industries. NTP is essential for synchronising clocks and guaranteeing precise timekeeping across networks and systems in the IT industry. NTP is frequently utilised in the telecommunications industry for call routing, network synchronisation, and invoicing procedures. For trading activity and transaction timestamps, financial services rely on NTP's accurate timekeeping. NTP is used by institutions and laboratories engaged in scientific research to synchronise timing for experiments and data analysis. NTP is used by broadcasting and media firms to precisely schedule programmes and uphold precise broadcast timing. NTP is also used by transportation systems to maintain synchronised timing, enabling effective scheduling and coordination between diverse modes of transportation. These sectors gain a lot from NTP's capacity to deliver accurate and synchronised timekeeping, enabling seamless operations and connectivity.

## tools used
- beautiful soup for obtaining the list of NTP servers
- ntplib for sending and receiving requests from NTP servers
- pandas for handling the datasets
- scikit-learn for data preprocesing and model evaluation
- tensorflow for constructing the deep learning model 

In order to facilitate the comparative analysis and the creation of a deep learning model, numerous potent technologies were used in this project. These tools were crucial to the project's success at different phases, from locating the list of NTP servers to preprocessing and analysing the datasets to building and testing the deep learning model. By leveraging the capabilities of these tools, this project was able to achieve its goals effectively and pave the way for insightful findings and practical implications.

1. Beautiful Soup, a popular Python library used for web scraping and parsing HTML. In this project, Beautiful Soup was employed to obtain the list of NTP servers by scraping the source websites and retrieve the required tags.

2. ntplib is a Python library that allows sending and receiving NTP requests to NTP servers. It provides functionalities to retrieve time information from NTP servers, which is essential for the comparative study between stratum 1 and stratum 2 servers. ntplib can be used to query different NTP servers and retrieve time data for analysis.

3. pandas is a powerful data manipulation and analysis library in Python. It offers flexible data structures and data analysis tools, making it suitable for handling datasets in this project. pandas was used to load, manipulate, and preprocess the collected data from the NTP servers, perform data cleaning, and organize the data for further analysis.
  
4. scikit-learn is a widely used machine learning library in Python. It provides a range of tools for data preprocessing, feature extraction, model selection, and evaluation. In this project, scikit-learn was utilized for data preprocessing tasks such as scaling or normalizing the features extracted from the NTP server data, and for evaluating the performance of different machine learning models.

5. TensorFlow is a popular open-source deep learning framework. It offers a comprehensive ecosystem for building and training deep learning models. TensorFlow was used to construct the neural network architecture, define the layers, and train the model using the preprocessed NTP traffic data.

## source website
“WebHome < Main < Network Time Foundation’s NTP Support Wiki.” _WebHome < Main < Network Time Foundation’s NTP Support Wiki_, support.ntp.org.

The particular web-source is chosen due to its legitimacy as it is provided by the website of the NTP management organisation. This makes sure that the data obtained from this source is trustworthy and current, giving the project a complete and accurate list of NTP servers. Relying on the official NTP governing organisation gives the data gathered more credibility and reliability.

## why using only correlation for feature selection
Thus, out of 87 features provided in the dataset, 22 features are selected for the model. These features are chosen based on a comprehensive Pearson's correlation analysis on the dataset. We performed other known feature selection techniques as well, such as ANOVA Test and Chi-Square Test on the numerical and categorical variables respectively, but they could not to provide features that have high collinearity with the target label "Attack". The features provided by the latter techniques failed to perform well on the initial frame and thus were not selected for training the LSTM model.

## connective paragraph between analysis and model results
The results of the comparative study between stratum 1 and stratum 2 NTP server responses provided valuable insights into their respective strengths and weaknesses. Analyzing the distribution of the collected responses over an 18-day period for various parameters of the NTP header information shed light on key characteristics and behaviors of these server types. This understanding of the different strata served as a foundation for identifying parameters that are crucial in mitigating NTP amplification attacks. Building upon this knowledge, the evaluation of the performance of our LSTM-based NTP DDoS attack detection model over a separate dataset further reinforced the significance of targeted fields. The following section discusses the model's results showcased its ability to effectively detect and mitigate NTP-based DDoS attacks, validating the importance of the parameter selection derived from the comparative study. By linking the findings of the comparative study to the evaluation of our detection model, we not only gained a comprehensive understanding of stratum differences but also developed a robust solution for NTP DDoS attack detection, enhancing overall network security.

## comparison with the GRU model
- Assis, Marcos VO, et al. "A GRU deep learning system against attacks in software defined networks." _Journal of Network and Computer Applications_ 177 (2021): 102942.
	- model
		- GRU 32 units
		- dropout 0.5
		- dense 10
		- output node 1 unit
	- used 83 features
	- did not handle class imbalance
	- test result 99.6
- our approach
	- model
		- LSTM 128 units
		- LSTM 64 units
		- dense 128 units
		- dense 64 units
		- dropout 0.3
		- dense 32 units
		- output node 1 unit
	- used 22 features
	- handled class imbalance using undersampling and SMOTE
	- test result 100%

The comparison between our implemented model for NTP DDoS attack detection and the model proposed in the paper on the same dataset reveals some notable differences. The model, presented in the study [], utilized a GRU deep learning system with 32 units, a dropout rate of 0.5, and a dense layer with 10 units. It incorporated a total of 83 features and did not address class imbalance. The test result of this model for "benign" class was reported to be 99.6%. In contrast, our approach employed an LSTM-based model with 128 and 64 units, multiple dense layers, and a dropout rate of 0.3. We used a reduced set of 22 features and implemented techniques to handle class imbalance, including undersampling and SMOTE. Notably, our model achieved a perfect test result of 100% for both the classes. 

While both models showcased strong performance, several distinctions are worth highlighting. Our model utilized a more complex architecture with multiple LSTM layers and larger units, which might have contributed to its higher accuracy. Additionally, our approach paid specific attention to handling class imbalance, which could have further improved the model's performance in detecting NTP DDoS attacks. In contrast, the first model did not address class imbalance, which may have affected its results. Another factor which can address the difference in classification capabilities would be the use of leaky_relu activation function in our Fully Connected Dense layers whereas the particular specification is not mentioned in the paper. Use of this activation function complements the strength of LSTM model in capturing long-term temporal dependencies and mitigates any source of vanishing gradient problem. These differences in feature selection, model architecture, and handling of class imbalance likely played a role in the divergent outcomes between the two models. Our model's ability to achieve perfect accuracy on the test dataset indicates its robustness and effectiveness in accurately identifying NTP DDoS attacks. 