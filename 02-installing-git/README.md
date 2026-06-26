← [What is Git](../01-what-is-git/README.md) | 🏠 [Home](../README.md) | → [Git Basics](../03-git-basics/README.md)

# Day 02 — Installing Git & Setting Up Your Development Environment

> *Before we can start tracking code with Git, we need to prepare our development environment. In this lesson, you'll learn the two main ways to use Git, install it on your computer, configure your identity, and set up a graphical tool that helps visualize Git workflows.*

---

# 📖 Introduction

Git is a command-line tool at its core, but today there are many graphical applications that make Git easier to use.

In this lesson you'll learn:

* The difference between using **Terminal** and **GUI** applications
* How to install Git
* How to verify that Git was installed correctly
* How to configure your Git identity
* How to install a graphical Git client (GitKraken)

Once these steps are complete, your computer will be ready for the rest of the course.

---

# 🧰 Commands Covered

| Command                                            | Purpose                                                | Example                                             |
| -------------------------------------------------- | ------------------------------------------------------ | --------------------------------------------------- |
| `git --version`                                    | Check whether Git is installed and display its version | `git --version`                                     |
| `git config --global user.name "Your Name"`        | Set your global Git username                           | `git config --global user.name "John Doe"`          |
| `git config --global user.email "you@example.com"` | Set your global Git email                              | `git config --global user.email "john@example.com"` |
| `git config user.name`                             | Display the configured username                        | `git config user.name`                              |
| `git config user.email`                            | Display the configured email                           | `git config user.email`                             |

---

# 🖥️ Big Picture

Before writing any code, your Git environment needs a small amount of setup.

```text
Install Git
      ↓
Verify Installation
      ↓
Configure Name
      ↓
Configure Email
      ↓
(Optional) Install GitKraken
      ↓
Ready to Start Using Git
```

There are also two different ways to interact with Git:

```text
                Git
               /   \
              /     \
     Terminal       GUI
(Command Line)   (Visual Interface)
```

Both perform the same Git operations.

The only difference is **how you interact with Git**.

---

# 💻 Terminal vs GUI

## What is the Terminal?

The **Terminal** (also called the **Command Line**) is a text-based interface where you type commands instead of clicking buttons.

Example:

```bash
git --version
```

Git was originally designed to be used this way, and most tutorials and official documentation use Terminal commands.

### Why use it?

* Works everywhere
* Faster once you're comfortable
* Gives you access to every Git feature
* Used by most professional developers

---

> 💡 **Code Wisdom**
>
> Learning the Terminal may feel slower at first, but it pays off quickly. Almost every Git tutorial, documentation page, and Stack Overflow answer assumes you're using the command line.

---

## What is a GUI?

A **GUI (Graphical User Interface)** lets you use Git through windows, buttons, and menus instead of typing commands.

Popular Git GUI applications include:

* GitKraken
* GitHub Desktop
* Sourcetree
* Tower

These applications are especially helpful for visualizing branches, commits, and project history.

### Why use a GUI?

* Easier for beginners
* More visual
* Less intimidating
* Great for understanding Git history

---

### Terminal vs GUI

| Terminal                     | GUI                                   |
| ---------------------------- | ------------------------------------- |
| Uses typed commands          | Uses buttons and menus                |
| Faster for experienced users | Easier for beginners                  |
| Supports every Git feature   | Some advanced features may be hidden  |
| Standard in documentation    | Different GUIs have different layouts |

Neither approach is "better."

Professional developers often use **both**.

They work from the Terminal for speed and use a GUI when they want a visual overview of the repository.

---

> 💡 **Code Wisdom**
>
> A GUI is an excellent learning tool, but understanding what happens behind each button click will make troubleshooting much easier later.

---

# ⚙️ Installing Git

Before using Git, it must be installed on your computer.

Most modern operating systems make this straightforward.

After installation, the first thing you should do is verify that Git is available.

Run:

```bash
git --version
```

Example output:

```text
git version 2.45.1
```

If Git prints its version number, the installation was successful.

---

## Why check the version?

This command answers two important questions:

* Is Git installed?
* Which version is currently running?

Newer Git versions include new features and improvements, so keeping Git reasonably up to date is recommended.

---

> 💡 **Code Wisdom**
>
> Whenever Git behaves differently from an online tutorial, checking your Git version is one of the first troubleshooting steps.

---

# 👤 Configuring Your Git Identity

Git records **who made each change**.

Whenever you create a commit, Git stores:

* Your name
* Your email address

This information becomes part of your project's history.

Without configuring your identity, Git won't know who created future commits.

---

## Configure Your Name

```bash
git config --global user.name "Your Name"
```

Example:

```bash
git config --global user.name "John Doe"
```

This sets your name for all Git repositories on your computer.

---

## Configure Your Email

```bash
git config --global user.email "john@example.com"
```

Git uses this email to associate commits with you.

If you plan to use GitHub later, it's a good idea to use the same email address that you'll use for your GitHub account.

---

## Verify Your Configuration

Check your configured name:

```bash
git config user.name
```

Check your configured email:

```bash
git config user.email
```

Git should display the values you configured earlier.

---

## What does `--global` mean?

The `--global` option tells Git:

> "Use these settings for every repository on this computer."

Without `--global`, the configuration only applies to the current project.

You'll learn about local configuration later in the course.

---

> 💡 **Code Wisdom**
>
> Your Git identity is **not** a password and is **not** connected to an account by itself. It's simply metadata stored inside your commits.

---

# 🖼️ Installing GitKraken

GitKraken is a graphical Git client.

It does **not replace Git**.

Instead, it provides a visual interface for working with Git repositories.

Throughout this course, GitKraken is used mainly to help visualize concepts like:

* Commit history
* Branches
* Merges
* File changes

Even when using GitKraken, Git is still doing the actual work behind the scenes.

---

## Do I have to use GitKraken?

No.

Everything in this course can be done from the Terminal.

GitKraken simply makes many Git concepts easier to understand visually.

---

> 💡 **Code Wisdom**
>
> Beginners often think GitKraken is "another version of Git." It isn't. It's simply another way to interact with the same Git installation.

---

# ⚠️ Common Beginner Mistakes

### Forgetting to configure name and email

Git commits need author information.

Always configure your identity before creating your first repository.

---

### Thinking GitHub and Git are the same thing

Git is the version control system.

GitHub is a website that hosts Git repositories.

They are related, but they are different tools.

---

### Depending only on a GUI

GUIs are helpful, but eventually you'll encounter documentation or tutorials that use Terminal commands.

Learning both approaches will make you much more flexible.

---

### Ignoring the Git version

Some tutorials use newer Git features.

If something doesn't work as expected, compare your Git version with the tutorial.

---

# 🖥️ Mac vs Windows

The overall Git workflow is identical on both operating systems.

The main differences are during installation:

| macOS                           | Windows                                    |
| ------------------------------- | ------------------------------------------ |
| Git is often already installed  | Git usually needs to be installed manually |
| Uses the built-in Terminal      | Commonly uses Git Bash                     |
| Installation is usually simpler | Includes Git Bash during setup             |

Once installation is complete, almost every Git command you'll learn works exactly the same on both systems.

---

# 📚 Quick Reference

```bash
# Check Git version
git --version

# Configure your name
git config --global user.name "Your Name"

# Configure your email
git config --global user.email "you@example.com"

# View configured name
git config user.name

# View configured email
git config user.email
```

---

# ✅ End of Section

Your Git environment is now ready.

You have:

* Installed Git
* Verified the installation
* Configured your identity
* Learned the difference between Terminal and GUI tools
* Installed a graphical Git client for visualization

In the next lesson, we'll start creating repositories and using Git to track real projects.
