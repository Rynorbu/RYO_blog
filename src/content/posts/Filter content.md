---
title: Filter content
published: 2025-04-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

In this section, we explore various tools and techniques for filtering and processing content directly from the command line. These tools are essential for efficiently handling large files and manipulating text without the need for external editors.

**More and Less**

Both more and less are pagers that allow you to view files one screen at a time. While more is simple, less offers more features like scrolling both forward and backward.

**Example:**

```jsx
cat /etc/passwd | more
```

This opens the file in more, where you can scroll through the content. Press [Q] to exit.

```jsx
less /etc/passwd
```

Similarly, less works, but unlike more, it doesn't leave the output visible when exited.

**Head and Tail**

When you want to view only the beginning or end of a file, head and tail are useful.

**Head:**

```jsx
head /etc/passwd
```

This command shows the first ten lines of the file.

**Tail:**

```jsx
tail /etc/passwd
```

This shows the last ten lines of the file. You can also use the -n flag to customize the number of lines.

**Sort**

To sort the contents of a file or output, use the sort command. For example:

```jsx
cat /etc/passwd | sort
```

This sorts the output alphabetically.

**Grep**

grep is a powerful tool for searching through text based on patterns. You can use it to filter content matching specific criteria.

**Example**:

```jsx
cat /etc/passwd | grep "/bin/bash"
```

This searches for lines containing "/bin/bash". Use the -v option to exclude matching lines:

```jsx
cat /etc/passwd | grep -v "false\|nologin"
```

**Cut**

To extract specific fields from text based on delimiters, cut is useful.

Example:

```jsx
cat /etc/passwd | cut -d ":" -f 1
```

This extracts the first field (the username) from each line, using ":" as the delimiter.

**Tr**

The tr command is used for translating or replacing characters in a stream of text.

**Example:**

```jsx
cat /etc/passwd | tr ":" " "
```

This replaces colons with spaces, making the output more readable.

**Column**

To format output in a table-like structure, use the column command.

**Example**:

```jsx
cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | column -t
```

This command pipes the output through column to neatly align it in columns.

**Awk**

awk is a versatile text-processing tool. You can use it to print specific fields from lines.

**Example:**

```jsx
**cat /etc/passwd | awk -F: '{print $1, $NF}'**
```

This prints the first and last fields from each line.

**Sed**

sed is a stream editor that allows you to modify text. A common use case is substituting patterns with s.

**Example:**

```jsx
cat /etc/passwd | sed 's/bin/HTB/'
```

This replaces all occurrences of "bin" with "HTB" in the output.

These tools combined allow for powerful and efficient text processing directly in the terminal. Experimenting with different commands and their options can help automate many tasks, especially when working with large datasets or system logs.

