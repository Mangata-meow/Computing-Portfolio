
# Dynamic Host Configuration Protocol (DHCP)

## 1. What Is DHCP?

**Dynamic Host Configuration Protocol (DHCP)** is a network management protocol that automates the process of configuring devices on IP networks.

It allows devices to automatically obtain an **IP address** and other network configuration parameters, such as:

- **Subnet mask** — identifies which part of an IP address represents the network.
- **Default gateway** — the router used to communicate with devices outside the local network.
- **DNS servers** — translate domain names into IP addresses.
- **Lease duration** — determines how long a device can use its assigned IP address.

DHCP simplifies network administration by eliminating the need to manually configure IP addresses on every device.

It also helps prevent IP address conflicts by managing address allocation from a defined pool of available addresses.

However, DHCP cannot guarantee that conflicts will never occur, especially when devices use manually configured IP addresses.

---

## 2. DHCP Server and DHCP Client

### DHCP Server

A **DHCP server** is a device or software service responsible for managing IP address allocation and distributing network configuration parameters.

A DHCP server can run on:

- A router
- A dedicated server
- Another device providing DHCP services

The DHCP server maintains a **pool of available IP addresses**, also called a DHCP scope, and assigns addresses to clients.

It also manages address leases and tracks which addresses have been allocated.

### DHCP Client

A **DHCP client** is any device that requests network configuration parameters from a DHCP server.

Examples include:

- Computers and laptops
- Smartphones
- Printers
- Smart TVs
- Other network-connected devices

When a DHCP-enabled device connects to a network, it can request an IP address and other necessary configuration information automatically.

---

## 3. DHCP DORA Process

The initial DHCP address allocation process in IPv4 is commonly known as **DORA**.

DORA stands for:

1. **Discover**
2. **Offer**
3. **Request**
4. **Acknowledge**

### Step 1: Discover (DHCPDISCOVER)

When a DHCP client connects to a network and needs an IP address, it sends a **DHCP Discover** message.

This message is typically broadcast because the client does not yet know the address of a DHCP server.

The purpose is to discover available DHCP servers on the network.

### Step 2: Offer (DHCPOFFER)

A DHCP server receives the Discover message and responds with a **DHCP Offer**.

The Offer proposes an available IP address and other network configuration parameters.

Multiple DHCP servers may respond with different offers.

### Step 3: Request (DHCPREQUEST)

The DHCP client receives the Offer and sends a **DHCP Request** message.

This indicates which offered IP address and DHCP server the client has selected.

During the initial allocation process, this message is typically broadcast so that other DHCP servers know their offers were not selected.

### Step 4: Acknowledge (DHCPACK)

The selected DHCP server responds with a **DHCP Acknowledge** message.

This confirms the IP address lease and provides the final network configuration parameters.

The client can then configure its network interface and begin communicating using the assigned IP address.

### DORA Process Summary

| Step | Message | Sender | Purpose |
|---|---|---|---|
| 1 | DHCPDISCOVER | Client | Searches for available DHCP servers |
| 2 | DHCPOFFER | Server | Offers an IP address and configuration |
| 3 | DHCPREQUEST | Client | Requests the selected address |
| 4 | DHCPACK | Server | Confirms the address lease |

**Simplified communication flow:**

```text
DHCP Client                         DHCP Server
     |                                   |
     | -------- DHCPDISCOVER ----------> |
     |                                   |
     | <--------- DHCPOFFER ------------ |
     |                                   |
     | -------- DHCPREQUEST -----------> |
     |                                   |
     | <---------- DHCPACK ------------- |
     |                                   |
     |       IP address configured       |
```

---

## 4. DHCP Lease and Renewal

**Important:** An IP address assigned dynamically by DHCP is not necessarily permanent.

It is usually assigned for a specific period called the **lease time**.

The DHCP client can use the assigned IP address during the valid lease period.

To continue using the address, the client must renew its lease before it expires.

### DHCP Lease Renewal

DHCP clients typically attempt to renew their leases automatically.

The renewal process usually involves two important timers:

- **T1 (Renewal Time)** — typically 50% of the lease duration. The client attempts to renew its lease with the DHCP server that originally assigned the address.
- **T2 (Rebinding Time)** — typically 87.5% of the lease duration. If renewal has not succeeded, the client attempts to contact any available DHCP server.

These are common default values and can be configured differently.

### Example: 24-Hour Lease

Suppose a DHCP server assigns an IP address with a lease duration of 24 hours.

| Time | Event |
|---|---|
| 0 hours | The client receives its IP address |
| 12 hours (T1) | The client typically attempts to renew its lease |
| 21 hours (T2) | If renewal failed, the client typically attempts rebinding |
| 24 hours | If the lease has not been renewed, it expires |

If the lease expires without renewal, the client must stop using that leased IP address.

A successful renewal extends the lease, often allowing the device to continue using the same IP address.

---

## 5. DHCP Technical Information

| Property | Description |
|---|---|
| Full name | Dynamic Host Configuration Protocol |
| Purpose | Automatic IP configuration |
| OSI layer | Application Layer (Layer 7) |
| Transport protocol | UDP |
| DHCP server port | UDP 67 |
| DHCP client port | UDP 68 |
| IPv4 allocation process | DORA |
| Address allocation | Typically lease-based |

**Note:** These ports and the DORA process describe DHCP for IPv4. DHCPv6 uses different ports and message exchanges.

