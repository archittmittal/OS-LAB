# 🖥️ Operating Systems Laboratory (OS LAB) — 2026

[![Language: C](https://img.shields.io/badge/Language-C-blue.svg)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Platform: Linux/Unix/macOS](https://img.shields.io/badge/Platform-Linux%20%7C%20Unix%20%7C%20macOS-brightgreen.svg)](https://www.gnu.org/)
[![Course: Operating Systems](https://img.shields.io/badge/Course-Operating%20Systems-orange.svg)]()
[![Status: Active](https://img.shields.io/badge/Status-Complete-success.svg)]()

Welcome to the **Operating Systems Laboratory** repository. This repository contains structured C programs, system programming experiments, and homework assignments covering foundational UNIX/Linux operating systems concepts, process management, inter-process communication (IPC), system calls, and file handling.

---

## 📌 Course Resources & Notes

- **📚 Lecture Notes & Study Material Drive:** [Access Google Drive Notes Folder](https://drive.google.com/drive/folders/1cgoAxjrQ6s09EXEoFg5ZmxytkWOAT7B0?usp=sharing)

---

## 📂 Repository Directory Structure

The laboratory codebase is organized chronologically into date-based directories (YYYY-MM-DD format for 2026):

```
OS-LAB/
├── 📁 2026-07-31/
│   ├── 📁 Class/
│   │   ├── q1_pid_ppid.c               # Process ID (PID) & Parent PID (PPID) using fork()
│   │   ├── q2_parent_child.c           # Identifying parent vs child process via fork() return code
│   │   ├── q3_wait.c                   # Parent process waiting for child process using wait()
│   │   ├── q4_fibonacci_factorial.c    # Fibonacci in child, Factorial in parent process
│   │   ├── q5_fibonacci_factorial_sum.c# Multi-level process hierarchy (Grandchild process)
│   │   ├── first.c                     # Basic fork() demonstration
│   │   └── Questions.md                # In-class assignment problems
│   └── 📁 Homework/
│       ├── parent_even_child_odd.c     # Parent prints even numbers, child prints odd numbers
│       ├── three_child_processes.c     # Concurrent creation of 3 child processes
│       ├── child_exit_status_wait.c    # Retrieving child exit status code via wait()
│       ├── orphan_process_demo.c       # Simulation of Orphan process dynamics
│       ├── zombie_process_demo.c       # Simulation of Zombie process dynamics
│       └── Homework.md                 # Homework assignment documentation
├── 📁 2026-08-07/
│   └── 📁 Class/
│       ├── prime_factorial_fork.c      # Prime checking in child, Factorial in parent
│       ├── fibonacci_armstrong_fork.c  # Fibonacci in child, Armstrong numbers in parent
│       └── Questions.md                # Lab problem descriptions
├── 📁 2026-08-17/
│   └── 📁 Class/
│       ├── sum_prime_child.c           # Array summation and prime check in child process
│       ├── permutation_child.c         # String permutations generation in child process
│       └── Questions.md                # Problem statements
├── 📁 2026-09-18/
│   ├── Prime.c                         # Inter-process communication (IPC) using pipe()
│   └── input.c                         # Process-level file creation & reading via fork()
├── 📁 2026-09-25/
│   ├── even_numbers.c                  # Writing even numbers to file in child, reading in parent
│   ├── child_open_file.c               # Low-level system file descriptor operations in child
│   └── zombie_orphan.c                 # Comprehensive Zombie and Orphan process handler
├── .gitignore                          # Build & temporary file exclusion rules
└── README.md                           # Comprehensive documentation (this file)
```

---

## 📑 Lab Experiments & Topics Covered

### 🗓️ 1. Process Management Fundamentals (`2026-07-31`)
Focuses on fundamental process creation using `fork()`, process identification, parent-child synchronization with `wait()`, and handling special process states.

| File / Folder | Topic / Description | Key System Calls |
| :--- | :--- | :--- |
| `Class/q1_pid_ppid.c` | Fork process creation; prints PID and PPID of parent and child. | `fork()`, `getpid()`, `getppid()` |
| `Class/q2_parent_child.c` | Branching execution logic based on `fork()` return value (`0` vs `>0`). | `fork()` |
| `Class/q3_wait.c` | Synchronization where parent waits for child process to finish printing numbers 1..5. | `fork()`, `wait()`, `sleep()` |
| `Class/q4_fibonacci_factorial.c` | Parallel processing: child calculates Fibonacci series while parent calculates factorial. | `fork()`, `wait()` |
| `Class/q5_fibonacci_factorial_sum.c` | Grandchild process creation: Child 1 prints Fibonacci, Child 2 prints Factorial, Parent sums natural numbers. | Multi-level `fork()`, `wait()` |
| `Homework/parent_even_child_odd.c` | Concurrent execution: Parent outputs even numbers (1-20), child outputs odd numbers. | `fork()` |
| `Homework/three_child_processes.c` | Creating 3 child processes concurrently and displaying their process metadata. | `fork()`, `getpid()`, `getppid()` |
| `Homework/child_exit_status_wait.c` | Child exits with specific status code (`10`), parent captures and decodes exit code. | `fork()`, `exit()`, `wait()`, `WEXITSTATUS()` |
| `Homework/orphan_process_demo.c` | Orphan process simulation: parent exits early, child gets adopted by `init`/system daemon (`PPID` updates). | `fork()`, `sleep()`, `getppid()` |
| `Homework/zombie_process_demo.c` | Zombie process simulation: child terminates while parent sleeps without invoking `wait()`. | `fork()`, `exit()`, `sleep()` |

---

### 🗓️ 2. Parallel Computation & Algorithms (`2026-08-07`)
Explores delegating heavy or isolated computational tasks to child processes.

| File | Description | Concepts Demonstrated |
| :--- | :--- | :--- |
| `Class/prime_factorial_fork.c` | Child process checks if input number is prime; parent process computes factorial. | Parallel compute, process separation |
| `Class/fibonacci_armstrong_fork.c` | Child process generates Fibonacci series up to $N$; parent calculates Armstrong numbers up to $N$. | Mathematical function delegation in fork |

---

### 🗓️ 3. Array Processing & String Manipulations (`2026-08-17`)
Focuses on complex data structure operations inside child processes.

| File | Description | Key Algorithms / Concepts |
| :--- | :--- | :--- |
| `Class/sum_prime_child.c` | Computes array element sum within child process and evaluates whether sum is prime. | Array processing in fork child |
| `Class/permutation_child.c` | Reads a string from user input in child process and outputs all string permutations. | Backtracking, string manipulation |

---

### 🗓️ 4. Inter-Process Communication & File I/O (`2026-09-18`)
Covers IPC mechanisms using UNIX anonymous pipes (`pipe()`) and process file sharing.

| File | Description | Key System Calls |
| :--- | :--- | :--- |
| `Prime.c` | **UNIX Pipe IPC**: Parent calculates array sum and writes it to a pipe (`fd[1]`). Child reads the sum (`fd[0]`) and verifies if it is prime. | `pipe()`, `fork()`, `write()`, `read()`, `close()` |
| `input.c` | Parent process creates and writes user info (`input.txt`), parent waits, child opens file and outputs contents. | `fork()`, `fopen()`, `fprintf()`, `fgetc()`, `wait()` |

---

### 🗓️ 5. Low-Level System File Descriptors & Advanced Dynamics (`2026-09-25`)
Advanced file descriptor operations and process lifecycle behavior.

| File | Description | Key System Calls / Features |
| :--- | :--- | :--- |
| `even_numbers.c` | Child process opens file using `open()`, writes even numbers (1-20), closes descriptor. Parent reads and prints file content. | `open()`, `write()`, `read()`, `close()`, `wait()` |
| `child_open_file.c` | Demonstrates opening files specifically inside a child process and checking file descriptor validity. | `open()`, `O_RDONLY`, `close()` |
| `zombie_orphan.c` | Complete demonstration of process states, execution delays, orphan adoption, and zombie state cleanup. | `fork()`, `sleep()`, `wait()`, `getpid()` |

---

## 🛠️ How to Compile and Run

### Prerequisites
- GCC (`gcc`) or Clang compiler
- POSIX-compliant OS (Linux, macOS, Unix, or WSL on Windows)

### Compilation Steps
Navigate to any lab directory and compile the target `.c` file using `gcc`:

```bash
# Example 1: Compiling and running the Pipe IPC program
gcc -o prime_pipe 2026-09-18/Prime.c
./prime_pipe

# Example 2: Compiling Zombie Process demo
gcc -o zombie_demo 2026-07-31/Homework/zombie_process_demo.c
./zombie_demo
```

### Inspecting Processes in Real-Time
To view active, orphan, or zombie processes during execution, run in a separate terminal:

```bash
# Check process tree
pstree -p

# Search for zombie processes (status 'Z')
ps aux | grep 'Z'
```

---

## 💡 Key OS Concepts Summary

1. **`fork()` System Call**: Duplicates the calling process, creating an exact child process. Returns `0` in the child process, the child's `PID` in the parent, and `-1` on error.
2. **Parent-Child Synchronization (`wait()`)**: Parent process suspends execution until a child process terminates, preventing zombie accumulation and capturing exit status (`WEXITSTATUS`).
3. **Zombie Process**: A process that has completed execution but still has an entry in the process table because its parent hasn't called `wait()`.
4. **Orphan Process**: A child process whose parent has terminated before it. Inherited by process ID `1` (`init` or `launchd`/`systemd`).
5. **UNIX Pipe (`pipe(fd)`)**: A unidirectional data channel for IPC. `fd[1]` is the write end, and `fd[0]` is the read end.

---

## 👤 Author

- **Archit Mittal** — [GitHub Profile](https://github.com/archittmittal)
- Repository: [https://github.com/archittmittal/OS-LAB.git](https://github.com/archittmittal/OS-LAB.git)
