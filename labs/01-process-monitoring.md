# Lab 1: Process and Memory Monitoring

## Objective
To understand how processes utilize system resources and how to interact with them via command line tools.

## Prerequisites
- A Linux environment (WSL, VM, or native Linux).
- Root/Sudo privileges are helpful but not required for basic observation.

## Exercise 1: Monitoring System Resource Usage
1. Open a terminal.
2. Run the `top` command:
   ```bash
   top
   ```
3. **Observe:** The header shows system uptime, load average, total CPU%, and Memory usage.
4. **Identify:** Find the process taking the most RAM (look at the `%MEM` column).
5. **Action:** Press `q` to exit `top`.

## Exercise 2: Searching for Specific Processes
1. Run a sleep command in the background:
   ```bash
   sleep 300 &
   ```
2. Find its Process ID (PID) using `ps` and `grep`:
   ```bash
   ps aux | grep sleep
   ```

## Exercise 3: Killing a Process
1. Using the PID you found in Exercise 2, gracefully terminate the process:
   ```bash
   kill <PID>
   ```
2. Verify it is no longer running by running `ps aux | grep sleep` again.

## Conclusion
You have effectively launched a process, monitored CPU and Memory at the OS level, queried the kernel for specific process data, and sent a system signal (SIGTERM) to end a process safely.
