# Identity and Access Management

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
