← [Installing Git](../03-git-basics/README.md) | 🏠 [Home](../README.md) | → [Branching](../05-branching/README.md)

# Day 04 — Atomic Commits & Commit Practices

## Introduction

This section teaches you how to write commits the right way. A commit is more than just saving your work—it's a decision about *what* to save together and *why*. Learning to write atomic commits (small, focused changes) and thoughtful commit messages is the difference between a repository that tells a story and one that's just noise. You'll also learn how to navigate Git's documentation when you're stuck, configure your editor for longer commit messages, and recover from mistakes.

---

## Commands Covered

| Command | Purpose | Example |
|---------|---------|---------|
| `git commit -m "message"` | Create a commit with a short message | `git commit -m "Fix typo in README"` |
| `git commit` | Open an editor for a longer commit message | `git commit` (then type in VS Code) |
| `git commit --amend` | Edit the previous commit | `git commit --amend` |
| `git log` | View commit history | `git log` |
| `git log --oneline` | View history in compact format | `git log --oneline` |
| `git config --global core.editor "code --wait"` | Set your default editor | Makes VS Code open for commits |

---

## Why This Matters: The Philosophy of Commits

Before learning *how* to commit, you need to understand *why* commits matter.

A commit is a **snapshot** of your work at a specific moment. Unlike save files in a game (which are temporary), commits are permanent historical records. When you push your code to GitHub or work with teammates, every commit tells a story:

- Other developers can understand your thought process
- If a bug appears, you can find exactly which commit introduced it
- You can revert bad commits without losing good work
- Code reviews become easier when commits are focused

**Bad commits**: Everything changes at once ("Fixed stuff"), dozens of files, mixed features
**Good commits**: One logical change, clear message, purposeful grouping

---

## 🧭 Big Picture: The Commit Lifecycle

```
Working Directory
       ↓ (you make edits)
   Staging Area
       ↓ (git add)
   Repository
       ↓ (git commit)
   Commit History
```

Your edits start in your **working directory** (actual files on disk). When you're ready, you **stage** them with `git add`. Then you **commit** with `git commit`, creating a permanent snapshot. Each commit lives in the repository's history forever.

**The key decision**: What should go together in one commit?

---

## 📦 Core Concepts

### Atomic Commits

An **atomic commit** is a single, indivisible unit of work. "Atomic" means it can't be broken down further without losing meaning.

Think of it like writing a book:
- **Bad**: One chapter that introduces a character, adds a plot twist, and kills the character all together
- **Good**: One chapter that *only* introduces a character; the next chapter adds the plot twist

In code:
- **Bad**: One commit that adds a feature, fixes a bug, and refactors three functions
- **Good**: One commit for the feature, one for the bug fix, one for the refactor

Why this matters: If you need to undo the bug fix, you don't lose the feature.

### Commit Messages: Present Tense vs. Past Tense

Git officially recommends **present tense, imperative mood**:

```
✅ Good: "Add error handling to API calls"
❌ Not recommended: "Added error handling" or "Adds error handling"
```

**Imperative mood** means writing as if giving an order to the codebase:
- "Fix typo in header" (give an order)
- "Update user validation" (give an order)

Not:
- "Fixed typo in header" (past tense, describing what you did)
- "Updates user validation" (third person, awkward)

**The reality**: The Git community is split on this. Some projects use past tense; some use present. **The most important rule is consistency and following your team's guidelines.** If you're working solo, choose one and stick with it.

---

## 🔍 Navigating Git Documentation

Git has excellent documentation, but it's **overwhelming**.

### Where to Find Git Docs

Go to **https://git-scm.com** and click "Documentation" (or search "git documentation" in Google).

You'll see two main sections:

#### 1. **Reference Manual**
- Alphabetical listing of all commands
- Not a tutorial; just a reference
- Useful when you know the command but need details
- **Example**: You've used `git commit -m`, but want to see all available flags

#### 2. **Pro Git Book**
- Organized by topic with explanations and diagrams
- Friendly and educational
- Better for learning something new
- **Example**: You're learning about branching; the book explains it step-by-step

### How to Use These Resources

- **One-off question?** → Reference Manual
- **Learning a new concept?** → Pro Git Book
- **Feeling overwhelmed?** → That's normal. Even experienced developers find the docs intimidating

> 💡 **Code Wisdom**: You don't need to memorize all of Git. Knowing how to find the documentation is more valuable than memorizing every command.

---

## 💻 Deep Dive: Writing Better Commits

### The Two-Part Commit Workflow

For **short, simple commits** (one-line message):
```bash
git add <files>
git commit -m "Short, clear message"
```

For **detailed commits** (explanation needed):
```bash
git add <files>
git commit
# An editor opens. Write:
# First line: summary (one line, 50 characters)
# 
# Body: explain *why* you made this change (not *what* changed)
# Bullet points, paragraphs, whatever you need
```

### Why the First Line Matters

When you run `git log --oneline`, only the first line shows:

```bash
a3f7c9e Fix typo in README
b2d8e4f Add error handling to API
c1a9f3d Update user validation
```

That's why the **first line must be a complete summary**. If it's vague, no one (including future-you) will understand it.

### When to Write a Longer Message

Use a longer message when:
- The change is complex
- You need to explain *why* you made this decision (not what you changed)
- You're working with a team
- This might be reverted someday, and you need to explain your reasoning

**Example of a good longer message**:
```
Refactor authentication logic for security

Previously, passwords were stored in plain text in the session.
This exposed credentials if the session file was leaked.

Now we use bcrypt hashing and validate on every request.
This adds ~2ms overhead per request, which is acceptable given
the security benefit.

Fixes #142 (password storage vulnerability)
```

---

## ⚠️ Common Beginner Mistakes

### Mistake 1: Committing Everything at Once

**What happens**:
```bash
git add .
git commit -m "stuff"
```

**Why it's wrong**: You mixed 5 unrelated changes. If one is bad, you have to revert all of them.

**How to fix it**:
```bash
git add <specific file 1>
git commit -m "Feature X"
git add <specific file 2>
git commit -m "Bug fix Y"
```

### Mistake 2: Vague Commit Messages

**What happens**:
```bash
git commit -m "updates"
git commit -m "fixes"
git commit -m "changes"
```

**Why it's wrong**: Six months later, you have no idea what these commits do.

**How to fix it**:
- Use specific verbs: "Add", "Fix", "Remove", "Refactor", "Update"
- Include the *thing* you changed: "Fix typo in settings page", not "Fix typo"

### Mistake 3: Forgetting to Add a File

**What happens**:
```bash
git commit -m "Add validation"
# Then you realize: "Oh no, I forgot to add the schema file!"
```

**How to fix it**: Use `git commit --amend` (explained later in this section).

### Mistake 4: Waiting Too Long to Commit

**What happens**:
You work for 3 hours, changing 10 files. Now you have to decide: commit everything together (bad) or spend 30 minutes figuring out what goes together?

**How to fix it**: Commit *more often*. Aim for small, logical chunks throughout your day, not one massive dump at the end.

---

## 💡 Code Wisdom

> **"A good commit is like a good sentence: it completes one thought."**

When you're deciding whether to add another change to your current commit, ask: "Does this belong with what I just did?" If the answer is "not really," start a new commit.

---

## 📚 Configuring Your Editor for Longer Messages

### The VIM Problem

If you run `git commit` without `-m`, Git opens your **default editor** to write a message. On many systems, this is **VIM**, a very confusing text editor.

If you see something that looks like this:

```
~
~
~
:
```

You're in VIM. It's not broken. You just need to know:
1. Press `i` to enter insert mode
2. Type your message
3. Press `Escape` to exit insert mode
4. Type `:wq` and press Enter to save and quit

This is annoying. Let's configure a better editor.

### Using VS Code as Your Default Editor

Run this command **once**:

```bash
git config --global core.editor "code --wait"
```

Breaking this down:
- `git config --global` = "set this for all my Git repositories"
- `core.editor` = "the editor Git should use"
- `"code --wait"` = open VS Code and wait for me to close the file

The `--wait` flag is important. Without it, Git won't know when you're done editing.

### Checking Your Configuration

```bash
git config --list | grep editor
```

If it worked, you'll see:
```
core.editor=code --wait
```

### Using Your Configured Editor

Now, instead of:
```bash
git commit -m "message"
```

You can do:
```bash
git commit
```

VS Code opens. Write as long a message as you need. When you save and close the file, Git commits automatically.

### Other Editors

If you prefer a different editor, the documentation has options:
- Sublime: `git config --global core.editor "subl -w"`
- Nano: `git config --global core.editor "nano"`
- Any other editor follows the same pattern

---

## 🎯 Quick Reference: Commit Cheatsheet

```bash
# Commit with a message (use for quick, simple changes)
git commit -m "Clear description of what changed"

# Commit without -m flag (opens editor for longer messages)
git commit

# See your commit history
git log

# See compact version (one line per commit)
git log --oneline

# Fix the last commit (add forgotten file, fix typo in message)
git commit --amend

# Check what's staged before committing
git status
```

---

## 📋 Commit Message Checklist

Before hitting Enter, ask:

- [ ] Does the message use an action verb? (Add, Fix, Remove, Update, Refactor)
- [ ] Is the first line 50 characters or less?
- [ ] Does it describe *what changed*, not *how* you changed it?
- [ ] Would someone reading this 6 months from now understand why you made this change?
- [ ] Does this commit include one logical change, not 5 unrelated changes?

---

## What's Next

You now understand atomic commits and how to write them thoughtfully. Next (Day 05), you'll learn about **Branching**—how to create independent lines of development and work on multiple features simultaneously without interfering with the main codebase.


← [Installing Git](../03-git-basics/README.md) | 🏠 [Home](../README.md) | → [Branching](../05-branching/README.md)