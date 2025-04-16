---
title: Saving the Results
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Nmap
draft: false
---

## Saving Nmap Scan Results

When conducting scans with Nmap, it's essential to save the results for future reference. These results can help us analyze and compare different scanning methods. Nmap supports saving output in three different formats, and even allows saving all of them at once.

### Available Output Formats

| Format    | Option | File Extension | Description                              |
|-----------|--------|----------------|------------------------------------------|
| Normal    | **-oN**-  | **-.nmap**-        | Human-readable format                    |
| Grepable  | **-oG**  | **-.gnmap**       | Easily searchable by grep or scripts     |
| XML       | **-oX**  | **-.xml**         | Machine-readable format for tools and reports |

To save all formats simultaneously, use the **--oA**- option followed by a base filename.

### Example Command

```jsx
sudo nmap 10.129.2.28 -p- -oA target
```

This command will save the scan results in three formats: **-target.nmap**-, **-target.gnmap**-, and **-target.xml**-.

**Explanation:**

- **10.129.2.28**: The target IP address
- **p-**: Scans all 65535 TCP ports
- **oA target:** Saves output in **.nmap**, **.gnmap**, and **.xml** formats, using "target" as the base name

### Output Files

After the scan completes, you'll find three files in your current directory:

```jsx
$ ls
target.nmap  target.gnmap  target.xml
```

### Output Format Breakdown

### 1. Normal Output (target.nmap)

This format is human-friendly and good for quick review.

```jsx
$ cat target.nmap
# Nmap 7.80 scan initiated Tue Jun 16 12:14:53 2020
Nmap scan report for 10.129.2.28
Host is up (0.053s latency).
Not shown: 65525 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)
# Nmap done: 1 IP address (1 host up) scanned in 10.22 seconds
```

### 2. Grepable Output (target.gnmap)

Great for scripting and automation.

```jsx
$ cat target.gnmap
# Nmap 7.80 scan initiated Tue Jun 16 12:14:53 2020
Host: 10.129.2.28 () Status: Up
Host: 10.129.2.28 () Ports: 22/open/tcp//ssh///, 25/open/tcp//smtp///, 80/open/tcp//http///
# Nmap done: 1 IP address (1 host up) scanned in 10.22 seconds
```

### 3. XML Output (target.xml)

Ideal for advanced parsing and report generation.

```jsx
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE nmaprun>
<?xml-stylesheet href="file:///usr/local/bin/../share/nmap/nmap.xsl" type="text/xsl"?>
<nmaprun scanner="nmap" args="nmap -p- -oA target 10.129.2.28">
  <host starttime="...">
    <status state="up"/>
    <address addr="10.129.2.28" addrtype="ipv4"/>
    <address addr="DE:AD:00:00:BE:EF" addrtype="mac" vendor="Intel Corporate"/>
    <ports>
      <port protocol="tcp" portid="22"><state state="open"/><service name="ssh"/></port>
      <port protocol="tcp" portid="25"><state state="open"/><service name="smtp"/></port>
      <port protocol="tcp" portid="80"><state state="open"/><service name="http"/></port>
    </ports>
  </host>
</nmaprun>
```

### Converting XML to HTML

To make the XML output more readable for reports or presentations, convert it to HTML using the **xsltproc** tool:

```
xsltproc target.xml -o target.html
```

