# Day 4 — Operating Systems (8 Items)

## 1. OS Overview

### What is an Operating System?
- **Intermediate** between hardware and user applications
- Manages resources: CPU, memory, I/O devices, files
- Provides: process management, memory management, file management, I/O management, security

### Types of Operating Systems
| Type | Description |
|------|-------------|
| **Batch** | Jobs collected in batch, processed sequentially (no interaction) |
| **Multiprogramming** | Multiple programs in memory; CPU switches to keep busy |
| **Multitasking** | CPU switches between processes so fast it appears simultaneous |
| **Multiprocessing** | Multiple CPUs/cores executing simultaneously |
| **Real-time** | Guaranteed response within deadlines (hard vs soft) |
| **Distributed** | Multiple connected computers appear as one |

### System Software vs Application Software
```
Which system software resides in main memory?
A. Executor
B. Compiler
C. Loader       ← ✓
D. Linker
```
- **Loader**: loads executable into memory (resides in memory)
- **Linker**: combines object files into executable (not in memory)
- **Compiler**: source → object code (not in memory)
- **Executor**: not a standard term

### Bootstrap Process
```
Which program initializes all aspects of the system from CPU registers 
to device controllers and main memory, then starts the OS?
A. Bootloader
B. BIOS
C. Bootstrap    ← ✓
D. Cache memory
```
- **Bootstrap**: small program stored in ROM that initializes hardware and loads OS kernel
- **Bootloader**: loads the OS (e.g., GRUB)
- **BIOS/UEFI**: firmware interface, runs POST and finds boot device
- Sequence: Power On → BIOS/UEFI → Bootstrap → Bootloader → OS Kernel

---

## 2. Process Management

### Process Definition
A **process** is a program in execution. It has:
- **Text section** (code)
- **Data section** (global variables)
- **Heap** (dynamic memory allocation)
- **Stack** (function calls, local variables)
- **Program Counter** (next instruction address)

### Process vs Program
| Program | Process |
|---------|---------|
| Passive (stored on disk) | Active (in memory + execution) |
| Static code | Dynamic (PC, registers, state) |
| One program → multiple processes | Each has own address space |

### Process Control Block (PCB)
The OS maintains a PCB for every process containing:
1. Process ID (PID)
2. Process state (Running, Ready, Blocked, etc.)
3. Program Counter
4. CPU registers
5. Memory limits
6. List of open files
7. Scheduling priority

### Process States

```
         ┌─────────────────┐
         │      NEW        │ (process created)
         └────────┬────────┘
                  ↓
         ┌─────────────────┐
    ┌─── │     READY       │ ←────────────┐
    │    └────────┬────────┘              │
    │             ↓ (scheduler dispatch)  │
    │    ┌─────────────────┐              │
    │    │    RUNNING      │              │
    │    └────────┬────────┘              │
    │             │                       │
    │    ┌────────┴────────┐              │
    │    ↓                 ↓              │
    │  [I/O or     [Timer interrupt      │
    │   event wait]   → preempted]        │
    │    ↓                 ↓              │
    │  BLOCKED          READY ────────────┘
    │    ↓ (I/O done)
    │  READY
    │
    └──→ TERMINATED
```

**Exam question**: When a process is in "Blocked" state waiting for I/O and the service completes, it goes to which state?

**Answer**: **Ready** (NOT Running — it must be scheduled again)

### Context Switch
- Saving state of current process and loading saved state of another
- Overhead: time spent switching is non-productive
- Context switch time is **pure overhead**

### Process Creation
- Parent creates child processes (tree hierarchy)
- `fork()` in Unix: creates child as copy of parent
- `exec()` : replaces process image with new program

---

## 3. CPU Scheduling

### Scheduling Objectives
- **Maximize**: CPU utilization, throughput
- **Minimize**: turnaround time, waiting time, response time

### Terminology
- **Turnaround time**: completion time - arrival time (total time in system)
- **Waiting time**: total time spent in Ready queue
- **Response time**: time from submission to first response
- **Throughput**: processes completed per unit time

### Scheduling Queues
| Queue | Purpose | Managed by |
|-------|---------|------------|
| **Job Queue** | All processes in system | Long-term scheduler |
| **Ready Queue** | In memory, ready to run | Short-term scheduler |
| **Device Queue** | Waiting for I/O device | I/O scheduler |

### Scheduler Types

| Scheduler | Frequency | Function |
|-----------|-----------|----------|
| **Long-term** (Job) | Low | Controls degree of multiprogramming |
| **Medium-term** | Medium | Swapping processes in/out of memory |
| **Short-term** (CPU) | Very high | Selects next process to execute |

**Exam question**: Which scheduler decides which available process will be executed by the processor?
- A. I/O scheduling
- B. **Short-term scheduling** ← ✓
- C. Long-term scheduling
- D. Medium-term scheduling

### Preemptive vs Non-Preemptive

| Non-Preemptive | Preemptive |
|----------------|------------|
| Process runs until it blocks or terminates | OS can interrupt process mid-execution |
| No context switch during execution | Timer interrupt forces context switch |
| Simpler, less overhead | Better responsiveness, fairness |

### Scheduling Algorithms

| Algorithm | Decision | Preemptive? | Starvation? | Characteristics |
|-----------|----------|-------------|-------------|-----------------|
| **FCFS** | Arrival order | No | No (convoy effect) | Simple, non-preemptive |
| **SJF** (Shortest Job First) | Shortest burst time next | No | Yes (long jobs starve) | Optimal avg waiting time |
| **SRTF** (Shortest Remaining Time First) | Shortest remaining time | Yes | Yes | Preemptive version of SJF |
| **Round Robin** | Fixed time quantum | Yes | No | Fair, good response time |
| **Priority** | Highest priority first | Can be | Yes (low priority) | Can combine with aging |
| **Multilevel Queue** | Process type determines queue | Per queue | Possible | Foreground/background |

### FCFS (First-Come, First-Served)
```java
// Non-preemptive
Process:    P1(24)  P2(3)  P3(3)  ← (burst times)
Order:      P1 → P2 → P3

Waiting time:  P1=0, P2=24, P3=27
Avg waiting:   (0+24+27)/3 = 17ms

// With different order:
Process:    P2(3)  P3(3)  P1(24)
Avg waiting:   (0+3+6)/3 = 3ms  ← much better!
```
**Convoy effect**: short processes stuck behind long process

### SJF (Shortest Job First)
```java
Process:    P1(6)  P2(8)  P3(7)  P4(3)
SJF order:  P4(3) → P1(6) → P3(7) → P2(8)

Waiting:    P4=0, P1=3, P3=9, P2=16
Avg:        (0+3+9+16)/4 = 7ms
```

### Round Robin
```java
Quantum = 4ms
Processes: P1(24), P2(3), P3(3)

Time 0-4:  P1 runs (remaining 20)
Time 4-7:  P2 runs (done, remaining 0)
Time 7-10: P3 runs (done)
Time 10-14: P1 runs (remaining 16)
... continues until P1 finishes at time 30

Wait times: P1=6, P2=4, P3=7
Avg wait: 5.67ms
```
- Quantum too large → degenerates to FCFS
- Quantum too small → too many context switches

### Priority Scheduling
- Can be preemptive or non-preemptive
- **Starvation**: low priority processes may never execute
- **Aging**: gradually increase priority of waiting processes to prevent starvation

### Multilevel Queue / Feedback
- Processes assigned to different queues based on type (system/interactive/batch)
- Each queue has own scheduling algorithm
- **Multilevel Feedback**: processes can move between queues

---

## 4. Process Synchronization

### Race Condition
- Multiple processes/threads access shared data concurrently
- Final result depends on execution order (unpredictable)

### Critical Section Problem
- **Critical section**: code segment where shared resources are accessed
- Requirements:
  1. **Mutual Exclusion**: only one process in critical section at a time
  2. **Progress**: if no process in CS, one waiting can enter
  3. **Bounded Waiting**: limited time before a waiting process enters

### Synchronization Tools

| Tool | Description |
|------|-------------|
| **Mutex** (Mutual Exclusion) | Lock resource. Only one thread can hold it. Operations: `lock()`, `unlock()` |
| **Semaphore** | Integer S accessed via `wait(S)` (decrement) and `signal(S)` (increment) |
| — Binary Semaphore | Like mutex (values 0 or 1) |
| — Counting Semaphore | Controls access to N resources |
| **Monitor** | High-level construct with condition variables |

### Semaphore Example
```java
semaphore mutex = 1;   // binary semaphore

// Process P1
wait(mutex);            // if mutex > 0, decrement and enter; else block
// critical section
signal(mutex);          // increment, wake up waiting process
```

### Deadlock in Synchronization
- Process A holds resource X, waits for Y
- Process B holds resource Y, waits for X
- Both blocked forever

---

## 5. Deadlock

### Deadlock Definition
> A set of processes is in deadlock if each process in the set is waiting for an event that can only be caused by another process in the set.

### Four Necessary Conditions (Coffman Conditions)
| Condition | Description |
|-----------|-------------|
| **1. Mutual Exclusion** | Resources cannot be shared (at least one resource held in non-sharable mode) |
| **2. Hold and Wait** | Process holds resources while waiting for additional ones |
| **3. No Preemption** | Resources cannot be forcefully taken from a process |
| **4. Circular Wait** | Circular chain of processes, each waiting for a resource held by the next |

All 4 must hold simultaneously for deadlock to occur.

### Deadlock Handling Strategies

| Strategy | Description |
|----------|-------------|
| **Prevention** | Ensure at least one of the 4 conditions never holds |
| **Avoidance** | OS knows future requests; uses Banker's Algorithm to avoid unsafe states |
| **Detection** | Allow deadlock, detect it, then recover |
| **Recovery** | Terminate processes or preempt resources |

### Banker's Algorithm
- **Deadlock avoidance** algorithm
- Modeled on how a banker deals with customers with credit lines
- Process must declare maximum resource needs in advance
- System checks if granting a request leads to **safe state**
- A state is **safe** if there exists a sequence where all processes can complete

```
Which statement is NOT addressing the Banker's Algorithm?
A. It considers each request before it occurs                    ← ✓ describes it
B. It is an extension of the deadlock detection algorithm        ← ✗ NOT correct
C. It is modeled on how a banker deals with customers            ← ✓ describes it
D. It is a scheduling algorithm                                  ← ✗ NOT correct
```
**Answer**: B and D are incorrect. But the question asks "not addressing" — B is wrong (it's avoidance, not an extension of detection). D is also technically wrong but the exam likely expects **B** as the primary incorrect statement.

### Deadlock Detection
- Allow deadlock to occur
- Detection algorithm (wait-for graph — if cycle exists, deadlock)
- Recovery: abort processes or preempt resources

### Resource Allocation Graph
- **Vertices**: processes (circles) and resources (rectangles)
- **Edges**: Request edge (P→R), Assignment edge (R→P)
- **Cycle** in graph → deadlock (if only one instance per resource type)

---

## 6. Memory Management

### Memory Hierarchy
```
Registers        ← fastest, smallest, most expensive
Cache (L1/L2/L3) ← fast, small
Main Memory      ← medium
Solid State Disk ← slow, large
Hard Disk        ← slowest, largest, cheapest
```

### Logical vs Physical Address
- **Logical address**: generated by CPU (virtual)
- **Physical address**: actual location in memory
- **MMU** (Memory Management Unit) maps logical → physical at runtime

### Memory Allocation

| Scheme | Description | Fragmentation |
|--------|-------------|---------------|
| **Contiguous** | Process allocated single contiguous block | External fragmentation |
| **Fixed Partitioning** | Memory divided into fixed-size partitions | Internal fragmentation |
| **Dynamic Partitioning** | Partitions created dynamically | External fragmentation |
| **Paging** | Process divided into pages; frames in memory | Internal (small) |
| **Segmentation** | Process divided into logical segments | External |

### Fragmentation
- **External**: free space exists but not contiguous enough
- **Internal**: allocated memory slightly larger than requested (waste within a partition)

### Paging
```
Logical address = Page number (p) + Offset (d)
Page table maps page → frame number
Physical address = Frame number + Offset
```

### Page Table Structure
```
Page 0 → Frame 3
Page 1 → Frame 7
Page 2 → Frame 1
...
```
- Each process has its own page table
- Page table stored in main memory (or TLB for fast access)

### TLB (Translation Lookaside Buffer)
- Small, fast cache in MMU
- Stores recently used page table entries
- **TLB hit**: address translation in 1 cycle
- **TLB miss**: must access page table in memory (slower)

### Page Size Trade-offs
| Small pages | Large pages |
|-------------|-------------|
| Less internal fragmentation | More internal fragmentation |
| Larger page tables | Smaller page tables |
| More I/O overhead | Less I/O overhead |

### Virtual Memory
- Allows execution of processes not fully in memory
- **Demand paging**: page loaded into memory only when needed
- Page fault occurs when accessed page is not in memory

### Page Replacement Algorithms
| Algorithm | Description | Belady's Anomaly? |
|-----------|-------------|-------------------|
| **FIFO** | Replace oldest page in memory | Yes (can have more frames → more faults) |
| **Optimal** (MIN) | Replace page that will be used farthest in future | No (ideal, not implementable) |
| **LRU** (Least Recently Used) | Replace page not used for longest time | No |
| **LFU** (Least Frequently Used) | Replace page with fewest references | No |

**Belady's Anomaly**: For FIFO, increasing number of frames can increase page faults!

### Replacement Policy
```
Which memory management policy decides which page or pages are 
to be supplanted when memory is full?
A. Cleaning policy
B. Load policy
C. Replacement policy     ← ✓
D. Fetch policy
```

### Thrashing
- Process spends more time paging than executing
- Caused by: too many processes in memory, insufficient frames per process
- Solution: Reduce degree of multiprogramming (working set model)

### Swapping
- Moving entire process between main memory and disk
- **Medium-term scheduler** handles swapping

---

## 7. File Systems

### File System Structure
```
Application → Logical File System → File Organization Module 
→ Basic File System → I/O Control → Devices
```

### File Allocation Methods
| Method | Description | Pros | Cons |
|--------|-------------|------|------|
| **Contiguous** | File stored in contiguous blocks | Fast sequential/random access | External fragmentation |
| **Linked** | Each block points to next | No fragmentation | Slow random access |
| **Indexed** | Index block has pointers to data blocks | Fast random access | Index block overhead |

### Free Space Management
| Technique | Description |
|-----------|-------------|
| **Bit Vector** | Bitmap with 1=free, 0=used |
| **Linked List** | Free blocks linked together |
| **Grouping** | Store addresses of n free blocks in first free block |
| **Counting** | Keep address + count of contiguous free blocks |

**Exam**: Modification of free-list → store addresses of n free blocks in first free block = **Grouping**

### Directory Structure
- **Single-level**: all files in one directory (simple, conflicts)
- **Two-level**: each user has own directory
- **Tree-structured**: hierarchical (current standard)
- **Acyclic graph**: shared subdirectories/symlinks

### Special File Systems
| FS | Description |
|----|-------------|
| **procfs** (`/proc`) | Virtual filesystem for kernel data structures (process info) |
| **sysfs** (`/sys`) | Exports hardware device info and kernel parameters |
| **tmpfs** | Temporary files in RAM |

**Exam**: Which file system can change kernel parameters at runtime using `sysctl` command?
- **procfs** (`/proc/sys` is where sysctl parameters live)

---

## 8. I/O Management

### I/O Hardware
- Devices: block (disk), character (keyboard), network
- Controllers: electronics that operate device
- Communication: port-mapped I/O, memory-mapped I/O

### I/O Methods
| Method | Description |
|--------|-------------|
| **Polling** | CPU repeatedly checks device status (busy-waiting) |
| **Interrupt-driven** | Device interrupts CPU when ready |
| **DMA** (Direct Memory Access) | Transfers data directly between device and memory without CPU involvement |

### Spooling
- Simultaneous Peripheral Operation On-Line
- Uses disk buffer to hold output for slow devices (printers)
- Multiple processes can send output; spooler queues them

---

## 9. System Calls & OS Structure

### System Calls
- Interface between user programs and OS kernel
- Types: Process control, File management, Device management, Information maintenance, Communication

### OS Structure Models
| Model | Description | Examples |
|-------|-------------|----------|
| **Monolithic** | Entire OS in kernel space | Linux (traditional) |
| **Microkernel** | Minimal kernel; services run in user space | Minix, QNX |
| **Layered** | OS divided into layers (bottom=hardware, top=user) | |
| **Modular** | Loadable kernel modules | Linux (modern) |

---

## Exam-Style Practice Questions

### Q1: Process State Transition
When a blocked process completes its I/O operation, it moves to:
- A. Running
- B. **Ready** ← ✓ (it needs scheduler dispatch)
- C. Terminated
- D. Suspended

---

### Q2: Scheduler Type
Which scheduler decides which available process will be executed by the processor?
- A. I/O scheduling
- B. **Short-term scheduling** ← ✓
- C. Long-term scheduling
- D. Medium-term scheduling

---

### Q3: Deadlock — All 4 Conditions
Which is NOT a necessary condition for deadlock?
- A. Mutual exclusion
- B. Hold and wait
- C. **Preemption** ← ✓ (it's "NO preemption" that's required)
- D. Circular wait

---

### Q4: Banker's Algorithm
Which statement is NOT correct about Banker's Algorithm?
- A. It considers each request before granting it
- B. It is an extension of deadlock detection ← ✗
- C. It is modeled on banker dealing with customers
- D. It prevents deadlock by avoiding unsafe states

**Answer**: B

---

### Q5: Memory Replacement
Which policy decides which page to remove when memory is full?
- A. **Replacement policy** ← ✓
- B. Load policy
- C. Fetch policy
- D. Cleaning policy

---

### Q6: Page Replacement — Belady's Anomaly
Which algorithm suffers from Belady's Anomaly (more frames → more faults)?
- A. LRU
- B. Optimal
- C. **FIFO** ← ✓
- D. LFU

---

### Q7: Bootstrap
Which program initializes CPU registers, device controllers, main memory, then starts the OS?
- A. Bootloader
- B. BIOS
- C. **Bootstrap** ← ✓
- D. Cache memory

---

### Q8: Free Space Management
Modification of free-list approach: store addresses of n free blocks in first free block = ?
- A. Counting
- B. Linked-list
- C. **Grouping** ← ✓
- D. Deadlock

---

### Q9: System Software in Memory
Which system software resides in main memory?
- A. Executor
- B. Compiler
- C. **Loader** ← ✓
- D. Linker

---

### Q10: File System for Kernel Parameters
Which file system can change kernel parameters at runtime using sysctl?
- A. ext4
- B. **procfs** ← ✓
- C. ext3
- D. sysfs

---

### Q11: Scheduling — Round Robin
Processes: P1=10ms, P2=5ms, P3=2ms. Quantum=4ms. What is avg waiting time?

```
Time 0-4: P1 (remaining 6)
Time 4-8: P2 (remaining 1)
Time 8-10: P3 (remaining 0, done at 10)
Time 10-14: P1 (remaining 2)
Time 14-15: P2 (remaining 0, done at 15)
Time 15-17: P1 (remaining 0, done at 17)

Waiting: P1=7, P2=9, P3=8
Avg: (7+9+8)/3 = 8ms
```

---

### Q12: Deadlock Detection
What does a cycle in a Resource Allocation Graph indicate?
- A. No deadlock
- B. **Possible deadlock** ← ✓ (if only one instance per resource type, cycle = deadlock)
- C. Starvation
- D. Thrashing

---

### Q13: Context Switch
Context switching is:
- A. Always beneficial
- B. **Pure overhead** ← ✓
- C. Only used in batch systems
- D. Eliminates need for scheduling

---

### Q14: Virtual Memory
Virtual memory allows:
- A. Running programs larger than physical memory ← ✓
- B. Eliminating page faults
- C. Removing need for MMU
- D. Faster than physical memory

---

### Q15: Thrashing
Thrashing occurs when:
- A. CPU is idle for too long
- B. **Process spends more time paging than executing** ← ✓
- C. Deadlock occurs
- D. File system is corrupted

**Solution**: Reduce degree of multiprogramming

---

### Q16: Semaphore
A binary semaphore can take values:
- A. Only 0
- B. Only 1
- C. **0 or 1** ← ✓
- D. Any integer

---

### Q17: Critical Section Requirements
Which is NOT a requirement for critical section solution?
- A. Mutual exclusion
- B. **Maximum throughput** ← ✓
- C. Progress
- D. Bounded waiting

---

### Q18: FCFS Convoy Effect
Convoy effect in FCFS scheduling means:
- A. Short processes execute first
- B. **Short processes wait for long process to finish** ← ✓
- C. All processes finish simultaneously
- D. No process executes

---

## Quick Reference Card

```
PROCESS STATES: New → Ready → Running → [Blocked | Ready] → Terminated
Blocked→Ready (NOT Running) when I/O completes

SCHEDULING:
  FCFS:      First come, first served (convoy effect)
  SJF:       Shortest job first (optimal avg wait, starvation)
  Round Robin: Time quantum (fair, context switch overhead)
  Priority:  Can starve (aging fixes it)

DEADLOCK: 4 conditions: Mutual Exclusion, Hold&Wait, No Preemption, Circular Wait
  Prevention: break one condition
  Avoidance: Banker's Algorithm (safe state)
  Detection: wait-for graph (cycle = deadlock)

MEMORY:
  Paging:    Fixed size pages, no external fragmentation
  Segments:  Variable size, logical divisions
  Page Replacement: FIFO (Belady's anomaly), LRU, Optimal (not realizable)
  Thrashing: Too much paging → reduce multiprogramming

SYSTEM SOFTWARE:
  Compiler:  source → object
  Linker:    object → executable
  Loader:    executable → memory

BOOT SEQUENCE:
  Power On → BIOS/UEFI → Bootstrap → Bootloader → OS Kernel
```
