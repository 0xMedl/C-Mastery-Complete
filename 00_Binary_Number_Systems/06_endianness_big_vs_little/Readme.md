# 06 - Endianness: Big Endian vs Little Endian

## Introduction

Computers store all information as bytes. A byte consists of 8 bits and is the smallest unit of memory that can usually be addressed individually.

When a value occupies only one byte, there is no ambiguity about how it is stored. For example:

```text
0x7A
```

occupies a single byte, so there is only one possible memory representation.

The situation changes when a value occupies multiple bytes.

Consider the hexadecimal value:

```text
0x12345678
```

This value requires four bytes:

```text
12 34 56 78
```

Since memory is organized as a sequence of bytes, the system must decide:

**Which byte should be placed at the lowest memory address?**

The answer to this question is called **endianness**.

---

# What is Endianness?

Endianness is the convention used by a computer system to determine the order in which the bytes of a multi-byte value are stored in memory.

It does not change the value itself.

It only changes how the bytes are arranged in memory.

For a value composed of multiple bytes, there are two primary arrangements:

1. Big Endian
2. Little Endian

---

# Understanding Significance

Before discussing byte order, we must understand significance.

Consider the decimal number:

```text
1234
```

The digit 1 has the greatest significance because it contributes:

```text
1 × 1000
```

The digit 4 has the least significance because it contributes:

```text
4 × 1
```

The same concept exists in hexadecimal numbers.

Consider:

```text
0x12345678
```

The bytes are:

```text
12 34 56 78
```

The byte:

```text
12
```

contributes the most to the final value and is therefore called the:

**Most Significant Byte (MSB)**

The byte:

```text
78
```

contributes the least and is therefore called the:

**Least Significant Byte (LSB)**

---

# Memory Addresses

Memory is a sequence of locations.

Suppose a value begins at address:

```text
1000
```

The next bytes occupy:

```text
1001
1002
1003
```

A four-byte value therefore occupies four consecutive memory locations.

The only question is how the bytes are distributed among those addresses.

---

# Big Endian

Big Endian stores the Most Significant Byte at the lowest memory address.

Using:

```text
0x12345678
```

the memory layout becomes:

```text
Address    Byte
1000       12
1001       34
1002       56
1003       78
```

Visualized:

```text
Low Address                 High Address

1000    1001    1002    1003
+----+  +----+  +----+  +----+
| 12 |  | 34 |  | 56 |  | 78 |
+----+  +----+  +----+  +----+
```

The most important byte appears first.

This layout resembles the way humans normally write numbers.

When we write:

```text
12345678
```

we place the most significant digit on the left.

Big Endian follows a similar philosophy.

---

# Little Endian

Little Endian stores the Least Significant Byte at the lowest memory address.

Using the same value:

```text
0x12345678
```

memory becomes:

```text
Address    Byte
1000       78
1001       56
1002       34
1003       12
```

Visualized:

```text
Low Address                 High Address

1000    1001    1002    1003
+----+  +----+  +----+  +----+
| 78 |  | 56 |  | 34 |  | 12 |
+----+  +----+  +----+  +----+
```

The least important byte appears first.

---

# Comparing Both Arrangements

For the value:

```text
0x12345678
```

Big Endian:

```text
12 34 56 78
```

Little Endian:

```text
78 56 34 12
```

The numerical value remains identical.

Only the storage order changes.

This is a critical point.

Many beginners mistakenly believe endianness changes the number itself.

It does not.

It only changes how that number is represented in memory.

---

# Why Do Different Endiannesses Exist?

Different processor designers made different architectural decisions.

Big Endian was considered intuitive because memory appears in the same order humans write numbers.

Little Endian was adopted because it simplifies certain hardware operations.

Historically, different processor families evolved independently and selected different conventions.

As a result, both formats became widely used.

---

# Reading a Multi-Byte Value

Suppose memory contains:

```text
Address    Byte
1000       78
1001       56
1002       34
1003       12
```

A Little Endian processor interprets these bytes as:

```text
0x12345678
```

because it expects the least significant byte first.

A Big Endian processor reading the same bytes would interpret:

```text
0x78563412
```

because it expects the most significant byte first.

The bytes did not change.

Only the interpretation changed.

---

# Endianness and Data Exchange

Problems arise when systems with different endianness exchange raw binary data.

Imagine:

System A stores:

```text
0x12345678
```

and sends its bytes directly:

```text
78 56 34 12
```

A system expecting Big Endian may reconstruct:

```text
0x78563412
```

instead of:

```text
0x12345678
```

The data becomes incorrect.

This is one of the main reasons endianness is important.

---

# Network Byte Order

Computer networks require a standard format.

Without a standard, communication between different architectures would be unreliable.

The Internet therefore defines:

```text
Network Byte Order
```

as:

```text
Big Endian
```

Whenever binary numbers are transmitted over many network protocols, they are represented in Big Endian form.

This ensures every machine interprets transmitted data consistently.

---

# Endianness in File Formats

Many binary file formats define their own byte order.

Examples include:

* Images
* Audio files
* Executable files
* Databases

If software reads data using the wrong endianness, values become corrupted because bytes are interpreted incorrectly.

Therefore file specifications often explicitly state whether values are stored using Big Endian or Little Endian.

---

# Bi-Endian Systems

Some processor architectures can operate in both modes.

These are called:

```text
Bi-Endian
```

processors.

Such systems can switch between Big Endian and Little Endian operation depending on configuration.

This provides flexibility when interacting with different software ecosystems.

---

# Common Misconceptions

## Misconception 1

"Endianness changes the value."

False.

Endianness changes only storage order.

The value itself remains the same.

---

## Misconception 2

"Big Endian is newer than Little Endian."

False.

Both have existed for decades.

---

## Misconception 3

"Only programmers care about endianness."

False.

Endianness affects:

* Networking
* Operating systems
* Databases
* Digital forensics
* Reverse engineering
* Hardware design
* Binary file processing

---

# Summary

Endianness defines how multi-byte values are arranged in memory.

Big Endian stores the Most Significant Byte first.

Little Endian stores the Least Significant Byte first.

The value represented by the bytes does not change; only the order of storage changes.

Understanding endianness is essential whenever data is examined at the byte level, transferred between different systems, stored in binary formats, or interpreted directly from memory.

A solid understanding of endianness provides a foundation for studying computer architecture, memory organization, networking, and low-level systems.
