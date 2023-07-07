# 1 second para se 1.3 tak pura (types of NTP attacks)
same
However, a significant challenge in maintaining accurate time lies in the phenomenon known as time drift. Clocks in various devices, even those equipped with quartz oscillators, experience gradual deviations from true time due to factors like temperature variations, aging, and inherent inaccuracies. Over time, these deviations accumulate, leading to discrepancies and inconsistencies among clocks. Such time discrepancies can have severe consequences in different industries. In financial transactions, even a slight time difference can result in incorrect calculations and compromise the integrity of audit trails. Unsynchronized clocks in telecommunications networks can cause call collisions and failed handovers, resulting in network congestion and degraded call quality. Time drift can disrupt schedules and lead to delays in transportation systems. In industrial processes, lack of time synchronization can hinder coordination, impacting productivity and quality control.

1.2
changed
Various protocols have been created to overcome the issues involved with time synchronisation, each striving to offer reliable and precise time values across devices and networks. The Network Time Protocol (NTP) [2] has emerged as a widely used and efficient option among these protocols. Network Time Protocol (NTP) is a dependable approach for maintaining time synchronisation between networked devices. NTP is critical in guaranteeing the smooth running of diverse systems and applications in today's linked world, as countless devices rely on precise and synchronised time information.

changed
In the 1980s, David Mills was the first to design NTP. It is now accepted practise for computer networks to synchronise time. Over packet-switched, variable-latency data networks, it is an internet protocol created to synchronise clocks between computer systems. NTP makes sure that all devices in the network keep a constant and precise time value by continuously adjusting the local clock depending on the data collected from the reference server. It techniques like the intersection algorithm and Marzullo's algorithm, to estimate and account for the transmission delay between the client and the reference server. NTP makes sure that each device's clock is set to display the right time as precisely as possible by taking into consideration these variables.

same
NTP is widely used across many different industries. NTP is essential for synchronizing clocks and guaranteeing precise timekeeping across networks and systems in the IT industry. NTP is frequently utilized in the telecommunications industry for call routing, network synchronization, and invoicing procedures. For trading activity and transaction timestamps, financial services rely on NTP's accurate timekeeping. NTP is used by institutions and laboratories engaged in scientific research to synchronize timing for experiments and data analysis. NTP is used by broadcasting and media firms to precisely schedule programmes and uphold precise broadcast timing. NTP is also used by transportation systems to maintain synchronized timing, enabling effective scheduling and coordination between diverse modes of transportation. These sectors gain a lot from NTP's capacity to deliver accurate and synchronized timekeeping, enabling seamless operations and connectivity.

1.3
Although NTP plays a crucial role in ensuring accurate time it is not impervious to cyber attacks. When NTP is compromised the repercussions can be extensive and impactful. An important consequence of NTP attacks is the distortion of time accuracy. Attackers can manipulate the NTP protocol. Resulting in erroneous timestamps in logs, authentication failures, transaction errors, and synchronization problems in distributed systems. These inaccuracies can have far reaching effects on different aspects of system functionality and are especially troublesome in sectors that deal with finance or handle large amounts of data [3].




# 4.1 pura

# 4.2 pura
4.2.1 first 2 para
A full list of NTP servers must be made in order to start the analysis. To guarantee a wide and representative sample of servers for our investigation, the list was crucial. Finding a trustworthy source that can supply the list of servers with the necessary information is the first step. Support.ntp.org was selected as the source after a review of several websites. The website was included in a number of approved NTP websites that offer protocol documentation and upkeep. It had information on around 1600 servers, including hostname and IP address, stratum level, server location, and access policy. These specifics are also gathered because they assisted in sorting the list into prerequisite courses.

Each server's specifics might be accessed through a unique URL. A specific website must be accessed in order to gather information from it about a certain server. The procedure of gathering data from the source was thus carried out using a web scraping approach. The Python script for scraping was divided into various phases, including acquiring the website's HTML script, filtering through tags to find the needed fields, getting the value from the field into a dictionary format in Python, and handling non-responsive URLs and empty fields. Write the list's components into a CSV file after gathering information about all the servers that are accessible in the form of a list of dictionaries so that it may be filtered using the

4.2.2
Requests to NTP servers are made in such a way that the NTP Header with the associated time synchronisation information may be read. byWe use the ntplib Python package for this [18]. 

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