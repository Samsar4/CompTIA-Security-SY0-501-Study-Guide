# Cryptography and PKI
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
