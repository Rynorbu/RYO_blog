---
title: System Information
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

This section is about learning basic Linux commands that help you understand your system, check network settings, and manage users. These commands are useful for general Linux tasks and also important in cybersecurity for checking security settings, finding weaknesses, or fixing security issues.

**Basic Commands to Check System Information:**

# Linux Command Cheat Sheet

## User & System Information
| Command   | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| `whoami`  | Displays your current username                                              |
| `id`      | Shows user identity (UID, GID, and groups)                                  |
| `hostname`| Shows or sets the system's hostname                                         |
| `uname`   | Displays OS and hardware info (`uname -a` for all details)                  |
| `who`     | Lists currently logged-in users                                             |
| `env`     | Displays or sets environment variables                                      |

## File System & Directories
| Command   | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| `pwd`     | Prints your current working directory                                       |
| `lsblk`   | Lists all block storage devices (disks, partitions)                         |
| `lsof`    | Shows all open files and which processes are using them                     |

## Network Utilities
| Command   | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| `ifconfig`| Displays or configures network interfaces (deprecated, use `ip` instead)    |
| `ip`      | Modern tool for network configuration (`ip addr`, `ip route`)               |
| `netstat` | Shows network connections (use `ss` for newer systems)                      |
| `ss`      | Socket statistics (replacement for `netstat`)                               |

## Hardware Information
| Command   | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| `lsusb`   | Lists all connected USB devices                                             |
| `lspci`   | Lists all PCI devices (graphics cards, network controllers, etc.)          |

## Process Management
| Command   | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| `ps`      | Lists running processes (`ps aux` for detailed list)                        |

**Checking Network Information:**

- ifconfig – Shows IP addresses and network settings (old command, replaced by IP).
- ip – Displays and changes network settings.
    - Example:

```jsx
$ ip a
```

(Shows IP addresses assigned to network interfaces.)
- **netstat** – Shows network connections and open ports.
- **ss** – A faster alternative to netstat for checking open network connections.

**Checking System Processes and Files:**

- **ps** – Shows running processes.
- **who** – Lists all logged-in users.
- **env** – Displays system environment variables.
- **lsblk** – Shows information about storage devices.
- **lsusb** – Lists connected USB devices.
- **lsof** – Shows open files and which processes are using them.
- **lspci** – Lists PCI (hardware) devices like graphics or network cards.