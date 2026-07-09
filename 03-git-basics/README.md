← [Installing Git](../02-installing-git/README.md) | 🏠 [Home](../README.md) | → [Branching](../04-atomic-commits/README.md)

# 🚀 Day 03 — Git Fundamentals



Welcome to **Day 03** of learning Git!

If you've never used a terminal, written a line of code, or worked with version control before, you're in the right place.

In this section you'll learn:

- What Git actually is
- What a Git Repository (Repo) is
- How to create your first repository
- How to inspect your repository
- Why the hidden `.git` folder is important
- Common beginner mistakes
- The complete committing workflow (coming next)

By the end of this lesson, you'll understand the foundation that every Git user builds upon.

---

# 📚 Commands Covered

| Command | Purpose | Example |
|---------|---------|---------|
| `git init` | Creates a new Git repository | `git init` |
| `git status` | Shows the current state of your repository | `git status` |
| `git add` | Stages changes before committing | `git add index.html` |
| `git commit -m "message"` | Saves a snapshot of staged changes | `git commit -m "Create homepage"` |
| `git log` | Displays commit history | `git log` |

---

# 🌱 Before We Start

Git is a **Version Control System**.

That sounds complicated, but the idea is actually simple.

Imagine you're writing a book.

Without Git, your computer might end up looking like this:

```
Essay.docx

Essay_Final.docx

Essay_Final_Real.docx

Essay_Final_Really_Final.docx

Essay_Final_Last_Version.docx
```

This quickly becomes confusing.

Git solves this problem.

Instead of creating dozens of copies, Git remembers every important version of your project.

Think of Git as a time machine for your work.

Whenever you save an important milestone, Git remembers it forever.

---

# 📦 What Is a Git Repository?

A **repository** (or **repo**) is simply a project folder that Git is tracking.

Example project:

```
Portfolio/

├── index.html
├── style.css
└── script.js
```

Right now it's just a normal folder.

Git isn't watching it yet.

Once you initialize Git, this folder becomes a repository.

Now Git can remember:

- file changes
- project history
- previous versions
- future updates

Every Git project begins as an ordinary folder.

---

# 🚀 git init

This is the first Git command you'll usually run.

It tells Git:

> "Start tracking this project."

Suppose you've created a folder called:

```
MyWebsite
```

Open your terminal.

Move inside the folder.

```bash
cd MyWebsite
```

Now initialize Git.

```bash
git init
```

You'll see something similar to:

```text
Initialized empty Git repository...
```

Congratulations!

Your project is now a Git repository.

---

## 🧠 Code Wisdom

> You only need to run `git init` **once** for a project.
>
> Running it repeatedly won't create multiple repositories—it simply isn't necessary.

---

# 🔍 git status

This command answers one important question:

> "What is happening in my repository right now?"

Whenever you're unsure, run:

```bash
git status
```

Example:

```text
On branch main

No commits yet

nothing to commit
```

Everything is clean.

Now imagine you create a new file:

```
notes.txt
```

Run:

```bash
git status
```

Git might respond with:

```text
Untracked files:

notes.txt
```

Git is basically saying:

> "I found this file, but I'm not tracking it yet."

As your project grows, `git status` becomes your best friend.

It tells you:

- what changed
- what Git is tracking
- what isn't tracked
- what will be committed

---

## 🧠 Code Wisdom

> Professional developers constantly use `git status`.
>
> If you're ever confused, don't guess.
>
> Ask Git.

---

# 📁 The Hidden `.git` Folder

After running:

```bash
git init
```

Git creates a hidden folder called:

```
.git
```

You usually won't see it unless hidden files are visible.

This folder is incredibly important.

It stores:

- project history
- branches
- commits
- repository configuration
- internal Git data

Your project might now look like this:

```
MyWebsite/

├── .git
├── index.html
├── style.css
└── script.js
```

Everything Git knows lives inside `.git`.

Delete this folder…

…and Git forgets everything.

Your project becomes an ordinary folder again.

---

## 🧠 Code Wisdom

> Never edit files inside `.git`.
>
> Think of it as Git's brain.
>
> If you damage it, your repository can become unusable.

---

# ⚠️ Common Beginner Mistakes

## Mistake #1 — Running `git init` in the Wrong Folder

Always check where you are before initializing Git.

Bad:

```
Desktop/

Homework/

Projects/

Downloads/
```

If you're inside `Desktop` and run:

```bash
git init
```

Git starts tracking your entire Desktop.

That's probably not what you wanted.

Instead:

```
Projects/

Calculator/
```

Move into your project first.

```bash
cd Calculator
```

Then run:

```bash
git init
```

---

## Mistake #2 — Creating a Repository Inside Another Repository

Bad example:

```
Portfolio/

├── .git

└── Practice/

    └── .git
```

This creates unnecessary confusion.

A better structure is:

```
Projects/

Portfolio/
    .git

Calculator/
    .git

WeatherApp/
    .git
```

Each project should normally have **one repository**.

---

## 🧠 Code Wisdom

> Before typing `git init`, ask yourself:
>
> "Am I inside the project I actually want Git to track?"

---

# 💻 Mac vs Windows

The Git commands are exactly the same.

The only difference is the terminal application.

### Windows

- Git Bash (recommended)
- PowerShell
- Command Prompt

### macOS

- Terminal

Everything you learn in this course works the same on both operating systems.

---

# 🎯 What We've Learned So Far

At this point you know how to:

✅ Create a Git repository

✅ Understand what a repository actually is

✅ Check the current state of your project

✅ Understand why the hidden `.git` folder exists

✅ Avoid the most common beginner mistakes

But there's one major problem...

Right now Git can **see** your project, but it **isn't actually saving your work yet**.

Git doesn't automatically remember every change you make.

Instead, Git follows a simple workflow that gives you complete control over what gets saved.

In the next section, we'll learn the most important workflow in Git:

**Working Directory → Staging Area → Commit**

This workflow is the heart of Git, and once you understand it, everything else becomes much easier.


# 🔄 The Git Committing Workflow

Git doesn't save every change automatically.

Instead, every change moves through **three simple stages** before it becomes part of your project's history.

Understanding this workflow is the key to understanding Git.

```
Working Directory
        │
        ▼
 Staging Area
        │
        ▼
     Repository
    (Commit History)
```

Let's break each step down.

---

# 📝 Step 1 — Working Directory

The **Working Directory** is simply your project folder.

Every time you:

- create a file
- edit a file
- delete a file

you're making changes here.

Example:

```
Portfolio/

├── index.html
├── style.css
└── script.js
```

Suppose you edit:

```
index.html
```

At this moment, Git notices something changed.

But it **doesn't save it yet**.

Think of the Working Directory as your desk while you're writing.

Your work exists...

...but it hasn't been officially filed away.

---

## 🧠 Code Wisdom

> Editing a file does **not** create a Git history.
>
> Until you commit, Git simply knows something changed.

---

# 📦 Step 2 — The Staging Area

The **Staging Area** acts like a shopping cart.

Instead of saving every file immediately, Git lets you choose exactly which changes belong in the next snapshot.

That's where `git add` comes in.

---

# ➕ git add

`git add` moves changes from the Working Directory into the Staging Area.

Example:

You edited:

```
index.html
```

Now run:

```bash
git add index.html
```

Git says:

> "Got it. I'll include this file in the next commit."

Want to stage every changed file?

```bash
git add .
```

The period (`.`) means:

> "Everything inside this folder."

This is one of the most commonly used Git commands.

---

### Example Workflow

Create a new file:

```
about.html
```

Check Git:

```bash
git status
```

Output:

```text
Untracked files:

about.html
```

Now stage it:

```bash
git add about.html
```

Check again:

```bash
git status
```

Now Git shows:

```text
Changes to be committed
```

The file is ready.

It isn't saved forever yet...

...it's simply waiting.

---

## 🧠 Code Wisdom

> Staging lets you decide **exactly** what belongs in one commit.
>
> Professional developers rarely commit every changed file blindly.

---

# 💾 Step 3 — git commit

A **commit** is a permanent snapshot of your project.

Think of it like pressing **Save** in a video game.

Once committed, Git remembers exactly how every tracked file looked at that moment.

Create your first commit:

```bash
git commit -m "Create homepage"
```

The `-m` stands for:

**message**

Every commit should include a short description explaining **why** the change was made.

After committing:

```
Working Directory

↓

Staging Area

↓

Repository ✓
```

The snapshot becomes part of your project's history.

---

## 🧠 Code Wisdom

> A commit is not just a backup.
>
> It tells the story of how your project evolved over time.

---

# ✍️ Writing Good Commit Messages

A good commit message should answer:

> "What changed?"

Good examples:

```bash
git commit -m "Create homepage"

git commit -m "Fix navigation bug"

git commit -m "Add contact page"

git commit -m "Update README"
```

Poor examples:

```bash
git commit -m "Stuff"

git commit -m "Changes"

git commit -m "asdf"

git commit -m "Final"
```

Imagine returning to this project six months later.

Which messages would actually help you?

---

## 🧠 Code Wisdom

> Your future self is one of the people reading your commit history.
>
> Write commit messages that you'll understand months later.

---

# 📜 git log

How do you see previous commits?

Use:

```bash
git log
```

Example output:

```text
commit 84b19c...

Author: John Doe

Date: ...

Create homepage

commit 4d91ef...

Add navigation bar
```

Each commit receives its own unique ID.

Git stores:

- who made the commit
- when it happened
- the commit message
- the complete project snapshot

Think of `git log` as your project's timeline.

---

## 🧠 Code Wisdom

> Every commit becomes part of your project's history.
>
> A clean commit history makes debugging and teamwork dramatically easier.

---

# 🔄 Putting Everything Together

Let's walk through a complete example.

Create a project:

```bash
mkdir Calculator

cd Calculator

git init
```

Create a file:

```
index.html
```

Check Git:

```bash
git status
```

Stage it:

```bash
git add index.html
```

Commit it:

```bash
git commit -m "Create calculator homepage"
```

View history:

```bash
git log
```

Congratulations!

You've completed the full Git workflow.

---

# 💻 Mac vs Windows

The commands are identical.

Only the terminal application changes.

Windows:

- Git Bash
- PowerShell
- Command Prompt

macOS:

- Terminal

---

# ⚡ Complete Quick Reference

```bash
# Go inside a project
cd MyProject

# Initialize Git
git init

# Check repository status
git status

# Stage one file
git add index.html

# Stage every changed file
git add .

# Create a commit
git commit -m "Describe your changes"

# View commit history
git log
```

---

# 🎯 Day 01 Summary

Today you learned the core ideas that every Git user relies on:

✅ What Git is

✅ What a Git repository is

✅ How to initialize a repository

✅ How to inspect repository status

✅ Why the `.git` folder exists

✅ The three-step Git workflow

✅ How to stage changes with `git add`

✅ How to create commits with `git commit`

✅ How to write meaningful commit messages

✅ How to view your project's history using `git log`

These concepts form the foundation of everything you'll do with Git. In future lessons, you'll build on this workflow by learning how to compare changes, work with branches, collaborate through GitHub, and recover from mistakes with confidence.

Happy coding! 🚀


← [Installing Git](../02-installing-git/README.md) | 🏠 [Home](../README.md) | → [Branching](../04-atomic-commits/README.md)
>>>>>>> a858840 (Add day 04 and edited the main README.md)
