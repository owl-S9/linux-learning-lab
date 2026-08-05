# Git - Switch

> Switch between branches or create and switch to a new branch.

<br>

# 🧠 Main Idea

`git switch` changes your current working branch.

It lets you move between branches without affecting their commit history.

Unlike the older `git checkout`, `git switch` is designed specifically for **branch management**, making it simpler and less confusing.

Think of it as **changing your workspace to another branch**.

<br>

# 🤔 Why Do We Need It?

Without `git switch`:

- Moving between branches would be less intuitive.
- Developers would rely on the more complex `git checkout`.
- It would be easier to accidentally misuse Git commands.

`git switch` provides a clear and modern way to work with branches.

<br>

# 📝 Syntax

Switch to an existing branch:

```bash
git switch <branch-name>
```

Create and switch to a new branch:

```bash
git switch -c <branch-name>
```

Switch to the previous branch:

```bash
git switch -
```

Create a branch from another branch and switch to it:

```bash
git switch -c <new-branch> <start-point>
```

<br>

# 💡 Real Example

View your branches:

```bash
git branch
```

Output:

```text
* main
  feature/login
```

Switch to the feature branch:

```bash
git switch feature/login
```

Verify:

```bash
git branch
```

Output:

```text
  main
* feature/login
```

Create and switch to a new branch:

```bash
git switch -c feature/profile
```

<br>

# ⚠️ Common Mistakes

❌ Thinking `git switch` creates a branch by default.

```bash
git switch feature/login
```

This only switches to an **existing** branch.

To create a new one:

```bash
git switch -c feature/login
```

<br>

❌ Trying to switch branches with uncommitted changes.

Git may prevent the switch if your local changes would be overwritten.

Always check:

```bash
git status
```

before switching.

<br>

❌ Confusing `git switch` with `git branch`.

- `git branch` creates or manages branches.
- `git switch` changes your current branch.

<br>

❌ Assuming `git switch` changes remote branches.

It only affects your **local** repository.

To publish a new branch to GitHub:

```bash
git push -u origin <branch-name>
```

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git branch` | Create and manage branches |
| `git merge` | Merge branches |
| `git rebase` | Reapply commits onto another branch |
| `git checkout` | Legacy command for switching branches |
| `git status` | Check repository status |
| `git push` | Publish a branch |

Typical workflow:

```text
git branch feature/login
          ↓
git switch feature/login
          ↓
Develop Feature
          ↓
git commit
          ↓
git switch main
          ↓
git merge feature/login
```

<br>

# 🏋️ Mini Challenge

1. Create a new repository.

2. Create a new branch:

```bash
git branch feature/dashboard
```

3. Switch to it:

```bash
git switch feature/dashboard
```

4. Return to the previous branch:

```bash
git switch -
```

Question:

Which branch are you on after each command?

<br>

# 💭 Easy To Forget

`git switch` only changes **which branch you're working on**.

It does **not**:

- Create a commit.
- Merge branches.
- Upload changes to GitHub.

Remember:

```text
git branch → Create

git switch → Change

git merge → Combine
```

<br>

# 🧩 Cheat Sheet

```bash
git switch main

git switch feature/login

git switch -c feature/profile

git switch -

git branch
```

<br>

# 📌 Summary

- `git switch` changes your current branch.
- Use `-c` to create and switch to a new branch.
- It is the modern alternative to `git checkout` for branch switching.
- Check `git status` before switching if you have uncommitted changes.
- `git switch` only affects your local repository.
