# Networks and Infrastructure - Basics 

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

### **PPP** - Point-to-Point Protocol
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

### **Forward Proxy - Client**
*The proxy simply forward the requests of respective client.*
 
* [Client -> **Proxy** -> Firewall -> Internet -> Server]

* **Hides the client**

* Provides:
	* Caching
	* Content filtering
	* Acts similar to firewall (block based on URL, content filtering and so on).


### **Reverse Proxy - Server**
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
	
### **Devices**
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

# Network - Part 2, Beyond the Basics 

### **802.11**

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

* **802.11i** IEEE standard

* Enterprise
	* CCMP + RADIUS
	* 128 bit AES MIC 

* Personal
	* CCMP + PSK
	* 128 bit AES MIC

**CCMP** - Cipher Block Chaining Message Code Protocol<br>
**AES** - Advanced Encryption System

## Vulnerabilities with Wireless Access Points

### **Rogue Access Point**
**Unauthorized** access point plugged into a wired one. *(Can be accidental)*

### **Evil Twin Attack**
Is a Rogue AP tha is broadcasting **the same (or very similar) SSID**. 

### **802.11 Jammer**
**Jamming is a form of intentional interference on wireless networks, designed as a DoS attack**. This type of attack by overpowering the signals of a legitimate wireless AP, typically using a rogue AP with its transmit power set to very high levels.

### **Deauthentication Attack**
Deauthenticates clients from the network to grab the authentication information performing a man-in-the-middle attack.

## Cracking WEP, WPA, WPA2 and WPS

### **WEP**
* **IV Attack** - Initialization Vector is vulnerable to cracking.
	* Aircrack can grab WEP keys and crack them.
* WEP is the oldest security standard 802.11

### **WPA/WPA2**
* WPA/WPA2 uses 4-way handshake
* WPA is vulnerable to a dictionary attack
* Can be cracked at the initial connection between the WPA/WPA2 client and the access point during the 4-way handshake
* Aircrack can grab WPA handshakes on authentication time and crack the PSK's (if they are common/weak).

### **WPS**
*Wi-Fi Protected Setup (WPS) - is a push button configuration, which enables the router WPS enable to another WPS device (wireless printers are the most common).*

* 8 digit key is actually only 7 digits, 2^7
* Key exchange is the first processed in 4-bit and 3-bit
* Can be cracked using Reaver
* *The new generation of WPS enabled device can detect an attack and shut off.*
* **WPS Attack Prevention**:
	* Get rid of older routers
	* Firmware updates
	* Upgrade to newer wireless routers

## Hardening 802.11 Networks
* Survey installation issues
* Maintaining existing wireless networks
* Monitoring 
* Define how to defend wireless clients

### Site Survey & Installation
* **Survey Tools**
	* Find SSIDs
	* Find MAC addresses
	* Band, channels, and signals
	* Document everything around 802.11 device

* **Maintanance Wireless Networks**
	* Good Documentation
		* SSIDs
		* MAC addresses associated to
			* WAPS
			* AP locations
			* Heatmaps
	* **Scanning**

* **WIDS** - Wireless Intrusion Detection System - *listen to what is going on inside the wireless network and help detect potential threats, or any abnormality.*
	* Monitors wireless radios
	* Watches for rogue access points
	* Knows MAC address of authorized equipment
	* Watches working protocols

* *Good Practice:*
	* AP isolation enabled 
	* 802.1X is more robust

## Fat vs. Thin Access Points

### Thick Client
* Good for small environments 
* Management console to configure security controls
* ACLs
* White/black listing
* Encryption
* Manage individually
* Also called controller-based AP

### Thin Client
* Good for big environments. *(i.e A building with multiple floors and hundreds of users might rely on one good switch (with a redundant backup) to control dozens of thin access points)*
* Act as a repeater taking the wireless signal and pushing it ot a managed access control (AC) switch that handles encryption and other security. Also called **Standalone AP**

## Antenna Types
Higher dB = better

* Omnidirecitonal
	Signals goes on every direction. 
* Dipole
* Directional
	* Long individual beam  
* Patch Graphic
	* Half Omni (i.e stick to the wall the get one side signals)

### Antenna Placement Examples
*Antennas should be centrally located throughout different areas of the facility so that hey can adequately span all areas of coverage within a facility, without being too close to exterior walls or the roof whenever possible.*

* Stadium like = **Omnidirectional Antenna**
* Outdoors = **Dipole Antenna**
* Shooting long distances *(one building to another)* = **Directional Antenna**

## Band Selection - 2.4 vs 5 GHz
The higher the frequency of a wireless signal, the shorter its range. **2.4 GHz wireless networks, therefore, cover a larger range than 5 GHz networks. In particular, signals of 5 GHz frequencies do not penetrate solid objects as well as 2.4 GHz signals, and this limits the reach of 5 GHz frequencies inside homes.**

### **2.4 GHz**
* Longer range
* Penetrate walls easily

### **5 GHz**
* Faster choice
* Automated channels
* Wider Channels = better

## Virtualization - Concepts
* Virtual version of host hardware
* Multiple virtual servers on one box/physical device
* Hardware consolidation and reduced energy consumption
* System Recovery

### Types
* **Type 2** - Runs on top of host OS
* **Type 1** - Runs directly on top of hardware, independent of host OS. *(i.e bootable Linux thumbdrive)*
* **Cloud-based Virtualization**
	* IaaS (i.e. AWS, MS Azure)

### Virtualization Benefits
* Security Feature
* Patch management
* Centralized hardware maintenance
* Resilient and high availability
* Great for testing everything and sandboxing environment
* Snapshots and backups 
* Network Separation

### Virtual Threats 
* VM sprawl - the out-of-control creation of VMs outside of security controls.
* VM escape - when a user inside a VM finds a way to break out the VM and get into the underlying hypervisor/host OS.

### Virtualization Hardening
* Remove remnant data
* Make good policies 
* Define user privileges
* Patch everything!
* CASB - Cloud Access Security Brokers: Intermediary between your infrastructure(in-house stuff) and the cloud; Make sure policies are controlled; watches for malware; 

## Containers
* Containers are self-contained applications that can communicate with network resources that have been explicity allowed
* Runs isolated instances of programs and services
* Can depend on each other, and can be configured to communicate with each other on a single host
* Runs a single program and all its dependencies, when the programs exists

## IaaS - Infrastructure-as-a-Service
* Basically virtual machines hosted by a cloud provider's infrastructure; Users simply connect to them via RDP (remote desktop protocol) or another secure remote connection protocol and use the as they would any other computer.
	* *i.e: AWS, Microsoft Azure, Digital Ocean, Google Cloud.*

## PaaS - Platform-as-a-Service
* Offers a computing platform, such as Web application server or database server with easy setup focusing on quick deployment; Enables you to access a software development platform without the need to host it yourself.
	* *i.e: Heroku*

## SaaS - Software-as-a-Service
* SaaS is a subscription based license; Access applications via subscription; 
	* *i.e: Microsoft Office 365, Dropbox storage, Google Docs*

## Cloud Deployment Models

* Private Cloud 
	* A group of virtual machines that only the organization can access.

* Public Cloud
	* Amazon S3, Microsoft Azure - Open for business

* Community Cloud
	* Is make up of infrastructure from several different entitites wich may be cloud providers, business partners, and so on. (members only type of thing)

* Hybrid Cloud
	* Any combination of the cloud models described above

* Virtual Desktop Environment (VDE)
	* Remote Access to a Remote System that **is not virtualised**

* Virtual Desktop Integration (VDI)
	* The actual virtualized environment in the cloud

## Static Hosts - Concepts
*Intelligent device designed to do a specific task or process*
* WAP
* Switch
* Router
* Printer

* **ICS** - Industrial Control Systems	
	* HVAC - Heating Ventilation, and Air Conditioning

* **SCADA** - Supervisory Control and Data Acquisition
	* Pretty much ICS with more funcionality

### Securing Static Hosts

* Change default passwords
* Turn off unnecessary services
* Monitoring security and firmware updates
* **Defense in depth**
	* Network Segmentation - VLANs with Firewalls; VPN to connect a pipeline securely.

## Mobile Connectivity

* **SATCOM** - Sattelite communication phone
* **Bluetooth**
* **NFC** - Near Field Communication: Almost/Physical contact with another device *(there's no security envolved when activated)* - Easy connection
* **ANT/ANT+** - Very simple form of wireless communication; slow and protected; (i.e Odometers, Heart Rate Monitors, Bikes)
* **Infrared** - Most Androids, communication Transmitter.
* **USB**, USB OTG (On-the-Go) 
* **Wi-Fi** and **Tethering**
	* ADHOC, Wi-Fi Direct (Easy connection)
	* Tethering - Wired and Wireless Tethering: acts like a router

## Deploying Mobile Devices

### **COBO** - Corporate Owned, Business Only
* Company owned
* Company devices what to do with that device
* What applications are on that device
* What encryption is used?
* What wireless is connected?

### **COPE** - Corporate Owned, Personally Enabled 
* Everyone has the same device
* Great control because everyone has same device on environment
* People will still want to use their own devices
* Learning curve

### **CYOD** - Choose Your Own Device
* Users get to choose from a list af approved devices
* Less of learning curve

### **BYOD** - Bring Your Own Device
* User get to choose to bring their own devices, based on their experiences
* Learning curve is decreased
* Very heavy device management
* Mobile application management

## Mobile Enforcement

### Sideloading
Installation of third-party applications that is different from original Application Store (Google Play, Apple Store)

### Carrier Unlocking

### Rooting/Jailbreaking
* Root Access
	* Install custom firmware
	
* Root Access Issues
	* Auto updates disabled
	* Trouble accessing the store
	* Exposure to malware

### Things to Avoid on Mobile
*To achieve this topics you will need a good policy*

* Firmware OTA updates (over-the-air) - turn off
* Camera use - can be use to take pictures of confidential information etc.   
* SMS/MMS - high cost
* External Media 
* Recording Mic/GPS tagging
* Payment Methods - when your bank account is connected to the phone

## Mobile Device Management - MDM

* **Content Management**
	* Applications Management
	* Databases
	* Documents

* **Geolocation**
	* Knows the location of that device

* **Geofencing**
	* Geolocation with geographic trigger

* **Push notification services**
	* Applications will push notifications if you want 

* **Passwords and PINs**
	* Require use of passwords and PINs
	* Can recover passwords

* **Biometrics**
	* Fingerprints
	* Facial Recognition
	* Vocal Recongnition
	* Can lock and unlock devices
	* Use to configure applications

* **Screen Locks**
	* Make sure your screen is locked

* **Remote Wipe**
	* Great when the device is lost

## Mobile Application Management - MAM
* Versioning
* Updates
* Patches

### Context-aware authentication
* Where are they right know?
* What OS are they using?
* What time/day are they trying to authenticate?

### Storage segmentation
* Dedicating a storage space for our applications

### Full Device Encryption
* Encrypt the entire storage of the device

🛑 - *Some companies provides **MDM solutions** (i.e Google - Android: What applications people can install, security policies and so on)* 

## Physical Controls

### **Deterrent** Physical Controls
* Outside light, Parking Lot Lighting
* Signage (i.e Restricted Area)
* Security Guards

### **Preventive** Physical Controls
* **External**
	* Fences, Gates, Barricades, K ratings(designed to stop vehicles)
	* Mantrap (some type of entry system, consisting of 2 doors)
	* Cabling systems - (Using AirGap ; VPNs or VLANs)
* **Internal**
	* Safe for Important documents
	* Locked cabinets
	* Faraday cages - to protect sensitive eletronic equipment
	* Locks
		* Key management system (where the keys are stored? who is in possession of those keys?...)

* Individual Workstation
	* Cable Locks
	* Screen filters

### **Detective** Physical Controls
* Alarms
* Cameras
* Motion detectors
* Infrared detectors
* Log Files - can be important in terms of tracking

### **Compensating & Corrective** Physical Control
Temporary fixes when these controls are weakened.<br> *i.e - If the outside fence in some way got a big hole, you need to place a security guard on that location until the fences got fixed.*

## HVAC - Heating, Ventilation, and Air Conditioning
* Office Environment - room temperature, humidity
* Server Rooms - Super sophisticated HVAC's systems; Make sure keep cool and dry

* **Infrared Camera** - we can determine heats more easily

![infrared](https://www.castlerockinspections.com/DataCentIR_1.jpg)

* **Zone-based HVAC**

* **Hot & Cold aisles** - Used in server rooms, HVACuse either hot and cold aisles a contained system to vent hot air out and away from ther server racks; Layout of data centers inteligently and efficiently. Aisles of equipment racks are set up such that there are alternating hot and cold aisles. 

🛑 - MAC filtering is a good idea on system controllers of HVAC

* **Remote Monitoring** - VPN access, 802.1X

## Fire Suppression
### Types of Fires and Appropriate Fire Extinguishers

Class | Type | Contains 
--|--|--
A | Ordinary(Wood, Paper) | Foam, Water
B | Liquids(Gases, oil) | CO2, Foam, Powder
C | Electrical (eletronic equipment) | CO2
D | Combustible metals (sodium, magnesium) | Powder

🛑 FM200 is a special extinguisher liquid that is great because it can stops fires, but can still save the electrical equipment; "Gold Standard" for fire suppression on server rooms.

🛑 Class C is best extinguisher for suppress fire on Server Room, but it may ruin some electronics due to the corrosive powder inside.
