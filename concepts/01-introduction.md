# Introduction to Operating Systems

## What is an Operating System?
An **Operating System (OS)** is system software that acts as an intermediary between computer hardware and user applications. It manages hardware resources — CPU, memory, storage, I/O devices — and provides a stable, consistent environment for programs to run.

Without an OS, every application would need to directly speak the hardware's language. The OS abstracts this complexity so developers can write `open("file.txt")` instead of managing raw disk sectors.

## Core Responsibilities of an OS
- **Process Management:** Creating, scheduling, suspending, and terminating processes. Enforcing fair CPU time-sharing.
- **Memory Management:** Allocating and deallocating RAM, implementing virtual memory, protecting address spaces.
- **File System Management:** Organizing data into files and directories, handling read/write permissions, managing disk space.
- **Device Management:** Via device drivers, the OS communicates with hardware (keyboard, GPU, network card).
- **Security & Access Control:** Users, permissions, authentication, sandboxing.

## Types of Operating Systems

| Type | Description | Examples |
|------|-------------|---------|
| **Batch OS** | Jobs queued and run without interaction | Early IBM mainframes |
| **Time-Sharing OS** | CPU time split among multiple users | Unix |
| **Real-Time OS (RTOS)** | Hard time constraints on task execution | FreeRTOS, VxWorks |
| **Distributed OS** | Manages resources across multiple networked machines | Amoeba, Plan 9 |
| **Mobile OS** | Optimized for touchscreens, battery, limited resources | Android, iOS |

## Kernel vs User Space
The OS is divided into two distinct privilege levels:

```
┌──────────────────────────────────────┐
│          User Space                  │ ← Applications run here
│   (Browser, Editor, Games, CLI)      │   limited hardware access
├──────────────────────────────────────┤
│          Kernel Space                │ ← OS core runs here
│ (Process mgmt, Memory, Drivers, FS) │   direct hardware access
└──────────────────────────────────────┘
```

- **User space:** Applications run with restricted privileges. They cannot directly access hardware.
- **Kernel space:** The core OS with full hardware privileges. Applications request services via **System Calls**.

## System Calls
System calls are the API between user-space programs and the kernel:

| System Call | Purpose |
|-------------|---------|
| `fork()` | Create a new child process |
| `exec()` | Replace process image with a new program |
| `open(), read(), write()` | File I/O |
| `malloc() → brk()/mmap()` | Memory allocation |
| `socket(), connect()` | Network I/O |
| `wait()` | Parent waits for child to finish |

## Monolithic vs Microkernel

- **Monolithic:** All OS services run in kernel space (Linux, Windows). Fast — no context switches for kernel services.
- **Microkernel:** Only minimal services in kernel (memory, IPC, scheduling). Drivers and FS run in user space (macOS XNU hybrid, Minix). More stable but slower.
