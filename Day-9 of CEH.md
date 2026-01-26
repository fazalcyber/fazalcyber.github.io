<div align="center">
  <h1>Day - 9 of CEH</h1>
</div>

## Overview
 This documentation contains the complete learning on:

- **Nmap** basics and usage
- **Host Discovery (Ping Scan -sn)**
- Difference between scanning **with sudo vs without sudo**
- Understanding **ARP, ICMP probes**
- Core concepts of **TCP and UDP**
- **TCP Three-Way Handshake**
- **Ports, Port Types, and Nmap Port States**
- **Metasploitable 2 installation overview**

---

## Introduction to Nmap
 **Nmap (Network Mapper)** is a powerful open-source tool used for:

- Network discovery  
- Host identification  
- Port scanning  
- Service and version detection  
- Security auditing  

### Official website: https://nmap.org

<center>
  <img src="images/206.png" alt="1" width="600">
</center>

<center>
  <img src="images/207.png" alt="1" width="600">
</center>


### Useful command:
 - `nmap --help` → Displays all available options and switches in Nmap

---

## Nmap Ping Scan / Host Discovery (`-sn`)
 The `-sn` option is used for **host discovery only**.  
It disables port scanning and checks which hosts are alive.

### Example
 - `nmap -sn 192.168.1.1/24`
  
<center>
  <img src="images/208.png" alt="1" width="600">
</center>
  
### Observations
- Lists all active IP addresses in the given subnet  
- Without sudo, fewer devices are detected (especially Windows systems)  
- With sudo, more devices are detected due to ARP-based scanning  

---

## Difference Between Nmap With and Without Sudo

### A) Nmap Host Discovery – WITHOUT sudo
 When Nmap is run without root privileges:

- It cannot send raw packets  
- Uses TCP-based probes  

#### Packets sent
- SYN packet to port **80** (HTTP)  
- SYN packet to port **443** (HTTPS)  

If any response is received from these ports, Nmap considers the host as **ACTIVE**.

#### Limitation
- Many hosts block these ports or firewalls drop packets  
- Windows machines may not respond → not detected  

---

### B) Nmap Host Discovery – WITH sudo
 When Nmap is run with sudo/root privileges:

- It can send raw packets  
- Uses **ARP, ICMP, and TCP probes**  

#### Step 1: ARP Scan (Local Network)
- Nmap first sends ARP requests  
- If any ARP reply is received → host is **ACTIVE**  
- ARP scan is very reliable in LAN environments  

#### Step 2: If ARP fails, Nmap sends 4 packets
1. ICMP Echo Request (Ping)  
2. ICMP Timestamp Request  
3. TCP ACK packet to port 80  
4. TCP SYN packet to port 443  

If Nmap receives any response to any one of these packets, it marks the device as **ACTIVE**.

#### Advantages
- Detects Windows, Linux, printers, routers, and IoT devices  
- MAC addresses are also identified  

#### Example
- `sudo nmap -sn 192.168.1.1/24`

<center>
  <img src="images/209.png" alt="1" width="600">
</center>

---

## Why More Devices Are Detected with Sudo
 Reasons why more devices are detected when using sudo:

- ARP works at **Layer 2 (Data Link Layer)**  
- Firewalls cannot block ARP inside a local network  
- Windows systems respond to ARP but often block ICMP  

That is why:
- Without sudo → fewer devices (example: 18)  
- With sudo → more devices (example: 29)  

---
## Tools similar to nmap
- fing
  
<center>
  <img src="images/210.png" alt="1" width="600">
</center>

<center>
  <img src="images/211.png" alt="1" width="600">
</center>


- portroid
-   
<center>
  <img src="images/212.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/213.png" alt="1" width="600">
</center>

## ICMP (Internet Control Message Protocol)
 ICMP is used for:

- Error reporting  
- Network diagnostics  

### Common ICMP types used by Nmap
- Echo Request (Ping)  
- Echo Reply  
- Timestamp Request  

--> Some systems block ICMP for security reasons.

---

## TCP (Transmission Control Protocol)

### Key Features
- Most commonly used protocol in IP suite  
- Connection-oriented protocol  
- Works at the Transport Layer  
- Reliable and ordered data delivery  

### Uses
- Websites (HTTP/HTTPS)  
- File transfers (FTP)  
- Emails (SMTP, POP3, IMAP)  
- Secure communications  

### Reliability Mechanisms
- Error detection  
- Acknowledgements (ACK)  
- Retransmission of lost packets  
- Flow control and congestion control  

---

## TCP Three-Way Handshake
 TCP establishes a connection using a 3-step handshake:

1. **SYN** → Client requests a connection  
2. **SYN-ACK** → Server acknowledges and agrees  
3. **ACK** → Client confirms  
 
<center>
  <img src="images/214.png" alt="1" width="600">
</center>

Once completed, the connection is established.

This mechanism ensures:
- Both devices are ready  
- Reliable communication  
  
<center>
  <img src="images/215.png" alt="1" width="600">
</center>

---

## UDP (User Datagram Protocol)
  
<center>
  <img src="images/216.png" alt="1" width="600">
</center>

### Key Features
- Connectionless protocol  
- Works at the Transport Layer  
- No handshake mechanism  
- Faster but unreliable  

### Characteristics
- No error correction  
- No retransmission  
- Packets may be lost or arrive out of order  

### Uses
- Live streaming  
- Online gaming  
- VoIP  
- Torrents  
- DNS queries  

--> UDP is preferred where speed is more important than accuracy.

---

## TCP vs UDP (Comparison)
  
<center>
  <img src="images/217.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/218.png" alt="1" width="600">
</center>



| Feature | TCP | UDP |
|--------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | High | Low |
| Speed | Slower | Faster |
| Handshake | Yes (3-way) | No |
| Use cases | Web, email, file transfer | Streaming, gaming |

---

## Metasploitable 2 Installation (Overview)
 **Metasploitable 2** is a vulnerable Linux virtual machine used for penetration testing practice.

### High-Level Steps
1. Download Metasploitable 2 image  
2.   
<center>
  <img src="images/219.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/220.png" alt="1" width="600">
</center>

3. Install Oracle VirtualBox  
4. Create a new VM  
5. Choose **Linux → Other Linux (32-bit)**  
6. Attach the Metasploitable `.vmdk` file  
7. Set network adapter to **NAT** or **Host-only**  
8. Start the VM  

 Default credentials:
- Username: `msfadmin`  
- Password: `msfadmin`  
  
<center>
  <img src="images/221.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/222.png" alt="1" width="600">
</center>


This VM is commonly used with Kali Linux for CEH practice labs.

---

## CEH Exam Perspective (Important Points)
 Important topics from exam and practical perspective:

- Difference between `nmap -sn` and normal scans  
- Role of ARP in host discovery  
- TCP vs UDP characteristics  
- TCP three-way handshake steps  
- Why sudo/root privileges matter in scanning  

---

## What is a Port?
 A **Port** is a logical communication endpoint used by a device to identify specific services or applications running on it.
   
<center>
  <img src="images/224.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/233.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/234.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/235.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/236.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/237.png" alt="1" width="600">
</center>


### Simple Example (Apartment Concept)
- Apartment Building → IP Address  
- Flat Number → Port Number  

Just like letters are delivered to a specific flat number inside a building, data packets are delivered to a specific port number inside a device.

### Technical Definition
 A port is a **16-bit number** used by TCP and UDP protocols to differentiate multiple services running on the same IP address.

Port Range:
- Total ports available: `0 – 65535`

<center>
  <img src="images/225.png" alt="1" width="600">
</center>

---

## Types of Ports
 Ports are classified into three main categories:
   
<center>
  <img src="images/223.png" alt="1" width="600">
</center>


### 1. Well-Known Ports (0 – 1023)
 Used by standard system services.

Examples:
- HTTP → 80  
- HTTPS → 443  
- FTP → 21  
- SSH → 22  
- DNS → 53  

--> These ports usually require administrator/root privileges.

---

### 2. Registered Ports (1024 – 49151)
 Used by user-installed applications and services.

Examples:
- MySQL → 3306  
- PostgreSQL → 5432  
- RDP → 3389  

---

### 3. Dynamic / Private Ports (49152 – 65535)
 Used temporarily by:
- Client applications  
- Web browsers  
- Background processes  

These ports are automatically assigned and released after use.

---

## Port Status (Nmap Results)
 When performing port scanning, Nmap shows different port states:
  
<center>
  <img src="images/238.png" alt="1" width="600">
</center>

### 1. Open
- Port is open  
- Application or service is running  
- Accepts incoming connections  

Example:
- `80/tcp open http`
  
<center>
  <img src="images/226.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/227.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/228.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/229.png" alt="1" width="600">
</center>

---

### 2. Closed
- Port is reachable  
- No application is running  
- Device responded but rejected the connection  

Example:
- `22/tcp closed ssh`

---

### 3. Filtered
- Port is blocked by firewall  
- No response from target  
- Nmap cannot determine whether port is open or closed  

Example:
- `443/tcp filtered https`
  
<center>
  <img src="images/230.png" alt="1" width="600">
</center>

<center>
  <img src="images/231.png" alt="1" width="600">
</center>
  
<center>
  <img src="images/232.png" alt="1" width="600">
</center>

---

### 4. Unfiltered
- Port is reachable  
- Firewall is not blocking the port  
- Nmap can access the port but cannot confirm whether it is open or closed  
- This state usually appears in ACK scans  

Example:
- `80/tcp unfiltered http`

---

### 5. Open | Filtered
- Nmap cannot determine whether the port is open or filtered  
- No response is received from the target  
- Could be due to firewall silently dropping packets  
- This state usually appears in UDP, FIN, NULL, and XMAS scans  

Example:
- `53/udp open|filtered domain`

---

### 6. Closed | Filtered
- Nmap cannot clearly identify whether the port is closed or filtered  
- Target response is ambiguous  
- Firewall or packet filtering device may be interfering  

Example:
- `25/tcp closed|filtered smtp`

---

## Conclusion
 Day 9 focuses on understanding how Nmap performs host discovery using different scanning methods and how scanning changes based on privilege level (sudo/root).  
Additionally, this day covers important networking concepts such as TCP, UDP, ICMP, ports, and Nmap port states, which are essential for CEH practical labs and examination preparation.

---
