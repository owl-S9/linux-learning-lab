# Git - Branch

> Create, list, rename, and delete branches in a Git repository.

<br>

# 🧠 Main Idea

A **branch** is an independent line of development in a Git repository.

`git branch` allows you to create, view, rename, and delete branches without affecting other branches.

Think of a branch as **a parallel timeline** where you can safely develop new features or fix bugs.

<br>

# 🤔 Why Do We Need It?

Without branches:

- Every change would be made directly on the main branch.
- Experimenting would be risky.
- Multiple developers would constantly interfere with each other's work.
- Feature development and bug fixes would be difficult to manage.

Branches let you work independently while keeping the main branch stable.

<br>

# 📝 Syntax

List local branches:

```bash
git branch
```

Create a new branch:

```bash
git branch <branch-name>
```

Create a branch from another branch:

```bash
git branch <new-branch> <start-point>
```

Rename the current branch:

```bash
git branch -m <new-name>
```

Rename another branch:

```bash
git branch -m <old-name> <new-name>
```

Delete a merged branch:

```bash
git branch -d <branch-name>
```

Force delete a branch:

```bash
git branch -D <branch-name>
```

List remote branches:

```bash
git branch -r
```

List all branches:

```bash
git branch -a
```

<br>

# 💡 Real Example

View existing branches:

```bash
git branch
```

Output:

```text
* main
```

Create a new branch:

```bash
git branch feature/login
```

View branches again:

```bash
git branch
```

Output:

```text
* main
  feature/login
```

The new branch has been created, but you are **still on `main`**.

To start working on it:

```bash
git switch feature/login
```

<br>

# ⚠️ Common Mistakes

❌ Thinking `git branch` switches to the new branch.

Creating a branch and switching to it are two different actions.

```bash
git branch feature/login
```

Only creates the branch.

To switch:

```bash
git switch feature/login
```

<br>

❌ Deleting a branch before its changes are merged.

Using:

```bash
git branch -d feature/login
```

Git refuses to delete the branch if it contains unmerged commits.

Using:

```bash
git branch -D feature/login
```

forces deletion and may permanently lose work.

<br>

❌ Working directly on `main`.

Create a feature branch before implementing new features or large changes.

Example:

```text
main
    │
    └── feature/login
```

<br>

❌ Confusing local branches with remote branches.

Creating a local branch does **not** automatically create it on GitHub.

To publish it:

```bash
git push -u origin feature/login
```

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git switch` | Switch branches |
| `git checkout` | Switch branches or restore files (legacy) |
| `git merge` | Merge branches |
| `git rebase` | Reapply commits onto another branch |
| `git push` | Publish branches and commits |
| `git branch -a` | View all branches |

Typical workflow:

```text
main
   │
git branch feature/login
   │
git switch feature/login
   │
Develop Feature
   │
git commit
   │
git switch main
   │
git merge feature/login
```

<br>

# 🏋️ Mini Challenge

1. Create a new repository.

2. Create a branch:

```bash
git branch feature/profile
```

3. List all branches:

```bash
git branch
```

4. Switch to the new branch:

```bash
git switch feature/profile
```

5. Verify your current branch:

```bash
git branch
```

Question:

Which branch has the `*` symbol?

<br>

# 💭 Easy To Forget

`git branch` **creates** branches.

It does **not** switch to them.

Remember:

```text
git branch → Create

git switch → Change branches
```

<br>

# 🧩 Cheat Sheet

```bash
git branch

git branch feature/login

git branch -a

git branch -r

git branch -d feature/login

git branch -D feature/login

git branch -m new-name
```

<br>

# 📌 Summary

- `git branch` manages branches in a Git repository.
- Branches allow independent development.
- Creating a branch does not switch to it.
- Delete merged branches with `-d`; use `-D` carefully.
- Publish a local branch using `git push -u origin <branch-name>`.
