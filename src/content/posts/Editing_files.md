---
title: Editing Files
published: 2025-08-02
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

After learning how to create files and directories, the next step is to edit them. There are several text editors available in Linux, but we’ll start with Nano, as it is simple and easy to use.

**Using the Nano Editor**

Nano is a basic text editor that allows you to create and edit files quickly. To create or open a file using Nano, use this command:

```jsx
nano notes.txt
```

This will open the Nano editor, where you can start typing. At the bottom, you will see shortcut keys for various functions.

**Basic Nano Commands:**

```
[CTRL + W] → Search for text in the file.
[CTRL + O] → Save the file.
[CTRL + X] → Exit Nano.
[CTRL + K] → Cut text.
[CTRL + U] → Paste text.

```

After editing, press [CTRL + O] to save and [ENTER] to confirm. Then press [CTRL + X] to exit.

To view the contents of your file, use:

```jsx
cat notes.txt
```

**Understanding the /etc/passwd File** 

- This file stores information about users on the system, including their usernames, user IDs, group IDs, and home directories.
- Passwords used to be stored here, but now they are kept in /etc/shadow for better security.
- If permissions are not set correctly, attackers might exploit this file to gain unauthorized access.



### Using the Vim Editor

Vim (Vi IMproved) is a more advanced text editor than Nano. It is modal, meaning it has different modes for editing and running commands.

To open Vim, type:

```jsx
vim
```

**Vim Modes:**

- Normal Mode → Used for running commands (default mode).
- Insert Mode → Used for typing/editing text (Press i to enter).
- Visual Mode → Used for selecting text.
Command Mode → Used for running commands (: to enter).



**Basic Vim Commands:**

```
i → Enter insert mode.
ESC → Return to normal mode.
:w → Save the file.
:q → Quit Vim.
:wq → Save and quit.
:q! → Quit without saving.

```

**Learning Vim with Vimtutor**

Since Vim has many commands, it can feel difficult at first. To practice, use:

```jsx
vimtutor
```

This will guide you through the basics of Vim in about 30 minutes.
