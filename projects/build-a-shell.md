# Project: Build a Basic Shell

## Overview
A shell is the command-line interpreter that provides the user interface for the operating system. In this project, you will build a simple shell using C that can execute commands, support built-ins like `cd` and `exit`, and handle background processes.

## Steps

### Step 1: The Basic Loop
Your shell needs to continually prompt the user for input.
```c
while (1) {
    printf("myshell> ");
    // Read input
}
```

### Step 2: Parsing Input
Once you read a string of input, you must parse it. Tokenize the string using `strtok()` to separate the command from its arguments.

### Step 3: Executing Commands
For external commands (like `ls`, `cat`), use system calls:
1. `fork()`: Create a child process.
2. `execvp()`: In the child process, load the program into memory and execute it.
3. `waitpid()`: In the parent process, wait for the child to finish.

### Step 4: Built-in Commands
Commands like `cd` and `exit` must be executed by the shell itself, not by a child process. Check if the parsed command equals "cd" and use the `chdir()` system call.

## Extensions to Try
- **I/O Redirection:** Implement `>` and `<` using `dup2()`.
- **Pipes:** Implement `|` to pipe output from one process to another.
