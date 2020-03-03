# Tools of Trade

## OS Utilities - Command Line (Linux & Windows)

### ping
can be handful for DNS checks (up / or down) | is a DNS tool to resolves web addresses to an IP address.

```sh
ping www.google.com 

PING www.google.com (172.217.168.164): 56 data bytes
64 bytes from 172.217.168.164: icmp_seq=0 ttl=55 time=25.981 ms
64 bytes from 172.217.168.164: icmp_seq=1 ttl=55 time=25.236 ms
--- www.google.com ping statistics ---
2 packets transmitted, 2 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 25.236/25.608/25.981/0.373 ms
```
🛑 In Windows you need to add a **-t** flag to keep running.

**Most useful switches for Ping command - Windows:**

Switch | Description
--|--
**-a** | Resolve address to hostnames
**-f** | Set don't fragment flag in packet (IPv4 only)
**-4** | Force using IPv4
**-6** | Force using IPv4


### netstat
get info on host system TCP / UDP connections and status of all open and listening ports and routing table.

* Who you talking to? 
* Who trying talking to you? 

```sh
netstat -a (server)
netstat -n (host)
```

### tracert | traceroute
traceroute - how packets get from host to another endpoint. Traceroute is helpful to see what routers are being hit, both internal and external.

* tracert - Windows
* traceroute - Linux

### arp 
address resolution protocol - caches of ip-to-ethernet


### ipconfig (Windows)
show all IP configuration on Windows-only systems.

**Useful switches:**

Switch | Description
--|--
**/all** | Exhaustive listing of virtually every IP and Ethernet setting (MAC address etc)
**/release** | Release the DHCP IP address lease
**/renew** | Renews the DHCP IP address lease
**/flushdns** | Clears the host's DNS cache
**/displaydns** | Displays the host's DNS cache

### ifconfig
equivalent to ipconfig for UNIX/Linux OS.

### iwconfig 
similar to ifconfig, but is dedicated to the wireless network interface.

### ip addr
show / manipulate routing, network devices, interfaces and tunnels.

Show all the ip configuration, mac address, ipv6 etc.

### nslookup
query Internet name servers interactively; check if the DNS server is working

```sh
nslookup www.certifiedhacker.com

output:
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
www.certifiedhacker.com canonical name = certifiedhacker.com.
Name:   certifiedhacker.com
Address: 162.241.216.11 inslookup www.certifiedhacker.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
www.certifiedhacker.com canonical name = certifiedhacker.com.
Name:   certifiedhacker.com
Address: 162.241.216.11

```

### dig 
DNS lookup tool - Functions like nslookup, but allows for further functionality.

```sh
dig www.certifiedhacker.com

output:
; <<>> DiG 9.11.14-3-Debian <<>> certifiedhacker.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15708
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 2048
; COOKIE: 70bd915b07b3fd08757c9ad65e5d6f3e549d5787b59e97cb (good)
;; QUESTION SECTION:
;certifiedhacker.com.           IN      A

;; ANSWER SECTION:
certifiedhacker.com.    14400   IN      A       162.241.216.11

;; Query time: 419 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Mon Mar 02 15:40:29 EST 2020
;; MSG SIZE  rcvd: 92

```

### netcat
TCP/IP swiss army knife; you can make any type of connection and see the results from a command line. With nc you can connect to anything on any port number or you can make your system listen on a port number. Can be an agressive tool for recon.

## Network Scanners
**Useful for collect and inventory the hosts on a network, and is useful for reconnaissance of your system.**

### Nmap
The Best way to query a system to check if they have open ports, services, system versions, service versions etc.

*Zenmap is a GUI version of Nmap.*

```sh
nmap -v -A -T5 scanme.nmap.org 

...
PORT      STATE SERVICE    VERSION
22/tcp    open  ssh        OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 ac:00:a0:1a:82:ff:cc:55:99:dc:67:2b:34:97:6b:75 (DSA)
|   2048 20:3d:2d:44:62:2a:b0:5a:9d:b5:b3:05:14:c2:a6:b2 (RSA)
|   256 96:02:bb:5e:57:54:1c:4e:45:2f:56:4c:4a:24:b2:57 (ECDSA)
|_  256 33:fa:91:0f:e0:e1:7b:1f:6d:05:a2:b0:f1:54:41:56 (ED25519)
80/tcp    open  http       Apache httpd 2.4.7 ((Ubuntu))
|_http-favicon: Unknown favicon MD5: 156515DA3C0F7DC6B2493BD5CE43F795
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.7 (Ubuntu)
|_http-title: Go ahead and ScanMe!
9929/tcp  open  nping-echo Nping echo
31337/tcp open  tcpwrapped
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
...

```

## Angry IP Scanner (GUI) - for Windows
Does a good job using simple protocols, mainly ping, to query a single IP address or an address range. 

## Protocol Analyzers
**Protocol Analyzers collect and inventory the network traffic.**

**Sniffer** - Some type of software that grab all the data that is going in and out of particular interface. 

### Why Protocol Analyze?
* Count all the packets coming through over a certain time period to get a strong ideas to your network utilization.
* Inspect packets for single protocols to verify they are working properly.
* Monitor communication between client and a server to look for problems.
* Look for servers that aren't authorized on the network.
* Find systems broadcasting bad data.
* Find problems in authentication by watching each step of the process.

### Wireshark
Wireshark is the world’s foremost and widely-used network protocol analyzer. It lets you see what’s happening on your network at a microscopic level.

*With Wirehsark you can inspect and detect ARP poisonings, Rogue DHCP servers, Broadcast Storm etc.*

🛑 Broadcast Storm - when a NIC (or port on a switch) sends large amounts of broadcast traffic, thereby crippling network resources.

### tcpdump
Another popular protocol analyzer option for UNIX/Linux.

## SNMP - Simple Network Management Protocol
Simple Network Management Protocol (SNMP) is an Internet Standard protocol for collecting and organizing information about managed devices on IP networks and for modifying that information to change device behavior. Devices that typically support SNMP include cable modems, routers, switches, servers, workstations, printers, and more.

* SNMP v1 - does not support encryption
* SNMP v2 - added basic encryption
* SNMP v3 - added TLS encryption  

**SNMP uses Port 161**

## Logging
There are two types of events (Network and Non-network events).

### Non-Network Logs
* Operation System Events
	* Host starting
	* Host shutdown
	* Reboot
	* Service starting, stopping, and failling
	* OS Updates

* Applications Events
	* Application Installation
	* Application starts, stops or crashes

* Security Events
	* Logons
	* Logons successes and failures

**Generic Log Structure:**
* Date and Time
* Process/Source/ID
* Account associated/System
* Event Number
* Event Description
* Network Logs

### Network Events

* O.S. / System-Level
	* Remote logon fail/not
	* Events on Shared Applicaton/Resources
		* Activity on Web Server (i.e. Apache)
		* Activity on Firewall

* Application-Level

### Centralized vs Descentralized Log Management
**Descentralized log management** - In environments such as very small networks and don't have large infrastructure or in isolated network segments, descentralized log management is usually the norm.

**Centralized log management** - means that the log files from different machines are automatically sent to a centralized logging facility or server, such as a syslog server, administrators review logs from a centralized loogging facility on the network. Enterprise correlate them into one unifed management interface, so the administrator can look for trends or events.

### Centralized
* Uses a Central repository
	* Drag on system
* Use SNMP Systems
	* Pulls informaton needed and generates graphs and charts

🛑 Monitoring-as-a-Services (MaaS)


### SIEM - Security Information and Event Management
Collects data points from network, including **log files, traffic captures, SNMP messages, and so on**, from every host on the network. **SIEM can collect all this data into one centralized location and correlate it for analysis to look for security and performance issues, as well negative trends all in real time.**


### Continuos Monitoring
Is a proactive way of ensuring that the network administrator receives all the different logs and other data points throughout the network from all network devices and all systems, on a constant basis. This data is continually fed into.

### Auditing
Important part of ensuring accountability on the network. Examines the logs and other data points of certain events and construct a time frame and event sequence surrounding an incident.

Auditing also consists of other activities, such as:
* Performing Network Sniffing traffic analysis
* Password Cracking
* Vulnerability Assessment
* Penetration Test
* Compliance Audits

🛑 *Auditing can reveal weak security configurations*

### Trend Analysis
Enables network administrator to correlate different data sources and data points from various places in the network, such as log files, IDS logs, wireless and wired sniffing as well as other event sources, and seek to identify on-going trends in both performance and security. The goal is find patterns that can indicate a emerging issue.
