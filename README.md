# C MASTERY COMPLETE

**From Zero to Systems Expert** — 500+ topics · 27 phases · Hardware to kernel · 1337 ready

![C](https://img.shields.io/badge/C-00599C?style=flat-square&logo=c&logoColor=white)
![Assembly](https://img.shields.io/badge/Assembly-6E4C13?style=flat-square&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![1337](https://img.shields.io/badge/1337-000000?style=flat-square&logo=42&logoColor=white)
![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)

---

## Visual Roadmap

![C Mastery Complete Roadmap](c_mastery_roadmap.svg)

---

## What Is This?

This repository is a self-driven, folder-by-folder learning framework for mastering C and low-level systems engineering from the ground up.

Every directory is an empty module. **You populate it** — your code, your notes, your implementations, your debugging labs. The roadmap above is the blueprint. This repo is the execution.

---

## The Learning Path

### Phase 00–02 — Hardware Foundations

Before writing a single line of C, you need to understand the machine underneath it. These phases cover everything the CPU actually does: how numbers are stored in binary, how the processor fetches and executes instructions, how registers and caches work, and how virtual memory maps to physical RAM. This is the layer most programmers skip — and the one that separates systems engineers from everyone else.

### Phase 03 — Assembly Language

Drop down to the metal. You write raw x86_64 instructions, manage the hardware stack yourself, and learn exactly what the compiler generates from your C code. Calling conventions, stack frames, SIMD registers — you understand them not from documentation but from writing them by hand.

### Phase 04 — C Language Core

The full C toolchain from preprocessor to binary. Types, scope, storage classes, pointers, functions, strings, macros, and the standard library. The focus here is on understanding what the compiler does with your code, not just writing code that compiles.

### Phase 05–07 — Memory Architecture & Pointers

The most important section for any serious C programmer. You map out the Text, Data, BSS, Stack, and Heap segments. You master multi-level pointer indirection, function pointers, void pointers, struct padding and alignment rules, and how memory allocators like `dlmalloc` and `jemalloc` actually work under the hood.

### Phase 08–12 — Systems Programming

This is where C meets the OS. You interact with the kernel directly through system calls: file descriptors, unbuffered I/O, `fork`/`exec`/`wait`, signal handling, named and unnamed pipes, shared memory, semaphores, and `mmap`. Then you add concurrency: POSIX threads, mutexes, condition variables, atomic operations, and race condition detection with TSan. Finally, network programming: TCP/UDP sockets, non-blocking I/O, and Linux `epoll` for high-performance multiplexing.

### Phase 13–14 — Data Structures & Algorithms

Built from scratch in C. Linked lists, stacks, queues, hash tables with collision resolution, BSTs, AVL trees, Red-Black trees, graphs, tries, segment trees, and union-find. Sorting algorithms analyzed for cache behavior. String matching with KMP and Rabin-Karp. Dynamic programming and greedy approaches with explicit time/space complexity bounds.

### Phase 15 — Debugging & Build Toolchains

You cannot write serious C without mastering your tools. Full GDB workflow, Valgrind memcheck and callgrind, `strace`/`ltrace` for syscall tracing, `perf` and flame graphs for performance profiling. Makefiles, CMake, static and shared libraries, `objdump`/`readelf` for binary inspection, and `gcov` for code coverage.

### Phase 16 — Optimization & Security

Cache-friendly data layout, loop unrolling, SIMD vectorization hints, PGO and LTO compiler passes, and lock-free programming with atomics. On the security side: stack buffer overflows, format string vulnerabilities, Return-Oriented Programming (ROP) chain construction, ASLR bypass techniques, stack canaries, and fuzzing with static analysis.

### Phase 17 — Linux Kernel & OS Internals

System call interface, context switching, the Completely Fair Scheduler, page cache, the SLUB allocator, VFS layer, ext4, writing and loading Linux Kernel Modules, procfs/sysfs, namespaces and cgroups for containerization, seccomp filtering, and kernel debugging with kgdb and ftrace.

### Phase 18 — Embedded Systems

Bare-metal ARM Cortex-M programming. GPIO, NVIC interrupt controllers, timers and PWM, ADC/DAC, UART/SPI/I2C/CAN bus communication. FreeRTOS task scheduling, bootloader development, JTAG debugging with OpenOCD, and OTA firmware update pipelines.

### Phase 19 — 1337 Piscine Projects

The full 42 Norm compliance workflow. Moulinette-ready implementations from C00 through C13, Rush00 and Rush01, custom `ft_printf`, linked list management, and build system projects. Everything tested against automated validators under strict style rules.

### Phases 20–24 — Practice, Exams & Real Projects

Coding challenges scaled from easy to hard, mock exam sandboxes timed to 1337 evaluation constraints, and production-grade project implementations: a POSIX mini-shell with pipelining, a multithreaded HTTP server, a custom `malloc` engine built on `mmap`, and a system monitor utility. The repository closes with curated reference cheat sheets for GDB, Valgrind, Makefiles, and the 42 Norm.

---

## Module Index

| # | Module | Key Topics |
|---|--------|------------|
| 00 | Binary & Number Systems | Binary, hex, two's complement, bitwise ops, endianness, IEEE 754 |
| 01 | CPU Architecture | x86/ARM, CISC vs RISC, pipelines, branch prediction, SIMD |
| 02 | Registers & Memory | Cache hierarchy, MESI, TLB, virtual memory, NUMA |
| 03 | Assembly Language | MOV/PUSH/POP, jumps, CALL/RET, stack frames, SSE/AVX |
| 04 | C Language Core | Toolchain, types, control flow, macros, standard library |
| 05 | Memory Management | Stack/heap layout, malloc/free, allocators, Valgrind, ASAN |
| 06 | Pointers | Arithmetic, double/triple pointers, function pointers, void* |
| 07 | Structs / Unions / Enums | Padding, packing, bit fields, opaque types |
| 08 | File I/O & Syscalls | File descriptors, open/read/write/close, dup2, sendfile |
| 09 | Process Management | fork/exec/wait, zombies, daemons, CPU affinity |
| 10 | Signals & IPC | Signals, pipes, shared memory, semaphores, mmap |
| 11 | Multithreading | pthreads, mutexes, condition vars, atomics, TSan |
| 12 | Network Programming | TCP/UDP sockets, select/poll/epoll, HTTP, TLS |
| 13 | Data Structures | Lists, trees (AVL/RB/B), hash tables, graphs, tries |
| 14 | Algorithms | Sorting, KMP, DP, greedy, backtracking, Dijkstra |
| 15 | Debugging & Build | GDB, Valgrind, strace, perf, flame graphs, Make/CMake |
| 16 | Optimization & Security | Cache layout, SIMD, buffer overflow, ROP, fuzzing |
| 17 | Linux Kernel & OS | Syscall layer, CFS, VFS, kernel modules, cgroups |
| 18 | Embedded Systems | ARM bare-metal, GPIO, FreeRTOS, JTAG, bootloaders |
| 19 | 1337 Piscine Projects | C00–C13, Rush00/01, ft_printf, 42 Norm compliance |
| 20 | Practice Problems | Easy/medium/hard challenges by topic |
| 21 | Exams & Evaluation | Mock exams, time management, norm violation list |
| 22 | Real World Projects | Mini shell, HTTP server, custom malloc, system monitor |
| 23 | Resources & References | Books, cheat sheets, man pages, GDB/Valgrind quick refs |
| 24 | Tools & Setup | GCC/Clang, GDB init, Valgrind profiles, Docker, Git |

---

## How to Use This Repo

1. Clone it locally
2. Make sure `c_mastery_roadmap.svg` sits in the root next to this file
3. Start at `00_Binary_Number_Systems/` and work forward
4. Add your own code, notes, and implementations to each folder as you go
5. Commit your progress regularly

```bash
git clone https://github.com/0xMedl/C-Mastery-Complete
cd C-Mastery-Complete
# Start learning — populate the modules as you go
```

---

> Built for mastering C, low-level engineering, systems programming, and the 1337/42 curriculum.
> Star the repo to track your journey.
