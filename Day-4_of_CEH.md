<div align="center">
  <h1>Day - 4 of CEH</h1>
</div>

# Network Anonymity & Privacy – Tools and Concepts Documentation

---

## 1. Installing Tools Without `git clone` (Using `.deb` Package)

In Linux, tools can be installed without using GitHub or git clone by directly installing package files.

### Example: Angry IP Scanner Installation (Linux)

### Steps

1. Download Angry IP Scanner from the official website using the `.deb` package.

<center>
  <img src="images/85.png" alt="steps for hacking" width="600">
</center>

<center>
  <img src="images/86.png" alt="steps for hacking" width="600">
</center>

2. Go to the Downloads directory.
3. List the downloaded files.
4. Identify the `.deb` package file.
5. Install the package using dpkg with the install option.
      - dpkg -i <package name> refers to install.

      <center>
        <img src="images/87.png" alt="steps for hacking" width="600">
      </center>

6. Verify installation by searching the tool in the system search bar.

<center>
  <img src="images/88.png" alt="steps for hacking" width="600">
</center>

---

## 2. Spoofing

### What is Spoofing?

Spoofing is a technique used to falsify identity information in order to impersonate another system or device on a network.

---

### IP Spoofing

- The attacker modifies the source IP address of network packets.
- Used to hide identity or bypass IP-based restrictions.
- Common in DDoS attacks and session hijacking.

---

### MAC Spoofing

- The attacker changes the MAC address of a network interface.
- Used to bypass MAC filtering and impersonate trusted devices.

---

### Important Note

Whenever an attack is performed on a server, the public IP address is logged.  
Using this public IP address, attackers can be tracked.

<center>
  <img src="images/89.png" alt="steps for hacking" width="600">
</center>
 
<center>
  <img src="images/ip explai.jpeg" alt="steps for hacking" width="600">
</center>


To check the public IP address:
- Visit whatismyipaddress
- The result will be the same in Parrot OS and Windows.

<center>
  <img src="images/90.png" alt="steps for hacking" width="600">
</center>


---

## 3. Proxy

### What is a Proxy?

A proxy server acts as an intermediary between a user and the internet, masking the real IP address.
 
<center>
  <img src="images/proxy.jpeg" alt="steps for hacking" width="600">
</center>


---

### Types of Proxies

1. Paid Proxy  
   - Usually does not store logs  
   - Faster and more reliable  

2. Free Proxy  
   - May or may not store logs  
   - Slower and less secure  
 
---

### Configuring Proxy in Firefox (Parrot OS)

1. Open Firefox.
2. Search for Free Proxy List.
  
<center>
  <img src="images/91.png" alt="steps for hacking" width="600">
</center>

3. Copy the proxy IP address and port number.
4. Open Firefox Settings.
5. Search for Proxy.
6. Open Network Settings.
7. Select Manual Proxy Configuration.
8. Paste the IP address in HTTP Proxy and the port number.
  
<center>
  <img src="images/92.png" alt="steps for hacking" width="600">
</center>

9. Enable HTTPS proxy.
10. Save the settings.
11. Verify the IP change using whatismyipaddress.
12. Disable proxy by selecting Use system proxy settings.
  
<center>
  <img src="images/93.png" alt="steps for hacking" width="600">
</center>

---

## 4. VPN (Virtual Private Network)

### What is VPN?

A VPN encrypts internet traffic and hides the real IP address, providing privacy and anonymity.
 
<center>
  <img src="images/vpn.jpeg" alt="steps for hacking" width="600">
</center>


---

### Free VPN (Browser-Based)

#### Example: VeePN for Firefox

1. Search for VeePN Firefox.
2. Open the official link.
3. Click Add to Firefox.
4. Accept permissions.
5. Open the extension.
  
<center>
  <img src="images/94.png" alt="steps for hacking" width="600">
</center>

6. Click Connect.
7. Verify the IP address using whatismyipaddress.
  
<center>
  <img src="images/95.png" alt="steps for hacking" width="600">
</center>


---

## 5. Proton VPN Installation (Linux / Parrot OS)

### Account Creation

1. Visit the Proton VPN website.
2. Click Get Proton VPN.
3. Select Proton Free.
4. Create an account.
5. Complete verification if required.
6. Set a password.

---

### Download OpenVPN Configuration File

1. Go to the Downloads page.
2. Select Platform as Linux.
3. Choose protocol UDP or TCP.
  
<center>
  <img src="images/96.png" alt="steps for hacking" width="600">
</center>

4. Select a server with low load.
  
<center>
  <img src="images/97.png" alt="steps for hacking" width="600">
</center>

5. Download the `.ovpn` configuration file.

---

### Import VPN Configuration (GUI Method)

1. Open Network Connections.
2. Go to VPN and select Import VPN.
3. Choose the downloaded `.ovpn` file.
  
<center>
  <img src="images/98.png" alt="steps for hacking" width="600">
</center>

4. Enter the Proton VPN username (IKEv2 username) and password.
5. Start the VPN connection.

---

### Terminal Method (If GUI Fails)

1. Start the VPN using the OpenVPN configuration file.
2. If the message "Initialization Sequence Completed" appears, the VPN is connected.
 
<center>
  <img src="images/99.png" alt="steps for hacking" width="600">
</center>
 
<center>
  <img src="images/100.png" alt="steps for hacking" width="600">
</center>

3. Stop the VPN using Ctrl + C.
4. Verify the connection using whatismyipaddress.
 
<center>
  <img src="images/101.png" alt="steps for hacking" width="600">
</center>

---

## 6. Types of Web
 
<center>
  <img src="images/surface.jpeg" alt="steps for hacking" width="600">
</center>


### Surface Web

- Indexed by search engines
- Publicly accessible
- Examples: Google, Wikipedia, YouTube

---

### Deep Web

- Not indexed by search engines
- Requires authentication
- Examples: Gmail, banking portals, college portals

---

### Dark Web

- Requires special browsers
- Provides anonymity
- Contains both legal and illegal content

---

## 7. Tor (The Onion Router)

### What is Tor?

Tor routes internet traffic through multiple encrypted nodes, hiding the user's identity.
 
<center>
  <img src="images/tor.jpeg" alt="steps for hacking" width="600">
</center>


---

### Installing Tor Browser (Parrot OS)

1. Open Firefox.
2. Search for Tor Browser Linux.
 
<center>
  <img src="images/102.png" alt="steps for hacking" width="600">
</center>
 
<center>
  <img src="images/103.png" alt="steps for hacking" width="600">
</center>

3. Download the `.xz` file.
 
<center>
  <img src="images/104.png" alt="steps for hacking" width="600">
</center>

4. Fix broken packages.
5. Install xz utilities.
6. Extract the downloaded file.

---

### Meaning of `-xf`

- `-x` means extract.
- `-f` specifies the file name.

---

### Launching Tor Browser

1. Open the Tor Browser directory.
2. Start the Tor Browser launcher.
3. Click Connect.
 
<center>
  <img src="images/105.png" alt="steps for hacking" width="600">
</center>
 
<center>
  <img src="images/106.png" alt="steps for hacking" width="600">
</center>

4. Wait for the Tor network connection.

---

### Accessing the Dark Web

1. Open Chrome.
2. Search for Hidden Wiki.
3. Copy any `.onion` link.
4. Paste the link into Tor Browser.
5. The site will open only inside Tor Browser.

---

## Conclusion

- `.deb` packages can be used instead of git clone.
- Spoofing hides identity but public IP addresses are traceable.
- Proxies provide limited anonymity.
- VPNs encrypt traffic and hide IP addresses.
- Tor provides maximum anonymity.
- Dark Web access is possible only through Tor Browser.
