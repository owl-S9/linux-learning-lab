# Git Notes

> A practical Git knowledge base covering the most important commands, concepts, and workflows.


### Getting Started
- [init](git-init.md)
- [clone](git-clone.md)

### Daily Workflow
- [status](git-status.md)
- [add](git-add.md)
- [commit](git-commit.md)
- [push](git-push.md)
- [pull](git-pull.md)
- [diff](git-diff.md)
- [log](git-log.md)

### Branching
- [branch](git-branch.md)
- [switch](git-switch.md)
- [merge](git-merge.md)
- [rebase](git-rebase.md)

### Recovery
- [reset](git-reset.md)
- [restore](git-restore.md)
- [reflog](git-reflog.md)
- [stash](git-stash.md)
- [clean](git-clean.md)

### Advanced
- [tag](git-tag.md)
- cherry-pick
- [fetch](git-fetch.md)
- [remote](git-remote.md)

<br>

# Git Workflow

There are only **two ways** to start working with a Git repository:

### 1. Create a new repository

```bash
git init
```

Use this when you are starting a brand-new project.

**OR**

### 2. Clone an existing repository

```bash
git clone <repository-url>
```

Use this when the project already exists (for example on GitHub).

<br>

---

<br>

Imagine Git as an online shopping process.

```text
Working Directory
       │
       │ Edit Files
       ▼
+------------------+
| Working Directory|
+------------------+
       │
       │ git add
       ▼
+------------------+
|  Staging Area 🛒 |
| (Shopping Cart)  |
+------------------+
       │
       │ git commit
       ▼
+------------------+
| Local Repository |
|   (Snapshots)    |
+------------------+
       │
       │ git push
       ▼
+------------------+
| GitHub / Remote  |
+------------------+
```

Think of the **Staging Area** as a **shopping cart**.

- You edit files in your project.
- You choose which changes to put into the cart using `git add`.
- When you're satisfied, `git commit` creates a permanent snapshot of everything inside the cart.
- Finally, `git push` uploads those commits to the remote repository (such as GitHub).

In short:

```text
Edit
  ↓
git add
  ↓
git commit
  ↓
git push
```

<br>

# Where Does Each Command Work?

| Area | Main Commands |
|-------|---------------|
| Repository Creation | `git init`, `git clone` |
| Working Directory | `git status`, `git diff`, `git restore` |
| Staging Area | `git add`, `git reset`, `git restore --staged` |
| Local Repository | `git commit`, `git log`, `git show`, `git branch`, `git merge`, `git rebase`, `git tag`, `git stash`, `git reflog`, `git cherry-pick` |
| Remote Repository | `git remote`, `git fetch`, `git pull`, `git push` |

<br>

# Typical Workflow

```text
Create / Clone Repository
          ↓
      Edit Files
          ↓
     git status
          ↓
      git diff
          ↓
       git add
          ↓
     git commit
          ↓
      git push
```

<br>

# Tips

Git is **not GitHub**.

- **Git** is the version control system installed on your computer.
- **GitHub** is an online service that hosts Git repositories.

You can use Git without GitHub.

GitHub simply stores and shares your repositories.

