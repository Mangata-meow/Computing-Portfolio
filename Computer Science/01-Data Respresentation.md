
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
