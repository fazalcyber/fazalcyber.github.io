<div align="center">
  <h1>Day - 13 of CEH</h1>
</div>

---
NetBIOS Enumeration, SMB Enumeration, SMTP Enumeration, NAT vs Bridged Networking

## 1. Objective of the Session
The objective of this session is to understand how network services expose information during the enumeration phase of ethical hacking. This includes identifying information leakage through NetBIOS, SMB, and SMTP services, understanding how attackers exploit such services, and learning appropriate countermeasures. The session also explains virtualization networking modes required for penetration testing environments.

---

## 2. Enumeration in Ethical Hacking
Enumeration is the process of actively extracting detailed information from a target system after scanning. It involves direct interaction with services to obtain usernames, machine names, shared resources, network structure, and service configurations. Enumeration converts basic reconnaissance data into actionable intelligence used for further exploitation.

---

## 3. Important Default Ports and Their Significance
Network services operate on well-known ports which help attackers identify running services quickly.
RDP operates on TCP port 3389 and allows remote access to Windows systems.
NetBIOS Name Service operates on UDP port 137 and is used for name resolution.
NetBIOS Datagram Service operates on UDP port 138 and supports connectionless communication.
NetBIOS Session Service operates on TCP port 139 and supports session-based communication.
SMB operates on TCP port 445 and provides file and printer sharing.
SMTP operates on TCP port 25 and is used for email transmission.
Exposed ports increase the attack surface of a system.

---

## 4. Host Discovery and Service Detection
Host discovery identifies live systems within a network.
Service detection identifies which services are running on discovered hosts.
This phase reveals open ports, service availability, service versions, and operating systems.
Attackers use this information to select suitable enumeration and exploitation techniques.
Defenders use this information to harden exposed services.

---

## 5. NetBIOS Enumeration
NetBIOS enumeration is the process of extracting information from NetBIOS-enabled systems.
It is mainly used against Windows-based networks.
Information obtained includes:
Workgroup or domain names
Computer names
Logged-in users
Network shares
NetBIOS assists in name resolution and session establishment.
Poorly configured NetBIOS services leak sensitive internal network information.

<center>
  <img src="images/303.png" alt="1" width="600">
</center>

<center>
  <img src="images/304.png" alt="1" width="600">
</center>

<center>
  <img src="images/305.png" alt="1" width="600">
</center>

<center>
  <img src="images/306.png" alt="1" width="600">
</center>

<center>
  <img src="images/307.png" alt="1" width="600">
</center>

<center>
  <img src="images/308.png" alt="1" width="600">
</center>

<center>
  <img src="images/309.png" alt="1" width="600">
</center>

<center>
  <img src="images/310.png" alt="1" width="600">
</center>

---

## 6. SMB Enumeration
SMB enumeration is used to identify shared folders, files, printers, users, and permissions.
SMB is widely used in Windows environments for resource sharing.
Information obtained through SMB enumeration includes:
List of shared folders
Access permissions on shares
User and group information
Password policies (in some cases)
Misconfigured SMB shares may allow unauthorized access to sensitive data.

<center>
  <img src="images/311.png" alt="1" width="600">
</center>

<center>
  <img src="images/312.png" alt="1" width="600">
</center>

---

## 7. Relationship Between NetBIOS and SMB
NetBIOS provides naming and session services.
SMB provides file and printer sharing functionality.
In older systems, SMB relies on NetBIOS.
In modern systems, SMB runs directly over TCP port 445.
Both services together expose extensive internal network information if not secured.

---

## 8. Enumeration Tools and Their Purpose
Enumeration tools automate information gathering from NetBIOS and SMB services.
They are used to:
Identify shared resources
List users and groups
Detect weak configurations
Simulate real-world attacks in penetration testing labs
Understanding these tools helps defenders recognize enumeration behavior.

---

## 9. Samba and SMB Protocol Versions
Samba is an open-source implementation of SMB for Linux systems.
Older SMB versions such as SMBv1 (NT1) are insecure.
SMBv1 is vulnerable to multiple attacks and exploits.
Modern systems use SMBv2 and SMBv3 which provide:
Improved authentication
Encryption support
Better performance
Legacy protocols should only be enabled in isolated lab environments.

---

## 10. SMTP Enumeration
SMTP enumeration is the process of identifying valid email users on a mail server.
Attackers analyze server responses to determine whether a mailbox exists.
Requirements for SMTP enumeration include:
Port 25 must be open
Knowledge of the target mail domain
Availability of usernames
Misconfigured SMTP servers may reveal valid users.

---

## 11. SMTP Commands and Enumeration Risk
SMTP supports commands such as HELO, MAIL FROM, RCPT TO, VRFY, and EXPN.
If VRFY or EXPN is enabled, attackers can confirm valid email accounts.
Information obtained can be used for:
Phishing attacks
Social engineering
Password attacks
Secure SMTP servers restrict or disable enumeration-related commands.

---

## 12. SMTP Security Issues
SMTP enumeration may lead to:
Email user list disclosure
Spam attacks
Open mail relay abuse
Mail server blacklisting
Proper configuration is required to prevent misuse.

---

## 13. Virtualization in Ethical Hacking Labs
Virtual machines are widely used in ethical hacking labs.
Networking mode selection determines communication capability.
Incorrect network configuration can block enumeration and scanning activities.

---

## 14. NAT Networking Mode
NAT stands for Network Address Translation.
The virtual machine accesses the internet through the host.
The VM receives a private internal IP address.
Inbound connections from the host or network are blocked by default.
NAT provides isolation but limits enumeration capability.
Not ideal for internal network scanning labs.

<center>
  <img src="images/315.png" alt="1" width="600">
</center>

<center>
  <img src="images/316.png" alt="1" width="600">
</center>
---

## 15. Bridged Networking Mode
Bridged mode connects the VM directly to the physical network.
The VM receives an IP address from the same network as the host.
The VM behaves like a real machine on the network.
Allows full communication between:
VM and host
VM and other LAN devices
Best mode for enumeration and scanning labs.

<center>
  <img src="images/314.png" alt="1" width="600">
</center>

---

## 16. Host-Only Networking Mode
Host-only mode allows communication only between host and VM.
No internet access is available.
Used for isolated testing environments.

---

## 17. Countermeasures Against Enumeration
Disable unused services such as NetBIOS and SMB if not required.
Restrict ports 139 and 445 using firewalls.
Disable SMBv1 and enforce SMBv2 or SMBv3.
Apply strong password policies and account lockout mechanisms.
Restrict SMTP commands that allow enumeration.
Enable IDS and IPS to detect scanning behavior.
Enable logging and monitoring for investigation.

<center>
  <img src="images/313.png" alt="1" width="600">
</center>

---

## 18. Security Best Practices
Follow the principle of least privilege for shared resources.
Avoid public or anonymous access to network services.
Patch systems regularly to fix vulnerabilities.
Audit network services periodically.
Conduct authorized penetration testing to identify weaknesses.

---

## 19. Ethics and Legal Considerations
Enumeration must only be performed in authorized environments.
Unauthorized scanning and enumeration is illegal.
Ethical hackers must follow legal guidelines and professional standards.
The goal of ethical hacking is security improvement, not exploitation.

---

## 20. Conclusion
NetBIOS, SMB, and SMTP enumeration expose critical internal network information when misconfigured. Understanding these services, their risks, and proper defenses is essential for cybersecurity professionals. Secure configuration, monitoring, and ethical practices ensure resilient and protected network environments.
