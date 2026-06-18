# Day 4 — Operating Systems (97 Items)

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


## Practice Questions (from Question Bank)

Answer: A
### Q647. Which scheduling can cause starvation?

- A) FCFS
- B) Priority Scheduling
- C) SJF
- D) Round Robin
  **Answer: B**

### Q648. Consider a system where four necessary deadlock conditions?

- A) Mutual Exclusion, Hold-Wait, No Preemption, Circular Wait
- B) Hold-Wait, Starvation, Priority Inversion, No Preemption
- C) Mutual Exclusion, Preemption, Sharing, Circular
- D) Preemption, Hold-Wait, Circular, Starvation
  **Answer: A**

### Q649. How is Internal fragmentation best characterized?

- A) Allocated block larger than needed
- B) Pages of different sizes
- C) OS memory overlaps user
- D) Free memory is scattered
  **Answer: A**

### Q650. In which scenario would is be employed?

- A) Storing disk blocks
- B) Storing PCBs
- C) Buffering I/O
- D) Caching page table
  **Answer: D**

### Q651. In a resource-constrained environment, how is Thrashing best characterized?

- A) Too many system calls
- B) Process spending more time
- C) OS overwriting user memory
- D) Disk fragmentation
  **Answer: B**

### Q652. Optimal page replacement replaces page?

- A) Added earliest
- B) Not used for longest future time
- C) Accessed most recently
- D) Least recently used
  **Answer: B**

### Q653. Process vs Thread?

- A) Process has own memory space
- B) Threads are heavier
- C) Thread has own memory
- D) Process can have one thread only
  **Answer: D**

### Q654. When designing for high performance, round Robin too-small quantum causes?

- A) Excessive context switch
- B) Degrades to FCFS
- C) Starvation
- D) Priority given to short
  **Answer: A**

### Q655. System call is?

- A) User app function
- B) Hardware interrupt
- C) Compiler directive
- D) Interface for user
  **Answer: D**

### Q656. Banker's Algorithm does?

- A) Ignores deadlock
- B) Detects deadlocks
- C) Prevents by eliminating
- D) Avoids deadlock by only
  **Answer: D**

### Q657. When designing for high performance, fCFS scheduling: main problem?

- A) Starvation of all processes
- B) Requires burst time
- C) Complex to implement
- D) Convoy effect — long jobs
  **Answer: D**

### Q658. SJF advantage?

- A) Optimal average waiting time
- B) No burst time needed
- C) Fair to all processes
- D) Preemptive always
  **Answer: A**

### Q659. Which of the following best describes Process Control Block (PCB)?

- A) Memory page table
- B) Data structure storing all
- C) File descriptor table
- D) Physical CPU register
  **Answer: B**

### Q660. When designing for high performance, process states in order?

- A) Ready, Running, New, Waiting, Terminated
- B) New, Running, Ready, Waiting, Terminated
- C) New, Ready, Running, Waiting, Terminated
- D) Running, Ready, New, Terminated, Waiting
  **Answer: A**

### Q661. Identify the correct statement about context switching.

- A) Changing process priority
- B) Saving state of one process
- C) Switching CPU cores
- D) Changing memory pages
  **Answer: B**

### Q662. Identify the correct statement about monolithic kernel.

- A) Kernel with minimal services
- B) Kernel loaded at startup only
- C) Distributed kernel
- D) Kernel where all OS services run in
  **Answer: D**

### Q663. Consider a system where which of the following best describes microkernel?

- A) Kernel on embedded systems
- B) Very small application
- C) Minimal kernel
- D) Kernel with small memory footprint
  **Answer: C**

### Q664. Which description of virtual memory is accurate?

- A) Cache memory
- B) RAM on GPU
- C) Technique allowing
- D) Virtual machine memory
  **Answer: C**

### Q665. Page table maps?

- A) Files to memory
- B) Processes to pages
- C) Physical to logical
- D) Logical page numbers to
  **Answer: D**

### Q666. Consider a system where which description of external fragmentation is accurate?

- A) Disk fragmentation
- B) Allocated memory larger
- C) Memory outside RAM
- D) Free memory scattered in
  **Answer: D**

### Q667. Paging solves which fragmentation?

- A) Neither
- B) External fragmentation
- C) Internal fragmentation
- D) Both types
  **Answer: B**

### Q668. Identify the correct statement about demand paging.

- A) Pages pre-fetched ahead of use
- B) Pages loaded into RAM only when accessed
- C) User requests specific pages
- D) Pages loaded all at once
  **Answer: B**

### Q669. When designing for high performance, page fault occurs when?

- A) Page table is full
- B) Page is in RAM
- C) Process accesses page
- D) TLB miss always
  **Answer: C**

### Q670. LRU page replacement replaces?

- A) Page not used for longest
- B) Oldest page
- C) Page not used for longest
- D) Most recently used
  **Answer: A**

### Q671. FIFO page replacement?

- A) Removes most recently loaded page
- B) Removes page loaded first
- C) Removes page with no references
- D) Removes least used page
  **Answer: B**

### Q672. Consider a system where belady's anomaly affects which algorithm?

- A) FIFO
- B) LRU
- C) Optimal
- D) Clock
  **Answer: A**

### Q673. Which of the following best describes semaphore?

- A) OS scheduling unit
- B) Page replacement algorithm
- C) Synchronization variable
- D) Signal flag in networking
  **Answer: C**

### Q674. Binary semaphore vs counting semaphore?

- A) No difference
- B) Counting is 0
- C) Binary allows multiple
- D) Binary is 0
  **Answer: B**

### Q675. Consider a system where identify the correct statement about mutex.

- A) Multiple-use text
- B) Memory unit extension
- C) Multi-user text system
- D) Mutual exclusion lock
  **Answer: D**

### Q676. Which description of race condition is accurate?

- A) Outcome depends on
- B) Priority inversion
- C) Deadlock variant
- D) CPU scheduling algorithm
  **Answer: A**

### Q677. Critical section is?

- A) Code segment accessing shared resource
- B) Most important OS code
- C) Memory-protected region
- D) Kernel interrupt handler
  **Answer: A**

### Q678. When designing for high performance, which description of priority inversion is accurate?

- A) Scheduling by reverse priority
- B) High-priority task blocked by
- C) Lower priority task runs first
- D) Priority of processes reverses
  **Answer: B**

### Q679. Identify the correct statement about ging in scheduling.

- A) Processes get older
- B) Gradually increasing
- C) Removing old processes
- D) Time-based scheduling
  **Answer: B**

### Q680. Which of the following best describes Ostrich algorithm for deadlock?

- A) Detects via resource graph
- B) Complex detection algorithm
- C) Prevents by resource ordering
- D) Ignore deadlock and hope it doesn't happen
  **Answer: D**

### Q681. Which statement about Circular wait condition in deadlock is correct?

- A) Processes run in circles
- B) CPU scheduling cycle
- C) Chain of processes each
- D) Page replacement cycle
  **Answer: C**

### Q682. How can Hold-and-Wait be eliminated for deadlock prevention?

- A) Using priority scheduling
- B) Allowing preemption
- C) Allowing resource sharing
- D) Requiring process to request all
  **Answer: D**

### Q683. Which of the following best describes preemption in scheduling?

- A) Process voluntarily releases CPU
- B) Process waiting for I/O
- C) Process requests more CPU
- D) OS forcibly removes CPU from
  **Answer: D**

### Q684. In a resource-constrained environment, dMA (Direct Memory Access) allows?

- A) Memory to self-organize
- B) Device to transfer data directly
- C) CPU to access memory faster
- D) Multiple CPUs to share memory
  **Answer: B**

### Q685. Which description of disk scheduling SCAN algorithm is accurate?

- A) Services nearest request first
- B) Disk arm moves in one direction
- C) Scans disk for errors
- D) Services requests in FCFS order
  **Answer: C**

### Q686. SSTF disk scheduling?

- A) FIFO for disk
- B) Earliest deadline first
- C) Services request with
- D) Elevator algorithm
  **Answer: C**

### Q687. In a resource-constrained environment, which description of interrupt-driven I/O is accurate?

- A) Software triggers I/O
- B) DMA manages all I/O
- C) CPU polls device repeatedly
- D) Device notifies CPU via
  **Answer: D**

### Q688. Which description of spooling is accurate?

- A) Thread scheduling technique
- B) Memory paging
- C) CPU context switching
- D) Buffering data for device
  **Answer: D**

### Q689. Which description of kernel's privilege mode is accurate?

- A) Privileged/supervisor
- B) Guest mode in VM
- C) Admin user account
- D) User mode with extra RAM
  **Answer: A**

### Q690. When designing for high performance, which description of thread pool is accurate?

- A) Queue of blocked threads
- B) Pre-created set of threads
- C) Memory pool for threads
- D) Collection of CPU cores
  **Answer: B**

### Q691. Which of the following best describes multi-programming?

- A) Multiple users simultaneously
- B) Multiple CPUs
- C) Using multiple programming languages
- D) Multiple processes in memory
  **Answer: D**

### Q692. Which of the following best describes time-sharing OS?

- A) OS shared between computers
- B) Multiple users share CPU via
- C) Real-time OS
- D) OS based on time zones
  **Answer: B**

### Q693. Consider a system where identify the correct statement about real-time OS (RTOS).

- A) OS running at real-time
- B) OS with live updates
- C) Multi-user OS
- D) OS guaranteeing tasks
  **Answer: A**

### Q694. Which of the following best describes memory-mapped I/O?

- A) All I/O goes through memory
- B) Device registers mapped to
- C) RAM used instead of I/O
- D) Memory used as disk cache
  **Answer: B**

### Q695. Identify the correct statement about logical vs physical address.

- A) No difference
- B) Both are same in virtual memory
- C) Physical is CPU-generated
- D) Logical is CPU-generated
  **Answer: D**

### Q696. Which of the following best describes segmentation in memory?

- A) Network segmentation
- B) Divides memory into fixed
- C) Disk partitioning
- D) Divides process into
  **Answer: A**

### Q697. Which of the following best describes working set of a process?

- A) Pages currently in RAM
- B) Set of pages actively used
- C) Pages on disk
- D) All memory ever used
  **Answer: B**

### Q698. Thrashing prevention technique?

- A) Increase page size
- B) Disable virtual memory
- C) Reduce number of processes
- D) Use working set model to
  **Answer: D**

### Q699. Identify the correct statement about cooperative multitasking.

- A) OS forcibly preempts processes
- B) Processes help each other
- C) Multiple CPUs cooperate
- D) Processes voluntarily yield CPU
  **Answer: D**

### Q700. Which of the following best describes preemptive multitasking?

- A) Processes yield voluntarily
- B) Cooperative scheduling
- C) Priority-based voluntary yield
- D) OS forcibly preempts processes
  **Answer: D**

### Q701. Fork() system call in Unix?

- A) Terminates process
- B) Opens a file
- C) Switches process context
- D) Creates child process as
  **Answer: D**

### Q702. Consider a system where exec() system call?

- A) Executes SQL query
- B) Terminates process
- C) Replaces current process
- D) Creates child process
  **Answer: A**

### Q703. Which description of zombie process is accurate?

- A) Process waiting for I/O
- B) Process consuming excessive CPU
- C) Terminated process whose entry
- D) Process in infinite loop
  **Answer: C**

### Q704. Which of the following best describes orphan process?

- A) Process whose parent
- B) Process with no children
- C) System process
- D) Background process
  **Answer: A**

### Q705. When designing for high performance, which description of daemon process is accurate?

- A) Background process
- B) Child process
- C) Real-time process
- D) Malicious process
  **Answer: A**

### Q706. Identify the correct statement about inter-process communication (IPC).

- A) Mechanisms for processes to exchange data
- B) CPU-to-CPU communication
- C) Internet protocol communication
- D) OS-to-user communication
  **Answer: A**

### Q707. Which description of pipe in IPC is accurate?

- A) Unidirectional data
- B) Shared memory segment
- C) Network socket
- D) Hardware connection
  **Answer: A**

### Q708. In a resource-constrained environment, which description of shared memory IPC is accurate?

- A) Memory shared between OS and
- B) Cache shared by cores
- C) Processes share CPU
- D) Multiple processes access
  **Answer: D**

### Q709. Identify the correct statement about message passing IPC.

- A) Processes communicate by
- B) Logging system calls
- C) Broadcasting to all processes
- D) Email between processes
  **Answer: A**

### Q710. Which of the following best describes file descriptor?

- A) File metadata
- B) File location on disk
- C) Integer handle representing
- D) File permission string
  **Answer: C**

### Q711. In a resource-constrained environment, identify the correct statement about n inode.

- A) Internet node
- B) Data structure storing
- C) Input node in network
- D) Index of directory
  **Answer: B**

### Q712. Identify the correct statement about hard link.

- A) Symbolic shortcut
- B) Cross-device file reference
- C) Read-only file reference
- D) Directory entry pointing
  **Answer: D**

### Q713. Which description of symbolic (soft) link is accurate?

- A) File containing path to another file
- B) Encrypted file reference
- C) Direct inode reference
- D) Hard link variant
  **Answer: A**

### Q714. Which of the following best describes difference between hard link and soft link?

- A) Soft links share inode
- B) Hard links share inode
- C) Both break if target deleted
- D) No difference
  **Answer: B**

### Q715. Identify the correct statement about disk partitioning.

- A) Splitting CPU time
- B) Splitting RAM
- C) Dividing disk into
- D) Dividing network bandwidth
  **Answer: C**

### Q716. Identify the correct statement about file system.

- A) Method of organizing and
- B) Collection of files
- C) File permission system
- D) Directory structure
  **Answer: A**

### Q717. In a resource-constrained environment, fAT vs NTFS file system?

- A) FAT is simpler/older
- B) No difference
- C) FAT supports larger files
- D) NTFS is simpler
  **Answer: A**

### Q718. Identify the correct statement about journaling in file systems.

- A) Audit trail of file access
- B) Recording changes before
- C) Incremental backup
- D) Logging user activities
  **Answer: B**

### Q719. Identify the correct statement about boot loader.

- A) Loads user apps
- B) Software loading OS
- C) Network boot protocol
- D) BIOS replacement
  **Answer: B**

### Q720. Consider a system where which description of hypervisor is accurate?

- A) High-priority process
- B) Advanced scheduler
- C) GPU manager
- D) Software creating and
  **Answer: D**

### Q721. Type 1 vs Type 2 hypervisor?

- A) Type 1 runs on bare metal
- B) Type 2 runs on bare metal
- C) No difference
- D) Both run on host OS
  **Answer: A**

### Q722. Which description of SMP (Symmetric Multiprocessing) is accurate?

- A) Multiple CPUs sharing same OS and memory
- B) Software-managed parallelism
- C) Single-master processing
- D) Sequential process management
  **Answer: A**

### Q723. When designing for high performance, which description of load balancing in OS is accurate?

- A) Memory distribution
- B) Distributing processes
- C) Network packet distribution
- D) Balancing file sizes
  **Answer: B**

### Q724. Which description of kernel module is accurate?

- A) User application
- B) Boot loader component
- C) Code loaded into kernel
- D) Hardware driver always
  **Answer: C**

### Q725. What does POSIX define?

- A) Database standard
- B) Network protocol
- C) Portable OS interface
- D) Programming language
  **Answer: C**

### Q726. Which of the following best describes power management in OS?

- A) Battery manufacturing
- B) OS controlling hardware
- C) CPU overclocking
- D) Managing electrical grid
  **Answer: B**

### Q727. Which description of difference between blocking and non-blocking I/O is accurate?

- A) No difference
- B) Both always block
- C) Non-blocking waits
- D) Blocking waits for I/O
  **Answer: C**

### Q728. Identify the correct statement about n access control matrix.

- A) CPU register matrix
- B) Encryption key matrix
- C) Table where rows=subjects
- D) Network access table
  **Answer: C**

### Q729. In a resource-constrained environment, which description of rootkit threat is accurate?

- A) Malware gaining privileged
- B) Admin tool
- C) SQL injection variant
- D) Network attack tool
  **Answer: A**

### Q730. Identify the correct statement about ddress space layout randomization (ASLR).

- A) Randomizes page sizes
- B) Randomizes CPU scheduling
- C) Randomizes memory addresses
- D) Encrypts memory
  **Answer: C**

### Q731. Which description of OOM (Out Of Memory) killer is accurate?

- A) Memory compression
- B) Error message only
- C) Swap space manager
- D) Linux mechanism terminatin
  **Answer: D**

### Q732. When designing for high performance, which description of copy-on-write in OS is accurate?

- A) Always copies data on write
- B) Copy files on write to disk
- C) Multiple processes share pages
- D) Cache write policy
  **Answer: C**

### Q733. Which of the following best describes principle of least privilege?

- A) Processes share all privileges
- B) Processes/users get minimum
- C) Users get maximum access
- D) Kernel has least access
  **Answer: B**

### Q734. Which of the following best describes race condition's solution?

- A) Faster CPU
- B) Better scheduling
- C) Synchronization mechanism
- D) More memory
  **Answer: C**

### Q735. Identify the correct statement about busy waiting (spinlock).

- A) Thread continuously
- B) Thread sleeping waiting for
- C) I/O waiting state
- D) Thread blocked by OS
  **Answer: A**

### Q736. Identify the correct statement about readers-writers problem.

- A) Memory allocation problem
- B) CPU scheduling problem
- C) File naming problem
- D) Multiple readers can access
  **Answer: D**

### Q737. Identify the correct statement about dining philosophers problem.

- A) CPU scheduling problem
- B) AI problem
- C) Classic synchronization
- D) Memory management problem
  **Answer: C**

### Q738. Consider a system where which description of multilevel page table is accurate?

- A) Multiple page sizes
- B) Multiple TLBs
- C) Shared page table
- D) Hierarchical page table
  **Answer: D**

### Q739. Identify the correct statement about swapping in OS.

- A) CPU context switch
- B) Thread migration
- C) Page replacement
- D) Moving entire process
  **Answer: D**

### Q740. Identify the correct statement about difference between swap space and virtual memory.

- A) Swap is RAM
- B) Swap is disk space used
- C) No difference
- D) Virtual memory doesn't
  **Answer: A**

### Q741. Which description of purpose of the OS scheduler is accurate?

- A) Decide which process/thread runs
- B) Schedule disk I/O only
- C) Schedule maintenance tasks
- D) Manage file system access
  **Answer: A**

### Q742. Identify the correct statement about Completely Fair Scheduler (CFS).

- A) Priority scheduler
- B) FIFO scheduler
- C) Real-time scheduler
- D) Linux scheduler giving
  **Answer: D**

### Q743. Which of the following best describes producer-consumer problem?

- A) Synchronization problem where
- B) Distributed computing problem
- C) Memory allocation problem
- D) CPU scheduling problem
