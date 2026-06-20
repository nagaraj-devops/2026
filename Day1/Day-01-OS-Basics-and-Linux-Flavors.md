# 📅 Day 1: OS Basics & Linux Flavors

## 📘 Concept Overview

**What is an Operating System (OS)?**
- An OS is **system software** that sits between hardware and the user/applications.
- It manages **hardware resources** (CPU, memory, disk, network) and provides a platform to run applications.
- Examples: Windows, macOS, Linux, Unix.

**Core Functions of an OS:**
- **Process Management** — runs, schedules, and terminates programs.
- **Memory Management** — allocates RAM to processes.
- **File System Management** — organizes and stores data on disk.
- **Device Management** — communicates with hardware via drivers.
- **Security & Access Control** — manages users, permissions.

**Types of Operating Systems:**
| Type | Description |
|---|---|
| **Batch OS** | Executes jobs in batches without user interaction |
| **Multi-programming OS** | Runs multiple programs in memory at once |
| **Time-Sharing OS** | Multiple users share CPU time in slices |
| **Distributed OS** | Manages a group of networked computers as one system |
| **Network OS** | Provides services to computers on a network |
| **Real-Time OS (RTOS)** | Processes data within strict time constraints |

**What is Linux?**
- Linux is an **open-source, Unix-like kernel** created by Linus Torvalds in 1991.
- The **Linux Kernel** + **GNU tools** + packaging = a **Linux Distribution (Distro)**.
- It is the **dominant OS for servers, cloud infrastructure, and AWS EC2 instances**.

**Popular Linux Flavors (Distros):**
- **Ubuntu** — beginner-friendly, widely used in cloud & dev environments.
- **Debian** — stable, the base for Ubuntu.
- **Red Hat Enterprise Linux (RHEL)** — enterprise-grade, paid support.
- **CentOS / Rocky Linux / AlmaLinux** — free RHEL-compatible alternatives.
- **Amazon Linux** — AWS-optimized distro, ideal for EC2.
- **Fedora** — cutting-edge, community-driven (upstream of RHEL).
- **SUSE / openSUSE** — popular in enterprise data centers.

---

## 🗺️ Architecture Diagram — OS Layers

```
┌───────────────────────────────────────────┐
│               APPLICATIONS                  │
│     (Browser, VS Code, Apache, MySQL)        │
├───────────────────────────────────────────┤
│             SHELL / GUI LAYER                │
│        (Bash, Zsh, Desktop Environment)      │
├───────────────────────────────────────────┤
│           OPERATING SYSTEM KERNEL            │
│   - Process Mgmt   - Memory Mgmt             │
│   - File System    - Device Drivers          │
├───────────────────────────────────────────┤
│                 HARDWARE                     │
│      (CPU, RAM, Disk, Network Card)          │
└───────────────────────────────────────────┘
```

## 🗺️ Linux Distro Family Tree

```
                     LINUX KERNEL
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
   Debian-based       RHEL-based         Independent
        │                 │                 │
   ┌────┴────┐      ┌─────┴─────┐     ┌─────┴─────┐
  Ubuntu    Mint    RHEL   CentOS    Amazon Linux
   │                Rocky  AlmaLinux   SUSE   Fedora
  Kali, Pop!_OS
```

---

## 📊 Why / What / How / When

| Aspect | Details |
|---|---|
| **Why** | An OS is the foundation every application and cloud server depends on. Understanding it is essential before learning AWS, since every EC2 instance runs on an OS (mostly Linux). |
| **What** | A layer of system software that manages hardware resources and provides services to applications. Linux is a free, open-source, Unix-like OS kernel with many distributions. |
| **How** | The kernel handles low-level hardware communication; the shell/GUI lets users interact; distros package the kernel with tools, package managers (`apt`, `yum`, `dnf`), and defaults for ease of use. |
| **When** | You interact with an OS every time you boot a laptop, SSH into a server, or launch an EC2 instance. Choose a distro based on use case — e.g., **Amazon Linux** for AWS-native workloads, **Ubuntu** for general dev/cloud use, **RHEL** for enterprise compliance needs. |
