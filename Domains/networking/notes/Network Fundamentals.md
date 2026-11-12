# Network Fundamentals
## Encapsulation, PDU, TCP, UDP, TCP Flags, Flow Control, ICMP, Ping & Traceroute

---

## Table of Contents

1. [Encapsulation and PDU](#1-encapsulation-and-pdu)
2. [TCP vs. UDP](#2-tcp-vs-udp)
3. [TCP Three-Way Handshake](#3-tcp-three-way-handshake)
4. [TCP Flags](#4-tcp-flags)
5. [TCP Window and Flow Control](#5-tcp-window-and-flow-control)
6. [ICMP](#6-icmp)
7. [Ping](#7-ping)
8. [Traceroute](#8-traceroute)
9. [Ping vs. Traceroute](#9-ping-vs-traceroute)
10. [Practical Lab](#10-practical-lab)
11. [Key Takeaways](#11-key-takeaways)

---

# 1. Encapsulation and PDU

## 1.1. What Is Encapsulation?

**Encapsulation** is the process of adding protocol-specific information to data as it moves down through the network layers before transmission.

Each layer adds its own control information, typically in the form of headers and, in some cases, trailers.

This information enables devices to identify, route, transport, and process data correctly across a network.

### How Encapsulation Works

When a host sends data to another device, the data passes through several network layers:

1. **Application Layer:** Generates the original application data.
2. **Transport Layer:** Adds a TCP or UDP header containing information such as source and destination port numbers.
3. **Network Layer:** Adds an IP header containing source and destination IP addresses.
4. **Data Link Layer:** Adds a frame header and trailer containing link-layer information, such as MAC addresses and error-detection data.
5. **Physical Layer:** Transmits the resulting bitstream over the physical medium.

### Encapsulation Process

```text
Application Layer
       |
       v
      Data
       |
       v
Transport Layer
       |
       v
  TCP / UDP Header
       |
       v
Network Layer
       |
       v
     IP Header
       |
       v
Data Link Layer
       |
       v
 Ethernet Header + Trailer
       |
       v
Physical Layer
       |
       v
      Bits
```

## 1.2. What Is a PDU?

**PDU (Protocol Data Unit)** is the technical name given to a unit of data processed by a particular network layer.

The PDU name changes as data moves through the network stack.

### PDU Names in the OSI Model

| OSI Layer | PDU Name |
|---|---|
| Layer 7 – Application | Data |
| Layer 6 – Presentation | Data |
| Layer 5 – Session | Data |
| Layer 4 – Transport | Segment (TCP) / Datagram (UDP) |
| Layer 3 – Network | Packet |
| Layer 2 – Data Link | Frame |
| Layer 1 – Physical | Bits |

**Important terminology:**

- TCP PDU: Segment.
- UDP PDU: Datagram.
- IP PDU: Packet.
- Ethernet PDU: Frame.

## 1.3. Decapsulation

**Decapsulation** is the reverse process of encapsulation.

When data reaches its destination, it moves up through the network layers. Each layer processes and removes its corresponding protocol information before passing the remaining payload to the next layer.

### Encapsulation vs. Decapsulation

| Encapsulation | Decapsulation |
|---|---|
| Occurs at the sending side | Occurs at the receiving side |
| Adds protocol headers and trailers | Processes and removes protocol headers and trailers |
| Moves down the network stack | Moves up the network stack |
| Prepares data for transmission | Recovers the original application data |

## 1.4. Addressing at Different Layers

Different network layers use different addressing mechanisms.

| Address Type | Function |
|---|---|
| Port Number | Identifies the application endpoint or service |
| IP Address | Identifies a logical network endpoint |
| MAC Address | Identifies a network interface on a local network link |

**Example:**

When accessing an HTTPS website:

- The destination IP address identifies the remote host.
- TCP port 443 identifies the HTTPS service endpoint.
- The destination MAC address identifies the next-hop interface on the local Ethernet network.

Note: The destination MAC address normally belongs to the local gateway when communicating with a remote network, not the final remote server.

---

# 2. TCP vs. UDP

TCP and UDP are transport-layer protocols (Layer 4 of the OSI model).

Both provide communication between applications running on different devices, but they use different mechanisms to achieve this.

## 2.1. TCP (Transmission Control Protocol)

TCP is a connection-oriented transport protocol that provides reliable, ordered byte-stream delivery.

Before normal data transmission begins, TCP establishes a connection between the communicating endpoints.

### Main Characteristics

1. **Connection-Oriented:** Establishes a logical connection before data transfer.
2. **Reliable Delivery:** Uses acknowledgments and retransmissions to recover from data loss.
3. **Ordered Delivery:** Ensures that data is delivered to the application in the correct byte order.
4. **Error Detection:** Uses checksums to detect corrupted segments.
5. **Flow Control:** Prevents the sender from overwhelming the receiver.
6. **Congestion Control:** Adjusts transmission behavior according to network conditions.

### Common TCP Applications

- HTTP/1.1 and HTTP/2
- HTTPS
- SSH
- FTP
- SMTP
- IMAP

## 2.2. UDP (User Datagram Protocol)

UDP is a connectionless transport protocol that provides lightweight, datagram-based communication.

Unlike TCP, UDP does not establish a connection before sending data and does not provide built-in delivery acknowledgments, retransmissions, or ordering guarantees.

### Main Characteristics

1. **Connectionless:** No connection establishment is required.
2. **Low Overhead:** Uses a small 8-byte header.
3. **No Delivery Guarantee:** Does not guarantee that datagrams reach their destination.
4. **No Ordering Guarantee:** Datagrams may arrive out of order.
5. **No Built-in Retransmission:** Lost datagrams are not automatically retransmitted by UDP.
6. **No Built-in Flow Control:** Does not implement TCP-style receiver flow control.

### Common UDP Applications

- DNS
- DHCP
- VoIP
- Real-time communication
- Online gaming
- Live media streaming

Note: Modern protocols such as QUIC operate over UDP while implementing additional reliability and congestion-control mechanisms at a higher layer.

## 2.3. TCP vs. UDP Comparison

| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable delivery mechanisms | No built-in delivery guarantee |
| Data Ordering | Ordered byte stream | No ordering guarantee |
| Retransmission | Supported | Not built in |
| Header Size | 20 bytes minimum | 8 bytes |
| Flow Control | Supported | Not built in |
| Congestion Control | Supported | Not built in |
| Communication Unit | Segment | Datagram |

**Key Takeaway:**

- TCP prioritizes reliable and ordered data delivery.
- UDP provides lightweight communication with minimal protocol overhead.

UDP is not inherently faster in every scenario. Its main advantage is reduced protocol overhead and the absence of mandatory connection-establishment and retransmission mechanisms.

---

# 3. TCP Three-Way Handshake

## 3.1. Overview

The **TCP Three-Way Handshake** is the process used to establish a TCP connection between a client and a server.

It consists of three steps:

### Step 1: SYN (Synchronize)

The client sends a TCP segment with the SYN flag enabled.

Purpose:

- Initiates the connection.
- Synchronizes the initial sequence number.

### Step 2: SYN-ACK (Synchronize-Acknowledge)

The server responds with a segment containing both SYN and ACK flags.

Purpose:

- Acknowledges the client's SYN.
- Provides the server's initial sequence number.

### Step 3: ACK (Acknowledgment)

The client sends an ACK segment.

Purpose:

- Acknowledges the server's SYN.
- Completes the connection establishment process.

After the handshake is successfully completed, the TCP connection enters the **ESTABLISHED** state.

## 3.2. Three-Way Handshake Diagram

```text
       CLIENT                         SERVER
          |                              |
          |                              |
          | -------- SYN --------------> |
          |                              |
          | <------- SYN + ACK ----------|
          |                              |
          | -------- ACK --------------> |
          |                              |
          |                              |
          |       CONNECTION ESTABLISHED |
          |                              |
```

## 3.3. Sequence and Acknowledgment Numbers

TCP uses sequence and acknowledgment numbers to track transmitted data.

For example:

- Client sends SYN with sequence number 1000.
- Server responds with SYN-ACK using sequence number 5000 and acknowledgment number 1001.
- Client sends ACK with acknowledgment number 5001.

The acknowledgment number indicates the next sequence number expected from the other endpoint.

**Key Takeaway:**

```text
SYN → SYN-ACK → ACK
```

Three messages establish a TCP connection.

---

# 4. TCP Flags

## 4.1. What Are TCP Flags?

TCP flags are control bits located in the TCP header.

They indicate the purpose of a TCP segment and help manage connection establishment, data transmission, and connection termination.

## 4.2. Important TCP Flags

| Flag | Full Name | Purpose |
|---|---|---|
| SYN | Synchronize | Initiates a connection and synchronizes sequence numbers |
| ACK | Acknowledgment | Indicates that the acknowledgment field is valid |
| FIN | Finish | Initiates graceful connection termination |
| RST | Reset | Resets or aborts a connection |
| PSH | Push | Requests prompt delivery of buffered data to the application |
| URG | Urgent | Indicates that the urgent pointer field is significant |

### SYN

Used during TCP connection establishment.

Example: The first message of the Three-Way Handshake.

### ACK

Used to acknowledge received data and connection-control messages.

Example: The third message of the Three-Way Handshake.

### FIN

Used to initiate an orderly connection shutdown.

It indicates that the sender has finished transmitting data in that direction.

### RST

Used to immediately reset a TCP connection.

It may appear when a connection attempt is rejected or an existing connection cannot continue.

### PSH

Requests that received data be passed promptly to the receiving application.

### URG

Indicates that the Urgent Pointer field contains significant information.

## 4.3. TCP Flags in Network Security

Understanding TCP flags is essential for network analysis and security testing.

Examples:

- **SYN Scan:** Uses SYN packets to investigate TCP port states.
- **FIN Scan:** Uses FIN packets to examine how ports respond.
- **RST Analysis:** Helps identify connection resets and rejected connections.

These behaviors can be inspected using tools such as Wireshark and Nmap.

---

# 5. TCP Window and Flow Control

## 5.1. What Is TCP Window?

The TCP Receive Window (rwnd) is a flow-control mechanism that specifies how much additional data a receiver is currently willing to accept.

Its purpose is to prevent a sender from transmitting more data than the receiver can handle.

### Example

Consider two computers:

- Computer A: Sender.
- Computer B: Receiver.

If Computer B has limited available buffer space, it advertises a smaller receive window.

Computer A must respect this advertised limit when transmitting data.

This prevents receiver-buffer overflow.

## 5.2. Sliding Window Mechanism

TCP uses a mechanism called the **Sliding Window** to improve transmission efficiency.

Instead of sending one segment and waiting for its acknowledgment before sending the next, TCP can transmit multiple bytes of data within the permitted window.

As acknowledgments arrive, the transmission window advances.

### Benefits

- Improves network utilization.
- Reduces unnecessary waiting.
- Supports continuous data transmission.
- Improves communication efficiency.

## 5.3. Receive Window vs. Congestion Window

Two important TCP mechanisms control the amount of data that can be in transit.

| Mechanism | Purpose |
|---|---|
| Receive Window (rwnd) | Controls data transmission according to receiver capacity |
| Congestion Window (cwnd) | Controls data transmission according to network congestion |

The sender's effective transmission limit is constrained by the smaller of these two values.

**Key Takeaway:**

- rwnd = Receiver protection.
- cwnd = Network congestion management.

Flow Control and Congestion Control solve different problems.

---

# 6. ICMP

## 6.1. What Is ICMP?

**ICMP (Internet Control Message Protocol)** is a network-layer protocol used to communicate error conditions and diagnostic information related to IP packet delivery.

It helps network devices identify and report problems encountered during IP communication.

ICMP is not a transport protocol and does not provide application-to-application communication like TCP or UDP.

## 6.2. Common ICMP Message Types

| Message | Description |
|---|---|
| Echo Request | Requests a response from another device |
| Echo Reply | Responds to an Echo Request |
| Destination Unreachable | Indicates that a destination or network cannot be reached |
| Time Exceeded | Indicates that a packet's TTL has expired |

## 6.3. Why Is ICMP Important?

ICMP is commonly used for:

- Network diagnostics.
- Connectivity testing.
- Error reporting.
- Troubleshooting routing problems.
- Detecting packet delivery issues.

**Important:** Ping and many Traceroute implementations rely on ICMP messages.

---

# 7. Ping

## 7.1. What Is Ping?

Ping is a network diagnostic utility used to test whether a destination responds to network requests and to measure the Round-Trip Time (RTT).

It commonly uses ICMP Echo Request and Echo Reply messages.

## 7.2. Basic Usage

Linux / Kali Linux:

```bash
ping 8.8.8.8
```

Windows:

```cmd
ping 8.8.8.8
```

## 7.3. Understanding Ping Output

Example:

```text
64 bytes from 8.8.8.8: icmp_seq=1 ttl=117 time=20 ms
```

| Field | Meaning |
|---|---|
| 64 bytes | Size of the received response |
| 8.8.8.8 | Source address of the response |
| icmp_seq | ICMP sequence number |
| ttl | Remaining Time To Live value |
| time=20 ms | Round-Trip Time |

## 7.4. Important Networking Metrics

### Latency

The time required for data to travel between network endpoints.

### Round-Trip Time (RTT)

The total time required for a request to reach its destination and for the response to return.

### Packet Loss

The percentage of transmitted packets that do not receive a response.

### Why Use Ping?

- Verify basic network reachability.
- Measure round-trip time.
- Identify packet loss.
- Troubleshoot connectivity problems.

**Important Limitation:**

A failed Ping does not necessarily mean that a host is offline. Firewalls and network configurations may block ICMP traffic.

---

# 8. Traceroute

## 8.1. What Is Traceroute?

Traceroute is a network diagnostic utility used to identify the intermediate routers (hops) through which packets travel from a source device toward a destination.

It helps administrators understand network paths and investigate routing or latency problems.

## 8.2. What Is a Hop?

A **Hop** represents one router traversed by a packet along its network path.

Example:

```text
Source Computer
      |
      v
   Router 1
      |
      v
   Router 2
      |
      v
   Router 3
      |
      v
Destination Server
```

Each intermediate router represents a hop.

## 8.3. How Does Traceroute Work?

Traceroute primarily relies on the IP Time To Live (TTL) field.

TTL limits how many router hops a packet can traverse before being discarded.

Traceroute sends probes with progressively increasing TTL values:

1. First probe: TTL = 1.
2. Second probe: TTL = 2.
3. Third probe: TTL = 3.
4. The process continues until the destination is reached or the maximum hop limit is reached.

When a router decrements the TTL to zero, it normally discards the packet and returns an ICMP Time Exceeded message.

Traceroute uses these responses to identify intermediate routers.

## 8.4. Commands

Linux / Kali Linux:

```bash
traceroute google.com
```

Windows:

```cmd
tracert google.com
```

## 8.5. Why Use Traceroute?

- Identify the network path to a destination.
- Discover intermediate routers.
- Investigate possible routing problems.
- Identify hops with unusually high response times.
- Troubleshoot connectivity issues.

**Important Limitation:**

Some routers filter or do not respond to traceroute probes. In such cases, the output may display:

```text
* * *
```

This does not necessarily indicate a network failure.

Note: Traceroute implementations may use UDP, ICMP, or TCP probes depending on the operating system and selected options.

---

# 9. Ping vs. Traceroute

| Feature | Ping | Traceroute |
|---|---|---|
| Primary Purpose | Test destination reachability | Discover the network path |
| Intermediate Routers | Not displayed | Displayed when they respond |
| Response Time | Measures RTT | Measures response time per hop |
| Common Protocol | ICMP | UDP, ICMP, or TCP depending on implementation |
| Main Application | Connectivity testing | Routing diagnostics |

### When Should You Use Each Tool?

Use **Ping** when you want to determine whether a destination responds and measure its round-trip time.

Use **Traceroute** when you want to investigate the path packets take toward a destination and identify intermediate network devices.

---

# 10. Practical Lab

The following exercises provide hands-on experience with the concepts covered in this document.

## 10.1. Test Network Connectivity

```bash
ping 8.8.8.8
```

**Objective:**

- Test basic IP connectivity.
- Observe ICMP Echo Requests and Replies.
- Measure RTT.
- Identify packet loss.

## 10.2. Test DNS Resolution and Connectivity

```bash
ping google.com
```

**Objective:**

- Observe hostname resolution.
- Identify the resolved IP address.
- Test connectivity to the destination.

Note: A successful DNS resolution does not guarantee that ICMP traffic will be permitted.

## 10.3. Discover the Network Path

```bash
traceroute google.com
```

**Objective:**

- Identify intermediate routers.
- Observe the number of hops.
- Examine response times.
- Investigate missing responses.

## 10.4. Capture ICMP Traffic Using Wireshark

Start a Wireshark capture on your active network interface.

Apply the following display filter:

```text
icmp
```

In another terminal, execute:

```bash
ping 8.8.8.8
```

Observe the following fields:

- Source IP Address.
- Destination IP Address.
- ICMP Type.
- ICMP Code.
- Sequence Number.

Expected messages:

- Echo Request.
- Echo Reply.

## 10.5. Analyze the TCP Three-Way Handshake

Start a new Wireshark capture.

Apply the following display filter:

```text
tcp
```

Generate a TCP connection to a reachable service, for example:

```bash
curl https://example.com
```

Look for the following sequence:

```text
SYN
SYN, ACK
ACK
```

Inspect the TCP headers and identify:

- Source Port.
- Destination Port.
- Sequence Number.
- Acknowledgment Number.
- TCP Flags.
- Window Size.

**Lab Objective:** Understand how TCP establishes connections and how its control information appears in real network traffic.

---

# 11. Key Takeaways

| Concept | Essential Point |
|---|---|
| Encapsulation | Adds protocol information as data moves down network layers |
| Decapsulation | Processes and removes protocol information at the destination |
| PDU | Identifies the data unit associated with each network layer |
| TCP | Connection-oriented transport protocol with reliable delivery mechanisms |
| UDP | Connectionless transport protocol with low overhead |
| Three-Way Handshake | Establishes TCP connections using SYN, SYN-ACK, and ACK |
| TCP Flags | Control connection establishment, data handling, and termination |
| Receive Window | Controls data transmission according to receiver capacity |
| Congestion Window | Controls transmission according to network congestion |
| ICMP | Provides IP-related error reporting and diagnostic messages |
| Ping | Tests destination responsiveness and measures RTT |
| Traceroute | Identifies intermediate network hops |

## Final Conceptual Overview

These concepts are closely related and form an essential foundation for understanding network communication.

- **Encapsulation and PDU:** Explain how data is structured for transmission.
- **TCP and UDP:** Explain how applications exchange data.
- **TCP Handshake and Flags:** Explain how TCP connections are established and controlled.
- **TCP Window:** Explains how data transmission is regulated.
- **ICMP:** Provides diagnostic and error-reporting mechanisms.
- **Ping and Traceroute:** Provide practical tools for network troubleshooting.

**Learning Objective:** By completing these topics and their practical exercises, you should be able to explain the basic structure of network communication, understand the behavior of TCP and UDP, interpret common network-control messages, and perform fundamental connectivity diagnostics.

---

*Document Category: Networking Fundamentals*  
*Level: Beginner to Intermediate*  
*Environment: Linux / Kali Linux / Windows*  
*Practical Tools: Wireshark, Ping, Traceroute, Curl*
