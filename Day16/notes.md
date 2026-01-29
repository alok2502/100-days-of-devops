# Day 16 – Linux Permissions, Process Management & Monitoring

## Focus of the Day
Today’s learning focused on core Linux administration skills that are heavily used in DevOps:
- File permission management
- Process management
- System monitoring
- Disk usage and disk management basics

---

## Linux File Permission Management

Linux file permissions are managed at three levels:
- User (owner)
- Group
- Others

Each level can have three types of permissions:
- Read (r)
- Write (w)
- Execute (x)

---

## chmod – Changing File Permissions

Permissions can be modified using the `chmod` command.

### Symbolic Method
Permissions can be set using symbols:
- u → user
- g → group
- o → others

Example:
- Assign permissions using symbolic notation (u=rwx, g=rx, o=)

---

### Numeric Method
Each permission has a numeric value:
- Read = 4
- Write = 2
- Execute = 1

The sum defines the permission:
- 7 → read + write + execute
- 6 → read + write
- 5 → read + execute
- 4 → read only

Example:
- 777 → full permissions for everyone

Note: Using 777 is generally discouraged in production due to security risks.

---

## chown – Changing File Ownership

The `chown` command is used to:
- Change file owner
- Change group ownership

Ownership control is critical in multi-user environments.

---

## Process Management in Linux

A process is a running instance of a program.

As a DevOps engineer, common tasks include:
- Viewing processes
- Stopping or killing processes
- Resuming processes
- Managing process priority

---

## Viewing Processes

Two commonly used commands:
- ps -ef
- ps aux

Difference:
- ps aux shows memory and CPU utilization
- ps -ef focuses more on process hierarchy and details

---

## Killing and Controlling Processes

- kill → Gracefully terminates a process
- kill -9 → Forcefully kills a process
- kill -STOP → Stops (pauses) a process
- kill -CONT → Resumes a stopped process

Force killing should be used only when graceful termination fails.

---

## Process Priority (renice)

- renice is used to change the priority of a running process
- Helps prioritize or deprioritize processes based on system needs

---

## Process vs Service

- Process:
  - Runs when started manually
  - Stops when terminated
  - Does not restart automatically

- Service:
  - Managed by init system (systemd)
  - Can start automatically at system boot
  - Used for long-running background applications

---

## Linux System Monitoring

Monitoring system health is critical in production.

### CPU & Memory Monitoring
- top → Real-time system monitoring
- htop → Enhanced wrapper over top
- vmstat → Memory and system performance statistics
- free -h → Displays memory usage

---

### CPU Core Information
- nproc → Shows number of CPU cores

---

## Disk Usage Monitoring

- df -h → Shows disk space usage
- du -sh * → Shows disk usage per directory

Useful for identifying disk space issues.

---

## Disk Management Basics

Revisited concepts:
- Increasing disk size on EC2
- Mounting new storage
- Extending existing volumes

Disk management is essential for handling growing workloads.

---

## Summary

- Learned Linux permission model
- Practiced chmod and chown
- Strengthened process management skills
- Understood process vs service
- Monitored CPU, memory, and disk usage
- Revisited disk management basics

---

✅ Day 16 Completed – Linux Permissions, Processes & Monitoring
