# WARP.md — Quick Reference Cheatsheet

This file is loaded during Revision Mode or when the student asks for a cheat sheet. It contains the fastest lookup material across all subjects.

---

## DSA at a Glance

### Time Complexities to Memorize

| Operation | Array | Linked List | BST (avg) | Hash Map |
|---|---|---|---|---|
| Search | O(n) | O(n) | O(log n) | O(1) |
| Insert | O(1) end | O(1) head | O(log n) | O(1) |
| Delete | O(n) | O(n) | O(log n) | O(1) |

### Sorting Algorithms

| Algorithm | Best | Average | Worst | Space |
|---|---|---|---|---|
| Bubble Sort | O(n) | O(n2) | O(n2) | O(1) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
| Quick Sort | O(n log n) | O(n log n) | O(n2) | O(log n) |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) |

### Top 10 DSA Patterns for Interviews

1. Sliding Window
2. Two Pointers
3. Fast and Slow Pointers
4. Merge Intervals
5. Cyclic Sort
6. Binary Search on Answer
7. BFS and DFS
8. Dynamic Programming (Top Down + Bottom Up)
9. Backtracking
10. Monotonic Stack

---

## OS at a Glance

### Process States
New -> Ready -> Running -> Waiting -> Terminated

### CPU Scheduling Algorithms
- FCFS: Non preemptive, convoy effect problem
- SJF: Optimal average wait time, starvation possible
- Round Robin: Time quantum based, best for time sharing
- Priority Scheduling: Preemptive or non preemptive

### Deadlock Conditions (all four must hold)
1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

### Page Replacement Algorithms
- FIFO: Simple, Belady's anomaly possible
- LRU: Optimal in practice, costly to implement
- Optimal: Best performance, not implementable in real time

---

## OOPs at a Glance

### Four Pillars
| Pillar | One Line Definition |
|---|---|
| Encapsulation | Binding data and methods, hiding internals |
| Abstraction | Showing only necessary details |
| Inheritance | Child class inherits parent class properties |
| Polymorphism | One interface, many implementations |

### SOLID Principles
- S: Single Responsibility
- O: Open Closed
- L: Liskov Substitution
- I: Interface Segregation
- D: Dependency Inversion

### Common Design Patterns
- Singleton: One instance globally
- Factory: Create objects without specifying class
- Observer: Subscribe and notify pattern
- Decorator: Add behavior without changing class
- Strategy: Swap algorithms at runtime

---

## Computer Networks at a Glance

### OSI Layers (top to bottom)
7. Application (HTTP, FTP, DNS)
6. Presentation (SSL, encryption)
5. Session (session management)
4. Transport (TCP, UDP)
3. Network (IP, routing)
2. Data Link (MAC, switches)
1. Physical (cables, signals)

### TCP vs UDP
| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection oriented | Connectionless |
| Reliability | Guaranteed delivery | No guarantee |
| Speed | Slower | Faster |
| Use case | HTTP, FTP, Email | Video, DNS, Gaming |

### HTTP Status Codes to Know
- 200: OK
- 201: Created
- 301: Moved Permanently
- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 500: Internal Server Error

---

## DBMS at a Glance

### Normal Forms
- 1NF: No repeating groups, atomic values
- 2NF: 1NF + no partial dependency
- 3NF: 2NF + no transitive dependency
- BCNF: Every determinant is a candidate key

### ACID Properties
- Atomicity: All or nothing
- Consistency: Valid state before and after
- Isolation: Transactions do not interfere
- Durability: Committed data persists

### SQL Commands by Category
- DDL: CREATE, ALTER, DROP, TRUNCATE
- DML: SELECT, INSERT, UPDATE, DELETE
- DCL: GRANT, REVOKE
- TCL: COMMIT, ROLLBACK, SAVEPOINT

---

## Aptitude Quick Formulas

### Time and Work
- If A finishes in n days, A's 1 day work = 1/n
- Combined work of A and B = 1/a + 1/b

### Speed, Distance, Time
- Distance = Speed x Time
- Average Speed (two legs) = 2ab / (a+b)

### Percentages
- X% of Y = (X x Y) / 100
- Percentage change = (New - Old) / Old x 100

### Probability
- P(A) = Favorable outcomes / Total outcomes
- P(A and B) = P(A) x P(B) for independent events
- P(A or B) = P(A) + P(B) - P(A and B)

### Permutations and Combinations
- nPr = n! / (n-r)!
- nCr = n! / (r! x (n-r)!)

---

## System Design Quick Framework

### For any system design question, follow RESHADED:

**R** — Requirements (functional and non functional)
**E** — Estimation (scale, storage, bandwidth)
**S** — Storage schema (DB choice, schema design)
**H** — High level design (components, services)
**A** — APIs (define key APIs)
**D** — Data flow (how data moves through system)
**E** — Explain bottlenecks and how to handle them
**D** — Deep dive into one component

### Common System Design Components
- Load Balancer: Distributes traffic
- Cache (Redis): Reduces DB load
- CDN: Serves static content fast
- Message Queue (Kafka): Async communication
- Database Sharding: Horizontal scaling
- Replication: High availability
