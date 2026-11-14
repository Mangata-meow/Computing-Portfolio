
# Transmission Control Protocol/Internet Protocol (TCP/IP) Model

The **Transmission Control Protocol/Internet Protocol (TCP/IP) model** is a networking model designed for practical implementation on the Internet and other networks.

It is often described as a simplified version of the OSI model because it organizes networking functions into **four layers**, rather than seven.

---

## Layer 1 — Link Layer

The **Link Layer** is responsible for handling communication over the local network, including the physical aspects of network hardware and transmission media.

It includes technologies such as:

- **Ethernet (IEEE 802.3)** — used for wired network connections.
- **Wi-Fi (IEEE 802.11)** — used for wireless network connections.

The Link Layer covers functions such as physical connectivity and data framing.

**OSI correspondence:** The Link Layer combines the functions of the **Physical Layer (Layer 1)** and **Data Link Layer (Layer 2)** of the OSI model.

---

## Layer 2 — Internet Layer

The **Internet Layer** is responsible for logical addressing and routing packets across different networks.

Its main purpose is to enable data to travel from its source network to its intended destination network.

Examples of protocols associated with this layer include:

- **IP (Internet Protocol)** — provides logical addressing and packet delivery between networks.
- **ICMP (Internet Control Message Protocol)** — supports network error reporting and diagnostic messages.
- **IPsec (Internet Protocol Security)** — provides security mechanisms for IP communications.

The Internet Layer uses IP addresses and routing information to support packet forwarding between networks.

**OSI correspondence:** The Internet Layer corresponds to the **Network Layer (Layer 3)** of the OSI model.

---

## Layer 3 — Transport Layer

The **Transport Layer** provides end-to-end communication services between applications running on different devices.

Depending on the protocol used, it can provide reliable and ordered data delivery or connectionless communication with less overhead.

Two important protocols operate at this layer:

- **TCP (Transmission Control Protocol)** — provides reliable, connection-oriented communication with ordered data delivery.
- **UDP (User Datagram Protocol)** — provides connectionless communication with less overhead but does not guarantee delivery or ordering.

**OSI correspondence:** The Transport Layer corresponds to the **Transport Layer (Layer 4)** of the OSI model.

---

## Layer 4 — Application Layer

The **Application Layer** contains protocols that provide specific network communication services to applications.

These protocols enable functions such as web browsing, file transfers, email communication, and remote access.

Examples include:

- **HTTP (Hypertext Transfer Protocol)** — used for web communication.
- **FTP (File Transfer Protocol)** — used for transferring files.
- **SMTP (Simple Mail Transfer Protocol)** — used for sending email.
- **POP3 (Post Office Protocol Version 3)** — used for retrieving email.
- **IMAP (Internet Message Access Protocol)** — used for accessing and managing email.
- **SSH (Secure Shell)** — used for secure remote access.

The Application Layer provides the protocols and services that applications use to exchange data over networks.

**OSI correspondence:** The Application Layer combines the functions of the **Session Layer (Layer 5)**, **Presentation Layer (Layer 6)**, and **Application Layer (Layer 7)** of the OSI model.

---

## Comparison with the OSI Model

The TCP/IP model contains **four layers**, while the OSI model contains **seven layers**.

The TCP/IP model combines several OSI layers into broader categories.

| TCP/IP Layer | Corresponding OSI Layers | Main Function |
|---|---|---|
| **4 — Application** | 7 — Application, 6 — Presentation, 5 — Session | Provides network services to applications |
| **3 — Transport** | 4 — Transport | End-to-end communication between applications |
| **2 — Internet** | 3 — Network | Logical addressing and routing |
| **1 — Link** | 2 — Data Link, 1 — Physical | Local network communication and physical transmission |

### Main Differences

- **Number of layers:** The OSI model has seven layers, while the TCP/IP model has four.
- **Purpose:** The OSI model provides a conceptual framework for understanding network communication, while the TCP/IP model describes the architecture used by the Internet protocol suite.
- **Layer organization:** TCP/IP combines some OSI layers into broader layers.
- **Practical use:** TCP/IP is the foundation of modern Internet communication, while OSI is commonly used to explain and troubleshoot networking concepts.

---
