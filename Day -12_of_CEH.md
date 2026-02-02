<div align="center">
  <h1>Day - 12 of CEH</h1>
</div>

## Overview
 This documentation covers **Password Cracking** concepts and tools used in ethical hacking.  
Password cracking is an important part of penetration testing because it helps in identifying **weak credentials** and improving the overall authentication security of an organization.

**Important Note (Ethical Rule):**  
 Password cracking should only be performed in **authorized environments** such as:
- Labs (TryHackMe / HackTheBox / Metasploitable)
- Test networks
- Systems where you have **written permission**

---

## Introduction to Password Cracking
**Password cracking** is the process of recovering passwords from stored or transmitted data.  
In ethical hacking, it is used to test password strength and detect weak authentication mechanisms.

### Why Password Cracking is Used in Ethical Hacking?
Ethical hackers perform password cracking to:
- Identify weak passwords used by employees/users
- Test login systems against brute-force attempts
- Improve security policies
- Recommend safer authentication methods (MFA, rate limiting, etc.)

---

## Online Password Attack Tool – Hydra
**Hydra** is a popular network login cracker used to perform **online password attacks**.

### Supported Services
Hydra supports many login services, such as:

- SSH  
- FTP  
- HTTP  
- HTTPS  
- Telnet  
- SMTP  

<center>
  <img src="images/284.png" alt="1" width="600">
</center>

<center>
  <img src="images/285.png" alt="1" width="600">
</center>

<center>
  <img src="images/286.png" alt="1" width="600">
</center>

<center>
  <img src="images/287.png" alt="1" width="600">
</center>

<center>
  <img src="images/288.png" alt="1" width="600">
</center>

### Key Features
- Multi-threaded attacks (faster testing)
- Supports multiple protocols
- Can resume interrupted sessions

---

### Important Hydra Options (Conceptual)
Hydra uses these options to specify usernames and passwords:

- `-l` → Single username  
- `-L` → Multiple usernames (username list file)  
- `-p` → Single password  
- `-P` → Multiple passwords (password list file)  
- `-s` → Custom port (if service runs on a different port)  
- `-v` → Verbose mode (shows detailed output)

--> Hydra should be used only in legal lab environments or authorized systems.

---

# Medusa – Password Brute-Forcing Tool

## Overview

**Medusa** is a fast, parallel, and modular **password brute-forcing and login testing tool** used in **penetration testing** and **ethical hacking**.  
It supports numerous network services and allows attackers or security testers to perform **credential-based attacks** efficiently.

Medusa is commonly used during the **Password Attacks** phase in the **CEH (Certified Ethical Hacker)** methodology.
---

## Why Medusa?

Medusa is preferred over traditional brute-force tools because:

- Extremely **fast and parallel**
- **Modular architecture**
- Supports **multiple protocols**
- Can test **multiple hosts simultaneously**
- Ideal for **large-scale password audits**

---

## Services Supported by Medusa

Medusa supports many authentication services, including:

- SSH
- FTP
- Telnet
- HTTP / HTTPS
- SMB
- MySQL
- PostgreSQL
- VNC
- RDP
- SMTP
- POP3
- IMAP
- MSSQL
- LDAP

<center>
  <img src="images/289.png" alt="1" width="600">
</center>

<center>
  <img src="images/290.png" alt="1" width="600">
</center>

<center>
  <img src="images/291.png" alt="1" width="600">
</center>

<center>
  <img src="images/292.png" alt="1" width="600">
</center>
---

## Ethical Attack Workflow (Lab Process)
 A structured workflow must be followed for ethical password testing:

1. Perform port scanning  
2. Identify running services  
3. Detect login service (SSH, FTP, HTTP, etc.)  
4. Prepare username and password lists  
5. Perform controlled testing  
6. Analyze successful credentials  
7. Document findings  

--> This process helps keep your testing professional and report-ready.

#  Accessing Metasploit Graphically Using VNC Viewer

##  Overview

Metasploit can be accessed not only via the **command line (msfconsole)** but also through a **Graphical User Interface (GUI)** using **VNC Viewer**.  
This approach is commonly used in **virtual labs, remote Kali machines, cloud-based pentesting environments, and CEH practice setups**.

Using VNC allows you to:
- Access the **full Kali Linux desktop**
- Launch **Metasploit Framework GUI**
- Perform attacks visually instead of terminal-only interaction

---

## Why Use Metasploit Graphically?

Graphical access is helpful for:

- Beginners learning Metasploit
- Visual understanding of exploits & modules
- Remote access to Kali Linux
- Managing multiple tools alongside Metasploit

---

##  Step 1: Install VNC Server on Kali Linux

VNC Server allows remote graphical access to the Kali desktop.

<center>
  <img src="images/293.png" alt="1" width="600">
</center>

<center>
  <img src="images/294.png" alt="1" width="600">
</center>

<center>
  <img src="images/295.png" alt="1" width="600">
</center>

# Accessing Metasploit Graphically Using RDP (Remote Desktop Protocol)

## Overview

**Remote Desktop Protocol (RDP)** allows graphical remote access to a system over the network. 
<center>
  <img src="images/297.png" alt="1" width="600">
</center>

<center>
  <img src="images/298.png" alt="1" width="600">
</center>

<center>
  <img src="images/299.png" alt="1" width="600">
</center>

<center>
  <img src="images/300.png" alt="1" width="600">
</center>

<center>
  <img src="images/301.png" alt="1" width="600">
</center>

<center>
  <img src="images/302.png" alt="1" width="600">
</center>

---

## Password Storage Concepts
Understanding password storage is important because it affects how passwords can be recovered.

---

### 7.1 Plain Text Passwords
Plain text passwords are:
- Stored directly without encryption
- Very insecure
- Easy to steal and misuse

--> If plain text passwords are leaked, attackers get instant access.

---

### 7.2 Hashed Passwords
 Hashed passwords are:
- Converted using hashing algorithms
- More secure than plain text
- Not directly readable

--> Hashing protects passwords, but weak hashes can still be attacked using cracking methods.

---

### 7.3 Salted Hashes
Salted hashes involve adding an extra random value (salt) before hashing.

Benefits:
- Prevents rainbow table attacks
- Makes cracking much harder
- Even same passwords will produce different hashes

---

## Common Password Weaknesses
Many passwords are weak due to predictable behavior.

### Common mistakes
- Using common words
- Short password length
- Reusing passwords
- No special characters
- Predictable patterns

--> Weak passwords increase the success rate of dictionary and hybrid attacks.

---

## Defense Against Password Attacks
Organizations can reduce password cracking risks using strong defenses.

---

### 9.1 Strong Password Policy
A strong password should have:
- Minimum **12 characters**
- Uppercase + lowercase letters
- Numbers
- Symbols

--> Strong passwords reduce brute-force success.

---

### 9.2 Account Lockout Policy
Account lockout helps by:
- Locking the account after multiple failed login attempts
- Preventing unlimited login guesses

--> This prevents online brute-force attempts.

---

### 9.3 Multi-Factor Authentication (MFA)
MFA adds an extra layer of security.

 Even if the password is cracked, attacker still needs:
- OTP
- Authenticator verification
- biometric approval

---

### 9.4 CAPTCHA Implementation
CAPTCHA helps by:
- Preventing automated attacks
- Blocking bots from repeating login attempts

---

### 9.5 Rate Limiting
Rate limiting prevents attacks by:
- Limiting login attempts per IP
- Slowing down automated password guessing tools

--> Very effective against tools like Hydra.

---

## Best Practices for Ethical Hackers
Ethical hackers must follow responsible rules during password testing.

### Best Practices
- Always take permission before testing  
- Maintain attack logs  
- Avoid testing on production systems  
- Report vulnerabilities responsibly  

--> Unauthorized password cracking is illegal and unethical.

---

## Conclusion 
Password cracking techniques help identify weak authentication mechanisms.  
Ethical hackers use dictionary attacks, brute-force attacks, and hybrid attacks to test password security and recommend strong protections such as:

- Strong password policies  
- MFA  
- Account lockout  
- Rate limiting and CAPTCHA  
- Secure password storage (hashed + salted)

---
