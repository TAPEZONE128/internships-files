# Module 2: Pentest Lab Setup and OS DOS Command

## Topics Covered

### **Fundamentals of VMware and VirtualBox**
- **VMware:**  
  - VMware is a leading virtualization platform that allows you to run multiple independent operating systems (virtual machines, or VMs) on a single physical computer. VMware's technology is widely used in enterprise environments for server consolidation, testing, and training purposes.
    - *Why use VMware?* VMware provides robust features like snapshot management, advanced networking, and high performance, making it ideal for pentesting labs where you frequently need to revert to clean states or simulate complex networks.
    - *Example Scenario:* You want to safely test malware or exploits: you create a Windows 10 VM in VMware, take a snapshot, perform your tests, then revert to the clean snapshot to reset the environment.

- **VirtualBox:**  
  - VirtualBox is a free and open-source virtualization tool developed by Oracle. It supports a wide range of guest OSes and is popular among students and hobbyists.
    - *Why use VirtualBox?* VirtualBox is cross-platform, cost-free, easy to use, and supports features like shared folders and seamless mode. It is ideal for individual learners or smaller labs.
    - *Example Scenario:* You set up a Kali Linux VM on your MacBook using VirtualBox to practice penetration testing tools and techniques.

- **Comparison:**  
  - Both VMware and VirtualBox allow you to isolate environments, test attacks, and manage multiple OSes without affecting your main system. VMware is often preferred in corporate/professional settings for its advanced features, while VirtualBox is favored for its accessibility and cost.

### **VM Network Setting (NAT/Bridge/Host-only)**
- **NAT (Network Address Translation):**  
 - NAT allows your VM to access external networks (e.g., the internet) using the host’s IP address, but isolates it from the local network.
    - *Why use NAT?* NAT is safer for internet access—your VM is hidden from other devices on your LAN, reducing attack surface during experiments.
    - *Example Scenario:* You want your Kali VM to download tools from the internet but don't want other devices on your home network to “see” it.

- **Bridged:**  
  - In bridged mode, your VM appears as a separate device on your physical network and gets its own IP address.
    - *Why use Bridged?* Bridged mode is necessary when you want your VM to interact with other real devices on your network (e.g., for network pentesting).
    - *Example Scenario:* You want to test ARP spoofing or Man-in-the-Middle attacks between your VM and another laptop on your LAN.

- **Host-only:**  
  - Host-only mode creates a virtual network isolated from the outside world; only the host and VMs on the same host-only network can communicate.
    - *Why use Host-only?* This is ideal for simulating private, isolated environments (e.g., red team/blue team scenarios) where no external communication is needed.
    - *Example Scenario:* You create a mini lab with two VMs (Kali Linux and vulnerable Windows) that only talk to each other and your host, for safe exploit testing.

### **Virtualization of Windows and Linux**
- **Windows Virtualization:**  
  - Creating a Windows VM involves installing Windows from an ISO file. This is useful for pentesters who want to test attacks/exploits or analyze malware in a controlled Windows environment.
    - *Insight:* Many corporate environments use Windows, so being able to simulate and attack Windows systems is essential for real-world pentesting.
    - *Example Scenario:* You create a Windows Server 2019 VM to practice privilege escalation techniques.

- **Linux Virtualization:**  
  - Installing a Linux distribution (like Ubuntu, CentOS, or Kali Linux) as a VM is common for both servers and pentesting tools.
    - *Insight:* Linux’s open-source nature and flexibility make it the backbone of many tools and exploits in cybersecurity. Linux is often used as the attacker's platform (e.g., Kali Linux) and is also a common target in infrastructure.
    - *Example Scenario:* You set up an Ubuntu Server VM and a Kali Linux VM to practice web application attacks and server hardening.

### **Installation of Kali Linux**
- **Kali Linux:**  
  - Kali Linux is a Debian-based distribution developed by Offensive Security specifically for penetration testing and security auditing. It comes pre-loaded with hundreds of hacking and forensic tools.
    - *Why was it named Linux?*  
      The name “Linux” comes from its kernel, created by Linus Torvalds in 1991. “Kali” refers to the Hindu goddess associated with empowerment—signifying the system’s power for security work.
    - *Where was Linux created?*  
      Linux was created by Linus Torvalds, a Finnish computer science student, at the University of Helsinki, Finland.
    - *What programming language?*  
      The Linux kernel is primarily written in **C** for portability and efficiency, with some critical parts in **assembly language** for direct hardware access or performance optimization.
    - *Why is it related to assembly?*  
      Operating systems, including Linux, require low-level control over hardware and memory. Assembly language enables this by allowing direct communication with CPU instructions—used for boot loaders, context switching, and performance-critical kernel code.
    - *Example Scenario:* You download the Kali Linux ISO, create a new VM in VirtualBox, and install Kali for use as your main pentesting environment.

#### Step-by-Step Installation of Kali Linux in a Virtual Machine
1. **Download the Kali Linux ISO**
   - Go to the official [Kali Linux download page](https://www.kali.org/get-kali/).
   - Choose the appropriate ISO (Installer or Live, 64-bit is most common).
   - Verify the checksum to ensure file integrity.

2. **Create a New Virtual Machine in VMware or VirtualBox**
   - Open your virtualization software.
   - Click "New" or "Create New VM".
   - Set OS type to "Linux" and version to "Debian (64-bit)" or "Other Linux (64-bit)".

3. **Configure VM Hardware**
   - Allocate at least 2 GB RAM (4 GB recommended).
   - Assign at least 20 GB of hard disk space (use dynamically allocated for flexibility).
   - Add at least 2 virtual CPUs if possible.
   - Attach the downloaded Kali ISO as the VM's optical drive.

4. **Start the Virtual Machine**
   - Boot the VM; it will detect the attached ISO and begin the Kali installer.

5. **Run the Kali Linux Installer**
   - Select "Graphical install" for an easy-to-use interface.
   - Choose your preferred language, location, and keyboard layout.

6. **Configure the Network**
   - Set a hostname (e.g., kali).
   - You may also set a domain name (optional).

7. **Set Up User Account**
   - Create a strong password for the root or standard user account.
   - Remember your credentials for later use.

8. **Partition Disks**
   - Choose "Guided - use entire disk" for simplicity (recommended for beginners).
   - Allow it to create partitions automatically (unless you want to customize).

9. **Install the System**
   - The installer will now copy files and install Kali Linux. This may take several minutes.

10. **Configure Package Manager**
    - If prompted, choose to use a network mirror for updates (recommended).

11. **Install GRUB Boot Loader**
    - Install the GRUB boot loader to the primary hard drive so your VM will boot into Kali.

12. **Complete Installation and Reboot**
    - Once installation is complete, reboot the VM.
    - Remove the ISO from the virtual drive if prompted.

13. **First Boot**
    - Log in with the username and password you created.
    - (Optional but recommended) Open a terminal and update Kali:  
      `sudo apt update && sudo apt upgrade -y`

14. **Install Virtual Machine Tools (Optional but recommended)**
    - For better performance and usability (shared clipboard, drag-and-drop), install VMware Tools or VirtualBox Guest Additions from the VM’s menu or package manager.

15. **Take a Snapshot**
    - Once your installation is complete and updated, take a VM snapshot. This allows you to restore to a clean state before/after tests.

> Tip: Take screenshots of each step and save them for your portfolio or documentation.

### **Command Kung-fu for Windows and Linux**
- **Windows CMD/PowerShell:**  
  - The command prompt (CMD) and PowerShell are powerful interfaces for controlling and automating Windows systems. PowerShell, in particular, is a scripting environment used for administration and pentesting.
    - *Insight:* Many attacks (e.g., privilege escalation, persistence) rely on command-line tools and scripting to evade detection.
    - *Example Scenario:* You use `netstat` to list network connections, or PowerShell scripts to automate privilege escalation checks.

- **Linux Terminal:**  
  - The shell (bash, zsh, etc.) is the heart of Linux system administration, automation, and hacking. Most pentesting tools are CLI-based, so mastering the terminal is essential.
    - *Insight:* Many exploits and enumeration techniques require advanced command-line usage, combining multiple tools with pipes and redirection.
    - *Example Scenario:* You use `grep` and `awk` to parse log files and identify suspicious authentication events.

## Hands-on Activities
1. **Set up a virtual lab with at least one Windows and one Kali Linux VM**
   - Download ISO images for each OS.
   - Create and configure VMs in VMware or VirtualBox (allocate RAM, CPUs, disk).
   - Install the operating systems, take snapshots at clean states.
   - *Why?* This allows you to safely test attacks and exploits without impacting your real environment.

2. **Configure network settings for different lab scenarios (NAT, Bridged, Host-only)**
   - Experiment with each mode:
     - NAT: Confirm internet access but isolation from LAN.
     - Bridged: Confirm VMs get LAN IPs and can communicate with other LAN devices.
     - Host-only: Confirm VMs only see the host and each other.
   - *Why?* Understanding these modes is crucial for simulating real-world attack scenarios and isolating dangerous activities.

3. **Install and update Kali Linux; take a screenshot of your first boot**
   - Document installation steps and updates (`sudo apt update && sudo apt upgrade`).
   - *Why?* Kali’s tools are frequently updated—updating ensures you have the latest exploits and defenses.

4. **Practice 10 essential Windows CMD commands**
   - `ipconfig` – View network settings.
   - `netstat` – List network connections.
   - `tasklist` – Display running processes.
   - `ping` – Test connectivity.
   - `tracert` – Trace route to a remote host.
   - `dir` – List directory contents.
   - `cd` – Change directory.
   - `copy` – Copy files.
   - `del` – Delete files.
   - `systeminfo` – View detailed system information.
   - *Scenario Example:* Use `ipconfig` to find your Windows VM’s IP, then `ping` the Kali VM IP to confirm connectivity.

5. **Practice 10 essential Linux terminal commands**
   - `ifconfig`/`ip a` – Display network interfaces.
   - `netstat`/`ss` – Show network connections.
   - `ps aux` – List all running processes.
   - `grep` – Search text patterns.
   - `tail` – Show end of files (logs).
   - `cd` – Change directory.
   - `ls` – List files and directories.
   - `cp` – Copy files.
   - `rm` – Remove files.
   - `cat` – Display file contents.
   - *Scenario Example:* Use `ifconfig` on Kali to check your IP address, then `ping` the Windows VM to confirm connectivity.

> Insight: A strong pentesting lab not only provides a safe playground for learning and experimentation, but also mirrors the real-world environments you will encounter as a cybersecurity professional. Mastering virtualization, networking, and the command line will make you a versatile and effective ethical hacker.

