
# 1. Bits, Bytes, and Binary Information

## 1.1 The Bit

A **bit** (short for **binary digit**) is the basic unit of digital information. It has **two possible values**:

- `0`
- `1`

These two values are abstract symbols representing two distinguishable states.

In physical hardware, binary states may be implemented through electrical charge, voltage levels, magnetic orientation, or other physical properties.

A bit does not inherently mean *true*, *false*, *on*, or *off*. Those meanings depend on the system interpreting it. Multiple bits can be combined to represent larger sets of data.

### Number of Bits and Possible Patterns

| Number of bits | Possible patterns |
|---------------:|------------------:|
| 1 | 2 |
| 2 | 4 |
| 3 | 8 |
| 4 | 16 |
| 8 | 256 |
| 16 | 65,536 |
| 32 | 4,294,967,296 |

The number of possible patterns is always:

$$N = 2^n$$

Where:
- **N** = number of possible patterns
- **n** = number of bits

For example:

$$2^6 = 64$$

Six bits provide **64 distinct patterns**. If interpreted as an unsigned integer, these patterns represent values from **0 to 63**.

Therefore, the maximum unsigned integer representable with `n` bits is:

$$\text{Maximum unsigned value} = 2^n - 1$$

## 1.2 Bytes and Nibbles

A **byte** is a group of **eight bits**.

Example: `10110110`

Eight bits provide:

$$2^8 = 256$$

Therefore, a byte can represent an **unsigned integer from 0 to 255**.

A **nibble** is a group of **four bits**.

Example: `0110`

Four bits provide:

$$2^4 = 16$$

This makes a nibble convenient for representing **one hexadecimal digit**.


## 1.3 Units of Digital Storage

Digital information is measured using units based on **bits and bytes**.

Storage capacities are commonly expressed using either decimal or binary prefixes:

- **Decimal prefixes** use powers of `1000` ($10^3$).
- **Binary prefixes** use powers of `1024` ($2^{10}$).

Although these units are similar, they are **not interchangeable**.

### Decimal vs Binary Units

| Decimal unit | Bytes | Binary unit | Bytes |
|-------------|------:|-------------|------:|
| kB | 1,000 | KiB | 1,024 |
| MB | 1,000,000 | MiB | 1,048,576 |
| GB | 1,000,000,000 | GiB | 1,073,741,824 |
| TB | 1,000,000,000,000 | TiB | 1,099,511,627,776 |

For example:

$$1\text{ MB} = 10^6 = 1,000,000\text{ bytes}$$

$$1\text{ MiB} = 2^{20} = 1,048,576\text{ bytes}$$

This distinction is important when comparing storage devices, memory capacities, and file sizes.

### Bits vs Bytes

The distinction between lowercase `b` and uppercase `B` is important:

- `b` — bit
- `B` — byte
- `Mb` — megabits
- `MB` — megabytes
- `Mbps` — megabits per second
- `MB/s` — megabytes per second

Since one byte contains eight bits:

$$1\text{ B} = 8\text{ bits}$$

For example, converting a network speed of `80 Mbps` into megabytes per second:

$$80 \div 8 = 10$$

Therefore:

$$80\text{ Mbps} = 10\text{ MB/s}$$

This is a **unit conversion**, not a guarantee of actual network throughput. Real transfer speeds may be lower because of protocol overhead, network conditions, and hardware limitations.

---

## 1.4 Bit Positions: MSB and LSB

Each bit in a binary number occupies a particular **position**.

In an unsigned binary integer, each position has a weight corresponding to a power of two.

Consider the eight-bit pattern:

`10110110`

| Bit position | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|-------------|---|---|---|---|---|---|---|---|
| Bit value | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 |
| Weight | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

The weight of each position is calculated using:

$$2^i$$

Where:
- **i** = bit position, starting from `0` on the right.

### Most Significant Bit (MSB)

The **Most Significant Bit (MSB)** is the bit with the greatest positional weight.

In a conventional binary integer representation, it is the **leftmost bit**.

For an eight-bit unsigned integer, its weight is:

$$2^7 = 128$$

### Least Significant Bit (LSB)

The **Least Significant Bit (LSB)** is the bit with the smallest positional weight.

In a conventional binary integer representation, it is the **rightmost bit**.

Its weight is:

$$2^0 = 1$$

### Calculating the Decimal Value

To determine the decimal value of `10110110`, multiply each bit by its corresponding positional weight and add the results:

$$1(128)+0(64)+1(32)+1(16)+0(8)+1(4)+1(2)+0(1)$$

$$=128+32+16+4+2$$

$$=182$$

Therefore:

$$10110110_2 = 182_{10}$$

**Important:** MSB and LSB describe the significance of bits within a representation. They should not be confused with **byte order (endianness)**, which describes how multi-byte values are arranged in memory.

---

## 1.5 Bit Patterns vs Meaning

A **bit pattern** is a sequence of binary digits.

However, a bit pattern does not inherently represent a particular type of information.

Its meaning depends on **how the computer interprets it**.

For example, consider:

`01000001`

This pattern may represent:

- **Unsigned integer:** `65`
- **ASCII character:** `A`
- **Binary file data:** one byte within a file
- **Network data:** part of a protocol field
- **Machine instruction:** part of an instruction encoding

The underlying binary pattern remains the same.

### Signed vs Unsigned Interpretation

Consider another eight-bit pattern:

`11111111`

Depending on its interpretation:

| Representation | Value |
|---------------|------:|
| Unsigned 8-bit integer | 255 |
| Signed 8-bit two's-complement integer | -1 |

The bit pattern is identical, but the represented values are different.

### Why Does This Matter?

Computers do not automatically know whether a particular sequence of bits represents a number, character, instruction, or another type of data.

The interpretation is determined by factors such as:

- Data types
- Character encodings
- File formats
- Instruction-set architectures
- Network protocols
- Software conventions

**Core principle:** A bit pattern receives meaning through its representation format and interpretation.

This principle is fundamental to understanding **programming languages, binary files, memory, networking, and cybersecurity**.

---

# 2. Positional Number Systems

A **number system** defines how numerical values are represented using a set of symbols.

Computers commonly use several positional number systems, especially **binary, octal, decimal, and hexadecimal**.

## 2.1 Radix and Positional Notation

A **positional number system** assigns a value to each digit according to:

1. The digit itself.
2. Its position within the number.
3. The base of the number system.

The **radix**, also called the **base**, determines how many distinct digit symbols are available.

For example:

- Binary has base `2`.
- Octal has base `8`.
- Decimal has base `10`.
- Hexadecimal has base `16`.

In a positional number system, each digit is multiplied by the base raised to the power of its position.

The general formula for a nonnegative integer is:

$$N = \sum_{i=0}^{n} d_i \times b^i$$

Where:
- **N** = numerical value
- **dᵢ** = digit at position `i`
- **b** = base (radix)
- **i** = position, starting from `0` on the right

### Example: Decimal Positional Notation

Consider the decimal number `472`.

$$472 = 4 \times 10^2 + 7 \times 10^1 + 2 \times 10^0$$

$$= 400 + 70 + 2$$

$$= 472$$

Each position represents a different power of ten.

The same principle applies to other positional number systems, but with different bases.

### Common Number Systems

| System | Base | Allowed digits | Example |
|--------|-----:|----------------|---------|
| Binary | 2 | 0–1 | `101101₂` |
| Octal | 8 | 0–7 | `55₈` |
| Decimal | 10 | 0–9 | `45₁₀` |
| Hexadecimal | 16 | 0–9, A–F | `2D₁₆` |

All four examples represent the **same numerical value: 45**.

### Why Multiple Number Systems?

Different number systems are useful in different situations:

- **Binary:** corresponds naturally to the bit patterns used by digital computers.
- **Decimal:** is the standard system used in everyday numerical communication.
- **Octal:** provides a compact representation of binary values and is used in Unix file permissions.
- **Hexadecimal:** provides a particularly convenient and compact representation of binary data.

---

## 2.2 Binary

The **binary number system** is a positional system with base `2`.

It uses only two digits:

- `0`
- `1`

Each position represents a power of two.

| Position | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|----------|---|---|---|---|---|---|---|---|
| Power | 2⁷ | 2⁶ | 2⁵ | 2⁴ | 2³ | 2² | 2¹ | 2⁰ |
| Weight | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

### Example: Binary to Decimal

Consider:

$$110101_2$$

Multiply each digit by the corresponding power of two:

$$1(2^5)+1(2^4)+0(2^3)+1(2^2)+0(2^1)+1(2^0)$$

$$=32+16+0+4+0+1$$

$$=53$$

Therefore:

$$110101_2 = 53_{10}$$

Binary is fundamental to computer science because digital hardware can represent and manipulate binary states using electronic circuits.

---

## 2.3 Octal

The **octal number system** is a positional system with base `8`.

It uses eight digits:

`0 1 2 3 4 5 6 7`

Each position represents a power of eight.

### Example: Octal to Decimal

Consider:

$$157_8$$

Expand the number using positional weights:

$$1(8^2)+5(8^1)+7(8^0)$$

$$=64+40+7$$

$$=111$$

Therefore:

$$157_8 = 111_{10}$$

### Relationship Between Octal and Binary

Because:

$$8=2^3$$

**One octal digit corresponds to exactly three binary bits.**

For example:

| Binary | Octal |
|--------|------:|
| 000 | 0 |
| 001 | 1 |
| 010 | 2 |
| 011 | 3 |
| 100 | 4 |
| 101 | 5 |
| 110 | 6 |
| 111 | 7 |

Consider the binary number:

`001101111`

Divide it into groups of three bits, starting from the right:

```text
Binary:  001 101 111
Octal:     1   5   7
```

Therefore:

$$001101111_2 = 157_8$$

Octal notation is particularly useful when working with **Unix and Linux file permissions**.

---

## 2.4 Hexadecimal

The **hexadecimal number system** is a positional system with base `16`.

It uses sixteen symbols:

`0 1 2 3 4 5 6 7 8 9 A B C D E F`

The letters `A` through `F` represent decimal values from `10` to `15`.

| Hexadecimal digit | Decimal value |
|-------------------|--------------:|
| A | 10 |
| B | 11 |
| C | 12 |
| D | 13 |
| E | 14 |
| F | 15 |

Each position represents a power of sixteen.

### Example: Hexadecimal to Decimal

Consider:

$$2F_{16}$$

Expand the number using positional weights:

$$2(16^1)+15(16^0)$$

$$=32+15$$

$$=47$$

Therefore:

$$2F_{16}=47_{10}$$

### Relationship Between Hexadecimal and Binary

Because:

$$16=2^4$$

**One hexadecimal digit corresponds to exactly four binary bits (one nibble).**

This makes hexadecimal especially useful for representing long binary sequences.

### Binary-to-Hexadecimal Reference Table

| Binary pattern | Hexadecimal |
|----------------|-------------|
| `0000` | `0x0` |
| `0001` | `0x1` |
| `0010` | `0x2` |
| `0011` | `0x3` |
| `0100` | `0x4` |
| `0101` | `0x5` |
| `0110` | `0x6` |
| `0111` | `0x7` |
| `1000` | `0x8` |
| `1001` | `0x9` |
| `1010` | `0xA` |
| `1011` | `0xB` |
| `1100` | `0xC` |
| `1101` | `0xD` |
| `1110` | `0xE` |
| `1111` | `0xF` |

### Example: Binary to Hexadecimal

Consider the eight-bit pattern:

`10110101`

Divide the pattern into groups of four bits:

```text
Binary:       1011 0101
Hexadecimal:     B    5
```

Therefore:

$$10110101_2 = B5_{16}$$

In programming, hexadecimal values are commonly written using the `0x` prefix:

`0xB5`

### Example: A 16-Bit Pattern

Consider the following 16-bit pattern:

`1010010011001000`

Divide it into four-bit groups:

```text
Binary:       1010 0100 1100 1000
Hexadecimal:     A    4    C    8
```

Therefore:

$$1010010011001000_2 = A4C8_{16}$$

Using hexadecimal notation:

`0xA4C8`

This demonstrates how a long binary pattern can be represented much more compactly.

### Why Hexadecimal Matters

Hexadecimal is widely used in:

- **Memory addresses:** representing locations in computer memory.
- **Binary debugging:** inspecting raw bytes and program data.
- **Machine-code inspection:** examining instruction encodings.
- **Network packet analysis:** interpreting packet contents.
- **File signatures:** identifying file formats through characteristic byte sequences.
- **Cryptographic hashes:** displaying hash values compactly.
- **Color values:** representing RGB color components.
- **Low-level programming:** manipulating bit patterns and hardware-related values.

Examples:

```text
0xFF = 255
0x10 = 16
0xA5 = 165
```

The prefix `0x` commonly indicates that a value is written in **hexadecimal notation**.

**Important:** Hexadecimal does not change the underlying value. It only provides a different, more compact way of representing it.

