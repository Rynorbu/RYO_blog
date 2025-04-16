---
title: Service and Process Management
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

### Service and Process Management in Linux

### Overview

Linux provides robust tools for managing system services and processes. This section explains how to handle background services (daemons) and running processes, with particular focus on modern systems using systemd.

## Service Management

### Types of Services

- **System Services**: Critical services required for system operation (e.g., systemd, sshd)
- **User-Installed Services**: Optional services providing additional functionality (e.g., web servers, databases)

### Service Management with systemctl

The `systemctl` command is the primary interface for service management in systemd-based systems:

| Command | Description |
| --- | --- |
| `systemctl start <service_name>` | Starts a specified service |
| `systemctl status <service_name>` | Displays current status of a service |
| `systemctl enable <service_name>` | Configures service to start at boot |
| `systemctl list-units --type=service` | Lists all available services |
| `journalctl -u <service_name> --no-pager` | Shows service logs |

## Process Management

### Process States

Processes may exist in various states:

- **Running**: Actively executing
- **Waiting**: Paused for resources
- **Stopped**: Suspended execution
- **Zombie**: Completed but not yet removed

### Process Control Commands

### Process Termination

| Command | Description |
| --- | --- |
| `kill <PID>` | Sends termination signal to process |
| `kill -9 <PID>` | Forces immediate termination (SIGKILL) |
| `kill -15 <PID>` | Requests graceful termination (SIGTERM) |
| `kill -19 <PID>` | Stops/pauses a process (SIGSTOP) |

### Background Process Management

| Command | Description |
| --- | --- |
| `[Ctrl + Z]` | Suspends current foreground process |
| `bg` | Resumes suspended process in background |
| `command &` | Runs command directly in background |
| `jobs` | Lists background jobs |
| `fg` | Brings background job to foreground |

### Process Monitoring

| Command | Description |
| --- | --- |
| `ps -aux` | Lists all running processes |
| `kill -l` | Displays all available signals |
| `top` | Interactive process viewer |

## Practical Examples

1. **Starting and enabling a service**:

```
systemctl start nginx
systemctl enable nginx
```

1. **Checking service status**:

```
systemctl status sshd
```

1. **Terminating a process**:

```
ps -aux | grep chrome
kill -15 1234
```

1. **Managing background processes**:

```
long_running_command &
jobs
fg %1
``` 