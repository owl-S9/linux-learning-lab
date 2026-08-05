# Git - Log

> Display the commit history of a Git repository.

<br>

# 🧠 Main Idea

`git log` shows the history of commits in a Git repository.

Each commit includes information such as:

- Commit ID (SHA)
- Author
- Date
- Commit message

Think of it as **Git's timeline** that records everything that has happened in your project.

<br>

# 🤔 Why Do We Need It?

Without `git log`:

- You can't see previous commits.
- You can't identify when changes were made.
- You can't find commit IDs for commands like `git checkout`, `git reset`, or `git revert`.
- Debugging and reviewing project history become much harder.

`git log` is one of the most important tools for understanding a repository.

<br>

# 📝 Syntax

Show the complete commit history:

```bash
git log
```

Show each commit on one line:

```bash
git log --oneline
```

Show the last *n* commits:

```bash
git log -n 5
```

or

```bash
git log --max-count=5
```

Display commits with a graph:

```bash
git log --graph
```

Show a compact graph with branch names:

```bash
git log --oneline --graph --decorate
```

Show commits affecting a specific file:

```bash
git log <file>
```

<br>

# 💡 Real Example

View the commit history:

```bash
git log --oneline
```

Example output:

```text
f82d9a1 Add login page
9bccc41 Fix authentication bug
c5sed7f Create README
a142cc2 Initial commit
```

Each line contains:

- Short commit ID
- Commit message

To see more details:

```bash
git log
```

<br>

# ⚠️ Common Mistakes

❌ Thinking the commit ID shown by `git log --oneline` is incomplete.

The short SHA is simply an abbreviated version of the full commit ID and is usually enough for Git commands.

<br>

❌ Forgetting that commits are shown from newest to oldest.

The most recent commit appears at the top of the list.

<br>

❌ Confusing `git log` with `git status`.

- `git status` shows the current state of your working directory.
- `git log` shows the repository's history.

<br>

❌ Assuming `git log` shows uncommitted changes.

`git log` only displays **committed** history.

Changes in the working directory or staging area do **not** appear until you create a commit.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git status` | View current repository status |
| `git show` | Display details of a specific commit |
| `git diff` | Compare changes |
| `git commit` | Create a new commit |
| `git reflog` | View reference history |
| `git reset` | Move to another commit |

Typical workflow:

```text
Edit Files
      ↓
git add
      ↓
git commit
      ↓
git log
      ↓
Find Commit ID
      ↓
git show / git reset
```

<br>

# 🏋️ Mini Challenge

1. Create three commits.

2. Display the history:

```bash
git log --oneline
```

3. Display only the last two commits:

```bash
git log -2
```

4. Display the history as a graph:

```bash
git log --oneline --graph
```

Question:

Can you identify the most recent commit and its SHA?

<br>

# 💭 Easy To Forget

Every commit has a **unique SHA (commit hash)**.

Many Git commands use this SHA, including:

```bash
git show

git checkout

git reset

git revert
```

You can obtain the SHA using:

```bash
git log
```

or

```bash
git log --oneline
```

<br>

# 🧩 Cheat Sheet

```bash
git log

git log --oneline

git log -5

git log --graph

git log --oneline --graph --decorate

git log README.md
```

<br>

# 📌 Summary

- `git log` displays the commit history of a repository.
- Every commit has a unique SHA and message.
- Use `--oneline` for a compact view.
- Use `--graph` to visualize branch history.
- `git log` only shows committed changes.
