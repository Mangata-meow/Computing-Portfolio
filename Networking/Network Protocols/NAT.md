
# Network Address Translation (NAT)

**Network Address Translation (NAT)** is a process performed by a router or a similar networking device that modifies the source or destination IP addresses in the headers of IP packets as they pass through the device.

NAT is commonly used to translate the private IP addresses of devices within a local network into a public IP address assigned to the router. This allows multiple devices on a private network to access the Internet using a shared public IP address.

## Types of NAT

There are three commonly discussed types of NAT:

### 1. Static NAT

**Static NAT** involves a one-to-one mapping, where each private IP address corresponds directly to a specific public IP address.

### 2. Dynamic NAT

**Dynamic NAT** assigns a public IP address from a pool of available addresses to a private IP address as needed, depending on network demand.

### 3. Port Address Translation (PAT) / NAT Overload

**Port Address Translation (PAT)**, also known as **NAT Overload**, is the most common form of NAT used in home networks.

It allows multiple devices with different private IP addresses to share a single public IP address by distinguishing connections using port numbers.

This method is widely used in home and small office networks, allowing multiple devices to access the Internet through the same public IP address.

---

## Benefits of NAT

- **IPv4 address conservation** — helps conserve the limited IPv4 address space by allowing multiple devices to share a public IP address.
- **Internal address hiding** — prevents private IP addresses from being directly exposed to external networks, although NAT itself is not a security mechanism.
- **Flexible internal addressing** — allows organizations to manage private IP addressing schemes independently of their public IP addresses.

## Trade-Offs of NAT

- **Additional configuration** — hosting a public server behind NAT may require additional configuration, such as port forwarding.
- **End-to-end connectivity limitations** — NAT can interfere with certain protocols that rely on direct end-to-end communication unless special handling is implemented.
- **More complex troubleshooting** — address translation can make diagnosing network connectivity issues more difficult.
