# Git - Restore

> Restore files to a previous state by discarding or unstaging changes.

<br>

# 🧠 Main Idea

`git restore` is used to **undo changes** (ctrl-z) in your working directory or remove files from the staging area.

It helps you safely recover files without modifying your commit history.

Think of it as **Git's Undo button**.

<br>

# 🤔 Why Do We Need It?

Without `git restore`:

- You couldn't easily discard unwanted changes.
- Accidentally staged files would be harder to fix.
- Recovering files would require more complex Git commands.

`git restore` makes undoing changes simple and safe.

<br>

# 📝 Syntax

Restore a file in the working directory:

```bash
git restore <file>
```

Restore multiple files:

```bash
git restore file1 file2
```

Restore all files:

```bash
git restore .
```

Unstage a file:

```bash
git restore --staged <file>
```

Restore both the working directory and staging area:

```bash
git restore --staged --worktree <file>
```

Restore a file from a specific commit:

```bash
git restore --source=<commit> <file>
```

<br>

# 💡 Real Example

Suppose you accidentally modified `main.c`.

Check the status:

```bash
git status
```

Discard the changes:

```bash
git restore main.c
```

Check again:

```bash
git status
```

The file is restored to its last committed version.

### Unstage a file

```bash
git add README.md
```

Oops! You didn't want to stage it.

```bash
git restore --staged README.md
```

The file is now removed from the staging area but your changes are still kept.

<br>

# ⚠️ Common Mistakes

❌ Thinking `git restore` recovers deleted commits.

`git restore` only works with files.

To recover commits, use commands such as:

```bash
git reflog
```

or

```bash
git reset`
```

<br>

❌ Running `git restore` without realizing changes will be lost.

```bash
git restore main.c
```

Any **uncommitted** changes in the file will be permanently discarded.

<br>

❌ Confusing `git restore` with `git reset`.

- `git restore` restores **files**.
- `git reset` moves **HEAD** and changes commit history.

<br>

❌ Forgetting `--staged` when unstaging files.

Without:

```bash
git restore --staged <file>
```

Git restores the working directory instead of removing the file from the staging area.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git status` | Check repository status |
| `git add` | Stage changes |
| `git diff` | View changes |
| `git reset` | Move HEAD or unstage files |
| `git checkout` | Legacy command for restoring files |
| `git commit` | Save changes permanently |

Typical workflow:

```text
Edit File
      ↓
git status
      ↓
Mistake?
      ↓
git restore
      ↓
Continue Working
```

<br>

# 🏋️ Mini Challenge

1. Create a repository.

2. Create a file:

```text
README.md
```

3. Commit it.

4. Modify the file.

5. Run:

```bash
git status
```

6. Restore it:

```bash
git restore README.md
```

Question:

What does `git status` show after restoring the file?

<br>

# 💭 Easy To Forget

There are two common uses of `git restore`:

Discard local changes:

```bash
git restore <file>
```

Unstage a file:

```bash
git restore --staged <file>
```

These perform **different** actions.

<br>

# 🧩 Cheat Sheet

```bash
git restore <file>

git restore .

git restore --staged <file>

git restore --staged --worktree <file>

git restore --source=<commit> <file>
```

<br>

# 📌 Summary

- `git restore` undoes changes to files.
- Use `git restore <file>` to discard local changes.
- Use `git restore --staged <file>` to unstage files.
- It does not change commit history.
- Be careful—discarded uncommitted changes cannot be recovered easily.
