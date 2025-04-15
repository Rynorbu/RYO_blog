---
title: Navigation
published: 2025-08-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

**Linux Navigation in Simple Terms**

When using Linux, moving around in the system is similar to how you use a mouse in Windows. You navigate through files and folders using commands. These commands help you find, list, and manage files and directories.

**1. Check Your Current Location**

To see where you are in the system, use the pwd command:

```jsx
pwd
```

**Example output:**

```jsx
/home/username
```

This tells you that you are inside the home directory.

**2. List Files and Folders**

To see what’s inside a directory, use the ls command:

```jsx
ls
```

**Example output:**

```jsx
Desktop  Documents  Downloads  Music  Pictures  Videos
```

This shows all the files and folders inside your current location.

To see more details (permissions, owner, size, and date modified), use:

```jsx
ls -l
```

**Example output:**

drwxr-xr-x  2 username  groupname  4096  Nov 13 17:37  Desktop

```jsx
drwxr-xr-x → File type and permissions
2 → Number of hard links
username → Owner
groupname → Group owner
4096 → Size in bytes
Nov 13 17:37 → Date modified
Desktop → File/Folder name

```

To see hidden files (files that start with a dot .), use:

```jsx
ls -la
```

**3. Change Directories**

To move into a folder, use cd:

```jsx
cd Documents
```

To go back to the previous directory:

```jsx
cd ..
```

To go directly to another directory, use the full path:

```jsx
cd /var/log
```

To return to the last directory you were in:

```jsx
cd -
```

**4. Auto-Complete**

Instead of typing long folder names, you can use the Tab key to complete them.
For example, if you type:

```jsx
cd /dev/s
```

Press Tab and Linux will suggest options like:

```jsx
shm/ snd/
```

If you type more letters, it will complete the folder name.

**5. Clear the Screen**

To clean up your terminal, use:

```jsx
clear
```

Or press Ctrl + L.

**6. Check Directory Contents Without Entering It**

You don’t need to enter a folder to check what’s inside. Instead, run:

```jsx
ls -l /var/log
```