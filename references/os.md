# OS Reference -- Operating Systems

## Process vs Thread

| Aspect | Process | Thread |
|---|---|---|
| Definition | Program in execution | Smallest unit of execution within a process |
| Memory | Separate memory space | Shares memory space with other threads in process |
| Communication | IPC (pipes, sockets, shared memory) | Direct sharing of variables |
| Creation cost | High (fork) | Low |
| Crash impact | One process crash does not affect others | One thread crash can crash the whole process |
| Context switch | Expensive | Cheaper |

**Multithreading vs Multiprocessing**
Multithreading: multiple threads in one process, share memory, good for I/O bound tasks.
Multiprocessing: multiple processes, separate memory, good for CPU bound tasks, true parallelism on multi-core.

---

## CPU Scheduling Algorithms

**FCFS (First Come First Serve)**
Non-preemptive. Simple but can cause convoy effect (short jobs wait behind long jobs).

**SJF (Shortest Job First)**
Non-preemptive or preemptive (SRTF). Optimal average waiting time but requires knowing burst time in advance.

**Round Robin**
Preemptive. Each process gets a time quantum. Fair but high context switch overhead if quantum is too small.

**Priority Scheduling**
Preemptive or non-preemptive. Can cause starvation of low-priority processes. Solved by aging (gradually increasing priority of waiting processes).

**Multilevel Queue Scheduling**
Different queues for different process types (foreground, background). Fixed priority between queues.

**Metrics**
- Turnaround Time = Completion Time minus Arrival Time
- Waiting Time = Turnaround Time minus Burst Time
- Response Time = First CPU Time minus Arrival Time
- Throughput = Number of processes completed per unit time

---

## Process Synchronization

**Race Condition**: multiple threads access shared data concurrently and outcome depends on execution order.

**Critical Section Problem**: only one process in the critical section at a time.
Requirements: Mutual Exclusion, Progress, Bounded Waiting

**Mutex (Mutual Exclusion Lock)**
Binary lock. Only the thread that locked it can unlock it.

**Semaphore**
Counter variable. wait() decrements, signal() increments.
- Binary Semaphore: works like a mutex but any thread can signal
- Counting Semaphore: controls access to a resource pool of n instances

**Monitor**
High-level synchronization construct. Methods are mutually exclusive. Condition variables (wait, signal) coordinate threads.

**Classic Synchronization Problems**
- Producer-Consumer: producer adds to buffer, consumer removes. Buffer has fixed size.
- Readers-Writers: multiple readers OK simultaneously, writer needs exclusive access.
- Dining Philosophers: 5 philosophers, 5 forks, must pick up both adjacent forks to eat. Deadlock if all pick left fork simultaneously.

---

## Deadlock

**Four Necessary Conditions (Coffman Conditions)**
1. Mutual Exclusion: resource held by one process at a time
2. Hold and Wait: process holds a resource while waiting for another
3. No Preemption: resources cannot be forcibly taken
4. Circular Wait: cycle in resource allocation graph

**Deadlock Prevention**: negate one of the four conditions
**Deadlock Avoidance**: Banker's Algorithm -- grant request only if system remains in safe state
**Deadlock Detection and Recovery**: allow deadlock, detect via resource allocation graph, recover by killing process or preempting resources
**Deadlock Ignorance**: (Ostrich Algorithm) pretend it does not happen. Used by most OS for rare cases.

---

## Memory Management

**Contiguous Allocation**
Memory divided into fixed or variable partitions.
Fragmentation: External (gaps between allocated blocks), Internal (wasted space within allocated block).

**Paging**
Physical memory divided into frames, logical memory into pages of same size.
No external fragmentation. Internal fragmentation possible.
Page Table maps page numbers to frame numbers.
TLB (Translation Lookaside Buffer): cache for page table entries, speeds up translation.

**Segmentation**
Memory divided into variable-size logical segments (code, data, stack).
External fragmentation possible.

**Virtual Memory**
Allows execution of processes not fully in memory. Uses disk as extension of RAM.
Demand Paging: load page only when needed.
Page Fault: referenced page not in memory, OS loads it from disk.

**Page Replacement Algorithms**
- FIFO: replace oldest page. Simple but Belady's Anomaly (more frames can cause more faults).
- LRU: replace least recently used. No Belady's Anomaly. Expensive to implement exactly.
- Optimal: replace page not used for longest time in future. Theoretical benchmark.

---

## File Systems

**File Allocation Methods**
- Contiguous: fast sequential access, external fragmentation
- Linked: no fragmentation, poor random access
- Indexed: uses index block, good random access, overhead for small files

**Directory Structures**: Single-level, Two-level, Tree, Acyclic Graph, General Graph

**Disk Scheduling Algorithms**
- FCFS: service requests in order of arrival
- SSTF (Shortest Seek Time First): service nearest request, can cause starvation
- SCAN (Elevator): head moves in one direction servicing requests, then reverses
- C-SCAN (Circular SCAN): head moves in one direction only, jumps back to start

---

## Common Interview Questions

1. What is the difference between kernel mode and user mode?
2. What is a context switch? What is saved/restored?
3. What is thrashing? How is it caused and prevented?
4. What is the difference between internal and external fragmentation?
5. Explain the working of fork() in Unix.
6. What is a zombie process? An orphan process?
7. What is the purpose of the OS scheduler?
8. How does the TLB improve memory access performance?
9. What is a system call? Give examples.
10. What is the difference between preemptive and non-preemptive scheduling?
