# Abstract
In this project, we propose a deep learning-based detection model for Network Time Protocol (NTP) Distributed Denial of Service (DDoS) attacks. NTP is a critical protocol used for time synchronization in computer networks. However, NTP servers are susceptible to DDoS attacks, which can disrupt network operations and compromise system integrity. We develop a deep learning model that leverages the power of neural networks to accurately detect NTP DDoS attacks, enabling timely and effective mitigation strategies. Furthermore, we conduct an extensive analysis and comparative study on the responses from NTP stratum 1 and stratum 2 servers to gain insights into the difference in performance and distribution of other essential parameters. The results of this study provide valuable insights for securing NTP infrastructure and enhancing the resilience of network time synchronization protocols against DDoS attacks.

---
# Introduction
## Time Synchronization
The accurate measurement and synchronization of time are of paramount importance in various industries and sectors worldwide. Industries such as finance, telecommunications, transportation, power grids, and industrial control systems heavily rely on precise timekeeping for their operations. In the financial sector, accurate timestamps are crucial for transaction sequencing, ensuring data integrity, and facilitating auditing processes. Telecommunications networks require precise time synchronization to manage call routing and billing effectively, as well as to support synchronization protocols in mobile communication technologies. Transportation systems, including trains, buses, and airplanes, depend on accurate time values to maintain synchronized schedules and minimize delays. Power grids rely on precise time synchronization for monitoring, fault detection, and real-time control, enabling stable and reliable energy distribution. Similarly, industrial control systems require accurate time synchronization for coordinating distributed processes and optimizing resource utilization.

However, a significant challenge in maintaining accurate time lies in the phenomenon known as time drift. Clocks in various devices, even those equipped with quartz oscillators, experience gradual deviations from true time due to factors like temperature variations, aging, and inherent inaccuracies. Over time, these deviations accumulate, leading to discrepancies and inconsistencies among clocks. Such time discrepancies can have severe consequences in different industries. In financial transactions, even a slight time difference can result in incorrect calculations and compromise the integrity of audit trails. Unsynchronized clocks in telecommunications networks can cause call collisions and failed handovers, resulting in network congestion and degraded call quality. Time drift can disrupt schedules and lead to delays in transportation systems. In industrial processes, lack of time synchronization can hinder coordination, impacting productivity and quality control.

## Network Time Protocol
To address the challenges associated with time synchronization, various protocols have been developed, each aiming to provide reliable and accurate time values across devices and networks. Among these protocols, the Network Time Protocol (NTP) has emerged as a widely adopted and efficient solution. Network Time Protocol (NTP) serves as a reliable solution for maintaining time synchronization across devices in a networked environment. In today's interconnected world, where numerous devices rely on accurate and synchronized time values, NTP plays a crucial role in ensuring the smooth operation of various systems and applications.

NTP was first developed in the 1980s by David L. Mills at the University of Delaware and has since become the de facto standard for time synchronization in computer networks. It is an internet protocol designed to synchronize clocks between computer systems over packet-switched, variable-latency data networks. NTP uses a sophisticated algorithm to calculate the offset and delay between the local clock of a device and the time received from a reference server. By continuously adjusting the local clock based on the information obtained from the reference server, NTP ensures that all devices in the network maintain a consistent and accurate time value. It uses a combination of algorithms, including the Marzullo's algorithm and the intersection algorithm, to estimate and compensate for the transmission delay between the reference server and the client. By taking into account these factors, NTP ensures that each device's clock is adjusted to reflect the correct time as accurately as possible. 

## Cyber-attacks in NTP traffic
While NTP serves an essential role in maintaining accurate time, it is not immune to cyber-attacks. When NTP is compromised, the impact can be significant and wide-ranging. One of the primary consequences of NTP attacks is time inaccuracy. By tampering with the NTP protocol, attackers can introduce errors in time synchronization, leading to incorrect timestamps in logs, authentication failures, transaction errors, and synchronization issues in distributed systems. Such inaccuracies can have cascading effects on various aspects of system functionality and can be particularly problematic in critical sectors such as finance or data-intensive environments.

Another major impact of NTP cyber-attacks is service disruption. Attackers can exploit vulnerabilities in NTP servers by overwhelming them with a large volume of requests, leading to server overload or even crashes. When NTP servers become unavailable or unreliable, accurate time synchronization becomes challenging or impossible, affecting systems and applications that rely on synchronized time. This disruption can have severe consequences, especially for time-sensitive operations that depend on accurate timestamps or time-based event coordination. Critical systems that require precise time synchronization, such as financial transactions, real-time data analysis, or distributed databases, can be significantly impacted, resulting in operational disruptions and financial losses.

Furthermore, NTP attacks can exploit the time dependency of various security mechanisms and protocols. The accurate timing of cryptographic protocols, certificate validity, and time-based access controls are crucial for ensuring the security of networked systems. Manipulating the NTP protocol can undermine the integrity and effectiveness of these security measures. For example, a successful NTP attack could compromise the validity of certificates, making systems vulnerable to unauthorized access or impersonation. Additionally, cryptographic protocols that rely on accurate time synchronization, such as key exchange or timestamping, can be undermined, potentially leading to data breaches or unauthorized activities.

Some common types of attacks in the context of NTP:

1. Man-in-the-Middle (MitM) Attacks: In NTP, MitM attacks involve an attacker intercepting and modifying NTP communications between a client and a server. By inserting themselves in the communication path, attackers can manipulate the time synchronization process, leading to time discrepancies or even falsified timestamps. This can be particularly damaging when security mechanisms or cryptographic protocols rely on accurate time for secure operations.

2. Replay Attacks: Replay attacks involve an attacker intercepting and maliciously retransmitting NTP packets that were captured earlier. By replaying NTP packets, attackers can manipulate the time synchronization process and potentially disrupt system operations or compromise the integrity of time-dependent security measures.

3. Delay Attacks: Delay attacks aim to introduce intentional delays in NTP communications between clients and servers. By delaying NTP packets, attackers can disrupt the accurate time synchronization across systems, potentially leading to synchronization errors, authentication failures, or system malfunctions that rely on precise timing.

## NTP amplification attack
Another form of cyber-attack which is the most devastating and most commonly observed is NTP amplification, a type of Distributed Denial-of-Service or DDoS attack. This involves the attacker exploiting the design of the NTP protocol to overwhelm the target or victim network by redirecting an amplified volume of traffic towards it. The attacker typically uses networks of compromised computers, also known as botnets to launch the attack from a distributed source. These are able to cause significant disruption to the victim network's traffic as the amplification factor for request to response is substantially huge, reaching upwards till 200, leading to severe degradation or complete loss of services. This can result in extended downtime, financial losses, reputational damage, and disruption of critical business operations.

The objective of the project is to perform analysis and a comparative study between the responses from servers at different stratums of the NTP hierarchy in terms of various parameters concerning performance in time synchronization activities. A deep learning based detection model for NTP DDoS attacks is also proposed for network analysis and early detection of anomalies which indicate a possible NTP-DDoS attacks.

---
# Theoretical Background
## Obtaining Accurate Time
As per the 13th General Conference on Weights and Measures (CGPM), 

"The second is the duration of 9,192,631,770 periods of the radiation corresponding to the transition between the two hyperfine levels of the ground state of the cesium-133 atom."

The above definition helps us to measure time with extreme precision with the help of Atomic Clocks. These can maintain time with precision within a few billionths of a second per day. Unlike clocks working on other principles like quartz, which tends to lose one second every 30 years, atomic clocks lose one second in several billions of years. Thus, the accurate value of time at any instant can be obtained from an atomic clock. There are several National Metrological Institutes (NMIs) in the world, which are responsible for the standardization of the SI units for their region. These institutes have independent atomic clock systems which dictates the accurate time value for the region. The weighted average of around 450 atomic clocks in over 80 national laboratories is termed as International Atomic Time (TAI) and it represents the accurate time value as dictated by the atomic clocks. This value is different from the astronomical time (denoted by UT1) and thus is adjusted with leap seconds to get Coordinated Universal Time (UTC). 

## Time dissemination using NTP
The time obtained from the atomic clocks must be shared across computer systems in a network that request for time synchronization services. For the purpose of dissemination of time across devices over a packet-switched network, Network Time Protocol was developed by David L. Mills in 1980s. It is one of the oldest protocols that is currently being used, the latest version being NTPv4.0, released in 2010. 

NTP operates on a hierarchical system of time servers, where each server is assigned a stratum level representing its distance from a reference time source. The reference time source, known as a primary server or stratum 0, typically consists of highly accurate atomic clocks or satellite-based systems like the Global Positioning System (GPS). Stratum 1 servers directly synchronize with the primary source, while stratum 2 servers synchronize with stratum 1 servers, and so on. Devices within the network act as NTP clients, synchronizing their clocks with the most reliable and accurate stratum server available.

The stratum 1 servers are known as primary servers as they are directly synchronized with the atomic clocks. For instance, the NTP server for CSIR-National Physical Laboratory, time.nplindia.org is a primary server as it is synchronized with the atomic clock at NPL. These can provide synchronization to one or more clients. Secondary servers are those which are synchronized to the primary servers or other secondary servers. These have one or more upstream servers, from which it gets the time synchronization services and downstream servers, to which it provides it provides time synchronization services.

The client device which requires the time synchronization sends a request packet to an NTP server with an NTP Header, a protocol data unit for NTP, over the UDP unit. The NTP Header consists of fields like protocol version being used for transmission, stratum value of the NTP server, association mode of communication, timestamp of the server clock, etc. which are essential for the system to get synchronized with the NTP server. During transmission of the NTP request packet, the fields are left empty as these are to be filled by the NTP server during transmission of the response to the request. Once the packet is received by the intended target, the server fill the fields with the corresponding values and sends a response packet to the client. The client upon receiving the response calculates the appropriate offset which has to be added to the server clock timestamp due to round trip delay between the transmissions and sets the resulting timestamp as the system time.

Time synchronization is needed by a device when the system clock is at a different timestamp than a server clock. This difference is called offset and is represented by Greek symbol theta. It indicates whether the client's clock is running ahead (positive offset) or behind (negative offset) the server's clock. It is computed by comparing the timestamp of the client's request packet with the corresponding timestamp in the server's reply packet. Another important parameter which is calculated after the response packet is received by the client is delay, denoted by Greek symbol delta. This represents the round-trip-time (RTT) or round-trip-delay (RTD) between the client and the server, i.e., the time it takes for the client's request packet to reach the server and for the server's reply packet to return to the client. It provides for an estimate of the network delay or latency between the two entities and is calculated by subtracting the transmission timestamp in the client's request packet from the reception timestamp in the server's reply packet. These two help in calculating the correct time at the client side by incorporating the delay and offset and helps in evaluating the performance of the NTP server and the network infrastructure between the client and the server.

## Working of NTP amplification attacks
NTP amplification attacks by design are not very complex, but are extremely effective in causing disruption in victim network's traffic. As discussed earlier, it is a type of DDoS attack which exploits the NTP server which are vulnerable to such attacks with the help of command "monlist", which allows the client to request the list of IP address of the last 600 users which availed NTP services from the server. The command is a functionality introduced in the older version of the protocol and is responsible for the significantly amplified response which is directed towards the target. 

The attacker first identifies the vulnerable servers which are publicly available. Once the list is sourced, the attacker then creates the request packets to be sent to the NTP server while spoofing the source IP address as the target network's IP address. This creates the illusion of requests coming from the target's IP address, while the requests actually originate from the attacker's IP address. This helps in concealing the identity of the attacker as the responses are never traced back to the malicious system. These request packets typically are transmitted in large quantities over a period of time from a distributed system of compromised computers called botnets, so that the number of requests sent can be maximized so that the amount of traffic directed towards the target IP address is significantly huge. 

The response from the NTP servers on these malicious requests contains the requested list of the last 600 IP address that have interacted with the server. This resulting reply packet is substantially larger in size than the request packet, giving extremely high amplification factor. DDoS attacks like these which implement amplification are very difficult to identify as they appear like genuine traffic and do not present themselves as outliers. Thus, detection of such attacks is pertinent so that the attackers do not exploit the NTP servers to overburden the victim network's infrastructure.

---
# Methodology
## Analysis
The methodology employed for conducting the comparative study between NTP stratum 1 and stratum 2 server responses involved a systematic approach to gather and analyze data. This section outlines the steps undertaken to ensure a robust and reliable investigation. 

Firstly, a comprehensive list of servers was compiled using web scraping techniques from the support.ntp.org website, which served as the primary data source. The collected server information included hostname, IP address, geographical location, and stratum level. Once the list was compiled, requests were sent to the NTP servers using appropriate protocols, and the corresponding responses were collected. This process allowed for a direct comparison of the response behavior of stratum 1 and stratum 2 servers. The subsequent sections provide further details on each step of the methodology, including the specific procedures and tools used in the study.

### Compiling a List of Servers
In order to begin with the analysis, a comprehensive list of NTP servers must be created. The list was essential to ensure for a diverse and representative sample of servers for our analysis. At first, we need to find a reliable source which can provide the aforementioned list of servers with the required details. After evaluating multiple sites, support.ntp.org was chosen as the source. The website was listed in several official NTP websites which provide documentation and maintenance for the protocol. It contained the details of about 1600 servers, with information like hostname and IP address, stratum level, location of the server and their access policy. These details are also collected as they helped in filtering the list into required classes.

The details about each server was available with its own URL. To collect the details from the website about a particular server, the corresponding site has to be visited. Thus, a web scraping technique was utilized for the process of collection of data from the source. The Python script for scraping consisted of several sections like obtaining the HTML script for the website, filtering through the tags to reach the desired fields, obtaining the value from the field into a dictionary format in Python and treating non-responsive URLs and empty fields. After collecting the information about all the available servers in the form of list of dictionaries, write the elements of the list into a CSV file so that it can be filtered with the help of pandas Python library. 

After reopening the file as a DataFrame with the help of ISO-8859-1 encoding, only those servers are selected for the analysis which have open access policy and then are split on the basis of stratum levels into two different CSV files. Out of 1599 servers in the master list, 1359 servers had open access policy, out of which 209 belonged to stratum 1, 346 belonged to stratum 2 and 809 servers were inactive. The active servers were filtered and placed in new CSV files. Now using these two lists of active servers, requests needed to be sent so that responses can be collected.

### Sending Requests to NTP servers
The requests to the NTP servers are sent in such a way so that the response with the NTP Header containing the corresponding time synchronization information can be accessed. For this, we utilize the ntplib Python library. It enables us to send an NTP request to the required server and receive the response with all the required fields of the NTP Header. 

For sending a request, a NTPClient object has to be instantiated. Using this object NTP requests can be sent using `NTPClient.request(server)` method. We need to read the CSV file to retrieve the list of appropriate stratum level servers and get the list of hostnames. The elements in this list are used to set the server argument in the `request()` method. 

```python
import ntplib

server = 'time.nplindia.org'
ntp_client = ntplib.NTPClient()
ntp_response = ntp_client.request(server)

data = []
dic = {}

dic['server'] = server
dic['leap'] = response.leap
dic['version'] = response.version
dic['mode'] = response.mode
...
data.append(dic)
```

### Collecting the corresponding responses
We invoke the request method for all the available server hostnames using a loop and store the response obtained from the server in a list of dictionary format. In some of the iterations, there might not be any response from the NTP server. In such a case, the fields of the NTP Header in the dictionary must be filled with blank string so that the instances of non-responsive requests will be noted during the analysis.

The obtained list of replies from the servers are then stored in a CSV file with append mode argument as the responses have to be collected on a regular basis. The python script to send requests and store responses is automated and scheduled to run 3 times a day at equal intervals to represent the performance throughout the day. 

```python
file = 'data.csv'
with open(file, 'a', newline='') as csvfile:
    writer = csv.DictWriter(csvfile, fieldnames = col)
    writer.writerows(data)
```

## Detection Model
### Dataset Used
### Implemented Model

---
# Result and Discussion
This section presents a comprehensive analysis of the comparative study between Stratum 1 and Stratum 2 NTP server responses, along with the evaluation of the performance of the applied model for identifying NTP amplification attacks within the NTP traffic on a variety of datasets. These results and analysis outcomes aims to provide a detailed understanding of the performance and limitations of the server types and deep learning model, which ultimately enables us to interpret the relationship between various aspects of the protocol response and NTP DDoS attacks  the mitigate the attacks as much as possible. 

## Comparison study of Stratum 1 and Stratum 2
The comparative study on the hierarchy levels of the NTP servers is conducted over a period of 18 days, from June 16, 2023 to June 23, 2023, during which the Python script was able to successfully record 49 epochs of responses from the servers. An epoch is termed as the process of requesting the time sources for accurate time values and obtaining the corresponding response for all the servers. For the purpose of this project, the number of epochs per day is kept at 3, with each epoch taking place at equal intervals. 

The study consisted a total of 555 NTP servers were selected, comprising of 209 Stratum 1 servers and 346 Stratum 2 servers. These servers were carefully chosen on the basis of geographical heterogeneity, open access policy and network infrastructure. The responses were collected from each server several times, resulting in a substantial dataset of server replies. In total, there is a comprehensive set of 28,860 responses, in which the dataset consists of 10,868 instances corresponding to list of Stratum 1 servers and 17,992 instances corresponding to the Stratum 2 servers. This dataset serves as the basis for further analysis and exploration into the behaviour and performance of servers across the stratum levels. 

The comparative review is based upon statistical analysis and the inference of the information obtained from the analysis for each of the parameters in the NTP Header. The NTP Header contains the time synchronization information as well as other arguments which indicates the performance and effectiveness of any server in the domain of time keeping. The analysis and the respective deduction of parameters is as follows.

### mention the mechanism of obtaining the responses by referencing above section
### mention null responses

### Leap Indicator (leap)
This parameter is used to give the warning of an impending leap second to be inserted or deleted in the last minute of the current month. Leap second is a one-second adjustment which is either added to or subtracted from the UTC to account for the irregular difference between astronomical time and accurate obtained from an atomic clock. The need for such an accommodation arises when the difference between the two clocks is more than 0.6 seconds. The parameter is a two bit field in the Header and can hold 4 values, from 0 to 3, each having a specific interpretation for the time keeping clock. 

In the collected set of responses, the leap value for all the responses from the Stratum 1 NTP server had value 0. This indicates that there is no need for any adjustment of an additional second. However, among the responses from Stratum 2 NTP servers, 2 servers on separate occasions returned the packets with the leap value as 3, which indicates unsynchronized clock at the server's side. These servers were: tick.meteonews.ch at time and ntp4.netwrx1.com. This points towards that the Stratum 1 servers are more precise and have less number of faults.  

### Version Number
The packet with an NTP Header, i.e., an NTP request or response has to inform the recipient device about the version of the protocol that is being used to send the requests. This information is relayed with the help of the Version Number field, where the values can vary from 1.0 to 4.0. The subsequent versions of the NTP protocol come with backward compatibility, thus systems with varying NTP versions can communicate and synchronize their clocks. 

In our observation, there are a variety of NTP versions being used currently by the servers of both the stratum levels. In the batch of responses from Stratum 1 servers, the distribution of Version Number over the responses is as follows: 

|         | number of responses |           |
| ------- | ------------------- | --------- |
| version | stratum 1           | stratum 2 |
| 2.0     | 5703                | 9541      |
| 3.0     | 409                 | 47        |
| 4.0     | 312                 | 0         |

This allotment shows us that most of the Stratum 1 and Stratum 2 servers are still using NTPv2.0, even after over 31 years of introduction of an advanced version of the protocol. This suggests how the servers are resolute in maintaining the time keeping architectures as older models are considered more reliable and stable. Another implication would be several of these servers running on legacy systems solely dependent on backward compatibility of the protocol and other systems. As compared to the usage of version 2, NTPv3.0 and NTPv4.0 in Stratum 1 and 2 and NTPv3.0 in Stratum 2 responses and are very scarce, with only 45 responses received from the version 3 servers in the case of latter. Another remark that could be made is that no response packets in Stratum 2 version 4 server is recorded over the period of observation in contrast to about 300 responses from Stratum 1 version 4 servers. This leads to the assumption that Stratum 1 servers are maintained and organized better than the Stratum 2 servers, as they are regularly upgraded for new software and firmware.

This information is very crucial to attackers as they use the data to identify weak and vulnerable servers which are working on old software. Such servers are more susceptible to the DDoS attacks as the NTP amplification employs the command present in older version NTP and they lack any new development regarding protection against such attacks as they are available to the newer versions. 

### Mode
The mode value represents the association mode used for the transmission of the response. While communicating between servers and clients, several modes of associations can be formed between the entities. This includes symmetric active, symmetric passive client, server, broadcast, etc. Each has some unique value associated with it called the mode value. Some of the values of this field are reserved for specific purposes and specific users as well. 

Throughout the dataset, across all the responses, the value for mode is taken as 4, i.e., client association mode by the response packets sent by the server. This is because the relationship between the system is sending the packet and the system requesting the time is of client-server type. Thus, to compliment that, the server sets the particular field with the value 4. This distribution, or lack thereof, is a result of the architecture of the request and response system. 

### Stratum
The stratum level at which the server is operating is provided by this field. This information is important to determine the level of accuracy with which the client system clock is synchronized with. The level of stratums determine the quality and accuracy of the server clock as the accuracy decreases as we move down the levels. Atomic clocks which determine the accurate time are denoted with Stratum 0. These are the time source that act as the reference clocks for the systems across the world. The Stratum 1 servers extract their synchronized time from the above mentioned Stratum 0 servers, thus being the server with the most accurate time which can be disseminated to other clients and servers. Thus Stratum 1 servers have the responsibility to maintain the level of quality to ensure precise values of time are being passed down to other systems. Each NTP Stratum 1 server is in fact associated to a primary time source like an Atomic Clock or a GPS-based system. The servers which get their information from Stratum 1 servers instead of directly from the time sources at Stratum 0 are known as Stratum 2 servers. These are dedicated to serve the huge traffic of systems requesting time synchronization from NTP servers. Unlike these have one or more upstream servers as they synchronize their systems with the help of a number of sources, thus maintaining the accuracy and establishing redundancy. However, since the round trip delay to relay the packets in a packet switched network gets accumulated along the stratum levels, they are slightly less accurate as compared to the Stratum 1 servers.

In the set of responses collected from the servers, the stratum information in the packets of the responses should coincide with the information about the respective servers on the website from which the list of servers was compiled. But due to some inconsistencies during the compilation of data by the organization, several servers were classified incorrectly. This was known after filtering packets on the basis of the 'stratum' field of the response. Out of 209 servers originally grouped as Stratum 1, 41 servers were Stratum 2 and 8 servers were Stratum 3 in reality. Similarly, out of 346 Stratum 2 servers, 17 belonged to Stratum 1, 41 belonged to Stratum 3 and 10 belonged to Stratum 4 level. These misclassified server responses were filtered from the original dataset and were not chosen for further analysis for the sake of maintaining the consistency and continuity of the time series data as the result of analysis on other parameters might get skewed due to any irregularities in the collection of data from the servers of both the stratum levels.

### Poll
The maximum interval between two successive communications with the server in log2 seconds is denoted by the parameter called 'poll value'. This value is quite essential as it enables us to determine how frequently can the server entertain NTP requests from clients and regulate the rate or frequency at which the client can send requests to the server to synchronize its time. 

The responses collected help us understand the distribution of the poll values among the packets from various servers and analyse the hidden patterns between the said value and its chances of being used for an amplified attack. For Stratum 1 server responses the distribution of the poll values lie in the range of 0 to 13, with the maximum number responses being from servers with poll values 0 and 3. There are 50 servers in the list of Stratum 1 servers that utilize the poll value of 0 which represents the servers do not have any restriction on the number of communications which are handled per unit time as the maximum interval between consecutive messages is set at 0. In contrast there are about 7 servers, belonging to NIST and NSFNET with 13 of maximum interval between two successive messages. 

In the response from Stratum 2 servers, the distribution of poll values is from 0 to 10, with majority of them having poll value of 3. The trend of number of servers with highest and lowest poll values are similar to that of previously discussed Stratum 1, where there are 56 servers which sent the synchronization information with the poll value of 0 and only one server with the highest value of 10, i.e., tick.binary.net. 

The poll values are critical for identifying the servers which can be exploited for the amplification attack as the servers with low poll values can respond to more malicious packets per unit time, resulting in an increase in the amplification rate. Thus, servers which are maintained regularly are kept at a higher poll value so that the system cannot be misused for malicious purposes. The default values set for the maximum and minimum poll value as per the RFC documentation of NTPv4.0 are 6 and 10 log2 seconds respectively. The percentage of servers with poll value above the default minimum value for Stratum 1 and 2 are 13.61% and 2.67% respectively, reflecting on the fact that Stratum 2 servers are much more vulnerable to be used for DDoS attacks that Stratum 1 servers because of their lower poll value and their ability to respond more frequently. 

### Precision
It is an 8-bit signed integer value representing the precision of the system clock of the device which is sending the NTP packet. While sending the reply for the NTP request, the server attaches its specified precision value to the NTP Header to inform the client about its timekeeping accuracy. It is stored in terms log2 seconds and thus, a lower value indicates a higher precision and vice versa. Higher the precision value, more accurate is the time value provided by the system. It can also be considered a metric of performance and can be used for comparing the servers for appropriate usage. 

The value of precision lies over a range of -29 to -17 for Stratum 1 and a range of -29 to -6 for Stratum 2 servers. There are several Stratum 2 servers which are transmitting responses with precision value lower than the minimum value of the Stratum 1 servers, indicating a degradation of quality and accuracy of time across the stratum levels. Although, the number of responses in the range of -25 to -20 precision value for Stratum 2 is greater than that of Stratum 1, the proportion of Stratum 1 servers in higher precision is greater that Stratum 2, supported by the statistics that about 23.81% of the Stratum 1 servers have successfully transmitted 1408 NTP packets with a precision value above -18, i.e., a generally accepted admissible value for general purpose usage, whereas the same percentage for Stratum 2 lies as 6.22% of the servers with about 553 successful transmissions. 

### Root Delay (rootdelay)
This represents the total round trip delay, i.e., the time taken to receive the request and to transmit the response to the client and for the client to receive the response packet. This value is an estimated figure of the round trip delay which will actually occur when an actual client sends a requests to the NTP server. The estimated value helps in ranking the server as per the network architecture and their overall performance in broad terms. 

The value for Root Delay is significantly low for the Stratum 1 servers, with about 123 servers operating with an estimated round trip delay of 0 seconds, with a collection of 5276 responses recorded throughout the period of experiment. The rest of the responses are distributed over values 0.000015 and 0.000244, with a small spike at 0.100006. In contrast, the responses of Stratum 2 servers are scattered almost uniformly over the range of 0 to 0.361374, with the maximum number of responses having a delay of 0.000229 and 0.000259. 

The value of Root Delay in the NTP Header is an estimated value as mentioned above and is used for an overall ranking of the server's performance, but the true value of total round trip delay is actually used to synchronize the client system clock with the acquired time value from the requested server as the time taken in the transmission has to be accounted for while setting the clock.

### Root Dispersion (rootdisp)
The Root Dispersion value represents the estimated maximum error associated with the server clock. This value provides an indication of the stability or quality of the time source and is similar to Root Delay value in its usage for comparing the NTP servers in their timekeeping services.

The distribution of the field is very similar to that of Root Delay for both the stratums, with a huge majority of responses belonging to the group having dispersion value of 0 which is also the minimum value for Stratum 1 with rest of the responses lying between the minimum and 4.897125. Analogous to the distribution of Stratum 2 responses, the recorded packets lie in the range of 0 to 4.901962. The value of uncertainty or dispersion is accumulated across each level of the hierarchy of the NTP architecture, thus, reflects higher dispersion values for servers at lower stratum levels.

### Reference ID (refid)
A 32-bit code representing the reference clock that the server is synchronized with, which can be identified using a unique ID. The value of this parameter has different interpretations as the ID value depends on the stratum level of the NTP server. For Stratum 1, it is a 4 character ASCII string denoting a reference clock, like GPS for Global Position System, IRIG for Inter-Range Instrumentation Group and so on. In the servers belonging to Stratum 2 or higher, the identifier corresponds to the first four octet of the IPv4 address of the reference clock used to synchronize their time, which here are the Stratum 1 servers. Another usage of Reference ID is to detect presence of any timing loops between the secondary servers. The number of sources used by the servers to synchronize their clocks are 35 and 281 for Stratum 1 and 2 responses respectively. 

The value helps us to understand the reliability of the upstream reference clock as the ID can be traced back to the source and the server's accuracy can be associated with the reference clock. This again points towards the fact that Stratum 1 servers provide with much more accurate time as they are synchronized by a system of source which act as the primary source of accurate time, whereas the Stratum 2 servers are dependent on the former for their synchronization.

### Reference Timestamp
This field refers to the timestamp at which the server's system clock was last updated. This information is usually specified as number of seconds from the Unix epoch, i.e., 1 January 1970 00:00:00. The significance of the reference timestamp is that it represents the reliability and the relevance of the server's timekeeping services and helps determining how recently the time being synchronized with was updated from the system's upstream servers. A more recent timestamp refers to a more accurate value of time as the offset between the server clock and reference time source accumulates over and increases over time. 

While studying the distribution of reference timestamps from the collected data, the timestamps of the time of recording with the most responses are chosen for both the stratum levels as these will be able to convey the information about most of the responses on the basis of the timestamps. The recording timestamps chosen for Stratum 1 and Stratum 2 are "2023-06-07 16:00:00" and "2023-06-10 11:00:00" respectively. By further analysis, it was found that the components of reference timestamps for the particular recording timestamp for Stratum 1 have distinct values only by the minutes and seconds implying that the servers are updated within the preceding hour of recording the results. The same analysis on Stratum 2 responses yielded that the server's system clocks are updated within a few days preceding the date of recording, suggesting a significantly lower frequency of synchronizing of the system clocks for Stratum 2 NTP servers. This again shows how Stratum 1 NTP servers are superior to the Stratum 2 counterparts in terms of accuracy and reliability. 

### Other Timestamps
There are 4 other parameters involving timestamps in the NTP Header which convey the information about the time at which certain activities took place. These are Origin Timestamp (T1), Receive Timestamp (T2), Transmit Timestamp (T3) and Destination Timestamp (T4).

The T1 denotes the time at which the NTP request is sent from the client device. It is included in the NTP packet by the device right before sending the request while the other fields are empty. T2 is the time at which the server receives the NTP request packet from the client. It copies the T1 timestamp from the request and inputs its value along with T2 and T3 into the NTP response packet before transmitting back to the client device. The receiving timestamp is required to determine the network delay between the client and the server. When the server sends the response packet, it attaches the local system time as T3 which serves the purpose of transmitting timestamp for the packet. The last field is kept empty as it denotes the time at which the client device successfully receives the packet transmitted by the server. Once the reception is successful, the local time of the client's system clock is entered in the field as T4. These values help determining the total round-trip delay that the communication experiences. 

The value of transmit timestamp, or T3, is the actual value of the server's system which the client requested for time synchronization. This value needs to be adjusted for the delay appropriately before it is set as the synchronized time by the system. To access the value of the timestamp from the response packet using Python and ntplib module, the following code is used.

```python
import ntplib

server = 'time.nplindia.org'
ntp_client = ntplib.NTPClient()
ntp_response = ntp_client.request(server)

print(ntp_response.tx_time)
```

### Calculated Round-Trip Delay
The value of round-trip delay can be calculated using the timestamps present in the NTP Header and the following formula:
$$\text{round-trip delay, }\delta = (T4 - T1) - (T3-T2)$$
This gives the true delay experienced by the communication between the two entities in the request-reply configuration as opposed to the estimated value in the root delay field of the packet header. 

The results of the calculated round-trip delay are similar to the estimated value provided by the server, with almost all the values in Stratum 1 responses having delay of 0 and 1 seconds, with the rest of the values having a uniform distribution from 0.002556 to 3. The calculated delay has the highest value about 3 times the highest estimated value, which points the network conditions, the real world communication scenarios and how the network architecture holds up during the experiment. In contrast the Stratum 2 calculated delay value's distribution is very close to that of the estimated value in terms of range, with the estimated value lying in the range of 0 to 0.203856 seconds, but show spikes with 0 and 1 having the maximum values and the remainder of the values in the range having a uniform distribution. 

In Stratum 1, there are a few cases of responses registering a negative round-trip delay, with one instance with value of -36 and 8 cases where the delay calculated to be -1. These are indications of the server clock being unsynchronized and running behind the client's system clock, which is a rare observation. 

### Offset


### where does time.nplindia.org stand


## Detection Model

---
# Conclusion

---
