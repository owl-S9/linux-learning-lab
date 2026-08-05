# Git - Diff

> Show the differences between files, commits, branches, or the staging area.

<br>

# 🧠 Main Idea

`git diff` compares two versions of your project and displays exactly what has changed.

It helps you review modifications before staging, committing, or merging.

Think of it as **Git's comparison tool**.

<br>

# 🤔 Why Do We Need It?

Without `git diff`:

- You wouldn't know what changed.
- Reviewing code before committing would be difficult.
- Debugging changes would take much longer.

`git diff` lets you inspect changes before saving them.

<br>

# 📝 Syntax

```bash
git diff
```

Compare staged changes:

```bash
git diff --staged
```

Compare two commits:

```bash
git diff <commit1> <commit2>
```

Compare two branches:

```bash
git diff main feature/login
```

Compare one file:

```bash
git diff README.md
```

<br>

# 💡 Real Example

Modify `README.md`:

```bash
git diff
```

Output:

```diff
- Hello World
+ Hello Git
```

Stage it:

```bash
git add README.md
```

Now:

```bash
git diff
```

shows nothing.

Instead:

```bash
git diff --staged
```

shows the staged changes.

<br>

# ⚠️ Common Mistakes

❌ Thinking `git diff` shows staged changes.

Use:

```bash
git diff --staged
```

instead.

<br>

❌ Confusing `git diff` with `git log`.

- `git diff` → Changes
- `git log` → History

<br>

❌ Assuming `git diff` modifies files.

It only displays differences.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git status` | View repository status |
| `git add` | Stage changes |
| `git commit` | Save changes |
| `git show` | Display commit details |
| `git log` | View history |

Typical workflow:

```text
Edit Files
      ↓
git diff
      ↓
git add
      ↓
git diff --staged
      ↓
git commit
```

<br>

# 🏋️ Mini Challenge

Modify a file.

Run:

```bash
git diff
```

Stage it.

Run:

```bash
git diff --staged
```

Question:

Why are the outputs different?

<br>

# 💭 Easy To Forget

```text
git diff → Working Directory

git diff --staged → Staging Area
```

<br>

# 🧩 Cheat Sheet

```bash
git diff

git diff --staged

git diff HEAD

git diff main feature
```

<br>

# 📌 Summary

- Compare changes.
- Review before committing.
- Use `--staged` for staged files.
- Safe, read-only command.
