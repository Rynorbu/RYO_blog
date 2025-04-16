---
title: Promp Description
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

### Understanding the Bash Prompt in Simple Terms

**What is the Bash Prompt?**

The Bash prompt is the text you see in the terminal when your system is waiting for you to enter a command. It tells you:

- Who you are (username).
- Which computer are you using (hostname).
- Where you are in the system (current directory or folder).

By default, it looks something like this:

```jsx
username@hostname:~$
```

- **username** → Login name.
- **hostname** → The name of the computer.
- **~** → The home directory (default folder).
- **$** → Shows you are a regular user.

If you are logged in as the root user (with full system access), the prompt changes:

```jsx
root@hostname:/root#
```

- **#** → Indicates you have admin (root) access.

**Why Doesn't the Prompt Always Show These Details?**

Sometimes, when you access another system (like during a penetration test or hacking exercise), the prompt may only show:

```jsx
$
```

This happens when the PS1 variable (which controls the prompt appearance) is not set correctly.
Customizing the Bash Prompt

We can change how your Bash prompt looks by modifying the PS1 variable in the .bashrc file. This lets you:

- Add colors and symbols.
- Show the time, date, or current IP address.
- Display the full directory path instead of just the folder name.

**For example,** if you want your prompt to show your username and full directory path:

```jsx
PS1="\u@\h:\w$ "
```

- \\u → Shows the username.
- \\h → Shows the hostname.
- \\w → Shows the full path of the current folder.

**Other useful codes:**

- \\d → Shows the date (e.g., Mon Feb 6).
- \\t → Shows the time in 24-hour format (HH:MM:SS).
- \\@ → Shows the time in 12-hour format (AM/PM).

**Making Terminal Look Better**

We can also customize the look and feel of our terminal by:
- Changing color schemes and fonts.
- Using tools like Powerline to make your prompt more stylish.
- Using a Bash Prompt Generator to easily create custom prompts.