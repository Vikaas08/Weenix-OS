# Weenix Operating System Kernel

![Status](https://img.shields.io/badge/Status-Completed-success)
![C](https://img.shields.io/badge/Language-C-blue)
![Platform](https://img.shields.io/badge/Platform-QEMU-orange)
![Category](https://img.shields.io/badge/Category-Kernel%20Development-red)

A comprehensive, Unix-like operating system kernel built from the ground up as part of the **CSCI 402: Operating Systems** course at the **University of Southern California**.

> **Note:** Per university policy, the source code for this project is hosted in a private repository. This repository serves as a portfolio to demonstrate the architectural design and features implemented during the MSCS program.

---

## 🚀 Project Overview

Weenix is a teaching operating system designed to provide hands-on experience with the internal workings of a Unix kernel. Over a single semester, I implemented several critical subsystems, culminating in a kernel capable of booting into a user-space shell and executing complex concurrent processes.

## 🛠 Subsystems Implemented

### 1. Threads and Processes (PROCS)

Implemented the core execution model for a uniprocessor system.

- **Thread Lifecycle:** Managed thread creation, execution, and termination.
- **Scheduler:** Built a non-preemptive FIFO scheduler.
- **Synchronization:** Developed Mutexes, Condition Variables, and Wait Queues to manage concurrency.
- **Context Switching:** Handled low-level state saving and restoring of CPU registers.

### 2. Virtual File System (VFS)

Developed an abstraction layer that allows the kernel to interact with different file system implementations transparently.

- **System Calls:** Implemented `open()`, `read()`, `write()`, `close()`, `lseek()`, `stat()`, and `mkdir()`.
- **Abstractions:** Managed `vnode` and `vfs` structures, and per-process file descriptor tables.

### 3. S5 File System (S5FS)

Built a simplified version of the System V File System to handle persistent storage.

- **Disk Management:** Implemented Inode management, data block allocation, and directory entry traversal.
- **Consistency:** Managed the free-list and ensured proper synchronization during disk I/O.

### 4. Virtual Memory (VM)

The final and most complex phase, enabling user-space memory management.

- **Address Spaces:** Managed memory mappings using anonymous and file-backed objects.
- **Demand Paging:** Implemented a page fault handler to load data only when accessed.
- **Copy-on-Write (COW):** Optimized memory usage for the `fork()` system call.
- **Process Pipeline:** Implemented `fork()`, `exec()`, and `brk()`, allowing the kernel to boot into a functional Unix-like shell.

---

## 🔍 Verification & Testing

The stability of the kernel was verified through rigorous stress tests:

- **`faber_thread_test`:** Validated thread synchronization and scheduling.
- **`vfstest`:** Confirmed VFS abstraction and file system integrity.
- **`memtest`:** Verified virtual memory allocation and page fault handling.
- **`forkbomb`:** Stress-tested resource limits and process cleanup under heavy load.

---

## 💻 Technical Stack

- **Language:** C
- **Tools:** GDB (Kernel-level debugging), QEMU, GCC, Make
- **Concepts:** Kernel-mode vs User-mode, Interrupt Handling, Paging, Deadlock Avoidance.

---

## 🔗 References & Credits

- **Project Source:** [The Weenix Project](https://github.com/brown-cs167/weenix) (Originally developed at Brown University).
- **Instructor:** [Prof. William (Bill) Cheng](http://merlot.usc.edu/william/usc/)
- **Course:** CSCI 402: Operating Systems, University of Southern California
