
# Networking Fundamentals

## Nodes and Links

### Node

A **node** is an individual device connected to a network.

### Link

A **link** is a communication pathway that connects nodes within a network.

Links can be either **wired** or **wireless**.

---

## Media Access Control (MAC) Address

A **Media Access Control (MAC) address** is an identifier assigned to a network interface, such as a Network Interface Card (NIC), allowing it to be identified within a local network.

MAC addresses play an important role in communication within a local network segment, helping ensure that data is delivered to the correct network interface.

### MAC Address Structure

A traditional MAC address is **48 bits (6 bytes)** long and is typically represented in **hexadecimal format**.

It consists of six pairs of hexadecimal digits, usually separated by colons (`:`).

**Example:**

```text
00:1A:2B:3C:4D:5E
```

Each pair represents one byte (8 bits).

A traditional globally administered MAC address consists of two main parts:

1. **Organizationally Unique Identifier (OUI)** — The first 24 bits (the first three pairs of hexadecimal digits) identify the organization that registered the identifier, typically the manufacturer of the network interface.

2. **Device-specific identifier** — The remaining 24 bits (the last three pairs) are assigned by the manufacturer to distinguish individual network interfaces.

**Example breakdown:**

```text
00:1A:2B : 3C:4D:5E
   OUI  : Device-specific identifier
```

This addressing structure is designed to support globally unique MAC addresses and reduce address conflicts.

However, MAC addresses are not guaranteed to be unique in every situation, as they can be manually changed, spoofed, or randomly generated.

---


## Internet Protocol (IP) Address

An **Internet Protocol (IP) address** is a numerical identifier assigned to a network interface on a network that uses the Internet Protocol for communication.

IP addresses allow devices to identify and communicate with each other across different networks.

There are two versions of IP addresses: **IPv4** and **IPv6**.

### IPv4 (Internet Protocol Version 4)

IPv4 addresses are **32 bits long** and are typically represented as four decimal numbers separated by dots.

**Example:**

```text
192.168.1.1
```

Each number represents 8 bits (one byte) and can range from 0 to 255.

### IPv6 (Internet Protocol Version 6)

IPv6 addresses are **128 bits long** and are typically represented as eight groups of four hexadecimal digits separated by colons.

**Example:**

```text
2001:0db8:0000:0000:0000:ff00:0042:8329
```

IPv6 addresses can also be shortened by omitting leading zeros and compressing consecutive groups of zeros.

---

## Private and Public IP Addresses

IP addresses can be divided into **private** and **public** addresses.

### Private IP Addresses

**Private IP addresses** are designated for use within local networks, such as homes, schools, and offices.

These addresses are not routable on the public Internet, meaning that routers on the global Internet do not forward packets to these private address ranges.

Common private IPv4 address ranges include:

| Private IP Range | CIDR Notation |
|---|---|
| `10.0.0.0` – `10.255.255.255` | `10.0.0.0/8` |
| `172.16.0.0` – `172.31.255.255` | `172.16.0.0/12` |
| `192.168.0.0` – `192.168.255.255` | `192.168.0.0/16` |

Private IP addresses allow devices within local networks to communicate without requiring a unique public IP address for every device.

They also reduce the direct exposure of internal devices to the public Internet. However, private addressing alone does not guarantee network security.

### Public IP Addresses

**Public IP addresses** are globally unique addresses used for communication across the public Internet.

They are allocated through Internet address registries and are commonly assigned to customers by **Internet Service Providers (ISPs)**.

Public IP addresses allow devices and networks to be identified and reached across the Internet.

Unlike private IP addresses, public IP addresses are globally routable.

However, having a public IP address does not automatically mean that a device is accessible from anywhere, as firewalls and other network configurations may restrict incoming connections.

---

## Types of Networks

### Local Area Network (LAN)

A **Local Area Network (LAN)** connects devices within a relatively small geographical area.

Characteristics:

- Covers a small area, such as a home, office, or school.
- Typically owned and managed by a single person or organization.
- Generally provides high data transfer rates.
- Uses wired connections (Ethernet cables) or wireless connections (Wi-Fi).

### Wide Area Network (WAN)

A **Wide Area Network (WAN)** connects devices and networks across large geographical areas.

Characteristics:

- Covers large areas, such as cities, countries, or continents.
- Often involves multiple organizations or service providers, such as Internet Service Providers (ISPs).
- May have higher latency and lower data transfer rates than LANs due to longer transmission distances and other network conditions.
- Uses technologies such as fiber-optic connections, satellite links, and telecommunication lines.

---

## Components of a Network

Networks consist of three main categories of components:

### 1. End Devices (Hosts)

**End devices**, also known as **hosts**, are devices that send or receive data within a network.

Examples include:

- Personal computers (PCs)
- Smartphones
- Tablets
- Internet of Things (IoT) devices

End devices play an important role in both **data generation and consumption**.

They often serve as the primary interface through which users access network services and the World Wide Web.

### 2. Intermediary Devices

**Intermediary devices** facilitate communication and the flow of data between end devices, both within a Local Area Network (LAN) and between different networks.

Examples include:

- Routers
- Switches
- Wireless access points

Their role is to support efficient, reliable, and secure data transmission.

Depending on the type of device, their responsibilities may include:

- **Data forwarding** — forwarding data toward its intended destination.
- **Traffic management** — helping manage the flow of data across the network.
- **Network connectivity** — enabling communication between devices and networks.
- **Security** — some intermediary devices provide security features, such as firewalls.

### 3. Network Media and Software Components

**Network media and software components** enable communication and support the operation of a network.

#### Network Media

Network media provide the physical or wireless pathways through which data travels between devices.

Examples include:

- Ethernet cables
- Fiber-optic cables
- Wireless signals

#### Software Components

Software components define and implement the rules and procedures used for network communication.

They help ensure that data is correctly:

- Formatted
- Addressed
- Transmitted
- Routed
- Received

Together, network media and software components allow devices to communicate and exchange information.

---
