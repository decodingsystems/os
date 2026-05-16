# OS Commands Cheatsheet

### Process Management
**Linux / UNIX**
- `ps -aux`: List all running processes.
- `top` / `htop`: Interactive process viewer.
- `kill -9 <PID>`: Force kill a process.
- `nice -n 10 <command>`: Run a process with a specific priority.

**Windows**
- `tasklist`: Displays a list of currently running processes.
- `taskkill /PID <PID> /F`: Force kill a process by ID.

### Memory & System Info
**Linux**
- `free -m`: Show RAM usage in MB.
- `df -h`: Show disk space usage.
- `uname -a`: Display system/kernel information.

**Windows**
- `systeminfo`: Comprehensive overview of system configuration.

### Network Monitoring
**Linux**
- `netstat -tulpn`: List active connections and listening ports.
- `ping <ip>`: Test reachability of a host.

**Windows**
- `netstat -ano`: Displays active TCP connections.
