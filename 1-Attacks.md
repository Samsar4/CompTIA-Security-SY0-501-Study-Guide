# Securing Individual Systems 

## Denial-of-Service (DoS)
Prevents others from accessing a system / comprimising the availability.
### Attack Types

* **Volumetric Attack**
  * Ping Flood
  * UDP Flood
* **Protocol Attack**
  * SYN Flood/TCP SYN Attack
* **Application Attack**
  * SlowLoris Attack - *(tries to keep many connections to the target web server open and hold them open as long as possible)*

* **Amplification Attack**
Generate a high volume of packets to flood the target website without alerting the intermediary, by returning a large reply to a small request. The basic defense against these attacks is blocking spoofed-source packets.

* **Smurf Attack** - flooded with spoofed ping messages.

## Distributed-Denial-of-Service (DDoS)
Uses multiple systems to attack a single host - Generally controlled by **BotNets**, which is a type of malware that uses remotely controlled malicious software to control a large range of computers.

## Host Threats
* **Spam**

* **Phishing & Spear Phishing** - The difference between both is that Spear Phishing is for targeted individuals with some type of information about the victim embeded.

* **Spim** - Phishing through instant messaging

* **Vishing** - Unsolicited use of voice to get sensitive information

* **Click Jacking** - malicious click bait sites that forces you type your PII or download some malicious software.

* **Typo squatting** - Mistype URL's (i.e. - facebook.corn)

* **Domain Hijacking** - the act of changing the registration of a domain name without the permission of its original registrant, or by abuse of privileges on domain hosting and registrar software systems.

* **Privilege Escalation**   

## Man-in-the-Middle Attack
* Third-party intercepting between a two-party conversation
* Uses the information to the third party's advantage

* Wireless MITM 
	* 802.11
	* Bluetooth

* Wired MITM
	* Spoof MAC address, IP address, ARP, DNS...

* Typosquatting

* Domain Hijacking

* Replay atack - when an attacker detects a data transmission and fraudulently has it delayed or repeated 

* Downgrade attack - is a cryptographic attack that makes it change the encrypted connection to the older one (i.e. cleartext).

* Session Hijacking - Inject information on middle of connection 

## System Resiliency
Generally they handle risks better, adding technologies and processes to enable the system recovery easily.

### Scalability
Adding more resources to take care the demand (manually added)

### Elasticity
The resources grow on demand as they required (i.e. IaaS)

### Redundancy - Distributed Allocation
*Is a form of distributive allocation.*

* Mass storage
* Redundant systems
* Redundant networks

*You can create more than one copy of non-OS critical data so that if one copy dies, another copy is ready to go to keep the systems up and running.*

### Non-persistance
*Is data that is collected but will not be saved on restart.*

* Snapshots - take the current state of something (i.e binary level) and store. A snapshot reverts to known state.
* Virtualization
* Revert/rollbacks tools - The rollback method bring the system back to a previous state. (i.e. Bad Driver, broken Updated etc).
* Live boot

## RAID - (Redudant Array of Independent Disks) 
Different levels of RAID arrays or combination is for:

* Improve disk access. 
* Improve fault tolerance and data integrity.
* Or both

![raid](https://ipwithease.com/wp-content/uploads/2018/01/img_57f86df8509a6.png)

### RAID 0
* **Has no data integrity.**
* **Improves speed** - data striping(divide the data into pieces in X hard drives); RAID0 speeds up performance but has no integrity, because if one of these hard drives fail, the data is lost.

### RAID 1
* **Has data integrity** - but doesn't have performance ; slow process because the data processed in all hard drives.

### RAID 5 
* **Has disk striping with parity** - parity information is spread across all disks evenly; 1/n of the total disk space available is used for parity. You can only loose one drive and keep the data, the problem is if you loose more than one drive.

### RAID 6
* **Disk parity with double distributed parity** - Same as RAID 5 but has one more parity which you can loos two drives and keep your data safe.

### RAID 0+1  (01)
* **Disk striping with mirroring** - combines both RAID levels 0 and 1 for performance and redundancy; a mirror of two striped arrays.

### RAID 1+0 (10)
* **Disk mirroring with striping** - combines both RAID level 0 and 1 for performance and redundancy; a strip of two mirrored arrays.

🛑 **The most common RAID styles includes 0, 1, 5 and 10.**

🛑 **RAID 1 and RAID 0 requires at least 2 drives.**

🛑 **RAID 5 requires 3 or more drives and RAID 10 requires 4 drives.** 

## NAS and SAN
Storage area networks and network-attached storage both provide networked storage solutions. A NAS is a single storage device that operates on data files, while a SAN is a local network of several devices.

<p align="center">
<img src="https://www.lifewire.com/thmb/w4dk2kMnVAycdG6bCGRmjVShV30=/768x0/filters:no_upscale():max_bytes(150000):strip_icc()/san-vs-nas-818005-v2-5c1042ba46e0fb0001bf6882.png" />
</p>

### Network Attached Storage (NAS)
* Runs over a standard network
* Shows up as normal shares on network
* Good for small environments
* **File-level**


### Storage Area Networks (SAN)
* **SAN runs on block-level storage**
* Fibre Channel (FC) or iSCSI 
* Expensive implementation
