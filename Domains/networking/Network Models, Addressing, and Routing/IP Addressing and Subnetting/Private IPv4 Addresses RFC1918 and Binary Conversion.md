# Private IPv4 Addresses (RFC1918) and Binary Conversion

## Overview

This document covers two fundamental networking concepts: IPv4 binary representation and private IP addressing.

It explains how IPv4 addresses are represented in binary, how decimal-to-binary conversion works, and how RFC1918 defines private IPv4 address ranges.

## 1. IPv4 Address Structure

IPv4 (Internet Protocol Version 4) is a network addressing system that uses 32-bit addresses.

An IPv4 address consists of four groups called **Octets**, separated by dots.

Example:

```text
192.168.1.10
```

Each octet contains 8 bits.

```text
192       .168       .1         .10
8 bits    8 bits     8 bits     8 bits

Total: 4 × 8 = 32 bits
```

Each octet has a decimal value between 0 and 255.

## 2. Binary Number System

Computers represent data using the binary number system (Base-2).

Binary uses only two digits:

- `0` – OFF
- `1` – ON

Each bit in an IPv4 octet represents a specific decimal value.

### Binary Place Values

| Bit Position | Decimal Value |
|---|---:|
| 1 | 128 |
| 2 | 64 |
| 3 | 32 |
| 4 | 16 |
| 5 | 8 |
| 6 | 4 |
| 7 | 2 |
| 8 | 1 |

### Decimal to Binary Conversion

Example: Convert 192 into binary.

```text
192 = 128 + 64

128  64  32  16  8  4  2  1
 1    1   0   0   0  0  0  0
```

Result:

```text
192 = 11000000
```

Another example:

```text
10 = 8 + 2

10 = 00001010
```

### Binary to Decimal Conversion

To convert binary into decimal, add the values of all positions containing `1`.

Example:

```text
11000000

128 + 64 = 192
```

Result:

```text
11000000 = 192
```

### Complete IPv4 Example

```text
IPv4:
192.168.1.10

Binary:
11000000.10101000.00000001.00001010
```

Understanding binary conversion is essential for interpreting subnet masks, calculating network boundaries, and performing subnetting operations.

---

## 3. RFC1918 – Private IPv4 Addressing

RFC1918 defines three IPv4 address blocks reserved for private networks.

These addresses are commonly used in internal network infrastructures, including home networks, corporate environments, and private servers.

### Private IPv4 Address Ranges

| Private Network | CIDR | Address Range |
|---|---|---|
| 10.0.0.0 | /8 | 10.0.0.0 – 10.255.255.255 |
| 172.16.0.0 | /12 | 172.16.0.0 – 172.31.255.255 |
| 192.168.0.0 | /16 | 192.168.0.0 – 192.168.255.255 |

### Understanding the Three Ranges

**Range 1: 10.0.0.0/8**

A large private address block commonly used in enterprise networks and internal infrastructures.

**Range 2: 172.16.0.0/12**

A private address block covering the second octet from 16 through 31.

**Range 3: 192.168.0.0/16**

Commonly used in home networks, small offices, and local environments.

### Important Note

Not every address beginning with `172` is private.

For example:

```text
172.20.1.5  → Private
172.40.1.5  → Not RFC1918 private
```

Only addresses within the defined RFC1918 ranges are considered private.

---

## 4. Private IP vs Public IP

### Private IP Address

- Used inside private networks.
- Not directly routable over the public Internet.
- Allows internal devices to communicate.
- Commonly used with NAT.

### Public IP Address

- Globally unique within the public addressing system.
- Routable across the public Internet.
- Used for communication between public networks.

## 5. NAT – Network Address Translation

NAT is a networking mechanism that translates IP addresses between different addressing domains.

A common use case is allowing multiple devices with private IP addresses to access the Internet through a public IP address.

Example:

```text
Private Network

PC 1: 192.168.1.10
PC 2: 192.168.1.11
PC 3: 192.168.1.12
          |
          v
       Router
          |
          v
     Public IP
          |
          v
       Internet
```

NAT is widely used in home networks, enterprise infrastructures, and cloud environments.

---

## Key Takeaways

| Concept | Description |
|---|---|
| IPv4 | 32-bit addressing system |
| Octet | Group of 8 bits |
| Binary | Base-2 number system |
| Decimal | Base-10 number system |
| RFC1918 | Defines private IPv4 address blocks |
| Private IP | Used inside private networks |
| Public IP | Globally routable address |
| NAT | Translates IP addresses |

## Conclusion

Understanding binary representation and RFC1918 private addressing provides the foundation for working with IPv4 networks.

These concepts are essential for network administration, infrastructure management, cybersecurity, and cloud networking.

**Topics:** IPv4 · Binary Conversion · RFC1918 · Private IP · Public IP · NAT · Networking Fundamentals
