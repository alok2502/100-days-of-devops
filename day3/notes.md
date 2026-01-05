# Day 03 – Linux Operating System Basics & Shell Scripting

## Topics Covered
- What is an Operating System
- Why Linux is widely used
- Linux architecture
- Basic Linux commands
- Shell scripting fundamentals
- Linux & shell scripting from a DevOps perspective

---

## What Is an Operating System?

An operating system acts as an intermediate layer between software and hardware.

When a user performs an action (for example, creating a folder):
- The user communicates with the operating system
- The operating system communicates with the hardware
- The hardware performs the action
- The response flows back from hardware → OS → user

This is how all user actions are executed in a system.

---

## Why Linux Is Widely Used

Linux is one of the most popular operating systems in DevOps and cloud environments because:

- It is free and open source
- It is highly secure
- It is very stable and reliable
- It comes in many distributions
- It is very fast, especially without GUI
- Most servers and cloud systems run on Linux

Because of these reasons, Linux is the backbone of DevOps.

---

## Linux Architecture

Linux is made up of multiple components:

### Kernel
- The heart of the operating system
- Manages CPU, memory, devices, and processes
- Handles system calls

### System Libraries
- Provide core functionalities
- Allow applications to interact with the kernel

### System Software & User Processes
- Compilers
- Shell
- Utilities
- User applications

These components together enable interaction between the user and the system.

---

## Basic Linux Commands Learned

- whoami – shows the current user
- pwd – prints the current working directory
- ls – lists files and directories
- cd – changes directory
- vim – text editor
- cat – displays file content
- nproc – shows number of CPU cores
- free -h – displays memory usage
- df -h – shows disk usage
- top – displays live system resource usage

These commands are used daily by DevOps engineers for debugging and monitoring.

---

## What Is Shell Scripting?

Shell scripting is a way to communicate with the Linux operating system and automate tasks.

Shell scripts start with a shebang:

#! followed by the shell executable path

Common shell executables include:
- /bin/bash
- /bin/sh
- /bin/dash
- /bin/ksh

Bash is the most popular shell used in DevOps.

Earlier, /bin/sh was linked to bash, but in most modern Linux distributions it is linked to dash, which is faster but has slightly different syntax.

---

## Executing Shell Scripts & Permissions

When a shell script is created:
- It does not have executable permission by default

On execution:
- A permission error occurs

This is fixed using the chmod command.

### Linux Permission Concept

Permissions are represented using numbers:
- 4 → Read
- 2 → Write
- 1 → Execute

7 is considered a magic number (4 + 2 + 1).

Permissions are applied to:
- User
- Group
- Others

This permission model is a core part of Linux security.

---

## Useful Linux Utilities Learned

- history – shows previously executed commands
- man – manual pages for Linux commands
- vim editor – used for editing files efficiently

---

## Shell Scripting in DevOps (Why It Matters)

From a DevOps perspective, shell scripts are mainly used for:

- Code automation
- Infrastructure management
- Configuration management
- General automation tasks

Shell scripting helps reduce manual work and improves efficiency.

---

## Key Takeaways

- Linux is the foundation of DevOps and cloud systems
- Understanding OS fundamentals is critical before advanced tools
- Permissions are a core Linux security concept
- Shell scripting enables automation
- Linux skills directly translate to real-world DevOps work

---

✅ Day 03 Completed – Linux Fundamentals & Shell Scripting
