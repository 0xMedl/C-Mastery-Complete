# 09 - Base Conversion Practice

## Introduction

Humans usually work with numbers using the **decimal system**, also known as **base 10**.

Computers, however, operate using **binary (base 2)**. In many technical fields, **octal (base 8)** and **hexadecimal (base 16)** are also commonly used.

Because different systems use different bases, it is important to know how to convert numbers from one base to another.

Base conversion is one of the most fundamental skills in computer science because it helps us understand how computers store, process, and display data.

This chapter focuses on understanding number bases and learning reliable methods for converting between them.

---

# What Is a Number Base?

A number base determines:

1. Which digits are available.
2. The value represented by each position.

In everyday life we use decimal:

```text
0 1 2 3 4 5 6 7 8 9
```

Ten symbols are available.

Therefore decimal is:

```text
Base 10
```

Binary uses only:

```text
0 1
```

Therefore binary is:

```text
Base 2
```

Hexadecimal uses:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Sixteen symbols are available.

Therefore hexadecimal is:

```text
Base 16
```

---

# Understanding Positional Value

Consider the decimal number:

```text
345
```

The digits do not have the same value.

The rightmost digit represents:

```text
5 × 10⁰
```

The middle digit represents:

```text
4 × 10¹
```

The left digit represents:

```text
3 × 10²
```

Therefore:

```text
345 =
(3 × 10²) +
(4 × 10¹) +
(5 × 10⁰)
```

which becomes:

```text
300 + 40 + 5
```

The same principle works in every base.

Only the base changes.

---

# Binary Numbers

Binary uses powers of 2.

Example:

```text
1011₂
```

Expanding each position:

```text
1 × 2³
0 × 2²
1 × 2¹
1 × 2⁰
```

Calculating:

```text
8 + 0 + 2 + 1
```

Result:

```text
11₁₀
```

Therefore:

```text
1011₂ = 11₁₀
```

---

# Converting Binary to Decimal

This is usually the easiest conversion.

Example:

```text
110101₂
```

Expand each position:

```text
1 × 2⁵
1 × 2⁴
0 × 2³
1 × 2²
0 × 2¹
1 × 2⁰
```

Calculate:

```text
32 + 16 + 0 + 4 + 0 + 1
```

Result:

```text
53
```

Therefore:

```text
110101₂ = 53₁₀
```

---

# Converting Decimal to Binary

This conversion uses repeated division by 2.

Example:

```text
25₁₀
```

Divide repeatedly:

```text
25 ÷ 2 = 12 remainder 1
12 ÷ 2 = 6  remainder 0
6  ÷ 2 = 3  remainder 0
3  ÷ 2 = 1  remainder 1
1  ÷ 2 = 0  remainder 1
```

Read remainders from bottom to top:

```text
11001
```

Therefore:

```text
25₁₀ = 11001₂
```

---

# Why Read Bottom to Top?

This confuses many beginners.

The first remainder obtained corresponds to the least significant bit.

The last remainder corresponds to the most significant bit.

Reading upward reconstructs the number correctly.

---

# Octal Numbers

Octal uses:

```text
0 1 2 3 4 5 6 7
```

and powers of 8.

Example:

```text
157₈
```

Expands to:

```text
1 × 8²
5 × 8¹
7 × 8⁰
```

Calculating:

```text
64 + 40 + 7
```

Result:

```text
111₁₀
```

Therefore:

```text
157₈ = 111₁₀
```

---

# Converting Binary to Octal

A useful shortcut exists.

Group bits into sets of three starting from the right.

Example:

```text
101110011₂
```

Group:

```text
101 110 011
```

Convert each group:

```text
101 = 5
110 = 6
011 = 3
```

Result:

```text
563₈
```

Therefore:

```text
101110011₂ = 563₈
```

---

# Hexadecimal Numbers

Hexadecimal uses sixteen symbols:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

The letters represent:

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

Hexadecimal was created because long binary values are difficult to read.

---

# Converting Hexadecimal to Decimal

Example:

```text
2F₁₆
```

Expand:

```text
2 × 16¹
F × 16⁰
```

Replace F:

```text
F = 15
```

Calculate:

```text
(2 × 16) + 15
```

Result:

```text
47
```

Therefore:

```text
2F₁₆ = 47₁₀
```

---

# Converting Decimal to Hexadecimal

Use repeated division by 16.

Example:

```text
255₁₀
```

Divide:

```text
255 ÷ 16 = 15 remainder 15
15 ÷ 16 = 0 remainder 15
```

Convert remainders:

```text
15 = F
```

Read upward:

```text
FF
```

Therefore:

```text
255₁₀ = FF₁₆
```

---

# Converting Binary to Hexadecimal

Group bits into groups of four.

Example:

```text
110101111010₂
```

Group:

```text
1101 0111 1010
```

Convert:

```text
1101 = D
0111 = 7
1010 = A
```

Result:

```text
D7A₁₆
```

---

# Converting Hexadecimal to Binary

Convert each hex digit independently.

Example:

```text
3A₁₆
```

Convert:

```text
3 = 0011
A = 1010
```

Combine:

```text
00111010₂
```

Therefore:

```text
3A₁₆ = 00111010₂
```

---

# Why Hexadecimal Is Popular

Binary is accurate but difficult for humans to read.

Consider:

```text
1111111111111111
```

Now compare:

```text
FFFF
```

Both represent the same value.

Hexadecimal is shorter, cleaner, and easier to work with.

For this reason it is heavily used in:

* Memory addresses
* Machine code
* Debuggers
* Networking
* Operating systems
* Digital electronics

---

# Common Conversion Relationships

One hexadecimal digit corresponds exactly to:

```text
4 binary bits
```

Example:

```text
A = 1010
```

One octal digit corresponds exactly to:

```text
3 binary bits
```

Example:

```text
7 = 111
```

This is why binary-octal and binary-hex conversions are extremely fast.

---

# Common Mistakes

## Mistake 1

Reading binary numbers as decimal digits.

Example:

```text
1010
```

This is not one thousand and ten.

In binary it equals:

```text
10₁₀
```

---

## Mistake 2

Forgetting positional powers.

Every digit's value depends on its position.

---

## Mistake 3

Reading division remainders in the wrong direction.

For decimal-to-binary and decimal-to-hex conversions:

```text
Read remainders from bottom to top.
```

---

## Mistake 4

Treating hexadecimal letters as ordinary characters.

Remember:

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

---

# Practice Examples

Convert:

```text
1010₂
```

to decimal.

Solution:

```text
1×2³ + 0×2² + 1×2¹ + 0×2⁰
= 8 + 2
= 10
```

---

Convert:

```text
42₁₀
```

to binary.

Solution:

```text
42 ÷ 2 = 21 r0
21 ÷ 2 = 10 r1
10 ÷ 2 = 5  r0
5  ÷ 2 = 2  r1
2  ÷ 2 = 1  r0
1  ÷ 2 = 0  r1
```

Read upward:

```text
101010₂
```

---

Convert:

```text
7B₁₆
```

to decimal.

Solution:

```text
7×16¹ + 11×16⁰
= 112 + 11
= 123
```

---

# Summary

A number base determines the symbols available and the value of each position.

The most important bases in computing are:

```text
Base 2  → Binary
Base 8  → Octal
Base 10 → Decimal
Base 16 → Hexadecimal
```

All conversions rely on the same fundamental idea:

**Every digit contributes a value based on its position and the base being used.**

Once positional notation is understood, converting between bases becomes a mechanical process rather than a memorization exercise.

Mastering base conversion is one of the most important foundations for understanding computer systems, memory representation, machine code, networking, and digital electronics.
