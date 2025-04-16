---
title: Network Services
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

Your explanation covers a variety of essential network services, particularly SSH, NFS, and web servers, which are integral to penetration testing and system administration tasks. Here's a summary and some additional insights on each topic:

1. **SSH (Secure Shell)**

SSH is fundamental for securely managing remote Linux systems. You’ve mentioned OpenSSH, which is the most widely used SSH server. It's excellent for encrypted communication, preventing interception of sensitive data like passwords. 

It's essential for administrators and penetration testers to know how to configure and manage SSH services securely, especially by editing the **/etc/ssh/sshd_config** file to disable weak authentication methods, enforce key-based authentication, and limit login attempts.

**Key Concepts:**

```
Install OpenSSH:

```

```jsx
sudo apt install openssh-server -y
```

Check Server Status:

```jsx
systemctl status ssh
```

SSH Login:

```
ssh username@remote_host

```

Penetration testers also need to audit SSH configurations to ensure that weak configurations, such as allowing password authentication or having a high number of allowed login attempts, are not enabled.

**2. NFS (Network File System)**

NFS allows file sharing between Linux machines over a network. When setting up NFS, administrators can control which directories are shared and with which systems, ensuring only authorized users have access. 

NFS can be a useful target during penetration testing, as improper configurations (like "no_root_squash") can lead to privilege escalation opportunities.

**Key Concepts:**

```
Install NFS:

```

```jsx
sudo apt install nfs-kernel-server -y
```

Check NFS Server Status:

```jsx
systemctl status nfs-kernel-server
```

**Configure Shared Directories:** Edit /etc/exports and specify access rights such as rw for read-write access.

```jsx
/home/user/shared_folder client_ip(rw,sync)
```

**Mount NFS Share:**

```
mount server_ip:/path/to/share /local/mount_point

```

Penetration testers should check for weak configurations such as no_root_squash or async settings, which can result in access controls being bypassed or data inconsistencies.

**3. Web Servers**

Web servers are crucial targets during penetration tests. Apache and Nginx are the most widely used, but even lightweight servers like Python’s HTTP server can be useful in testing.

**Apache Configuration:**

The **/etc/apache2/apache2.conf** file allows fine-grained access control, and AllowOverride All in particular enables .htaccess files, which can introduce potential security risks if misconfigured. For example, weak permissions could allow an attacker to upload malicious scripts or gain unauthorized access.

**Key Concepts:**

```
Install Apache:

```

```jsx
sudo apt install apache2 -y
```

**Default Folder Access Configuration:** Edit /etc/apache2/apache2.conf:

```
<Directory /var/www/html>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

```

As a penetration tester, it is crucial to ensure the correct permissions are set, to check for directory traversal vulnerabilities, and to review the Apache logs for suspicious activity.

**Python Web Server:**

```
Install Python:

```

```jsx
sudo apt install python3 -y
```

**Start Python HTTP Server:**

```
python3 -m http.server

This starts a basic web server, useful for quick file sharing or testing a target system’s ability to interact with web-based services.

```

**Additional Penetration Testing Tips**

- **SSH Configuration:** Always disable root login and enforce the use of SSH keys over passwords. Monitor SSH logs for failed login attempts and brute-force attacks.
- **NFS Audits:** Ensure that NFS shares are restricted to only trusted systems, and disable root access where possible. Use root_squash to prevent root user access from clients.
- **Web Server Security:** Regularly patch web servers and disable unnecessary modules. Use security headers like Content-Security-Policy and Strict-Transport-Security to prevent common attacks like XSS and man-in-the-middle attacks.
