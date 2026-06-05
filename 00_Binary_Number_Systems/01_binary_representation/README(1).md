# 00 — Binary Number Systems

> **C Mastery Complete** › Module 00  
> *The bedrock of everything. Before C, before pointers, before memory — there is binary.*

---

## Table of Contents

1. [What is Binary?](#1-what-is-binary)
2. [Why Binary? (The Hardware Reason)](#2-why-binary-the-hardware-reason)
3. [Number Systems Compared](#3-number-systems-compared)
4. [Powers of 2 — Your New Best Friend](#4-powers-of-2--your-new-best-friend)
5. [Conversion: Decimal ↔ Binary](#5-conversion-decimal--binary)
6. [Bits, Bytes, and Data Sizes](#6-bits-bytes-and-data-sizes)
7. [Bit Positions — MSB & LSB](#7-bit-positions--msb--lsb)
8. [Hexadecimal — Binary's Shorthand](#8-hexadecimal--binarys-shorthand)
9. [Binary Arithmetic](#9-binary-arithmetic)
10. [How C Uses Binary](#10-how-c-uses-binary)
11. [Common Mistakes](#11-common-mistakes)
12. [Practice Problems](#12-practice-problems)
13. [Resources](#13-resources)
14. [What's Next](#14-whats-next)

---

## 1. What is Binary?

Binary is a **base-2 number system** — it uses only two digits: `0` and `1`. Each digit is called a **bit** (binary digit).

Compare it to the decimal system you already know:

| System | Base | Digits Used | Example |
|--------|------|-------------|---------|
| Decimal | 10 | 0–9 | `253` |
| Binary | 2 | 0–1 | `11111101` |
| Octal | 8 | 0–7 | `375` |
| Hexadecimal | 16 | 0–9, A–F | `FD` |

All four above represent the same value: **253**.

### Quick Reference: 0–15

| Dec | Bin | Dec | Bin |
|-----|-----|-----|-----|
| 0 | `0000` | 8 | `1000` |
| 1 | `0001` | 9 | `1001` |
| 2 | `0010` | 10 | `1010` |
| 3 | `0011` | 11 | `1011` |
| 4 | `0100` | 12 | `1100` |
| 5 | `0101` | 13 | `1101` |
| 6 | `0110` | 14 | `1110` |
| 7 | `0111` | 15 | `1111` |

---

## 2. Why Binary? (The Hardware Reason)

Computers are built from billions of **transistors** — tiny switches that are either **ON** or **OFF**.

```
ON  → voltage present  → 1
OFF → no voltage       → 0
```

Two states is all you need. Why not base-3 or base-10?

- **Noise immunity**: Distinguishing 2 voltage levels is far more reliable than 10.
- **Boolean logic**: `AND`, `OR`, `NOT` map directly to `1`s and `0`s.
- **Circuit simplicity**: Binary arithmetic circuits are simpler and faster to build.
- **Error detection**: Easier to detect corruption when only 2 valid states exist.

> Every image you see, every character you type, every instruction your CPU runs — it's all `1`s and `0`s at the lowest level.

---

## 3. Number Systems Compared

### Positional Notation

Every number system uses **positional notation**: each position carries a weight equal to the base raised to that position's index (counting from 0 on the right).

**Decimal — Base 10:**
```
  2    5    3
  |    |    |
 10²  10¹  10⁰
 100   10    1

= (2×100) + (5×10) + (3×1) = 253
```

**Binary — Base 2:**
```
  1    0    1    1
  |    |    |    |
  2³   2²   2¹   2⁰
  8    4    2    1

= (1×8) + (0×4) + (1×2) + (1×1) = 11
```

The rule is always: **position value = base^position**, starting at position 0 on the right.

---

## 4. Powers of 2 — Your New Best Friend

Memorize at least up to 2¹⁰. You'll use these constantly.

| Power | Value | Common Name |
|-------|-------|-------------|
| 2⁰ | 1 | |
| 2¹ | 2 | |
| 2² | 4 | |
| 2³ | 8 | |
| 2⁴ | 16 | |
| 2⁵ | 32 | |
| 2⁶ | 64 | |
| 2⁷ | 128 | |
| 2⁸ | 256 | |
| 2⁹ | 512 | |
| 2¹⁰ | 1,024 | 1 Kibibit |
| 2¹⁶ | 65,536 | Max value of `unsigned short` |
| 2³² | 4,294,967,296 | Max value of `unsigned int` (32-bit) |
| 2⁶⁴ | 18,446,744,073,709,551,616 | Max value of `unsigned long long` |

---

## 5. Conversion: Decimal ↔ Binary

### Decimal → Binary (Division Method)

Repeatedly divide by 2 and collect remainders. Read from **bottom to top**.

**Example: 43 → binary**

```
43 ÷ 2 = 21  remainder  1   ↑  (LSB — read last, written first bottom-up)
21 ÷ 2 = 10  remainder  1   ↑
10 ÷ 2 =  5  remainder  0   ↑
 5 ÷ 2 =  2  remainder  1   ↑
 2 ÷ 2 =  1  remainder  0   ↑
 1 ÷ 2 =  0  remainder  1   ↑  (MSB — read first)

Result: 101011
```

**Verify:** `32 + 0 + 8 + 0 + 2 + 1 = 43` ✓

---

### Binary → Decimal (Expand by Position)

Write out the positional weights and sum.

**Example: `1101` → decimal**

```
Position:   3    2    1    0
Bit:        1    1    0    1
Weight:     8    4    2    1

= (1×8) + (1×4) + (0×2) + (1×1)
= 8 + 4 + 0 + 1
= 13
```

---

### Shortcut: Subtraction Method (Decimal → Binary)

Find the largest power of 2 that fits, subtract, repeat.

**Example: 100 → binary**

```
100 - 64  = 36   → bit 6 = 1
 36 - 32  =  4   → bit 5 = 1
  4 -  4  =  0   → bit 2 = 1
  
Positions set: 6, 5, 2
Binary: 1100100
```

**Verify:** `64 + 32 + 4 = 100` ✓

---

## 6. Bits, Bytes, and Data Sizes

| Unit | Size | Notes |
|------|------|-------|
| Bit | 1 bit | Smallest unit. `0` or `1`. |
| Nibble | 4 bits | One hex digit. |
| Byte | 8 bits | Stores 0–255. One character in ASCII. |
| Word | 16/32/64 bits | Depends on CPU architecture. |
| Kilobyte (KB) | 1,024 bytes | 2¹⁰ bytes |
| Megabyte (MB) | 1,048,576 bytes | 2²⁰ bytes |
| Gigabyte (GB) | 1,073,741,824 bytes | 2³⁰ bytes |

### C Integer Type Sizes (typical 64-bit system)

| Type | Bytes | Bits | Range |
|------|-------|------|-------|
| `char` | 1 | 8 | -128 to 127 |
| `unsigned char` | 1 | 8 | 0 to 255 |
| `short` | 2 | 16 | -32,768 to 32,767 |
| `unsigned short` | 2 | 16 | 0 to 65,535 |
| `int` | 4 | 32 | -2,147,483,648 to 2,147,483,647 |
| `unsigned int` | 4 | 32 | 0 to 4,294,967,295 |
| `long long` | 8 | 64 | ±9.2 × 10¹⁸ |

> Use `sizeof(type)` in C to check the actual size on your system.

---

## 7. Bit Positions — MSB & LSB

```
Binary number:   1  0  1  1  0  1  0  0
Bit position:    7  6  5  4  3  2  1  0
                 ^                    ^
                MSB                  LSB
           (Most Significant     (Least Significant
              Bit — highest         Bit — lowest
              place value)          place value)
```

**MSB (Most Significant Bit):** Leftmost bit. Highest positional value. In signed integers, it's the **sign bit** (`0` = positive, `1` = negative).

**LSB (Least Significant Bit):** Rightmost bit. Determines if a number is odd (`1`) or even (`0`).

### Why It Matters in C

```c
unsigned char x = 0b10110100;  // = 180

// Check LSB (is it odd?)
if (x & 1) { /* odd */ }

// Check MSB (is bit 7 set?)
if (x & 0x80) { /* MSB is 1 */ }

// Isolate a specific bit
int bit5 = (x >> 5) & 1;  // Extract bit 5
```

---

## 8. Hexadecimal — Binary's Shorthand

Hexadecimal (base-16) exists to make binary readable. Every 4 bits = 1 hex digit.

| Hex | Decimal | Binary |
|-----|---------|--------|
| 0 | 0 | `0000` |
| 1 | 1 | `0001` |
| 2 | 2 | `0010` |
| 3 | 3 | `0011` |
| 4 | 4 | `0100` |
| 5 | 5 | `0101` |
| 6 | 6 | `0110` |
| 7 | 7 | `0111` |
| 8 | 8 | `1000` |
| 9 | 9 | `1001` |
| A | 10 | `1010` |
| B | 11 | `1011` |
| C | 12 | `1100` |
| D | 13 | `1101` |
| E | 14 | `1110` |
| F | 15 | `1111` |

### Binary ↔ Hex Conversion (Group by 4)

```
Binary:  1010  1111  0011
          A      F     3
Hex:    0xAF3
```

```
Hex:    0x2C
         2    C
Binary: 0010 1100
```

In C, hex literals are prefixed with `0x`: `int x = 0xFF;` equals 255.

---

## 9. Binary Arithmetic

### Addition

Rules: `0+0=0`, `0+1=1`, `1+0=1`, `1+1=0` (carry 1)

```
    1 0 1 1   (11)
  + 0 1 1 0   ( 6)
  ---------
  1 0 0 0 1   (17)
  ^
  carry
```

### Subtraction (Two's Complement)

Computers don't subtract — they **negate and add**. Negating in two's complement:
1. Flip all bits (one's complement)
2. Add 1

**Example: Negate 5 (`00000101`) to get -5:**

```
00000101   (5)
11111010   (flip all bits)
11111011   (add 1 → this is -5 in two's complement)
```

**Verify:** `11111011` as signed 8-bit: `-128 + 64 + 32 + 16 + 8 + 0 + 2 + 1 = -5` ✓

This is how `int` in C stores negative numbers.

---

## 10. How C Uses Binary

### Bitwise Operators

These operate directly on the bits of integers — fundamental to systems programming.

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `&` | AND | `0b1100 & 0b1010` | `0b1000` |
| `\|` | OR | `0b1100 \| 0b1010` | `0b1110` |
| `^` | XOR | `0b1100 ^ 0b1010` | `0b0110` |
| `~` | NOT | `~0b00001111` | `0b11110000` |
| `<<` | Left shift | `0b0001 << 3` | `0b1000` (×8) |
| `>>` | Right shift | `0b1000 >> 2` | `0b0010` (÷4) |

### Common Bit Manipulation Patterns

```c
// SET bit n
x = x | (1 << n);

// CLEAR bit n
x = x & ~(1 << n);

// TOGGLE bit n
x = x ^ (1 << n);

// CHECK bit n
int is_set = (x >> n) & 1;

// Check if power of 2 (only one bit set)
int is_power_of_2 = (x != 0) && ((x & (x - 1)) == 0);

// Swap two integers without a temp variable
a ^= b;
b ^= a;
a ^= b;
```

### Literals in C

```c
int decimal = 42;
int octal   = 052;     // prefix 0
int hex     = 0x2A;    // prefix 0x
int binary  = 0b101010; // prefix 0b (C23 / GCC extension)
```

---

## 11. Common Mistakes

**Integer overflow — silent and deadly:**
```c
unsigned char x = 255;
x++;  // x is now 0, NOT 256. Wraps around silently.
```

**Sign extension trap:**
```c
char c = 0xFF;   // -1 as signed char
int  i = c;      // i = -1, NOT 255. Sign bit extended.
```

**Shift undefined behavior:**
```c
int x = 1 << 31;  // Undefined behavior in C! (shifts into sign bit)
unsigned int y = 1u << 31;  // Fine — use unsigned.
```

**Assuming `int` size:**
```c
// Wrong — int size varies by platform:
int x = 2147483648;  // May overflow on 32-bit

// Correct — use stdint.h:
#include <stdint.h>
uint32_t x = 2147483648u;
```

**Confusing `&` (bitwise AND) with `&&` (logical AND):**
```c
if (flags & 0x04)   // Tests if bit 2 is set — correct
if (flags && 0x04)  // Always true if flags != 0 — probably wrong
```

---

## 12. Practice Problems

### Level 1 — Conversion

1. Convert `42` to binary.
2. Convert `0b11001010` to decimal.
3. Convert `0xFF` to binary and decimal.
4. Convert `0b10110111` to hex.

### Level 2 — Bit Manipulation

5. Given `x = 0b10110010`, set bit 0. What is the result?
6. Given `x = 0b11111111`, clear bits 4 and 5. What is the result?
7. What does `x & (x - 1)` do to the binary representation of `x`?
8. How many bits are set in `0b01101101`? (This is "popcount".)

### Level 3 — C Code

9. Write a C function `int count_bits(unsigned int n)` that counts the number of `1` bits.
10. Write a function `void print_binary(unsigned int n)` that prints an integer in binary.
11. Write a function that returns 1 if the nth bit of an integer is set, 0 otherwise.

<details>
<summary>Hints (click to expand)</summary>

- Q7: `x & (x-1)` clears the lowest set bit of `x`.
- Q9: Use a loop, check `n & 1`, then `n >>= 1`.
- Q10: Start from the MSB (bit 31 for 32-bit int) and work down.

</details>

---

## 13. Resources

### Interactive Tools
| Resource | Use For |
|----------|---------|
| [integer.exposed](https://integer.exposed/) | Visual bit-level integer explorer |
| [Cisco Binary Game](https://learningnetwork.cisco.com/s/binary-game) | Speed drilling conversions |
| [baseconvert.com](https://baseconvert.com/) | Verify your manual conversions |
| [Compiler Explorer (godbolt.org)](https://godbolt.org/) | See how C code compiles to machine code |

### Reading
| Resource | Level |
|----------|-------|
| [CS50 Week 0 Notes](https://cs50.harvard.edu/x/notes/0/) | Beginner |
| [Beej's Guide to C](https://beej.us/guide/bgc/) | Beginner–Intermediate |
| *Code* by Charles Petzold | Beginner (book) |
| [Low-Level Programming by Igor Zhirkov](https://nostarch.com/lowlevelprogramming) | Advanced |

### Video
| Resource | What It Covers |
|----------|----------------|
| [Computerphile — Binary](https://www.youtube.com/user/Computerphile) | Short, clear explainers |
| [CS50 Lecture 0](https://www.youtube.com/watch?v=IDDmrzzB14M) | Full lecture on binary & data representation |

---

## 14. What's Next

Now that you understand binary, you're ready for:

```
00_Binary_Number_Systems  ← YOU ARE HERE
01_Data_Types_And_Variables
02_Bitwise_Operators
03_Memory_And_Pointers
04_Integers_And_Overflow
```

Understanding binary deeply makes the following concepts click immediately:
- Why `int` has specific ranges
- How pointers and memory addresses work
- Why bitwise operations are faster than multiplication/division
- How negative numbers are stored (two's complement)
- How floating point works (IEEE 754)

---

<div align="center">

**[⬆ Back to top](#00--binary-number-systems)**

Part of [C Mastery Complete](https://github.com/0xMedl/C-Mastery-Complete) — a ground-up journey through C and systems programming.

</div>
