<div align="center">
  <h1>Day - 10 of CEH</h1>
</div>

## Overview
This documentation covers **Advanced Nmap Port Scanning & Enumeration**.  
On this day, the main focus is understanding how Nmap performs different types of scans, how to control scan speed and accuracy, and how to enumerate services running on open ports.

This module includes:

- Skipping DNS Resolution (`-n`, `-R`)
- Skipping Host Discovery (`-Pn`)
- Default Nmap scanning behavior
- Scanning all ports (`-p-`)
- Scanning specific port ranges (`-p 1-2000`)
- Top ports scanning (`--top-ports`)
- Fast scan (`-F`)
- Service version detection (`-sV`)
- Accessing services based on results
- OS detection (`-O`)
- NSE script scanning (`--script`)
- Searching NSE scripts (`locate`, `grep`)
- Script help (`--script-help`)
- Aggressive scan (`-A`)
- Aggressive scan with selected ports
- Scanning multiple targets using file (`-iL`)
- UDP scanning (`-sU`)
- Countermeasures against port scanning

---

## Skipping DNS Resolution (`-n`)
When scanning targets, Nmap may perform DNS resolution to find hostnames.  
This can slow down scanning, especially when scanning multiple targets.

To speed up scanning, we can skip DNS resolution.

### Command
- `nmap -n <IP>`

### Why we use this?
- Avoids DNS lookup delay
- Improves scan speed
- Useful in large scans

---

## Force Reverse DNS Lookup (`-R`)
In some cases, we want Nmap to perform reverse DNS lookup even if it is not done by default.

### Command
- `nmap -R <IP>`

### Purpose
- Helps identify the hostname of the target (if available)
- Useful in documentation and network mapping

---

## Skipping Host Discovery (`-Pn`)
By default, Nmap first checks if the host is alive using ping/ICMP and discovery probes.  
But sometimes, firewall rules block ICMP and the host appears "down" even though it is active.

In such cases, we skip host discovery and directly scan ports.

### Command
- `nmap -Pn <IP>`

### When to use `-Pn`?
- ICMP ping is blocked
- Targets appear as "Host seems down"
- You want to directly scan ports without checking host availability

---

## Default Nmap Scan Behavior
By default, Nmap scans only the **most common/popular ports**, not the full 65535 ports.

### Command
- `nmap 192.168.1.52`

### Output Example
- `977 ports closed`
- `23 ports open`

### Meaning
Nmap checks common ports and reports:
- Open ports → services running
- Closed ports → service not running but reachable
- Filtered ports → firewall blocking

---

## Scanning All Ports (0–65535) (`-p-`)
To scan every possible TCP port on a target, we use `-p-`.

### Command
- `nmap 192.168.1.52 -p-`


<center>
  <img src="images/239.png" alt="1" width="600">
</center>


### Why scan all ports?
- Detect hidden services running on uncommon ports
- Full security assessment requires full port scan

Note: Full port scanning takes more time compared to default scanning.

---

## Scanning Specific Port Range (`-p 1-2000`)
Instead of scanning all ports, we can scan only a specific range.

### Command
- `nmap 192.168.1.52 -p 1-2000`

<center>
  <img src="images/240.png" alt="1" width="600">
</center>

<center>
  <img src="images/243.png" alt="1" width="600">
</center>

### When to use this?
- Faster scanning than full scan
- Useful when you want to focus on common service range

---

## Top Ports Scanning (`--top-ports`)
Nmap can scan the top most commonly used ports using `--top-ports`.

### Top 100 Ports
- `nmap 192.168.1.52 --top-ports 100`

<center>
  <img src="images/241.png" alt="1" width="600">
</center>

### Benefit
- Very fast scanning
- Good for initial reconnaissance
- Useful when time is limited

---

## Fast Scan (`-F`)
Fast scan checks the top 100 most common ports quickly.

### Command
- `nmap 192.168.1.52 -F`

<center>
  <img src="images/242.png" alt="1" width="600">
</center>

### Why use Fast Scan?
- Quick initial scan
- Identifies major open services immediately
- Saves time compared to full scan

---

## Service Version Detection (`-sV`)
Service version detection is used to identify:
- which service is running on a port
- what version the service is using

### Command
- `nmap <IP> -sV`

<center>
  <img src="images/244.png" alt="1" width="600">
</center>

### What does it detect?
- HTTP version
- FTP version
- SSH version
- Application banners

### Why this matters?
Service versions help in vulnerability analysis.  
Example: If an old vulnerable version of FTP/Apache is running, it may be exploitable.

---

## Accessing Services Based on Scan Results
Once we know which services are running, we can access them using appropriate tools.

### Common Service Access Methods
- HTTP / HTTPS → Browser
- SSH → Terminal
- FTP → FTP client
- RDP → Remote Desktop

### SSH Example
- `ssh msfadmin@192.168.1.55`

<center>
  <img src="images/252.png" alt="1" width="600">
</center>

This command attempts SSH login to the target device with the user `msfadmin`.

---

## Operating System Detection (`-O`)
Nmap can detect the operating system of the target machine using OS fingerprinting.

### Command
- `sudo nmap -O <IP>`

<center>
  <img src="images/245.png" alt="1" width="600">
</center>

### What it detects?
- OS type
- Kernel version
- Device fingerprint

Note: OS detection generally needs root privileges (sudo) for accuracy.

---

### Script scanning (NSE):
Nmap runs built-in scripts to automatically collect extra details from the target service (like HTTP title, headers, basic info).

### Syntax
- `sudo nmap <target-IP> -p <port> -sV`

<center>
  <img src="images/254.png" alt="1" width="600">
</center>

## NSE Script Scanning (Nmap Scripting Engine)
**NSE (Nmap Scripting Engine)** is a powerful feature of Nmap used for:
- automation
- enumeration
- vulnerability detection
- advanced scanning

### Locate NSE Scripts
- `locate *.nse`

<center>
  <img src="images/253.png" alt="1" width="600">
</center>

This helps list available `.nse` scripts installed on your system.

### Run Default Scripts
- `nmap <IP> --script default`


Default scripts perform safe and useful checks automatically, such as:
- basic enumeration
- service detection
- common security checks

---

## Searching Scripts Using Grep
We can search script content or script names using grep.

### Command
- `grep "ftp" filename`

### Purpose
- Find scripts related to specific services
- Quickly locate useful scripts during enumeration

---

## Script Help
To understand how a specific NSE script works, use script help.

###  Command
- `nmap --script-help <scriptname>`

<center>
  <img src="images/246.png" alt="1" width="600">
</center>

<center>
  <img src="images/255.png" alt="1" width="600">
</center>

### Why it is useful?
- Shows description of the script
- Explains required arguments
- Helps avoid mistakes during usage

---

## Aggressive Scan (`-A`)
Aggressive scan is one of the most powerful Nmap scans.  
It performs multiple scanning techniques together.

### Command
- `nmap <IP> -A`


### What it includes?
- OS detection
- Version detection
- Script scanning
- Traceroute

### Use Case
- When you want maximum information in a single scan
- Useful for full enumeration of a target

Note: Aggressive scans generate more traffic and can be detected by IDS/IPS.

---

## Aggressive Scan with Specific Ports
Instead of scanning all ports aggressively, we can limit the scan to selected ports.

### Command
- `nmap 192.168.1.52 -A -p 21,22,80,443`

<center>
  <img src="images/247.png" alt="1" width="600">
</center>

<center>
  <img src="images/248.png" alt="1" width="600">
</center>

### Why use this?
- Faster than a full aggressive scan
- Targets only important service ports

---

## Scanning Multiple IPs Using a File (`-iL`)
If we have multiple target IP addresses, we can store them in a file and scan all at once.

### Command
- `nmap -iL targets.txt -p 80,443`

<center>
  <img src="images/249.png" alt="1" width="600">
</center>

<center>
  <img src="images/251.png" alt="1" width="600">
</center>

### Benefit
- Faster scanning in bulk
- Helps in enterprise scanning
- Best for vulnerability assessment workflows

---

## UDP Port Scanning (`-sU`)
UDP scanning checks UDP services such as DNS, SNMP, NTP, etc.

### Command
- `sudo nmap <IP> -sU`

<center>
  <img src="images/250.png" alt="1" width="600">
</center>

### Notes on UDP Scanning
- UDP scanning is slow compared to TCP scanning
- It may take **20–30 minutes** depending on target and network conditions
- Very important for detecting services that do not use TCP

Common UDP services:
- DNS (53/udp)
- SNMP (161/udp)
- NTP (123/udp)

---

## Countermeasures Against Port Scanning
Organizations must protect systems from port scanning and enumeration attacks.

### Security Countermeasures
To reduce port scanning risk:
- Enable firewall rules
- Close unused ports
- Disable unnecessary services
- Use IDS/IPS (Intrusion Detection/Prevention Systems)
- Enable logging and monitoring
- Continuous monitoring of network activity

<center>
  <img src="images/256.png" alt="1" width="600">
</center>

These measures reduce attackers’ ability to identify services and vulnerabilities.

---

## Conclusion
CEH Day 10 covers advanced Nmap scanning methods used in real-world reconnaissance and enumeration.  
By understanding different scan techniques such as full port scan, fast scan, service detection, OS fingerprinting, NSE scripts, and UDP scanning, an ethical hacker can identify exposed services and assist in strengthening system security.
