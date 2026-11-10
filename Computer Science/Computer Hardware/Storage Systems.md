# Storage Systems

## 1. Secondary Storage

Secondary storage has several advantages over main memory, including greater non-volatility, higher storage capacity, lower cost per unit of storage, and, in many cases, the ability to remove the storage medium from a computer for archiving or transferring data to another machine.

The main disadvantages of traditional magnetic and optical storage systems are their moving mechanical components. These components require additional time to write and retrieve data and are more susceptible to mechanical failure.

## 2. Magnetic Storage Systems

One of the most common types of magnetic storage is the **hard disk drive (HDD)**, which uses thin, rotating platters coated with magnetic material.

Read/write heads are positioned above and/or below the platters. As a platter rotates, each head accesses a circular path called a **track**.

By changing the position of the read/write heads, the system can access different concentric tracks.

A **cylinder** is a collection of tracks located at the same radial position across the recording surfaces of the disk platters. When the read/write heads move to a different position, they access a different cylinder.

Each track is divided into smaller sections called **sectors**.

Traditionally, sectors on a disk contain a fixed amount of data. However, this does not mean that every track contains the same amount of data.

In high-capacity storage systems, tracks closer to the outer edge of a platter can contain more sectors, and therefore more bits, than tracks closer to the center. This technique is known as **zone bit recording (ZBR)**.

The storage capacity of a hard disk also depends on the number of platters and the density at which tracks and bits are recorded. Data can be stored on both the upper and lower surfaces of each platter.

### 2.1. Hard Disk Performance Metrics

The following parameters are used to evaluate the performance of a disk storage system:

1. **Seek Time** — The time required to move the read/write heads from one track to another.
2. **Rotational Latency** — The time required for the desired sector to rotate beneath the read/write head after the head has been positioned over the correct track. Average rotational latency is approximately half of a full rotation.
3. **Access Time** — The time required to access requested data. In a simplified HDD model, positioning time is the sum of seek time and rotational latency:

   $$
   \text{Positioning Time} = \text{Seek Time} + \text{Rotational Latency}
   $$

   Depending on the definition used, access time may also include data transfer time and controller overhead.

4. **Transfer Rate** — The speed at which data can be transferred to or from the disk, typically measured in MB/s or GB/s.
5. **Throughput** — The amount of data successfully transferred per unit of time. Unlike a theoretical transfer rate, actual throughput may be affected by overhead, workload characteristics, and other system limitations.
6. **Latency** — The total delay between requesting data and receiving it. Depending on the measurement, this can include seek time, rotational latency, data transfer time, and additional processing or queuing delays.

## 3. Optical Storage Systems

An example of an optical storage system is the **compact disc (CD)**. CDs consist of a reflective layer protected by a transparent coating. Information is represented by microscopic pits and lands that affect reflected light. A laser reads the information by detecting changes in the reflected signal as the disc rotates.

Information on a CD is arranged along a single **spiral track**, running from the center toward the outer edge. The track is divided into sectors. In the standard CD-ROM Mode 1 format, each sector contains **2,048 bytes (2 KiB)** of user data, along with additional information for synchronization and error handling.

Data is stored at approximately uniform linear density along the spiral track, so an outer turn of the spiral contains more data than an inner turn.

CDs are well suited to reading long, continuous sequences of data, but their mechanical seeking makes random access relatively slow.

Traditional CDs typically have capacities of approximately **600–700 MB**.

**DVD (Digital Versatile Disc)** technology can use multiple recording layers, which a precisely focused laser can read separately, allowing capacities of several gigabytes.

**Blu-ray Disc (BD)** uses a blue-violet laser instead of the red laser used by DVDs. Its shorter wavelength allows more precise focusing and higher data density. A standard single-layer Blu-ray Disc stores **25 GB**, more than five times the capacity of a single-layer DVD. Higher-capacity multilayer formats can store **100 GB or more**.

## 4. Flash Memory

In flash memory, bits are stored by applying electrical signals to memory cells. Depending on the technology, electrons are stored on a **floating gate** or in a **charge-trap layer**, changing the electrical characteristics of the cell.

These cells can retain information for long periods without an external power supply.

Repeated program/erase cycles gradually wear out flash memory cells. Flash memory is resistant to physical shocks compared with mechanical magnetic and optical storage devices, which makes it useful in devices such as laptops.

Flash drives can provide capacities of hundreds of gigabytes or more. They are portable and can easily be connected to or disconnected from a computer, making them useful for transferring and storing data.

Larger storage devices based on flash memory include **SSDs (Solid-State Drives)**.

### 4.1. Solid-State Drives (SSDs)

Compared with HDDs, SSDs generally offer greater resistance to vibration and physical shocks, quieter operation because they have no moving parts, and shorter access times.

SSDs generally cost more per gigabyte than HDDs, although prices and capacities vary. They are particularly useful in mobile applications such as laptops. Smartphones also commonly use flash-based storage, although not necessarily an SSD in the conventional drive form factor.

SSDs have limited write endurance. However, **wear leveling** helps reduce uneven wear by distributing writes across different memory cells.

### 4.2. SD Memory Cards

Flash technology is also used in **SD (Secure Digital)** memory cards. They are small, portable storage devices available in standard, miniSD, and microSD form factors.

The SD family includes several capacity standards:

| Standard | Capacity range |
|---|---|
| **SD (Secure Digital)** | Up to 2 GB |
| **SDHC (Secure Digital High Capacity)** | More than 2 GB to 32 GB |
| **SDXC (Secure Digital eXtended Capacity)** | More than 32 GB to 2 TB |

There is also a newer **SDUC (Secure Digital Ultra Capacity)** standard, which extends the specified capacity range beyond SDXC. Actual available products and capacities vary.
