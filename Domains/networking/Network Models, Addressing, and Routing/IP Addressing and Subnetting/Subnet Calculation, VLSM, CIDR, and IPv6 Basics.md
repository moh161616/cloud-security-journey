# Subnet Calculation, VLSM, CIDR, and IPv6 Basics

## Overview

This document explores essential IP addressing and network segmentation concepts.

It covers subnet calculations, CIDR notation, Variable Length Subnet Masking (VLSM), and the fundamentals of IPv6 addressing.

The objective is to understand how networks are divided, how IP addresses are allocated, and how IPv4 and IPv6 addressing structures work.

---

## 1. CIDR – Classless Inter-Domain Routing

CIDR is a method of representing IP network prefixes using slash notation.

Example:

```text
192.168.1.0/24
```

The `/24` represents the number of bits assigned to the network portion.

IPv4 contains 32 bits in total.

```text
Network Bits: 24
Host Bits:     8

Total:        32
```

### Host Calculation

The number of usable IPv4 host addresses in a conventional subnet is calculated using:

```text
2^(32 - Prefix Length) - 2
```

Two addresses are normally reserved:

- Network Address.
- Broadcast Address.

Example:

```text
192.168.1.0/26

32 - 26 = 6 Host Bits

2^6 - 2 = 62 Usable Hosts
```

### Common CIDR Prefixes

| CIDR | Subnet Mask | Usable Hosts |
|---|---|---:|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /29 | 255.255.255.248 | 6 |
| /30 | 255.255.255.252 | 2 |

A larger CIDR prefix means fewer host bits and therefore fewer available host addresses.

---

## 2. Subnetting

Subnetting is the process of dividing a larger IP network into smaller logical networks.

Each subnet has its own network address, address range, and broadcast address.

### Why Subnetting Is Important

- Organizes network infrastructure.
- Separates departments and services.
- Reduces broadcast domains.
- Improves IP address management.
- Supports network segmentation.
- Helps implement security boundaries.

### Subnet Calculation Example

Consider the following network:

```text
192.168.1.0/26
```

First, calculate the number of host bits:

```text
32 - 26 = 6
```

Then calculate the total number of addresses:

```text
2^6 = 64
```

Each subnet contains 64 addresses, with 62 normally usable host addresses.

### Block Size

The block size represents the number of addresses in each subnet.

For `/26`:

```text
Subnet Mask: 255.255.255.192

Block Size = 256 - 192

Block Size = 64
```

The resulting subnet boundaries are:

| Subnet | Network Address | Address Range |
|---|---|---|
| 1 | 192.168.1.0/26 | .0 – .63 |
| 2 | 192.168.1.64/26 | .64 – .127 |
| 3 | 192.168.1.128/26 | .128 – .191 |
| 4 | 192.168.1.192/26 | .192 – .255 |

### Network Address Components

For the first subnet:

```text
Network:   192.168.1.0
First Host: 192.168.1.1
Last Host:  192.168.1.62
Broadcast:  192.168.1.63
```

Important definitions:

| Term | Description |
|---|---|
| Network Address | Identifies the subnet. |
| First Host | First normally assignable address. |
| Last Host | Last normally assignable address. |
| Broadcast Address | Used to reach all hosts in an IPv4 subnet. |
| Subnet Mask | Separates network and host portions. |

---

## 3. VLSM – Variable Length Subnet Mask

VLSM allows different subnet sizes to be used within the same network.

Instead of assigning the same number of addresses to every department, VLSM allocates address space according to actual requirements.

### Example Scenario

A company has four departments with different host requirements:

| Department | Required Hosts |
|---|---:|
| HR | 50 |
| IT | 25 |
| Finance | 10 |
| Management | 5 |

Starting network:

```text
192.168.10.0/24
```

### VLSM Allocation

The network requirements are sorted from largest to smallest.

| Department | Required Hosts | CIDR | Usable Hosts |
|---|---:|---|---:|
| HR | 50 | /26 | 62 |
| IT | 25 | /27 | 30 |
| Finance | 10 | /28 | 14 |
| Management | 5 | /29 | 6 |

### Assigned Network Ranges

| Department | Network Address | Full Address Range |
|---|---|---|
| HR | 192.168.10.0/26 | .0 – .63 |
| IT | 192.168.10.64/27 | .64 – .95 |
| Finance | 192.168.10.96/28 | .96 – .111 |
| Management | 192.168.10.112/29 | .112 – .119 |

### VLSM Allocation Principles

1. Identify the host requirements for each subnet.
2. Sort requirements from largest to smallest.
3. Calculate the smallest suitable subnet for each department.
4. Allocate network addresses sequentially.
5. Ensure that subnet ranges do not overlap.
6. Verify network and broadcast addresses.

VLSM improves address utilization and provides flexibility when designing enterprise networks.

---

## 4. IPv6 Basics

IPv6 (Internet Protocol Version 6) is the successor to IPv4.

It was developed to provide a significantly larger address space and support the growth of Internet-connected devices.

### IPv4 vs IPv6

| Feature | IPv4 | IPv6 |
|---|---|---|
| Address Length | 32 bits | 128 bits |
| Number System | Decimal | Hexadecimal |
| Structure | 4 octets | 8 groups |
| Separator | `.` | `:` |
| Broadcast | Supported | Not supported |
| Example | 192.168.1.10 | 2001:db8::1 |

### IPv6 Address Structure

Example:

```text
2001:0db8:0000:0000:0000:ff00:0042:8329
```

An IPv6 address contains:

- 128 bits.
- 8 groups.
- 16 bits per group.
- 4 hexadecimal digits per group.

### Hexadecimal Number System

IPv6 uses Base-16, known as hexadecimal.

It contains the following digits:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Values:

| Hexadecimal | Decimal |
|---|---:|
| A | 10 |
| B | 11 |
| C | 12 |
| D | 13 |
| E | 14 |
| F | 15 |

Each hexadecimal digit represents 4 bits.

Therefore:

```text
8 Groups × 16 Bits = 128 Bits
```

---

## 5. IPv6 Address Compression

IPv6 addresses can be shortened using two main compression rules.

### Rule 1: Remove Leading Zeros

Leading zeros can be removed from each individual group.

Example:

```text
Original:
2001:0db8:0000:0001

Compressed:
2001:db8:0:1
```

### Rule 2: Replace Consecutive Zero Groups

Multiple consecutive groups containing only zeros can be replaced with `::`.

Example:

```text
Original:
2001:0db8:0000:0000:0000:0000:0000:0001

Compressed:
2001:db8::1
```

The `::` notation can only appear once in an IPv6 address because using it multiple times would make the original address ambiguous.

---

## 6. IPv6 Subnetting and Prefix Length

IPv6 uses prefix lengths to identify the network portion of an address.

Example:

```text
2001:db8:abcd:0012::/64
```

A `/64` prefix divides the 128-bit address into:

```text
Network Prefix: 64 bits
Interface ID:   64 bits
```

### Common IPv6 Prefixes

| Prefix | Number of /64 Subnets |
|---|---:|
| /48 | 65,536 |
| /56 | 256 |
| /64 | 1 |

A `/64` prefix is commonly used for individual IPv6 LAN segments.

### IPv6 Broadcast

Unlike IPv4, IPv6 does not support broadcast addressing.

Instead, it uses multicast and other communication mechanisms.

---

## Key Concepts Summary

| Concept | Purpose |
|---|---|
| CIDR | Represents network prefixes. |
| Subnet Mask | Defines network and host portions. |
| Subnetting | Divides networks into smaller segments. |
| Block Size | Determines subnet address increments. |
| Network Address | Identifies a subnet. |
| Broadcast Address | Identifies the IPv4 subnet broadcast destination. |
| VLSM | Allocates different subnet sizes. |
| IPv6 | Provides a 128-bit addressing system. |
| Hexadecimal | Represents IPv6 addresses. |
| Prefix Length | Identifies the network portion of an IP address. |

---

## Conclusion

Subnetting, CIDR, and VLSM are essential concepts for designing and managing efficient IP networks.

Understanding IPv6 addressing and prefix calculations is equally important as modern network infrastructure increasingly supports both IPv4 and IPv6.

These concepts provide a foundation for enterprise networking, cloud infrastructure, network engineering, and cybersecurity.

**Topics:** Subnetting · CIDR · VLSM · Subnet Calculation · IPv4 · IPv6 · Hexadecimal · Network Segmentation · IP Addressing
