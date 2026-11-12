# Cloud Security Roadmap: From Zero to Cloud Security Engineer

> **Structure:** Domain > Module > Lesson > Topics / Hands-on.
> **Numbering:** `domain.module.lesson.topic`, where `T` = hands-on exercise, `C` = module challenge, `Z` = certifications, and `P` = projects.

---

## Table of Contents

- [0. Ground Rules](#0-ground-rules)
- [Domain 1: Networking](#domain-1-networking-90-hours)
- [Domain 2: Linux](#domain-2-linux-70-hours)
- [Domain 3: Python, Bash, and Git](#domain-3-python-bash-and-git-80-hours)
- [Domain 4: AWS Core](#domain-4-aws-core-170-hours)
- [Domain 5: DevOps (Terraform, Docker, CI/CD, Kubernetes)](#domain-5-devops-terraform-docker-cicd-and-kubernetes-180-hours)
- [Domain 6: Security Fundamentals](#domain-6-security-fundamentals-150-hours)
- [Domain 7: AWS Cloud Security](#domain-7-aws-cloud-security-190-hours)
- [Domain 8: Advanced Specialization and Employment](#domain-8-advanced-specialization-and-employment-120-hours)
- [Free Certifications and Badges](#free-certifications-and-badges)
- [Highest-ROI Paid Certifications](#highest-roi-paid-certifications-in-order)
- [Suggested Weekly Routine](#suggested-weekly-routine-2-hours-per-day)
- [Domain Readiness Criteria](#domain-readiness-criteria)

---

## 0. Ground Rules

### 0.1 Realistic Time Estimates

| Domain | Hours |
|---|---|
| 1. Networking | 90 |
| 2. Linux | 70 |
| 3. Python, Bash, and Git | 80 |
| 4. AWS Core | 170 |
| 5. DevOps | 180 |
| 6. Security Fundamentals | 150 |
| 7. AWS Cloud Security | 190 |
| 8. Advanced Specialization and Employment | 120 |
| **Total** | **1,050** |

- 0.1.1 At 1 hour per day: approximately 3 years
- 0.1.2 At 2 hours per day: approximately 17 months
- 0.1.3 At 3 hours per day: approximately 12 months
- 0.1.4 Domains 1 to 5 produce a job-ready Cloud Engineer. Do not wait until Domain 8 to start applying.
- 0.1.5 The time listed for each lesson includes both study and hands-on practice.

### 0.2 Working Principles

- 0.2.1 Spend 30% of your time watching and reading, and 70% hands-on.
- 0.2.2 A lesson without hands-on practice is not considered complete.
- 0.2.3 Publish a short write-up on GitHub for every lab and CTF (steps taken, mistakes made, lessons learned). These write-ups form your portfolio.
- 0.2.4 Keep a single notebook (Obsidian or Notion) for every command, every error, and its resolution.
- 0.2.5 If you are stuck for more than 45 minutes: search for a solution, then ask in the platform's Discord community, then move on and return later.
- 0.2.6 Use spaced repetition (Anki) for Linux commands, network ports, and AWS services.

### 0.3 AWS Safety Rules (Mandatory Before the First Lab)

- 0.3.1 Enable MFA on the root account and do not use it after initial setup.
- 0.3.2 Create an AWS Budget with a $1 threshold and email alerts.
- 0.3.3 Delete all resources after every lab. The most common sources of unexpected charges are NAT Gateways, forgotten EC2 instances, RDS databases, unattached Elastic IPs, and Load Balancers.
- 0.3.4 Never commit access keys to GitHub. Enable git-secrets or gitleaks.

### 0.4 Lab Environment (Setup Week, 6 hours)

- 0.4.1 VirtualBox or VMware with Ubuntu Server and Kali Linux on an isolated Host-Only network
- 0.4.2 Accounts and tools: AWS Free Tier, GitHub, Docker Desktop, and VS Code
- 0.4.3 Platform accounts: TryHackMe, Hack The Box (Academy), picoCTF, PortSwigger Academy, OverTheWire, and CTFtime

---

# Domain 1: Networking [90 hours]

## 1.1 Module: Models, Addressing, and Routing [30 hours]

### 1.1.1 Lesson: OSI and TCP/IP [4 hours]
- **Topics**
  - 1.1.1.1 Layers and encapsulation
  - 1.1.1.2 PDU at each layer
  - 1.1.1.3 TCP vs. UDP: three-way handshake, flags, window size
  - 1.1.1.4 Ports
  - 1.1.1.5 ICMP, ping, and traceroute
- **Hands-on**
  - 1.1.1.T1 TryHackMe Pre-Security rooms: OSI Model, Packets & Frames, Extending Your Network
  - 1.1.1.T2 Capture a real TCP handshake in Wireshark and label every flag

### 1.1.2 Lesson: IP Addressing and Subnetting [8 hours]
- **Topics**
  - 1.1.2.1 IPv4 and binary conversion
  - 1.1.2.2 Private address ranges (RFC 1918)
  - 1.1.2.3 CIDR
  - 1.1.2.4 VLSM
  - 1.1.2.5 Manual subnet calculation
  - 1.1.2.6 IPv6 fundamentals
- **Hands-on**
  - 1.1.2.T1 Solve 50 problems on subnettingpractice.com without a calculator, at under 30 seconds per problem

### 1.1.3 Lesson: Ethernet, Switching, ARP, and VLANs [6 hours]
- **Topics**
  - 1.1.3.1 MAC addresses and the CAM table
  - 1.1.3.2 ARP
  - 1.1.3.3 VLANs and trunking (802.1Q)
  - 1.1.3.4 STP concepts
- **Hands-on**
  - 1.1.3.T1 Cisco Packet Tracer: build 3 VLANs with a trunk
  - 1.1.3.T2 Observe ARP traffic in Wireshark

### 1.1.4 Lesson: Routing, NAT, and DHCP [6 hours]
- **Topics**
  - 1.1.4.1 Static and default routes
  - 1.1.4.2 OSPF and BGP concepts
  - 1.1.4.3 NAT and PAT
  - 1.1.4.4 DHCP and DORA
- **Hands-on**
  - 1.1.4.T1 Packet Tracer: router-on-a-stick with DHCP and NAT

### Challenge 1.1.C [6 hours]
1. 1.1.C.1 Build a complete corporate network in Packet Tracer with 3 VLANs
2. 1.1.C.2 Configure inter-VLAN routing
3. 1.1.C.3 Configure DHCP
4. 1.1.C.4 Configure NAT
5. 1.1.C.5 Implement an ACL that blocks the Sales department from accessing IT
6. 1.1.C.6 Document the build with a network diagram and a write-up
7. 1.1.C.7 Complete the Cisco Networking Academy "Networking Basics" course (free, with completion certificate)

## 1.2 Module: Application Protocols and Packet Analysis [30 hours]

### 1.2.1 Lesson: DNS [5 hours]
- **Topics**
  - 1.2.1.1 Resolution process
  - 1.2.1.2 Record types: A, AAAA, CNAME, MX, TXT, NS, PTR
  - 1.2.1.3 TTL and zones
  - 1.2.1.4 DNSSEC
  - 1.2.1.5 DNS tunneling and cache poisoning
- **Hands-on**
  - 1.2.1.T1 Use dig and nslookup against real domains
  - 1.2.1.T2 Run dnsmasq or BIND in a VM
  - 1.2.1.T3 TryHackMe "DNS in Detail" room

### 1.2.2 Lesson: HTTP, HTTPS, and TLS [7 hours]
- **Topics**
  - 1.2.2.1 Methods and status codes
  - 1.2.2.2 Headers, cookies, and sessions
  - 1.2.2.3 CORS
  - 1.2.2.4 TLS handshake and certificate chains
  - 1.2.2.5 SNI
  - 1.2.2.6 HTTP/2
- **Hands-on**
  - 1.2.2.T1 Run `curl -v` against a variety of sites
  - 1.2.2.T2 Install Nginx with a Let's Encrypt certificate (or a self-signed certificate in the lab)
  - 1.2.2.T3 Scan the site with SSL Labs
  - 1.2.2.T4 Burp Suite Community: intercept and modify a request

### 1.2.3 Lesson: SSH, Email, and SMB [4 hours]
- **Topics**
  - 1.2.3.1 SSH keys, port forwarding, and tunnels
  - 1.2.3.2 SMTP and IMAP
  - 1.2.3.3 SPF, DKIM, and DMARC
  - 1.2.3.4 SMB and FTP
- **Hands-on**
  - 1.2.3.T1 OverTheWire Bandit, levels 0 to 15
  - 1.2.3.T2 Inspect a domain's SPF/DKIM/DMARC records with MXToolbox

### 1.2.4 Lesson: Wireshark and Packet Analysis [8 hours]
- **Topics**
  - 1.2.4.1 Capture and display filters
  - 1.2.4.2 Follow Stream
  - 1.2.4.3 File extraction
  - 1.2.4.4 Reading statistics
  - 1.2.4.5 Anomaly detection
- **Hands-on**
  - 1.2.4.T1 TryHackMe: Wireshark Basics and Packet Operations
  - 1.2.4.T2 Three exercises from Malware-Traffic-Analysis.net
  - 1.2.4.T3 picoCTF pcap challenges (Forensics)

### 1.2.5 Lesson: Nmap and Network Scanning [6 hours]
- **Topics**
  - 1.2.5.1 Scan types: SYN, TCP connect, UDP
  - 1.2.5.2 Service and version detection
  - 1.2.5.3 NSE scripts
  - 1.2.5.4 Interpreting results
  - 1.2.5.5 Basic evasion techniques
- **Hands-on**
  - 1.2.5.T1 TryHackMe Nmap rooms
  - 1.2.5.T2 Scan only devices you own
  - 1.2.5.T3 Try several scan modes and compare their noise in Wireshark

### Challenge 1.2.C [6 hours, CTF]
1. 1.2.C.1 Complete the TryHackMe Network Fundamentals path
2. 1.2.C.2 Complete Nmap Live Host Discovery
3. 1.2.C.3 Solve 5 pcap challenges from picoCTF or CyberDefenders (easy Network Forensics)
4. 1.2.C.4 Write a write-up for each

## 1.3 Module: Network Security [30 hours]

### 1.3.1 Lesson: Firewalls, ACLs, and IDS/IPS [6 hours]
- **Topics**
  - 1.3.1.1 Stateful vs. stateless inspection
  - 1.3.1.2 iptables, nftables, and ufw
  - 1.3.1.3 IDS/IPS concepts
  - 1.3.1.4 Snort and Suricata (introduction)
- **Hands-on**
  - 1.3.1.T1 Configure ufw, then iptables, on Ubuntu
  - 1.3.1.T2 Test the rules with Nmap from Kali
  - 1.3.1.T3 Install Suricata and run a rule that detects an Nmap scan

### 1.3.2 Lesson: VPN, IPsec, and WireGuard [6 hours]
- **Topics**
  - 1.3.2.1 Site-to-site vs. remote access
  - 1.3.2.2 IPsec (IKE phases)
  - 1.3.2.3 WireGuard
  - 1.3.2.4 Split tunneling
- **Hands-on**
  - 1.3.2.T1 Set up WireGuard between two VMs (this lab is repeated later on EC2)

### 1.3.3 Lesson: Common Network Attacks [6 hours]
- **Topics**
  - 1.3.3.1 ARP spoofing and MITM
  - 1.3.3.2 DNS poisoning
  - 1.3.3.3 DoS and DDoS
  - 1.3.3.4 Sniffing
  - 1.3.3.5 Rogue DHCP
- **Hands-on**
  - 1.3.3.T1 In an isolated VM network only: run an ARP spoofing attack with Bettercap and observe it in Wireshark
  - 1.3.3.T2 Defend against the attack using Dynamic ARP Inspection or static ARP entries

### 1.3.4 Lesson: Reverse Proxy, Load Balancing, and CDN [6 hours]
- **Topics**
  - 1.3.4.1 Nginx as a reverse proxy
  - 1.3.4.2 Load-balancing algorithms
  - 1.3.4.3 Health checks
  - 1.3.4.4 CDN and WAF concepts
- **Hands-on**
  - 1.3.4.T1 Nginx in front of two backend servers with TLS
  - 1.3.4.T2 Stop one backend server and observe the failover

### Challenge 1.3.C [6 hours]
1. 1.3.C.1 Build a 3-VM lab: web server, firewall, and attacker
2. 1.3.C.2 Run a scan and an ARP attack
3. 1.3.C.3 Configure defenses: firewall, Suricata, and Nginx with TLS
4. 1.3.C.4 Repeat the attack and compare the results
5. 1.3.C.5 Write up the before-and-after results

## 1.Z Domain 1 Certifications and Deliverables

1. 1.Z.1 Free: Networking Basics, Network Devices, and Introduction to Cybersecurity from Cisco Networking Academy
2. 1.Z.2 Review the CompTIA Network+ N10-009 syllabus with Professor Messer (the exam is optional)
3. 1.P.1 Domain project: a GitHub repository containing the network diagram, configuration files, and the three write-ups

---

# Domain 2: Linux [70 hours]

## 2.1 Module: Fundamentals [25 hours]

### 2.1.1 Lesson: File System and Navigation [4 hours]
- **Topics**
  - 2.1.1.1 FHS layout: /etc, /var, /usr, /home
  - 2.1.1.2 ls, cd, find, locate, which
  - 2.1.1.3 Hard and symbolic links
  - 2.1.1.4 man and --help
- **Hands-on**
  - 2.1.1.T1 Linux Journey (free)
  - 2.1.1.T2 OverTheWire Bandit, levels 0 to 10

### 2.1.2 Lesson: Users and Permissions [6 hours]
- **Topics**
  - 2.1.2.1 Users and groups
  - 2.1.2.2 chmod, chown, umask
  - 2.1.2.3 SUID, SGID, and the sticky bit
  - 2.1.2.4 sudo and sudoers
  - 2.1.2.5 ACLs
- **Hands-on**
  - 2.1.2.T1 TryHackMe Linux Fundamentals, Part 2
  - 2.1.2.T2 Create users and a misconfigured-permissions scenario, then fix it

### 2.1.3 Lesson: Text Processing and Pipes [7 hours]
- **Topics**
  - 2.1.3.1 grep, sed, awk, cut, sort, uniq
  - 2.1.3.2 Redirects and pipes
  - 2.1.3.3 Regular expressions
- **Hands-on**
  - 2.1.3.T1 Analyze /var/log/auth.log and extract the top 10 IP addresses with failed logins using a single pipeline
  - 2.1.3.T2 Bandit, levels 10 to 20

### 2.1.4 Lesson: Processes and Services [5 hours]
- **Topics**
  - 2.1.4.1 ps, top, kill, and signals
  - 2.1.4.2 systemd and systemctl
  - 2.1.4.3 journalctl
  - 2.1.4.4 cron
- **Hands-on**
  - 2.1.4.T1 Write a systemd service that runs a script at boot
  - 2.1.4.T2 Schedule a cron job
  - 2.1.4.T3 TryHackMe Linux Fundamentals, Part 3

### 2.1.5 Lesson: Packages and Storage [3 hours]
- **Topics**
  - 2.1.5.1 apt and dnf
  - 2.1.5.2 mount and fstab
  - 2.1.5.3 LVM
  - 2.1.5.4 Disks and partitions
- **Hands-on**
  - 2.1.5.T1 Add a virtual disk to a VM, partition it, and mount it persistently

### Challenge 2.1.C (CTF)
1. 2.1.C.1 Complete OverTheWire Bandit (levels 0 to 33)
2. 2.1.C.2 Write up the 5 hardest levels
3. 2.1.C.3 Solve at least 10 picoCTF challenges in the General Skills category

## 2.2 Module: Administration and Hardening [25 hours]

### 2.2.1 Lesson: Linux Networking [5 hours]
- **Topics**
  - 2.2.1.1 ip, ss, and netplan
  - 2.2.1.2 Routing table
  - 2.2.1.3 resolv.conf
  - 2.2.1.4 nftables
- **Hands-on**
  - 2.2.1.T1 Configure two VMs with static IPs and routing between them, with one acting as a router

### 2.2.2 Lesson: SSH Hardening [4 hours]
- **Topics**
  - 2.2.2.1 Key-based authentication instead of passwords
  - 2.2.2.2 sshd_config: PermitRootLogin and AllowUsers
  - 2.2.2.3 fail2ban
  - 2.2.2.4 Jump hosts
- **Hands-on**
  - 2.2.2.T1 Configure a key-only server
  - 2.2.2.T2 Attack your own server with Hydra and observe fail2ban banning your IP

### 2.2.3 Lesson: Logging and Auditing [5 hours]
- **Topics**
  - 2.2.3.1 rsyslog and journald
  - 2.2.3.2 /var/log
  - 2.2.3.3 auditd and writing rules
  - 2.2.3.4 logrotate
- **Hands-on**
  - 2.2.3.T1 Write and test an auditd rule that monitors modifications to /etc/passwd

### 2.2.4 Lesson: CIS-Based Hardening [6 hours]
- **Topics**
  - 2.2.4.1 CIS Benchmarks
  - 2.2.4.2 Lynis
  - 2.2.4.3 SELinux and AppArmor
  - 2.2.4.4 sysctl
  - 2.2.4.5 Automatic updates
- **Hands-on**
  - 2.2.4.T1 Run Lynis before and after hardening. Target: a score above 80

### 2.2.5 Lesson: Bash Fundamentals [5 hours]
- **Topics**
  - 2.2.5.1 Variables, conditionals, and loops
  - 2.2.5.2 Functions
  - 2.2.5.3 Error handling: `set -euo pipefail`
  - 2.2.5.4 ShellCheck
- **Hands-on**
  - 2.2.5.T1 Write a script that automatically hardens a server
  - 2.2.5.T2 Exercism Bash track exercises

### Challenge 2.2.C [6 hours]
1. 2.2.C.1 Build a hardened Ubuntu server with key-based SSH
2. 2.2.C.2 Configure ufw
3. 2.2.C.3 Configure fail2ban
4. 2.2.C.4 Configure auditd
5. 2.2.C.5 Configure unattended-upgrades
6. 2.2.C.6 Achieve a Lynis score above 80
7. 2.2.C.7 Produce a before-and-after report and automate everything in a single Bash script

## 2.3 Module: Linux Security and Privilege Escalation [20 hours]

### 2.3.1 Lesson: Privilege Escalation [8 hours]
- **Topics**
  - 2.3.1.1 Misconfigured SUID binaries
  - 2.3.1.2 `sudo -l`
  - 2.3.1.3 Cron and PATH hijacking
  - 2.3.1.4 Capabilities
  - 2.3.1.5 Kernel exploits (concepts)
- **Hands-on**
  - 2.3.1.T1 TryHackMe Linux PrivEsc room
  - 2.3.1.T2 Use GTFOBins as a reference
  - 2.3.1.T3 HTB Academy Linux Privilege Escalation module

### 2.3.2 Lesson: Beginner CTF Machines [12 hours]
- **Topics**
  - 2.3.2.1 Enumeration
  - 2.3.2.2 Initial access
  - 2.3.2.3 Escalation
  - 2.3.2.4 Write-ups
- **Hands-on**
  - 2.3.2.T1 Complete 5 easy machines on TryHackMe (Blue, Ice, Pickle Rick, Bounty Hacker, and others from the Jr Penetration Tester path) or HTB Starting Point

### Challenge 2.3.C
1. 2.3.C.1 Complete 5 machines with a write-up for each
2. 2.3.C.2 Publish them on GitHub

## 2.Z Domain 2 Certifications and Deliverables

1. 2.Z.1 Free: Linux Essentials and Linux Unhatched from Cisco NetAcad (in partnership with NDG)
2. 2.Z.2 HTB Academy Linux Fundamentals path
3. 2.Z.3 Review the LFCS syllabus (the exam is optional)
4. 2.P.1 Domain project: a published hardening script with a before-and-after Lynis report

---

# Domain 3: Python, Bash, and Git [80 hours]

## 3.1 Module: Git and GitHub [15 hours]

### 3.1.1 Lesson: Git Internals [7 hours]
- **Topics**
  - 3.1.1.1 init, add, commit, log
  - 3.1.1.2 Branches, merge, and rebase
  - 3.1.1.3 Resolving conflicts
  - 3.1.1.4 .gitignore
  - 3.1.1.5 Tags
  - 3.1.1.6 reset, revert, and reflog
- **Hands-on**
  - 3.1.1.T1 Learn Git Branching: complete all levels
  - 3.1.1.T2 Oh My Git! (game)

### 3.1.2 Lesson: GitHub and Collaboration [8 hours]
- **Topics**
  - 3.1.2.1 Fork, pull request, and code review
  - 3.1.2.2 Issues and Projects
  - 3.1.2.3 Branch protection
  - 3.1.2.4 GitHub Actions (introduction)
  - 3.1.2.5 Secret scanning and Dependabot
- **Hands-on**
  - 3.1.2.T1 GitHub Skills (free interactive courses)
  - 3.1.2.T2 Contribute a real pull request to an open-source project (even a documentation fix)

### Challenge 3.1.C
1. 3.1.C.1 Scan your repository with gitleaks
2. 3.1.C.2 Intentionally commit a fake AWS key in an old commit
3. 3.1.C.3 Detect it
4. 3.1.C.4 Remove it from history using git filter-repo
5. 3.1.C.5 Write up what happened

## 3.2 Module: Python for Automation and Security [50 hours]

### 3.2.1 Lesson: Language Fundamentals [15 hours]
- **Topics**
  - 3.2.1.1 Variables and types
  - 3.2.1.2 Conditionals and loops
  - 3.2.1.3 Functions
  - 3.2.1.4 Lists, dictionaries, and sets
  - 3.2.1.5 Files, JSON, and CSV
  - 3.2.1.6 Errors and try/except
  - 3.2.1.7 venv and pip
- **Hands-on**
  - 3.2.1.T1 *Automate the Boring Stuff with Python* (free online)
  - 3.2.1.T2 30 exercises on the Exercism Python track

### 3.2.2 Lesson: Intermediate Python [12 hours]
- **Topics**
  - 3.2.2.1 Classes and OOP
  - 3.2.2.2 Modules and packages
  - 3.2.2.3 Regular expressions
  - 3.2.2.4 Decorators and generators
  - 3.2.2.5 Testing with pytest
  - 3.2.2.6 Logging
- **Hands-on**
  - 3.2.2.T1 Build an argparse-based CLI tool covered by pytest tests

### 3.2.3 Lesson: Networking and HTTP in Python [8 hours]
- **Topics**
  - 3.2.3.1 requests
  - 3.2.3.2 sockets
  - 3.2.3.3 Threading and asyncio (introduction)
  - 3.2.3.4 HTML parsing with BeautifulSoup
- **Hands-on**
  - 3.2.3.T1 Build a simple port scanner
  - 3.2.3.T2 Write a script that checks the status of 50 websites and logs the results

### 3.2.4 Lesson: Boto3 and the AWS SDK [8 hours]
> Postpone this lesson until after Lesson 4.1.1 if you have not yet worked with AWS.
- **Topics**
  - 3.2.4.1 Credentials and profiles
  - 3.2.4.2 Working with S3, EC2, and IAM
  - 3.2.4.3 Pagination
  - 3.2.4.4 Error handling
- **Hands-on**
  - 3.2.4.T1 Write a script that lists public S3 buckets and security groups open to 0.0.0.0/0 (your first real security tool)

### 3.2.5 Lesson: Python for Security [7 hours]
- **Topics**
  - 3.2.5.1 Hashing and encoding
  - 3.2.5.2 Log analysis
  - 3.2.5.3 Subprocess
  - 3.2.5.4 Writing simple exploits
- **Hands-on**
  - 3.2.5.T1 Write a script that analyzes SSH logs and detects brute-force attempts
  - 3.2.5.T2 picoCTF Cryptography category: 5 challenges
  - 3.2.5.T3 CryptoHack Introduction path

### Challenge 3.2.C [8 hours]
1. 3.2.C.1 Build an open-source Python tool, published under your name, that audits an AWS account
2. 3.2.C.2 Check for: public S3 buckets
3. 3.2.C.3 Check for: root account without MFA
4. 3.2.C.4 Check for: stale access keys
5. 3.2.C.5 Check for: open security groups
6. 3.2.C.6 Output an HTML or JSON report
7. 3.2.C.7 Include a README and tests

## 3.3 Module: Advanced Bash [15 hours]

### 3.3.1 Lesson: Production Scripts [8 hours]
- **Topics**
  - 3.3.1.1 Arguments and getopts
  - 3.3.1.2 Arrays
  - 3.3.1.3 Traps and resource cleanup
  - 3.3.1.4 Here-docs
  - 3.3.1.5 jq for JSON processing
  - 3.3.1.6 xargs and parallel
- **Hands-on**
  - 3.3.1.T1 Write a backup script with rotation and clear error messages
  - 3.3.1.T2 Re-solve Bandit levels 20 to 33 using Bash scripts

### 3.3.2 Lesson: Working with APIs from the Terminal [7 hours]
- **Topics**
  - 3.3.2.1 curl
  - 3.3.2.2 jq
  - 3.3.2.3 Webhooks
  - 3.3.2.4 Cron
- **Hands-on**
  - 3.3.2.T1 Write a script that fetches new CVEs from the NVD API and sends an alert to Telegram or Slack

## 3.Z Domain 3 Certifications and Deliverables

1. 3.Z.1 Free: Python Essentials 1 from Cisco NetAcad
2. 3.Z.2 Free: Scientific Computing with Python from freeCodeCamp
3. 3.Z.3 Google IT Automation with Python (free to audit; certificate is paid)
4. 3.P.1 Domain project: a Python AWS Auditor tool with a README, an architecture diagram, and a two-minute demo video

---

# Domain 4: AWS Core [170 hours]

> Every lab in this domain follows the safety rules in Section 0.3.

## 4.1 Module: Foundations and Identity [35 hours]

### 4.1.1 Lesson: Introduction to AWS [6 hours]
- **Topics**
  - 4.1.1.1 Regions, Availability Zones, and Edge locations
  - 4.1.1.2 Shared Responsibility Model
  - 4.1.1.3 Console, CLI v2, and SDK
  - 4.1.1.4 Free Tier and Budgets
  - 4.1.1.5 Well-Architected Framework (six pillars)
- **Hands-on**
  - 4.1.1.T1 AWS Cloud Practitioner Essentials course on AWS Skill Builder (free)
  - 4.1.1.T2 Enable Budgets, MFA, and billing alerts

### 4.1.2 Lesson: IAM in Depth [16 hours]
- **Topics**
  - 4.1.2.1 Users, groups, and roles
  - 4.1.2.2 Policies: identity-based vs. resource-based
  - 4.1.2.3 JSON structure: Effect, Action, Resource, and Condition
  - 4.1.2.4 Evaluation logic: explicit deny > allow > implicit deny
  - 4.1.2.5 AssumeRole and STS
  - 4.1.2.6 IAM Identity Center
  - 4.1.2.7 Access Analyzer
- **Hands-on**
  - 4.1.2.T1 IAM Workshop on workshops.aws
  - 4.1.2.T2 Write a policy that grants read access to a single bucket only
  - 4.1.2.T3 Write a policy restricted by IP and MFA
  - 4.1.2.T4 The Big IAM Challenge (bigiamchallenge.com) by Wiz

### 4.1.3 Lesson: CLI and Organizations [6 hours]
- **Topics**
  - 4.1.3.1 Profiles and SSO login
  - 4.1.3.2 Organizations and OUs
  - 4.1.3.3 Consolidated billing
  - 4.1.3.4 SCPs (introduction)
- **Hands-on**
  - 4.1.3.T1 Create an Organization with two accounts: Management and Sandbox
  - 4.1.3.T2 Sign in using IAM Identity Center

### 4.1.4 Lesson: CloudTrail and CloudWatch [7 hours]
- **Topics**
  - 4.1.4.1 Management and data events
  - 4.1.4.2 Trails vs. Event History
  - 4.1.4.3 CloudWatch Logs, Metrics, and Alarms
  - 4.1.4.4 EventBridge
- **Hands-on**
  - 4.1.4.T1 Create an alarm that sends an email on root account sign-in
  - 4.1.4.T2 Use Athena to search for an IAM user creation event

### Challenge 4.1.C (CTF)
1. 4.1.C.1 flaws.cloud: all six levels (free, by Scott Piper)
2. 4.1.C.2 flaws2.cloud: both the Attacker and Defender paths
3. 4.1.C.3 Write-up for each level: the original mistake and the fix

## 4.2 Module: Networking and Compute [50 hours]

### 4.2.1 Lesson: VPC [16 hours]
- **Topics**
  - 4.2.1.1 CIDR and subnets (public and private)
  - 4.2.1.2 Route tables
  - 4.2.1.3 Internet Gateway
  - 4.2.1.4 NAT Gateway
  - 4.2.1.5 Security Groups vs. NACLs
  - 4.2.1.6 VPC Endpoints: Gateway and Interface
  - 4.2.1.7 VPC Peering and Transit Gateway
  - 4.2.1.8 VPC Flow Logs
- **Hands-on**
  - 4.2.1.T1 Build a VPC from scratch without the wizard: public and private subnets across two Availability Zones, with NAT
  - 4.2.1.T2 Create Flow Logs and read an actual rejected-packet record

### 4.2.2 Lesson: EC2 [14 hours]
- **Topics**
  - 4.2.2.1 Instance types and pricing: On-Demand, Spot, and Savings Plans
  - 4.2.2.2 AMI, EBS, and snapshots
  - 4.2.2.3 User data
  - 4.2.2.4 Instance profiles
  - 4.2.2.5 Key pairs vs. Session Manager
  - 4.2.2.6 IMDSv2
- **Hands-on**
  - 4.2.2.T1 Launch an instance without SSH and connect through Session Manager only
  - 4.2.2.T2 Test IMDSv1, then enforce IMDSv2, and understand why it is the most important control against SSRF

### 4.2.3 Lesson: Load Balancing and Auto Scaling [10 hours]
- **Topics**
  - 4.2.3.1 ALB and NLB
  - 4.2.3.2 Target groups and health checks
  - 4.2.3.3 Launch templates
  - 4.2.3.4 Scaling policies
  - 4.2.3.5 ACM and HTTPS
- **Hands-on**
  - 4.2.3.T1 Auto Scaling group behind an ALB with an ACM certificate
  - 4.2.3.T2 Load-test it with `hey` and observe scaling

### 4.2.4 Lesson: Route 53 and CloudFront [10 hours]
- **Topics**
  - 4.2.4.1 Hosted zones
  - 4.2.4.2 Routing policy types
  - 4.2.4.3 Health checks
  - 4.2.4.4 CloudFront distributions
  - 4.2.4.5 Origin Access Control
  - 4.2.4.6 Caching and invalidation
- **Hands-on**
  - 4.2.4.T1 Register an inexpensive domain and point it at CloudFront in front of S3

### Challenge 4.2.C [8 hours]
1. 4.2.C.1 Build a three-tier website
2. 4.2.C.2 Public ALB
3. 4.2.C.3 EC2 instances in private subnets with no public IP
4. 4.2.C.4 Database in an isolated subnet
5. 4.2.C.5 Prove with Flow Logs that the database has no internet connectivity

## 4.3 Module: Storage and Databases [35 hours]

### 4.3.1 Lesson: S3 [12 hours]
- **Topics**
  - 4.3.1.1 Storage classes and lifecycle policies
  - 4.3.1.2 Versioning and MFA Delete
  - 4.3.1.3 Bucket policies and ACLs
  - 4.3.1.4 Block Public Access
  - 4.3.1.5 Encryption: SSE-S3 and SSE-KMS
  - 4.3.1.6 Presigned URLs
  - 4.3.1.7 Object Lock
  - 4.3.1.8 Replication
- **Hands-on**
  - 4.3.1.T1 Host a static website, then place it behind CloudFront only and block direct access
  - 4.3.1.T2 Write a bucket policy that enforces TLS and KMS encryption

### 4.3.2 Lesson: EBS and EFS [6 hours]
- **Topics**
  - 4.3.2.1 EBS types: gp3 and io2
  - 4.3.2.2 Snapshots and encryption
  - 4.3.2.3 EFS and mount targets
- **Hands-on**
  - 4.3.2.T1 Mount EFS on two servers and verify file sharing

### 4.3.3 Lesson: RDS and Aurora [10 hours]
- **Topics**
  - 4.3.3.1 Multi-AZ vs. read replicas
  - 4.3.3.2 Parameter groups
  - 4.3.3.3 Backups and point-in-time recovery
  - 4.3.3.4 Encryption
  - 4.3.3.5 Secrets Manager integration
- **Hands-on**
  - 4.3.3.T1 Deploy a private RDS instance in an isolated subnet, connect to it from EC2 only, then restore it from a snapshot

### 4.3.4 Lesson: DynamoDB [7 hours]
- **Topics**
  - 4.3.4.1 Partition and sort keys
  - 4.3.4.2 GSI and LSI
  - 4.3.4.3 Capacity modes
  - 4.3.4.4 Streams
  - 4.3.4.5 Fine-grained access control with IAM
- **Hands-on**
  - 4.3.4.T1 Create a table with a Lambda function that writes to it

### Challenge 4.3.C [5 hours]
1. 4.3.C.1 Complete the Cloud Resume Challenge (cloudresumechallenge.dev)
2. 4.3.C.2 Host a resume website on S3 and CloudFront
3. 4.3.C.3 Add a visitor counter using Lambda, DynamoDB, and API Gateway
4. 4.3.C.4 This is the most important portfolio piece at this stage

## 4.4 Module: Serverless and Integration [30 hours]

### 4.4.1 Lesson: Lambda [10 hours]
- **Topics**
  - 4.4.1.1 Runtimes and handlers
  - 4.4.1.2 Triggers
  - 4.4.1.3 Layers
  - 4.4.1.4 Execution roles
  - 4.4.1.5 Environment variables and secrets
  - 4.4.1.6 Concurrency
  - 4.4.1.7 Cold starts
- **Hands-on**
  - 4.4.1.T1 Build a Lambda that automatically cleans up old snapshots
  - 4.4.1.T2 Build a Lambda that deletes a security group open on port 22 as soon as it is created (via EventBridge)

### 4.4.2 Lesson: API Gateway, SQS, SNS, and Step Functions [10 hours]
- **Topics**
  - 4.4.2.1 REST vs. HTTP APIs
  - 4.4.2.2 Authorizers
  - 4.4.2.3 Queues and DLQs
  - 4.4.2.4 Topics
  - 4.4.2.5 State machines
- **Hands-on**
  - 4.4.2.T1 Build an API that accepts a request and places it in SQS, with a Lambda function processing it

### 4.4.3 Lesson: SAM and CloudFormation [10 hours]
- **Topics**
  - 4.4.3.1 Templates
  - 4.4.3.2 Stacks and change sets
  - 4.4.3.3 Parameters and outputs
  - 4.4.3.4 Drift detection
  - 4.4.3.5 SAM CLI
- **Hands-on**
  - 4.4.3.T1 Rebuild the entire Cloud Resume project using CloudFormation or SAM

## 4.5 Module: Certification Preparation [20 hours]

### 4.5.1 Lesson: Cloud Practitioner CLF-C02 [5 hours]
- **Hands-on**
  - 4.5.1.T1 Complete the free Skill Builder course
  - 4.5.1.T2 Take practice exams
  - 4.5.1.T3 Schedule the exam

### 4.5.2 Lesson: Solutions Architect Associate SAA-C03 [15 hours]
- **Resources**
  - 4.5.2.1 Andrew Brown's course on freeCodeCamp (YouTube, free)
  - 4.5.2.2 Tutorials Dojo practice exams (paid, inexpensive, and widely regarded as the best)
  - 4.5.2.3 AWS Skill Builder Exam Prep (partially free)
- **Prerequisite**
  - 4.5.2.4 Do not schedule the exam until you consistently score above 85% on practice exams

## 4.Z Domain 4 Certifications and Deliverables

1. 4.Z.1 AWS Cloud Practitioner and AWS Solutions Architect Associate (exams are paid; Skill Builder courses and badges are free)
2. 4.Z.2 Free: AWS Educate badges and AWS Cloud Quest
3. 4.P.1 Cloud Resume Challenge
4. 4.P.2 Three-tier website
5. 4.P.3 The Python auditor tool from Domain 3, deployed as a Lambda function that runs daily

---

# Domain 5: DevOps (Terraform, Docker, CI/CD, and Kubernetes) [180 hours]

## 5.1 Module: Docker [35 hours]

### 5.1.1 Lesson: Container Internals [8 hours]
- **Topics**
  - 5.1.1.1 Namespaces and cgroups
  - 5.1.1.2 Containers vs. VMs
  - 5.1.1.3 Images and layers
  - 5.1.1.4 Registries
- **Hands-on**
  - 5.1.1.T1 Play with Docker (labs.play-with-docker.com), free
  - 5.1.1.T2 Run a container and inspect its namespaces from within Linux

### 5.1.2 Lesson: Dockerfile and Compose [12 hours]
- **Topics**
  - 5.1.2.1 FROM, RUN, COPY, CMD, and ENTRYPOINT
  - 5.1.2.2 Multi-stage builds
  - 5.1.2.3 Volumes and networks
  - 5.1.2.4 docker compose
  - 5.1.2.5 .dockerignore
  - 5.1.2.6 Health checks
- **Hands-on**
  - 5.1.2.T1 Containerize your application into an image under 100 MB
  - 5.1.2.T2 Run an application and a database with Compose

### 5.1.3 Lesson: Docker Security [10 hours]
- **Topics**
  - 5.1.3.1 Running as a non-root user
  - 5.1.3.2 Read-only filesystem
  - 5.1.3.3 Dropping capabilities
  - 5.1.3.4 Secrets
  - 5.1.3.5 Image scanning with Trivy
  - 5.1.3.6 Image signing with Cosign
  - 5.1.3.7 Docker Bench
- **Hands-on**
  - 5.1.3.T1 Scan an official image with Trivy and list its vulnerabilities
  - 5.1.3.T2 Fix an intentionally insecure Dockerfile until the critical vulnerabilities are gone

### 5.1.4 Lesson: AWS ECR, ECS, and Fargate [5 hours]
- **Topics**
  - 5.1.4.1 ECR and image scanning
  - 5.1.4.2 Task definitions
  - 5.1.4.3 Services
  - 5.1.4.4 Task roles
- **Hands-on**
  - 5.1.4.T1 Push an image to ECR and run it on Fargate behind an ALB

### Challenge 5.1.C (CTF)
1. 5.1.C.1 TryHackMe Docker rooms: Docker Rodeo and Container Vulnerabilities
2. 5.1.C.2 Escape from a privileged container in your own lab
3. 5.1.C.3 Write-up: why the escape succeeded and how to prevent it

## 5.2 Module: Terraform [45 hours]

### 5.2.1 Lesson: IaC Fundamentals [10 hours]
- **Topics**
  - 5.2.1.1 Providers and resources
  - 5.2.1.2 Variables and outputs
  - 5.2.1.3 State
  - 5.2.1.4 plan, apply, and destroy
  - 5.2.1.5 HCL
- **Hands-on**
  - 5.2.1.T1 HashiCorp Developer tutorials (free)
  - 5.2.1.T2 Create a bucket, then an EC2 instance, with Terraform

### 5.2.2 Lesson: State and Backends [8 hours]
- **Topics**
  - 5.2.2.1 Remote state on S3
  - 5.2.2.2 DynamoDB locking
  - 5.2.2.3 Workspaces
  - 5.2.2.4 terraform import
- **Hands-on**
  - 5.2.2.T1 Migrate state to an encrypted S3 backend with locking
  - 5.2.2.T2 Import a resource that you created manually

### 5.2.3 Lesson: Modules and Design [12 hours]
- **Topics**
  - 5.2.3.1 Writing modules
  - 5.2.3.2 Registry
  - 5.2.3.3 for_each and count
  - 5.2.3.4 Dynamic blocks
  - 5.2.3.5 Data sources
  - 5.2.3.6 Lifecycle
- **Hands-on**
  - 5.2.3.T1 Build a simple VPC module and reuse it in two environments: dev and prod

### 5.2.4 Lesson: Terraform in Teams [10 hours]
- **Topics**
  - 5.2.4.1 Terratest or `terraform test`
  - 5.2.4.2 tflint
  - 5.2.4.3 Pre-commit hooks
  - 5.2.4.4 Drift
  - 5.2.4.5 Terraform Cloud or Atlantis (concepts)
  - 5.2.4.6 Secrets in IaC
- **Hands-on**
  - 5.2.4.T1 Configure pre-commit to check your code before every commit

### 5.2.5 Lesson: Certification Review [5 hours]
- **Hands-on**
  - 5.2.5.T1 HashiCorp Terraform Associate (003): practice exams
  - 5.2.5.T2 The exam is paid (approximately $70) and optional, but valuable for a resume

### Challenge 5.2.C
1. 5.2.C.1 Rebuild your entire three-tier website from Domain 4 using Terraform
2. 5.2.C.2 One command to build (apply) and one command to tear down (destroy)
3. 5.2.C.3 Maximum build time of 10 minutes

## 5.3 Module: CI/CD [30 hours]

### 5.3.1 Lesson: GitHub Actions [14 hours]
- **Topics**
  - 5.3.1.1 Workflows, jobs, and steps
  - 5.3.1.2 Triggers
  - 5.3.1.3 Secrets and environments
  - 5.3.1.4 Matrix builds
  - 5.3.1.5 Caching
  - 5.3.1.6 Reusable workflows
  - 5.3.1.7 Runners
  - 5.3.1.8 OIDC with AWS (no access keys)
- **Hands-on**
  - 5.3.1.T1 Build a pipeline that builds a Docker image and pushes it to ECR
  - 5.3.1.T2 Configure OIDC instead of long-lived keys

### 5.3.2 Lesson: Complete Pipeline [10 hours]
- **Topics**
  - 5.3.2.1 Lint, test, build, scan, deploy
  - 5.3.2.2 Environments and approvals
  - 5.3.2.3 Rollback
  - 5.3.2.4 Blue/green and canary deployments (concepts)
- **Hands-on**
  - 5.3.2.T1 Build a pipeline that deploys to ECS with a manual approval gate for production

### 5.3.3 Lesson: Supply Chain Security [6 hours]
- **Topics**
  - 5.3.3.1 Dependabot
  - 5.3.3.2 SAST: CodeQL and Semgrep
  - 5.3.3.3 SCA
  - 5.3.3.4 SBOM with Syft
  - 5.3.3.5 Pinning Actions by SHA
  - 5.3.3.6 Secret scanning
- **Hands-on**
  - 5.3.3.T1 Add CodeQL, Trivy, and gitleaks to the pipeline and fail the build on a critical vulnerability

### Challenge 5.3.C
1. 5.3.C.1 A pipeline that contains no long-lived secrets
2. 5.3.C.2 It scans the code, the container, and the IaC
3. 5.3.C.3 Demonstrate this with a screenshot of the run log

## 5.4 Module: Kubernetes [60 hours]

### 5.4.1 Lesson: Architecture and Fundamentals [12 hours]
- **Topics**
  - 5.4.1.1 Control plane: API server, etcd, scheduler, and controller manager
  - 5.4.1.2 Nodes and kubelet
  - 5.4.1.3 Pods, ReplicaSets, and Deployments
  - 5.4.1.4 Services and Ingress
  - 5.4.1.5 ConfigMaps and Secrets
- **Hands-on**
  - 5.4.1.T1 Introduction to Kubernetes (LFS158) from the Linux Foundation (free)
  - 5.4.1.T2 Free KillerCoda labs
  - 5.4.1.T3 Run Kind or Minikube locally

### 5.4.2 Lesson: Day-to-Day Operations [16 hours]
- **Topics**
  - 5.4.2.1 kubectl
  - 5.4.2.2 YAML
  - 5.4.2.3 Namespaces
  - 5.4.2.4 Labels and selectors
  - 5.4.2.5 Probes
  - 5.4.2.6 Resources: requests and limits
  - 5.4.2.7 Volumes and PVCs
  - 5.4.2.8 StatefulSets
  - 5.4.2.9 Jobs and CronJobs
  - 5.4.2.10 Helm
- **Hands-on**
  - 5.4.2.T1 Deploy an application with a database using Helm
  - 5.4.2.T2 Practice troubleshooting: CrashLoopBackOff, ImagePullBackOff, and Pending

### 5.4.3 Lesson: Networking and Storage [10 hours]
- **Topics**
  - 5.4.3.1 CNI
  - 5.4.3.2 Network policies
  - 5.4.3.3 Ingress controllers
  - 5.4.3.4 CoreDNS
  - 5.4.3.5 StorageClasses
- **Hands-on**
  - 5.4.3.T1 Write a network policy that fully isolates a namespace and prove the isolation with curl

### 5.4.4 Lesson: Amazon EKS [14 hours]
- **Topics**
  - 5.4.4.1 Clusters and managed node groups
  - 5.4.4.2 Fargate profiles
  - 5.4.4.3 IRSA and Pod Identity
  - 5.4.4.4 AWS Load Balancer Controller
  - 5.4.4.5 Add-ons
  - 5.4.4.6 Karpenter (concepts)
- **Hands-on**
  - 5.4.4.T1 Create a cluster with Terraform and deploy your application with Helm
  - 5.4.4.T2 Delete the cluster immediately afterward (the control plane alone costs approximately $0.10 per hour)

### 5.4.5 Lesson: CKA Preparation [8 hours]
- **Hands-on**
  - 5.4.5.T1 killer.sh (included with the exam purchase) or KodeKloud
  - 5.4.5.T2 The exam is paid and hands-on. It is optional at this stage and recommended before the CKS in Domain 8

### Challenge 5.4.C (CTF)
1. 5.4.C.1 Kubernetes Goat (open-source GitHub repository): core scenarios
2. 5.4.C.2 Write-ups for the first 5 scenarios

## 5.Z Domain 5 Certifications and Deliverables

1. 5.Z.1 Free: Introduction to Kubernetes from the Linux Foundation (LFS158)
2. 5.Z.2 Free: AWS Skill Builder badges (Containers)
3. 5.Z.3 Free: Docker and the free portions of KodeKloud courses
4. 5.Z.4 Suggested paid: Terraform Associate and CKA
5. 5.P.1 **Capstone project**: a Docker application deployed to AWS (ECS or EKS) entirely through Terraform
6. 5.P.2 A GitHub Actions pipeline using OIDC
7. 5.P.3 Security scanning (Trivy, gitleaks, and CodeQL) integrated into the pipeline
8. 5.P.4 README, architecture diagram, and runbook
9. 5.P.5 At this point you are ready to apply for Cloud/DevOps Engineer roles. Begin applying in parallel with Domain 6

---

# Domain 6: Security Fundamentals [150 hours]

## 6.1 Module: Concepts, Cryptography, and Identity [40 hours]

### 6.1.1 Lesson: Core Concepts [8 hours]
- **Topics**
  - 6.1.1.1 CIA triad
  - 6.1.1.2 AAA
  - 6.1.1.3 Defense in depth
  - 6.1.1.4 Least privilege
  - 6.1.1.5 Zero Trust
  - 6.1.1.6 Threat, vulnerability, and risk
  - 6.1.1.7 CVE and CVSS
  - 6.1.1.8 MITRE ATT&CK (structure)
  - 6.1.1.9 Kill Chain
- **Hands-on**
  - 6.1.1.T1 TryHackMe Pre-Security path, then Introduction to Cyber Security
  - 6.1.1.T2 ATT&CK Navigator: choose 5 techniques and write how you would detect each

### 6.1.2 Lesson: Cryptography [12 hours]
- **Topics**
  - 6.1.2.1 Symmetric encryption: AES and modes
  - 6.1.2.2 Asymmetric encryption: RSA and ECC
  - 6.1.2.3 Hashing: SHA-2, bcrypt, and Argon2
  - 6.1.2.4 HMAC
  - 6.1.2.5 Digital signatures
  - 6.1.2.6 Key exchange: Diffie-Hellman
  - 6.1.2.7 PKI, CAs, and certificate chains
  - 6.1.2.8 Salting
- **Hands-on**
  - 6.1.2.T1 CryptoHack: the introductory General and Mathematics tracks (free)
  - 6.1.2.T2 OpenSSL: create a private CA, issue certificates, and verify them
  - 6.1.2.T3 CyberChef for decoding multiple encodings

### 6.1.3 Lesson: Authentication and Authorization [12 hours]
- **Topics**
  - 6.1.3.1 Passwords and password cracking: hashcat and John the Ripper
  - 6.1.3.2 MFA: TOTP and FIDO2/WebAuthn
  - 6.1.3.3 SSO and SAML
  - 6.1.3.4 OAuth 2.0 and OIDC
  - 6.1.3.5 JWT
  - 6.1.3.6 Kerberos (concepts)
  - 6.1.3.7 Session management
- **Hands-on**
  - 6.1.3.T1 PortSwigger Academy: Authentication, OAuth, and JWT (free)
  - 6.1.3.T2 Crack a real hash in TryHackMe using hashcat

### 6.1.4 Lesson: GRC and Frameworks [8 hours]
- **Topics**
  - 6.1.4.1 NIST CSF and ISO 27001
  - 6.1.4.2 CIS Controls
  - 6.1.4.3 SOC 2
  - 6.1.4.4 PCI DSS
  - 6.1.4.5 GDPR
  - 6.1.4.6 Risk assessment
  - 6.1.4.7 Policies
- **Hands-on**
  - 6.1.4.T1 Choose a fictional company and write a risk register of 15 risks with likelihood, impact, and treatment

### Challenge 6.1.C (CTF)
1. 6.1.C.1 Complete the picoCTF Cryptography category
2. 6.1.C.2 CryptoHack: 30 challenges
3. 6.1.C.3 Write-up on weak RSA and how it is broken

## 6.2 Module: Web Application Security [45 hours]

### 6.2.1 Lesson: OWASP Top 10 [20 hours]
- **Topics**
  - 6.2.1.1 Injection: SQLi and command injection
  - 6.2.1.2 Broken access control and IDOR
  - 6.2.1.3 Cryptographic failures
  - 6.2.1.4 XSS: reflected, stored, and DOM-based
  - 6.2.1.5 CSRF
  - 6.2.1.6 SSRF
  - 6.2.1.7 Security misconfiguration
  - 6.2.1.8 Vulnerable components
  - 6.2.1.9 Authentication failures
  - 6.2.1.10 Insecure deserialization
- **Hands-on**
  - 6.2.1.T1 PortSwigger Web Security Academy (the best free resource): SQLi, XSS, access control, and SSRF, with at least 50 labs
  - 6.2.1.T2 OWASP Juice Shop in Docker: at least 30 challenges

### 6.2.2 Lesson: Tools [10 hours]
- **Topics**
  - 6.2.2.1 Burp Suite: Proxy, Repeater, Intruder, and Decoder
  - 6.2.2.2 ffuf and gobuster
  - 6.2.2.3 sqlmap
  - 6.2.2.4 Nikto
  - 6.2.2.5 OWASP ZAP
- **Hands-on**
  - 6.2.2.T1 Test DVWA and WebGoat in your lab
  - 6.2.2.T2 Use ZAP in the Domain 5 pipeline

### 6.2.3 Lesson: Secure Development [8 hours]
- **Topics**
  - 6.2.3.1 Input validation
  - 6.2.3.2 Output encoding
  - 6.2.3.3 Parameterized queries
  - 6.2.3.4 Secrets management
  - 6.2.3.5 Security headers: CSP and HSTS
  - 6.2.3.6 SAST and DAST
- **Hands-on**
  - 6.2.3.T1 Fix Juice Shop vulnerabilities on a separate branch and write a pull request explaining each fix

### 6.2.4 Lesson: API Security [7 hours]
- **Topics**
  - 6.2.4.1 OWASP API Top 10
  - 6.2.4.2 BOLA
  - 6.2.4.3 Mass assignment
  - 6.2.4.4 Rate limiting
  - 6.2.4.5 JWT attacks
- **Hands-on**
  - 6.2.4.T1 OWASP crAPI challenge
  - 6.2.4.T2 PortSwigger API testing

### Challenge 6.2.C (CTF)
1. 6.2.C.1 HTB Academy: Web Fundamentals path, then Bug Bounty Hunter (free modules or via Cubes)
2. 6.2.C.2 5 web machines on TryHackMe
3. 6.2.C.3 Write-up for each

## 6.3 Module: Blue Team and Detection [35 hours]

### 6.3.1 Lesson: Logs and SIEM [12 hours]
- **Topics**
  - 6.3.1.1 Log sources
  - 6.3.1.2 Normalization
  - 6.3.1.3 Splunk or ELK
  - 6.3.1.4 SPL and KQL
  - 6.3.1.5 Correlation rules
  - 6.3.1.6 Alert fatigue
- **Hands-on**
  - 6.3.1.T1 Splunk Free (free up to 500 MB per day) or Elastic
  - 6.3.1.T2 Load a publicly available Boss of the SOC dataset and write 10 queries that detect malicious behavior

### 6.3.2 Lesson: Threat Detection [12 hours]
- **Topics**
  - 6.3.2.1 Sigma rules
  - 6.3.2.2 YARA
  - 6.3.2.3 Indicators of compromise
  - 6.3.2.4 Threat intelligence: MISP and OpenCTI
  - 6.3.2.5 Atomic Red Team
- **Hands-on**
  - 6.3.2.T1 Execute 5 Atomic Red Team techniques on a Windows VM and write a Sigma rule for each
  - 6.3.2.T2 Use VirusTotal and AbuseIPDB to investigate IOCs

### 6.3.3 Lesson: Incident Response [11 hours]
- **Topics**
  - 6.3.3.1 NIST IR lifecycle: preparation, detection, containment, eradication, recovery, and lessons learned
  - 6.3.3.2 Forensics: memory and disk
  - 6.3.3.3 Chain of custody
  - 6.3.3.4 Playbooks
  - 6.3.3.5 Post-mortems
- **Hands-on**
  - 6.3.3.T1 TryHackMe SOC Level 1 path
  - 6.3.3.T2 CyberDefenders: 5 challenges (or Blue Team Labs, or LetsDefend, which is partially free)

### Challenge 6.3.C
1. 6.3.C.1 Investigate a full-attack dataset: phishing, execution, persistence, and exfiltration
2. 6.3.C.2 Write a professional incident report with a timeline
3. 6.3.C.3 IOCs
4. 6.3.C.4 Root cause
5. 6.3.C.5 Recommendations

## 6.4 Module: Security+ and Methodology [30 hours]

### 6.4.1 Lesson: Penetration Testing Methodology [10 hours]
- **Topics**
  - 6.4.1.1 Reconnaissance
  - 6.4.1.2 Scanning
  - 6.4.1.3 Exploitation
  - 6.4.1.4 Post-exploitation
  - 6.4.1.5 Reporting
  - 6.4.1.6 PTES and the OWASP Testing Guide
  - 6.4.1.7 Legal considerations and authorization
- **Hands-on**
  - 6.4.1.T1 Complete the TryHackMe Jr Penetration Tester path or HTB Starting Point
  - 6.4.1.T2 Write a full penetration test report for a single machine

### 6.4.2 Lesson: Security+ SY0-701 Review [20 hours]
- **Topics (the five exam domains)**
  - 6.4.2.1 General Security Concepts
  - 6.4.2.2 Threats and Vulnerabilities
  - 6.4.2.3 Security Architecture
  - 6.4.2.4 Security Operations
  - 6.4.2.5 Security Program Management
- **Hands-on**
  - 6.4.2.T1 Complete Professor Messer's course (free)
  - 6.4.2.T2 Practice exams (Jason Dion or Professor Messer)
  - 6.4.2.T3 Do not schedule the exam until you consistently score above 85%
  - 6.4.2.T4 The exam is paid (approximately $400) and is the most requested certification for entry-level roles
  - 6.4.2.T5 Try the free ISC2 CC certification first, since it is a real exam at no cost

## 6.Z Domain 6 Certifications and Deliverables

1. 6.Z.1 Free: ISC2 Certified in Cybersecurity (CC): free training and exam through the ISC2 initiative
2. 6.Z.2 Free: Cisco Introduction to Cybersecurity, Cybersecurity Essentials, Ethical Hacker, and Junior Cybersecurity Analyst Career Path
3. 6.Z.3 Free: Fortinet Certified Fundamentals and Certified Associate in Cybersecurity
4. 6.Z.4 Free: IBM SkillsBuild Cybersecurity Fundamentals
5. 6.Z.5 Google Cybersecurity Certificate (free to audit)
6. 6.Z.6 Paid: CompTIA Security+ (the target certification for this domain)
7. 6.P.1 A full penetration test with a report
8. 6.P.2 An incident investigation in Splunk
9. 6.P.3 Juice Shop vulnerability fixes
10. 6.P.4 Benchmark: 100+ TryHackMe rooms and a top 5% ranking by the end of this domain, which carries more weight than a certificate

---

# Domain 7: AWS Cloud Security [190 hours]

> **Standing references:** hackingthe.cloud (free), the AWS Security workshops at catalog.workshops.aws, and the Security Learning Plan on AWS Skill Builder.

## 7.1 Module: Advanced IAM and Privilege Escalation [40 hours]

### 7.1.1 Lesson: Advanced Policies [12 hours]
- **Topics**
  - 7.1.1.1 Condition keys: aws:SourceIp, aws:PrincipalOrgID, and aws:MultiFactorAuthPresent
  - 7.1.1.2 Permission boundaries
  - 7.1.1.3 Session policies
  - 7.1.1.4 SCPs: deny lists vs. allow lists
  - 7.1.1.5 ABAC with tags
  - 7.1.1.6 Resource policies and cross-account access
  - 7.1.1.7 NotAction and NotResource, and their risks
- **Hands-on**
  - 7.1.1.T1 Write an SCP that prevents disabling CloudTrail and prevents creating resources outside two Regions
  - 7.1.1.T2 Test it in the Domain 4 Organization

### 7.1.2 Lesson: Identity at Scale [8 hours]
- **Topics**
  - 7.1.2.1 IAM Identity Center with an external IdP
  - 7.1.2.2 Federation: SAML and OIDC
  - 7.1.2.3 Eliminating long-term keys
  - 7.1.2.4 Credential Report
  - 7.1.2.5 Access Advisor
  - 7.1.2.6 Access Analyzer: external and unused access
  - 7.1.2.7 Roles Anywhere
- **Hands-on**
  - 7.1.2.T1 Generate a Credential Report and write a script that identifies keys older than 90 days
  - 7.1.2.T2 Enable Access Analyzer and review its findings

### 7.1.3 Lesson: IAM Attacks [14 hours]
- **Topics**
  - 7.1.3.1 Privilege escalation paths: iam:PassRole, iam:CreatePolicyVersion, sts:AssumeRole, lambda:UpdateFunctionCode, and others
  - 7.1.3.2 Enumeration with Pacu and enumerate-iam
  - 7.1.3.3 Persistence through roles and access keys
  - 7.1.3.4 SSRF to IMDS and credential theft
  - 7.1.3.5 Confused deputy
- **Hands-on**
  - 7.1.3.T1 IAM Vulnerable (GitHub repository, deployed with Terraform) to practice every escalation path
  - 7.1.3.T2 CloudGoat (Rhino Security Labs): iam_privesc_by_rollback and iam_privesc_by_attachment
  - 7.1.3.T3 For each scenario: how you detected it and how you prevent it

### 7.1.4 Lesson: Detecting Privilege Escalation [6 hours]
- **Topics**
  - 7.1.4.1 CloudTrail events corresponding to each attack
  - 7.1.4.2 Athena queries
  - 7.1.4.3 EventBridge alerts
- **Hands-on**
  - 7.1.4.T1 Execute an attack from IAM Vulnerable and detect it in CloudTrail with an automated alert within minutes

### Challenge 7.1.C (CTF)
1. 7.1.C.1 The Big IAM Challenge (if not already completed)
2. 7.1.C.2 flaws2.cloud
3. 7.1.C.3 CloudFoxable by Bishop Fox
4. 7.1.C.4 Pwned Labs (free challenges)
5. 7.1.C.5 Deliverable: 10 write-ups

## 7.2 Module: Data Protection [30 hours]

### 7.2.1 Lesson: KMS [12 hours]
- **Topics**
  - 7.2.1.1 AWS managed keys vs. customer managed keys
  - 7.2.1.2 Key policies and grants
  - 7.2.1.3 Envelope encryption
  - 7.2.1.4 Key rotation
  - 7.2.1.5 Multi-Region keys
  - 7.2.1.6 Encryption context
  - 7.2.1.7 CloudHSM (concepts)
- **Hands-on**
  - 7.2.1.T1 Create a key with a policy that allows one role to encrypt and a different role to decrypt
  - 7.2.1.T2 Encrypt S3, EBS, and RDS with your own keys

### 7.2.2 Lesson: Secrets [8 hours]
- **Topics**
  - 7.2.2.1 Secrets Manager vs. SSM Parameter Store
  - 7.2.2.2 Automatic rotation
  - 7.2.2.3 Resource policies
  - 7.2.2.4 Usage in Lambda, ECS, and EKS
- **Hands-on**
  - 7.2.2.T1 Replace a hardcoded database password with a secret rotated every 30 days

### 7.2.3 Lesson: S3 Security and Sensitive Data [10 hours]
- **Topics**
  - 7.2.3.1 Account-level Block Public Access
  - 7.2.3.2 Access Points
  - 7.2.3.3 VPC endpoint policies
  - 7.2.3.4 Macie
  - 7.2.3.5 Object Lock
  - 7.2.3.6 Bucket policy with a Deny for non-TLS requests
  - 7.2.3.7 Presigned URL risks
- **Hands-on**
  - 7.2.3.T1 Enable Macie on a bucket containing fake data (card numbers) and review the findings
  - 7.2.3.T2 Test a public-bucket attack in a private lab and then remediate it

### Challenge 7.2.C
1. 7.2.C.1 Design a system that stores sensitive data
2. 7.2.C.2 One KMS key per environment
3. 7.2.C.3 Encryption at every layer
4. 7.2.C.4 Rotated secrets
5. 7.2.C.5 Locked-down S3
6. 7.2.C.6 CloudTrail data events
7. 7.2.C.7 Document the decisions with a diagram and a short article

## 7.3 Module: Network and Edge Security [30 hours]

### 7.3.1 Lesson: Secure Network Design [10 hours]
- **Topics**
  - 7.3.1.1 Security group references instead of IP addresses
  - 7.3.1.2 NACLs
  - 7.3.1.3 Isolated subnets
  - 7.3.1.4 VPC endpoints and PrivateLink
  - 7.3.1.5 Egress filtering
  - 7.3.1.6 Transit Gateway and inspection VPC
- **Hands-on**
  - 7.3.1.T1 Remove all outbound access from private subnets except through endpoints
  - 7.3.1.T2 Detect open security groups using your script from Domain 3

### 7.3.2 Lesson: WAF, Shield, and Network Firewall [10 hours]
- **Topics**
  - 7.3.2.1 AWS WAF: managed rules, rate-based rules, and Bot Control
  - 7.3.2.2 Shield Standard vs. Advanced
  - 7.3.2.3 Network Firewall (Suricata rules)
  - 7.3.2.4 Route 53 Resolver DNS Firewall
  - 7.3.2.5 Firewall Manager
- **Hands-on**
  - 7.3.2.T1 Place WAF in front of an ALB, run the SQLi and XSS attacks from Domain 6, and observe the blocking
  - 7.3.2.T2 Write a rate-based rule

### 7.3.3 Lesson: Secure Access [10 hours]
- **Topics**
  - 7.3.3.1 Session Manager instead of SSH
  - 7.3.3.2 Bastion host vs. SSM
  - 7.3.3.3 Client VPN
  - 7.3.3.4 Verified Access
  - 7.3.3.5 EC2 Instance Connect
- **Hands-on**
  - 7.3.3.T1 Eliminate port 22 entirely from your infrastructure and adopt Session Manager with session logging to S3

### Challenge 7.3.C (CTF)
1. 7.3.C.1 CloudGoat: SSRF scenario (ec2_ssrf)
2. 7.3.C.2 CloudGoat: Lambda scenarios
3. 7.3.C.3 Write-up

## 7.4 Module: Detection and Monitoring [40 hours]

### 7.4.1 Lesson: Centralized Logging [10 hours]
- **Topics**
  - 7.4.1.1 Organization trail
  - 7.4.1.2 CloudTrail Lake
  - 7.4.1.3 S3 log storage with Object Lock
  - 7.4.1.4 VPC Flow Logs and DNS logs
  - 7.4.1.5 ELB and WAF logs
  - 7.4.1.6 Log Archive account
  - 7.4.1.7 Amazon Security Lake (concepts)
- **Hands-on**
  - 7.4.1.T1 Create a separate Log Archive account and send CloudTrail logs to it from every account
  - 7.4.1.T2 Make the log bucket non-deletable

### 7.4.2 Lesson: GuardDuty, Inspector, and Macie [10 hours]
- **Topics**
  - 7.4.2.1 GuardDuty finding types
  - 7.4.2.2 Runtime Monitoring for EKS and ECS
  - 7.4.2.3 Inspector for EC2, ECR, and Lambda
  - 7.4.2.4 Suppression rules
  - 7.4.2.5 Delegated administrator
- **Hands-on**
  - 7.4.2.T1 Generate sample GuardDuty findings
  - 7.4.2.T2 Perform genuinely suspicious behavior in your own environment only (for example, calling an API from a Tor IP address)

### 7.4.3 Lesson: Security Hub and Config [10 hours]
- **Topics**
  - 7.4.3.1 CIS AWS Foundations and AWS Foundational Security Best Practices standards
  - 7.4.3.2 Config rules and conformance packs
  - 7.4.3.3 Automated remediation (SSM Automation)
  - 7.4.3.4 Aggregators
  - 7.4.3.5 Detective (concepts)
- **Hands-on**
  - 7.4.3.T1 Enable Security Hub across the Organization and remediate every critical finding
  - 7.4.3.T2 Write a custom Config rule using Lambda

### 7.4.4 Lesson: Automation and SOAR [10 hours]
- **Topics**
  - 7.4.4.1 EventBridge rules
  - 7.4.4.2 Lambda for response actions
  - 7.4.4.3 SNS to Slack
  - 7.4.4.4 Step Functions playbooks
  - 7.4.4.5 Chatbot
- **Hands-on**
  - 7.4.4.T1 On detection of a leaked key: a Lambda function disables it, isolates the role, and sends an alert
  - 7.4.4.T2 Test it with a test key

### Challenge 7.4.C
1. 7.4.C.1 Stratus Red Team (Datadog, free): execute 10 attack techniques against AWS in your environment
2. 7.4.C.2 Confirm that each technique generates an alert
3. 7.4.C.3 Compile a table: technique, event, alert, and time to detect

## 7.5 Module: Incident Response and Investigation on AWS [25 hours]

### 7.5.1 Lesson: Cloud IR Fundamentals [10 hours]
- **Topics**
  - 7.5.1.1 AWS Security Incident Response Guide
  - 7.5.1.2 Containment: isolating instances, disabling keys, and deny SCPs
  - 7.5.1.3 Evidence preservation: snapshots and memory
  - 7.5.1.4 Investigation with CloudTrail and Athena
  - 7.5.1.5 Ready-made playbooks (aws-samples/aws-incident-response-playbooks)
- **Hands-on**
  - 7.5.1.T1 Simulate an incident: a leaked key used to launch cryptomining instances
  - 7.5.1.T2 Investigate with CloudTrail, contain the incident, and write a report

### 7.5.2 Lesson: Forensics for EC2 and Containers [8 hours]
- **Topics**
  - 7.5.2.1 Snapshots and volume mounting for analysis
  - 7.5.2.2 Memory acquisition with LiME
  - 7.5.2.3 Container forensics
  - 7.5.2.4 Timeline analysis
- **Hands-on**
  - 7.5.2.T1 Analyze a snapshot from a compromised instance (one you create yourself) on an isolated analysis instance

### 7.5.3 Lesson: Threat Modeling [7 hours]
- **Topics**
  - 7.5.3.1 STRIDE
  - 7.5.3.2 Data flow diagrams
  - 7.5.3.3 Attack trees
  - 7.5.3.4 AWS Threat Composer
  - 7.5.3.5 OWASP Threat Dragon
- **Hands-on**
  - 7.5.3.T1 Threat-model your Domain 5 capstone project and document 15 threats with mitigations

### Challenge 7.5.C
1. 7.5.C.1 End-to-end scenario: you are first the attacker, then the defender
2. 7.5.C.2 Compromise your own environment through CloudGoat or an SSRF vulnerability
3. 7.5.C.3 Investigate from the defensive side using logs only
4. 7.5.C.4 Dual report (Red and Blue)

## 7.6 Module: Governance and Landing Zone [15 hours]

### 7.6.1 Lesson: Control Tower and Multi-Account Strategy [8 hours]
- **Topics**
  - 7.6.1.1 Landing zone
  - 7.6.1.2 Recommended OUs: Security, Infrastructure, Workloads, and Sandbox
  - 7.6.1.3 Guardrails
  - 7.6.1.4 Account Factory
  - 7.6.1.5 Delegated administrators
- **Hands-on**
  - 7.6.1.T1 Build a small landing zone using Control Tower or Terraform

### 7.6.2 Lesson: Compliance Scanning [7 hours]
- **Topics**
  - 7.6.2.1 Prowler
  - 7.6.2.2 ScoutSuite
  - 7.6.2.3 CIS Benchmark
  - 7.6.2.4 CSPM (concepts)
  - 7.6.2.5 AWS Audit Manager
- **Hands-on**
  - 7.6.2.T1 Run Prowler against your account and review the report
  - 7.6.2.T2 Goal: remediate every Critical and High finding

## 7.7 Module: AWS Security Specialty Preparation [10 additional hours]

### 7.7.1 Lesson: Review
- **Exam domains**
  - 7.7.1.1 Threat Detection and Incident Response
  - 7.7.1.2 Security Logging and Monitoring
  - 7.7.1.3 Infrastructure Security
  - 7.7.1.4 Identity and Access Management
  - 7.7.1.5 Data Protection
  - 7.7.1.6 Management and Security Governance
- **Hands-on**
  - 7.7.1.T1 Courses by Adrian Cantrill or Stephane Maarek (paid)
  - 7.7.1.T2 Tutorials Dojo exams and AWS Skill Builder Exam Prep
  - 7.7.1.T3 Keep an error log for every practice exam
  - 7.7.1.T4 The exam is paid (approximately $300). Verify the current exam code (SCS-C02 or later) before scheduling

## 7.Z Domain 7 Certifications and Deliverables

1. 7.Z.1 AWS Certified Security Specialty
2. 7.Z.2 Free: AWS Skill Builder badges (Security Learning Plan), AWS Educate, and AWS Security Workshops
3. 7.P.1 **Capstone project**: a secured multi-account AWS environment built with Terraform
   - 7.P.1.1 Isolated Log Archive account
   - 7.P.1.2 Organization trail
   - 7.P.1.3 GuardDuty, Security Hub, and Config across all accounts
   - 7.P.1.4 SCPs
   - 7.P.1.5 IAM Identity Center
   - 7.P.1.6 Automated alerting and remediation
   - 7.P.1.7 Architecture diagram
   - 7.P.1.8 Before-and-after Prowler report
4. 7.P.2 Second project: write-ups for 10 attack-and-defense scenarios from CloudGoat, IAM Vulnerable, and flaws (this is what persuades hiring managers)

---

# Domain 8: Advanced Specialization and Employment [120 hours]

## 8.1 Module: Kubernetes and Container Security [35 hours]

### 8.1.1 Lesson: Securing the Cluster [15 hours]
- **Topics**
  - 8.1.1.1 RBAC
  - 8.1.1.2 Pod Security Standards and admission controllers
  - 8.1.1.3 OPA Gatekeeper or Kyverno
  - 8.1.1.4 Network policies
  - 8.1.1.5 Secrets and etcd encryption
  - 8.1.1.6 Audit logging
  - 8.1.1.7 Supply chain: Cosign and admission verification
- **Hands-on**
  - 8.1.1.T1 Run kube-bench and Kubescape against a cluster and remediate the findings
  - 8.1.1.T2 Write a Kyverno policy that blocks privileged pods and unsigned images

### 8.1.2 Lesson: Runtime Security and Detection [10 hours]
- **Topics**
  - 8.1.2.1 Falco
  - 8.1.2.2 eBPF (concepts)
  - 8.1.2.3 GuardDuty EKS Runtime Monitoring
  - 8.1.2.4 Container escape detection
- **Hands-on**
  - 8.1.2.T1 Install Falco, spawn a shell inside a pod, and detect it

### 8.1.3 Lesson: Attacking Kubernetes [10 hours]
- **Topics**
  - 8.1.3.1 Exposed dashboard and kubelet
  - 8.1.3.2 RBAC abuse
  - 8.1.3.3 Service account token theft
  - 8.1.3.4 Privileged pod escape
  - 8.1.3.5 Cloud pivoting from a pod to IAM
- **Hands-on**
  - 8.1.3.T1 Complete Kubernetes Goat
  - 8.1.3.T2 Wiz EKS Cluster Games (eksclustergames.com)
  - 8.1.3.T3 Wiz K8s LAN Party (k8slanparty.com)
  - 8.1.3.T4 Write-up for each challenge

### Challenge 8.1.C
1. 8.1.C.1 Produce a security report for the EKS cluster from the Domain 5 project: vulnerabilities
2. 8.1.C.2 Attacks
3. 8.1.C.3 Fixes
4. 8.1.C.4 Before and after
5. 8.1.C.5 Review the CKS certification (requires a valid CKA; the exam is hands-on and paid)

## 8.2 Module: DevSecOps and IaC Security [25 hours]

### 8.2.1 Lesson: IaC Scanning [10 hours]
- **Topics**
  - 8.2.1.1 Checkov, Trivy config, and tfsec (now merged into Trivy)
  - 8.2.1.2 KICS
  - 8.2.1.3 Policy as code: OPA, Conftest, and Sentinel
  - 8.2.1.4 Terraform plan scanning
- **Hands-on**
  - 8.2.1.T1 TerraGoat (Bridgecrew): an intentionally vulnerable Terraform repository. Scan it and remediate every finding
  - 8.2.1.T2 Add Checkov to the Domain 5 pipeline

### 8.2.2 Lesson: Complete Security Pipeline [10 hours]
- **Topics**
  - 8.2.2.1 Secret scanning: gitleaks and TruffleHog
  - 8.2.2.2 SAST, SCA, and DAST
  - 8.2.2.3 Container scanning
  - 8.2.2.4 SBOM and provenance (SLSA)
  - 8.2.2.5 Policy gating
  - 8.2.2.6 Signed commits
- **Hands-on**
  - 8.2.2.T1 Build a single pipeline that scans the code, the dependencies, the IaC, and the image, and runs ZAP after deployment
  - 8.2.2.T2 Document the duration of each stage

### 8.2.3 Lesson: CSPM and Cloud-Native Tools [5 hours]
- **Topics**
  - 8.2.3.1 CSPM, CWPP, and CNAPP (concepts)
  - 8.2.3.2 Wiz, Prisma Cloud, and Orca (market landscape)
  - 8.2.3.3 Open-source tools: Prowler, Cloud Custodian, and Steampipe
- **Hands-on**
  - 8.2.3.T1 Steampipe: write 10 SQL queries against your account's resources to identify misconfigurations

## 8.3 Module: Attacking the Cloud [30 hours]

### 8.3.1 Lesson: Cloud Penetration Testing on AWS [20 hours]
- **Topics**
  - 8.3.1.1 Reconnaissance: subdomain takeover, public buckets, and exposed keys
  - 8.3.1.2 Initial access: SSRF, leaked keys, and misconfigurations
  - 8.3.1.3 Enumeration
  - 8.3.1.4 Privilege escalation
  - 8.3.1.5 Lateral movement across accounts
  - 8.3.1.6 Persistence
  - 8.3.1.7 Exfiltration
  - 8.3.1.8 Defense evasion
- **Hands-on**
  - 8.3.1.T1 Pacu, ScoutSuite, and Prowler (offensive mode)
  - 8.3.1.T2 CloudGoat full scenarios
  - 8.3.1.T3 Pwned Labs (most labs require a subscription)
  - 8.3.1.T4 Hacking the Cloud as a reference

### 8.3.2 Lesson: Cloud Red Teaming [10 hours]
- **Topics**
  - 8.3.2.1 MITRE ATT&CK Cloud Matrix
  - 8.3.2.2 Purple teaming
  - 8.3.2.3 Detection validation
- **Hands-on**
  - 8.3.2.T1 Write a 10-step attack plan against the Domain 7 environment
  - 8.3.2.T2 Verify how many steps your defenses detected

### Challenge 8.3.C
1. 8.3.C.1 Participate in CTF events listed on CTFtime (team or individual)
2. 8.3.C.2 Work toward the Cloud category in any competition
3. 8.3.C.3 Write up at least one challenge after each competition

## 8.4 Module: Other Cloud Platforms [20 hours]

### 8.4.1 Lesson: Azure [12 hours]
- **Topics**
  - 8.4.1.1 The free AZ-900 learning path on Microsoft Learn, followed by SC-900
  - 8.4.1.2 Entra ID and RBAC
  - 8.4.1.3 Defender for Cloud and Sentinel
- **Hands-on**
  - 8.4.1.T1 Repeat a scaled-down version of the Domain 4 project on Azure using a free account

### 8.4.2 Lesson: GCP [8 hours]
- **Topics**
  - 8.4.2.1 IAM and projects
  - 8.4.2.2 Security Command Center
- **Hands-on**
  - 8.4.2.T1 Google Cloud Skills Boost (free credits and labs)
  - 8.4.2.T2 ThunderCTF (GCP challenges)

> **Objective:** understand the concepts shared across providers (identity, networking, logging, and KMS), even if you specialize in AWS. The market frequently requires multi-cloud knowledge.

## 8.5 Module: Employment [10 hours]

### 8.5.1 Lesson: Resume [3 hours]
- 8.5.1.1 Limit it to one page
- 8.5.1.2 Lead with projects, then certifications
- 8.5.1.3 Quantify results (for example, "reduced 30 vulnerabilities" or "automated X")
- 8.5.1.4 Link every project to its GitHub repository

### 8.5.2 Lesson: Portfolio [3 hours]
- 8.5.2.1 Build a personal website using the Cloud Resume Challenge
- 8.5.2.2 Include all of your write-ups and projects

### 8.5.3 Lesson: Interviews [4 hours]
- **Topics (practice questions)**
  - 8.5.3.1 IAM evaluation logic
  - 8.5.3.2 What happens if an access key is compromised?
  - 8.5.3.3 Design a secure network in AWS
  - 8.5.3.4 SSRF on EC2: how is it prevented?
  - 8.5.3.5 Explain the Shared Responsibility Model
  - 8.5.3.6 Incident response scenario
- **Hands-on**
  - 8.5.3.T1 Record yourself answering these questions

### 8.5.4 Job Search
- 8.5.4.1 Start with an entry-level role such as Cloud Engineer, Junior DevOps Engineer, SOC Analyst, or Cloud Support Associate, then transition to Cloud Security
- 8.5.4.2 Use LinkedIn, Wellfound, and company career pages
- 8.5.4.3 Begin applying after Domain 5

## 8.Z Domain 8 Certifications and Deliverables

1. 8.Z.1 CKA, then CKS (optional and paid)
2. 8.Z.2 Free: Azure Fundamentals on Microsoft Learn (the badge is free) and Google Cloud Skills Boost badges
3. 8.P.1 EKS security report
4. 8.P.2 Complete security pipeline
5. 8.P.3 Purple team plan
6. 8.P.4 CTF write-ups

---

# Free Certifications and Badges

> Offers change, so verify on the official page before starting. Course-completion certificates demonstrate effort but are not a substitute for paid certifications in hiring.

| Provider | What You Can Earn | Domain |
|---|---|---|
| Cisco Networking Academy | Networking Basics, Network Devices, Introduction to Cybersecurity, Cybersecurity Essentials, Ethical Hacker, Junior Cybersecurity Analyst Career Path, Python Essentials, Linux Essentials | 1, 2, 3, 6 |
| ISC2 | Certified in Cybersecurity (CC): free training and exam through the One Million Certified initiative | 6 |
| Fortinet | Fortinet Certified Fundamentals and Certified Associate in Cybersecurity: free training and exam | 6 |
| AWS Skill Builder | Cloud Practitioner Essentials, Security Learning Plan, digital badges, Cloud Quest | 4, 7 |
| AWS Educate | Cloud 101 and other badges | 4 |
| Microsoft Learn | AZ-900 and SC-900 learning paths and badges (exams are paid) | 8 |
| Google Cloud Skills Boost | Badges and labs with free credits | 8 |
| Linux Foundation | Introduction to Kubernetes (LFS158) and others | 5 |
| IBM SkillsBuild | Cybersecurity Fundamentals and others, with badges | 6 |
| Google (Coursera) | Google Cybersecurity Certificate: free to audit; certificate is paid or available via financial aid | 6 |
| freeCodeCamp | Scientific Computing with Python and others | 3 |
| GitHub Skills | Interactive courses (no official certificate) | 3, 5 |
| Splunk Education | Free fundamentals courses | 6 |
| TryHackMe / HTB | Official certifications are paid, but path badges and rankings are free | 2, 6, 7 |

# Highest-ROI Paid Certifications (in Order)

1. AWS Solutions Architect Associate
2. CompTIA Security+
3. AWS Security Specialty
4. Terraform Associate
5. CKA, then CKS
6. AWS Cloud Practitioner (optional if you plan to take SAA directly)

> Look for discount vouchers: AWS occasionally offers vouchers through Skill Builder and student programs, and CompTIA and others run seasonal promotions.

---

# Suggested Weekly Routine (2 Hours per Day)

1. Sunday to Wednesday: 1 hour of study + 1 hour of hands-on practice
2. Thursday: Anki review and finish write-ups
3. Friday: free-form CTF or a TryHackMe room
4. Saturday: a larger lab (3 to 4 hours) or project work
5. Monthly: review progress, update GitHub, and clean up the AWS account

# Domain Readiness Criteria

| Domain | Criterion |
|---|---|
| 1 and 2 | Complete all of Bandit, and explain the TCP handshake and subnetting without references |
| 3 | A published Python tool |
| 4 | Pass SAA with infrastructure you built yourself |
| 5 | All projects are built with Terraform and a pipeline, with no secrets in code |
| 6 | Security+ or ISC2 CC, and 100 TryHackMe rooms |
| 7 | Execute an IAM attack and detect it within minutes |
| 8 | Answer a Cloud Security interview with examples from your own projects |
