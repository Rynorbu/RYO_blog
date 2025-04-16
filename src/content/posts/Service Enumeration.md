---
title: Service Enumeration
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Nmap
draft: false
---

### **What Is Service Enumeration?**

Service enumeration is the process of identifying:

- **Open ports**
- **Running services**
- **Service versions**
- **Operating systems (OS)**

This allows attackers (or ethical hackers) to find vulnerabilities that are specific to those versions/services.

### Common Nmap Scanning Options

| Option               | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **-p-**               | Scans all 65,535 TCP ports                                                 |
| **-sV**               | Performs service version detection                                         |
| **-Pn**               | Treats host as online (skips ICMP ping)                                    |
| **-n**                | Disables DNS resolution                                                    |
| **--disable-arp-ping**| Disables ARP ping (useful for stealth scanning)                            |
| **--packet-trace**    | Shows all sent and received packets                                        |
| **-v**/**-vv**        | Increases verbosity (-v = normal, -vv = more verbose)                      |
| **--stats-every=5s**  | Shows scan progress every 5 seconds                                        |

### Efficient Scanning Strategy

**Initial fast scan**


Get an overview quickly:


```jsx
sudo nmap -p- --min-rate=1000 -T4 <IP>
```

**Service version detection on open ports:**

```jsx
sudo nmap -sV -p <open-ports> <IP>
```

**Full verbose enumeration with progress:**

```
sudo nmap -p- -sV -vv --stats-every=5s <IP>

```

### Banner Grabbing (Manual + Nmap)

**Automatic (Nmap)**

```
Nmap grabs banners by making actual connections and reading responses.

Example output:
25/tcp open smtp Postfix smtpd
```

Internally, this may come from:

```
220 inlane ESMTP Postfix (Ubuntu)

```

### Manual (Netcat + Tcpdump)

```jsx
nc -nv <IP> 25
```

**Output:**

    220 inlane ESMTP Postfix (Ubuntu)

Simultaneously, observe the packets:

```jsx
sudo tcpdump -i eth0 host <your-IP> and <target-IP>
```

### Tips

- Use **--sS (SYN Stealth Scan)** for stealthier port scans.

- If you're being blocked, try scanning from different ports (--source-port 53).

- Use **-A** for aggressive detection (OS, script scanning, traceroute) – but noisy.