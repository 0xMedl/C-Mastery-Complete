# 08 - Floating Point and IEEE 754

## Introduction

Not all numbers are whole numbers.

Many real-world calculations involve values such as:

```text
3.14
0.5
-12.75
0.0001
```

These numbers contain a fractional part and cannot be represented accurately using ordinary integers.

Computers therefore need a different system for storing and manipulating such values.

This system is called **floating-point representation**.

The most widely used standard for floating-point numbers is known as **IEEE 754**.

Understanding IEEE 754 is important because it explains why decimal values are stored the way they are, why some calculations produce unexpected results, and why computers sometimes appear to make tiny arithmetic mistakes.

---

# The Problem with Fractions

Integers are straightforward.

For example:

```text
5
100
-42
```

can be represented directly using bits.

Fractions are different.

Consider:

```text
0.1
```

Humans write this number using a base-10 system.

Computers operate using a base-2 system.

Many decimal fractions that look simple in base 10 cannot be represented exactly in base 2.

This creates one of the most important challenges in computer arithmetic.

---

# Scientific Notation

Before understanding floating-point numbers, consider scientific notation.

Instead of writing:

```text
123000000
```

we can write:

```text
1.23 × 10^8
```

Likewise:

```text
0.0000123
```

can be written as:

```text
1.23 × 10^-5
```

Scientific notation allows very large and very small numbers to be represented efficiently.

Floating-point representation uses the same idea.

---

# Why Is It Called "Floating Point"?

Consider the number:

```text
1234.56
```

The decimal point can move:

```text
1234.56
123.456 × 10¹
12.3456 × 10²
1.23456 × 10³
```

The value remains the same even though the decimal point appears in different positions.

The point is said to "float."

Floating-point representation stores:

1. The significant digits
2. The position of the point

rather than storing every digit directly.

---

# Binary Scientific Notation

Computers use powers of 2 instead of powers of 10.

For example:

```text
1101₂
```

can be written as:

```text
1.101₂ × 2³
```

Similarly:

```text
101.01₂
```

can be written as:

```text
1.0101₂ × 2²
```

This normalized form is the foundation of IEEE 754.

---

# What Is IEEE 754?

IEEE 754 is an international standard that defines:

* How floating-point numbers are stored
* How calculations are performed
* How rounding works
* How special values are represented

The goal is consistency.

Without a standard, different computers could produce different results for the same calculation.

---

# Components of a Floating-Point Number

IEEE 754 stores a floating-point value using three parts:

1. Sign
2. Exponent
3. Fraction (Mantissa)

Together these fields describe any floating-point number.

---

# The Sign Bit

The sign bit determines whether a number is positive or negative.

```text
0 = Positive
1 = Negative
```

Examples:

```text
0 → +3.14
1 → -3.14
```

Only one bit is required.

---

# The Exponent

The exponent determines the scale of the number.

Just as scientific notation uses:

```text
10³
10⁶
10⁻²
```

IEEE 754 uses:

```text
2³
2⁶
2⁻²
```

The exponent tells the computer how far to move the binary point.

Large exponents represent large numbers.

Small exponents represent small numbers.

---

# The Fraction (Mantissa)

The fraction contains the significant digits of the number.

It represents the precision of the value.

Think of it as the actual information that makes:

```text
1.234
```

different from:

```text
1.567
```

The more bits allocated to the fraction, the more precise the number becomes.

---

# Single Precision (32-bit)

A 32-bit floating-point number is divided into:

```text
1 bit    → Sign
8 bits   → Exponent
23 bits  → Fraction
```

Visual representation:

```text
+------+----------+-----------------------+
| Sign | Exponent |       Fraction        |
+------+----------+-----------------------+
   1         8               23
```

Total:

```text
32 bits
```

---

# Double Precision (64-bit)

A 64-bit floating-point number uses:

```text
1 bit    → Sign
11 bits  → Exponent
52 bits  → Fraction
```

Visual representation:

```text
+------+-------------+----------------------+
| Sign |  Exponent   |      Fraction        |
+------+-------------+----------------------+
   1         11                52
```

Total:

```text
64 bits
```

Double precision provides significantly more accuracy.

---

# Why Floating-Point Is Not Exact

One of the most surprising aspects of floating-point arithmetic is that some numbers cannot be represented exactly.

Consider:

```text
0.1
```

Humans see a simple value.

In binary, however, it becomes an infinitely repeating fraction.

Similar to how:

```text
1/3
```

becomes:

```text
0.333333333...
```

in decimal,

```text
0.1
```

becomes an endless repeating pattern in binary.

Since memory is finite, the computer must stop somewhere.

The value is rounded.

---

# The Famous Example

Consider:

```text
0.1 + 0.2
```

Mathematically:

```text
0.3
```

Many programming languages produce:

```text
0.30000000000000004
```

Why?

Because:

* 0.1 is approximated
* 0.2 is approximated
* The approximations are added

The tiny rounding errors become visible.

The computer is not broken.

It is using the closest representable values available.

---

# Precision vs Accuracy

These terms are often confused.

### Precision

How many digits can be represented.

### Accuracy

How close a value is to the mathematically correct result.

A number may be highly precise yet still contain a small error due to rounding.

---

# Rounding

Many values fall between two representable floating-point numbers.

When this happens, IEEE 754 applies rounding rules.

The most common strategy is:

```text
Round to nearest value
```

This minimizes cumulative errors during calculations.

---

# Very Large Numbers

Floating-point representation can store enormous values.

For example:

```text
10^20
10^100
10^300
```

depending on the precision used.

This is possible because the exponent allows the binary point to move far from its original position.

---

# Very Small Numbers

Floating-point numbers can also represent extremely tiny values:

```text
0.000001
0.000000000001
10^-100
```

Again, the exponent field makes this possible.

---

# Infinity

IEEE 754 defines special values.

One of them is:

```text
Infinity
```

Examples:

```text
Positive Infinity
Negative Infinity
```

These may appear when calculations exceed the maximum representable value.

For example:

```text
Very Large Number × Very Large Number
```

can overflow to infinity.

---

# NaN (Not a Number)

IEEE 754 also defines:

```text
NaN
```

which means:

```text
Not a Number
```

NaN appears when a mathematical operation has no valid numeric result.

Examples include:

```text
0 ÷ 0
```

or

```text
√(-1)
```

within ordinary real-number arithmetic.

NaN allows the system to continue operating while signaling that an invalid calculation occurred.

---

# Common Misconceptions

## Misconception 1

"Floating-point numbers are exact."

False.

Many decimal fractions must be approximated.

---

## Misconception 2

"Computers make arithmetic mistakes."

Not exactly.

The computer follows IEEE 754 rules correctly.

The apparent errors come from unavoidable approximations.

---

## Misconception 3

"Using more bits eliminates all errors."

False.

More bits reduce errors but cannot eliminate them completely.

Some values remain impossible to represent exactly.

---

## Misconception 4

"0.1 should be stored perfectly."

Humans think in decimal.

Computers store numbers in binary.

Many decimal fractions become repeating binary fractions and therefore require rounding.

---

# Why IEEE 754 Matters

Understanding IEEE 754 helps explain:

* Unexpected arithmetic results
* Rounding behavior
* Numerical precision limits
* Scientific computing challenges
* Financial calculation concerns
* Graphics and simulation behavior

It provides the foundation for almost every floating-point calculation performed by modern computers.

---

# Summary

Floating-point representation is a method for storing numbers that contain fractional parts.

IEEE 754 is the standard used by modern computer systems to represent and manipulate floating-point values.

Every floating-point number is composed of:

* A sign
* An exponent
* A fraction (mantissa)

This design allows computers to represent extremely large and extremely small numbers efficiently.

However, because many decimal values cannot be represented exactly in binary, floating-point arithmetic often involves approximations and rounding.

Understanding IEEE 754 is essential for understanding how computers work with real numbers and why floating-point calculations sometimes behave differently from pure mathematics.
