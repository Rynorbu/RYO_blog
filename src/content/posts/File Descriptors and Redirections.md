---
title: File Descriptors and Redirections
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

## What is a File Descriptor (FD)?

A **File Descriptor (FD)**
 is an integer reference used by the operating system to track open 
files, devices, and input/output (I/O) resources. When a process opens a
 file or a resource, the system assigns a unique FD, which acts as an 
identifier for subsequent operations. Conceptually, it functions like a 
ticket number that allows the system to locate and manage the associated
 resource.

In Unix/Linux systems, three standard FDs are predefined:

- **STDIN (FD 0)** – Standard input (where data is read from).
- **STDOUT (FD 1)** – Standard output (where normal results are displayed).
- **STDERR (FD 2)** – Standard error (where error messages are shown).

## Examples of STDIN, STDOUT, and STDERR

### STDIN and STDOUT Interaction

When a command such as `cat` is executed, it reads input from **STDIN** (typically the keyboard) and displays the output via **STDOUT** (the terminal). For example:

- Input: `SOME INPUT`
- Output: The same text is echoed back to the terminal.

### STDERR for Error Handling

If a command encounters an issue (e.g., insufficient permissions), the error message is sent to **STDERR** instead of STDOUT. For example:

- Running `find /etc/ -name shadow` may produce a "Permission denied" error, which appears in the terminal via STDERR.

## File Descriptor Redirection

### Redirecting STDERR to /dev/null

To suppress error messages, STDERR can be redirected to `/dev/null`, a special device that discards data:

```
find /etc/ -name shadow 2>/dev/null
```

### Redirecting STDOUT to a File

Normal output can be saved to a file instead of displaying it on the terminal:

```
find /etc/ -name shadow > results.txt
```

### Separating STDOUT and STDERR

Output and errors can be directed to different files:

```
find /etc/ -name shadow 1> stdout.txt 2> stderr.txt
```

### Redirecting STDIN from a File

Commands can read input from a file instead of keyboard input:

```
cat < input.txt
```

### Appending Output to a File

Using `>>` prevents overwriting and appends new data to an existing file:

```
find /etc/ -name passwd >> output.log
```

### Here Documents (<<) for Input Streams

A block of text can be passed as input until a specified delimiter (e.g., `EOF`) is encountered:

```
cat << EOF > document.txt
This is a multi-line
input block.
EOF
```

## Using Pipes (|)

Pipes allow the output of one command to serve as input for another:

```
find /etc/ -name *.conf 2>/dev/null | grep systemd
```

### Combining Multiple Commands with Pipes

Pipes can chain several commands for complex operations:

```
find /etc/ -name *.conf 2>/dev/null | grep systemd | wc -l
```

This example:

1. Searches for `.conf` files in `/etc/`.
2. Filters results containing "systemd".
3. Counts the number of matching files.