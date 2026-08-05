# Git - Rebase

> Reapply commits from one branch onto another to create a cleaner, linear history.

<br>

# 🧠 Main Idea

`git rebase` moves or reapplies commits from one branch onto another base.

Instead of creating a merge commit, Git rewrites the commit history as if your work had started from the latest commit of the target branch.

Think of it as **moving your branch to a new starting point**.

<br>

# 🤔 Why Do We Need It?

Without `git rebase`:

- Commit history can become cluttered with many merge commits.
- The project timeline is harder to read.
- Reviewing changes becomes more difficult.

`git rebase` creates a cleaner and more linear commit history.

<br>

# 📝 Syntax

Rebase the current branch onto another branch:

```bash
git rebase <branch>
```

Interactive rebase:

```bash
git rebase -i HEAD~3
```

Continue after resolving conflicts:

```bash
git rebase --continue
```

Skip the current commit:

```bash
git rebase --skip
```

Abort the rebase:

```bash
git rebase --abort
```

<br>

# 💡 Real Example

Current history:

```text
main
A --- B --- C

feature
      \
       D --- E
```

Update your feature branch:

```bash
git switch feature

git rebase main
```

Result:

```text
main
A --- B --- C --- D ---- E
            \
             D' --- E' (lost)
```

The commits are replayed on top of `main`.

<br>

# ⚠️ Common Mistakes

❌ Rebasing a branch that has already been shared.

Rebasing rewrites commit history.

Avoid rebasing branches that other developers are using.

<br>

❌ Confusing `merge` and `rebase`.

- `merge` preserves branch history.
- `rebase` rewrites branch history.

<br>

❌ Ignoring rebase conflicts.

Resolve the conflicts, then continue:

```bash
git rebase --continue
```

Or cancel:

```bash
git rebase --abort
```

<br>

❌ Forgetting to force push after rebasing a published branch.

After rebasing, the commit history changes.

If necessary, push with:

```bash
git push --force-with-lease
```

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git merge` | Merge branches |
| `git branch` | Manage branches |
| `git switch` | Switch branches |
| `git log --graph` | Visualize history |
| `git push` | Upload commits |

Typical workflow:

```text
git switch feature
        ↓
git fetch
        ↓
git rebase main
        ↓
Resolve Conflicts (if any)
        ↓
git push --force-with-lease
```

<br>

# 🏋️ Mini Challenge

1. Create a feature branch.

2. Make two commits.

3. Add a new commit to `main`.

4. Switch back:

```bash
git switch feature
```

5. Run:

```bash
git rebase main
```

Question:

How does the commit history differ from using `git merge`?

<br>

# 💭 Easy To Forget

Use:

```text
Merge → Preserve history

Rebase → Rewrite history
```

Never rebase shared branches unless everyone agrees.

<br>

# 🧩 Cheat Sheet

```bash
git rebase main

git rebase -i HEAD~3

git rebase --continue

git rebase --abort

git rebase --skip
```

<br>

# 📌 Summary

- `git rebase` creates a cleaner commit history.
- It rewrites commits onto a new base.
- Resolve conflicts with `--continue`.
- Cancel with `--abort`.
- Avoid rebasing shared branches.
