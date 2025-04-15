---
title: Linux Structure
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

## What is Linux?
- **Operating System (OS)**: Manages hardware & software communication (like Windows, macOS).
- **Distributions (Distros)**: Linux comes in many different distributions — often called "distros"— which are versions of Linux.
- **Open-Source**: Free to modify & distribute (used in servers, phones, IoT devices, etc.).


### History
- **Unix (1970s):** Linux is based on an older OS called **Unix**, created by Ken Thompson and Dennis Ritchie at AT&T.
- **GNU Project (1983):** Richard Stallman wanted to make a **free Unix-like OS**, leading to the creation of the **GNU General Public License (GPL)**.
- **Linux Kernel (1991):** Linus Torvalds, a Finnish student, built the **Linux kernel**, the core part of Linux.
- **Linux Today:** Linux is used everywhere—from servers to Android phones. There are **over 600 distros** like Ubuntu, Fedora, and RedHat.


**Why is Linux Popular?**

- **Security:** Less vulnerable to viruses than Windows.
- **Performance:** Stable and fast.
- **Customization:** Can be modified as per user needs.
- **Free and Open-Source:** No cost, and anyone can contribute.

**Linux Philosophy (How Linux Works)**

Linux follows simple but powerful principles:

1. **Everything is a file** – Even system settings are stored in files.
2. **Small, single-purpose programs** – Each tool does one task well.
3. **Combine programs together** – Small tools can work together for complex tasks.
4. **Avoid complex user interfaces** – Linux is designed for command-line (terminal) use.
5. **Text-based configuration** – System settings are saved in text files (e.g., `/etc/passwd` for user data).

**Linux Components (Building Blocks of Linux)**

- Linux is made up of different parts that work together:


| Component        | What It Does                                                                 |
|------------------|------------------------------------------------------------------------------|
| **Bootloader**   | Starts the computer and loads the OS (e.g., GRUB).                           |
| **Kernel**       | The core of Linux - manages hardware and processes.                          |
| **Daemons**      | Background services that run automatically (printing, networking, etc.).     |
| **Shell**        | Command-line interface (CLI) where users type commands.                      |
| **Graphics Server** | Enables graphical programs to run (e.g., X-server).                        |
| **Window Manager** | Controls how windows look and behave (e.g., GNOME, KDE).                   |
| **Utilities**    | Applications for specific tasks (file managers, web browsers, etc.).         |


**Linux Architecture (How Linux is Built)**

Linux has different layers, just like a cake:

- Hardware – The physical components (CPU, RAM, hard drive).
- Kernel – The core of Linux, managing resources and processes.
- Shell – The user interface where you type commands.
- System Utilities – Programs that help users interact with the system.

### **Linux File System (How Files Are Organized)**

Linux organizes files in a **tree structure**, starting from the **root (`/`) directory**.

**Important Directories in Linux**

| Directory  | Purpose & Examples                                                                 |
|------------|-----------------------------------------------------------------------------------|
| **/home**  | User personal files (`/home/username/Documents`, `/home/username/Downloads`)      |
| **/etc**   | System configuration files (`/etc/passwd`, `/etc/network/interfaces`)             |
| **/bin**   | Essential command-line programs (`ls`, `cp`, `mv`, `cat`, `bash`)                 |
| **/var**   | Variable data like logs (`/var/log`) and temporary files (`/var/tmp`)             |
| **/dev**   | Hardware device files (`/dev/sda` for disks, `/dev/ttyUSB0` for USB devices)      |
| **/boot**  | Boot loader files (kernels, initramfs, GRUB config)                               |
| **/root**  | Administrator's personal files (not to be confused with `/` root directory)       |