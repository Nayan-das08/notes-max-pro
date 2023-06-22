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

The above definition helps us to measure time with extreme precision with the help of Atomic Clocks. These are able to maintain time with precision within a few billionths of a second per day. Unlike clocks working on other principles like quartz, which tends to lose one second every 30 years, atomic clocks lose one second in several billions of years. Thus, the accurate value of time at any instant can be obtained from an atomic clock. There are several National Metrological Institutes (NMIs) in the world, which are responsible for the standardization of the SI units for their region. These institutes have independent atomic clock systems which dictates the accurate time value for the region. The weighted average of around 450 atomic clocks in over 80 national laboratories is termed as International Atomic Time (TAI) and it represents the accurate time value as dictated by the atomic clocks. This value is different from the astronomical time (denoted by UT1) and thus is adjusted with leap seconds to get Coordinated Universal Time (UTC). 

## Time dissemination using NTP
The time obtained from the atomic clocks has to be shared across computer systems in a network that request for time synchronization services. For the purpose of dissemination of time across devices over a packet-switched network, Network Time Protocol was developed by David L. Mills in 1980s. It is one of the oldest protocols that is currently being used, the latest version being NTPv4.0, released in 2010. 

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
## Analysis
### General Inference


### Inference from each parameter
### Comparison study between Stratum 1 and Stratum 2

## Detection Model

---
# Conclusion

---
NTP amplification attacks are a type of Distributed Denial of Service (DDoS) attack that exploit vulnerable NTP servers to overwhelm a target with a large volume of network traffic. These attacks take advantage of the monlist command, which is a feature of older versions of NTP that allows a client to request a list of the last 600 IP addresses that have communicated with the NTP server.

The attack begins with the attacker identifying NTP servers that have the monlist feature enabled. This can be done through scanning techniques or by leveraging publicly available lists of vulnerable servers. Once the vulnerable servers are identified, the attacker spoofs the source IP address of their malicious traffic to make it appear as if the requests are coming from the target's IP address.

The attacker then sends a series of crafted requests to the identified NTP servers, making use of the monlist command. These requests are designed to elicit responses from the NTP servers that are significantly larger than the original request, creating an amplification effect. The response from the NTP server can be several times larger than the request, thereby generating a massive amount of traffic directed towards the target.

The IP address spoofing technique is a crucial component of NTP amplification attacks. By spoofing the source IP address, the attacker conceals their identity and makes it appear as if the target is initiating the requests. This not only makes it difficult to trace the attacker but also increases the impact on the target, as the responses from the NTP servers are directed towards the target's IP address. This can overwhelm the target's network capacity and disrupt its normal functioning.

The monlist command plays a central role in NTP amplification attacks. It allows an attacker to send a small query to an NTP server, requesting a list of the last 600 IP addresses that have interacted with the server. The server then responds with a list that includes the IP addresses along with additional information, resulting in a larger response packet. This amplification factor, where the response is significantly larger than the request, is what makes NTP servers attractive for attackers.

To mitigate NTP amplification attacks, it is essential to secure NTP servers by disabling the monlist command and updating to newer versions of NTP that do not support this feature. Network administrators should also implement strict ingress and egress filtering to prevent IP address spoofing and monitor their network for any suspicious traffic patterns.

Furthermore, Internet Service Providers (ISPs) play a vital role in combating NTP amplification attacks. By filtering outbound traffic from their networks to block spoofed IP addresses, ISPs can prevent attackers from utilizing their infrastructure to launch these attacks.

Overall, NTP amplification attacks exploit vulnerable NTP servers by leveraging the monlist command, IP address spoofing, and the amplification effect of the server's response. Understanding these attack techniques and implementing appropriate security measures are crucial for defending against such DDoS attacks.