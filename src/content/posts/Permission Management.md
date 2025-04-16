---
title: Permission Management
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

**Linux Permissions**

In Linux, permissions are like locks and keys for files and directories. These permissions determine who can open, modify, or execute a file or folder.

- **Read (r):** Allows viewing the content of a file.
- **Write (w):** Allows modifying the content of a file or directory.
- **Execute (x):** Allows running a file as a program or entering a directory.


Each file or directory has three types of "owners":

- **Owner:** The person who created the file (usually).
- **Group:** A set of users who share common permissions.
- **Others:** Everyone else.


When you see something like this:
-rwxr-xr--, it means:

```
Owner has read, write, and execute permissions (rwx).
Group has read and execute permissions (r-x).
Others have read-only permissions (r--).

```

**Changing Permissions**

You can change permissions using the chmod command. For example:


- **Adding permissions:** chmod a+r file gives read permissions to everyone.
- **Removing permissions:** chmod g-w file removes write permission for the group.


Permissions are also represented using numbers (called octal). For example:

```
7 = read (4) + write (2) + execute (1) → rwx
5 = read (4) + execute (1) → r-x

```

So, chmod 754 file will give:


- **Owner:** read, write, execute (rwx)
- **Group:** read, execute (r-x)
- **Others:** read (r--)

**Changing Owner**

You can also change the owner or group of a file using the chown command. For example:

```
chown root:admin file changes the owner to root and the group to admin.

```

**Special Permissions**

There are a few extra permissions for files:


- **SUID (Set User ID):** When set on a file, it allows the file to be run with the owner's permissions, not the user's.
- **SGID (Set Group ID):** Similar to SUID, but with group permissions.
- **Sticky Bit:** This is set on directories to prevent users from deleting or modifying files they don't own, even if they have write access to the directory.

For example, when you see a sticky bit on a directory like this:

```js  
drw-rw-r-t 
```

it means the sticky bit is set. This protects files inside the directory.