## Index

1. Threats, Attacks and Vulnerabilities
1. Technologies and Tools
1. Architecture and Design
1. Identity and Access Management
1. Risk Management
1. Cryptography and PKI


# Introduction
Information security, sometimes shortened to infosec, is the practice of protecting information by mitigating information risks. It is part of information risk management. It typically involves preventing or at least reducing the probability of unauthorized/inappropriate access, use, disclosure, disruption, deletion/destruction, corruption, modification, inspection, recording or devaluation, although it may also involve reducing the adverse impacts of incidents.

## Goals of Security 

The CIA triad is put into pratice through various security mechanisms and controls. Every security technique, practice, and mechanism put into place to protect systems and data relates in some fashion to ensuring confidentiality, integrity, and availability.

<p align="center">
<b>The CIA Triad</b>
</p>
<p align="center">
<img width="50%" src="https://cyberdirective.com/wp-content/uploads/cyberdir/CIATriad-300x261.png" />
</p>

### **Confidentiality**: 
Keeping systems and data from being accessed, seen, read to anyone who is not authorized to do so. 

### **Integrity**: 
Protect the data from modification or deletion by unauthorized parties, and ensuring that when authorized people make changes that shouldn't have been made the damage can be undone.

### **Availability**:
Systems, access channels, and authentication mechanisms must all be working properly for the information they provide and protect to be available when needed.

**Note: In addition, other properties, such as authenticity, accountability, non-repudiation and reliability can also be involved. (ISO/IEC 27000:2009)**

### **Auditing & Accountability**
Basically keep tracking of everthing, like, who's been logging in when are they loggin in whose access this data.

### **Non-Repudiation**
Anyone can validate the authenticity of a message as well as the source of the message.
***
***
***

# 2. Tools 

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

***
***
***
# 4) Identity and Access Management

## Identification and AAA
Identification, authentication, authorization, and accounting work together to manage assets securely.

### **Identification**
The information on credentials identifies the user.

### **Authentication**
* **Authentication Factors:**
  * Something you **know** (password)
  * Something you **have** (smart card)
  * Something you **are** (fingerprint)
  * Something you **do** (android pattern)
  * **Somewhere** you are (geolocation)
  * *Multi-factor authentication generally uses two of this examples (Something you Know and Something you Have), never on same category*
* **Trusts and Federated Authentication**:
   * **Trust Relationship** - Active Directory DS
   * **Transitive Trust** - The organization trusts another entity because they are trusted by someone else that the organization trusts.
   * **Federated System** - Common authentication and credentials database that multiple entities use and share. (Active Directory: Different Domains could be used in other domains in the same forest).

### **Authorization**
* **Permissions**: Applied to resources
* **Rights** / **Privileges**: Assign at system level 
* **Authorization strategies**:
  * Least privileged
  * Separation of Duties

### Authorization Models

* **Mandatory Access Control (MAC)**:
	* Labelling
	* Used on old systems (i.e. Top Secret Gov. information)
* **Discretionary Access Control (DAC)**:
	* Owner of the data defines access
	* Roles
* **Role-based Access Control (RBAC)**:
	* Access to resources is defines by a set of rules
	* by Groups (i.e. Admin Groups --> Rights and Perms | Sales Group --> Rights and Perms)

#### 🛑 Access is defined by **ACL, Access Control List**.
#### 🛑 **Implicity deny** prevents access unless specifically permitted.

## Password Security
* **Complexity**
	* Length and character requirements

* **Expiration**
	* Reset and time triggers

* **Password history**
	* Reusage and retention

### Password Security
#### Password Policy (Local Security Policy - Windows)
* **Enforce Password History**: determine the number of new unique passwords [1-24]
* **Maximum Password Age**: Password age [1-999 days] 
* **Minimum Password Age**: Limit until request password change [1-998 days]
* **Maximum Password Lenght**: [1-20 characters]
* **Password Complexity:**
	* Not contain user account name or parts of full name
	* At least 6 characters lenght
	* At least three of four categories:
		* Uppercase [A-Z]
		* Lowercase [a-z]
		* Base 10 digits [0-9]
		* Non-alphabetic characters [!,@,#,$,...]

#### Account Lockout Policy
* **Account Lockout Duration**: Time (in minutes) for a locked-out account [0-99,999]
* **Account Lockout Threshold**: Number of failed logon attempts [0-999]
* **Reset Account Lockout Duration**: Period of time that must elapse before the account lockout counter is reset to 0 bad logon attempts. [1-99,999]

### Group Policy Objects (AD DS)
Set of rules that allow an administrator granular control over the configuration of objects in Active Directory, including user accounts, operation systems, applications and other AD objects. Can apply over multiple domains, groups and OU's.

## Linux - File Permissions

Linux has three permissions and they can be set for the owner, group or other.

**r = read** - open a file, view a file.<br>
**w = write** - edit a file, add or delete files for directories.<br>
**x = execute** - run a file, execute a program or script, CD to a different directory.<br>


Owner | Group | Other
--|--|--
rwx | rwx | rwx

* Viewing the permissions on Linux command-line:

```sh
ls -l
-rwxrwxr-x 1 user user 31337 Feb 11 13:13 File
```

### Using `chmod` - to change file modes or Access Control Lists 
* Clear out the permissions of the **File** to have no read, write and execute permissions on **Other**:<br> *(The flag equals to nothing[o=] deny the permissions)*

```sh
ls -l
-rwxrwxr-x 1 user user 31337 Feb 11 13:13 File

chmod o= File

ls -l
-rwxrwx--- 1 user user 31337 Feb 11 13:13 File
```

* Giving **read** and **write** permissions to **Group**:

```sh
ls -l
-rwx---r-- 1 user user 31337 Feb 11 13:13 File

chmod g=rw File

ls -l
-rwxrw-r-- 1 user user 31337 Feb 11 13:13 File
``` 

* Giving **all permissions** to everybody(Owner,Group and Other):

```sh
ls -l
-rwx---r-- 1 user user 31337 Feb 11 13:13 File

chmod a=rwx File

ls -l
-rwxrwxrwx 1 user user 31337 Feb 11 13:13 File
``` 

### Using `chmod` on oldschool way:
The chmod command will take the octal value and combine them to associate the permissions on three different positions for the Owner, Group and Other/Everyone. This boils down to a simple binary rule: 0 = off | 1 = on.

Octal | Binary | Permissions
--|--|--
0 | 000 | ---
1 | 001 | --x
2 | 010 | -w-
3 | 011 | -wx
4 | 100 | r--
5 | 101 | r-x
6 | 110 | rw-
7 | 111 | rwx

*If you want to give all permissions to a group for example, the number will be 7 (4 + 2 + 1).*

Read | Write | Execute
--|--|--
r-- | -w- | --x
4 | 2 | 1

#### Examples:

* Giving **read, write and execute** permission to everybody:

```sh
ls -l
-rwx---r-- 1 user user 31337 Feb 11 13:13 File

chmod 777 File

ls -l
-rwxrwxrwx 1 user user 31337 Feb 11 13:13 File
``` 

* Giving all permissions to the **owner**, read and write to **group** and no permissions to **other/everyone**:

```sh
ls -l
-r-x---r-- 1 user user 31337 Feb 11 13:13 File

chmod 760 File

ls -l
-rwxrw---- 1 user user 31337 Feb 11 13:13 File
```

### Linux - File Ownership using `chown` -- change file owner and group

```sh
ls -l
-rwxrwxrwx 1 user001 user001 31337 Feb 11 13:13 File

sudo chown root File

ls -l
-rwxrwxrwx 1 root user001 31337 Feb 11 13:13 File

```
*The chown command requires sudo*


### Linux - Changing the Password using `passwd`

```sh
sudo passwd
```

## Windows - NTFS File & Folder Permissions
NTFS permissions are granted to users and groups on folders and files.

### NTFS Permissions - Folder
* **Full Control** - Anything
* **Modify** - Read, Write and Delete Files and Subfolders
* **Read/Execute** - See contents and Run Programs
* **List** Folder Contents - See Contents of Folders and Subfolders
* **Read** - View Contents and Open data files
* **Write** - Write to Files and Create new files and folders

### NTFS Permissions - File
* **Full Control** - Anything
* **Modify** - Read, Write and Delete files
* **Read/Execute** - Open and Run the file
* **List** Folder Contents - Open the file See Contents of Folders and Subfolders
* **Read** -  Open the file
* **Write** - Open and Write to the file

🛑 *Deny is stronger than allow*

### Moving and Copying NTFS Objects
1. **Copy and Move** from drive X: to Y: - will take the NTFS permissions of the **destination** drive.
2. **Copy** from drive X: to the same drive X: - **will loose the NTFS permissions.**
3. **Move** from drive X: to the same drive X: - **will inheritance the NTFS permissions**

## User Account Management

### Continuous Access Monitoring
Monitoring all users account activity

* Track Log on and Log off activity
* Track file access

🛑 - Shared Accounts = Bad!!!<br>
🛑 - Multiple Accounts = Use different user/pass.<br>
🛑 - Use least privilege - enough necessary to accomplish task.<br>
🛑 - Monitor and log activity of users with multiple accounts. (Log everything)<br>
🛑 - Avoid default usernames on user accounts.

## Triple AAA - Authentication, Authorization and Accounting

Two most popular protocols of triple AAA is RADIUS and TACACS+, providing centralized **Authentication**, **Authorization** and **Account management and registry logging** for computers to connect and use a **network service** securely.

RADIUS or TACACS+ server resides on a remote system and responds to queries from clientes such as VPN clients, wireless access points, routers and switches.

#### How RADIUS and TACACS+ works:

* The server authenticates **username and password** [authentication]
* Determine if a user is **allowed to connect** to the client [authorization]
* **Log** the connection [accounting]

### RADIUS - Remote Authentication Dial-In User Service
used for network access

1. **Radius Server**: Get the stack of usernames and passwords (can be MySQL, AD/DS, etc.)
2. **Radius Client**: The Gateway between users and servers
3. **Radius Supplicant**: The person that want to authenticate

**RADIUS can use up to 4 different ports:**

* **1812**
* **1813**
* **1645**
* **1646**

### TACACS+ - Terminal Access Controller Access-Control System Plus
Is really good to manage a big number of network devices.

Provide the same as RADIUS but the service decouple the authorization from the authentication. Manages the authorization better than RADIUS.

**Uses TCP Port 49**  

## Authentication Methods

### **PAP** - Password Authentication Protocol
Is the oldest authentication method. PAP sends username and password **in the clear / plaintext**

### **CHAP** - Challenge Handshake Authentication Protocol
Uses a hash value of challenge message to authenticate

### **NTLM** - NT LAN Manager for Windows
Similar to the CHAP; uses a challenge hashed message with a different process than CHAP

### **Kerberos** - for AD/DS 
1. Authenticator (Encrypted with user's password)
2. TGT (Encrypted with KDC's key) [ticket-grant-ticket]
3. Resource Ticket (Encrypted with Resource's key by the KDC and issued to the user)
4. Resource Ticket used by Client to access the resources

**Uses Port 88**

<p align="center">
<img width="75%" src="https://www.manageengine.com/products/active-directory-audit/kb/images/event-4771-kerberos-authentication-illustration.jpg" />
</p>

### **SAML** - Security Assertion Markup Language
Used exclusive for **Web Application**

### **LDAP** - Lightweight Directory Access Protocol
Query Directories: Structured language that allows one computer to go into somebody's directory and query, update...

**Uses TCP/UDP Port 389**

### Single Sign-On

* **LAN**: Windows Active Directory is dominant for **security SSO**
* **SAML**: SSO for **Web Application** / used to manage multiple apps using a single account

***
***
***

# 5) Risk Management
Risk management is the identification, evaluation, and prioritization of risks followed by coordinated and economical application of resources to minimize, monitor, and control the probability or impact of unfortunate events or to maximize the realization of opportunities.

# Defining Risk

**Vulnerability: A weakness; System flaw**

**Threat: Exploit vulnerabilities to harm assets.**

**Risk: The likelihood of a THREAT exploiting a VULNERABILITY, resulting in a loss.**

**Formulas:**<br>
*threats x vulnerability = risk*<br>
*threats -> vulnerability = risk*

## 1) Asset:
Is a part of an IT infrastructure that has a value. You can measure value either tangibly or intangibly. A gateway router is an example of an asset with tangible value, if it fails, you can easily calculate the cost to replace the router.

Example of assets: 

Asset | Info.
--- | ---
Servers | The computers that offer shared resources
Workstations | The computers users need to do their job
Data | The stored, proprietary information an organization needs to operate
Applications | Specific programs an organization needs to use
Personnel | The people who work in an organization
Wireless access | Wireless access to the network 
Internet services | The public or private-facing resources an organization provides to customers, vendors, or personnel via the Web or the Internet applications

## 2) Probability
Probability means the likelihood - over a defined period of time - of someone or something damaging assets.

**Quantitative likelihood:** based on numbers and data, can be more easy to measure anually.

**Qualitative likelihood:** is more subjective like (low/medium/high).

## 3) Threat actors
A threat actor can be a malicious person, such as a hacker accessing corporate secrets.

**The exam cover six types of threat actor:**
* Hacktivists
* Script Kiddies
* Insiders
* Competitors
* Organized Crime
* Nation State/APT

# Risk Assessment
### 1) Vulnerability Assessment
* NIST SP 800-30
* CVE (Common Vulnerabilities and Exposures)
* Nessus scanner
* Penetration Testing

### 2) Threat Assessment
* **Environmental**: Natural disasters outside the control of humans
* **Manmade**: Any threat that is not environmental
* **Internal**: Threat generated by internal sources, usually an insider to the organization
* **External**: Threat generated from outside your infrastructure 


## Risk Response
*After identified and analyzed risk, you must decide how to responde to the risks produced as a result of the analysis.*
### **1) Risk Mitigation**
Is an attempt to reduce the risk, or at least minimize its effects on an asset.
### **2) Risk Transference**
Or Risk Sharing, deals with risk by sharing with third-party. Example buying insurance to protect against natural disasters.
### **3) Risk Acceptance**
Means the organization has implemented controls and some risk remains. (residual risk). Remember that risk can never be completely eliminated.
### **4) Risk Avoidance**
Means thtat the organization could choose not to participate in activities that cause unnecessary or excessive risk.

## Risk Frameworks
* NIST - Risk Management Framework SP 800-37
* ISACA Risk IT Framework

# Security Controls
The cornerstone of IT security is understanding security controls and how to apply them.

1) **Administrative Control** (People -> IT Security)
    * Laws
    * Policies
    * Guidelines
    * Best Practices 

2) **Technical Control** (IT Systems -> IT Security)
    * Computer stuff
    * Firewalls
    * Password links
    * Authentication
    * Encryption 

3) **Physical Control** (Physical World)
    * Gates
    * Guards
    * Mantraps
    * Keys

## Activity Phase Control Types

1) **Deterrent control**: Deters the actor from **attempting** the threat. *(Warning Sign, SSH Banner)*

2) **Preventive control**: Deters the actor from **performing** the threat. *(Fence, Server Locks, Password Complexity)*

3) **Detective control**: Recognizes an actor's threat. *(Background check, CCTV, IDS)*

4) **Corrective**: Mitigates the impact of a manifested threat. *(Backups)*

5) **Compensating**: Provides alternative fixes to any of the above functions

*Most of security controls are **preventive** phase controls*

## Interesting Security Controls
* Mandatory Vacation
* Job Rotation
* Multi-person Control
* Separation of Duties
* Principle of Least Privilege

# Defense in Depth
Every IT infrastructure might be looked at as a series of concentric shells. The location of these shells depends on the types of threats you are mitigating.

Defense in Depth uses **administrative, physical and technical controls**.

<p align="center">
Physical defense in depth
</p>
<p align="center">
<img width="70%" src="https://www.ciatec.com/wp-content/uploads/2018/03/Defense-in-Depth.jpg" />
</p>

<p align="center">
<img width="80%" src="https://www.researchgate.net/profile/James_Cusick/publication/322161382/figure/fig1/AS:578042084814848@1514827380600/Security-Defense-in-Depth-Model.png" />
</p>

### **Redundacy**
Repeating the same controls at various intervals.
### **Diversity**
Try different set of security controls in a random pattern.
* **Vendor Diversity**: Uses several vendors to supply equipament and services.

# IT Governance
Influences how the organization conducts IT security.

In its most core function is to actually make the right set of security controls.

1) Laws and Regulations
* HIPAA (Health Insurance Portability and Accountability - USA)
2) Standards
* **Governament Standards**: NIST, ISO<br>
* **Industry Standards**: PCI-DSS (Payment Card Industry Data Security Standard)
3) Best Practices
4) Common-Sense

## Policies
Document that defines how we're going to be doing something. Define Roles and Responsabilities.

## Organizational Standards
Have much more detail than policies. Define the acceptable level of performance policy.

*The security controls come from the policies and standards.*

## Procedures
Step by step process of how to do something.

Security controls, Policies and standards help define and build the **Procedures**.

<p align="center">
<img width="75%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/0aff7f60c0b9b6bf8d8c420fd2ded843eb29984d/it-governance.jpg" />
</p>

# Security Policies
### **The Acceptable Use Policy (AUP)**:
Defines what a person can or can not do when using company assets and equipament. *(The paper you sign before entry a job position).*

### **Data Sensitivity and Classification Policies**:
Define the importance or nature of the data. *(i.e. Applying labels on the Government, they use Top Secret, Classified, etc).*

### **Access Control Policies**:
* How people get access to data or resources
* What type of data do users have access to.
* Data access and classification restrictions 
*(It cover a lot of things based on the job type).*

### **Password Policy:**
* Password recovery
* Password retention
* Bad login attempt
* Password reuse
* Complexity

### **Care and Use of Equipament**
How you maintain company equipament.

### **Privacy Policy**:
Are often for customers; defines how your data or usage will be shared with other resoruces. *(i.e. Services like Facebook etc).*

### **Personnel Policies**:
* Background Check
* Mandatory Vacation
* Job Rotation
* Separation of Duties
* Multi-person Control

# Risk Management Frameworks
A framework is a description of a complex process, concentranting on major steps and the flows between the steps. **Describes the major steps and flows of the complex process of applying security controls in an organized and controlled fashion.**

Frameworks come from a variety of sources including:
* **Regulatory**
* **Non-Regulatory**
* **National**
* **Industry Standards (Best Practices)**

## Popular RMF 

**National Standard and Regulatory:**
* NIST SP 800-37

**Non-Regulatory**:
* ISACA IT Infrastructure

**International Standard**:
* ISO 27000

<p align="center">
<b>NIST Risk Management Framework:</b>
</p>
<p align="center">
<img width="70%" src="https://csrc.nist.gov/CSRC/media/Projects/Risk-Management/images-media/OrgRMF.png" /> </p>

# Quantitative Risk Assessment
Is based on objective data -typically, numerical data; Exact values, for instance, can be used to describe impact or loss of an asset.

## Asset Value (AV)
When valuing an asset, consider not only the replacement cost, but also the revenue the asset generates, as this will be lost as well if the asset is not available.


*Example:*

Asset | Cost | Repair | Revenue | = Total
--|--|--|--|--
**Router** | €600 | €500 x day | €2000 x day | €3100

## Exposure Factor (EF)
The percentage of an asset that could be lost during a negative event. Realistically, you will not always lose 100% (1) of the asset; you may lose only 20% (0.2) or 50% (0.5) for example. 

*Example:*

Incident | Exposure Value
--|--
Flood | 1 (100%)

## Single Loss Expectancy (SLE)
Is the value that's computed simply by multiplying the asset's value by the exposure factor (percentage of loss).

**Formula:**<br>
Single Loss Expectancy = Asset Value x Exposure Factor<br>
**SLE = AV x EF**

*Example (using data below):*

AV | x  EF | = SLE
--|--|--
€3100 | 1 | €3100 

SLE = €3100 (AV) x 1 (EF) = €3100 

## Annualized Rate of Occurrence (ARO)
How many times per year you would expect a particularly negative event to occur, resulting in a loss of the asset. **This value relates more to likelihood than impact.**

*Example:*
Flood on Server room, base on data: one flood in about 10 years, 1/10 (0.1). [SLE x ARO = ALE]

## Annualized Loss Expectancy (ALE)
Essentially looks at the amount of loss from the SLE and determines how much loss the organization could realistically expect in a one-year period. 

**Formula**:<br>
ALE (Annualized loss expectancy) = SLE x ARO<br>
**SLE x ARO = ALE**


# Business Impact Analysis
Designed to mitigate the effects of an incident, **not to prevent an incident**.

* Determine mission process. *(make sure servers are up)*
* Identify critical systems.
* Single point-of-failure. *(using Defense-in-Depth...)*
* Identify resource requirements.
* Identify recovery priorities. *(prioritize most important steps to kepp whatever essential function running)*

## Types of Impact
* Property
* Safety / Life / People
* Finance (Credit, Cash flows...)
* Reputation
* Privacy

### **Privacy Impact Assessment (PIA) and Privacy Threshold Assessment (PTA)**
PIA: Determine the impact on the privacy of the individuals who data is beign stored; and ensure that the organization has sufficient security controls applied to be within compliance of applicable laws or standards.

To create a **(PIA) - Privacy Impact Assessment**, the organization needs to perform a **(PTA) - Privacy Threshold Assessment** on its infrastructure to locate **personal information**, what personal info. is stored and from whom the personal info is collected.

*PTA and PIA - in order to understand the impact of the loss of personal information can do to a particular business.*

## Calculating Impact
Determine how long the particular equipament going to last. (qualitative)

<p align="center">
<img  width="70%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/13cf0c9fbcd0acba680220cce03829cbf0ce1506/MTBF.png" />
</p>

* **MTTF = Mean Time to Failure**
* **MTTR = Mean Time to Repair**
* **MTBF = Mean Time Between Failure**

## Recovery Time Objective (RTO):
* Maximum amount of time that a resource may remain unavailable before an unacceptable impact on other system resources occurs.
## Recovery Point Objective (RPO):
* Defines de amount of time that will pass between an incident and recovery from backup.

*Recovery priorities help define what needs to be addressed to maintain business continuity.*

# Organizing Data
The first step to dealing with data security is **organization**.

* Analyze individual chuncks of data (such as databases, files, access control lists..)
* Determine the importance - **the sensitivity of data.**

## Data Sensitivity | Labeling
* **Public Data**: Has no restrictions. (stills needs integrity and availability)

* **Confidential Information**: Limited to authorized viewing as agreed by the parties involved.

* **Private Information**:social security number, passport number, PII - Peronally identifiable information...

* **Proprietary Information**: Information owned by a company that gives a certain competitive advantages. (i.e. The secret formula of Coca-Cola).

* **PHI - Protected Health Information**: Not only Health information, PII may include on PHI.

## Data Roles
* **Owner of the data / Data Owner**: Legally responsible for the data, can be entity responsible.

* **Steward / Custodian**: Maintain the accuracy and integrity of data.

* **Privacy Officer**: Ensures data adhere to privacy policies and procedures.

## User Roles
* **Users**: Assigned standard permissions to complete tasks. | Must understand how system functions works and have proper security training to recognize common issues (Malware, etc).

* **Privileged Users**: Increased access and control over the data or system. (i.e. a Normal user can run anti-malware software, but the privileged can updated then).

* **Executive Users**: Concentrates on strategic decisions including policy review, incident response and disaster recovery.

* **System Administrator**: Has complete direct control over the data or system. (Can remove or add users, applying permissions, and doing system maintance...) 

* **Data Owner | System Owner**: People or organizations who have legal ownership of this particular data set or particular system.

# Security Training

### **Onboarding**:
New hires or contractors
* Background check
* NDA (Non-disclosure agrement)
* Standard Operation Procedures
* Specialized Issues (i.e. Clean Desk)
* Rules of Behavior (i.e. Good AUP)
* General Security Policies (i.e. Personal Email, Social network...)

### **Offboarding**:
When the employee leaves the company
* Disable accounts (never delete an account)
* Return Credentials
* Exit interview
* Knowledge transfer

## Personnel Management Controls
* **Mandatory Vacation**: 
    * Required
    * Prevents collusion
    * Dependency issues
    * Makes fraud harder

* **Job Rotation**:
    * Redundancy and Backup
    * Allows for cross-training
    * Makes fraud harder

* **Separation of Duties**:
    * Requires dual execution *(at least two people to do a sensitive function)*

* **Multi-Person control**:
    * Moren than one person required in a task/function

## Role-Based Data Controls
* **System Owner**:
    * Management level role
    * Maintains security of the system
    * Defines a system administrator
    * Works with all **Data Owners** to ensure data security

* **System Administrator**:
    * Day-to-day administration of a system
    * Implement security controls

* **Data Owner**:
    * Defines the sensitivity of the data
    * Defines the protection of the data
    * Works with **System Owner** to protect data
    * Defines access to the data

* **User**:
    * Accesses and uses the assigned data responsibly
    * Monitors and reports security breaches

* **Privileged**:
    * Has special access to data beyond the typical user
    * Works closely with **System Administrators** to ensure data security

* **Executive User**:
    * **Read only** access but can look at all business data

# Third-Party Risk / Agreements

### **Business Partnership Agreement (BPA)**:
Most common used in private sector.

* Primary entities
* Time frame
* Financial issues
* Management

### **Service Level Agreement (SLA)**:
Used in private sector.

* Agreement between who is getting the service and service provider
* Service to be provided
* Minimum up-time
* Response time (contacts)
* Start and End date

### **Interconnection Security Agreement (ISA)**:
Is a technical Agreement used on public sector.

* Statement of Requirements
    * *Why are we interconnecting?*
    * *What system is interconnecting?*
* System secuirty considerations
    * *What information is interconnecting?*
    * *Where is this information going?*
    * *What services are involved?*
    * *What encryption is needed?*
* Topological drawing
* Signature authoring
    * Time frame for the interconnection
    * Technical and security reviews from them

### **Memorandum of Understanding/Agreement (MOU / MOA)**:
Agreement used in public sector.

* The purpose of the interconnection
* Relevant authorities *(Who is on charge?)*
* Specify the responsabilities
    * Downtime
    * Billing
* Define the terms of the agreement
    * Cost
* Termination/reauthorization

***
***
***

# 6) Cryptography and PKI
Cryptography is the practice of disguising information in a way that looks random

### **Obfuscation**
Hidden sensitive data - providing confidentiality


### **Classic Algorithms - by Substituition**
* **Caesar Cipher** (ROT1-25) - *The earliest known and simples ciphers*
* **Vigenère Cipher** *(Employs the Caesar cipher as one element of the encryption process + the key)*

### **Kerkchoff Principle**
The crypto algorithm should be public and the key is the secret.

### Where to **Encrypt & Decrypt**?
* **Data-at-Rest**: Resides in storage
* **Data-in-Transit**: Transport / Network
* **Data-in-Process**: RAM & CPU

### **Symmetric Encryption**
* Fast
* One Single Key / Session Key to encryption and decryption
* Primary way to encrypt data
* Ephemeral Key
  * Temporary
  * Provides perfect forward secrecy

### **Asymmetric Encryption**
* Slow
* Uses a Key pair **(Public Key and Private Key)**  
   * Public Key - encrypt
   * Private Key - decrypt

### Cryptosystem
Defines key properties, communication requirements for the key exchange; actions through encryption and decryption process.

*(Ex: Using asymetric encryption to exchange Session keys after that communicate using Symmetric encryption.)*

### **Symmetric CryptoSystems** 

Algorithm | Block or Streaming | Block Size | Rounds | Key Size | Notes
--|--|--|--|--|--
**DES** | Block | 64-bit | 16 | 56 bits | Uses five modes of operation: ECB, CBC, CFB, OFB and CTR.
**Blowfish** | Block | 64-bit | 16 | 32-448 bits | Public domain algorithm. 
**Twofish** | Block | 128-bit | 16 | 128, 192 and 256 bits | Public domain algorithm.
**3DES** | Block | 64-bit | 16 | 168 bits (56 x 3) | Repeats DES process 3 times.
**AES** | Block | 128-bit | 10, 12, or 14 | 128, 192 or 256 bits | Encryption standard for the US Gov.
**RC4** | Streaming | N/A | 1 | 40-2048 bits | Used in WEP, SSL and TLS; largely deprecated in current technologies.

*Rounds: Repeating the XOR/left-shift iteration X times.*

### **Block modes**
* **ECB** - Eletronic Code Block *(deprecated because nowdays is a week method that always produces the same output results with same input)*

*All block modes below uses IV, which ensures the output block is uniquely different*
* **CBC** - Cipher Block Chaining
* **CFB** - Cipher Feedback
* **OFB** - Output Feedback 
* **CTR** - Counter

*A **Binary Block** is a plaintext converted into 16-bit, 64-bit or 128-bit binary ciphertext.*

## Asymmetric Algorithms
### RSA
Rivest Shamir and Edelman - Asymmetric algorithm, **generates the private and public key**.

### ECC
Elliptic Curve Cryptography - Can create a smaller key than RSA, provides the same security with increased performance (more faster).

### Diffie-Hellman
* **Does not** use Public or Private keys
* Uses key exchange protocol
* Diffie Hellman groups help by defining the size or type of key structure to use: 

**Diffie Hellman Groups**
Group | Size
--|--
Group 1 | 768-bit modulus 
Group 2 | 1024-bit modulus 
Group 5 | 1536-bit modulus 
Group 14 | 2048 bit modulus 
Group 19 | 256-bit elliptic curve 
Group 20 | 384-bit elliptic curve 
Group 21 | 521-bit elliptic curve 


## PGP - Pretty Good Privacy
Uses both asymmetric and symmetric keys for a wide variety of operations uses web-of-trust instead PKI.

### PGP Certificates
* Symantec Corp.
  * Enterprise $olution
  * Encrypts Massa storage
  * Signing
  * Disk Encryption
  * BitLocker
  * FileVault
  * Enterprise Cloud Solutions

* OpenPGP
  * Free
  * Encrypted email
  * PKI Support
  * S/MIME

* GPG (GNU Privacy Guard)
  * Free Toolset
  * File and Disk encryption

## Hashing
One-way encryption providing integrity.

Hash | Algo.
--|--
MD5 | 128 bit hash
SHA-1 | 160 bit hash

**SHA-1 and MD5 has the same cryptographic flaws, that can cause hash collision.**

### **SHA-2** Family
SHA-256 | minor version: SHA-224<br>
SHA-512 | minor version: SHA-384

### **SHA-3** 
Uses a hash function called Keccack and has the same length of SHA-2. 

SHA-1 and SHA-2 have been replaced by the latest iteration of SHA known as SHA-3.

### **RIPEMD**
RACE Integrity Primitives Evaluation Message Digest.
* Not very common 
* Open Standard
* 128, 168, 256, 320 bit digests

### **HMAC**
Hash Message Authentication Code - Used in conjunction with symmetric key both to authenticate and verify integrity of the message.

* Provides message integrity

* Requires each side of the conversation to have the same key

* It is based on standard hashes (SHA-1, MD5, etc)

## Steganography
The art of hide information inside the data (hide data within data), and can be encrypted.

## Certificates and Trust
* Certificates include a public key and at least one digital signature.

### Digital Signature
* To create a digital signature for a document, you hash the document using your private key. Others can verify your digital signature with your public key.

### **Web of Trust**
* Web of Trust uses a web of mutually trusting peers.
* Requires a lots of maintenance

### **PKI** - Public Key Infrastructure
Is a system consisting of hardware, software, policies and procedures that creates, manage, distributes, uses, store and revoke **DIGITAL CERTIFICATES.**

PKI is the way we do internet. Uses a hierarchical structure with root servers.

* Certificate Authority (CA): Issues the certificates (Verisign, Thawte, etc).

### **CRL - Certificate Revocation List**
A list of serial numbers of certificates that have been revoked or are no longer valid, therefore should not be relied on.

* Downside it is slow and old.

### **OCSP - Online Certificate Status Protocol**
Is a more modern version of CRL that are used today, have a better performance.

### Common Types of Digital Certificates:
* **PKCS-7**: is a way to store certificates as individual files.
* **PKCS-12**: stores the certificates and the private keys as packages.
* **X.509** 

## Cryptographic Attacks
* Brute Force 
* Dictionary Attack
* Rainbow Table (dictionary of hashes)
* Collision Attack
* Replay Attack

### **Salt**
Salt is an arbitrary value, usually created by the application or OS storing passwords, added to the end of the password before it is hashed, making cracking harder.

*Example*:
```
> Password: 123456
> Salt (arbitrary): aksfle3t

> Concatenated with Salt: 123456aksfle3t

> Salted password (SHA-256): 02FCD2C88B089D2E1816070FFF8B80E13242264DA14233A57821CDAF4DDA45DF
```

### **Keystretching**
Combine a very long salt and a huge number of hashing iterations to make cracking even more harder.

Two most popular Key derivation functions
* PBKDF2 (Password-Based Key Derivation Function 2) algorithm
* BCrypt algorithm

*Example*:
```
PBKDF2 

Password:
123456

Hash:
rYoSDg62evyzhE1+lWBa9A==:YaeMu71c8KU3H0RYFPle0Q==

--------------------------

BCrypt

Password: 
123456

Hash:
$2b$10$vES9mCPsE10//vOc1u01XeUVmJrZyHGMPaRfo39OIUoJ2g7iPtDnu
```

***
***
***