<div align="center">
  <h1>Day - 2 of CEH</h1>
</div>

# Part 1: Parrot OS Virtual Machine Settings (VirtualBox)

---

## Step 1: Adjust System RAM

Optimizing RAM ensures that **Parrot OS runs smoothly**, especially while using **resource-intensive security and penetration-testing tools**.

### Steps:
1. Open **VirtualBox** and select your **Parrot OS virtual machine**.
2. Click the **Settings** (gear icon).
3. Navigate to **System** from the left sidebar.
4. Under the **Motherboard** tab, adjust **Base Memory**:
   - **Recommended:** `4096 MB (4 GB)` or higher
5. Click **OK** to save changes.

<center>
  <img src="images/19.png" alt="Hacking" width="600">
</center>

---

## Step 2: Network Configuration

Configuring the network in **Bridged Mode** allows the virtual machine to behave like a **separate device on your physical network**.

### Steps:
1. Open **Settings** for Parrot OS.
2. Go to the **Network** tab.
3. Under **Adapter 1**, ensure **Enable Network Adapter** is checked.
4. In the **Attached to:** dropdown, select **Bridged Adapter**.
5. In the **Name:** dropdown, choose your active interface:
   - Physical **Wi-Fi** or **Ethernet** adapter
6. Click **OK**.

**Purpose:**  
Enables Parrot OS to receive a **dedicated IP address from the local router**, just like the host machine.

<center>
  <img src="images/20.png" alt="Hacking" width="600">
</center>

---

## Step 3: Enable Shared Clipboard

The shared clipboard improves productivity by allowing **text transfer between the Host OS and the Virtual Machine**.

### Steps:
1. Start the **Parrot OS virtual machine**.
2. In the VM’s top menu bar, click **Devices**.
3. Select **Shared Clipboard**.
4. Choose **Bidirectional**.

**Purpose:**  
Allows seamless **copy–paste functionality** between Host OS and Parrot OS.

<center>
  <img src="images/21.png" alt="Hacking" width="600">
</center>

---

# Part 2: Basic Network Commands

---

## `ifconfig`

The `ifconfig` (**interface configuration**) command is a **classic Linux networking tool** used to view and configure network interfaces.

### Purpose:
- Displays all network interfaces available on the system
- Shows IP address and network configuration details

### Information Displayed:
- Interface names (e.g., `eth0`, `wlan0`, `lo`)
- IP address (`inet`)
- MAC address
- Packet statistics

### Important Notes:
- `lo` → Loopback interface (`127.0.0.1`)
- `inet` → IPv4 address assigned to the interface

<center>
  <img src="images/22.png" alt="Hacking" width="600">
</center>

---

## `ping`

**Purpose:**  
Checks whether the system is connected to the network or internet.

**How it works:**  
Sends ICMP echo requests and receives replies.

**To stop ping:**  
`Ctrl + C`

<center>
  <img src="images/24.png" alt="Hacking" width="600">
</center>

<center>
  <img src="images/24.png" alt="Hacking" width="600">
</center>

---

## `ip a`

**Purpose:**  
Modern replacement for `ifconfig`.

**What it does:**  
- Shows IP address, interfaces, and network state  
- Recommended in modern Linux distributions

<center>
  <img src="images/23.png" alt="Hacking" width="600">
</center>

---

## `clear`

**Purpose:**  
- Clears all previous output from the terminal screen  
- Does not delete command history

---

## `ipconfig`

**Purpose:**  
- ❌ Not a Linux command  
- ✔ Used in **Windows** to view IP details

---

# Part 3: System Information Commands

---

## `whoami`

**Purpose:**  
- Shows the currently logged-in user  
- Useful to confirm privilege level

<center>
  <img src="images/26.png" alt="Hacking" width="600">
</center>

---

## `hostname`

**Purpose:**  
- Displays the system’s hostname  
- Important in network identification

<center>
  <img src="images/27.png" alt="Hacking" width="600">
</center>

---

## `uname -a`

**Purpose:**  
Displays complete system information.

**Shows:**
- Kernel version  
- Architecture  
- OS name  

*Helps attackers identify kernel vulnerabilities.*

<center>
  <img src="images/28.png" alt="Hacking" width="600">
</center>

---

## `date`

**Purpose:**  
- Shows current system date and time  
- Used for log analysis and timestamps

<center>
  <img src="images/29.png" alt="Hacking" width="600">
</center>

---

## `service <service_name> start | stop | restart | status`

**Purpose:**  
- Manages background services  
- Used to start web servers, databases, etc.

<center>
  <img src="images/31.png" alt="Hacking" width="600">
</center>

---

## `history`

**Purpose:**  
- Displays previously executed commands  
- Attackers can view past commands if access is gained

<center>
  <img src="images/30.png" alt="Hacking" width="600">
</center>

---

## `top`

**Purpose:**  
Shows running processes in real time.

**Displays:**
- CPU usage  
- Memory usage  
- Process IDs  

*Used to detect suspicious processes.*

<center>
  <img src="images/32.png" alt="Hacking" width="600">
</center>

---

## `htop`

**Purpose:**  
- Advanced version of `top` with GUI-style interface  
- Allows process killing using keyboard

<center>
  <img src="images/33.png" alt="Hacking" width="600">
</center>

---

## `Ctrl + C`

**Purpose:**  
- Stops a running command or process  
- Used frequently during scans and pings

---

# Part 4: Linux Directory Structure

---

<center>
  <img src="images/dir.png" alt="Hacking" width="600">
</center>

## `/`
Root directory — base of the entire Linux filesystem.

## `/root`
Home directory of the **root user**.

## `/home`
Contains home directories of normal users.

## `/bin`
Essential executable binaries (`ls`, `cat`, `cp`).

## `/sbin`
System binaries used by root user only.

## `/usr`
User system resources and applications.

## `/etc`
System configuration files.

## `/lib`
Library files required by binaries.

## `/var`
Log files and variable data.

## `/opt`
Optional third-party software.

## `/tmp`
Temporary files (cleared on reboot).

## `/media`
Mounted external devices (USB, CD).

---

# Part 5: File & Directory Commands

---

## `pwd`

**Purpose:**  
Shows current working directory.

<center>
  <img src="images/34.png" alt="Hacking" width="600">
</center>

---

## `ls`

Lists files and directories.

**Examples:**

ls

<center>
  <img src="images/35.png" alt="Hacking" width="600">
</center>

ls -l

<center>
  <img src="images/36.png" alt="Hacking" width="600">
</center>

ls -a

<center>
  <img src="images/37.png" alt="Hacking" width="600">
</center>

ls -la

<center>
  <img src="images/38.png" alt="Hacking" width="600">
</center>


### `ls --help`

**Purpose:**  
Shows help information for the `ls` command.

<center>
  <img src="images/39.png" alt="Hacking" width="600">
</center>

---

### `man <command>`

**Purpose:**  
Displays the manual (documentation) page of a command.

<center>
  <img src="images/40.png" alt="Hacking" width="600">
</center>

---

### `whatis <command>`

**Purpose:**  
Displays a one-line description of a command.

<center>
  <img src="images/41.png" alt="Hacking" width="600">
</center>

---

### `$` and `#`

**User symbols in the Linux terminal:**
- `$` → Normal user
- `#` → Root (superuser)

---

### `cd`

**Purpose:**  
Changes the current working directory.

**Examples:**
- `cd`

<center>
  <img src="images/42.png" alt="Hacking" width="600">
</center>

- `cd ..`

<center>
  <img src="images/43.png" alt="Hacking" width="600">
</center>

- `cd /home/user`

<center>
  <img src="images/44.png" alt="Hacking" width="600">
</center>


---

### Absolute vs Relative Path

- **Absolute Path:**  
  Starts from the root directory  
  `/home/user/file`

- **Relative Path:**  
  Based on the current directory  
  `../file`

---

### `&&`

**Purpose:**  
Runs multiple commands sequentially.  
The next command executes only if the previous command is successful.

<center>
  <img src="images/45.png" alt="Hacking" width="600">
</center>

---

### `mkdir`

**Purpose:**  
Creates a new directory.

<center>
  <img src="images/46.png" alt="Hacking" width="600">
</center>

---

### `touch`

**Purpose:**  
Creates an empty file.

<center>
  <img src="images/47.png" alt="Hacking" width="600">
</center>

---

### `cat`

**Purpose:**  
Displays the contents of a file.  
*Read-only display.*

<center>
  <img src="images/48.png" alt="Hacking" width="600">
</center>

---

### `pluma`

**Purpose:**  
Graphical (GUI) text editor available in Parrot OS.

<center>
  <img src="images/49.png" alt="Hacking" width="600">
</center>

---

### `nano`

**Purpose:**  
Terminal-based text editor available in all Linux distributions.

<center>
  <img src="images/50.png" alt="Hacking" width="600">
</center>

---

### `sudo su`

**Purpose:**  
Switches the current user to the root (superuser).

<center>
  <img src="images/51.png" alt="Hacking" width="600">
</center>

---

### `cp`

**Purpose:**  
Copies files or directories.

<center>
  <img src="images/52.png" alt="Hacking" width="600">
</center>

---

### `rm`

**Purpose:**  
Deletes a file.

<center>
  <img src="images/54.png" alt="Hacking" width="600">
</center>

---

### `rmdir`

**Purpose:**  
Deletes an empty directory.

<center>
  <img src="images/55.png" alt="Hacking" width="600">
</center>

---

### `mv`

**Purpose:**  
Moves or renames files and directories.

<center>
  <img src="images/53.png" alt="Hacking" width="600">
</center>

---

### `rm -rf`

**Purpose:**  
Forcefully deletes directories along with their contents.  
**Very dangerous command – use with extreme caution.**

---

## NOTE

All these commands are **foundation commands** required for:

- Kali / Parrot OS usage
- Linux privilege escalation
- Penetration testing workflows


