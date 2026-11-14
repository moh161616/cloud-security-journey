# Networking Fundamentals — TryHackMe Room Report

## 1. Overview

**Platform:** TryHackMe  
**Room:** [What is Networking?](https://tryhackme.com/room/whatisnetworking)  
**Category:** Networking Fundamentals  

<img width="1009" height="459" alt="image" src="https://github.com/user-attachments/assets/1c045af3-3d85-40fc-add5-55b71c1d8b6d" />


### Objective

The objective of this room was to understand the fundamental concepts of computer networking, how devices communicate, how they are identified, and how basic network connectivity can be tested.

Networking is an essential foundation in cybersecurity because almost every attack, service, and communication process depends on network infrastructure.

---

## 2. What Is Networking?

A computer network is a group of two or more devices connected together to communicate and exchange information.

Examples of network devices include:

- Computers and laptops.
- Smartphones.
- Servers.
- Security cameras.
- Network routers.

Devices communicate using predefined rules called **Protocols**.

These protocols ensure that different devices can understand and exchange information correctly.

### Key Concept

A network is not limited to computers. Any connected devices capable of communicating can be part of a network.

---

## 3. Understanding the Internet

The Internet is a global network made up of millions of interconnected smaller networks.

There are two main network types introduced in this room:

**Private Network**

A network used for communication between devices within a limited environment, such as a home or company.

Example:
- Home Wi-Fi network.
- Company internal network.

**Public Network**

A network that connects different networks and allows communication over the Internet.

### Historical Background

- ARPANET was an early network project developed in the late 1960s.
- Tim Berners-Lee invented the World Wide Web (WWW) in 1989.

**Important distinction:** The Internet and the World Wide Web are not the same thing. The Web is a service that operates over the Internet.

---

## 4. Identifying Devices on a Network

Devices need unique identifiers to communicate with each other.

This room introduces two important identifiers:

### 4.1 IP Address

**IP = Internet Protocol**

An IP address identifies a device or network interface within an IP network.

It allows devices to communicate and send data to the correct destination.

There are two main IP versions:

**IPv4**

- Uses 32-bit addresses.
- Contains four octets.
- Each octet represents 8 bits.
- Each octet has a decimal value between 0 and 255.

Example:

`192.168.1.77`

**IPv6**

- Uses 128-bit addresses.
- Provides a significantly larger address space.
- Was introduced to address IPv4 address exhaustion.

### Private vs Public IP Addresses

| Private IP | Public IP |
|---|---|
| Used inside private networks. | Used for Internet communication. |
| Not directly routable over the public Internet. | Globally routable, subject to network configuration. |
| Example: 192.168.1.77 | Example: 86.157.52.21 |

### Important Observation

Multiple devices inside the same home network can use different private IP addresses while sharing one public IP address when accessing the Internet.

This is commonly achieved through Network Address Translation (NAT).

---

### 4.2 MAC Address

**MAC = Media Access Control**

A MAC address is a Layer 2 identifier associated with a network interface.

It is commonly represented as a 48-bit hexadecimal value.

Example:

`a4:c3:f0:85:ac:2d`

A MAC address consists of:

- First 24 bits: Organizationally Unique Identifier (OUI).
- Last 24 bits: Interface-specific identifier.

### IP Address vs MAC Address

| IP Address | MAC Address |
|---|---|
| Layer 3 identifier. | Layer 2 identifier. |
| Used for logical addressing. | Used for local network frame delivery. |
| Can change depending on network configuration. | Can be changed or spoofed. |
| IPv4 or IPv6. | Usually represented in hexadecimal. |

---

## 5. MAC Address Spoofing — Practical Lab

### What Is MAC Spoofing?

MAC spoofing is the process of changing a network interface's reported MAC address to impersonate another device at Layer 2.

### Practical Scenario

The room provides an interactive hotel Wi-Fi simulation.

The scenario contains:

- Alice: Has paid for Internet access.
- Bob: Has not paid for Internet access.
- Router: Controls access based on MAC addresses.

The router allows Alice's packets but blocks Bob's packets.

### Practical Exercise

The objective was to modify Bob's MAC address to match Alice's MAC address.

This demonstrates how a network relying only on MAC-based identification can be vulnerable to impersonation.

### Security Implications

MAC spoofing can be relevant to:

- Bypassing poorly implemented MAC-based access controls.
- Network impersonation.
- Testing wireless network security.
- Understanding weaknesses in Layer 2 security.

**Security note:** MAC addresses should not be treated as strong authentication credentials because they can be spoofed.

---

## 6. Ping and ICMP

### 6.1 What Is ICMP?

**ICMP = Internet Control Message Protocol**

ICMP is a network-layer protocol used for diagnostic and error-reporting purposes.

It helps identify communication problems between network devices.

### 6.2 What Is Ping?

Ping is a network diagnostic utility that uses ICMP Echo Request and Echo Reply messages.

It helps determine:

- Whether a destination responds.
- The round-trip time (RTT).
- Whether packets are being lost.

### 6.3 How Ping Works

1. The source device sends an ICMP Echo Request.
2. The destination receives the request.
3. The destination sends an ICMP Echo Reply, if configured to respond.
4. The source measures the round-trip time.

### 6.4 Practical Commands

**Basic syntax:**

```bash
ping <IP_ADDRESS>
```

Example:

```bash
ping 10.10.10.10
```

Testing Google's public DNS address:

```bash
ping 8.8.8.8
```

### Understanding Ping Results

Important information displayed by ping includes:

- Packets transmitted.
- Packets received.
- Packet loss.
- Minimum response time.
- Average response time.
- Maximum response time.

### Security and Troubleshooting Importance

Ping is useful for:

- Basic connectivity testing.
- Identifying unreachable hosts.
- Detecting packet loss.
- Measuring network latency.
- Initial network troubleshooting.

**Important:** A failed ping does not necessarily mean that a host is offline. Firewalls may block ICMP traffic.

---

## 7. Practical Skills Acquired

After completing this room, I gained an introductory understanding of:

1. The fundamental concept of computer networking.
2. The relationship between private networks and the Internet.
3. IPv4 and IPv6 addressing.
4. The difference between public and private IP addresses.
5. The structure and purpose of MAC addresses.
6. MAC address spoofing and its security implications.
7. The purpose of ICMP.
8. Using Ping to test network connectivity.
9. Understanding basic network diagnostic results.

---

## 8. Cybersecurity Relevance

Networking knowledge is essential for understanding how systems communicate and where security weaknesses may exist.

The concepts introduced in this room are relevant to several cybersecurity areas:

**Network Security**
- Understanding network communication.
- Identifying devices and network interfaces.
- Understanding access-control weaknesses.

**Penetration Testing**
- Understanding IP addressing.
- Testing network connectivity.
- Learning about MAC spoofing.

**Cloud Security**
- Understanding public and private IP addressing.
- Understanding how devices communicate across networks.
- Building the foundation for learning virtual networks and network security groups.

---

## 9. Knowledge Limitations and Next Steps

This room provides an introduction to networking rather than an advanced technical explanation.

The following topics require further study:

- OSI Model and TCP/IP Model.
- Network encapsulation and decapsulation.
- Packets and Ethernet frames.
- Subnetting and CIDR.
- TCP and UDP.
- TCP Three-Way Handshake.
- Ports and network services.
- Routing and switching.
- DNS and DHCP.
- Network traffic analysis using Wireshark.

These subjects will help build a deeper understanding of network communication and prepare for more advanced cybersecurity and cloud networking topics.

---

## 10. Conclusion

Completing this room provided a practical introduction to computer networking and its fundamental concepts.

The most important lesson is that understanding how devices identify each other and exchange information is essential before studying network security.

Rather than focusing only on tools, it is important to understand the protocols and mechanisms operating behind them.

**Next recommended room:** Intro to LAN.

**Learning direction:** Networking Fundamentals → LAN → OSI Model → Packets & Frames → Network Protocols.
