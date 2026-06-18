# Operating Systems — Study Notes

## 1. Process Management

**Process**: program in execution — has its own memory space (code, data, heap, stack), registers, program counter.

**Process vs Thread**:
- **Process**: heavyweight, isolated memory space, context switch is expensive
- **Thread**: lightweight, shares memory within a process, faster context switch

**Process states**: New → Ready → Running → Waiting/Terminated.

**Process Control Block (PCB)**: kernel data structure containing process information (PID, state, program counter, registers, memory limits).

## 2. CPU Scheduling

**Scheduling algorithms**:
- **FCFS (First-Come, First-Served)**: processes executed in order of arrival; non-preemptive; can cause convoy effect
- **SJF (Shortest Job First)**: shortest next CPU burst first; optimal average waiting time; can cause starvation
- **Priority Scheduling**: higher priority runs first; can cause starvation (solved by aging)
- **Round Robin (RR)**: each process gets a fixed time quantum; preemptive; good for time-sharing

**Scheduling criteria**: CPU utilization, throughput, turnaround time, waiting time, response time.

## 3. Process Synchronization

- **Race condition**: multiple processes access shared data concurrently, result depends on execution order
- **Critical section**: code that accesses shared resources; only one process can execute at a time
- **Mutual Exclusion (Mutex)**: ensures only one process accesses a shared resource at a time
- **Semaphore**: integer variable used for signaling; `wait()` (P) decrements, `signal()` (V) increments; can be binary or counting
- **Deadlock**: processes waiting indefinitely for resources held by each other

## 4. Deadlock

**Four necessary conditions** (all must hold):
1. **Mutual Exclusion**: resource can only be used by one process at a time
2. **Hold and Wait**: process holding a resource waits for additional resources held by others
3. **No Preemption**: resources cannot be forcibly taken
4. **Circular Wait**: circular chain of processes waiting for resources

**Deadlock handling**: prevention (break at least one condition), avoidance (Banker's algorithm), detection and recovery, ignore (ostrich algorithm).

## 5. Memory Management

- **Paging**: fixed-size pages — no external fragmentation, internal fragmentation possible
- **Segmentation**: variable-size segments — external fragmentation possible
- **Virtual memory**: allows processes to use more memory than physically available
- **Page replacement**: FIFO (can suffer Belady's anomaly), LRU (approximated by counter/aging), Optimal (not realizable)

**Thrashing**: excessive paging activity — CPU spends more time swapping than executing. Solution: reduce degree of multiprogramming.

## 6. File Systems

- **File**: named collection of data on secondary storage
- **Directory**: organizes files hierarchically
- **Disk scheduling**: FCFS, SSTF (Shortest Seek Time First), SCAN (elevator), C-SCAN, LOOK

## 7. System Software

- **Compiler**: translates source code → object code (machine code for a specific architecture)
- **Assembler**: translates assembly → machine code
- **Linker**: combines object files into executable; resolves external references
- **Loader**: loads executable into memory for execution (relocation, linking)

**Boot sequence**: Power On → BIOS/UEFI → Bootstrap → Bootloader → OS Kernel.

**Kernel types**:
- **Monolithic**: all OS services run in kernel space (Linux, Unix); fast but less modular
- **Microkernel**: minimal kernel — only essential services (IPC, basic scheduling); more modular but slower IPC
- **Exokernel**: delegates resource management to applications (minimalist kernel)
- **Hybrid**: combines monolithic and microkernel approaches (Windows NT, macOS XNU)

## 8. I/O Management

- **Polling**: CPU repeatedly checks device status (busy-waiting)
- **Interrupts**: device notifies CPU when ready (efficient)
- **DMA (Direct Memory Access)**: transfers data directly between device and memory without CPU intervention
