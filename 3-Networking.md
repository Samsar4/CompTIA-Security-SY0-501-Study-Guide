# Networking - Basics 

## Switches
A network switch is networking hardware that connects devices on a computer network by using packet switching to receive and forward data to the destination device. A network switch is a multiport network bridge that uses **MAC addresses** to forward data at the **data link layer of the OSI model.**

<p align="center">
<img width="64%" src="https://cdn.networklessons.com/wp-content/uploads/2014/01/xcisco-smb-vlans.png.pagespeed.ic.O1ruqFKn-i.png)" />
</p>

* Filter & forward data based on **MAC address**
* Where VLANs are set up
* **STP (Spanning Tree Protocol)** prevents bridge loop / loop floods

🛑 **Bridge Loop/Switching Loop** - A switching loop or bridge loop occurs in computer networks when there is more than one Layer 2 path between two endpoints. The loop creates broadcast storms as broadcasts and multicasts are forwarded by switches out every port, the switch or switches will repeatedly rebroadcast the broadcast messages flooding the network.

### VLANs
A virtual LAN is any broadcast domain that is partitioned and isolated in a computer network at the data link layer. LAN is the abbreviation for local area network and in this context virtual refers to a physical object recreated and altered by additional logic.

<p align="center">
<img width="64%" src="https://qph.fs.quoracdn.net/main-qimg-1d62c3cc4e470287ee71383fafe1df66" />
</p>

* Provides layer 2 separation of networks
* **Flood guarding**
	* **STP (Spanning Tree Protocol) - enable**

## Routers
Router is a networking device which helps in routing the data packets between home network & other networks.

<p align="center">
<img width="64%" src="https://geek-university.com/wp-content/images/ccna/how_routers_work.jpg" />
</p>

* Filter & forward based on **IP address** 
* Allocates IP addresses to the devices connected to it using a DHCP server.
* It performs NAT (Network Address Translation)

🛑 *Generally operates in the Network layer*

🛑 A firewall is a piece of software that is commonly run on a gateway router which protects us from the evils of the Internet, so it can forward and filter based on port numbers, based on IP addresses, URL's, all kinds of different stuff. **So we would call this a network firewall because the gateway is running the firewall software** and protecting us from the evil of the Internet.

## Network Topologies - Basics
The actual organization of a network in terms of how is the data moving around and the best way to do it.

### LAN - Local Area Network

* A LAN is a network that has a logical and physical borders that a computer can broadcast

<p align="center">
<img width="64%" src="https://www.geocities.ws/alcantara97/starhttt.gif" />
</p>

### WAN - Wide Area Network

* WAN is a multiple LANs or additional WANs with routing functionality for interconnectivity.

<p align="center">
<img width="64%" src="https://gist.github.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/a3f9b5f3f243467208da83e0d0e543b32233c5d6/wan-topo.jpg" />
</p>


### MAN - Metropolitan Area Network 

<p align="center">
<img width="64%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/f37cec4e00f726cb4be3661f20ccad77751e003a/man-topo.jpg" />
</p>

### Internet
Connecting WANs through WANs until complete the entire world = Internet.

* The protocol which runs the internet is TCP/IP
* As long you're using legitimate IPv4 address or IPv6
<p align="center">
<img width="64%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/8c176b8a798fb5749c4391c45015ee5d14d56f13/internet.png" />
</p>

### Intranet
If you're using the TCP/IP stack and making your own LAN or WAN = Intranet.

* Intranet is a private network which still runs TCP/IP

<p align="center">
<img width="64%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/8c176b8a798fb5749c4391c45015ee5d14d56f13/intranet.png" />
</p>

🛑 **Extranet**: example of some vendor who need to access the Intranet network.

## Network Zones - Concepts

* **LAN** - the core of your network.

* **VLAN** - physical device that designate separate broadcast domains....

* **DMZ** - Demilitarized Zone: Perimeter network, isolating untrusted network from LAN area. DMZ is a firewall configuration used to secure hosts on a network segment, in most DMZs the hosts on the DMZ are connected behind a Firewall that is connected to a public network(internet).

<p align="center">
<img width="80%" src="https://1.bp.blogspot.com/_cbXvML3JELc/TCRH6WvlEvI/AAAAAAAAAGg/7xsnkGmBqo0/s1600/111.gif" />
</p>

* **Wireless Network** - Basically a LAN connected to an Wireless Access Point (WAP).

* **Guest Network** - i.e. Coffee Shop network. 

* **Virtualization** 

* **Airgap** - Simply means a disconnect to provide real isolation and the use of a completely separate internet from the world; Private internet.

## Network Access Controls

* Wireless Network
* Remote Access
* VPN Access

### PPP - Point-to-Point Protocol
In computer networking, Point-to-Point Protocol (PPP) is a data link layer (layer 2) communications protocol between two routers directly without any host or any other networking in between. It can provide connection authentication, transmission encryption, and compression. 

* Transport layer protocol
	* Initiate connection
	* Get address information
	* Make connection

* Poor authentication mechanisms:
	* PAP - password authentical protocol (passwords in the clear)
	* CHAP - Challenge handshake authentication protocol - (use of hashing)

### **EAP** - Extensible Authentication Protocol
Developed initially as an extension to the authentication part of PPP. EAP is only an extension for the protocol that having a connection, and was created as a better authentication method to PPP.

* **EAP - MD5**
	* basically MSCHAP
	* Takes those passwords and hashes them into MD5 hash

* **EAP - PSK**
	* Uses pre-determined symmetric keys
	* Similar to WPA and WPA-2

* **EAP - TLS**
	* Cand handle an entire TLS
	* Needs server and client certificates

* **EAP - TTLS**
	* Uses the TLS exchange method
	* Only requires server certificates

### Protocols that Encapsulates the EAP 

* **802.1X** - Full blown authentication standard that allows us to make connections between some type of client system. It provides an authentication mechanism to devices wishing to attach to a LAN or WLAN. 

* *Early EAP adaptations*:
	* **LEAP** (Cisco) - LEAP is weak nowdays
	* **PEAP** (Microsoft) - PEAP is weak nowdays 

## Network Firewalls - Concepts

### **Stateful** Firewall
Can watch traffic streams from end to end. They are aware of communications paths; Can implement varios IPSec functions (tunnels and encryption); Can tell what stage a TCP connection is in (open, open sent, synchronized SYN ACK or established).

* Are better at identifying unauthorized and forged communications.

### **Stateless** Firewall
They watch network traffic and restrict / block packets based on source and destination address or static values **(ACL Rules)**.

* Typically faster and perform better under havier traffic loads.

### Packet-filtering

* Inspect data packets (drop or forward), such as the destination and originiation IP address, packet type, port number and other surface-level information.

### Circuit-level firewall

* Quickly approve or deny traffic; verify transmission protocol (TCP) handshake (session).

### Application-level Firewall

* Filter traffic based on user group, group membership, application or services (works at layer 7 OSI - also called proxy firewall as well)

## Proxy Servers
A box/piece of software running on a computer acts an intermediary between two different devices having a session. 

* Application-specific
	* Web proxy
	* FTP proxy
	* VOIP proxy

### Forward Proxy
*The proxy simply forward the requests of respective client.*
 
* [Client -> **Proxy** -> Firewall -> Internet -> Server]

* **Hides the client**

* Provides:
	* Caching
	* Content filtering
	* Acts similar to firewall (block based on URL, content filtering and so on).


### Reverse Proxy Server
*Like a forward but complete reverse.*

* [Client <-  Internet <- Firewall <- **Proxy** <- Server]

* **Hides the servers**
	
* Provides
	* High security
	* Protect the servers
	* Handle DoS attacks
	* Load balancing
	* Caching
	* Encryption acceleration

## Honeypots

Emulate a web server, vulnerable machine purposely to attack; Inviting target to keep away from targets. 

* Benefit to see how threat actors, what techniques they're using, what vulnerabilities are they look for, what ports, and so on.

* Log all information (port information and the origin IP address)

* Usually located in the DMZ to get close to the source but still isolated to capture the traffic.

### Honeynet
A honeynet is a vulnerable and **simulated computer network** using a decoy server. **By design, honeynets are not authorized for any authentic uses. If a honeynet is accessed, a fair assumption is that the person accessing it is a bad actor.**

## VPN - Virtual Private Networks 
Organizations use virtual private networks (VPNs) to create an end-to-end private network connection (tunnel) over third-party networks such as the Internet or extranets.
The tunnel eliminates the distance barrier and enables remote users to access central site network resources.
The **IP Security (IPsec) protocol** provides a framework for configuring secure VPNs and is commonly deployed over the Internet to connect branch offices, remote employees, and business partners. Secure site-to-site VPNs, between central and remote sites, can be implemented using the IPsec protocol. IPsec can also be used in remote-access tunnels for telecommuter access.

### The two types of VPN - **Remote Access** and **Site-to-Site**
<p align="center">
<img width="73%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/61b8c0d475d2e4d5dbb31bd9c8b8c25497f9dbf8/vpn+topologies.png" />
</p>

* A **remote-access** VPN is created when VPN information is not statically set up, but instead allows for dynamically changing information and can be enabled and disabled. Consider a telecommuter who needs VPN access to corporate data over the Internet. The telecommuter does not necessarily have the VPN connection set up at all times. The telecommuter's PC is responsible for establishing the VPN, each host typically has Cisco VPN client software. 

* A **site-to-site** VPN is created when connection devices on both sides of the VPN connection are aware of the VPN configuration in advance.

### VPN Setup Steps

1. Protocol to set up tunnel
2. Protocol to handle authentication and encryption

### Early VPNs Protocols

* **PPTP** - Point-to-Point tunneling Protocol
	* Oldest VPN protocol
	* Uses PPP for tunnel
	* Password only
	* **TCP port 1723**
	* Weak encryption

* **L2TP** - Layer 2 Tunneling Protocol
	* Cisco proprietary
	* SImilar to PPTP
	* L2TP tunnel
	* IPsec encryption
	* **UDP ports 500, 1701, 4500**
	* 

* 'Pure' **IPsec**
	* uses IPsec for tunneling and encryption
	* Great for IPv6
	* **UDP ports 500, 4500**

* **SSL** and **TLS**
	* **TCP port 443**
	* Often works within a web browser
	* TUN/TAP (virtual network driver) tunnel
	* TLS encryption

* **OpenVPN**
	* Unique tunnel
	* Encryption based on SSL/TLS protocol
	* **TCP port 1194**, but can be changed 

## IPSec - IP Security
Is a suite of protocols developed to ensure the integrity, confidentiality and authentication of data communications over an IP network.

🛑 IPSec works at the IP layer

### **IPSec Components**

1. **Encapsulating Security Payload (ESP)** – It provides data integrity, encryption, authentication and anti replay. It also provides authentication for payload.

2. **Authentication Header (AH)** – It also provides data integrity, authentication and anti replay and it does not provide encryption. The anti replay protection, protects against unauthorized transmission of packets. It does not protect data’s confidentiality.
<p align="center">
<img width="69%" src="https://media.geeksforgeeks.org/wp-content/uploads/newb.png" />
</p>

3. **Internet Key Exchange (IKE)** – It is a network security protocol designed to dynamically exchange encryption keys and find a way over Security Association (SA) between 2 devices. The Security Association (SA) establishes shared security attributes between 2 network entities to support secure communication. **The Key Management Protocol (ISAKMP) and Internet Security Association which provides a framework for authentication and key exchange.** ISAKMP tells how the set up of the Security Associations (SAs) and how direct connections between two hosts that are using IPsec.

<p align="center">
<img width="69%" src="https://media.geeksforgeeks.org/wp-content/uploads/1212-2.png" />
</p>

### **Tunnel Mode and Transport Mode**
When IPsec protects traffic, it has a couple of services and modes to choose from.

**Transport mode** - preserving original IP header. Typically used in combination with GRE or other encapsulating protocols. (Host-to-Host)

**Tunnel mode** - encapsulating entire IP datagram within a new header, essentially tunneling the packet. (The gateway creates the tunnel)

1. *Some TCP data will be sent over:*
<p align="center">
<img width="69%" src="https://community.cisco.com/legacyfs/online/legacy/5/1/2/166215-Screen%20Shot%202013-11-12%20at%2011.52.30%20AM.png" />
</p>

2. *And now about how those IP protocols fit in the two modes.*
<p align="center">
<img width="69%" src="https://community.cisco.com/legacyfs/online/legacy/6/1/2/166216-Screen%20Shot%202013-11-12%20at%2011.52.17%20AM.png" />
</p>

The last mode is what is typically used with crypto map based IPsec VPNs.

#### Use of IPSec

* **VPNs**
	* Pure IPsec (using tunneling mode)
	* IPSec with L2TP (add a tunnel layer)

* **RADIUS and TACACS+**

* **IPSec with IPv6**

* **Using IPSec with Non-security protocols / Encrypting Unsecured Protocols**
	* i.e. IPsec over Telnet

## NIDS and NIPS
**Network Intrusion Detection Systems (NIDs)** and **Network Intrusion Prevention Systems (NIPS)** look at attacks coming into the network at large instead of into a host. Attacks could be in the form of malformed network traffic or excessive amounts of traffic.

### Prevention vs Detection
**NIDS** is a **passive** device and focuses on detection alone, making it a **detection control**. It detects network traffic issues and alerts and administrator to these issues, also logging the events in the process.

**NIPS** is /**inline**(Active) device and focuses not only on detecting network attacks, but preventing them. (block things from router)

### Detection
NIDS/NIPS solutions act very much like firewalls in that they inspect packets. 

**There's 4 types of detection methods:**

* **Behavioral/Anomaly** - Comparing traffic with a baseline of patterns considered normal for the network
* **Signature** - Preconfigured Signature-based
* **Rule** - Preconfigured rules in a ruleset - like firewall
* **Heuristic - (Anomaly and Signature)**

### Sensors: In-band & Out-of-Band

#### NIPS
* NIPS sensor must be installed **in-band** to your network traffic

<p align="center">
<img width="73%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/a2fc0101b75e32a25150d516dcef9e8a9ef5ad86/NIPS.png" />
</p>

#### NIDS
* NIDS sensor, being **passive**, is normally installed **out-of-band**

<p align="center">
<img width="73%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/a2fc0101b75e32a25150d516dcef9e8a9ef5ad86/NIDS.png" />
</p>
	
### Devices
#### Network Tap
Is a device that you can insert anywhere along a run to grab packets.

#### Port Mirror
Also called a Switch Port Analyzer, or SPAN in Cisco Devices, is a special port on a managed switch configured to listen for all data going in and out of the switch. Unlike a network tap, port mirroing is convenient and easily changed to reflect any changes in your NIDS/NIPS monitoring stragegy.


## SIEM - Security Information and Event Management
SIEM tools aggregate and correlate data, allowing you to organize it into valuable information. You can get to the time sequence of an event in all the logs quickly, have alerts and the ability to notify you based on a configurable trigger.

* **Aggregation** - Collecting data from disparate sources and organizing the data into a single format. Any device within a SIEM system that collects data is called collector or an aggregator.

* **Correlation** - is the logic that looks at data from disparate sources and can make determinations about events taking place on your network. (could be in-band or out-of-band, depending on the placement of the NIDS/NIPS)
	* Alerts - for notification if something goes bad
	* Triggering - Exceeding thresholds

* **Normalization** - will actually create multiple tables / organize in such a way that the data can become more efficient and allows our analysis and reports tools to work better.

* **WORM - Write Once Read Many**: The concept being is that log files are precious, and a lot of times you might want to look at them in an archival way, so that we can use optical media like WORM drives to store them.

#### Tools

* **Splunk**
* **ArcSight**
* **ELK - Elastic Search, Log Stash and Kibana (openSource)**

# Networking - Part 2 

### 802.11

*IEEE 802.11 is part of the IEEE 802 set of LAN protocols, and specifies the set of media access control (MAC) and physical layer (PHY) protocols for implementing wireless local area network (WLAN) Wi-Fi computer communication in various frequencies, including but not limited to 2.4 GHz, 5 GHz, and 60 GHz frequency bands.*

![80211](https://steemitimages.com/p/X37EMQ9WSwsMfHTdm8pfEYwuZbTCWFHqXbdDf3mYpu7MPCSF4g1H91WdvbEPreHqYfn7wJWqACH9w9uZtcuSAd6cDn1sAibTMxevS?format=match&mode=fit)

## **Wireless Access Point (WAP) - Concepts**

* Wireless Access Point is a Bridge between **802.11** and **Ethernet**.
* Every WAP have MAC address
* **SSID (Service Set identifier)** associated to the MAC address on a WAP is known as **BSSID - (Basic Service Set Identifier)**
* When a large network is connected multiple WAP's through a **Common Ethernet Broadcast Domain** - turns out **ESSID - (Extended Service Set Identifier)**

### **WEP** - Wireless Equivalency Privacy

* 64/128 bit RC4 ICV 

**RC4** - Rivest Cipher 4 Stream Cipher Algorithm<br>
**ICV** - Integrity Check Value

🛑 *Very old and insecure.*

### **WPA** - Wi-Fi Protected Access

* Enterprise
	* TKIP + RADIUS
	* 64/128 bit RC4 MIC

* Personal	
	* TKIP + PSK
	* 64/128 bit RC4 MIC

**TKIP** - Temporal Key Integrity Protocol<br>
**PSK** - Pre-Shared key<br>
**MIC** - Message Integrity Check<br>

### **WPA2** - Wi-Fi Protected Access v2

* 802.11i IEEE standard

* Enterprise
	* CCMP + RADIUS
	* 128 bit AES MIC 

* Personal
	* CCMP + PSK
	* 128 bit AES MIC

**CCMP** - Cipher Block Chaining Message Code Protocol<br>
**AES** - Advanced Encryption System

## Vulnerabilities - WAP
-
