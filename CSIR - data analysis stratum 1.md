## shape
- total number of rows: 4598 
- number of epochs: 22 
- in each epoch (209 rows = 1 epoch) 
	- number of duplicated servers: 10 
	- number of unique servers: 199 
- number of null valued rows: 972
- columns
	- categorical
		- `leap, version, stratum, time_of_recordin, refid`
	- numerical
		- `mode, precision, poll, rootdelay, rootdisp`
	- time values
		- `server, reftime, org, rec, xmt, dst, system_time`

## stats
- all `leap` values are 0
- most of the servers use `NTPv2`
- all servers communicated in `association mode 4`: **server mode**
- although the servers claimed to be Stratum One (on the basis of list obtained from *support.ntp.org*), there are some Stratum 2, 3 and 4 servers in the dataset
- the range of `precision` (<u>precision of the system clock, in $log_2$ seconds</u>) is from -29 to -17, maximum servers having precision of -25
    - the servers are working with 
      - **min. precision** of $2^{-17} = 7.6293 \times 10^{-6}$ seconds and 
      - **max. precision** of $2^{-29} = 1.8626 \times 10^{-9}$ seconds
- `poll` (<u>maximum interval between successive messages, in $log_2$ seconds</u>) for most servers is 3 and 0 (in decreasing order)
- `rootdelay` (<u>total round-trip delay to the reference clock</u>) for almost all servers is 0
- `rootdisp` (<u>total dispersion to the reference clock, dispersion being error or uncertainty in the server's time</u>) is 0 for almost all of the servers
- `refid` for most of the servers is $1196446464.0$
- features: `poll, rootdelay, rootdisp` have outliers
- some servers do not respond (due to address resolution issues or request time-out) in each epoch

## inference
### server

### stratum
- stratum 1
	- in the list of stratum 1 servers obtained from support.ntp.org
		- Stratum 1 = 3316 
		- Stratum 2 = 559 
		- Stratum 3 = 70 
		- Stratum 4 = 21
- stratum 2
	- in the list of stratum 2 servers,
		- stratum 0 = 8
		- stratum 1 = 351
		- stratum 2 = 5094
		- stratum 3 = 493
		- stratum 4 = 24
- the actual stratum values are obtained from the NTP header information of the NTP server response
- there were inconsistencies in the source where the description of each servers is provided
- the true stratum 1 and stratum 2 servers are filtered and analysed

### leap
- all servers responses have leap value = 0. 
- this means that there is no need for a leap second to be added or subtracted from the last minute of the current month during the duration of sending requests.
- the value will vary when a need arises for addition or subtraction of a leap second due to the difference between UTC and UT1 being greater than 0.6 seconds

### version
- stratum 1
	- majority of stratum 1 servers, i.e., 2936 servers sent response using NTPv2.0, while 168 servers used NTPv3.0 and 212 servers used NTPv4.0
	- this shows that although the latest version of NTP: NTPv4.0 was been released in 2010 with the publication of RFC 5905, older versions of the protocol are still in circulation as the protocol provides backward compatibility with older versions. Many organizations prefer continuing with older versions of protocols due to the availability of certain features. 
- stratum 2
	- all of the identified stratum 2 servers except for 25 servers are using NTPv2.0, rest are using NTPv3.0

### mode
- the association mode value for all captured packets is 4
- this is because the captured packets are responses from the NTP servers
- NTP servers disseminate the required information using the server association mode, where the system provides synchronization to one or more clients, i.e., acts as a server in the transmission.
- this value is a result of the method of data collection

### precision
- higher precision servers are superior

### poll
- 

### rootdelay
- 

### rootdisp
- 

### refid

### reftime

### org

### rec

### xmt

### dst




