---
title: Navigation
published: 2025-08-03
description: "How to use this blog template."
<!-- # image: "../../assets/images/my_photo.jpg" -->
tags: ["Cyber"]
category: Linux
draft: false
---


## Introduction
Scanning performance plays a significant role when scanning extensive networks or dealing with low bandwidth. Nmap provides various options to control scan speed and accuracy.

## Timeout Optimization

### Default Scan Example
```bash
sudo nmap 10.129.2.0/24 -F`

- **Results**: 256 IPs scanned, 10 hosts up in 39.44 seconds

### Optimized RTT Scan

```

```
sudo nmap 10.129.2.0/24 -F --initial-rtt-timeout 50ms --max-rtt-timeout 100ms
```


- **Results**: 256 IPs scanned, 8 hosts up in 12.29 seconds
- **Tradeoff**: Found 2 fewer hosts but 4x faster

### Timeout Options

| Option | Description |
| --- | --- |
| `--initial-rtt-timeout` | Sets initial Round-Trip-Time timeout |
| `--max-rtt-timeout` | Sets maximum RTT timeout |

## Retry Optimization

### Default Scan

bash

Copy

```
sudo nmap 10.129.2.0/24 -F | grep "/tcp" | wc -l
```

- **Results**: 23 open ports found

### Reduced Retries Scan

bash

Copy

```
sudo nmap 10.129.2.0/24 -F --max-retries 0 | grep "/tcp" | wc -l
```

- **Results**: 21 open ports found
- **Tradeoff**: Faster but may miss some ports

## Packet Rate Control

### Default Scan

bash

Copy

```
sudo nmap 10.129.2.0/24 -F -oN tnet.default
```

- **Results**: 29.83 seconds

### Optimized Rate Scan

bash

Copy

```
sudo nmap 10.129.2.0/24 -F -oN tnet.minrate300 --min-rate 300
```

- **Results**: 8.67 seconds (same host/port count)

## Timing Templates

Nmap provides six timing templates:

| Template | Name | Description |
| --- | --- | --- |
| -T0 | Paranoid | Very slow, stealthy |
| -T1 | Sneaky | Slow, less conspicuous |
| -T2 | Polite | Slower than normal |
| -T3 | Normal | Default balanced speed |
| -T4 | Aggressive | Faster, may trigger defenses |
| -T5 | Insane | Very fast, likely detected |

### Default Timing (-T3)

bash

Copy

```
sudo nmap 10.129.2.0/24 -F -oN tnet.default
```

- **Results**: 32.44 seconds

### Insane Timing (-T5)

bash

Copy

```
sudo nmap 10.129.2.0/24 -F -oN tnet.T5 -T5
```

- **Results**: 18.07 seconds

## Performance Comparison

| Optimization Method | Default Time | Optimized Time | Hosts Found | Ports Found |
| --- | --- | --- | --- | --- |
| RTT Timeouts | 39.44s | 12.29s | 10 → 8 | N/A |
| Max Retries | N/A | N/A | Same | 23 → 21 |
| Min Rate 300 | 29.83s | 8.67s | Same | Same |
| -T5 Template | 32.44s | 18.07s | Same | Same |

## Best Practices

1. **Test Environment**: Always test settings in a controlled environment first
2. **Balance Speed/Accuracy**: Faster scans may miss important information
3. **Whitebox Advantage**: Use aggressive settings only when whitelisted
4. **Documentation**: Refer to [Nmap timing docs](https://nmap.org/book/performance-timing-templates.html)