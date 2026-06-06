# Day 4 — OS Review Checklist

## Mastery Checklist

### OS Fundamentals
- [ ] What an OS does (resource manager, intermediary)
- [ ] Types: batch, multiprogramming, multitasking, multiprocessing, real-time, distributed
- [ ] System software: compiler, linker, loader (loader lives in memory)
- [ ] Bootstrap sequence: BIOS → Bootstrap → Bootloader → Kernel

### Process Management
- [ ] Process = program in execution (has PCB, address space, stack/heap)
- [ ] Process states: New → Ready → Running → [Blocked | Ready] → Terminated
- [ ] Blocked → Ready (NOT Running) when I/O completes
- [ ] Context switch = pure overhead (save/restore process state)
- [ ] PCB contents: PID, state, PC, registers, memory limits, open files

### CPU Scheduling
- [ ] FCFS: simple, convoy effect, non-preemptive
- [ ] SJF: optimal avg wait, starvation of long jobs
- [ ] SRTF: preemptive SJF
- [ ] Round Robin: time quantum, fair, context switch overhead
- [ ] Priority: starvation → fixed by aging
- [ ] Short-term vs Long-term vs Medium-term scheduler
- [ ] Preemptive vs Non-preemptive

### Synchronization
- [ ] Race condition: concurrent access → unpredictable results
- [ ] Critical section: mutual exclusion, progress, bounded waiting
- [ ] Mutex: lock/unlock, binary
- [ ] Semaphore: counting, wait(S)/signal(S)
- [ ] Monitor: high-level with condition variables

### Deadlock
- [ ] 4 conditions: Mutual Exclusion, Hold & Wait, No Preemption, Circular Wait
- [ ] Prevention: break one condition
- [ ] Avoidance: Banker's Algorithm (safe state)
- [ ] Detection: wait-for graph (cycle = deadlock if single instance)
- [ ] Recovery: abort or preempt

### Memory Management
- [ ] Logical vs Physical address (MMU translates)
- [ ] Contiguous allocation → external fragmentation
- [ ] Paging → no external fragmentation, page table
- [ ] TLB: fast cache for page table entries
- [ ] Virtual memory: demand paging, page faults
- [ ] Page replacement: FIFO (Belady's), LRU, Optimal
- [ ] Replacement policy vs Load policy vs Fetch policy
- [ ] Thrashing: too much paging → reduce multiprogramming

### File Systems
- [ ] Allocation: contiguous, linked, indexed
- [ ] Free space: bit vector, linked list, grouping, counting
- [ ] procfs for kernel params (sysctl)
- [ ] Directory structures: single-level, two-level, tree, acyclic graph

### I/O
- [ ] Polling vs Interrupt-driven vs DMA
- [ ] Spooling: buffer for slow devices (print queue)

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **Process states** | "New Ready Running Blocked Terminated" — NR●BT |
| **Blocked → Ready** | "I/O done → Ready queue, not directly to CPU" |
| **Deadlock conditions** | "**M**utual **E**xclusion **H**old **N**o **C**ircular" → MEHNC |
| **FCFS convoy** | "Short stuck behind long — like a convoy" |
| **SJF** | "Shortest first — optimal but needs burst prediction" |
| **RR quantum** | "Too big = FCFS, too small = overhead" |
| **Belady's FIFO** | "More frames, more faults — FIFO only!" |
| **Loader in memory** | "Loader loads — it's already loaded" |
| **Paging** | "Page → Frame, no external fragmentation" |
| **Thrashing** | "Paging > executing — too many processes!" |

## 1-Page Cram Sheet

```
PROCESS STATES
══════════════
New → Ready → Running → Blocked → Ready → Terminated
              ↑___________|  (time quantum expired)

SCHEDULING ALGORITHMS
═════════════════════
FCFS:       Non-preemptive, convoy effect
SJF:        Non-preemptive, optimal avg wait
SRTF:       Preemptive SJF
Round Robin: Preemptive, time quantum q
Priority:   Can be preemptive, may starve

DEADLOCK 4 CONDITIONS
═════════════════════
1. Mutual Exclusion    2. Hold & Wait
3. No Preemption       4. Circular Wait

MEMORY
══════
Paging: page table maps logical→physical
Page fault: accessed page not in memory
Thrashing: excessive paging

PAGE REPLACEMENT
════════════════
FIFO:    Oldest page out (Belady's anomaly)
LRU:     Least recently used out
Optimal: Replace page used farthest in future

BANKER'S ALGORITHM
══════════════════
Check if granting request leads to safe state
Safe = exists sequence where all processes can complete

SCHEDULER TYPES
════════════════
Long-term:   Job queue → Ready (controls multiprogramming)
Short-term:  Ready → Running (CPU scheduler, very frequent)
Medium-term: Swapping processes in/out

BOOT SEQUENCE
═════════════
BIOS → Bootstrap → Bootloader → OS Kernel

KEY RULES
═════════
- Blocked I/O complete → goes to READY, not RUNNING
- Context switch = pure overhead
- Loader is the system software in memory
- procfs allows sysctl kernel parameter changes
- Grouping = n free block addresses in first free block
```
