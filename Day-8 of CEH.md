<div align="center">
  <h1>Day - 8 of CEH</h1>
</div>
## Module 3: Scanning Networks

## What is a Network?

A **network** is a collection of connected devices such as:

- Computers
- Servers
- Routers
- Switches

These devices communicate with each other to share data and resources.

<center>
  <img src="images/173.png" alt="Network" width="600">
</center>

---

## Packet-Based Communication

In computer networks, data is not sent as a whole.  
It is divided into small units called **packets**.

### Example

- Website data is divided into packets (P1, P2, P3)
- Packets travel across the network
- Receiver reassembles packets into original data

---

## Network Interface Controller (NIC)

### Definition

A **Network Interface Controller (NIC)** is a hardware component that connects a device to a network.

<center>
  <img src="images/174.png" alt="Network Interface Controller" width="600">
</center>

### Key Points

- Connected to motherboard / CPU
- Activated when Ethernet or Wi-Fi is connected
- Each NIC has a unique MAC address

### Commands

#### Windows
- ipconfig

<center>
  <img src="images/175.png" alt="ip Address" width="600">
</center>

- ipconfig /all

<center>
  <img src="images/176.png" alt="Mac Adress" width="600">
</center>

<center>
  <img src="images/177.png" alt="Mac Adress" width="600">
</center>

#### Linux / Parrot OS
- ifconfig

<center>
  <img src="images/178.png" alt="ifconfig command" width="600">
</center>
- ip a

<center>
  <img src="images/179.png" alt="ip a command" width="600">
</center>

---

## MAC Address

- MAC stands for Media Access Control address
- Physical address
- Assigned to NIC

### Example
- 00:27:54:C1:7F:1A

---

## Protocols

### Definition

A **protocol** is a set of rules and regulations that devices follow to communicate.

### Examples

- TCP/IP
- HTTP / HTTPS
- FTP
- ICMP
- ARP

---

## Network Devices

### Hub
- Old and basic device
- Broadcasts data to all devices
- Less secure and inefficient

<center>
  <img src="images/180.png" alt="Hub" width="600">
</center>

### Switch
- Smarter than hub
- Sends data only to the intended device using MAC address
- Faster and more secure

<center>
  <img src="images/181.png" alt="Switch" width="600">
</center>

### Router
- Connects multiple networks
- Routes data using IP addresses
- Connects LAN to the Internet

<center>
  <img src="images/182.png" alt="Router" width="600">
</center>

---

## What is Network Scanning?

**Network scanning** is the process of collecting network-related information about a target.

### Information Gathered

- Live hosts
- IP addresses
- Open ports
- Running services
- Vulnerabilities

---

## Types of Scanning (CEH Important)

<center>
  <img src="images/183.png" alt="Types of Scanning" width="600">
</center>

### Network Scanning
- Identifies live systems

### Port Scanning
- Identifies open and closed ports

### Vulnerability Scanning
- Identifies weaknesses in systems and services

---

## IP Address

### Definition

An **IP address (Internet Protocol address)** is a unique identifier assigned to each device on a network.

---

## IPv4 and IPv6

### IPv4
- 32-bit address
- Example: 192.168.1.1

<center>
  <img src="images/184.png" alt="IPv4" width="600">
</center>

### IPv6
- 128-bit address
- Larger address space
- Example: 2001:0db8:85a3::8a2e:0370:7334

<center>
  <img src="images/185.png" alt="IPv6" width="600">
</center>

---

## IPv4 Address Classification

<center>
  <img src="images/189.png" alt="IPv4 Address Classification" width="600">
</center>

---

## IPv4 Address Structure

- Network part
- Host part

<center>
  <img src="images/204.png" alt="IPv4 Address Structure" width="600">
</center>

---

## Subnet Mask

### Definition

A **subnet mask** identifies:

- Network portion
- Host portion

### Example
- 255.255.255.0

<center>
  <img src="images/205.png" alt="Subnet Mask" width="600">
</center>

### Meaning
- 255 → Network bits
- 0 → Host bits

---

## Private and Public IP Address

### Private IP Ranges

- Class A: 10.0.0.0 – 10.255.255.255
- Class B: 172.16.0.0 – 172.31.255.255
- Class C: 192.168.0.0 – 192.168.255.255

### Public IP
- Assigned by ISP
- Used on the Internet

---

## Communication Types

### Unicast
Communication where data is sent from one sender to one specific receiver.  
Example: Client accessing a web server.

### Multicast
Communication where data is sent from one sender to multiple selected receivers.  
Example: Live video streaming to subscribed users.

### Broadcast
Communication where data is sent from one sender to all devices in the network.  
Example: ARP request in a local network.

---

## CIDR Conversion

CIDR conversion is the method of representing an IP address with a prefix length using `/` notation to specify the number of network bits, allowing flexible subnetting and efficient IP usage.

<center>
  <img src="images/202.png" alt="CIDR" width="600">
</center>

<center>
  <img src="images/203.png" alt="CIDR" width="600">
</center>

---

## Ping Command

### Purpose
- Checks whether a host is alive
- Uses ICMP packets

### Command Format
- ping <IP address>

<center>
  <img src="images/186.png" alt="PING command" width="600">
</center>

### Useful Options
- ping -h
- ping -a
- ping -c 4

<center>
  <img src="images/187.png" alt="PING command" width="600">
</center>

<center>
  <img src="images/188.png" alt="PING command" width="600">
</center>

### Note
Many systems block ICMP to prevent DoS/DDoS attacks.

---

## ARP (Address Resolution Protocol)

### What is ARP?

ARP is a network protocol used to map an IP address to its corresponding MAC address within a local network.

<center>
  <img src="images/193.png" alt="ARP" width="600">
</center>

### ARP Mapping
- IP address → MAC address

### Why ARP is Required?
Devices communicate using MAC addresses within a local network.

### ARP Request and Reply
- ARP Request → Broadcast
- ARP Reply → Unicast

<center>
  <img src="images/190.png" alt="ARP" width="600">
</center>

<center>
  <img src="images/191.png" alt="PING command" width="600">
</center>

<center>
  <img src="images/192.png" alt="PING command" width="600">
</center>

---

## Network Scanning Tools

### Netdiscover

Netdiscover is a network discovery tool used to identify live hosts, IP addresses, and MAC addresses using ARP requests.

- Basic syntax: netdiscover
- Scan range: netdiscover -r <IP_range>
- Example: 192.168.1.0/24

<center>
  <img src="images/194.png" alt="Netdiscover" width="600">
</center>

<center>
  <img src="images/195.png" alt="Netdiscover" width="600">
</center>
---

### Angry IP Scanner

Angry IP Scanner is used to quickly discover live hosts and open ports in a network by scanning a given IP range.

### Installation Using Firefox

1. Open Firefox
2. Search for Angry IP Scanner

<center>
  <img src="images/196.png" alt="search Angry IP Scanner" width="600">
</center>

3. Open the official website: https://angryip.org

<center>
  <img src="images/197.png" alt="open Angry IP Scanner" width="600">
</center>

4. Go to Download section
5. Select your operating system
6. Download and install
7. Launch the tool

<center>
  <img src="images/198.png" alt="install Angry IP Scanner" width="600">
</center>

8. Verify by scanning an IP range

<center>
  <img src="images/199.png" alt="Angry IP Scanner" width="600">
</center>

<center>
  <img src="images/200.png" alt="Angry IP Scanner" width="600">
</center>

<center>
  <img src="images/201.png" alt="open Angry IP Scanner" width="600">
</center>

### Color Indication
- Blue → Alive hosts
- Green → Open ports

---

## Summary (Keywords)

- Network and Packets
- NIC and MAC Address
- Protocols (TCP/IP, ICMP, ARP)
- Network Scanning
- IP Addressing (IPv4, IPv6, CIDR)
- Netdiscover and Angry IP Scanner
