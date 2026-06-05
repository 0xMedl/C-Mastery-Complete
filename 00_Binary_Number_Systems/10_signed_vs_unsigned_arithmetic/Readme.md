# 10 - Signed vs Unsigned Arithmetic

## Introduction

Computers store numbers using bits.

At first glance, a sequence of bits appears simple:

```text
10101010
```

However, a fundamental question immediately arises:

**How should these bits be interpreted?**

Should they represent only positive values?

Or should they represent both positive and negative values?

The answer determines whether a number is treated as **signed** or **unsigned**.

Understanding the difference between signed and unsigned arithmetic is essential because the exact same bit pattern can represent completely different values depending on how it is interpreted.

Many bugs, unexpected results, and security vulnerabilities arise from misunderstandings between signed and unsigned numbers.

---

# What Is an Unsigned Integer?

An unsigned integer can represent only non-negative values.

In other words:

```text
0
1
2
3
...
```

but never:

```text
-1
-2
-3
```

All available bits are used to represent magnitude.

Nothing is reserved for indicating whether the value is positive or negative.

---

# Unsigned Range

Consider an 8-bit unsigned number.

Eight bits provide:

```text
2⁸ = 256
```

possible combinations.

These combinations represent:

```text
0 → 255
```

The smallest value is:

```text
0
```

The largest value is:

```text
255
```

Example:

```text
00000000 = 0
```

```text
11111111 = 255
```

Every bit contributes directly to the value.

---

# What Is a Signed Integer?

A signed integer can represent both positive and negative values.

Examples:

```text
-5
-1
0
1
5
```

To achieve this, one bit must somehow indicate the sign.

Modern computers use a system called:

```text
Two's Complement
```

to represent signed integers.

Almost every modern processor uses two's complement because it simplifies arithmetic operations.

---

# Signed Range

Consider an 8-bit signed integer.

Since one bit is used to help represent negative values, the range changes.

Instead of:

```text
0 → 255
```

the range becomes:

```text
-128 → 127
```

The total number of possible values remains:

```text
256
```

but they are distributed differently.

---

# The Same Bits, Different Meaning

This is one of the most important concepts in computer arithmetic.

Consider:

```text
11111111
```

If interpreted as unsigned:

```text
255
```

If interpreted as signed:

```text
-1
```

The bits did not change.

Only the interpretation changed.

This is similar to language.

The same symbol can mean different things depending on context.

Bits behave the same way.

---

# Why Signed Numbers Exist

Many real-world calculations involve negative values.

Examples:

```text
Temperature changes
Financial losses
Position offsets
Velocity directions
Elevation differences
```

Without signed numbers, computers could not represent these values naturally.

Signed arithmetic allows positive and negative values to coexist within the same representation system.

---

# Understanding Two's Complement

Two's complement is the standard method for storing signed integers.

The most significant bit plays a special role.

For an 8-bit value:

```text
10000000
```

the leftmost bit has a negative weight.

This allows negative numbers to be represented naturally.

A full explanation of two's complement deserves its own chapter, but for now it is enough to understand:

```text
00000001 = 1
```

```text
11111111 = -1
```

```text
11111110 = -2
```

```text
11111101 = -3
```

and so on.

---

# Unsigned Arithmetic

Unsigned arithmetic assumes every value is positive.

Example:

```text
10 + 5 = 15
```

Simple and predictable.

Problems appear when results exceed the maximum range.

Consider an 8-bit unsigned integer:

```text
255 + 1
```

The mathematical answer is:

```text
256
```

But 256 cannot be represented.

The value wraps around:

```text
0
```

This is called:

```text
Unsigned Overflow
```

---

# Visualizing Unsigned Overflow

Imagine a circular counter:

```text
253
254
255
0
1
2
```

After reaching the maximum value, counting continues from the beginning.

The counter wraps around.

---

# Unsigned Underflow

Now consider:

```text
0 - 1
```

Mathematically:

```text
-1
```

However, unsigned integers cannot represent negative values.

The result wraps around:

```text
255
```

for an 8-bit unsigned integer.

This is called:

```text
Unsigned Underflow
```

---

# Visualizing Unsigned Underflow

Imagine moving backward on a clock.

If you go back one step from:

```text
0
```

you arrive at:

```text
255
```

instead of a negative number.

The value wraps around the boundary.

---

# Signed Arithmetic

Signed arithmetic must handle both positive and negative values.

Examples:

```text
5 + (-3)
```

```text
-10 + 4
```

```text
-7 - 8
```

Two's complement allows the processor to perform these operations efficiently.

To the hardware, addition and subtraction become surprisingly simple.

---

# Signed Overflow

Consider an 8-bit signed integer.

Maximum value:

```text
127
```

Adding one:

```text
127 + 1
```

produces:

```text
-128
```

because the range has been exceeded.

The value wraps around to the opposite end.

---

# Visualizing Signed Overflow

Signed numbers form a circular range:

```text
...
125
126
127
-128
-127
-126
...
```

Crossing the maximum boundary causes the value to reappear at the minimum boundary.

---

# Signed Underflow

Now consider:

```text
-128 - 1
```

The result should be:

```text
-129
```

but this value cannot be represented.

The stored result becomes:

```text
127
```

The value wraps around in the opposite direction.

---

# Comparing Signed and Unsigned

Consider the bit pattern:

```text
11111111
```

Unsigned interpretation:

```text
255
```

Signed interpretation:

```text
-1
```

Another example:

```text
10000000
```

Unsigned:

```text
128
```

Signed:

```text
-128
```

The same bits can represent completely different values.

This distinction is critical.

---

# Why Mixing Signed and Unsigned Is Dangerous

Many programming errors occur when signed and unsigned values are combined.

Suppose:

```text
Signed value:   -1
Unsigned value: 1
```

At first glance:

```text
-1 < 1
```

appears obviously true.

However, if the signed value is converted into an unsigned value, the comparison may produce an unexpected result.

The negative value may become a very large positive value after conversion.

This can lead to subtle bugs that are difficult to detect.

---

# Real-World Problems

Misunderstanding signed and unsigned arithmetic has caused:

* Software crashes
* Infinite loops
* Memory corruption
* Security vulnerabilities
* Incorrect calculations

Many vulnerabilities in operating systems and applications originated from arithmetic involving mismatched signed and unsigned values.

---

# When Should Signed Numbers Be Used?

Signed numbers are appropriate when values can become negative.

Examples:

```text
Temperature differences
Profit and loss calculations
Coordinates
Physics simulations
Elevation measurements
```

Whenever negative values are meaningful, signed representation is usually the correct choice.

---

# When Should Unsigned Numbers Be Used?

Unsigned numbers are useful when negative values make no sense.

Examples:

```text
Population counts
File sizes
Object counts
Memory sizes
Array lengths
```

A file cannot have:

```text
-10 bytes
```

Therefore unsigned values often make sense for quantities that can never be negative.

---

# Common Misconceptions

## Misconception 1

"Unsigned numbers are always better because they store larger values."

False.

They store larger positive values, but cannot represent negatives.

Choosing the wrong representation can create serious problems.

---

## Misconception 2

"Bits determine the value."

Partially true.

Bits determine the possible patterns.

The interpretation determines the actual value.

---

## Misconception 3

"The computer knows whether a number is signed."

Not automatically.

Bits are just bits.

Software and hardware instructions determine how those bits should be interpreted.

---

## Misconception 4

"Overflow always produces an error."

False.

Many systems simply wrap around and continue execution.

The result may be incorrect without any visible warning.

---

# Key Differences

| Signed                                   | Unsigned                                        |
| ---------------------------------------- | ----------------------------------------------- |
| Can represent negative values            | Cannot represent negative values                |
| Uses two's complement representation     | Uses all bits for magnitude                     |
| Smaller positive range                   | Larger positive range                           |
| Suitable for values that may be negative | Suitable for quantities that cannot be negative |

---

# Summary

Signed and unsigned integers use the same bits but interpret them differently.

Unsigned integers represent only non-negative values and use the entire bit range for positive numbers.

Signed integers use two's complement representation, allowing both positive and negative values to be stored.

Because the same bit pattern can represent different values depending on interpretation, understanding signed and unsigned arithmetic is essential for correctly reading data, performing calculations, avoiding overflow bugs, and writing reliable software.

The most important lesson is simple:

**Bits alone do not have meaning. Meaning comes from how those bits are interpreted.**
