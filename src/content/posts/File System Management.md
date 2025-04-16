---
title: File System Management
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

**Key Linux File Systems**

- **ext2:** Older, no journaling. Good for low-overhead needs like USB drives.
- **ext3:** Adds journaling (better crash recovery) compared to ext2.
- **ext4:** The default on most Linux systems, offering improved performance, reliability, and large file support.
- **Btrfs:** Known for advanced features like snapshots, checksums, and data integrity checks.
- **XFS:** Great for handling large files with high I/O performance.
- **NTFS:** Mainly for Windows, but Linux can use it for compatibility with dual-boot systems or external drives.


**File System Hierarchy & Structure**


- Linux uses a hierarchical directory structure, where directories contain files and subdirectories.
- **Inodes:** Store metadata about files and directories (permissions, ownership, etc.), but not actual file data.


**Common File Types**

- **Regular files:** Can store text, binary data, images, etc.
- **Directories:** Contain files or other directories.
- **Symbolic Links (Symlinks):** Shortcuts pointing to other files or directories, providing quick access without duplicating files.


**Disk Management Tools**

- **fdisk:** A tool for partitioning disks and displaying partition tables. 

**For example:**
```jsx
sudo fdisk -l
```

**gparted and GParted:** Alternatives for graphical disk partitioning.


**Mounting File Systems**

Mounting makes a partition accessible under the directory structure. You can mount partitions using:

```jsx
sudo mount /dev/sdb1 /mnt/usb
```

To automatically mount a file system at boot, entries are added to **/etc/fstab.**

**Unmounting File Systems**

To unmount, ensure no processes are using the filesystem. Use:

```jsx
**sudo umount /mnt/usb**
```

If processes are using the file system, use lsof to identify them.

**Automating Mount/Unmount**

You can configure mount and unmount behavior via **/etc/fstab:**


- Add noauto to prevent mounting at boot.
- Add the noauto option to automatically unmount at shutdown.

**Permissions and Ownership**

Linux permissions allow defining access control for files, specifying who can read, write, or execute them. Users, groups, and others may have different levels of access.

