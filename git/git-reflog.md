# Git - Reflog

> Display the history of where HEAD and branch references have pointed.

<br>

# 🧠 Main Idea

`git reflog` records every movement of **HEAD**.

It allows you to recover commits that no longer appear in `git log`.

Think of it as **Git's safety net**.

<br>

# 🤔 Why Do We Need It?

Without `git reflog`:

- Recovering accidentally deleted commits would be much harder.
- Mistakes with `git reset` or `git rebase` could seem irreversible.

`git reflog` helps recover lost work.

<br>

# 📝 Syntax

View the reflog:

```bash
git reflog
```

Restore a previous state:

```bash
git reset --hard HEAD@{2}
```

<br>

# 💡 Real Example

View the reflog:

```bash
git reflog
```

Example:

```text
HEAD@{0}: reset: moving to HEAD~1
HEAD@{1}: commit: Add login
HEAD@{2}: commit: Initial commit
```

Recover:

```bash
git reset --hard HEAD@{1}
```

<br>

# ⚠️ Common Mistakes

❌ Thinking lost commits are gone forever.

Check:

```bash
git reflog
```

first.

<br>

❌ Confusing `git log` with `git reflog`.

`git log` shows commit history.

`git reflog` shows HEAD history.

<br>

❌ Using `--hard` carelessly.

Verify the target before resetting.

<br>

❌ Assuming reflog exists on GitHub.

Reflog is local only.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git log` | Commit history |
| `git reset` | Recover commits |
| `git rebase` | Rewrite history |
| `git checkout` | Move HEAD |

Typical workflow:

```text
Mistake
    ↓
git reflog
    ↓
Find HEAD
    ↓
git reset
```

<br>

# 🏋️ Mini Challenge

Create three commits.

Reset to the previous one.

Recover it using:

```bash
git reflog
```

Question:

Can you restore the missing commit?

<br>

# 💭 Easy To Forget

If you think you've lost a commit...

Check:

```bash
git reflog
```

before panicking.

<br>

# 🧩 Cheat Sheet

```bash
git reflog

git reset --hard HEAD@{1}

git reset --hard HEAD@{2}
```

<br>

# 📌 Summary

- `git reflog` records HEAD movements.
- It helps recover lost commits.
- Reflog is local only.
- Often used with `git reset`.
- One of Git's most valuable recovery tools.
