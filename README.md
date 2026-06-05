<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
  body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'SF Pro Text', 'SF Pro Display', 'Helvetica Neue', sans-serif;
    background: linear-gradient(135deg, #0a0e27 0%, #1a1f3a 100%);
    padding: 40px 20px;
    color: #e0e0e0;
  }
  .container {
    max-width: 1400px;
    margin: 0 auto;
  }
  h1 {
    text-align: center;
    font-size: 3.5em;
    background: linear-gradient(135deg, #00d4ff, #7c3aed, #ff6b35);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    margin-bottom: 10px;
    text-shadow: 0 0 30px rgba(0,212,255,0.3);
  }
  .subtitle {
    text-align: center;
    font-size: 1.3em;
    color: #a0a0c0;
    margin-bottom: 50px;
  }
  .badge-container {
    text-align: center;
    margin-bottom: 40px;
  }
  .badge {
    display: inline-block;
    padding: 8px 16px;
    margin: 5px;
    border-radius: 20px;
    font-weight: bold;
  }
  .roadmap-level {
    margin-bottom: 60px;
    position: relative;
  }
  .level-title {
    font-size: 2em;
    font-weight: bold;
    margin-bottom: 25px;
    padding-left: 20px;
    border-left: 8px solid;
    border-image: linear-gradient(180deg, #00d4ff, #7c3aed);
    border-image-slice: 1;
  }
  .level-0 .level-title { border-left-color: #00b4d8; }
  .level-1 .level-title { border-left-color: #48cae4; }
  .level-2 .level-title { border-left-color: #90e0ef; }
  .level-3 .level-title { border-left-color: #fca311; }
  .level-4 .level-title { border-left-color: #ff6b35; }
  .level-5 .level-title { border-left-color: #7c3aed; }
  
  .module-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 25px;
    justify-content: center;
  }
  .module-card {
    background: rgba(20, 25, 55, 0.8);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    padding: 20px;
    width: 320px;
    transition: transform 0.3s, box-shadow 0.3s;
    border: 1px solid rgba(0,212,255,0.2);
  }
  .module-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 20px 40px rgba(0,212,255,0.2);
    border-color: #00d4ff;
  }
  .module-icon {
    font-size: 2.5em;
    margin-bottom: 10px;
  }
  .module-title {
    font-size: 1.3em;
    font-weight: bold;
    margin-bottom: 12px;
    color: #00d4ff;
  }
  .module-subtopics {
    font-size: 0.85em;
    color: #b0b0d0;
    line-height: 1.5;
    margin-top: 10px;
    padding-top: 10px;
    border-top: 1px solid rgba(255,255,255,0.1);
  }
  .arrow-down {
    text-align: center;
    font-size: 2.5em;
    margin: 20px 0;
    animation: bounce 2s infinite;
    color: #00d4ff;
  }
  @keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(15px); }
  }
  .progress-tracker {
    background: rgba(0,0,0,0.4);
    border-radius: 30px;
    padding: 20px;
    margin-top: 50px;
    text-align: center;
  }
  .progress-steps {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 15px;
  }
  .step {
    background: #1a1f3a;
    border-radius: 40px;
    padding: 12px 24px;
    font-size: 0.9em;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s;
    border: 2px solid transparent;
  }
  .step.completed {
    background: linear-gradient(135deg, #00d4ff, #00a8cc);
    color: #000;
  }
  .step.current {
    border-color: #ff6b35;
    animation: pulse 1.5s infinite;
  }
  @keyframes pulse {
    0%, 100% { box-shadow: 0 0 0 0 rgba(255,107,53,0.4); }
    50% { box-shadow: 0 0 0 10px rgba(255,107,53,0); }
  }
  .step:hover {
    transform: scale(1.05);
  }
  .visual-arrow {
    font-size: 3em;
    text-align: center;
    color: #ff6b35;
    margin: 10px 0;
  }
  hr {
    border: none;
    height: 2px;
    background: linear-gradient(90deg, transparent, #00d4ff, #7c3aed, #ff6b35, transparent);
    margin: 40px 0;
  }
</style>
</head>
<body>
<div class="container">

  <h1>🚀 C MASTERY COMPLETE</h1>
  <div class="subtitle">🎯 Your Visual Roadmap from Zero to Systems Expert</div>
  
  <div class="badge-container">
    <span class="badge" style="background:#00599C;">⚡ C Language</span>
    <span class="badge" style="background:#6E4C13;">🔧 Assembly</span>
    <span class="badge" style="background:#FCC624; color:#000;">🐧 Linux</span>
    <span class="badge" style="background:#7c3aed;">🎓 1337</span>
    <span class="badge" style="background:#0066CC;">💾 Embedded</span>
    <span class="badge" style="background:#ff6b35;">🔐 Security</span>
  </div>

  <hr>

  <!-- LEVEL 0 -->
  <div class="roadmap-level level-0">
    <div class="level-title">📗 LEVEL 0: DIGITAL FUNDAMENTALS</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">🔢</div>
        <div class="module-title">00_Binary_Number_Systems</div>
        <div class="module-subtopics">Binary • Hexadecimal • Two's Complement • Bitwise Ops • Endianness • IEEE754</div>
      </div>
      <div class="module-card">
        <div class="module-icon">💻</div>
        <div class="module-title">01_CPU_Architecture</div>
        <div class="module-subtopics">x86/ARM • RISC vs CISC • Pipelines • Branch Prediction • SIMD • Microarchitecture</div>
      </div>
      <div class="module-card">
        <div class="module-icon">🧠</div>
        <div class="module-title">02_Registers_Memory</div>
        <div class="module-subtopics">General/Special Registers • Cache Hierarchy • MESI • TLB • Virtual Memory • NUMA</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 1 -->
  <div class="roadmap-level level-1">
    <div class="level-title">⚙️ LEVEL 1: ASSEMBLY LANGUAGE</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">🛠️</div>
        <div class="module-title">03_Assembly_Language</div>
        <div class="module-subtopics">MOV • PUSH/POP • Arithmetic • Jumps • CALL/RET • SIMD (SSE/AVX) • Stack Frames • Calling Conventions • NASM/objdump/GDB</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 2 -->
  <div class="roadmap-level level-2">
    <div class="level-title">💎 LEVEL 2: C LANGUAGE CORE</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">📝</div>
        <div class="module-title">04_C_Language_Core</div>
        <div class="module-subtopics">Compilation Process • Data Types • Operators • Control Flow • Functions • Arrays • Strings • Preprocessor • Header Files • Standard Library</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 3 -->
  <div class="roadmap-level level-3">
    <div class="level-title">🎯 LEVEL 3: MEMORY & POINTERS</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">📍</div>
        <div class="module-title">05_Memory_Management</div>
        <div class="module-subtopics">Memory Layout (Text/Data/BSS/Stack/Heap) • malloc/calloc/realloc/free • Allocators (dlmalloc/jemalloc) • Fragmentation • Valgrind • ASAN/MSan</div>
      </div>
      <div class="module-card">
        <div class="module-icon">🪡</div>
        <div class="module-title">06_Pointers</div>
        <div class="module-subtopics">Address-of & Dereference • Pointer Arithmetic • Double/Triple Pointers • Function Pointers • Void Pointers • Self-referential Structs</div>
      </div>
      <div class="module-card">
        <div class="module-icon">🏗️</div>
        <div class="module-title">07_Structs_Unions_Enums</div>
        <div class="module-subtopics">Struct Padding & Packing • Bit Fields • Unions (memory sharing) • Enums • typedef • Opaque Types</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 4 -->
  <div class="roadmap-level level-4">
    <div class="level-title">🔧 LEVEL 4: SYSTEMS PROGRAMMING</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">💾</div>
        <div class="module-title">08_File_IO_System_Calls</div>
        <div class="module-subtopics">File Descriptors • open/read/write/close • lseek • dup/dup2 • stat • Directory Ops • sendfile (zero-copy)</div>
      </div>
      <div class="module-card">
        <div class="module-icon">🔄</div>
        <div class="module-title">09_Process_Management</div>
        <div class="module-subtopics">fork() • exec() • wait() • Zombies/Orphans • Daemons • Process Groups • CPU Affinity</div>
      </div>
      <div class="module-card">
        <div class="module-icon">📡</div>
        <div class="module-title">10_Signals_IPC</div>
        <div class="module-subtopics">Signals (SIGINT/SIGKILL) • Pipes (named/unnamed) • Shared Memory • Message Queues • Semaphores • mmap()</div>
      </div>
      <div class="module-card">
        <div class="module-icon">🧵</div>
        <div class="module-title">11_Multithreading</div>
        <div class="module-subtopics">pthread_create/join • Mutexes • Condition Variables • RW Locks • Race Conditions • Deadlocks • Thread Pools • TSan</div>
      </div>
      <div class="module-card">
        <div class="module-icon">🌐</div>
        <div class="module-title">12_Network_Programming</div>
        <div class="module-subtopics">Sockets (TCP/UDP) • bind/listen/accept • send/recv • select/poll/epoll • Non-blocking I/O • HTTP • TLS/SSL</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 5 -->
  <div class="roadmap-level level-5">
    <div class="level-title">📊 LEVEL 5: DATA STRUCTURES & ALGORITHMS</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">📚</div>
        <div class="module-title">13_Data_Structures</div>
        <div class="module-subtopics">Big O • Linked Lists • Stacks/Queues • Trees (BST/AVL/Red-Black/B-Tree) • Hash Tables • Graphs • Tries • Segment/Fenwick Trees • Union-Find</div>
      </div>
      <div class="module-card">
        <div class="module-icon">⚡</div>
        <div class="module-title">14_Algorithms</div>
        <div class="module-subtopics">Sorting (Merge/Quick/Heap/Radix) • Binary Search • KMP/Boyer-Moore • Dynamic Programming • Greedy • Backtracking • Dijkstra • Bit Manipulation</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 6 -->
  <div class="roadmap-level level-0">
    <div class="level-title">🐛 LEVEL 6: DEBUGGING & PROFILING</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">🔍</div>
        <div class="module-title">15_Debugging_Profiling_Build</div>
        <div class="module-subtopics">GDB (complete) • Valgrind (memcheck/callgrind) • strace/ltrace • perf • Flame Graphs • Makefiles • CMake • Static/Dynamic Libs • objdump/readelf • gcov</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 7 -->
  <div class="roadmap-level level-4">
    <div class="level-title">🔐 LEVEL 7: OPTIMIZATION & SECURITY</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">⚡</div>
        <div class="module-title">16_Optimization_Security</div>
        <div class="module-subtopics">Cache-friendly Code • Loop Optimization • Branch Prediction • SIMD Optimization • Compiler Flags (O0-O3/PGO) • Lock-free Programming • Buffer Overflow • ROP • Canary Values • Secure Coding • Fuzzing</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 8 -->
  <div class="roadmap-level level-1">
    <div class="level-title">🐧 LEVEL 8: LINUX KERNEL & OS</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">⚙️</div>
        <div class="module-title">17_Linux_Kernel_and_OS</div>
        <div class="module-subtopics">Kernel Architecture • System Calls • Context Switching • CFS Scheduler • Page Cache • SLUB Allocator • VFS • ext4 • Device Drivers • Kernel Modules • cgroups/namespaces • seccomp • kgdb/ftrace</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 9 -->
  <div class="roadmap-level level-2">
    <div class="level-title">🔌 LEVEL 9: EMBEDDED SYSTEMS</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">📟</div>
        <div class="module-title">18_Embedded_Systems</div>
        <div class="module-subtopics">ARM Cortex-M/AVR • GPIO • Interrupts (NVIC) • Timers/PWM • ADC/DAC • UART/SPI/I2C/CAN • FreeRTOS • Bare Metal • Bootloaders • JTAG/OpenOCD • OTA Updates</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 10 -->
  <div class="roadmap-level level-3">
    <div class="level-title">🎓 LEVEL 10: 1337 PISCINE PROJECTS</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">🏊</div>
        <div class="module-title">19_1337_Piscine_Projects</div>
        <div class="module-subtopics">42 Norm Rules • Moulinette • C00-C13 • Rush00/Rush01 • Custom printf • Linked Lists • Build Systems • File Ops • Function Pointers</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 11 -->
  <div class="roadmap-level level-4">
    <div class="level-title">💪 LEVEL 11: PRACTICE & EXAMS</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">📝</div>
        <div class="module-title">20_Practice_Problems</div>
        <div class="module-subtopics">Easy/Medium/Hard Problems • Arrays/Strings • Pointers/Memory • Data Structures • Algorithms • System Programming • Interview Questions</div>
      </div>
      <div class="module-card">
        <div class="module-icon">📋</div>
        <div class="module-title">21_Exams_Evaluation</div>
        <div class="module-subtopics">Exam Format • Common Problems • Time Management • Norm Violations • Previous Questions • Mock Exams</div>
      </div>
    </div>
  </div>

  <div class="visual-arrow">⬇️ ⬇️ ⬇️</div>

  <!-- LEVEL 12 -->
  <div class="roadmap-level level-5">
    <div class="level-title">🚀 LEVEL 12: REAL WORLD PROJECTS</div>
    <div class="module-grid">
      <div class="module-card">
        <div class="module-icon">🛠️</div>
        <div class="module-title">22_Real_World_Projects</div>
        <div class="module-subtopics">Mini Shell • HTTP Server • Custom malloc • File Manager • System Monitor • Network Utilities</div>
      </div>
      <div class="module-card">
        <div class="module-icon">📚</div>
        <div class="module-title">23_Resources_References</div>
        <div class="module-subtopics">Books • Courses • YouTube Channels • Man Pages • Cheat Sheets • GDB/Valgrind Cheatsheets • Makefile Templates • 42 Norm Cheatsheet</div>
      </div>
      <div class="module-card">
        <div class="module-icon">⚙️</div>
        <div class="module-title">24_Tools_Setup</div>
        <div class="module-subtopics">GCC/Clang • GDB • Valgrind • Docker • Git Workflow • Editor/IDE Config</div>
      </div>
    </div>
  </div>

  <hr>

  <!-- PROGRESS TRACKER -->
  <div class="progress-tracker">
    <h3 style="margin-bottom: 20px;">🎯 Track Your Progress</h3>
    <div class="progress-steps">
      <div class="step completed">✅ Fundamentals</div>
      <div class="step">⬜ Assembly</div>
      <div class="step">⬜ C Core</div>
      <div class="step">⬜ Memory</div>
      <div class="step">⬜ Pointers</div>
      <div class="step">⬜ Systems</div>
      <div class="step">⬜ Threads</div>
      <div class="step">⬜ Network</div>
      <div class="step">⬜ DS/Algo</div>
      <div class="step">⬜ Debugging</div>
      <div class="step">⬜ Security</div>
      <div class="step">⬜ Kernel</div>
      <div class="step">⬜ Embedded</div>
      <div class="step">⬜ 1337</div>
      <div class="step">⬜ Projects</div>
    </div>
    <p style="margin-top: 20px; font-size: 0.9em; opacity: 0.7;">⭐ Click on steps to mark your progress (local storage)</p>
  </div>

  <hr>

  <div style="text-align: center; margin-top: 50px; padding: 30px; background: rgba(0,212,255,0.1); border-radius: 20px;">
    <p style="font-size: 1.5em;">🎯 <strong>Each folder is a learning module</strong> — YOU add the code, notes, and resources!</p>
    <p style="margin-top: 15px;">⭐ Star this repo to save your journey from Zero to Systems Expert! ⭐</p>
  </div>

</div>

<script>
  // Progress tracker functionality
  const steps = document.querySelectorAll('.step');
  steps.forEach(step => {
    step.addEventListener('click', function() {
      if (this.classList.contains('completed')) {
        this.classList.remove('completed');
        this.innerHTML = this.innerHTML.replace('✅', '⬜');
      } else {
        this.classList.add('completed');
        this.innerHTML = this.innerHTML.replace('⬜', '✅');
      }
    });
  });
</script>

</body>
</html>
