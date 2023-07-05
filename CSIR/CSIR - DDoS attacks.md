Date: 02/06/2023

Reflection attacks
DNS amplification attacks


## DDoS attacks
- due to the design of the internet, there are several opportunities for malicious users to attack the target server
	- susceptibility of a system to DDoS attack depends on state of security in the rest of the global internet
	- there are limited number of resources with each network entity
	- coordinated and simultaneous attacks are detrimental to the victims
	- it is assumed for IP packets to carry the IP address of the device where the transmission originated, but is never validated or enforced at any point
		- gives the opportunity for **source address spoofing**
		- escape accountability
	- local networks

---
## DDoS attacks in NTP
- **NTP (Network Time Protocol) amplification** is a type of Distributed Denial of Service (DDoS) attack.
- Attackers send small requests to publicly accessible NTP servers, *forging the source IP address to be the target's IP*.
- Due to a flaw in the NTP protocol, the server responds with a larger reply to the forged IP address.
	- return IP address spoofed to be the target address
- This amplification effect allows attackers to generate a large volume of traffic directed at the target, *overwhelming its network capacity*.
- Attackers typically use **botnets** (networks of compromised computers) to launch NTP amplification attacks.
- NTP amplification attacks can result in *significant disruption*, leading to service outages or degraded performance.
- *real address of an attacker is never used* due to the spoofing of the source IP address (reflection attack?)
- detailed analysis of such attacks is important in order to gain information which may be valuable in mitigating or finding the source of an attack
- mitigation of NTP amplification attacks is challenging because the responses from the NTP servers are ostensibly *legitimate traffic from valid servers*.
- volume of DDoS traffic could easily overwhelm even the most resilient of network infrastructures
- Mitigation techniques involve 
	- securing NTP servers
	- implementing rate limiting
	- filtering or blocking suspicious traffic at network level.
- *paper*: Rudman, Lauren, and B. Irwin. "Characterization and analysis of NTP amplification based DDoS attacks." 2015 Information Security for South Africa (ISSA). IEEE, 2015.
	- presented initial exploratory analysis of the IPv4 Time-to-Live values observed in two NTP based DDoS attack datasets.
	- victims of the attacks were found by looking at the source port of the original attack packet
	- most popular source port found was port 80/udp, which they said may have been used to target games using this port or websites
	- total of 64 distinct TTL values observed. The most frequent of these being 111
		- attacker was using a Windows operating system (assuming the TTL is not spoofed) as Windows sets the initial TTL to 128.
	- several common NTP DDos tools explicitly set the TTL field of the generated packets to the maximum value (255).


---
## Dataset specifications

| total | restricted | open | closed |
| ----- | ---------- | ---- | ------ |
| 1599  | 151        | 1359 | 88     |

| total | Stratum 1 | Stratum 2 | Inactive |
| ----- | --------- | --------- | -------- |
| 1599  | 281       | 372       | 943      |

- total = 1599
- open = 1359
	- stratum 1 = 209
	- stratum 2 = 346
	- inactive = 801
- closed = 88
	- stratum 1 = 20
	- stratum 2 = 3
	- inactive = 65
- restricted = 151
	- stratum 1 = 52
	- stratum 2 = 23
	- inactive = 76