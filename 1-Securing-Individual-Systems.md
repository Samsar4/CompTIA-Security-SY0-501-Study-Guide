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

<p align="center">
<img src="https://upload.wikimedia.org/wikipedia/commons/b/b5/MITM_Diagramm.png" />
</p>

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

## Physical Hardening
**Policies can control how system hardware acts or reacts to an action**.

* Removable media controls

* **Data Execution Prevention (DEP)**
DEP is refer to Windows, in generic term is *Executable space protection*; DEP is almost always on by default on Windows. 

🛑 DEP should be always be on, quietly protecting systems from buffer overflows. **The need to turn off DEP is rare**.

* Disabling Ports (can be done in the BIOS); Turn off legacy non-active ports to avoid vulnerable entry point.

## RFI and EMI
<p align="center">
<img width="60%" src="https://www.precisionmicro.com/wp-content/uploads/2018/10/etched-emi-shielding-header.jpg" />
</p>

### Electromagnetic Interference (EMI)
Is a disturbance generated by an external source that affects an electrical circuit by electromagnetic induction, electrostatic coupling, or conduction.

* Shielded twisted pair (STP) cable.
* Creating a distance between the device generating the EMI, or shield the emanating device or media.

### Radio Frequency Interference (RFI)
RFI is EMI that transmits in the **radio frequency** range. (i.e. 802.11, cellular WAN radio bands)...

* Both 802.11 and cellular WANs almost always have automatic channel-hopping features that automatically tune devices to the least congested channel.

### Electrostatic discharge (ESD)
Discharge of an electrical current through the air, arcing from a point of a relative positive charge to a point of a relative negative charge.

* Protect equipment by shielding it in protective cases
* Only use properly grounded power supplies
* Anti-ESD wrist strap 

## Host Hardening

* **Disabling Unecessary Services**  - i.e. SSH server, Apache server...
* **Default Passwords** - Simply avoid default passwords and use good password methodologies.
* **Disabling Unecessary Accounts** - i.e. Windows default guest account, Duplicate accounts...
* **Patch Management**  
	1. Monitoring patches
		* Might not get reminders
	2. Testing the patches on Sandbox 
	3. Evaluating
	4. Deploying the patch
		* Scheduling
	5. Document what is patched 

### Anti-Malware

* Training for users
* Procedures
	* Best practices
* Monitoring 
* IDS
* Third-party anti-malware tools

### Host Firewalls

* **Whitelist**
	* Defines all the applications a user is allowed to install

* **Blacklist**
	* Blocked programs

## Data & System Security

* Data integrity
* Speed/performance quick access
* High availability

### Solutions to secure data:
#### RAID
* Provides Good integrity
* Provides Good speed
* Affordable

#### Clustering - Distributive allocation
The primary rationale for server clusters is protection against outages and downtime. 
 There are three main reasons for server clustering. They are availability, scalability, and reliability. The key to a protected IT infrastructure lies in redundancy.

* Good method to protect not only Data, but system resources
* Clustering is Expensive

#### Load Balancing
Refers to efficiently distributing incoming network traffic across a group of backend servers, also known as a server farm or server pool.

* Distributes work loads across multiple machines

#### Virtualize the serves 

* Scalability
* High-availability comes from elasticity
* Snapshots 
* Affordable

### Disk Encryption

*Usage:*

* Mobile and Portable devices
	* Laptops, smartphones, tablets

* Desktop Systems with limited security

### TPM - Trusted Platform Module
Microchip built into a computer hardware that is used to store cryptographic information(public/private key). *(i.e **BitLocker** 1.2+)*; The OS relies on this **hardware of root trust** to check for low-level changes at boot up.

*examples of disk encryption TPM and non-TPM:*

* BitLocker (for Windows - TPM)
* PGP Disk (non-TPM)
* TrueCrypt (non-TPM)
* FileVault (for macOS - non-TPM)

🛑 **BitLocker is a built-in Windows Utility Drive Encryption Tool; must have a recovery key to access the data.**

#### Secure Boot - TPM
During the boot process, the TPM and UEFI generate reports about the process and can send those reports to a remote system, like a central authentication server. This process is called **remote authentication** / remote attestation.

### Hardware / Firmware Security

* **Full Disk Encryption (FDE)**
	* i.e. Windows - BitLocker

* **Self-encrypting Drive (SED)**

### Hardware Security Module (HSM)
Is any type of hardware that's designed to do security work. For ATMs, Web Servers, or other applications that perform an unusually high amount of key handling, it's usually a good idea to offload this work to other hardware.

## Secure OS Types

* **Server OS** [RedHat Server, Windows Server etc]
 * Built-in functionality 
 * Connections
 
* **Workstation** [Linux Ubuntu, Windows 10 etc]
	* Desktop version
	* Workhorse

* **Embedded Systems** [Routers, CCTVs etc]
	* Appliance
	* Their own OS

* **Kiosk** [i.e. Big Touch Screens on Museums, Mall etc]
	* Limited function 

* **Mobile OS**
	* Apple iOS
  * Android OS

🛑 *Picking an OS based on least functionality is a good security practice.*


## Secure Peripherals
- Keyboards, USB flash drivers, printers, monitors and so on.

* Patch!
* Disable unecessary ports
* Avoid backdoors

### Bluetooth Security

**Bluejacking** - When bad actors connects with any Device that have Bluetooth enable by default.

**Bluesnarfing** - When the attacker steals data from the target device by connecting to an unsuspecting user's device.

*Types of bluetooth*:

* Class1 is 328' foot 
* Class2 is 33' foot
* Class3 is 3' foot

🛑 *Most Mobile phones and Bluetooth headsets are class2 - range upto 33'*

### 802.11
Many peripherals can connect to an 802.11 network as a host. Printers and multifunction devices (MFDs) are very commonly connected with 802.11.

## Malwares
*Viruses do things to files and propagates, Malware collect keystrokes and information*

#### Virus

* Piece of malicious software
* Attach to other files
* Propagate
* Spread to other devices
* Active

#### Adware

* Web-centric 
* Programs that pop-up unecessary advertisment

#### Spyware

* Hide from system
* Tracking your web brownsing
* Stealing cookies

#### Trojans

* Standalone programs that must be installed **disguised** in programs
* Deliver payload without users knowledge
* Backdoor access

#### RAT - Remote Access Trojan

* Mimic the behavior of legitimate remote control
* Can hide in common 'inofensive' programs like games
* Backdoor access

#### Ransomware - Crypto-Malware

* Uses some form of encryption to lock a user out of a system.
* Usually encrypting the boot drive
* Then forces the user to pay money to get the system decrypted
* Can devastate systems

#### Logic Bomb

* Are triggered by an event *(i.e. erasing file shares or disk storage at a certain time or date)*
* Can devastate systems

#### Rootkit

* Piece of software that escalates privileges to execute other things on computer
* Hard to detect

#### Backdoor

* Piece of software that work on obfuscating an remote access.

#### Polymorphic Malware

* Changes his own code to confuse the digital signature of anti-malware programs
* Hard to detect and destroy

#### Armored Virus

* Design to make harder the detection by anti-malware programs.
* Hard to detect and destroy

#### Keylogger

* Record keystrokes
* Inject scripts


## Analyzing Output

### Anti-Malware
* Almost all anti-malware tools include a point scanner and a mass storage scanner.

### Host-based Firewall
- Inbound rules / outbound rules

* All host based firewalls are basically they exclude everybody, so it is called an **implicity deny** *(not programs gets in or out)*

* The output is really an Access Control List
* Use of Least privilege and whitelisting 

🛑 **False positive** - scan results identify a file that may not actually harm a system or is allowed on the system. (i.e. you just downloaded the Cain & Abel to crack some passwords on your assessment, probably Windows Defender will try to block it out).

### File Integrity Check
Verify the integrity of file is in good order and ready to run. 

**Basically to check if the file isn't:**

* corrupted
* tampered
* version and date

🛑 *To create a file integrity check, you can Generate a hash from source code - checksum. If somebody tamper the file or change from source code, the output hash will be different.*

### Application Whitelisting
Everything about software management, application whitelisting, the main job - it's to make sure that users are running the right applications on each individual systems.

## IDS and IPS

![ips-ids](https://ipwithease.com/wp-content/uploads/2018/01/107-difference-between-ips-and-ids-in-network-security.png)

#### Intrusion Detection Systems (IDS)  

* Lives inside the Network
* Watches within the network traffic
* Sends alerts on suspicious activity

#### Intrusion Prevention System (IPS)

* Active IDS
* IPS is usually close to the edge the network
* Action to prevent will occur at the IPS device

🛑 **IDS: notifies | IPS: acts to stop | Firewall: filters**

## Automation Strategies
*Automation is often used with various scans and updates based on configurable trigger.*

* Repetitive
* Consistent
* Template restoration
* Continuous monitoring network devices (i.e. SNMP)
* Automatic update from OS
* Monitoring host for application whitelists
* Application Development - continuous integration tools like fuzzing, static testing
* Built-in tools vs Shell Scripting to Automate (Powershell(Windows) , Bash(Linux) ..)

## Media Sanitization | Data Destruction 


### Clearing/Clear
Clear means to tell the device through user commands inherent to the massa storage device to sanitize the data. *(i.e. send commands to a hard drive to erase data)*

🛑 Can be done with commands such as erase, format and delete (these methods are not final)

### Purge
Purging will process the device to remove data from the drive, the device might will no longer be usable. Means to use anything other than an internal command to sanitize the data on the media. *(i.e. Degausser: machine with a strong magnetic field that destroys/purge the data from massa storage devices)*

**purge also means that the device is basically not useful anymore**

### Crypto Erase
In case you lost the keys to encrypted device.

### Destroy / Data Destruction
Ruin the media in such a way tha it is no longer functional.

* Mass storage device
* Tape media
* Floppy disks
* Paper

#### Methods:

* Burning
* Pulping
* Shredding
* Pulverizing
