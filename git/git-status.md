# Git - Status

> Show the current state of the working directory and staging area.

<br>

# 🧠 Main Idea

`git status` displays the current state of your Git repository.

It shows:

- Which files have been modified.
- Which files are staged for the next commit.
- Which files are untracked.
- Which branch you're currently on.
- Whether your branch is ahead of, behind, or up to date with the remote repository.

Think of it as **Git's dashboard**.

<br>

# 🤔 Why Do We Need It?

Without `git status`:

- You may commit the wrong files.
- You may forget to stage important changes.
- You won't know if your repository is clean.
- You can easily lose track of your work.

It is one of the safest commands in Git because it never changes anything—it only reports the current state.

<br>

# 📝 Syntax

Show repository status:

```bash
git status
```

Show a shorter, compact output:

```bash
git status --short
```

Show branch information:

```bash
git status --branch
```

Show both short output and branch information:

```bash
git status --short --branch
```

<br>

# 💡 Real Example

Check the repository status:

```bash
git status
```

Example output:

```text
On branch main

Changes to be committed:
    modified: README.md

Changes not staged for commit:
    modified: main.c

Untracked files:
    notes.txt
```

Meaning:

- `README.md` is staged.
- `main.c` has been modified but not staged.
- `notes.txt` is not being tracked by Git.

<br>

# ⚠️ Common Mistakes

❌ Ignoring `git status` before committing.

Always check what is staged before running:

```bash
git commit
```

<br>

❌ Confusing "Modified" with "Staged".

Modified files are **not** included in the next commit until you stage them using:

```bash
git add
```

<br>

❌ Forgetting about untracked files.

New files are ignored until you explicitly add them:

```bash
git add <file>
```

<br>

❌ Thinking `git status` changes files.

It is a read-only command.

It never modifies your repository.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git add` | Stage changes |
| `git commit` | Save staged changes |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |
| `git restore` | Discard changes |
| `git log` | View commit history |

Typical workflow:

```text
Edit Files
      ↓
git status
      ↓
git add
      ↓
git status
      ↓
git commit
      ↓
git status
```

<br>

# 🏋️ Mini Challenge

1. Create a new repository.

2. Create a file:

```text
README.md
```

3. Run:

```bash
git status
```

4. Stage the file:

```bash
git add README.md
```

5. Run:

```bash
git status
```

Question:

How does the output change after staging the file?

<br>

# 💭 Easy To Forget

A **clean working tree** means there are no changes to commit.

Example:

```text
On branch main

nothing to commit, working tree clean
```

Seeing this message means your local repository is synchronized with your latest commit.

<br>

# 🧩 Cheat Sheet

```bash
git status

git status --short

git status --branch

git status --short --branch
```

<br>

# 📌 Summary

- `git status` shows the current state of your repository.
- It displays staged, unstaged, and untracked files.
- It tells you which branch you're on.
- It never changes your files.
- Run `git status` frequently to avoid mistakes.
