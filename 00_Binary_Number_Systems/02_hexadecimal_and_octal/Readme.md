# 02 — Hexadecimal and Octal

Before learning bitwise operations, memory addresses, debuggers, or reverse engineering, you need to become comfortable reading numbers that are **not decimal**.

Most beginners learn binary and then immediately wonder:

> Why do programmers keep writing weird numbers like `0xFF`, `0x7FFFFFFF`, or `0755`?

The answer is simple:

Binary is easy for computers.

Hexadecimal and octal are easier for humans.

---

## Hexadecimal (Base 16)

Hexadecimal is a number system that uses **16 symbols** instead of 10.

Decimal uses:

```text
0 1 2 3 4 5 6 7 8 9
```

Hexadecimal uses:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

The letters continue counting after 9:

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

After F comes:

```text
10 (hex)
```

Just like after 9 comes:

```text
10 (decimal)
```

The difference is that hexadecimal is counting in groups of 16 instead of groups of 10.

---

## Why Hexadecimal Exists

Imagine you have this binary number:

```text
1111111111111111
```

You can read it.

But what about this?

```text
11111110101011010011110001010101
```

Now it starts becoming annoying.

Hexadecimal solves this problem.

The same value can be written as:

```text
FEAD3C55
```

Much easier.

That's why debuggers, operating systems, assembly code, memory dumps, and CPUs use hexadecimal everywhere.

---

## The Most Important Hex Table

Memorize this.

Seriously.

| Hex | Binary |
| --- | ------ |
| 0   | 0000   |
| 1   | 0001   |
| 2   | 0010   |
| 3   | 0011   |
| 4   | 0100   |
| 5   | 0101   |
| 6   | 0110   |
| 7   | 0111   |
| 8   | 1000   |
| 9   | 1001   |
| A   | 1010   |
| B   | 1011   |
| C   | 1100   |
| D   | 1101   |
| E   | 1110   |
| F   | 1111   |

Why?

Because **1 hexadecimal digit = exactly 4 bits**.

Once you know this table, converting between binary and hex becomes almost instant.

Example:

```text
101011110011
```

Split into groups of 4:

```text
1010 1111 0011
```

Convert each group:

```text
1010 = A
1111 = F
0011 = 3
```

Result:

```text
0xAF3
```

---

## Hexadecimal in C

In C, hexadecimal numbers start with:

```c
0x
```

Examples:

```c
int x = 0xFF;
int y = 0x2A;
```

These mean:

```text
0xFF = 255
0x2A = 42
```

You'll see hexadecimal constantly when working with:

* Memory addresses
* Bit masks
* Registers
* Embedded systems
* Reverse engineering
* Operating systems

Example:

```text
0x7FFDF8A21030
```

This looks scary today.

In a few weeks it'll look completely normal.

---

## Octal (Base 8)

Octal is another number system.

Instead of using 16 symbols, it uses 8:

```text
0 1 2 3 4 5 6 7
```

Notice something missing?

```text
8
9
```

They don't exist in octal.

---

## Why Octal Exists

Long before hexadecimal became popular, programmers liked octal because:

```text
1 octal digit = 3 binary bits
```

Example:

```text
110101111
```

Split into groups of 3:

```text
110 101 111
```

Convert:

```text
110 = 6
101 = 5
111 = 7
```

Result:

```text
657
```

Today hex is used far more often, but octal still appears in a few places.

---

## Octal in C

Octal numbers begin with a leading zero.

```c
int x = 075;
```

Many beginners think:

```text
75
```

But C interprets it as octal.

Actual value:

```text
7 × 8 + 5

= 61
```

This is one of the oldest traps in C.

Even experienced programmers occasionally get caught by it.

---

## Unix Permissions

One place where octal is still extremely common is Linux permissions.

You've probably seen:

```bash
chmod 755 file
```

or

```bash
chmod 644 file
```

Those numbers are octal.

Example:

```text
755
```

means:

```text
rwx r-x r-x
```

You'll understand exactly how this works when you study bitwise operations.

---

## When Should I Use Hex vs Octal?

Use hexadecimal when:

* Reading memory
* Reading assembly
* Working with bit masks
* Looking at machine code
* Debugging programs

Use octal when:

* Working with Unix permissions
* Reading older C code
* Working with some embedded systems

In modern programming, hexadecimal is vastly more common.

---

## Things Worth Memorizing

```text
0xF  = 15
0xFF = 255
0xFFFF = 65535
```

And:

```text
1 hex digit = 4 bits
1 octal digit = 3 bits
```

If you remember only those facts, you're already ahead of most beginners.

---

## Practice

Convert these without a calculator:

```text
0xA
0x10
0x2A
0xFF
```

Convert these to hexadecimal:

```text
42
64
128
255
```

Convert these binary values:

```text
1010
11111111
101011110011
```

---

## Resources

### Read

* Beej's Guide to C
  https://beej.us/guide/bgc/

* CS50 Notes
  https://cs50.harvard.edu/x/

* Computer Systems: A Programmer's Perspective

* Code: The Hidden Language of Computer Hardware and Software

### Watch

* Ben Eater
  https://www.youtube.com/@BenEater

* Computerphile
  https://www.youtube.com/@Computerphile

* CS50 Harvard
  https://www.youtube.com/@cs50

### Practice

* https://integer.exposed/
* https://baseconvert.com/
* https://godbolt.org/
* https://hexed.it/

---

Next module:

```text
00_Binary_Number_Systems
01_Data_Types_And_Variables
02_Hexadecimal_And_Octal  ← You are here
03_Bitwise_Operators
```

Once hexadecimal starts feeling natural, bitwise operators become much easier to understand.
