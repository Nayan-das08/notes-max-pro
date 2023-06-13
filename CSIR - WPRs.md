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
### week 4

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

### Achievements

### Future Work Plans


---
## week 4: 19/06/2023 - 25/06/2023
### Target For The Week

### Achievements

### Future Work Plans


