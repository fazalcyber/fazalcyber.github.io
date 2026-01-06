<div align="center">
  <h1>Day - 5 of CEH</h1>
</div>

# Footprinting and Reconnaissance

## 1. What is Footprinting?
Footprinting is the first phase of ethical hacking and penetration testing. It involves gathering as much information as possible about a target system, network, or organization before attempting any attack. The goal is to understand the target’s infrastructure and reduce uncertainty.

<center>
  <img src="images/107.jpg" alt="Footprinting" width="600">
</center>

Footprinting can be:
- **Passive**: Information gathering without directly interacting with the target (low risk of detection).
- **Active**: Direct interaction with the target system (higher accuracy, higher risk of detection).

---

## 2. Types of Footprinting

<center>
  <img src="images/108.png" alt="Types of Footprinting" width="600">
</center>

### 2.1 Passive Footprinting
- WHOIS lookup
- Search engines (Google, Bing)
- Social media
- Public records
- DNS information from public sources

### 2.2 Active Footprinting
- Ping
- Traceroute
- Network scanning
- Banner grabbing
- Website technology detection

---

## 3. Footprinting Methodologies

1. **Identify the Target**
   - Domain name
   - Organization name

2. **Collect Network Information**
   - IP address
   - Network range
   - DNS records

3. **Collect System Information**
   - Operating system
   - Server type
   - Web technologies

4. **Collect Organizational Information**
   - Employees
   - Email addresses
   - Contact details

5. **Document the Information**
   - Useful for vulnerability analysis and later attack phases

---

## 4. Information Obtained in Footprinting
- Domain name details
- IP address (public IP)
- Network topology
- Server location
- Operating system and web server
- CMS and framework details
- Cloud usage (IaaS / PaaS)

<center>
  <img src="images/109.jpg" alt="Information Obtained in Footprinting" width="600">
</center>

---

## 5. Using Ping Command

### Purpose of Ping
- To check whether a system is connected to the network
- To verify whether a website or host is responding

### Syntax
```
ping <website-name>
ping <ip-address>
```

### Examples
```
ping google.com
ping vignaniit.edu.in
ping iare.ac.in
```

<center>
  <img src="images/110.png" alt="Ping" width="600">
</center>

### Key Points
- Ping can be performed using **domain name** or **IP address**
- From ping results, we can identify the **public IP address** of a website
- If the IP address looks like **1.1.x.x**, it usually indicates the website is hosted on a **paid cloud server**

---

## 6. Finding Websites on the Same Server

To find how many websites are running on the same web server:

- Use **Bing search engine**
- Search format:
```
ip:<ip-address>
```

<center>
  <img src="images/111.png" alt="same ip address search" width="600">
</center>

<center>
  <img src="images/112.png" alt="many websites are running on the same web server" width="600">
</center>

This technique is known as **Reverse IP Lookup**.

---

## 7. Route Command

### route -n
- Displays the routing table
- Shows how packets are routed inside the network
- Helps understand network paths and gateways

---

<center>
  <img src="images/113.png" alt="route -n" width="600">
</center>

## 8. Wappalyzer Installation (Parrot OS – Firefox)

### Steps
1. Open **Firefox** in Parrot OS
2. Go to Firefox Add-ons
3. Search for **Wappalyzer**

<center>
  <img src="images/114.png" alt="Wappalyzer Firefox" width="600">
</center>

4. Install the extension
5. Pin it to the Firefox toolbar
6. Open any website
7. Click on Wappalyzer icon to view technologies used

<center>
  <img src="images/115.png" alt="Wappalyzer icon to view technologies used" width="600">
</center>

### Information Revealed
- Web server
- Programming language
- CMS
- Frameworks
- Analytics tools

---

## 9. Vulnerability Insight from Technologies
- Websites that reveal **version numbers** may be vulnerable
- Vulnerabilities can be found by searching:
  - `software-name version vulnerability`
- Websites running on **cloud servers** often use **IaaS** or **PaaS**
- Websites using **CMS (WordPress, Joomla, etc.)** may expose admin pages

Example:
```
/wp-login
```

---

## 10. WHOIS Command

### Syntax
```
whois <website-name>
```

<center>
  <img src="images/116.png" alt="WHOIS Command" width="600">
</center>

<center>
  <img src="images/117.png" alt="WHOIS Command" width="600">
</center>

### Information Obtained
- Domain owner name
- Organization
- Email address
- Phone number
- Domain registration and expiry dates
- Name servers

### Alternatives
- Online WHOIS lookup websites

---

## 11. Hiding WHOIS Information

- Domain owners can hide details using **WHOIS privacy protection** (paid)
- Fake information can be generated using:
  - Fake Name Generator

<center>
<img src="images/118.png" alt="Fake Name Generator" width="600">
</center>

<center>
<img src="images/119.png" alt="Fake Name Generator" width="600">
</center>

- For profile pictures (DP):
  - `this-person-does-not-exist`

<center>
<img src="images/120.png" alt="this-person-does-not-exist" width="600">
</center>

<center>
<img src="images/121.png" alt="this-person-does-not-exist" width="600">
</center>
---

## 12. Obtaining IP Address Using Grabify

### Purpose
- To capture IP address of a person who clicks a link

### Basic Steps
1. Visit Grabify website

<center>
<img src="images/122.png" alt="Grabify website" width="600">
</center>

2. Enter any URL

<center>
<img src="images/123.png" alt="Enter any URLto be changed" width="600">
</center>

3. Generate tracking link

<center>
<img src="images/124.png" alt="generates a fake link" width="600">
</center>

4. Share the link with the target
5. When the target clicks, IP details are logged

### Additional Note
- The target can check their own IP using:
  - whatismyipaddress website

---

## 13. Hound Tool (Parrot OS)

### Purpose
- Works similar to Grabify
- Provides IP address and map location

### Steps
1. Clone the tool

<center>
<img src="images/125.png" alt="hound website" width="600">
</center>

<center>
<img src="images/126.png" alt="Clone the tool" width="600">
</center>

2. Navigate to the directory
```
cd hound
```
3. Give execution permission
```
chmod +x hound.sh
```
4. Verify permission
```
ls -la hound.sh
```
5. Execute the tool
```
./hound.sh
```
<center>
<img src="images/127.png" alt="Execute the tool" width="600">
</center>
---

## 14. “I Know What You Download” Website

### Purpose
- Shows torrent or download activity associated with a public IP address

<center>
<img src="images/128.png" alt="I Know What You Download website" width="600">
</center>

<center>
<img src="images/129.png" alt="I Know What You Download website" width="600">
</center>

### Key Point
- Information is based on **public IP logs**
- Results may not always be accurate

---

## 15. Summary
Footprinting and reconnaissance are crucial initial phases in ethical hacking. They help attackers and security professionals understand the target environment, identify potential vulnerabilities, and plan further actions efficiently while minimizing risks.

