---
tags:
  - csir
---
## overall progress
- attacks
	- MITM attack
	- Replay attack
	- Delay attack
	- DDoS attack
	- investigate different mitigation techniques
- python script 
	- retrieve time synchronization NTP information from server
	- sync devices to NTP server
	- get a list of all NTP servers
		- find a source
		- use web scraping techniques to extract the list
	- separate the list is terms of Stratum 1 and 2
	- collect NTP information for all the servers

### week 1
- Studied NTP
	- RFC-5905
- attacks
	- DDoS attack
	- investigate different mitigation techniques
- python script 
	- retrieve time synchronization NTP information from server
	- sync devices to NTP server
	- get a list of all NTP servers
		- find a source

### week 2
- attacks
	- MITM attack
	- Replay attack
	- Delay attack
	- investigate different mitigation techniques
- python script 
	- get a list of all NTP servers
		- use web scraping techniques to extract the list
	- separate the list is terms of Stratum 1 and 2
	- collect NTP information for all the servers

### week 3
- troubleshooted the python script for send and receiving NTP requests. 
- streamlined the process of saving to CSV file
- performed statistical analysis on data regarding responses from NTP servers
- cleaned the NTP response data of outliers
- preprocessed the NTP attack dataset
- explored initial models on NTP attack dataset

### week 4
- performed further preprocessing on the NTP attack dataset
- separated data of interest from various attack datasets from the same source
- performed training and testing on several models and finalized an LSTM-based model for classification
- obtained evaluation metrics for the model on various testing sets
- compiled the project report with all the results and included detailed discussions about the methodologies and outcomes involved


Project Progress Schedule (PERT Chart)
1. week 1: understanding NTP and components
2. week 2: working on dataset creation for NTP servers
3. week 3: understanding the dataset for DDoS attacks, experiment with initial models
4. week 4: developing and enhancing the model

---
## week 1: 29/05/2023 - 04/06/2023
### Target For The Week
Study NTP protocol, identify all types of cyber-attacks on NTP, create a web scraping tool to create a database for all active NTP servers.

### Achievements
Studied NTP protocol and its components, examined DDoS attacks on NTP, searched and found a source for list of active NTP servers.

### Future Work Plans
Create a web scraping script for creating a database of NTP servers, gather information from the servers gathered using NTP requests, examine other types of cyber attacks on NTP.

- targets
	- Gain a comprehensive understanding of the Network Time Protocol (NTP) and its underlying principles; explore the architecture, functioning, and synchronization mechanisms employed by NTP; familiarize with NTP's components, including servers, clients, and reference clocks.
	- Conduct in-depth research to identify various cyber-attacks that target NTP infrastructure; investigate different attack vectors, such as amplification attacks, reflection attacks, and protocol exploitation; understand the techniques used in NTP-based Distributed Denial of Service (DDoS) attacks and their impact on network availability and stability.
	- Develop a custom web scraping tool capable of extracting relevant information from online sources; configure the tool to collect data on active NTP servers, including their IP addresses, locations, and other pertinent details; implement robust error handling and data validation mechanisms to ensure accuracy and reliability of the gathered information.
	- Design a database schema suitable for storing the collected NTP server information; set up and populate the database with the scraped data, organizing it in a structured and accessible manner; implement appropriate indexing and query optimization techniques to enhance the database's performance.

- Achievements:
	- Gaining a thorough understanding of the Network Time Protocol (NTP) and its key components, such as the NTP server, client, and reference clocks, to ensure accurate time synchronization across network devices.
	- Recognizing the importance of time synchronization in various systems and networks, including financial transactions, distributed databases, and log file management, to maintain consistency and prevent errors or conflicts.
	- Exploring the impact of Distributed Denial of Service (DDoS) attacks on NTP traffic, such as amplification attacks, which exploit vulnerabilities in NTP servers to flood targeted systems with overwhelming traffic, causing service disruptions or outages.
	- Conducting research and compiling a comprehensive list of active NTP servers worldwide, including public and private servers, to identify reliable time sources for network synchronization purposes, considering factors like location, reliability, and accessibility.

---
## week 2: 05/06/2023 - 11/06/2023
### Target For The Week
Study MITM, Replay and Delay cyber-attacks, investigate different mitigation techniques, create a web scraping script for creating a database of NTP servers, gather information from the servers gathered using NTP requests.

### Achievements
Studied other types of cyber attacks on NTP traffic, created a database for NTP servers, created a script for requesting information from the servers, found some public dataset for dataset for comparison and understanding various fields required.

### Future Work Plans
Collect NTP network traffic, clean and analyse the collected traffic information, start implementing initial models on the data.

targets:
- Study and understand other types of cyber attacks like - MITM attacks, Replay attacks and Delay attacks; understand how they affect NTP and how can they be reduced.
- Create a database for all active NTP servers and other essential information using web-scraping from various sources.
- Maintain a database of NTP information such as: server time, protocol and port used, time offset between system and server, etc. from the collected servers on a regular basis.

achievements:
- Gained comprehensive understanding of Man-In-The-Middle attacks, Replay attacks and Delay attacks; studied their impact and techniques of operation in NTP traffic; identify methods of mitigation.
- Developed custom web-scraping tools to collect essential information on NTP servers from various online sources; ensured the collected data was validated, cleaned, and structured for efficient storage and retrieval.
- Developed a script that can initiate requests to the identified NTP servers, retrieving detailed information about their configuration, synchronization status, and performance metrics; automated the process for running 3 times a day.
- Conducted a search for publicly available datasets related to DDoS attacks on NTP traffic; acquired relevant datasets for comparison and analysis; utilized these datasets to enhance understanding and identify important features required for detection and other forms of analysis.

---
## week 3: 12/06/2023 - 18/06/2023
### Target For The Week
Clean, preprocess and analyse the collected data on responses from NTP servers, explore the DDoS attack dataset, apply initial models on the DDoS dataset and check performance.

### Achievements
Troubleshooted the python script for send and receiving NTP requests, performed statistical analysis on data regarding responses from NTP servers, cleaned the NTP response data of outliers, preprocessed the NTP attack dataset, explored initial models on NTP attack dataset.

### Future Work Plans
Complete NTP stratum level analysis, finalize the DDoS attack detection dataset and deep learning model, obtain performance metrics for the models in various environments.

targets:
- Clean, preprocess, and analyze the collected data on responses from NTP servers and analyze data using descriptive statistics, visualization, and correlation analysis to understand patterns and characteristics.
- Explore the DDoS attack dataset by examining the target variable distribution, identify class imbalance, identify features correlated with attacks, and understand normal/attack traffic characteristics.
- Apply initial models on the DDoS dataset like traditional ML models and evaluate performance using classification metrics to establish baseline and guide model refinement or selection.

achievements:
- Troubleshooted the Python script for sending and receiving NTP requests by identified and resolved errors or bugs in the script responsible for null value being recorded for valid responses.
- Performed statistical analysis on data regarding responses from NTP servers using techniques such as mean, median, standard deviation, and visualization to analyze the collected NTP response data, uncovering insights into distribution and variability.
- Cleaned the NTP response data of outliers using interquartile range and boxplots to remove or handle them, improving data quality for further analysis.
- Prepared the NTP attack dataset for modeling by performing data normalization and feature scaling to ensure the data is in a suitable format for training machine learning models.
- Selected and applied initial machine learning models and assessed their performance for determining a baseline for further model refinement or selection.


---
## week 4: 19/06/2023 - 25/06/2023
### Target For The Week
Finalize the model for classification of NTP DDoS attacks against benign communication records, prepare testing sets with varying distributions, train the model and evaluate the performance of the model with commonly known metric and techniques. 

### Achievements
Performed further preprocessing on the NTP attack dataset, separated data of interest from various attack datasets from the same source, performed training and testing on several models and finalized an LSTM-based model for classification, obtained evaluation metrics for the model on various testing sets, compiled the project report with all the results and included detailed discussions about the methodologies and outcomes involved.

### Future Work Plans
Automate the collection of the NTP server responses on a remote system, collect a more comprehensive dataset for DDoS attacks using packet capturing and port mirroring techniques from an NTP server, train the dataset on a more efficient network models, like Transformers or Gated Recurrent Units, deploying the model on the remote system configured with the switch so that model can parse through the incoming traffic and detect any anomalies. 

- performed further preprocessing on the NTP attack dataset
- separated data of interest from various attack datasets from the same source
- performed training and testing on several models and finalized an LSTM-based model for classification
- obtained evaluation metrics for the model on various testing sets
- compiled the project report with all the results and included detailed discussions about the methodologies and outcomes involved

targets:
- Finalize the model for classification of NTP DDoS attacks against benign communication records after conducting preliminary experiments. Optimize the architecture, hyperparameters, and any other relevant settings of the chosen model to achieve the best possible performance in distinguishing between NTP DDoS attacks and benign network traffic.
- Prepare testing sets with varying distributions to assess the model's robustness and generalization capability. Create subsets of data that represented different scenarios, such as varying attack intensities, different time periods, or different geographical locations. 
- Train the finalized model using the prepared training dataset, which contained labeled examples of NTP DDoS attacks and benign communication records. Adjust the model's parameters based on the provided labels, and iteratively update the model's internal representations to optimize its performance.
- Evaluate the performance of the model with commonly known metrics and techniques after training. Compute accuracy, precision, recall, F1 score, and area under the receiver operating characteristic curve (AUC-ROC). 

achievements:
- Performed further preprocessing on the NTP attack dataset to ensure the data was in a suitable format for analysis. This included tasks such as encoding categorical data, handling class imbalance and normalizing the data. Preprocessing was aimed at improving the quality of the dataset and preparing it for further analysis.
- Separated data of interest from various attack datasets from the same source as the NTP attack dataset was part of a larger collection of attack datasets from the same source. This involved filtering the dataset based on specific criteria on attributes related to NTP attacks such as the features which had maximum correlation with the target variable. After isolating the relevant data, it becomes easier to focus on the specific attack type and perform more accurate analysis.
- Performed training and testing on several models and finalized an LSTM-based model for classification. These models could include various traditional ML algorithms and some neural networks architectures. After comparing the performance of different models, an LSTM-based model was selected as the most suitable for classification. LSTM (Long Short-Term Memory) is a type of recurrent neural network that excels in handling sequential data, making it a popular choice for time series and text-based classification tasks.
- Obtained evaluation metrics for the model on various testing sets. Evaluation metrics such as accuracy, precision, recall, F1 score, AUC and confusion matrix were computed to quantify the model's classification performance on both training and validation sets during training for each epoch. After training they were obtained for the testing set as well. These metrics provided insights into the model's ability to correctly classify NTP attacks and distinguish them from other types of network traffic.
- Compiled the project report with all the results and included detailed discussions about the methodologies and outcomes involved. The report included detailed explanations of the methodologies used, such as the preprocessing techniques and the LSTM-based model architecture. It also presented the outcomes of the project, including the evaluation metrics obtained for the model on different testing sets. 


