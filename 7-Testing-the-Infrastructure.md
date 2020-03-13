# Testing the Infrastructure

## Vulnerability Scanning Tools
* traceroute/tracert
* Advanced IP scanner 
* Nmap
* MBSA - Microsoft Baseline Security Analyzer (determine the security state of a system by assessing missing security updates and less-secure security settings; report good information for vulnerability assessment)

## Vulnerability Scanning Assessmentk
*The purpose of Vulnerability Scanning is to identify vulnerabilities cause by lack of security controls, common misconfigurations, and so on.*

### Credential vs Non-credential Vulnerability Assessments
A **Credential Vulnerability Asssessment** basically means you've got usernames and passwords as a part of your assessment. **Non-credential** you don't touch on usernames and passwords on assessments.

### Intrusive vs. Non-intrusive
Almost all vulnerability assessments are **non-intrusive**. Scanning systems, gather information and identifying vulnerabilities are different than corrupt the entire database.

## Vulnerability Assessment Tools
* Nessus by Tenable
* Nexpose by Rapid7
* OpenVAS (Opensource) 

## Principles of Social Engineering
* **Authority**
	* Impersonate or imply a position of authority
* **Intimidation**
	* Frighten by threat
* **Consensus**
	* To convince of a general group agreement
* **Scarcity**
	* To describe a lack of something
* **Familiarity**
	* To imply a closer relationship
* **Trust**
	* To assure reliance on their honesty and integrity
* **Urgency**
	* To call for imediate action

## Social Engineering Attacks
* **Phishing**<br>
* **Spear Phishing** - Directed towards a specific person or company<br>
* **Vishing** - Uses Voice calls/telephone system to get private information<br>
* **Hoax** - Warns someone that something bad is happening when its not<br>
* **Watering Hole Attack** - An attempt to infect websites that a group of end users would normally go to gain access to their information or network<br>
* **Whaling** - Spear phishing tha targets senior management and executives<br>
* **Tailgating** - *(i.e leave computer unlocked, door etc)*<br>
* **Shoulder Surfing** 👀 <br>
* **Dumpster Diving** 

## Web Application Attacks
* **Common Log Format (CLF)** - Standard type of logs that every single type of web server generates.

```
127.0.0.1 - - [28/OCT/2012/13:12:44 - 0500] "GET /CertifiedHacker.png HTTP/1.0" 200 42213
    |      |             |                    |                                  |     |
  HOST    IDENT     DATE & TIME            REQUEST                             STATUS BYTES
```
**IDENT** - If the IdentityCheck directive is enabled and the client machine runs ident, then this is the identity information reported by the client.<br>
**GET** - Request HTTP method command<br>
**STATUS** - status, 200 = Everything is ok<br>
**BYTES** - the number of bytes in the object returned to the client, excluding all HTTP headers.

### Common Web Application Attacks
* **Cross-site scripting (XSS)** - Client-side script injected into trusted web site
* **XML injections** - Used to manipulate or compromise the logic of an XML application or service (i.e change the price of a product on ecommerce)

### Attacking Applications
* **Code Injection**
* **Comand Injection**
* **SQL injection (queries)**
	* inner join 
	* select from 
	* insert into 
* **LDAP injection (queries info)** 
	* based on X.500 protocol
		* DC = Domain Component
		* OU = Organizational Unit
		* CN = Common Name
* **Buffer Overflow** - overflows the input directly to the memory 
* **Integer Overflow** - overflow an input variable (i.e typing a large number on calculate forcing an error)

### Applications Vulnerabilities
* **Race Condition**
* **Improper Input Handling**
* **Improper Error Handling**
* **Memory/buffer vulnerability**
	* Memory Leak
	* Integer Overflow
	* Buffer Overflow
* **Pointer deference**
* **Resource exhaustion**
* **Weak cipher suites and implementations**
* **DLL injection**

## Pentesting / Penetration Testing
A penetration test will actually try to grab the data itself. A vulnerability assessment at no time will ever actually try to grab the data. 

### Pentesting Process
1. Reconnaissance
2. Scanning
3. Gaining Access
4. Maintaining Access
5. Expanding to other systems
6. Avoid Detection

### Principles
* Authorization
	* Define the targets
	* Attack model
		* White box - have extensive knowledge about the target
		* Black box - attacker know nothing about the target
		* Gray box - somewhere between the two
* Discover Vulnerabilities
	* Reconnaissance
		* Passive Discovery 
		* Semi-passive discovery
		* Active discovery
	* Try to get Information
* Exploit vulnerabilities
	* Pivotting
	* Persistance
	* Privilege Escalation
