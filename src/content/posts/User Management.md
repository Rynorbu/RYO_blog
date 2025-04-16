---
title: User Management
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

User management in Linux involves controlling system access, 
permissions, and resource allocation. System administrators create and 
manage user accounts, assign group memberships, and configure 
appropriate file permissions.

## User Accounts and Groups

### Basic Concepts

- **User Accounts**: Individual identities with unique login credentials
- **Groups**: Collections of users sharing common access privileges
- **Root User**: Superuser with full system access (UID 0)

## User Management Commands

### Account Operations

| Command | Description | Example |
| --- | --- | --- |
| **useradd** | Creates new user | **sudo useradd alex** |
| **usermod** | Modifies user properties | **sudo usermod -aG developers alex** |
| **userdel** | Deletes user account | **sudo userdel alex** |
| **passwd** | Changes password | **passwd** (current user) or **sudo passwd alex** |

### Group Management

| Command | Description | Example |
| --- | --- | --- |
| **addgroup** | Creates new group | **sudo addgroup developers** |
| **delgroup** | Removes group | **sudo delgroup developers** |
| **groups** | Shows user's groups | **groups alex** |

## Privilege Management

### Elevated Access

| Command | Description | Usage |
| --- | --- | --- |
| **sudo** | Execute command as root | **sudo cat /etc/shadow** |
| **su** | Switch user identity | **su - root** |

### Sudo Configuration

- Managed via **/etc/sudoers**
- Edited safely with **visudo** command
- Example entry: **alex ALL=(ALL) NOPASSWD: /usr/bin/apt**

## File Permissions and Security

### Important System Files

| File | Purpose | Permissions |
| --- | --- | --- |
| `/etc/passwd` | User account info | 644 (rw-r--r--) |
| `/etc/shadow` | Encrypted passwords | 640 (rw-r-----) |
| `/etc/group` | Group definitions | 644 (rw-r--r--) |

### Permission Management

- **chmod**: Change file permissions
- **chown**: Change file ownership
- **chgrp**: Change file group

## Best Practices

1. **Principle of Least Privilege**: Grant only necessary access
2. **Regular Audits**: Review user accounts and permissions periodically
3. **Password Policies**: Enforce strong passwords and regular changes
4. **Sudo Restrictions**: Limit root access through sudo
5. **Group Organization**: Use groups for shared resource access

## Example Workflow

1. Creating a new developer:

```
sudo useradd -m -s /bin/bash dev_user
sudo passwd dev_user
sudo addgroup developers
sudo usermod -aG developers dev_user
```

1. Granting controlled sudo access:

```
sudo visudo
# Add line: dev_user ALL=(ALL) NOPASSWD: /usr/bin/git
```

1. Setting up project directory:

```
sudo mkdir /var/project
sudo chown root:developers /var/project
sudo chmod 775 /var/project
```

## Security Considerations

- Always use **visudo** for editing sudoers file
- Regularly review **/etc/passwd** for unexpected accounts
- Monitor **/var/log/auth.log** for suspicious access attempts
- Disable root login via SSH in **/etc/ssh/sshd_config**