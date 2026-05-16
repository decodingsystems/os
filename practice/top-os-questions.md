# Top OS Interview Questions

### 1. What is a Deadlock? Mention the necessary conditions for a deadlock.
A deadlock is a situation where a set of processes are blocked because each process is holding a resource and waiting for another resource acquired by some other process.
**Necessary conditions (Coffman conditions):**
1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

### 2. Difference between a Process and a Thread?
- **Process:** Heavyweight, has its own memory space, context switching is slow.
- **Thread:** Lightweight, shares memory with sibling threads, context switching is fast.

### 3. What is a Mutex vs Semaphore?
- **Mutex:** A locking mechanism used to synchronize access to a resource. Only the thread that acquired the mutex can release it.
- **Semaphore:** A signaling mechanism. It's an integer variable that can be updated via wait() and signal() operations. Any thread can signal a semaphore.

### 4. What is Thrashing?
Thrashing occurs when a computer's virtual memory subsystem is in a constant state of paging, rapidly exchanging data in memory for data on disk, leading to severe performance degradation.

### 5. Explain Spooling.
Simultaneous Peripheral Operations On-Line (Spooling) is a process in which data is temporarily held to be used and executed by a device, program, or the system. For instance, sending documents to a printer.
