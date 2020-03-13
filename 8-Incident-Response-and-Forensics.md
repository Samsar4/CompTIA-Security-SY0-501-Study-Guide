# Incident Response & Forensics

## Incident Response Process
**Preparation**
- The big plan
- Who's doing what
- Organize types of incidents that might happen

**Reporting**
- What reports go to whom?
- Escalation

**Identification**
- Recognize what incident has ocurred
- Report from users
- Check the monitoring tools you use
- Watch alerts and logs
- Assess the impact
- Define who's involved

**Containment**
- Mitigate the damage
- Stop the attack
- Segregate the network
- Shutdown the system
- Turn off a service

**Eradication**
- Remove the malware
- Close off vulnerabilities
- Add new controls

**Recovery**
- Restore from backups
- Pull from snapshots
- Hire replacemente personnel
- Monitor to ensure good operation

**Documentation**
- Document the incident
- What failed?
- What worked?

## Incident Response Plan
**CIRT-Cyber incident response team**
- A group of people whose job is to response to all incident
- Full or part time - or both
- IT Security Team
- IT Department
- Human Resources
- Legal
- Public Relations

**Document incident types / Category definitions**
- Physical access
- Malware Phishing
- Social engineering
- Data access

**Roles and Responsabilities**
- Users 
- Help Desk
- Human Resources
- Database manager
- Incident Hotline
- IR manager/ IR officer
- IR team

**Reporting Requirements / Escalation**
- Determine Severity
- Based on severity have a clear chain of escalation
- Informing law enforcement

**Practice**
- Annual scenario drills 

## Digital Forensics
Digital forensics is the process of uncovering and interpreting electronic data. The goal of the process is to preserve any evidence in its most original form while performing a structured investigation by collecting, identifying and validating the digital information for the purpose of reconstructing past events.

The context is most often for usage of data in a court of law, though digital forensics can be used in other instances.

### Chain of Custody
*The whole idea of hcina of custody is to show good integrity of the evidence itself.*
- Gathering Evidence - data is of high integrity

#### **Chain of Custody Process**
1. Define the Evidence
2. Document collection method
3. Data/time collected
4. Person(s) handling the evidence
5. Function of person handling evidence (qualified person)
6. All locations of the evidence (i.e inital collection, moved to law enforcement...)

### **Order of Volatility**
*The order of volatility is a process that **enumerates when, where, and how to gather the data/evidence before the data changes or disappears***.
- **Memory**
	- Caches
	- Routing tables
	- ARP tables
- **Data on the Disk**
	- Optical, flash drives
	- Cache files, temp files
	- Write blocks enabled tools
- **Remotely logged data**
	- Web site data
	- Remote file server logs
	- Backups
- **Backups**
	- Trends
	- Low volatility takes time to gather data

### **Forensic Data Acquisition**
*Checklist of issues you should consider when you're performing Digital Forensics.*

1. Capture the system image
2. Netwrok traffic and logs
3. Capture video 
	- Security cameras
	- Record time offset
4. Take Hashes
5. Take screenshots
6. Interview witnesses
7. Track man hours

## Contingency Planning
*Attempts to mitigate adverse incidents to preserve business continuity*.
- How do we recover from a specific type of a disaster?
- What to do for keep the **Business Continuity** going?

### Disaster Recovery - Evacuation Plan
- **Backup Sites**
	- **Cold site**
		- It takes weeks to bring online
		- Basic office spaces (i.e building, chairs, AC...)
		- No operational equipment
		- Cheapest recovery site
	- **Warm site**
		- It takes days to bring online
		- Operational equipment but little or no data
	- **Hot site**
		- It take hours to bring online
		- Real-time synchronization
		- Almost all data ready to go - often just a quick update
		- Very expensive

- **Distance & Location** - different backup sites
- **Internet requirements**
- **Housing & entertainment**
- **Legal Issues** 

### Order of Restoration
- Power
- Wired LAN (is open and running)
- ISP link (running)
- Active Directory/DNS/DHCP server (up and cooking)
- Account servers 
- Sales and account workstations
- Production servers
- Production workstation
- Wireless access
- Peripherals (Printers, Camers, Scanners, faxes...)

**Annual exercises**<br>
**Failover** - simpe means the process of making recovery site happen.<br>
**Alternative Processing Sites** - different types of processing sites<br>
**Alternative business practices**<br>
**After action reports** - A clear and detailed documentation of everything that happened so that if it ever happens again you'll be ready to handle any form of business contingency planning.

🛑 Through planning and practice is what makes recovery plans successful when disasters occur

## Backups
- `stat` **Linux** command - stat can return the status of an entire file system, the status of the first hard disk and so on.

<p align="center">
<img width="73%" src="https://www.howtoforge.com/images/command-tutorial/big/stat-basic.png" />
</p>

- Archive attribute - **Windows** - if something is created or changed

### **Differential Backup**
- Backup all the changes since the last full backup
<p align="center">
<img width="73%" src="https://www.easeus.com/images/en/screenshot/todo-backup/guide/differential-backup.png" />
</p>

🛑 *Differential there are less backup sets but they get bigger.*<br>

### **Incremental Backup**
- Only backs up changes made from last backup
<p align="center">
<img width="73%" src="https://www.easeus.com/images/en/screenshot/todo-backup/guide/incremental-backup.png" />
</p>

🛑 *Incremental more backup sets but smaller.*

### **Snapshots**
Snapshots typically under virtual machines and they are an absolute perfect way of making a copy of something that's happened in the past.

### What Media
- External hard-drive
- Tape
- Cloud

### Offsite Backup
Remote backup is good for disasters in general.

### Cloud Backup
Cloud backups work beautifully, however, they have one big downside and that is they take up a tremendous amount of time to get the initial backups going.