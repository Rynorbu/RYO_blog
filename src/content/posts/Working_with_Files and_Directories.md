---
title: Working with Files and Directories
published: 2025-10-03
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Linux
draft: false
---

In Linux, we often use the terminal (command-line interface) instead of a graphical file manager like Windows Explorer to create, move, rename, and delete files. The terminal is faster and more powerful, allowing us to handle multiple files quickly

**1. Creating Files and Folders**

**Create a new file:**

```jsx
touch info.txt
```

(This creates an empty file called info.txt in the current directory.)

**Create a new folder (directory):**

```jsx
mkdir Storage
```

(This makes a folder called Storage in the current directory.)

**Create multiple folders inside each other:**

```jsx
mkdir -p Storage/local/user/documents
```

(This creates the whole folder structure in one command.)

**Check the folder structure:**

```jsx
tree .
```

(This shows all files and folders inside the current directory in a tree format.)

**2. Creating Files in Specific Folders**
    
**Create a file inside a folder:**
    
```jsx
touch Storage/local/user/userinfo.txt
```
    
(This creates userinfo.txt inside Storage/local/user/.)
    
**3. Renaming and Moving Files**
    
**Rename a file:**
    

```jsx
mv info.txt information.txt
```

(This renames info.txt to information.txt.)

**Move a file to a different folder:**

```
mv information.txt Storage/

(This moves information.txt into the Storage folder.)

```

**4. Copying Files**
    
**Copy a file to another location:**
    
```jsx
cp Storage/readme.txt Storage/local/
```
    
(This copies readme.txt from Storage/ to Storage/local/ without removing the original.)
    
**5. Deleting Files and Folders**
    
**Delete a file:**
    

```jsx
rm filename.txt
```

(This removes filename.txt permanently.)

**Delete an empty folder:**

```jsx
rmdir foldername
```

(This removes foldername only if it's empty.)

**Delete a folder with all its contents:**

```
rm -r foldername

(This removes foldername and everything inside it.)

```

**6. Editing Files**

Instead of using a GUI editor, you can edit files directly in the terminal:

Edit a file using nano (simple editor):

```jsx
nano filename.txt
```

(Opens the file for editing. Press CTRL + X, then Y, then Enter to save and exit.)

**Edit a file using vim (advanced editor):**

```
vim filename.txt
```

**Why Use the Terminal?**

- Faster than using a mouse and clicking through folders.
- More powerful, allowing you to work with multiple files at once.
- Essential for remote work, as Linux servers often don’t have a graphical interface.