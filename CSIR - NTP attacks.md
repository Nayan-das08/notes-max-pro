Date: 02/06/2023

DDoS attacks
Reflection attacks
DNS amplification attacks

## DDoS attacks in NTP
- **NTP (Network Time Protocol) amplification** is a type of Distributed Denial of Service (DDoS) attack.
- Attackers send small requests to publicly accessible NTP servers, forging the source IP address to be the target's IP.
- Due to a flaw in the NTP protocol, the server responds with a larger reply to the forged IP address.
	- return IP address spoofed to be the target address
- This amplification effect allows attackers to generate a large volume of traffic directed at the target, overwhelming its network capacity.
- Attackers typically use **botnets** (networks of compromised computers) to launch NTP amplification attacks.
- NTP amplification attacks can result in significant disruption, leading to service outages or degraded performance.
- real address of an attacker is never used due to the spoofing of the source IP address (reflection attack?)
- detailed analysis of such attacks is important in order to gain information which may be valuable in mitigating or finding the source of an attack
- mitigation of NTP amplification attacks is challenging because the responses from the NTP servers are ostensibly legitimate traffic from valid servers.
- volume of DDoS traffic could easily overwhelm even the most resilient of network infrastructures
- Mitigation techniques involve 
	- securing NTP servers
	- implementing rate limiting
	- filtering or blocking suspicious traffic at network level.
- *paper*: Rudman, Lauren, and B. Irwin. "Characterization and analysis of NTP amplification based DDoS attacks." 2015 Information Security for South Africa (ISSA). IEEE, 2015.
	- victims of the attacks were found by looking at the source port of the original attack packet
	- most popular source port found was port 80/udp, which they said may have been used to target games using this port or websites