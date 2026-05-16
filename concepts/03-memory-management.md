# Memory Management

## Why Memory Management Matters
Every running process needs RAM. The OS is responsible for deciding: which process gets which memory region, ensuring processes can't read each other's memory, and efficiently using limited physical RAM to support more processes than RAM can physically hold.

## Physical vs Virtual Memory
Modern OSes give each process the illusion it has the entire address space to itself — this is **Virtual Memory**.

```
Process A thinks it owns 0x0000 → 0xFFFF
Process B thinks it owns 0x0000 → 0xFFFF

OS + MMU translates both virtual addresses to different physical RAM locations
```

The **Memory Management Unit (MMU)** hardware does this translation on every memory access using a **Page Table**.

## Paging
Virtual and physical memory are divided into fixed-size chunks:
- **Pages:** Fixed-size blocks of virtual memory (typically 4KB)
- **Frames:** Fixed-size blocks of physical memory (same size as pages)
- **Page Table:** Per-process mapping of page number → frame number

```
Virtual Address = [Page Number | Page Offset]
                         ↓
                  Page Table Lookup
                         ↓
Physical Address = [Frame Number | Page Offset]
```

## Page Fault
When a process accesses a page not currently in RAM:
1. MMU raises a **page fault** interrupt.
2. OS checks if the address is valid (in page table).
3. OS finds a free frame or **evicts** (swaps out) another page.
4. OS loads the page from disk (swap space).
5. Updates page table and resumes the process.

### Page Replacement Algorithms
- **LRU (Least Recently Used):** Evict the page not used for the longest time. Optimal in practice.
- **FIFO:** Evict the oldest-loaded page. Simple but can evict frequently used pages.
- **Optimal:** Evict the page that won't be used for the longest time in future. Theoretical only.

## Memory Allocation

### Stack Allocation
- Managed automatically by the compiler.
- Fast: just increment/decrement the stack pointer.
- Limited size (typically 1-8 MB). Stack overflow crashes the program.

### Heap Allocation
- Dynamic, managed explicitly (`malloc`/`free` in C, `new`/`delete` in C++).
- Flexible size but subject to **fragmentation**.

### Fragmentation
- **Internal fragmentation:** Allocated block is larger than needed. Wasted space inside blocks.
- **External fragmentation:** Enough total free memory exists but not in one contiguous block.

## Segmentation
An alternative to paging: divide memory into logical segments (code, data, stack, heap) of variable size. Closer to how programmers think. Modern systems combine both: **paged segmentation**.

## Swapping and Swap Space
When physical RAM is full, the OS moves entire processes or pages to disk (**swap space**). Accessing swap is 1000× slower than RAM — when swap is heavily used, the system **thrashes** (spends more time paging than running).
