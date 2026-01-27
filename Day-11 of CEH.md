<div align="center">
  <h1>Day - 11 of CEH</h1>
</div>


## DNS Enumeration & Password Attacks

> Part of CEH (Certified Ethical Hacker) Practical Learning  
> Topic: DNS Enumeration, FTP Enumeration & Password Attacks

## Table of Contents

1. What is Enumeration?
2. Information Gathered During Enumeration
3. DNS Basics
4. What is DNS Enumeration?
5. DNS Record Types
6. DNS Enumeration Tools
7. DNS Enumeration Process
8. DNS Zone Transfer (AXFR)
9. Advanced DIG Commands
10. Nmap & DNS Enumeration
11. FTP Enumeration Basics
12. Password Attacks
13. Password List Generation (Crunch)
14. Password Cracking Tools
15. Custom Wordlist Generation (CeWL)
16. Conclusion

## What is Enumeration?

Enumeration is the process of actively extracting detailed information from a target system by sending structured queries and analyzing responses.

<center>
  <img src="images/257.png" alt="2" width="600">
</center>

<center>
  <img src="images/258.png" alt="2" width="600">
</center>


Goal:
To gather as much valid information as possible about the target environment.

## Information Gathered During Enumeration

Network and Website Information:
- Active hosts
- Subdomains (mail.domain.com, vpn.domain.com)
- Open ports and running services

Network Shares:
- Shared folders
- File permissions
- Misconfigured public shares

Accessing SMB Share (Windows):
Win + R  
\\192.168.1.25

DNS Information:
- DNS records
- Name servers
- Subdomains

System Details:
- Hostnames
- Machine names

Users and Groups:
- Valid usernames
- Administrator accounts
- Privilege information

## DNS Basics

DNS (Domain Name System) converts domain names into IP addresses.

DNS Resolution Flow:
1. Browser sends request to DNS Resolver
2. Resolver contacts Root Server, TLD Server, and Authoritative DNS Server
3. IP address is returned to the browser

DNS Resolver acts as the DNS client.

## What is DNS Enumeration?

DNS Enumeration is the process of collecting all DNS-related information about a target domain.

<center>
  <img src="images/259.png" alt="2" width="600">
</center>


Information Collected:
- DNS servers
- Subdomains
- IP addresses
- Mail servers
- TXT records
- Zone transfer data

Helps in understanding the entire domain structure.

## DNS Record Types

A record – IPv4 address mapping  
AAAA record – IPv6 address mapping  
NS record – Name server  
MX record – Mail server  
TXT record – Verification or SPF  
CNAME record – Alias  
SOA record – Zone authority information  
PTR record – Reverse DNS mapping  

<center>
  <img src="images/260.png" alt="2" width="600">
</center>

<center>
  <img src="images/261.png" alt="2" width="600">
</center>


## DNS Enumeration Tools

dig (Domain Information Groper):
Used for detailed DNS queries and provides answer, authority, and additional sections.

nslookup:
Used for quick DNS lookups and basic DNS enumeration.

<center>
  <img src="images/263.png" alt="2" width="600">
</center>

<center>
  <img src="images/264.png" alt="2" width="600">
</center>

## DNS Enumeration Process

1. Select target domain
2. Identify name servers
3. Query DNS records
4. Discover subdomains
5. Test zone transfer vulnerability

<center>
  <img src="images/262.png" alt="2" width="600">
</center>

<center>
  <img src="images/265.png" alt="2" width="600">
</center>

## DNS Zone Transfer (AXFR)

Zone Transfer copies DNS records from one DNS server to another.

AXFR refers to a full zone transfer.

<center>
  <img src="images/266.png" alt="2" width="600">
</center>

<center>
  <img src="images/267.png" alt="2" width="600">
</center>

<center>
  <img src="images/268.png" alt="2" width="600">
</center>

<center>
  <img src="images/269.png" alt="2" width="600">
</center>

<center>
  <img src="images/270.png" alt="2" width="600">
</center>

Risk:
- Disclosure of all subdomains
- Internal hostnames
- Network structure
- Mail servers

Prevention:
- Allow zone transfers only to trusted IPs
- Disable public AXFR
- Use TSIG authentication

## Advanced DIG Commands

Dig can query specific DNS servers, return short output, and trace DNS resolution paths from root to authoritative servers.

## Nmap & DNS Enumeration

<center>
  <img src="images/271.png" alt="2" width="600">
</center>

DNS operates on Port 53.

UDP 53 – Normal DNS queries  
TCP 53 – Zone transfer and large DNS responses  

Nmap can be used for host discovery, firewall detection, and DNS port scanning.

## FTP Enumeration Basics

<center>
  <img src="images/272.png" alt="2" width="600">
</center>

FTP (File Transfer Protocol) allows file transfer between client and server.

FTP Ports:
- TCP 21 – Control channel
- TCP 20 – Data channel

FTP is insecure because credentials are sent in plain text.

## Password Attacks

Dictionary Attack:
Uses predefined wordlists such as admin, root, and password.

<center>
  <img src="images/279.png" alt="2" width="600">
</center>

<center>
  <img src="images/278.png" alt="2" width="600">
</center>

<center>
  <img src="images/280.png" alt="2" width="600">
</center>

<center>
  <img src="images/281.png" alt="2" width="600">
</center>

<center>
  <img src="images/282.png" alt="2" width="600">
</center>


Brute Force Attack:
Attempts all possible combinations and is very slow for strong passwords.

Hybrid Attack:
Combines dictionary words with numbers or symbols such as admin123 or root@2026.

## Password List Generation (Crunch)

Crunch is used to generate custom password lists based on defined character sets and length.

<center>
  <img src="images/277.png" alt="2" width="600">
</center>

## Password Cracking Tools

Hydra:
Online password attack tool used against FTP, SSH, HTTP, and other services.

John the Ripper:
Offline password cracking tool used to crack hashed passwords.

## Custom Wordlist Generation (CeWL)

CeWL crawls websites and generates custom wordlists based on depth and minimum word length.

<center>
  <img src="images/275.png" alt="2" width="600">
</center>

<center>
  <img src="images/276.png" alt="2" width="600">
</center>



## Conclusion

DNS Enumeration is a critical phase in penetration testing that reveals domain structure, misconfigurations, and sensitive information. Combined with FTP enumeration and password attacks, it provides deep insight into target systems. Proper security configuration and strong access controls are essential to prevent exploitation.
