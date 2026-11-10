<h1>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linux/linux-original.svg" alt="Linux" width="40" align="center" />
  System Information and Networking
</h1>

## 1. Operating System Information

```bash
date                 # Current date and time
cal                  # Calendar (if installed)
uname -a             # Kernel, machine, and related information
cat /etc/os-release  # Distribution identification
hostname             # Current hostname
```

`uname -a` mainly reports kernel/system information; `/etc/os-release` identifies the Linux distribution. The original `cat os-release` example only works when the current directory contains such a file.

## 2. User and Process Information

```bash
whoami               # Effective username
id                   # User and group IDs
who                  # Logged-in sessions
ps                   # Process status
env                  # Environment variables
lsof                 # Open files (if installed)
```

## 3. Storage, Memory, and Hardware

```bash
df -h                # Filesystem usage and available space
free -h              # Memory and swap usage
lsblk                # Block devices
lsusb                # USB devices (if installed)
lspci                # PCI devices (if installed)
```

`df` reports filesystem capacity and available space, not just 'empty space on the drive'. `free` reports used and available memory, including buffers/cache information.

## 4. Network Interfaces and Sockets

```bash
ip address           # Show interface addresses
ip route             # Show routing table
ss -tuln             # TCP/UDP listening sockets, numeric addresses/ports
netstat -tuln        # Legacy equivalent, if installed
ifconfig             # Legacy interface information, if installed
```

`ss -tuln` flags:

| Flag | Meaning |
|---|---|
| `-t` | TCP |
| `-u` | UDP |
| `-l` | Listening sockets |
| `-n` | Numeric addresses and ports |

### Hack The Box question

**Question:** How many services are listening on the target system on all interfaces, excluding localhost-only listeners and IPv4-only sockets?

The original notes suggested:

```bash
netstat -tuln | grep 'LISTEN' | grep -v 'tcp6\|127.0.0'
```

**Correction:** That pipeline is not a reliable answer. It removes IPv6 TCP listeners (`tcp6`), although the question explicitly concerns all interfaces and not IPv4-only. It also excludes all lines containing `127.0.0`, and does not correctly account for UDP sockets or binding semantics.

Start by inspecting:

```bash
ss -tuln
```

Then distinguish wildcard bindings (`0.0.0.0` for IPv4 and `[::]` for IPv6) from loopback-only bindings (`127.0.0.1` or `[::1]`). Whether an IPv6 wildcard also accepts IPv4 depends on system and socket settings. Count unique services or sockets according to the lab question, not blindly the number of matching output lines.

## 5. Debian Package Management

`dpkg` is a low-level package management utility on Debian-based Linux distributions.

```bash
dpkg -l              # List package states and installed-package records
```

For repository-aware installation and updates, Debian-based systems commonly use `apt`.
