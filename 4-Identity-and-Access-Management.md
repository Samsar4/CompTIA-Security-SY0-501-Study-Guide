# Identity and Access Management

## Identification and AAA
Identification, authentication, authorization, and accounting work together to manage assets securely.

### **Identification**
The information on credentials identifies the user.
## **AAA**
* **Authentication**
  * **Authentication Factors:**
    * Something you **know** (password)
    * Something you **have** (smart card)
    * Something you **are** (fingerprint)
    * Something you **do** (android pattern)
    * **Somewhere** you are (geolocation)
    * *Multi-factor authentication generally uses two of this examples (Something you Know and Something you Have), never on same category.*
  * **Trusts and Federated Authentication**:
    * **Trust Relationship** - Active Directory DS
    * **Transitive Trust** - The organization trusts another entity because they are trusted by someone else that the organization trusts.
    * **Federated System** - Common authentication and credentials database that multiple entities use and share. (Active Directory: Different Domains could be used in other domains in the same forest).
* **Authorization**

* **Accounting**