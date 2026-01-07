<div align="center">
  <h1>Day - 7 of CEH</h1>
</div>

## Advanced Footprinting, OSINT & Subdomain Enumeration

This repository contains detailed documentation for CEH Day 7, focusing on Advanced Footprinting, Open-Source Intelligence (OSINT), Google Dorking, and Subdomain Enumeration. All techniques discussed fall under passive reconnaissance, which is a critical phase in ethical hacking.

---

## 1. Censys

Censys is an internet-wide scanning and intelligence platform used to discover publicly exposed assets such as servers, websites, IoT devices, certificates, and services.

Website:
https://censys.io

<center>
  <img src="images/147.png" alt="1" width="600">
</center>

## For better usage of Censys we use : 

### Censys GPT?

Censys GPT is an AI-assisted feature or workflow that helps users generate structured Censys search queries automatically using natural language prompts.
Instead of manually writing complex filters, users can describe what they want to find, and Censys GPT converts it into a valid Censys query.

<center>
  <img src="images/148.png" alt="1" width="600">
</center>

Use Cases:
- Passive reconnaissance
- Identifying exposed infrastructure
- Understanding public-facing assets


<center>
  <img src="images/149.png" alt="1" width="600">
</center>

<center>
  <img src="images/150.png" alt="1" width="600">
</center>

---

## 2. Infoga (Email & OSINT Tool)

Infoga is an OSINT-based tool used for email harvesting, domain intelligence, and employee enumeration.

<center>
  <img src="images/151.png" alt="1" width="600">
</center>

<center>
  <img src="images/152.png" alt="1" width="600">
</center>

Usage:
python3 infoga.py -d <domain> -s <source>

<center>
  <img src="images/153.png" alt="1" width="600">
</center>


Relevance:
- Email pattern discovery
- Phishing simulation support
- Organization profiling

---

## 3. Archive.org (Wayback Machine)

Archive.org allows viewing historical versions of websites, which helps uncover deleted pages, old directories, and sensitive information removed over time.

Website:
https://archive.org

<center>
  <img src="images/154.png" alt="1" width="600">
</center>

<center>
  <img src="images/155.png" alt="1" width="600">
</center>

<center>
  <img src="images/156.png" alt="1" width="600">
</center>

---

## 4. Google Advanced Search (Google Dorking)

Google Dorking uses advanced Google search operators to find sensitive information exposed publicly.

### Examples:

site:example.com admin
filetype:pdf "linux basics for hackers"
filetype:xls password

<center>
  <img src="images/157.png" alt="1" width="600">
</center>

<center>
  <img src="images/158.png" alt="1" width="600">
</center>

Note:
Google Dorking is part of passive information gathering and must be used ethically.

---

## 5. Google Hacking Database (GHDB)

GHDB is a curated collection of predefined Google dorks used to locate login portals, backup files, configuration files, and exposed databases.

<center>
  <img src="images/159.png" alt="1" width="600">
</center>

<center>
  <img src="images/160.png" alt="1" width="600">
</center>


Relevance:
- Saves reconnaissance time
- Commonly referenced in CEH exams

---

## 6. Dork GPT

Dork GPT refers to using AI tools such as ChatGPT, SGPT, or TGPT to automatically generate effective Google dorks based on user intent.

<center>
  <img src="images/172.png" alt="1" width="600">
</center>

Advantages:
- Faster dork creation
- Beginner-friendly
- Improved OSINT accuracy

Example Prompt:
Generate Google dorks to find exposed admin panels

---

## 7. Subdomain Enumeration

Subdomain enumeration is the process of identifying hidden or undocumented subdomains, which may increase the attack surface.

<center>
  <img src="images/161.png" alt="1" width="600">
</center>

Tool:
Sublist3r

<center>
  <img src="images/162.png" alt="1" width="600">
</center>

<center>
  <img src="images/163.png" alt="1" width="600">
</center>

Usage:
sudo sublist3r -d example.com

Importance:
- Discovers hidden assets
- Identifies test or development environments

---

## 8. Netcraft

Netcraft is an OSINT platform used for DNS enumeration, subdomain discovery, and hosting or server intelligence.

Website:
https://searchdns.netcraft.com

<center>
  <img src="images/164.png" alt="1" width="600">
</center>

<center>
  <img src="images/165.png" alt="1" width="600">
</center>

<center>
  <img src="images/166.png" alt="1" width="600">
</center>

---

## 9. People Information Gathering (Spokeo)

Spokeo is an OSINT tool used to gather publicly available information about individuals.

<center>
  <img src="images/167.png" alt="1" width="600">
</center>

<center>
  <img src="images/168.png" alt="1" width="600">
</center>

Conditions:
- Paid service
- Data mainly for US citizens
- Educational use only

---

## 10. ChatGPT / SGPT / TGPT

AI-based tools assist CEH learners by generating Google dorks, explaining commands, and supporting automated learning.

<center>
  <img src="images/169.png" alt="1" width="600">
</center>

<center>
  <img src="images/170.png" alt="1" width="600">
</center>


Example:
tgpt "generate google dorks for exposed admin panels"

<center>
  <img src="images/171.png" alt="1" width="600">
</center>


---


## Conclusion

Advanced Footprinting and OSINT form the foundation of ethical hacking and penetration testing. The tools and techniques covered in CEH Day 7 focus entirely on passive reconnaissance, enabling the collection of valuable intelligence without direct interaction with target systems. Mastering these tools helps security professionals understand an organization’s digital footprint, prepare for real-world security assessments, and succeed in the CEH examination.

Disclaimer:
This documentation is for educational purposes only. Unauthorized or malicious use of the techniques discussed is illegal.

---
