
## Network Interface Card (NIC) / Network Adapter

A **Network Interface Card (NIC)**, also commonly called a **network adapter**, is a hardware component that allows a computer to connect to a network and communicate with other devices and systems.

NICs are commonly available in two variants:

- **Wired NIC (Ethernet adapter)** — connects a device to a network using an Ethernet cable.
- **Wireless NIC (Wi-Fi adapter)** — connects a device to a wireless network using radio signals.

Network adapters are often integrated into the motherboard but can also be installed separately as expansion cards, typically using PCI Express (PCIe). External adapters can also connect through USB.

A NIC provides the interface between the computer and the network medium, handling the transmission and reception of data.

Each network interface typically has a **Media Access Control (MAC) address**, which is used to identify interfaces and deliver Ethernet frames within a local network.

MAC addresses are generally assigned by manufacturers, but they can also be modified or spoofed.

---

## Router

A **router** is a networking device responsible for forwarding data packets between different networks and directing network traffic toward its destination.

Routers operate primarily at **Layer 3 (Network Layer)** of the OSI model.

They examine the destination IP address of incoming packets and use a **routing table** to determine where the packets should be forwarded.

Routing tables can be populated through:

- **Directly connected routes** — networks attached directly to the router.
- **Static routes** — manually configured by a network administrator.
- **Dynamic routing protocols** — protocols that exchange routing information between routers.

Examples of dynamic routing protocols include:

- **OSPF (Open Shortest Path First)** — commonly used to exchange routing information within an organization or autonomous system.
- **BGP (Border Gateway Protocol)** — commonly used to exchange routing information between autonomous systems, including across the Internet.

Routers allow devices on different networks to communicate and select forwarding paths based on their routing information.

They can also support traffic management through features such as Quality of Service (QoS), which helps prioritize certain types of network traffic.

---

## Switch

A **network switch** connects multiple devices within the same network, most commonly a **Local Area Network (LAN)**.

Traditional Ethernet switches operate primarily at **Layer 2 (Data Link Layer)** of the OSI model.

Switches use **MAC addresses** to determine where Ethernet frames should be forwarded.

They maintain a **MAC address table**, which maps learned MAC addresses to switch ports.

When a switch receives a frame, it examines the destination MAC address:

- If the destination MAC address is known, the switch forwards the frame through the appropriate port.
- If the destination MAC address is unknown, the switch typically floods the frame through other ports in the same VLAN.
- Broadcast frames are generally forwarded to all other ports within the same VLAN.

Unlike hubs, switches do not normally send every frame to every connected device.

This reduces unnecessary traffic and improves network performance.

Some switches, known as **Layer 3 switches**, can also perform routing between networks or VLANs.

---

## Hub

A **network hub** is a basic networking device that connects multiple devices within the same network segment.

Hubs operate at **Layer 1 (Physical Layer)** of the OSI model.

When a hub receives an electrical signal on one port, it repeats that signal to all other connected ports, regardless of the intended destination.

Unlike switches, hubs:

- Do not examine MAC addresses.
- Do not maintain MAC address tables.
- Cannot selectively forward traffic to a specific destination.
- Share bandwidth and a collision domain among connected devices.

Because hubs repeat traffic to all connected ports, they can cause unnecessary network traffic and collisions.

Hubs are much less efficient than switches and are rarely used in modern Ethernet networks.

---
