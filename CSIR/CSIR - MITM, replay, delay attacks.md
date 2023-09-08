---
tags:
  - csir
---
Date: 06/06/2023

## Man-in-the-middle (MITM) attack
- attacker secretly intercepts and relays communications between two parties 
- the two parties believe they are directly communicating with each other. 
- the attacker positions themselves between the legitimate parties and effectively becomes an intermediary, 
- gains unauthorized access to the information being transmitted
- steps
	- **establishing communication**
		- communication occurring between two entities
	- **interception**
		- attacker positions themselves in between the communication path between the two entities
	- **impersonation**
		- they impersonate the sender and relay the messages to authenticate each other
		- obtains authentication from both the entities
	- **relaying messages**
		- the messages sent by the entities after authentication is controlled by the attacker
		- spoofs the sender address to make the packet look like it originated from one of the two entities
		- can capture, manipulate the content of the communications

## MITM in NTP
- This type of attacks does occur in NTP traffic
- the attacker can incept the request to the NTP servers and manipulate the synchronized time which is sent as the response to the request

---
## replay attacks
- low tier form of MITM attacks 
- objective of the attacker is to intercept and re-transmit the messages between network entities
- the attacker intercepts the authentication during initial legitimate communication 
- the attacker can *replay* messages to the devices at a later time, acting as the original recipient of the captured transmission
- steps
	- capture and storage of authentication
	- replay of messages
	- achieving system acceptance

---
## time-delay attacks
- during time synchronization process
- client sends an NTP request to the server
- NTP server receives the request and sends a response with synchronized time
- there is a time delay between 
	- the instant the request is sent by the client
	- the instant the request is received and responded by the server
	- the instant the response is received by the client
- let 
	- $D_{CS}$ be the delay in client-to-server transmission
	- $D_{SC}$ be the delay in server-to-client transmission
	- $\Delta T$ be the total time delay
	- $t_C$ be the time of the client clock
	- $t_S$ be the time of the server clock
- now
	- $t_C = t_S + D_{SC}$
	- $\Delta T = D_{CS} + D_{SC}$
- assumption / simplification
	- $D_{CS} = D_{SC}$
- therefore
	- $t_C = t_S + \Delta T/2$
	- with $D_{prox} = \Delta T/2$
- problem
	- the assumption of $D_{CS} = D_{SC}$ may not hold if there is a delay caused by an attacker who is intercepting the transmissions between the client and the NTP server
	- because of this delay, $D_{SC} > D_{CS}$, which results in wrong time being input at the client side
	- the attacker can delay transmissions in both directions, with which the attacker can decide which clock (client or server) is ahead or behind.
- no mechanisms known to mitigate / counter delay attacks completely
- MITM attackers can delay or drop packets






