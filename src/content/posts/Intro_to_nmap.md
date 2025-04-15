---
title: Introduction to Nmap
published: 2025-16-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Nmap
draft: false
---

Nmap **(Network Mapper)** is a powerful, free, and open-source tool used to scan and analyze networks.

It helps security professionals and network administrators discover hosts and services on a computer network, thus creating a "map" of the network.

It’s written in **C, C++, Python, and Lua** and is widely used by **network administrators** and **ethical hackers** to find:

- Devices on a network
- Identify open ports
- Services running on each port
- Operating systems and versions
- Security risks like misconfigured firewalls or services

### What Can Nmap Do?

Nmap helps with many tasks in network and security testing, such as:

- Auditing network security
- Simulating penetration tests
- Checking firewall and IDS (Intrusion Detection System) settings
- Mapping networks (finding devices)
- Analyzing network responses
- Identifying open ports
- Detecting vulnerabilities

### Nmap Architecture

Nmap offers several types of scans that give different kinds of information. Here are the **main scanning techniques**:

1. **Host Discovery** – Finds out which machines are online.
2. **Port Scanning** – Checks which ports are open or closed.
3. **Service Detection** – Identifies services and their versions.
4. **OS Detection** – Tries to find out the operating system running on the host.
5. **Nmap Scripting Engine (NSE)** – Runs custom scripts to interact with services (e.g., brute force, vulnerability checks).

### Nmap Syntax

Using Nmap is pretty simple. Here’s the basic format:

```jsx
nmap <scan type> <options> <target>
```

Example:

```jsx
nmap -sS 10.10.10.8
```
This scans your local machine using a TCP SYN scan.

### Scan Techniques

Nmap has many scanning options. Some popular ones include:

```jsx
nmap --help
```

You’ll see options like:

- `sS`: **TCP SYN scan** (default & most popular)
- `sT`: TCP Connect scan
- `sA`: ACK scan
- `sU`: UDP scan
- `sN`, `sF`, `sX`: Null, FIN, and Xmas scans
- `sI`: Idle scan
- `sO`: IP Protocol scan
- `b`: FTP bounce scan
- `-scanflags`: Custom TCP flags

### TCP SYN Scan (`sS`)

This is the **default and fastest** scan method. It works like this:

- Sends a packet with the **SYN** flag to the port.
- If the port replies with **SYN-ACK**, the port is **open**.
- If it replies with **RST**, the port is **closed**.
- If there's **no reply**, Nmap marks it as **filtered** (probably blocked by a firewall).