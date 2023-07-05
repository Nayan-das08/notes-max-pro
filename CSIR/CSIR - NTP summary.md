Date: 01/06/2023
%%# NTP summary%%
## basics
- Network Time Protocol is a widely used protocol to synchronize computer clocks in the Internet
- computer clocks become inconsistent with each other after some time even after initialization with same time. 
	- this is because of clock drift
	- there are many reasons for clock drift in computer clocks
		- crystal oscillator clocks' accuracy diminishes over time die to temperature changes or aging
		- operating system synchronizing the clock with some accumulated error
		- power system introducing errors
		- etc.
- NTP can synchronize computers within few milliseconds of UTC.

## NTP in detail
- NTP is widely used to synchronize system clocks among a set of distributed time servers and clients
- NTP synchronizes a primary server to a reference clock which can be directly traceable to UTC. 

### protocol modes
- there are three NTP protocol variants
	- symmetric
	- client/server
	- broadcast
- each associated with an association mode
	- description of relationship between two devices using NTP (NTP speakers)
	- determines how NTP speakers interact with each other and exchange time information
- the modes are
	- **Symmetric Active**
		- association mode value = 1
		- packet mode value = 1 or 2
		- both devices are peers and actively communicate with each other
		- node mode value = 1: both can initiate request for synchronization
		- node mode value = 2: both can respond to them
	- **Symmetric Passive**
		- association mode value = 2
		- packet mode value = 1
		- one speaker acts as a passive peer, while the other speaker acts as an active peer.
		- active peer initiates requests
		- passive peer responds to them
	- **Client**
		- association mode value = 3
		- packet mode value = 4
		- persistent client (device configured to synchronize its time) sends 'packet mode 4' packets to server
	- **Server**
		- association mode value = 4
		- packet mode value = 3
		- NTP provides synchronization to one or more clients
		- server responds with 'packet mode 3' packets with time synchronization info
		- they can also become a reference clock driver that obtains time directly from standard source (GPS receiver or telephone modem service)
	- **Broadcast Server**
		- association mode value = 5
		- packet mode value = 5
		- NTP server broadcasts time synchronization info to multiple clients
		- server sends 'packet mode 5' packets containing time synchronization information to clients
	- **Broadcast Client**
		- association mode value = 6
		- packet mode value = not applicable as no info is sent
		- clients sync their time on the basis of broadcast information received
	- the devices communicating with NTP are synced on the basis of association modes
	- standard practice dictates that network topology should avoid timing loops. 
	- Bellman-Ford algorithm gives the shortest path tree with primary servers as the source/root. 
	- using this algorithm results in most accurate and reliable time in the network
- level of each server in the hierarchy is defined by stratum number

### terminologies
- timestamp $T(t)$ represents the UTC date or time offset from UTC at running time $t$.
$$T(t)=T(t_0) + R(t_0)(t-t_0) + \frac{1}{2}D(t_0)(t-t_0)^2 + e$$
where
- $T(t)$ is the time offset at time $t$
- $R(t)$ is the frequency offset
- $D(t)$ is the aging rate
	- first derivative of $R(t)$ wrt $t$
	- neglected for computer oscillators
- $T(t_0)$ is time offset determined at $t=t_0$
- $e$ is the stochastic error

When using NTP, it is important to assess the timekeeping function. The NTP performance model includes 4 statistics which are updated each time a client makes a measurement with a server.
- offset (theta)
	- the offset represents the difference in time between the client's clock and the server's clock at the time the measurement is made.
	- It indicates whether the client's clock is running ahead (positive offset) or behind (negative offset) the server's clock.
	- The offset is calculated by comparing the timestamp of the client's request packet with the corresponding timestamp in the server's reply packet.
- delay (delta)
    - round-trip time (RTT) between the client and the server, representing the time it takes for the client's request packet to reach the server and for the server's reply packet to return to the client.
    - It provides an estimate of the network delay or latency between the client and server.
    - The delay is calculated by subtracting the transmission timestamp (T1) in the client's request packet from the reception timestamp (T4) in the server's reply packet.
- dispersion (epsilon)
    - represents the maximum error or uncertainty in the server's time
    - increases at a rate equal to maximum disciplined system clock frequency tolerance (phi)
    - It provides an indication of the stability or quality of the time source.
    - Each time the client makes a measurement, the server includes its current dispersion value in the reply packet, and the client updates its own dispersion value based on this information.
- jitter (psi)
	- RMS average of the most recent offset differences
	- represents the nominal error in estimating offset

## NTP header

| Name      | Formula   | Description           |
| --------- | --------- | --------------------- |
| leap      | leap      | leap indicator (LI)   |
| version   | version   | version number (VN)   |
| mode      | mode      | mode                  |
| stratum   | stratum   | stratum               |
| precision | rho       | precision exponent    |
| poll      | poll      | poll exponent         |
| rootdelay | delta_r   | root delay            |
| rootdisp  | epsilon_r | root dispersion       |
| refid     | refid     | reference ID          |
| reftime   | reftime   | reference timestamp   |
| org       | T1        | origin timestamp      |
| rec       | T2        | receive timestamp     |
| xmt       | T3        | transmit timestamp    |
| dst       | T4        | destination timestamp |
| keyid     | keyid     | key ID                |
| dgst      | dgst      | message digest        |

- **leap indicator (LI)**
	- warning of an impending leap second to be inserted or deleted in the last minute of the current month
- **version number (VN)**
	- NTP version number, currently 4
- **mode**
	- 0-7 values for association modes
- **stratum**
	- 0 = unspecified or invalid
	- 1 = primary server
	- 2-15 = secondary server
	- 16 = unsynchronized
	- 17-255 = reserved
	- as stratum number increases, its accuracy degrades
	- *primary server*
		- synchronized to a reference clock directly traceable to UTC (eg: GPS)
		- can provide synchronization to one or more clients
	- *secondary server*
		- synchronized to primary or secondary servers
		- has one or more upstream servers
		- has one or more downstream servers (clients)
- **poll**
	- maximum interval between successive messages, in log2 seconds
- **precision exponent**
	- precision of the system clock, in log2 seconds
	- eg: a value of -18 corresponds to a precision of about one microsecond
- **root delay**
	- Total round-trip delay to the reference clock.
- **root dispersion**
	- Total dispersion to the reference clock.
- **reference ID**
	- ASCII code identifying the particular server or reference clock
- **reference timestamp**
	- Time when the system clock was last set or corrected
- **origin timestamp (T1)**
	- Time at the client when the request departed for the server
- **receive timestamp (T2)**
	- Time at the server when the request arrived from the client
- **transmit timestamp (T3)**
	- Time at the server when the response left for the client
- **destination timestamp (T4)**
	- Time at the client when the reply arrived from the server
	- not included as a header field; it is determined upon arrival of the packet and made available in the packet buffer data structure
- **key ID**
	- used by the client and server to designate a secret 128-bit MD5 key
- **message digest**
	- MD5 hash computed over the key followed by the NTP packet header and extensions fields
- offset = $\theta$ = $\frac{(T2-T1)+(T3-T4)}{2}$
- round-trip delay = $\delta$ = (T4 - T1) - (T3-T2)
- correction
	- dest_time(T4) + offset($\theta$) = tx_time(T3) + delay($\delta$)/2
	- correction = dest_time(T4) - tx_time(T3) = delay($\delta$)/2 - offset($\delta$)

---

- NTP from RFC-5905: NTP Specification document
	- protocol association modes and their affects
	- terminologies like time offset
	- statistics associated to NTP performance
		1. offset
		2. delay
		3. dispersion
		4. jitter
	- packet header
- created a python program using ntplib library to display ntp header for an NTP request
- having difficulty in capturing packets using scapy and pcapy due to system configurations.



NCITR


- NTP in terms of National time-keeping
- uncertainty vs error
- type 1 type 2 error
- calibration cert
- NTP service models
	- performance
	- script - 
	- identify servers
	- sync multiple times during the day
	- gather data about response, performance


