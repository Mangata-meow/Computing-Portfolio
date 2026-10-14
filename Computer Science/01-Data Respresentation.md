
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

$$N = \sum_{i=0}^{n-1} d_i \times b^i$$

Where:

- **N** = numerical value
- **dᵢ** = digit at position `i`
- **b** = base (radix)
- **i** = position, starting from `0` on the right
- **n** = total number of digits

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

The table shows **individual hexadecimal digits**. The `0x` prefix is used when writing a hexadecimal number in many programming languages, not when naming each digit.

| Binary pattern | Hexadecimal |
|----------------|-------------|
| `0000` | `0` |
| `0001` | `1` |
| `0010` | `2` |
| `0011` | `3` |
| `0100` | `4` |
| `0101` | `5` |
| `0110` | `6` |
| `0111` | `7` |
| `1000` | `8` |
| `1001` | `9` |
| `1010` | `A` |
| `1011` | `B` |
| `1100` | `C` |
| `1101` | `D` |
| `1110` | `E` |
| `1111` | `F` |

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

---

# 3. Number-System Conversions

Number-system conversion is the process of expressing the **same numerical value in a different base**.

For example, the decimal number `45` can be represented as:

- **Binary:** `101101₂`
- **Octal:** `55₈`
- **Decimal:** `45₁₀`
- **Hexadecimal:** `2D₁₆`

Although their representations differ, their numerical value remains the same.


## 3.1 Binary to Decimal

To convert a binary number into decimal, **multiply each binary digit by its corresponding power of two and add the results**.

The general formula is:

$$N = \sum_{i=0}^{n-1} b_i \times 2^i$$

Where:

- **N** = decimal value
- **bᵢ** = binary digit at position `i`
- **i** = bit position, starting from `0` on the right
- **n** = total number of bits

### Example 1: Convert 101101₂ to Decimal

Consider the binary number:

$$101101_2$$

Assign each digit its corresponding positional weight:

| Bit position | Binary digit | Weight | Contribution |
|-------------:|-------------:|-------:|-------------:|
| 5 | 1 | 32 | 32 |
| 4 | 0 | 16 | 0 |
| 3 | 1 | 8 | 8 |
| 2 | 1 | 4 | 4 |
| 1 | 0 | 2 | 0 |
| 0 | 1 | 1 | 1 |

Multiply each digit by its corresponding power of two:

$$1(2^5)+0(2^4)+1(2^3)+1(2^2)+0(2^1)+1(2^0)$$

$$=32+0+8+4+0+1$$

$$=45$$

Therefore:

$$101101_2 = 45_{10}$$

### Example 2: Convert 101001₂ to Decimal

Consider the binary number:

$$101001_2$$

Assign each digit its corresponding positional weight:

| Bit position | Binary digit | Weight | Contribution |
|-------------:|-------------:|-------:|-------------:|
| 5 | 1 | 32 | 32 |
| 4 | 0 | 16 | 0 |
| 3 | 1 | 8 | 8 |
| 2 | 0 | 4 | 0 |
| 1 | 0 | 2 | 0 |
| 0 | 1 | 1 | 1 |

Multiply each digit by its corresponding power of two:

$$1(2^5)+0(2^4)+1(2^3)+0(2^2)+0(2^1)+1(2^0)$$

$$=32+0+8+0+0+1$$

$$=41$$

Therefore:

$$101001_2 = 41_{10}$$

**Important:** Each binary position represents a power of two. Only positions containing `1` contribute to the final sum.


## 3.2 Decimal to Binary: Repeated Division

To convert a decimal integer into binary, **repeatedly divide the number by two and record the remainder of each division**.

The remainder will always be either:

- `0` — when the number is even.
- `1` — when the number is odd.

Continue dividing the integer quotient until it becomes `0`. For the special case of decimal `0`, the binary representation is simply `0`.

The binary representation is obtained by **reading the remainders from bottom to top**.

### Example 1: Convert 45₁₀ to Binary

Consider the decimal number:

$$45_{10}$$

Repeatedly divide by two:

| Division | Quotient | Remainder |
|----------|---------:|----------:|
| 45 ÷ 2 | 22 | 1 |
| 22 ÷ 2 | 11 | 0 |
| 11 ÷ 2 | 5 | 1 |
| 5 ÷ 2 | 2 | 1 |
| 2 ÷ 2 | 1 | 0 |
| 1 ÷ 2 | 0 | 1 |

Read the remainders **from bottom to top**:

`101101`

Therefore:

$$45_{10} = 101101_2$$

### Example 2: Convert 18₁₀ to Binary

Consider the decimal number:

$$18_{10}$$

Repeatedly divide by two:

| Division | Quotient | Remainder |
|----------|---------:|----------:|
| 18 ÷ 2 | 9 | 0 |
| 9 ÷ 2 | 4 | 1 |
| 4 ÷ 2 | 2 | 0 |
| 2 ÷ 2 | 1 | 0 |
| 1 ÷ 2 | 0 | 1 |

Read the remainders **from bottom to top**:

`10010`

Therefore:

$$18_{10} = 10010_2$$

### Verification

To verify the result, convert the binary representation back into decimal:

$$10010_2 = 1(2^4)+0(2^3)+0(2^2)+1(2^1)+0(2^0)$$

$$=16+0+0+2+0$$

$$=18$$

The conversion is correct.

### General Rule

Repeated division can be used to convert a nonnegative decimal integer into any positional number system.

Instead of always dividing by two, divide by the **base of the target number system**:

- **Binary:** divide by `2`.
- **Octal:** divide by `8`.
- **Hexadecimal:** divide by `16`.

For hexadecimal, remainders from `10` to `15` are represented by the letters `A` through `F`.

**Important:** The remainders must be read from bottom to top because the first remainder represents the least significant digit, while the last represents the most significant digit.


## 3.3 Binary to Hexadecimal

To convert a binary number into hexadecimal, **divide the binary digits into groups of four bits, starting from the right, and convert each group into its corresponding hexadecimal digit**.

This works because hexadecimal uses base `16`, and:

$$16 = 2^4$$

Therefore, **one hexadecimal digit corresponds to exactly four binary bits (one nibble)**.

### Example 1: Convert 1101011011₂ to Hexadecimal

Consider the binary number:

$$1101011011_2$$

**Step 1 — Divide the binary number into groups of four, starting from the right.**

```text
11 | 0101 | 1011
```

Notice that the leftmost group contains only **two bits**, while the other groups contain four.

**Step 2 — Add leading zeros to complete the leftmost group.**

```text
0011 | 0101 | 1011
```

We added two zeros **to the beginning of the binary number**, so that every group contains exactly four bits.

**Important:** Leading zeros are added only to make the groups easier to convert. They do not change the numerical value of a nonnegative binary integer.

For example:

$$11_2 = 0011_2 = 3_{10}$$

Both binary representations have exactly the same value.

**Step 3 — Convert each four-bit group into hexadecimal.**

| Binary group | Decimal value | Hexadecimal digit |
|--------------|--------------:|-------------------|
| `0011` | 3 | 3 |
| `0101` | 5 | 5 |
| `1011` | 11 | B |

**Step 4 — Combine the hexadecimal digits in their original order.**

```text
Binary:       0011 0101 1011
Hexadecimal:     3    5    B
```

Therefore:

$$1101011011_2 = 35B_{16}$$

### Example 2: Convert 10110101₂ to Hexadecimal

Consider the binary number:

$$10110101_2$$

**Step 1 — Divide the binary number into groups of four.**

```text
1011 | 0101
```

Both groups already contain four bits, so **no leading zeros are necessary**.

**Step 2 — Convert each group into hexadecimal.**

| Binary group | Decimal value | Hexadecimal digit |
|--------------|--------------:|-------------------|
| `1011` | 11 | B |
| `0101` | 5 | 5 |

**Step 3 — Combine the hexadecimal digits.**

```text
Binary:       1011 0101
Hexadecimal:     B    5
```

Therefore:

$$10110101_2 = B5_{16}$$

### Why Do We Add Leading Zeros?

A binary number does not always contain a number of bits divisible by four.

For example:

`1011011`

This number contains seven bits. To divide it into complete four-bit groups, we add one zero to the beginning:

```text
Original:  1011011
Padded:   01011011

Groups:   0101 1011
```

The additional zero contributes nothing to the numerical value.

$$1011011_2 = 01011011_2$$

Both represent decimal `91`.

**We add leading zeros only for grouping and readability, not to change the number.**

Adding zeros to the **right**, however, would change the value of a binary integer:

$$101_2 = 5_{10}$$

$$1010_2 = 10_{10}$$

### Important Rules

- Always group binary integer digits **from right to left**.
- Each hexadecimal digit corresponds to **four binary bits**.
- Add leading zeros only when the leftmost group contains fewer than four bits.
- Leading zeros do not change the numerical value of a nonnegative binary integer. In fixed-width formats, however, the number of stored bits can matter.
- Convert each four-bit group separately.
- Combine the hexadecimal digits in their original order.
- If the number of bits is already divisible by four, no additional zeros are needed.


## 3.4 Hexadecimal to Binary

To convert a hexadecimal number into binary, **replace each hexadecimal digit with its corresponding four-bit binary representation**.

This is the reverse of binary-to-hexadecimal conversion.

Because:

$$16 = 2^4$$

Each hexadecimal digit corresponds to exactly four binary bits.

### Example 1: Convert A7₁₆ to Binary

Consider the hexadecimal number:

$$A7_{16}$$

**Step 1 — Identify each hexadecimal digit.**

The number contains two digits:

- `A`
- `7`

**Step 2 — Convert each digit into its four-bit binary equivalent.**

In hexadecimal, `A` represents decimal `10`.

$$10_{10} = 1010_2$$

Therefore:

`A → 1010`

The hexadecimal digit `7` represents decimal `7`.

$$7_{10} = 0111_2$$

Therefore:

`7 → 0111`

Notice that `7` is written as `0111`, rather than `111`, because **each hexadecimal digit must be represented by exactly four binary bits**.

The leading zero does not change the value:

$$111_2 = 0111_2 = 7_{10}$$

It is included to preserve the four-bit representation of the hexadecimal digit.

**Step 3 — Combine the binary groups in their original order.**

```text
Hexadecimal:     A    7
Binary:       1010 0111
```

Therefore:

$$A7_{16} = 10100111_2$$

### Example 2: Convert 3F2₁₆ to Binary

Consider the hexadecimal number:

$$3F2_{16}$$

**Step 1 — Identify the hexadecimal digits.**

- `3`
- `F`
- `2`

**Step 2 — Convert each digit into four binary bits.**

| Hexadecimal digit | Decimal value | Four-bit binary |
|-------------------|--------------:|-----------------|
| 3 | 3 | `0011` |
| F | 15 | `1111` |
| 2 | 2 | `0010` |

**Step 3 — Combine the binary groups.**

```text
Hexadecimal:     3    F    2
Binary:       0011 1111 0010
```

Therefore:

$$3F2_{16} = 001111110010_2$$

The leading zeros may be omitted when writing the number as a nonnegative binary integer:

$$3F2_{16} = 1111110010_2$$

Both binary representations have the same numerical value.

### Why Are Four Bits Always Used?

A hexadecimal digit can represent sixteen possible values:

$$0,1,2,\ldots,15$$

Four bits also provide sixteen possible patterns:

$$2^4 = 16$$

For example:

| Hexadecimal | Binary |
|-------------|--------|
| `1` | `0001` |
| `5` | `0101` |
| `A` | `1010` |
| `F` | `1111` |

Even if a hexadecimal digit could be represented using fewer binary digits, we write it using **four bits to preserve the correspondence between hexadecimal digits and binary groups**.

### Important Rules

- Convert each hexadecimal digit independently.
- Always write **four binary bits for each hexadecimal digit**.
- Add leading zeros within a group when necessary.
- Combine the binary groups in their original order.
- Leading zeros do not change the numerical value of a nonnegative integer, although bit width may matter in fixed-width representations.
- The conversion does not require repeated division or multiplication.

**Remember:** Binary-to-hexadecimal conversion involves grouping bits into fours, while hexadecimal-to-binary conversion involves replacing each hexadecimal digit with four bits.

## 3.5 Decimal to Hexadecimal

To convert a decimal integer into hexadecimal, **repeatedly divide the number by 16 and record the remainder of each division**.

This method is similar to converting decimal into binary, but instead of dividing by `2`, we divide by `16` because hexadecimal is a **base-16 number system**.

Hexadecimal uses sixteen digits:

- `0–9` represent decimal values from `0` to `9`.
- `A–F` represent decimal values from `10` to `15`.

### Conversion Procedure

1. Divide the decimal number by `16`.
2. Record the integer quotient and remainder.
3. Divide the quotient by `16` again.
4. Continue until the quotient becomes `0`. (For decimal `0`, the hexadecimal representation is simply `0`.)
5. Convert remainders from `10` to `15` into hexadecimal letters (`A–F`).
6. Read the remainders **from bottom to top** to obtain the hexadecimal representation.

### Example 1: Convert 254₁₀ to Hexadecimal

Consider the decimal number:

$$254_{10}$$

**Step 1 — Repeatedly divide the number by 16.**

| Division | Quotient | Remainder |
|----------|---------:|----------:|
| 254 ÷ 16 | 15 | 14 |
| 15 ÷ 16 | 0 | 15 |

The first division gives:

$$254 = 15 \times 16 + 14$$

The second division gives:

$$15 = 0 \times 16 + 15$$

**Step 2 — Convert the remainders into hexadecimal digits.**

| Decimal remainder | Hexadecimal digit |
|------------------:|-------------------|
| 14 | E |
| 15 | F |

**Step 3 — Read the remainders from bottom to top.**

```text
Division        Remainder

254 ÷ 16 = 15      14 → E
 15 ÷ 16 =  0      15 → F
                       ↑
               Read bottom to top
```

The last remainder is `F`, followed by `E`.

Therefore:

$$254_{10} = FE_{16}$$

Using the hexadecimal prefix:

`0xFE`

### Verification

To verify the result, convert the hexadecimal number back into decimal using positional notation.

Each hexadecimal digit is multiplied by its corresponding power of `16`, starting from position `0` on the right.

For `FE₁₆`:

- `F = 15`, at position `1`.
- `E = 14`, at position `0`.

Therefore:

$$FE_{16} = 15 \times 16^1 + 14 \times 16^0$$

$$=15 \times 16 + 14 \times 1$$

$$=240+14$$

$$=254$$

The conversion is correct:

$$254_{10} = FE_{16}$$

### Example 2: Convert 1000₁₀ to Hexadecimal

Consider the decimal number:

$$1000_{10}$$

**Step 1 — Repeatedly divide by 16.**

| Division | Quotient | Remainder |
|----------|---------:|----------:|
| 1000 ÷ 16 | 62 | 8 |
| 62 ÷ 16 | 3 | 14 |
| 3 ÷ 16 | 0 | 3 |

**Step 2 — Convert the remainders into hexadecimal digits.**

```text
8  → 8
14 → E
3  → 3
```

**Step 3 — Read the remainders from bottom to top.**

```text
Bottom → Top: 3 E 8
```

Therefore:

$$1000_{10} = 3E8_{16}$$

### Verification

$$3E8_{16} = 3 \times 16^2 + 14 \times 16^1 + 8 \times 16^0$$

$$=3 \times 256 + 14 \times 16 + 8 \times 1$$

$$=768+224+8$$

$$=1000$$

The conversion is correct.

### Why Do We Read the Remainders from Bottom to Top?

When dividing by `16`, the first remainder represents the **least significant hexadecimal digit** (the rightmost digit).

Each subsequent division determines the next digit to the left.

For example, when converting `254₁₀`:

- The first remainder, `14` (`E`), represents the units position ($16^0$).
- The second remainder, `15` (`F`), represents the sixteens position ($16^1$).

Therefore, the digits must be written in reverse order of discovery:

`F E`

### Important Rules

- Divide by `16` because hexadecimal uses base `16`.
- Record the **integer quotient** and remainder at each step.
- Continue until the quotient becomes `0`.
- Convert remainders from `10` to `15` into letters `A–F`.
- Read the remainders **from bottom to top**.
- Verify the result by converting the hexadecimal number back into decimal.

**Remember:** Decimal-to-hexadecimal conversion uses repeated division by `16`, while hexadecimal-to-decimal conversion uses positional weights that are powers of `16`.
