
# <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" width="25"/> Linux File System Hierarchy

Linux uses a tree-like filesystem hierarchy. The Filesystem Hierarchy Standard (FHS) defines the purpose and location of many standard directories, although implementations may vary between Linux distributions.

All files and directories are organized under a single root directory: `/`.

---

## Overview of the Structure

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── sys
├── tmp
├── usr
└── var
```

**Note:** On many modern Linux distributions, `/bin`, `/sbin`, and `/lib` are symbolic links to corresponding directories under `/usr`.

---

## Most Important Directories

### `/` - Root Directory

The top-level directory that contains all other files and directories in the filesystem hierarchy.

### `/bin` - Essential Command Binaries

Contains essential command binaries used for basic system operation.

**Examples:**
- `ls` - lists directory contents
- `cp` - copies files and directories
- `cat` - displays or concatenates file content

On many modern distributions, `/bin` is a symbolic link to `/usr/bin`.

### `/boot` - Boot Files

Contains files required to boot the operating system, such as the Linux kernel and bootloader-related files.

### `/dev` - Device Files

Contains special files that provide interfaces to hardware and virtual devices.

**Examples:**
- `/dev/sda` - a disk device, commonly using SATA or similar storage interfaces
- `/dev/nvme0n1` - an NVMe storage device

### `/etc` - System Configuration

Contains host-specific system configuration files.

**Examples:**
- `/etc/passwd` - user account information
- `/etc/hosts` - static hostname-to-IP-address mappings

### `/home` - User Home Directories

Contains home directories for regular users, where personal files and user-specific settings are typically stored.

**Example:**

```bash
/home/julia
```

### `/lib` - Essential Shared Libraries

Traditionally contains shared libraries required by essential programs and for system startup.

On many modern distributions, `/lib` is a symbolic link to `/usr/lib`.

### `/media` - Removable Media

Provides mount points for removable storage devices, such as USB drives and optical discs.

### `/mnt` - Temporary Mount Points

Traditionally used for temporarily mounting filesystems.

### `/opt` - Optional Software

Contains optional software packages, often including third-party applications.

### `/proc` - Process and Kernel Information

A virtual filesystem that exposes information about running processes and the Linux kernel.

**Examples:**
- `/proc/cpuinfo` - information about the processor
- `/proc/meminfo` - information about system memory

### `/root` - Root User's Home Directory

The home directory of the root (administrator) user.

### `/run` - Runtime Data

Contains runtime information generated since the system was started, such as process identifiers and service state information.

### `/sbin` - System Administration Binaries

Traditionally contains binaries used for system administration.

**Examples:**
- `iptables` - manages firewall rules where supported
- `reboot` - restarts the system

On many modern distributions, `/sbin` is a symbolic link to `/usr/sbin`.

### `/sys` - System and Device Information

A virtual filesystem that exposes information about hardware devices, drivers, and kernel subsystems.

### `/tmp` - Temporary Files

Contains temporary files created by the operating system and applications.

Files may be automatically removed during startup or through periodic cleanup, depending on the system configuration.

**Example:**

```bash
# Check temporary files
ls /tmp
```

### `/usr` - Applications and Shared Resources

Contains many system applications, libraries, documentation, and shared resources.

**Examples:**
- `/usr/bin` - user commands and applications
- `/usr/lib` - libraries
- `/usr/share/man` - manual pages

### `/var` - Variable Data

Contains files whose contents change during normal system operation, such as:

- Logs
- Mail data
- Application data
- Caches

**Example:**

```bash
# Navigate to system logs
cd /var/log
```


