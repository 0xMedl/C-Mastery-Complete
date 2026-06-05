# 07 - Integer Overflow and Underflow

## Introduction

Computers cannot store infinitely large numbers.

Every integer occupies a fixed amount of memory, and that memory provides a limited number of bits for representing values.

Because the available space is limited, every integer type has a maximum value and a minimum value that it can represent.

When a calculation produces a value outside this range, the result can no longer be represented correctly.

This phenomenon is known as **overflow** or **underflow**.

Understanding these concepts is essential because they can lead to unexpected behavior, incorrect calculations, software bugs, security vulnerabilities, and system failures.

---

# Why Does Overflow Exist?

The root cause is simple:

**Memory is finite.**

Imagine a container that can hold only ten liters of water.

If you try to pour twelve liters into it, the container cannot store the extra amount.

The same idea applies to integers.

An integer type has a fixed number of bits.

Once all available bits are used, there is no space left to represent larger values.

---

# Understanding Integer Ranges

The number of bits determines how many different values can be represented.

Consider an unsigned 8-bit integer.

Eight bits can produce:

```text
2^8 = 256
```

different values.

These values range from:

```text
0
```

to:

```text
255
```

Nothing larger than 255 can be represented with only 8 bits.

Likewise, nothing smaller than 0 can be represented.

Every integer type has similar limits.

---

# What is Integer Overflow?

Integer overflow occurs when an arithmetic operation produces a value larger than the maximum value that can be represented.

Imagine an unsigned 8-bit integer.

Maximum value:

```text
255
```

Suppose we add one:

```text
255 + 1
```

Mathematically the result should be:

```text
256
```

However, the integer cannot store 256 because its range ends at 255.

The value wraps around and becomes:

```text
0
```

This is overflow.

---

# Visualizing Overflow

Think of a car odometer.

When it reaches:

```text
999999
```

and one more kilometer is added, it becomes:

```text
000000
```

The odometer does not grow another digit.

It wraps back to the beginning.

Integer overflow works similarly.

Example:

```text
253
254
255
  0
  1
  2
```

After reaching the maximum possible value, counting continues from the start.

---

# What is Integer Underflow?

Integer underflow occurs when a calculation produces a value smaller than the minimum value that can be represented.

Consider again an unsigned integer.

Minimum value:

```text
0
```

Now subtract one:

```text
0 - 1
```

Mathematically the answer is:

```text
-1
```

But unsigned integers cannot represent negative values.

Instead, the value wraps around to the largest representable number.

For an 8-bit unsigned integer:

```text
255
```

This is underflow.

---

# Visualizing Underflow

Imagine a clock.

If the time is:

```text
00:00
```

and you move backward one minute, you get:

```text
23:59
```

You do not go below the lowest value.

You wrap around to the highest value.

Unsigned integers behave similarly.

Example:

```text
2
1
0
255
254
253
```

---

# Signed Integers

So far we have discussed unsigned integers.

Signed integers introduce both positive and negative values.

For example, a signed 8-bit integer typically represents values from:

```text
-128
```

to:

```text
127
```

The exact storage mechanism is called **two's complement**, which is the standard representation used by modern computers.

---

# Signed Overflow

Consider the maximum signed 8-bit value:

```text
127
```

Adding one gives:

```text
127 + 1
```

The mathematical result should be:

```text
128
```

But 128 cannot be represented.

The stored value becomes:

```text
-128
```

The number appears to jump from the largest positive value to the smallest negative value.

---

# Signed Underflow

Consider the minimum signed 8-bit value:

```text
-128
```

Subtract one:

```text
-128 - 1
```

The mathematical result should be:

```text
-129
```

But this value is outside the representable range.

The stored value becomes:

```text
127
```

The number wraps around to the opposite end of the range.

---

# Why Overflow Can Be Dangerous

Overflow is not always obvious.

A program may continue running while silently producing incorrect results.

This can lead to:

* Incorrect calculations
* Corrupted data
* Infinite loops
* Financial errors
* System crashes
* Security vulnerabilities

A program may appear to work correctly until a value approaches the limits of its integer type.

---

# Real-World Example

Imagine a bank application storing balances in a variable with a maximum value.

If a transaction causes the balance to exceed the maximum representable amount, the stored value may wrap around unexpectedly.

Instead of increasing, the balance could become a negative number or a very small positive number.

The result would be catastrophic.

---

# Security Implications

Integer overflow has been responsible for numerous software vulnerabilities.

Attackers sometimes exploit overflow conditions to:

* Bypass security checks
* Corrupt memory
* Cause unexpected behavior
* Trigger crashes
* Gain unauthorized access

For this reason, secure software development pays close attention to arithmetic operations that may exceed valid ranges.

---

# Detecting Overflow

Whenever arithmetic is performed near the limits of a data type, overflow should be considered.

Questions to ask:

* What is the maximum value this variable can hold?
* What is the minimum value this variable can hold?
* Can this calculation exceed those limits?
* What happens if user input is larger than expected?

Thinking about limits before writing code helps prevent overflow-related bugs.

---

# Common Misconceptions

## Misconception 1

"Computers can store any integer."

False.

Every integer type has a finite range.

---

## Misconception 2

"Overflow causes an error."

Not necessarily.

Many systems continue running and simply store an incorrect wrapped value.

---

## Misconception 3

"Overflow only affects large programs."

False.

Even a simple calculation can overflow if the result exceeds the available range.

---

## Misconception 4

"Overflow and underflow are rare."

False.

Any software that processes large amounts of data, financial values, counters, timestamps, or user input can encounter them.

---

# Summary

Integer overflow occurs when a calculation produces a value larger than the maximum representable value.

Integer underflow occurs when a calculation produces a value smaller than the minimum representable value.

Both happen because integer types have a limited number of bits and therefore a limited range of representable values.

When the limits are exceeded, values often wrap around to the opposite end of the range, producing results that may appear surprising or incorrect.

Understanding overflow and underflow is fundamental for understanding how computers represent numbers and why arithmetic operations sometimes behave differently from pure mathematics.
