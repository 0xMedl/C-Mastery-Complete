# 01 — Bits, Bytes & Nibbles

> **C Mastery Complete** › Module 01
> *Before numbers, before hex, before memory — everything starts with bits.*

---

## The idea in one sentence

A computer doesn’t see numbers, letters, or images.

It only sees **bits**:

```text
0 and 1
```

Everything else is just a way of grouping and interpreting those bits.

---

## 1. Bit — the smallest unit

A **bit** is a single binary digit.

It can only be:

```text
0 or 1
```

That’s it.

One bit alone is not very useful, but combine many bits and you can represent anything.

---

## 2. Byte — the real working unit

A **byte = 8 bits**

```text
1 byte = 8 bits
```

Example:

```text
10101100
```

A byte is important because it is the smallest addressable unit in most computers.

That means:

* Memory is organized in bytes
* Each character is usually 1 byte
* Most basic data types are measured in bytes

---

### What a byte can represent

With 8 bits:

```text
2^8 = 256 values
```

So a byte can store:

```text
0 → 255   (unsigned)
-128 → 127 (signed, two's complement)
```

---

## 3. Nibble — the half-byte

A **nibble = 4 bits**

```text
1 nibble = 4 bits
```

Example:

```text
1010
```

Why does this matter?

Because:

```text
4 bits = 1 hexadecimal digit
```

So:

| Bits | Hex |
| ---- | --- |
| 0000 | 0   |
| 1111 | F   |

This is the reason hexadecimal exists — it maps perfectly to binary.

---

## 4. Why these groupings exist

Computers don’t *need* bytes or nibbles.

We created them because:

### Bit level is too small

You can’t store useful data in 1 bit.

### Byte level is practical

* 1 byte = 1 character (ASCII)
* 1 byte = smallest usable memory unit

### Nibble level is convenient

* 4 bits = 1 hex digit
* Makes binary readable

---

## 5. Visual hierarchy

```text
1 bit      → 0 or 1
4 bits     → 1 nibble
8 bits     → 1 byte
16 bits    → 2 bytes
32 bits    → 4 bytes
64 bits    → 8 bytes
```

---

## 6. Memory reality

When you store something in memory:

```text
char c = 'A';
```

What actually happens:

```text
01000001
```

That is:

* 1 byte
* ASCII value of 'A'
* Stored as bits

---

## 7. Why 8 bits became standard

There is nothing magical about 8.

But it became standard because:

* Early hardware designs converged on 8-bit architecture
* It is enough to represent 256 characters (ASCII)
* It balances efficiency and complexity

Today:

* 8-bit = byte (universal standard)

---

## 8. Relationship between everything

This is the part most people miss:

```text
bit → smallest unit (0/1)

byte → storage unit (8 bits)

nibble → hex convenience unit (4 bits)

hex → human-readable binary shorthand
```

Everything in low-level programming connects back to this chain.

---

## 9. Why this matters in C

When you write C code:

```c
int x = 42;
```

The CPU stores it like:

```text
00000000 00000000 00000000 00101010
```

That is:

* 4 bytes (32 bits)
* Grouped as bytes
* Interpreted as an integer

Understanding bits and bytes helps you understand:

* overflow
* memory layout
* pointers
* bitwise operations

---

## 10. Common confusion

### “Is a byte always 8 bits?”

Modern systems: yes

But technically:

* historically it could vary
* today almost all systems use 8-bit bytes

---

### “Why do we need nibbles?”

You don’t *need* them.

But they are useful because:

* 4 bits = hex digit
* makes binary readable

---

## 11. Quick memory rules

```text
1 byte = 8 bits
1 nibble = 4 bits
1 byte = 2 hex digits
```

Example:

```text
11111111 (binary)
= FF (hex)
= 255 (decimal)
```

---

## 12. Practice

Try these mentally:

1. How many values in 5 bits?
2. What is the max value of 1 byte?
3. Convert `1010 1111` to hex
4. How many nibbles in a byte?
5. Why is hex always 2 digits per byte?

---

## 13. Resources (best explanations)

### Core explanations

* https://www.khanacademy.org/computing/computer-science/cryptography
* https://www.cs.cornell.edu/courses/cs3410/2019sp/notes/
* https://www.cs.utexas.edu/~fussell/courses/cs310h/lectures/Lecture_03-310h.pdf

---

### Beginner-friendly learning

* https://www.csfieldguide.org.nz/en/chapters/data-representation/bits-and-bytes/
* https://www.computerhistory.org/revolution/digital-logic/12/273

---

### Interactive

* https://integer.exposed/
* https://baseconvert.com/

---

## 14. What comes next

```text
00_Binary_Number_Systems
01_Bits_Bytes_Nibbles   ← YOU ARE HERE
02_Hexadecimal_And_Octal
03_Twos_Complement
04_Bitwise_Operators
```

Once you understand bits and bytes properly, everything else in low-level programming becomes easier.

Because from this point onward:

You are no longer reading numbers.

You are reading memory.
