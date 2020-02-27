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

### Linux File Perms

