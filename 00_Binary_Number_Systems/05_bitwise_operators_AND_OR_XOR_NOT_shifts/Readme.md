# 05 — Bitwise Operators (AND, OR, XOR, NOT, Shifts)

> **C Mastery Complete** › Module 05
> *This is where you stop thinking in numbers and start thinking in bits.*

---

## Why this topic matters

Up to now, you’ve been treating numbers like values:

```text
42, 255, -5
```

But inside the computer, everything is just bits:

```text
01010110
```

Bitwise operators let you **directly control those bits**.

This is what powers:

* low-level system code
* embedded programming
* performance optimization
* graphics
* compression
* networking
* device drivers

---

## 1. The core idea

Bitwise operations work **bit by bit**, not on the whole number.

Example:

```text
A =  1010
B =  1100
```

We don’t treat them as 10 and 12.

We treat them as:

```text
1 0 1 0
1 1 0 0
```

---

## 2. Bitwise AND (`&`)

Rule:

```text
1 & 1 = 1
everything else = 0
```

Example:

```text
  1010
& 1100
------
  1000
```

### Think of it like:

“Keep the bit only if BOTH are 1”

### Common use:

* checking flags
* masking bits

```c
if (x & 0x04)
{
    // bit 2 is ON
}
```

---

## 3. Bitwise OR (`|`)

Rule:

```text
1 | 1 = 1
1 | 0 = 1
0 | 0 = 0
```

Example:

```text
  1010
| 1100
------
  1110
```

### Think of it like:

“Turn on bits if either side has 1”

### Common use:

* setting flags

```c
x = x | 0x08; // set bit 3
```

---

## 4. Bitwise XOR (`^`)

Rule:

```text
same bits → 0
different → 1
```

Example:

```text
  1010
^ 1100
------
  0110
```

### Think of it like:

“Difference detector”

### Common uses:

* toggling bits
* simple encryption tricks
* detecting changes

```c
x ^= 0x01; // toggle last bit
```

---

## 5. Bitwise NOT (`~`)

Rule:

```text
0 → 1
1 → 0
```

Example (8-bit):

```text
  00001111
~ --------
  11110000
```

### Important:

NOT flips **all bits**, including sign bit in signed integers.

So:

```c
~5
```

is NOT just "-5".

It becomes:

```text
-(5 + 1)
```

because of two’s complement.

---

## 6. Left Shift (`<<`)

Rule:

```text
x << n  = x × 2ⁿ
```

Example:

```text
00000101 << 1
= 00001010
= 10
```

So:

```text
5 << 1 = 10
5 << 2 = 20
```

### Think of it like:

“move bits left, multiply by 2”

### Common use:

* fast multiplication
* building bit masks

```c
1 << 3  // 00001000 (bit 3)
```

---

## 7. Right Shift (`>>`)

Rule:

```text
x >> n  = x ÷ 2ⁿ
```

Example:

```text
00001010 >> 1
= 00000101
= 5
```

### Think of it like:

“move bits right, divide by 2”

---

### Important detail (signed numbers)

Right shift of signed integers can behave differently:

* logical shift (fills with 0)
* arithmetic shift (keeps sign bit)

Most modern systems use arithmetic shift for signed values.

---

## 8. Why shifts are powerful

Instead of:

```c
x * 8
```

you can write:

```c
x << 3
```

Because:

```text
2³ = 8
```

This is faster at the hardware level (historically very important).

---

## 9. Bit masking (real-world usage)

### Set a bit

```c
x = x | (1 << n);
```

### Clear a bit

```c
x = x & ~(1 << n);
```

### Toggle a bit

```c
x = x ^ (1 << n);
```

### Check a bit

```c
if (x & (1 << n))
{
    // bit is 1
}
```

---

## 10. Real-world examples

### File permissions (Unix)

```text
chmod 755
```

is bitwise representation of:

* read/write/execute flags

---

### Hardware registers

Embedded systems use:

```c
PORT |= (1 << 2);
```

to turn ON a pin.

---

### Graphics / colors

Bitwise operations define:

* RGB channels
* alpha blending
* pixel packing

---

## 11. Common mistakes

### Mistake 1: confusing `&` and `&&`

```c
if (x & 1)   // bitwise check
if (x && 1)  // logical check (wrong for bits)
```

---

### Mistake 2: assuming NOT is simple negation

```c
~5 != -5
```

It becomes:

```text
-6
```

---

### Mistake 3: shifting signed numbers blindly

```c
1 << 31   // dangerous in signed int
```

Use unsigned:

```c
1u << 31
```

---

## 12. Mental model (IMPORTANT)

Think like this:

```text
AND  → filter bits
OR   → set bits
XOR  → flip bits
NOT  → invert bits
<<   → multiply by 2
>>   → divide by 2
```

If you remember only this, you're already strong.

---

## 13. Practice

Try without running code:

1. `0b1010 & 0b0110`
2. `0b1010 | 0b0110`
3. `0b1010 ^ 0b0110`
4. `~0b00001111` (8-bit)
5. `5 << 2`
6. `20 >> 2`

---

## 14. Resources

### Beginner + Visual

* https://www.csfieldguide.org.nz/en/chapters/binary-numbers/
* https://www.khanacademy.org/computing/computer-science

---

### Interactive

* https://integer.exposed/
* https://visualgo.net/en/binary

---

### Practical C focus

* https://beej.us/guide/bgc/
* https://www.learn-c.org/

---

### Video (very recommended)

* Computerphile (bitwise operations)
* Neso Academy (bitwise operators C)
* Ben Eater (hardware view)

---

## 15. What’s next

```text
03_Twos_Complement
04_Integer_Overflow
05_Bitwise_Operators   ← YOU ARE HERE
06_Memory_And_Pointers
```

Bitwise operators are the bridge between:

* mathematics
* hardware
* and real systems programming

Once this clicks, pointers and memory manipulation become much easier.
