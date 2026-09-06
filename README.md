# Pintos — Stanford Instructional Operating System

CS2043 – Operating Systems  
Department of Computer Science and Engineering, University of Moratuwa

## Overview

Pintos is an instructional operating system framework for x86 architecture. Within the CS2043 curriculum, it serves as the practical backbone for systems programming, kernel development, and translating operating system theory into concrete, verifiable implementations.

This project approaches Pintos as a continuous personal OS-development initiative: tracing kernel mechanisms, implementing core primitives, debugging concurrency invariants, and verifying kernel behavior under strict grading test harnesses.

## Environment & Toolchain

- **Host Environment**: Windows 11 with WSL2 (Windows Subsystem for Linux)
- **Linux Distribution**: Ubuntu LTS
- **Emulator**: Bochs / QEMU
- **Compiler**: GCC with 32-bit compilation (`-m32`), position-independent code disabled
- **Debugger**: GDB with remote target socket connection (`target remote localhost:1234`)
- **Reference Standard**: PKU Pintos GitBook and official Stanford Pintos technical documentation

## Project Roadmap & Branch Architecture

All operating system laboratory milestones and feature additions are developed within this centralized repository through structured Git branches rather than separate repositories.

| Phase | Milestone | Focus Areas | Branch Reference |
| :--- | :--- | :--- | :--- |
| **Setup** | Environment Configuration | WSL2 toolchain, Bochs/QEMU build setup, and compilation fixes | `main` |
| **Lab 0** | Getting Real & Kernel Monitor | Kernel boot sequence, interactive shell, `whoami`, `ram`, `time`, `shutdown` | `lab01-interactive-shell` |
| **Lab 1** | Threads & Synchronization | Timer sleep by blocking (avoiding busy-wait), Priority Scheduling, Priority Donation, and MLFQS | `project1-alarm-clock` |
| **Lab 2** | User Programs & Protection | Process execution, user-kernel address validation, and system calls (`halt`, `exit`, `exec`, `wait`, `write`, `read`) | `lab02-user-programs` *(Planned)* |
| **Lab 3** | Virtual Memory | Supplemental page tables, frame table, page fault handling, stack growth, eviction, and swap | `lab03-virtual-memory` *(Planned)* |
| **Lab 4** | File Systems | Indexed inodes, directory hierarchies, buffer cache, file expansion, and synchronization | `lab04-file-systems` *(Planned)* |

## Theory Alignment with CS2043

- **Kernel Boot & Hardware Abstraction**: Week 01 – History & Overview of Operating Systems
- **Threads, Concurrency & Synchronization**: Weeks 02–04 – Processes, Threads, CPU Scheduling & Synchronization
- **System Calls & User Mode**: Week 05 – Operating System Structures & System Calls
- **Memory Management & Paging**: Weeks 06–08 – Main Memory & Virtual Memory Systems
- **Storage & Inodes**: Weeks 09–11 – File-System Interface and Implementation
- Theory notes and conceptual analyses are maintained in the [CS2043-Weekly-Notes](https://github.com/CS2043-Operating-Systems/CS2043-Weekly-Notes) repository.

## Repository Structure

```text
.
├── src/
│   ├── threads/        # Kernel thread scheduler, timer, synchronization primitives, interrupt handling
│   ├── userprog/       # Process loading, system call infrastructure, exception handling
│   ├── vm/             # Virtual memory management, page tables, swap slot allocation
│   ├── filesys/        # Inode management, directory parsing, file system operations
│   ├── devices/        # Timer, keyboard, serial, disk, and console device drivers
│   ├── lib/            # Standard C library subset and kernel data structures (list, hash, bitmap)
│   ├── tests/          # Automated test suites for threads, userprog, vm, and filesys
│   └── utils/          # Host tools: pintos runner script, disk partitioner, GDB macros
└── README.md
```

## Engineering & Git Standards

- **Commit Conventions**: All commits adhere to Conventional Commits format (`feat:`, `fix:`, `chore:`, `docs:`, `refactor:`).
- **Branching Workflow**: Each laboratory milestone branches from its preceding stable baseline, is verified against automated test suites, and is tracked on designated milestone branches.
- **Verification**: Kernel changes are verified by running automated test suites inside the build directory:
  ```bash
  cd src/threads/build && make check
  ```

## Academic Context

Department of Computer Science and Engineering, University of Moratuwa.
