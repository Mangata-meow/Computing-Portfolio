
# Open Systems Interconnection (OSI) Model

The **Open Systems Interconnection (OSI) model** is a conceptual framework that standardizes the functions of a telecommunications or computing system into seven abstract layers.

It provides a structured way to understand how networked devices send, receive, and interpret data.

The OSI model consists of **seven layers**, each responsible for specific networking functions.

---

## Layer 1 — Physical Layer

The **Physical Layer** is responsible for transmitting raw bits over a physical medium.

This layer deals with the physical connections between devices, including the hardware and signals used for network communication.

Examples of components operating at this layer include:

- Ethernet cables
- Hubs
- Repeaters

---

## Layer 2 — Data Link Layer

The **Data Link Layer** provides node-to-node data transfer between devices connected to the same network segment.

It is responsible for organizing data into **frames** and supporting synchronization and error detection during transmission. Some data link technologies also provide error correction.

Devices such as switches operate primarily at this layer, using **Media Access Control (MAC) addresses** to identify network interfaces and forward frames.

The Data Link Layer receives packets from the Network Layer and encapsulates them into frames, adding information such as source and destination MAC addresses.

---

## Layer 3 — Network Layer

The **Network Layer** handles packet forwarding and routing between different networks.

It is responsible for:

- **Logical addressing** — identifying devices using IP addresses.
- **Routing** — determining paths for packets to travel between networks.
- **Packet forwarding** — directing packets toward their destinations.

Routers operate primarily at this layer, using **Internet Protocol (IP) addresses** and routing tables to determine where packets should be forwarded.

Examples of routing protocols include:

- **OSPF (Open Shortest Path First)**
- **RIP (Routing Information Protocol)**

---

## Layer 4 — Transport Layer

The **Transport Layer** provides end-to-end communication services between applications.

Depending on the protocol, its responsibilities can include:

- Data segmentation and reassembly
- Reliable or unreliable data delivery
- Flow control
- Error detection

Two important protocols operate at this layer: **TCP** and **UDP**.

### Transmission Control Protocol (TCP)

**TCP** is a connection-oriented transport protocol designed to provide reliable and ordered data delivery.

Characteristics:

- Ensures reliable data delivery using acknowledgments and retransmissions.
- Establishes a connection between communicating endpoints before transmitting application data.
- Uses flow control to prevent a sender from overwhelming the receiver.
- Delivers data to applications in the correct order.
- Retransmits lost data when necessary.
- Introduces additional overhead compared to UDP because of its reliability and connection-management mechanisms.
- May experience delays when packets are lost because missing data must be retransmitted.

TCP is useful when reliable and ordered data delivery is important.

### User Datagram Protocol (UDP)

**UDP** is a connectionless transport protocol that sends datagrams without establishing a connection beforehand.

Characteristics:

- Has less protocol overhead than TCP.
- Does not guarantee that data will reach its destination.
- Does not guarantee that packets will arrive in the correct order.
- Does not provide built-in retransmission or flow control.
- Allows applications to implement their own reliability or flow-control mechanisms when needed.
- Is flexible and suitable for applications that prioritize low latency.
- Packet loss or unstable connections can negatively affect applications that rely on timely data delivery.

UDP is often preferred when low latency is more important than guaranteed delivery.

---

## Layer 5 — Session Layer

The **Session Layer** manages communication sessions between applications.

It is responsible for establishing, maintaining, and terminating sessions, allowing applications to maintain ongoing communication.

This layer can also support **session synchronization, checkpointing, and recovery**, helping communication resume after interruptions.

Sessions provide a way to organize and manage communication between applications.

---

## Layer 6 — Presentation Layer

The **Presentation Layer** acts as a translator between application data and the format used for communication.

It handles data representation, ensuring that information sent by one system can be correctly interpreted by another.

Its responsibilities include:

- **Data formatting and translation** — converting data into compatible formats.
- **Encryption and decryption** — protecting data by transforming it into an encrypted format and back.
- **Data compression** — reducing the size of transmitted data.

For example, encryption used in secure web communication (HTTPS) performs functions commonly associated with this layer in the OSI model.

---

## Layer 7 — Application Layer

The **Application Layer** provides network services to software applications used by end users.

It serves as the interface between applications and network communication services.

This layer enables functions such as web browsing, file transfers, email communication, and domain name resolution.

Examples of Application Layer protocols include:

- **HTTP (Hypertext Transfer Protocol)** — used for web communication.
- **FTP (File Transfer Protocol)** — used for transferring files.
- **SMTP (Simple Mail Transfer Protocol)** — used for sending email.
- **DNS (Domain Name System)** — used for resolving domain names into IP addresses.

---

## OSI Model Summary

| Layer | Name | Main Function | Example Protocols, Standards, or Technologies |
|---|---|---|---|
| **7** | Application | Provides network services to applications | HTTP, FTP, DNS, POP3, SMTP, IMAP |
| **6** | Presentation | Data encoding, encryption, and compression | Unicode, MIME, JPEG, PNG, MPEG |
| **5** | Session | Establishes, maintains, and synchronizes sessions | RPC, NFS (session-related functions) |
| **4** | Transport | End-to-end communication and data segmentation | TCP, UDP |
| **3** | Network | Logical addressing and routing between networks | IP, ICMP, IPsec |
| **2** | Data Link | Frame transmission between devices on the same network segment | Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11) |
| **1** | Physical | Transmission of raw bits through physical media | Electrical, optical, and radio signals |

**Note:** The OSI model is a conceptual framework. Real-world networking protocols and technologies do not always fit perfectly into a single OSI layer.
