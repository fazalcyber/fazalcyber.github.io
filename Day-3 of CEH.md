<div align="center">
  <h1>Day - 3 of CEH</h1>
</div>

---

## Linux User, Group & Permission Management (Kali Linux & Parrot OS)

### Objective
This document explains Linux **user management, group management, file permissions, package handling, and file searching commands**, which are critical for **privilege escalation, post-exploitation, and system hardening** in CEH.

---

## 🔹 1. User and Group Management Commands

### Add a New User
Use `sudo adduser <username>` to create a new user along with a home directory and password.

<center>
  <img src="images/56.png" alt="Hacking" width="600">
</center>

---

### Add a New Group
Use `sudo addgroup <groupname>` to create a new group in the system.

<center>
  <img src="images/57.png" alt="Hacking" width="600">
</center>

---

### Check Group Membership of a User
Use `groups <username>` to view all groups a user belongs to.

<center>
  <img src="images/58.png" alt="Hacking" width="600">
</center>

---

### Add User to a Group (Kali & Parrot OS)
Use `sudo usermod -aG <groupname> <username>`

- `-a` means append (keeps existing groups)
- `-G` specifies the group name

 Always use `-aG` together, otherwise existing groups will be removed.

<center>
  <img src="images/59.png" alt="Hacking" width="600">
</center>

---

### Remove User from a Group (Kali Linux Only)
Use `sudo usermod -rG <groupname> <username>`

- `-r` means remove
- This option is **not available in Parrot OS**

<center>
  <img src="images/60.png" alt="Hacking" width="600">
</center>

---

### Add User to Group in Parrot OS
Use `sudo gpasswd -a <username> <groupname>`

---

### Remove User from Group in Parrot OS
Use `sudo gpasswd -d <username> <groupname>`

<center>
  <img src="images/61.png" alt="Hacking" width="600">
</center>

---

### Delete a User
Use `sudo deluser <username>`

<center>
  <img src="images/62.png" alt="Hacking" width="600">
</center>

 This command does **not remove user files**.

To delete user files manually, use  
`sudo rm -rf /home/<username>`

<center>
  <img src="images/63.png" alt="Hacking" width="600">
</center>

---

### Change User Password
Use `passwd <username>` to change or reset a user password.

<center>
  <img src="images/64.png" alt="Hacking" width="600">
</center>

---

## 🔹 2. System User Information Files

### Operating System Information
Use `cat /etc/os-release` to display OS name, version, and ID.

<center>
  <img src="images/65.png" alt="Hacking" width="600">
</center>

---

### User Account Details
Use `cat /etc/passwd` to view all users in the system.

<center>
  <img src="images/66.png" alt="Hacking" width="600">
</center>

#### Example Entry
`root:x:0:0:root:/root:/bin/bash`

#### Explanation of Fields

| Field | Meaning |
|------|--------|
| root | Username |
| x | Password stored in `/etc/shadow` |
| 0 | User ID (UID) |
| 0 | Group ID (GID) |
| root | User description |
| /root | Home directory |
| /bin/bash | Default shell |

---

### Password Hash File
Use `sudo cat /etc/shadow`

This file stores **hashed passwords** and is readable only by the root user.

<center>
  <img src="images/67.png" alt="Hacking" width="600">
</center>

---

## 🔹 3. File Searching Commands

### Locate Command
Use `locate <filename>` to quickly find files using a database.

Before using locate, update the database with  
`sudo updatedb`

<center>
  <img src="images/68.png" alt="Hacking" width="600">
</center>

---

### Find Command
Use  
`find / -name <filename> -type f 2>/dev/null`

- `/` starts searching from root
- `-type f` searches files
- `-type d` searches directories
- `2>/dev/null` hides permission errors

<center>
  <img src="images/69.png" alt="Hacking" width="600">
</center>

---

## 🔹 4. Linux File Permissions

### Permission Values

| Permission | Symbol | Value |
|-----------|--------|-------|
| Read | r | 4 |
| Write | w | 2 |
| Execute | x | 1 |

---

### Permission Categories

| Symbol | Description |
|------|-------------|
| u | User |
| g | Group |
| o | Others |

---

### Permission Structure Explanation

`- --- --- ---`

- First character indicates file or directory
- Second group is user permissions
- Third group is group permissions
- Fourth group is others permissions

---

### Modify Permissions Using Symbols

- Add permission: `chmod u+r <filename>`
- Remove permission: `chmod g-w <filename>`
- Execute permission: `chmod o+x <filename>`

<center>
  <img src="images/70.png" alt="Hacking" width="600">
</center>

<center>
  <img src="images/71.png" alt="Hacking" width="600">
</center>
---

### Modify Permissions Using Numbers

Use numeric values based on permission sums.

Example:  
`chmod 300 <filename>`

- User → Write only
- Group → No permission
- Others → No permission

<center>
  <img src="images/72.png" alt="Hacking" width="600">
</center>

Example:  
`chmod 731 <filename>`

- User → Read, Write, Execute
- Group → Write only
- Others → Execute only

<center>
  <img src="images/73.png" alt="Hacking" width="600">
</center>

---

### List Directory Permissions
Use `ls -ld <directory>` to view directory permissions.

<center>
  <img src="images/74.png" alt="Hacking" width="600">
</center>

---

## 5. Package Management Commands (APT)

### Update Repository
Use `sudo apt update` to refresh package lists.

<center>
  <img src="images/75.png" alt="Hacking" width="600">
</center>

---

### Install a Package
Use `sudo apt install <package_name>`

<center>
  <img src="images/76.png" alt="Hacking" width="600">
</center>

---

### Search for a Package
Use `apt-cache search <toolname>`

<center>
  <img src="images/77.png" alt="Hacking" width="600">
</center>

---

### View Package Details
Use `apt show <toolname>`

<center>
  <img src="images/78.png" alt="Hacking" width="600">
</center>

---

### Remove a Package
Use `sudo apt remove <toolname>`

<center>
  <img src="images/79.png" alt="Hacking" width="600">
</center>

This removes the package but keeps configuration files.

---

### Remove Package with Configuration Files
Use  
`sudo apt purge <toolname>`  
or  
`sudo apt --purge remove <toolname>`

<center>
  <img src="images/80.png" alt="Hacking" width="600">
</center>

---

## 6. Installing Tools from GitHub

When a tool is not available in the OS repository, install it from GitHub.

### Steps
1. Open Firefox

<center>
  <img src="images/81.png" alt="Hacking" width="600">
</center>

2. Search for `<toolname> GitHub`

<center>
  <img src="images/82.png" alt="Hacking" width="600">
</center>

3. Open the official repository

4. Copy the repository URL

<center>
  <img src="images/83.png" alt="Hacking" width="600">
</center>

5. Clone the repository using  
   `git clone <repository_link>`
   
<center>
  <img src="images/84.png" alt="Hacking" width="600">
</center>

---

##  CEH Practical Importance

- User enumeration
- Privilege escalation
- Password attacks
- Linux system hardening
- Post-exploitation techniques

---


