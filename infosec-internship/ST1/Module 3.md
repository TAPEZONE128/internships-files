# Module 3: Basic Networking

## Topics Covered

### **Fundamental IP Address & Subnet Mask**
- **IP Address:**  
  - An IP (Internet Protocol) address is a unique identifier assigned to each device on a network, allowing communication between devices.
    - **IPv4:** 32-bit address (e.g., 192.168.1.10).
    - **IPv6:** 128-bit address (e.g., 2001:0db8:85a3::8a2e:0370:7334).
    - *Example Scenario:* Assigning a static IP to a Kali VM (e.g., 192.168.56.101) ensures it remains reachable for tests.
- **Subnet Mask:**  
  - Determines which part of the IP address is the network and which is the host.
    - E.g., 255.255.255.0 for IPv4 indicates the first three octets are the network.
    - *Example Scenario:* Using 255.255.255.0 allows up to 254 hosts in the same subnet, useful for small labs.
> Best Practice: Plan your network addressing scheme to avoid conflicts, and use private IP ranges for internal labs.

### **Network Devices**
- **Router:**  
  - Directs traffic between different networks (e.g., between your LAN and the internet).
    - *Example Scenario:* Your home router forwards packets between your devices and your ISP.
- **Switch:**  
  - Connects devices within the same network and forwards data only to the destined device.
    - *Example Scenario:* In a corporate office, all computers connect to a switch for internal communication.
- **Firewall:**  
  - Monitors and filters incoming/outgoing network traffic based on security rules.
    - *Example Scenario:* A firewall blocks unauthorized access from the internet to your DMZ server.
- **Hub:**  
  - Broadcasts all incoming network traffic to every port; not commonly used due to inefficiency/security risks.
    - *Example Scenario:* In a legacy lab, using a hub allows all traffic to be captured for learning purposes.
- **Access Point:**  
  - Extends wired network to wireless devices.
    - *Example Scenario:* Connecting your laptop to Wi-Fi via an access point in a coffee shop.
> Best Practice: Use switches over hubs, segment networks with routers and firewalls, and secure access points with strong encryption.

### **OSI Model vs. TCP/IP Model**
- Understanding these models is essential for troubleshooting, designing, and attacking networks. They describe how data moves from an application on one device to an application on another.

#### **OSI Model (Open Systems Interconnection Model – 7 Layers)**
1. **Physical Layer**  
   - Deals with the physical transmission of data (electrical signals, cables, connectors, radio frequency).  
     - *Example:* Ethernet cables, Wi-Fi radio waves.

2. **Data Link Layer**  
   - Provides node-to-node data transfer and handles error correction from the physical layer. Responsible for MAC addressing and switching.  
     - *Example:* Ethernet (MAC addresses), switches.

3. **Network Layer**  
   - Determines how data is sent to the receiving device across multiple networks (routing, logical addressing).  
     - *Example:* IP addresses, routers.

4. **Transport Layer**  
   - Ensures reliable data transfer between end systems, flow and error control, segmentation.  
     - *Example:* TCP (reliable), UDP (unreliable).

5. **Session Layer**  
   - Manages sessions (connections) between applications, including setup, management, and teardown.  
     - *Example:* Establishing a remote desktop session.

6. **Presentation Layer**  
   - Translates, encrypts, or compresses data for the application layer.  
     - *Example:* SSL/TLS encryption, JPEG image compression.

7. **Application Layer**  
   - Closest to the user; provides network services to end-user applications.  
     - *Example:* HTTP (web browsing), SMTP (email), FTP (file transfer).

#### **TCP/IP Model (4 Layers)**
- The TCP/IP model is a simplified, practical model used for real-world networking and the internet.
1. **Link Layer**  
   - Covers physical and data link layers of OSI; handles the physical connection to the network.
     - *Example:* Ethernet, Wi-Fi.

2. **Internet Layer**  
   - Responsible for logical addressing and routing of packets between networks.  
     - *Example:* IP protocol, routers.

3. **Transport Layer**  
   - Same as OSI’s transport; provides end-to-end communication, reliability, and flow control.
     - *Example:* TCP, UDP.

4. **Application Layer**  
   - Encompasses session, presentation, and application layers from OSI; provides services for network applications.
     - *Example:* HTTP, FTP, DNS.

#### **Mapping Example**
When you load a website in your browser:
- **Application Layer:** Browser uses HTTP or HTTPS to request a webpage.
- **Transport Layer:** HTTP data is sent over TCP (establishes connection, ensures reliable delivery).
- **Internet Layer:** Data is encapsulated in IP packets and routed across the internet.
- **Link Layer:** IP packets are transmitted over Ethernet or Wi-Fi to the next device.

**Summary Table:**
| OSI Layer          | TCP/IP Layer | Example Protocols/Devices            |
|--------------------|--------------|--------------------------------------|
| 7. Application     | Application  | HTTP, FTP, DNS, SMTP                 |
| 6. Presentation    | Application  | SSL/TLS, JPEG, ASCII                 |
| 5. Session         | Application  | NetBIOS, RPC                         |
| 4. Transport       | Transport    | TCP, UDP                             |
| 3. Network         | Internet     | IP, ICMP, ARP                        |
| 2. Data Link       | Link         | Ethernet, Wi-Fi, Switches            |
| 1. Physical        | Link         | Cables, Hubs, Radio Waves            |

> Best Practice: Memorize the OSI layers (“Please Do Not Throw Sausage Pizza Away”) and understand how protocols and devices fit into each layer. This helps in effective troubleshooting, attack simulation, and defense planning. Understand which protocols operate at which layers for effective troubleshooting and targeted attacks.

### **ARP, ICMP, TCP, UDP Protocols**
- **ARP (Address Resolution Protocol):**  
  - Resolves IP addresses to MAC addresses within a local network.
    - *Example Scenario:* Kali VM uses ARP to find the MAC address of the Windows VM for direct communication.
    - *Attack Example:* ARP spoofing to redirect traffic (Man-in-the-Middle).
- **ICMP (Internet Control Message Protocol):**  
  - Used for diagnostics and error messages (e.g., ping).
    - *Example Scenario:* Using `ping` to check if a server is reachable.
    - *Attack Example:* ICMP flood to cause DoS.
- **TCP (Transmission Control Protocol):**  
  - Connection-oriented, reliable protocol (e.g., web, email).
    - *Example Scenario:* Your browser uses TCP to load a secure webpage.
- **UDP (User Datagram Protocol):**  
  - Connectionless, faster but unreliable (e.g., video streaming, DNS).
    - *Example Scenario:* Streaming a live event over UDP.
  
> Best Practice: Use TCP for critical data, monitor ARP/ICMP for suspicious activity, and restrict unnecessary UDP services.

### **TCP Flags**
- **SYN:** Initiates a connection.
- **ACK:** Acknowledges receipt of a packet.
- **FIN:** Requests to finish/close a connection.
- **RST:** Resets a connection due to errors.
- **PSH:** Pushes data to the receiving application immediately.
- **URG:** Marks data as urgent.
- *Scenario Example:* In a SYN flood attack, an attacker sends many SYN packets and never completes the handshake, overwhelming the server.

> Best Practice: Monitor for abnormal flag combinations and rates (e.g., many SYNs without ACKs) to detect attacks.

### **TCP 3-Way Handshake**
- **Process:**
  1. SYN: Client sends SYN to server.
  2. SYN-ACK: Server replies with SYN-ACK.
  3. ACK: Client sends ACK; connection established.
- *Example Scenario:* Your web browser completes this handshake to start loading a website.
- *Attack Example:* SYN flood disrupts this process, causing a denial of service.
- **Best Practice:**  
  Use firewalls and rate-limiting to mitigate handshake abuse.

### **Well-known Services Port**
- **Ports:**  
  - Numeric identifiers for specific services.  
    - 80 (HTTP), 443 (HTTPS), 21 (FTP), 22 (SSH), 53 (DNS), 25 (SMTP), 3389 (RDP).
- *Example Scenario:* SSH server listens on port 22—attackers scan for open port 22 to find SSH services.

> Best Practice: Close unused ports, use non-default ports for sensitive services, and monitor for port scans.

### **Red Flags: Suspicious IP Address Behavior & Signs of Malicious Activity**
- Understanding normal versus suspicious network behavior is critical in cybersecurity and penetration testing. Here are red flags and signs that may indicate a compromised IP address or a malicious payload running on your system:

#### **Red Flags for Suspicious IP Behavior**
- **Unusual Outbound Connections:**  
  - Your device connects to unfamiliar or foreign IP addresses, especially in high-risk regions or known blacklists.
    - *Example Scenario:* Your workstation establishes frequent connections to IPs in countries where you have no business ties.

- **Unexpected Inbound Connections:**  
  - Repeated unsolicited attempts to connect to your system from external sources.
    - *Example Scenario:* Multiple failed SSH login attempts from different global IPs.

- **Port Scanning Activity:**  
  - Detection of your IP actively scanning other devices or being scanned by others.
    - *Example Scenario:* Your firewall logs show your system probing random ports on remote networks.

- **High Volume or Unusual Traffic Patterns:**  
  - Significant spikes in bandwidth, especially during odd hours, or traffic on uncommon ports.
    - *Example Scenario:* A spike in outbound traffic at 3 AM, or data sent on ports commonly used by malware (e.g., 4444, 6667).

- **Connections to Known Malicious Hosts:**  
  - Your device communicates with IP addresses associated with botnets, C2 servers, or blacklisted domains.
    - *Example Scenario:* Outbound traffic detected to IPs listed on threat intelligence blocklists.

- **Frequent ARP Requests or ARP Spoofing:**  
  - Excessive ARP broadcasts or changes in ARP table entries may indicate a Man-in-the-Middle attack.
    - *Example Scenario:* Multiple devices report your IP/MAC address as the gateway.

- **Unexpected Open Ports:**  
  - Discovery of unfamiliar services running and listening on your IP (e.g., a web server on port 8080 that you did not install).
    - *Example Scenario:* Nmap scan reveals new open ports after installing third-party software.

#### **Signs There’s a Malicious Payload on Your IP**
- **Unusual or Unauthorized Processes Running:**  
  - New, suspicious, or resource-intensive processes consuming CPU/RAM.
    - *Example Scenario:* A process with a random or misleading name running and connecting to the internet.

- **Reverse Shells or Remote Command Sessions:**  
  - Outbound connections to external IPs on high/random ports, especially if using bash, cmd, or powershell.
    - *Example Scenario:* Netstat shows your device has an established outbound connection on port 4444 (commonly used for reverse shells).

- **Frequent Antivirus/IDS Alerts:**  
  - Security software flags new files, registry changes, or network activity.
    - *Example Scenario:* Your endpoint protection system repeatedly blocks attempts to create scheduled tasks or modify system files.

- **Modification of Hosts or DNS Settings:**  
  - Changes to `/etc/hosts` or DNS settings redirecting traffic to malicious sites.
    - *Example Scenario:* All traffic to legitimate websites is silently redirected to phishing sites.

- **Unexplained System Slowdown or Crashes:**  
  - The system is noticeably slower or crashes unexpectedly, often due to malicious payloads running in the background.
    - *Example Scenario:* System freezes after connecting to a suspicious Wi-Fi network.

#### **Best Practices for Detection and Response**
- Regularly monitor your network traffic using tools like Wireshark, tcpdump, and netstat.
- Check running processes with Task Manager (Windows) or `ps aux` (Linux).
- Audit open ports with Nmap and review firewall logs for anomalies.
- Keep your operating system and security tools up-to-date.
- Use reputable threat intelligence feeds to identify suspicious IPs.
- If you suspect a payload or compromise, immediately isolate the affected device from the network and begin incident response protocols.

> Remember: Early identification of these red flags can prevent escalation and data breaches. As a pentester or defender, always be vigilant for abnormal behaviors in your network traffic and system processes.

## Hands-on Activities

1. **Use `ipconfig`/`ifconfig` to identify and configure IP addresses on your VMs.**
   - Open terminal (Linux) or CMD (Windows).
   - Run `ipconfig` (Windows) or `ifconfig`/`ip a` (Linux) to view IP info.
   - Assign static IPs for controlled network experiments.
   - *Best Practice:* Document assigned IPs to avoid conflicts.

2. **Draw and label the OSI and TCP/IP models; map protocols and devices to each layer.**
   - Use diagrams to visualize layer functions.
   - Map protocols: e.g., HTTP (Application), TCP (Transport), IP (Network).
   - *Best Practice:* Keep reference diagrams handy for troubleshooting and planning attacks.

3. **Use Wireshark or tcpdump to capture and analyze TCP handshakes and protocol traffic.**
   - Start a capture, initiate a web connection, and observe the SYN, SYN-ACK, ACK sequence.
   - Identify ARP, ICMP, TCP, and UDP packets in traffic.
   - *Best Practice:* Filter captures to focus on relevant protocols and avoid information overload.

4. **Identify open ports on your VMs using Nmap.**
   - Run `nmap <target IP>` to scan for open services.
   - Interpret results to find potentially vulnerable services.
   - *Best Practice:* Scan your own lab only—never scan unauthorized networks!

5. **Perform a basic ARP spoofing lab in your virtual environment.**
   - Use tools like `arpspoof` or `ettercap` to poison ARP cache between two VMs.
   - Observe the impact with Wireshark.
   - *Best Practice:* Only perform ARP spoofing in isolated labs, as it disrupts network traffic.

## Best Practices Recap
- Always use private IP ranges and secure network segments.
- Restrict unnecessary services and open ports.
- Monitor network traffic for unusual patterns.
- Document all changes and configurations.
- Never perform attacks or scans on networks you do not own or have explicit permission to test.

---
