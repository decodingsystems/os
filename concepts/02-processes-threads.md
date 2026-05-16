# Processes and Threads

## What is a Process?
A **process** is a program in execution — a running instance of a program with its own isolated memory space, file handles, and system resources. When you open Chrome, the OS creates a process for it. Open it again — another separate process.

### Process Components
- **Code (Text) Segment:** The compiled instructions of the program.
- **Data Segment:** Global and static variables.
- **Heap:** Dynamically allocated memory (`malloc`, `new`).
- **Stack:** Function call frames, local variables, return addresses.
- **Process Control Block (PCB):** OS data structure tracking the process — PID, state, registers, memory maps, open files.

## Process States
```
New → Ready → Running → Terminated
              ↓      ↑
            Waiting (I/O)
```

| State | Meaning |
|-------|---------|
| **New** | Process is being created |
| **Ready** | In memory, waiting for CPU |
| **Running** | Currently executing on CPU |
| **Waiting** | Blocked on I/O or event |
| **Terminated** | Finished or killed |

## Process Creation: fork() and exec()
```c
pid_t pid = fork();   // Clone the process
if (pid == 0) {
    // Child process
    exec("/bin/ls", args);  // Replace with new program
} else {
    // Parent process
    wait(NULL);  // Wait for child
}
```
- `fork()` creates an exact copy of the calling process.
- `exec()` replaces the copied process image with a different program.

## What is a Thread?
A **thread** is a lightweight unit of execution within a process. Multiple threads share the same process memory (heap, code, data) but each has its own stack and registers.

### Process vs Thread
| Aspect | Process | Thread |
|--------|---------|--------|
| Memory | Separate address space | Shared address space |
| Creation overhead | High | Low |
| Communication | Complex (IPC needed) | Simple (shared memory) |
| Fault isolation | High (crash doesn't affect others) | Low (crash can kill all threads) |

## CPU Scheduling
When there are more ready processes/threads than CPU cores, the OS **scheduler** decides who runs:

- **FCFS (First Come, First Served):** Simple queue. No preemption. Can cause convoy effect.
- **Round Robin:** Each process gets a fixed **time quantum**. Fair and starvation-free.
- **Priority Scheduling:** Higher priority runs first. Risk: starvation of low-priority processes.
- **Shortest Job First (SJF):** Optimal average wait time but requires knowing burst time in advance.

## Concurrency Problems
### Race Condition
When two threads access shared data simultaneously and the outcome depends on scheduling order.
### Deadlock
Four conditions must ALL hold: Mutual exclusion, Hold & Wait, No Preemption, Circular Wait.
### Solutions
- **Mutex / Lock:** Only one thread executes the critical section at a time.
- **Semaphore:** Counter-based signaling between threads.
- **Monitor:** Higher-level language construct (Java `synchronized`).
