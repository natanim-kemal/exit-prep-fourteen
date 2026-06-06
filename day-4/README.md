# Day 4 — Operating Systems (8 Items)

## Files in this directory

| File | Content |
|------|---------|
| `01-os-complete.md` | Full theory: process management, CPU scheduling (FCFS/SJF/RR/Priority), synchronization, deadlock (Banker's Algorithm), memory management (paging/replacement), file systems, I/O, system calls + 18 exam Q&As |
| `02-trace-exercises.md` | 15 exam-style problems: scheduling calculations (FCFS/SJF/RR with timing), Banker's Algorithm safe/unsafe state, FIFO/LRU/Optimal page replacement, logical→physical address translation, fragmentation, context switch overhead, CPU utilization |
| `03-review-checklist.md` | Mastery checklist, mnemonics, Bloom's taxonomy, 1-page cram sheet |

## How to use today

1. **Read** `01-os-complete.md` (2-3 hrs) — focus on process states, scheduling algorithms, deadlock conditions, paging
2. **Practice** `02-trace-exercises.md` (1-2 hrs) — especially scheduling calculations and page replacement (common exam problems)
3. **Self-test** `03-review-checklist.md` (30 min)

## Key exam focus (from actual model exams)

- **Process state transitions** — Blocked→Ready is the trick question
- **Scheduler types** — Short-term = CPU scheduler
- **Deadlock** — Banker's Algorithm is AVOIDANCE not detection
- **Memory replacement policies** — FIFO, LRU, Optimal
- **Bootstrap process** — initializes everything and starts OS
- **Loader in memory** — system software that resides in main memory
- **procfs** — file system for kernel parameters via sysctl
- **Free space grouping** — n addresses in first free block

## Next: Day 5 — Databases (7 items)
