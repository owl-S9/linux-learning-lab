# Git - Reset

> Move the current branch to a different commit and optionally reset the staging area and working directory.

<br>

# 🧠 Main Idea

`git reset` changes where **HEAD** and the current branch point.

Depending on the option you use, it can:

- Move the current branch to another commit.
- Unstage files.
- Discard local changes.

Think of it as **rewinding your Git history**.

<br>

# 🤔 Why Do We Need It?

Without `git reset`:

- You couldn't easily undo recent commits.
- Removing files from the staging area would be less convenient.
- Recovering from mistakes before pushing would be more difficult.

`git reset` is a powerful tool for rewriting **local** Git history.

<br>

# 📝 Syntax

Move the current branch to a commit (default: `--mixed`):

```bash
git reset <commit>
```

Unstage files without changing the working directory:

```bash
git reset <file>
```

Keep your changes but remove the commit:

```bash
git reset --soft <commit>
```

Remove commits and unstage changes:

```bash
git reset --mixed <commit>
```

Remove commits and discard all changes:

```bash
git reset --hard <commit>
```

Reset to the previous commit:

```bash
git reset --hard HEAD~1
```

<br>

# 💡 Real Example

Suppose your history looks like this:

```text
A --- B --- C (HEAD)
```

Remove the last commit but keep the changes staged:

```bash
git reset --soft HEAD~1
```

Result:

```text
A --- B (HEAD)
```

The changes from commit `C` are still staged.

<br>

Discard the last commit and all its changes:

```bash
git reset --hard HEAD~1
```

Result:

```text
A --- B (HEAD)
```

Commit `C` and its uncommitted changes are removed from your local repository.

<br>

# ⚠️ Common Mistakes

❌ Using `git reset --hard` without understanding the consequences.

```bash
git reset --hard HEAD~1
```

This permanently discards uncommitted changes in your working directory.

<br>

❌ Using `git reset` after pushing commits.

If other developers have already pulled your commits, resetting and force-pushing can rewrite shared history.

In most collaborative situations, prefer:

```bash
git revert
```

instead.

<br>

❌ Confusing `--soft`, `--mixed`, and `--hard`.

```text
--soft
✔ Move HEAD
✔ Keep staging area
✔ Keep working directory

--mixed (Default)
✔ Move HEAD
✔ Reset staging area
✔ Keep working directory

--hard
✔ Move HEAD
✔ Reset staging area
✔ Reset working directory
```

<br>

❌ Confusing `git reset` with `git restore`.

- `git reset` primarily moves commits and unstages changes.
- `git restore` restores files without moving commit history.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git restore` | Restore files |
| `git revert` | Undo a commit safely |
| `git commit` | Save changes |
| `git reflog` | Recover lost commits |
| `git log` | View commit history |
| `git status` | Check repository status |

Typical workflow:

```text
Mistake?
      ↓
git log
      ↓
Choose Commit
      ↓
git reset
      ↓
Continue Working
```

<br>

# 🏋️ Mini Challenge

1. Create three commits.

2. View the history:

```bash
git log --oneline
```

3. Reset to the previous commit:

```bash
git reset --soft HEAD~1
```

4. Run:

```bash
git status
```

Question:

Are your changes still staged?

Repeat the exercise with:

```bash
git reset --mixed HEAD~1
```

and compare the results.

<br>

# 💭 Easy To Forget

`git reset` rewrites **local history**.

If a commit has already been pushed to GitHub and shared with others, using:

```bash
git reset
```

followed by:

```bash
git push --force
```

can disrupt your collaborators' work.

When working on shared branches, `git revert` is usually the safer choice.

<br>

# 🧩 Cheat Sheet

```bash
git reset <file>

git reset HEAD~1

git reset --soft HEAD~1

git reset --mixed HEAD~1

git reset --hard HEAD~1
```

<br>

# 📌 Summary

- `git reset` moves the current branch to another commit.
- `--soft` keeps staged changes.
- `--mixed` (default) unstages changes but keeps your files.
- `--hard` discards both staged and working directory changes.
- Avoid rewriting shared history unless you understand the consequences.
