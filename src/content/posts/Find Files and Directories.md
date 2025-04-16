---
title: Find Files and Directories
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

When working with a Linux system, it's important to find the files and folders we need without manually checking each one. There are tools that can help us do this efficiently.

1. **which Command**

The which command helps us find the exact location of a program or tool in the system. For example, if we want to check if Python is installed and where it is located, we can run:

```jsx
which python
```

This will return something like:

```jsx
/usr/bin/python
```

If the program is not installed, it won't show any output.

**2. find Command**

The find command helps us locate files and folders based on different filters like name, size, owner, and modification date.

**Basic Syntax:**

```jsx
find <location> <options>
```

**Example:**

```jsx
find / -type f -name "*.conf" -user root -size +20k -newermt 2020-03-03 -exec ls -al {} \; 2>/dev/null
```

**What this does:**

- **type f** → Look for files only (not folders).
- **name "*.conf"** → Find files that have .conf in their name.
- **user root** → Show only files owned by the root user.
- **size +20k** → Find files larger than 20 KB.\
- **newermt 2020-03-03** → Find files modified after March 3, 2020.
- **exec ls -al {} \\;** → Show details (like permissions and size) of each found file.
- **2>/dev/null** → Hide any error messages.

**3. locate Command**

The locate command is a faster way to search for files because it uses a database instead of scanning the entire system. However, it may not show newly created files unless the database is updated.

**Updating the database:**

```jsx
sudo updatedb
```

Finding all .conf files quickly:

```jsx
locate *.conf
```

**Output example:**

- /etc/GeoIP.conf
- /etc/NetworkManager/NetworkManager.conf
- /etc/adduser.conf

**Limitations:** locate is fast but does not have advanced filters like find.