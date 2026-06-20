# Day 00 — Terminal Basics

Before learning Git, you need to know how to navigate your computer using the terminal.
These are the essential commands you'll use throughout the entire course.

> 💡 **Why does this matter?** Every Git command runs in the terminal. Knowing your way around saves you from confusion later.

---

## Commands Covered

| Command | What it does | Example |
|---------|-------------|---------|
| `ls` | List files and folders in current location | `ls` |
| `ls <folder>` | List contents of a specific folder | `ls pets` |
| `pwd` | Print your current location | `pwd` |
| `cd <folder>` | Move into a folder | `cd documents` |
| `cd ..` | Go back one folder | `cd ..` |
| `touch <file>` | Create a new empty file | `touch notes.txt` |
| `mkdir <name>` | Create a new folder | `mkdir my-project` |
| `rm <file>` | Delete a file (permanent!) | `rm notes.txt` |
| `rm -rf <folder>` | Delete a folder and everything in it | `rm -rf my-folder` |
| `clear` | Clear the terminal screen | `clear` |
| `open .` | Open current folder in Finder — Mac only | `open .` |
| `start .` | Open current folder in File Explorer — Windows only | `start .` |

---

## Key Concepts

### Where am I? — pwd
When you open the terminal, you start at your home directory, shown as ~
pwd tells you the exact path to where you are right now.

```bash
pwd
# Mac:     /Users/yourname
# Windows: C:/Users/yourname
```

### What's here? — ls

```bash
ls            # show contents of current folder
ls pets       # show contents of the pets folder
ls pets/cats  # show contents of a nested folder
```

### Moving around — cd

```bash
cd documents    # go into documents
cd ..           # go back one level
cd ../..        # go back two levels
```

> ⚠️ Windows tip: You can't switch drives with cd. Type F: first, then use cd.

### Creating files — touch

```bash
touch index.html              # one file
touch style.css script.js    # multiple files at once
```

### Creating folders — mkdir

```bash
mkdir my-project          # one folder
mkdir src tests docs      # multiple folders at once
```

> ⚠️ No spaces in names! Use - or _ instead.
> mkdir my project → creates TWO folders
> mkdir my-project → creates ONE folder

### Deleting — rm

```bash
rm notes.txt        # delete a file
rm -rf my-folder    # delete a folder and all its contents
```

> 🔴 Warning: No undo. Deleted files do NOT go to Trash.

---

## Mac vs Windows

| Action | Mac / Git Bash | Windows CMD |
|--------|---------------|-------------|
| Open current folder | open . | start . |
| Path separator | / | \ |

---

## Quick Reference

```bash
pwd           # where am I?
ls            # what's here?
cd <folder>   # go into folder
cd ..         # go back
touch <file>  # create file
mkdir <name>  # create folder
rm <file>     # delete file
rm -rf <dir>  # delete folder
clear         # clean up terminal
```

> Next: 01 — What is Git?