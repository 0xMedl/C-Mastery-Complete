# 03 — Two's Complement

> *The way computers represent negative integers.*

After learning binary, hexadecimal, and octal, a natural question appears:

```text
How does a computer store -5?
```

A computer only understands bits.

```text
0
1
```

There is no minus sign stored inside memory.

Yet computers can represent:

```text
-1
-5
-42
-1000
```

and perform arithmetic on them correctly.

The solution is called **Two's Complement**.

---

## The Problem

Imagine we have 8 bits.

```text
00000101
```

This is:

```text
5
```

Easy.

But what should:

```text
-5
```

look like?

We need a way to encode negative numbers using only bits.

---

## The Naive Solution: Sign Magnitude

Humans might decide:

```text
0 = positive
1 = negative
```

Use the first bit as a sign.

Example:

```text
00000101 = +5
10000101 = -5
```

Looks reasonable.

Unfortunately it causes problems.

Example:

```text
+0 = 00000000
-0 = 10000000
```

Now there are two zeros.

Computers hate that.

Arithmetic also becomes more complicated.

---

## The Better Solution

Instead of storing a sign separately, modern computers use:

```text
Two's Complement
```

Nearly every CPU today uses it.

---

## The Main Idea

Positive numbers stay exactly the same.

```text
00000001 = 1
00000010 = 2
00000011 = 3
```

Negative numbers occupy the upper half of the bit patterns.

For 8 bits:

```text
00000000 = 0
00000001 = 1
...
01111111 = 127

10000000 = -128
10000001 = -127
...
11111111 = -1
```

Notice:

```text
MSB = 1
```

usually means the number is negative.

---

## How To Find a Negative Number

Rule:

```text
Flip every bit
Add 1
```

Example:

Find -5.

Start with:

```text
5

00000101
```

Flip all bits:

```text
11111010
```

Add 1:

```text
11111011
```

Result:

```text
11111011 = -5
```

---

## Verify It

Add:

```text
5 + (-5)
```

```text
00000101
11111011
---------
00000000
```

Result:

```text
0
```

Exactly what we want.

---

## Why It Is Called Two's Complement

Step 1:

```text
Flip bits
```

This produces the **One's Complement**.

Example:

```text
00000101

↓

11111010
```

Step 2:

```text
Add 1
```

```text
11111011
```

This final value is the **Two's Complement**.

---

## Shortcut Method

Instead of:

```text
flip everything
add one
```

you can:

1. Start from the right.
2. Copy bits until the first 1.
3. Flip everything to the left.

Example:

```text
00010100
```

Copy from the right:

```text
00010100
       ^
```

Keep first 1:

```text
00010100
      1
```

Flip remaining left side:

```text
11101100
```

Same answer.

---

## Range of Values

For n bits:

```text
-(2^(n-1))
to
(2^(n-1))-1
```

Examples:

### 8-bit

```text
-128 to 127
```

### 16-bit

```text
-32768 to 32767
```

### 32-bit

```text
-2147483648 to 2147483647
```

---

## Why The Leftmost Bit Matters

The leftmost bit is called the:

```text
Most Significant Bit (MSB)
```

In two's complement:

```text
MSB = 0 → positive
MSB = 1 → negative
```

Example:

```text
01111111 = 127
```

```text
11111111 = -1
```

---

## The Famous Example: -1

Start with:

```text
00000001
```

Flip:

```text
11111110
```

Add 1:

```text
11111111
```

Therefore:

```text
11111111 = -1
```

This pattern appears everywhere in systems programming.

---

## Why CPUs Love Two's Complement

With sign-magnitude, CPUs need separate hardware for:

```text
addition
subtraction
negative arithmetic
```

With two's complement:

```text
subtraction = addition
```

Everything becomes simpler.

Simpler hardware means:

* faster CPUs
* fewer transistors
* easier arithmetic

This is why two's complement won.

---

## Things Worth Memorizing

```text
MSB = sign indicator

positive:
0xxxxxxx

negative:
1xxxxxxx
```

```text
To negate:

flip bits
add 1
```

```text
11111111 = -1
```

```text
10000000 = -128 (8-bit)
```

---

## Practice

Convert to two's complement:

```text
-1
-5
-12
-42
```

Convert back to decimal:

```text
11111111
11111011
11110100
10000000
```

Explain:

```text
Why does two's complement only have one zero?
```

---

## Resources

### Books

Code — Charles Petzold

But How Do It Know? — J. Clark Scott

Computer Systems: A Programmer's Perspective

Digital Design and Computer Architecture

Computer Science Illuminated

### Videos

Ben Eater

Computerphile

Neso Academy — Two's Complement

### Interactive

integer.exposed

baseconvert.com

RapidTables Binary Converter

---

Next:

```text
00_Binary_Number_Systems
01_Hexadecimal_And_Octal
02_Twos_Complement ← You are here
03_Bitwise_Operators
04_Integer_Overflow
```

Understanding two's complement is the key to understanding signed integers, overflow, bitwise operations, and how CPUs perform arithmetic.
