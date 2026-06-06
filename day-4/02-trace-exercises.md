# Day 4 — OS Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: CPU Scheduling Calculations

### Problem 1 — FCFS Scheduling
Processes arrive at time 0 in order: P1(6ms), P2(8ms), P3(7ms), P4(3ms)

```
Gantt Chart:
| P1 | P2 | P3 | P4 |
0    6    14   21   24

Waiting Time: P1=0, P2=6, P3=14, P4=21
Turnaround:   P1=6, P2=14, P3=21, P4=24
Avg Waiting:  (0+6+14+21)/4 = 10.25ms
Avg Turnaround: (6+14+21+24)/4 = 16.25ms
```

---

### Problem 2 — SJF Scheduling (Non-Preemptive)
Processes with burst times: P1(6), P2(8), P3(7), P4(3)

```
Order by burst: P4(3) → P1(6) → P3(7) → P2(8)

Gantt:
| P4 | P1 | P3 | P2 |
0    3    9    16   24

Waiting:  P4=0, P1=3, P3=9, P2=16
Avg Waiting: (0+3+9+16)/4 = 7ms
```

SJF gives optimal average waiting time — but requires knowing burst times in advance.

---

### Problem 3 — SJF with Arrival Times
Processes: P1(0,7), P2(2,4), P3(4,1), P4(5,4)
Format: (arrival, burst)

```
Time 0-2: only P1 arrived → P1 runs (remaining 5)
Time 2-4: P1, P2 ready → P2 has shorter burst (4) than P1 remaining (5)
          Wait, actually SJF picks shortest among arrived.
          At time 2: P1(rem 5), P2(burst 4) → run P2 for 4ms
Time 4-6: P1(rem 5), P3(arrived at 4, burst 1), P4(not yet)
          P3(1) is shortest → run P3
Time 6-7: P1(rem 5), P4(arrived at 5, burst 4) → P4(4) < P1(5) → run P4 for 4ms
Time 7-11: P4 runs
Time 11-16: P1 runs (remaining 5)

Gantt: | P1 | P2 | P3 | P4 | P1 |
       0    2    6    7    11   16

Waiting: P1=4, P2=0, P3=2, P4=2
Avg: (4+0+2+2)/4 = 2ms
```

---

### Problem 4 — Round Robin, Quantum = 4ms
Processes: P1(10), P2(5), P3(2)

```
Ready Queue: [P1, P2, P3]

Time 0-4:  P1 runs (rem 6) → enqueue P1 → Q: [P2, P3, P1]
Time 4-8:  P2 runs (rem 1) → enqueue P2 → Q: [P3, P1, P2]
Time 8-10: P3 runs (rem 0, done!) → Q: [P1, P2]
Time 10-14: P1 runs (rem 2) → enqueue P1 → Q: [P2, P1]
Time 14-15: P2 runs (rem 0, done!) → Q: [P1]
Time 15-17: P1 runs (rem 0, done!)

Completion: P1=17, P2=15, P3=10
Turnaround: P1=17, P2=15, P3=10
Waiting:    P1=7, P2=10, P3=8
Avg Wait:   (7+10+8)/3 = 8.33ms
```

---

### Problem 5 — Effect of Time Quantum
With quantum = 20ms for P1(24):
```
Time 0-20: P1 runs (rem 4) → enqueue
Time 20-24: P1 runs (done)

With quantum = 4ms for P1(24):
Time 0-4, 8-12, 16-20, 22-24, ... much more context switching
```
**Key point**: Large quantum → FCFS behavior; Small quantum → too much context switch overhead

---

## Set 2: Deadlock — Banker's Algorithm

### Problem 6 — Safe State Check
System has 12 instances of resource R.

| Process | Max | Allocation | Need |
|---------|-----|------------|------|
| P0 | 10 | 5 | 5 |
| P1 | 4 | 2 | 2 |
| P2 | 9 | 2 | 7 |

Available = 12 - (5+2+2) = 3

```
Available = 3
P1 needs 2 ≤ 3 → can run. After P1, releases 2 → Available = 3+2 = 5
P0 needs 5 ≤ 5 → can run. After P0, releases 5 → Available = 5+5 = 10
P2 needs 7 ≤ 10 → can run.

Safe sequence: P1 → P0 → P2
State is SAFE.
```

---

### Problem 7 — Unsafe State
System has 10 instances.

| Process | Max | Allocation | Need |
|---------|-----|------------|------|
| P0 | 8 | 5 | 3 |
| P1 | 3 | 2 | 1 |
| P2 | 9 | 3 | 6 |

Available = 10 - (5+2+3) = 0

```
Available = 0
P1 needs 1 > 0 → cannot run
P0 needs 3 > 0 → cannot run
P2 needs 6 > 0 → cannot run

No process can proceed → State is UNSAFE
```

---

## Set 3: Page Replacement Traces

### Problem 8 — FIFO Page Replacement
Reference string: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1
Frames = 3

```
Ref   Frames         Page Fault?
7     [7, _, _]      ✓
0     [7, 0, _]      ✓
1     [7, 0, 1]      ✓
2     [2, 0, 1]      ✓ (replace 7, oldest)
0     [2, 0, 1]         (0 is in memory)
3     [2, 3, 1]      ✓ (replace 0? no, replace oldest which is 2... wait)
      Actually FIFO: replace the page that arrived first
      Queue: [7(0), 0(1), 1(2)] 
      Page 2: replace 7 → [2, 0, 1], queue: [0(1), 1(2), 2(3)]
      Page 0: hit → queue stays
      Page 3: replace oldest = 0 → [2, 3, 1], queue: [1(2), 2(3), 3(4)]
      ...
```
FIFO is simple but can suffer from **Belady's Anomaly**.

---

### Problem 9 — LRU Page Replacement
Same reference string: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2
Frames = 3

```
Ref   Frames         LRU order (most recent first)
7     [7]            [7]
0     [7, 0]         [7, 0]
1     [7, 0, 1]      [7, 0, 1]
2     [2, 0, 1]      [0, 1, 2]  (7 LRU, replaced)
0     [2, 0, 1]      [1, 2, 0]  (0 hit, becomes most recent)
3     [2, 3, 1]      [2, 1, 3]  (0 not LRU is wrong... 1 is LRU...)
      Wait: before reference 3, LRU order is [1, 2, 0] (0 most recent)
      So LRU = 1 → replace 1 with 3 → [2, 0, 3]
```
LRU replaces the page that has not been used for the longest time.

---

### Problem 10 — Optimal Page Replacement
Same string, frames = 3

```
Ref   Frames         Decision
7     [7]            fault
0     [7, 0]         fault
1     [7, 0, 1]      fault
2                   replace page used farthest in future
                    7 used at index ∞, 0 at 4, 1 at ... 
                    replace 7 → [2, 0, 1]
```
Optimal replaces the page that will be used farthest in the future (or never again).
Not implementable in practice — used as theoretical benchmark.

---

## Set 4: Memory Management Calculations

### Problem 11 — Logical to Physical Address
Page size = 4KB (4096 bytes = 2¹²)
Page table: Page 0→Frame 3, Page 1→Frame 7, Page 2→Frame 1

Logical address = 4KB + 100 = 4096 + 100 = address 4196

```
Page number = 4196 / 4096 = 1
Offset      = 4196 % 4096 = 100
Frame = page table[1] = 7
Physical address = (7 * 4096) + 100 = 28672 + 100 = 28772
```

**Formula**: Physical = Frame × PageSize + Offset

---

### Problem 12 — Fragmentation
A system has 100KB free in two chunks: 30KB and 70KB.
A process needs 40KB.

**External fragmentation** exists: total free = 100KB, but no single block large enough for 40KB if using fixed partitions or if contiguous allocation requires one block.

---

## Set 5: Process Concepts

### Problem 13 — PCB Contents
Which is NOT stored in the Process Control Block?
- A. Process ID
- B. Program Counter
- C. **Compiler version** ← ✓
- D. CPU registers

---

### Problem 14 — Context Switch
If context switch takes 1ms and time quantum is 10ms, what percentage of CPU time is spent on context switching?

```
Overhead = 1ms per switch / 10ms quantum = 10%
```

---

### Problem 15 — CPU Utilization
Process spends 80% of its time waiting for I/O. If 3 such processes are in memory, what is CPU utilization?

```
CPU utilization = 1 - (0.8)³ = 1 - 0.512 = 0.488 = 48.8%
```
With n processes: CPU util = 1 - (waitFraction)^n

---

## Common Exam Traps — OS

| Trap | Explanation |
|------|-------------|
| **Blocked → Running** | Blocked process goes to READY, not directly to Running |
| **Deadlock vs Starvation** | Deadlock = circular wait; Starvation = never scheduled |
| **Banker's = Detection** | Banker's is AVOIDANCE, not detection |
| **Belady's FIFO only** | Belady's anomaly only affects FIFO, not LRU/Optimal |
| **Short-term vs Long-term** | Short-term = CPU scheduler (fast); Long-term = job scheduler (slow) |
| **Loader vs Linker** | Loader puts executable in memory; Linker combines object files |
| **Bootstrap vs Bootloader** | Bootstrap initializes HW; Bootloader loads OS |
| **Preemptive ≠ Priority** | Preemptive means can interrupt; Priority is a scheduling policy |
| **Multiprogramming vs Multitasking** | Multiprogramming = keep CPU busy (no time sharing); Multitasking = time sharing |
| **FCFS = non-preemptive** | FCFS is always non-preemptive |
