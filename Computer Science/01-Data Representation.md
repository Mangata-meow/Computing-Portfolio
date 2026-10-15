# 1. Bits, Bytes, and Binary Information

## 1.1 The Bit

A **bit** (binary digit) is the basic unit of digital information. It has two possible values:

- `0`
- `1`

These values are abstract symbols representing two distinguishable states.

In physical hardware, binary states may be implemented through electrical charge, voltage levels, magnetic orientation, or other physical properties.

A bit does not inherently mean *true*, *false*, *on*, or *off*. Those meanings depend on the system interpreting it.

### Why Binary?

Binary systems are particularly suitable for digital hardware because it is practical to distinguish two physical states and build reliable circuits around them.

A single bit represents two possibilities. Multiple bits can be combined to represent larger sets of values.

| **Number of bits** | **Possible patterns** |
| ------------------ | --------------------- |
| 1                  | 2                     |
| 2                  | 4                     |
| 3                  | 8                     |
| 4                  | 16                    |
| 8                  | 256                   |
| 16                 | 65,536                |
| 32                 | 4,294,967,296         |

The number of possible patterns is:

$$N = 2^n$$

where `n` is the number of bits.

For example, six bits can represent:

$$2^6 = 64\text{ distinct patterns}$$

If interpreted as an unsigned integer, these patterns represent values from `0` to `63`.

The maximum unsigned integer is therefore:

$$2^n - 1$$

### Information Capacity

If all `2ⁿ` patterns are available, an `n`-bit sequence can distinguish among `2ⁿ` possibilities.

The number of bits required to represent `N` distinct possibilities using fixed-length binary codes is:

$$\lceil \log_2 N \rceil$$

For example, representing 100 distinct categories requires:

$$\lceil \log_2 100 \rceil = 7\text{ bits}$$

because six bits provide only 64 patterns, while seven bits provide 128.

This does not imply that all patterns must be used.

**Second example:** To represent 200 distinct categories, eight bits are required:

$$\lceil \log_2 200 \rceil = 8\text{ bits}$$

Seven bits provide only 128 patterns, whereas eight bits provide 256. The remaining 56 patterns need not be assigned.

## 1.2 Bytes and Nibbles

A **byte** is a group of eight bits.

A **nibble** is a group of four bits.

Example:

Byte:        10110110

High nibble: 1011

Low nibble:  0110

Eight bits provide:

```
2⁸ = 256 patterns
```

A byte can therefore represent an unsigned integer from `0` to `255`.

A four-bit nibble provides 16 patterns, making it convenient for representing one hexadecimal digit.

## 1.3 Units of Digital Storage

Decimal prefixes use powers of 1000, while binary prefixes use powers of 1024.

| **Decimal unit** | **Bytes**     | **Binary unit** | **Bytes**     |
| ---------------- | ------------- | --------------- | ------------- |
| kB               | 1,000         | KiB             | 1,024         |
| MB               | 1,000,000     | MiB             | 1,048,576     |
| GB               | 1,000,000,000 | GiB             | 1,073,741,824 |
| TB               | 10¹²          | TiB             | 2⁴⁰           |

The distinction between lowercase `b` and uppercase `B` is important:

- `Mb` — megabits
- `MB` — megabytes
- `Mbps` — megabits per second
- `MB/s` — megabytes per second

Since one byte contains eight bits:

```
80 Mbps ÷ 8 = 10 MB/s
```

This is a unit conversion, not a guarantee of actual network throughput.

## 1.4 Bit Positions: MSB and LSB

Consider the eight-bit pattern:

10110110

For an unsigned binary integer, bit positions are weighted by powers of two.

| **Bit position** | **7** | **6** | **5** | **4** | **3** | **2** | **1** | **0** |
| ---------------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| Bit value        | 1     | 0     | 1     | 1     | 0     | 1     | 1     | 0     |
| Weight           | 128   | 64    | 32    | 16    | 8     | 4     | 2     | 1     |

The **Most Significant Bit (MSB)** has the greatest positional weight.

The **Least Significant Bit (LSB)** has the smallest positional weight.

Calculating the value:

```
128 + 32 + 16 + 4 + 2 = 182
```

Therefore:

**10110110₂ = 182₁₀**

### Second Example: Eight-Bit Position Weights

Consider `01001101₂`. Its nonzero positions have weights `64`, `8`, `4`, and `1`:

```text
Bit pattern:  0 1 0 0 1 1 0 1
Weights:    128 64 32 16 8 4 2 1
```

$$64 + 8 + 4 + 1 = 77$$

Therefore, **01001101₂ = 77₁₀**.

The terms MSB and LSB describe significance within a representation. They should not be confused with byte order in memory.

## 1.5 Bit Patterns vs Meaning

A binary pattern does not inherently describe a particular type of information.

For example:

01000001

Depending on its interpretation, it may represent:

- Unsigned integer: `65`
- ASCII character: `A`
- A byte in a file
- A field in a network protocol
- Part of a machine instruction

Similarly:

11111111

can represent:

- `255` as an unsigned 8-bit integer.
- `-1` as an 8-bit two's-complement integer.

The underlying pattern is identical.

**Core principle: A bit pattern receives meaning through its representation format and interpretation.**

This principle is fundamental to understanding binary files, programming types, networking protocols, and machine instructions.

---

# 2. Positional Number Systems

## 2.1 Radix and Positional Notation

A **positional number system** assigns a value to each digit according to its position and the base (radix) of the number system.

For a nonnegative integer with digits `dₙ ... d₁d₀` in base `b`:

$$N = \sum_{i=0}^{n} d_i \times b^i$$

Each digit must be smaller than the base.

For example, in decimal:

```
472 = 4 × 10² + 7 × 10¹ + 2 × 10⁰
= 400 + 70 + 2
```

**Second example:** In decimal, `305` has a zero in the tens position:

```text
305 = 3 × 10² + 0 × 10¹ + 5 × 10⁰
    = 300 + 0 + 5
    = 305
```

### Common Number Systems

| **System**  | **Base** | **Allowed digits** | **Example** |
| ----------- | -------- | ------------------ | ----------- |
| Binary      | 2        | 0–1                | 101101₂     |
| Octal       | 8        | 0–7                | 55₈         |
| Decimal     | 10       | 0–9                | 45₁₀        |
| Hexadecimal | 16       | 0–9, A–F           | 2D₁₆        |

All four examples represent the same integer: 45.

### Why Multiple Bases?

Binary corresponds naturally to bit patterns.

Decimal is convenient for human numerical communication.

Hexadecimal provides a compact representation of binary data.

Octal is historically important and remains useful in areas such as Unix file permissions.

## 2.2 Binary

Binary is a base-2 positional system.

Each position represents a power of two.

```text
Position:  7   6   5   4   3   2   1   0
Weight:  128  64  32  16   8   4   2   1
```

Example:

```
110101₂
```

 = `1×32 + 1×16 + 0×8 + 1×4 + 0×2 + 1×1`

 = `32 + 16 + 4 + 1`

\= **53₁₀**

### Second Example: Binary Positional Weights

Convert `100110₂` into decimal:

```text
100110₂ = 1×32 + 0×16 + 0×8 + 1×4 + 1×2 + 0×1
        = 32 + 4 + 2
        = 38₁₀
```

## 2.3 Octal

Octal is base 8.

Its digits range from `0` to `7`.

Example:

```
157₈
```

 = `1×8² + 5×8¹ + 7×8⁰`

 = `64 + 40 + 7`

\= **111₁₀**

Because `8 = 2³`, one octal digit corresponds to three binary bits.

Example:

```text
Binary: 001 101 111
Octal:    1   5   7
```

Therefore:

```
001101111₂ = 157₈
```

### Second Example: Octal to Decimal

Convert `246₈` into decimal:

```text
246₈ = 2×8² + 4×8¹ + 6×8⁰
     = 128 + 32 + 6
     = 166₁₀
```

Since one octal digit corresponds to three bits, `246₈` can also be written as `010 100 110₂`.

## 2.4 Hexadecimal

Hexadecimal is base 16.

It uses the symbols:

```
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

The letters represent:

| **Hex digit** | **Decimal value** |
| ------------- | ----------------- |
| A             | 10                |
| B             | 11                |
| C             | 12                |
| D             | 13                |
| E             | 14                |
| F             | 15                |

Example:

```
2F₁₆
```

 = `2×16¹ + 15×16⁰`

 = `32 + 15`

\= **47₁₀**

### Second Example: Hexadecimal Positional Weights

Convert `A3₁₆` into decimal (`A = 10`):

```text
A3₁₆ = 10×16¹ + 3×16⁰
     = 160 + 3
     = 163₁₀
```

Because `16 = 2⁴`, each hexadecimal digit corresponds to four binary bits.

```text
Binary:       0010 1111
Hexadecimal:     2    F
```

### Why Hexadecimal Matters

Hexadecimal is widely used in:

- Memory addresses
- Binary debugging
- Machine-code inspection
- Network packet analysis
- File signatures
- Cryptographic hashes
- Color values
- Low-level programming

For example:

```text
0xFF = 255
0x10 = 16
0xA5 = 165
```

The `0x` prefix commonly indicates a hexadecimal literal.

---

# 3. Number-System Conversions

## 3.1 Binary to Decimal

Multiply each binary digit by its corresponding power of two and add the results.

Example:

```
101101₂
```

| **Digit** | **Weight** | **Contribution** |
| --------- | ---------- | ---------------- |
| 1         | 32         | 32               |
| 0         | 16         | 0                |
| 1         | 8          | 8                |
| 1         | 4          | 4                |
| 0         | 2          | 0                |
| 1         | 1          | 1                |

Sum:

```
32 + 8 + 4 + 1 = 45
```

Therefore:

**101101₂ = 45₁₀**

### Example 2: Convert 101001₂ to Decimal

Assign each bit its positional weight:

| **Digit** | **Weight** | **Contribution** |
| --------- | ---------- | ---------------- |
| 1 | 32 | 32 |
| 0 | 16 | 0 |
| 1 | 8 | 8 |
| 0 | 4 | 0 |
| 0 | 2 | 0 |
| 1 | 1 | 1 |

Sum:

```text
32 + 8 + 1 = 41
```

Therefore:

**101001₂ = 41₁₀**

## 3.2 Decimal to Binary: Repeated Division

Repeatedly divide the integer by two, recording each remainder.

Example: convert `45₁₀` to binary.

| **Division** | **Quotient** | **Remainder** |
| ------------ | ------------ | ------------- |
| 45 ÷ 2       | 22           | 1             |
| 22 ÷ 2       | 11           | 0             |
| 11 ÷ 2       | 5            | 1             |
| 5 ÷ 2        | 2            | 1             |
| 2 ÷ 2        | 1            | 0             |
| 1 ÷ 2        | 0            | 1             |

Read the remainders from bottom to top:

**45₁₀ = 101101₂**

### Example 2: Convert 18₁₀ to Binary

| **Division** | **Quotient** | **Remainder** |
| ------------ | ------------ | ------------- |
| 18 ÷ 2 | 9 | 0 |
| 9 ÷ 2 | 4 | 1 |
| 4 ÷ 2 | 2 | 0 |
| 2 ÷ 2 | 1 | 0 |
| 1 ÷ 2 | 0 | 1 |

Reading the remainders from bottom to top gives `10010`.

**18₁₀ = 10010₂**

Verification:

```text
10010₂ = 16 + 2 = 18₁₀
```

The same method works for other integer bases by dividing by the desired base.

## 3.3 Binary to Hexadecimal

Group the bits into sets of four, starting from the right.

Example:

```text
Binary: 1101011011
```

Add leading zeros:

```text
0011 0101 1011
```

Convert each group:

- `0011` → `3`
- `0101` → `5`
- `1011` → `B`

Therefore:

**1101011011₂ = 35B₁₆**

### Why Do We Add Leading Zeros?

A hexadecimal digit corresponds to **exactly four binary bits** because $16 = 2^4$. When grouping a binary integer from **right to left**, the leftmost group may have fewer than four bits.

In the example above, the original binary number has ten bits:

```text
Original:       11 0101 1011
Padded:       0011 0101 1011
```

We add **two zeros on the left only to complete the four-bit group**. These zeros have no effect on the numerical value:

$$11_2 = 0011_2 = 3_{10}$$

More generally, leading zeros do not change the value of a **nonnegative binary integer**. They make the groups easier to read and match to hexadecimal digits. Adding zeros to the **right** would change the integer's value: `101₂ = 5₁₀`, but `1010₂ = 10₁₀`.

This padding rule concerns the numerical value of nonnegative integers. For fixed-width signed representations, the number of bits and the sign-extension rules matter.

### Example 2: Convert 10110101₂ to Hexadecimal

This number already contains eight bits, so no padding is needed:

```text
Binary:       1011 0101
Hexadecimal:     B    5
```

- `1011₂ = 11₁₀`, represented by `B` in hexadecimal.
- `0101₂ = 5₁₀`, represented by `5` in hexadecimal.

Therefore:

**10110101₂ = B5₁₆**

## 3.4 Hexadecimal to Binary

Replace each hexadecimal digit with its four-bit equivalent.

Example:

```
A7₁₆
```

- `A` → `1010`
- `7` → `0111`

Therefore:

**A7₁₆ = 10100111₂**

The digit `7` is written as `0111` (rather than `111`) so that **each hexadecimal digit maps to a full four-bit group**. The added zero does not change the value: `0111₂ = 111₂ = 7₁₀`.

### Example 2: Convert 3F2₁₆ to Binary

Replace each hexadecimal digit with four bits:

| **Hex digit** | **Four-bit binary** |
| ------------- | ------------------- |
| 3 | `0011` |
| F | `1111` |
| 2 | `0010` |

```text
Hexadecimal:     3    F    2
Binary:       0011 1111 0010
```

Therefore:

**3F2₁₆ = 001111110010₂**

The first two zeros can be omitted when expressing the value as a nonnegative integer: `1111110010₂` has the same numerical value. They are retained here to show the one-to-four digit correspondence.

## 3.5 Decimal to Hexadecimal

Use repeated division by 16.

Example: convert `254₁₀`.

```text
254 ÷ 16 = 15 remainder 14
 15 ÷ 16 =  0 remainder 15
```

Convert the remainders:

- 14 → E
- 15 → F

Read from bottom to top:

**254₁₀ = FE₁₆**

Verification:

```
15×16 + 14 = 254
```

### Example 2: Convert 1000₁₀ to Hexadecimal

Repeatedly divide by 16:

| **Division** | **Quotient** | **Remainder** |
| ------------ | ------------ | ------------- |
| 1000 ÷ 16 | 62 | 8 |
| 62 ÷ 16 | 3 | 14 |
| 3 ÷ 16 | 0 | 3 |

Convert the remainders: `8 → 8`, `14 → E`, `3 → 3`.

Read them **from bottom to top**:

**1000₁₀ = 3E8₁₆**

Verification:

```text
3×16² + 14×16 + 8
= 768 + 224 + 8
= 1000
```
