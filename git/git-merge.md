# Git - Merge

> Combine the history of one branch into another.

<br>

# 🧠 Main Idea

`git merge` integrates changes from one branch into another.

It combines the commit histories while preserving the history of both branches.

Think of it as **joining two development paths into one**.

<br>

# 🤔 Why Do We Need It?

Without `git merge`:

- Completed features would remain isolated in their own branches.
- Bug fixes couldn't be integrated into the main branch.
- Collaboration using branches would be impossible.

`git merge` is the standard way to bring completed work back into a shared branch.

<br>

# 📝 Syntax

Merge a branch into the current branch:

```bash
git merge <branch-name>
```

Merge without creating a merge commit (Fast-Forward only):

```bash
git merge --ff-only <branch-name>
```

Always create a merge commit:

```bash
git merge --no-ff <branch-name>
```

Abort a merge after conflicts:

```bash
git merge --abort
```

<br>

# 💡 Real Example

Suppose your repository looks like this:

```text
main
  │
  └── feature/login
```

Switch to the target branch:

```bash
git switch main
```

Merge the feature branch:

```bash
git merge feature/login
```

Result:

```text
main
  │
  ├── Initial Commit
  ├── Add README
  ├── Feature: Login
```

The changes from `feature/login` are now part of `main`.

<br>

# ⚠️ Common Mistakes

❌ Merging while on the wrong branch.

Git merges **into the current branch**.

For example:

```bash
git switch main

git merge feature/login
```

means:

> Merge `feature/login` **into** `main`.

<br>

❌ Forgetting to pull before merging.

Your local branch may be outdated.

Always update first:

```bash
git pull
```

<br>

❌ Deleting the feature branch before confirming the merge.

Verify the merge was successful before running:

```bash
git branch -d feature/login
```

<br>

❌ Ignoring merge conflicts.

If Git cannot merge automatically, you'll see merge conflicts.

Resolve the conflicts, then:

```bash
git add .

git commit
```

or, if you want to cancel:

```bash
git merge --abort
```

<br>
 
❌ Assuming the deleted file will remain.

By default, Git will remove the file if it was removed from one branch and hasn’t been changed in the other.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git branch` | Create and manage branches |
| `git switch` | Change branches |
| `git rebase` | Reapply commits onto another branch |
| `git pull` | Download and merge remote changes |
| `git push` | Upload merged changes |
| `git log --graph` | Visualize branch history |

Typical workflow:

```text
main
   │
Create Branch
   │
Develop Feature
   │
git commit
   │
git switch main
   │
git merge feature
   │
git push
```

<br>

# 🏋️ Mini Challenge

1. Create a repository.

2. Create a new branch:

```bash
git switch -c feature/about
```

3. Make a change and commit it.

4. Switch back to `main`:

```bash
git switch main
```

5. Merge the feature branch:

```bash
git merge feature/about
```

6. View the history:

```bash
git log --oneline --graph
```

Question:

Can you identify where the feature branch was merged?

<br>

# 💭 Easy To Forget

Git merges **into the branch you're currently on**.

Always check your current branch before merging:

```bash
git status
```

or

```bash
git branch
```

The branch marked with `*` is the one that will receive the changes.

<br>

# 🧩 Cheat Sheet

```bash
git switch main

git merge feature/login

git merge --ff-only feature/login

git merge --no-ff feature/login

git merge --abort

git log --oneline --graph
```

<br>

# 📌 Summary

- `git merge` combines one branch into another.
- Always switch to the target branch before merging.
- Resolve merge conflicts before completing the merge.
- Use `git merge --abort` to cancel a conflicted merge.
- Visualize merges with `git log --graph`.
