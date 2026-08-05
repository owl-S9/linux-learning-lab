# Git - Pull

> Download and integrate changes from a remote repository into your local branch.

<br>

# 🧠 Main Idea

`git pull` updates your local repository with the latest changes from a remote repository.

It is essentially a combination of:

```text
git fetch
        +
git merge
```

Think of it as **syncing your local branch with the remote branch**.

<br>

# 🤔 Why Do We Need It?

Without `git pull`:

- Your local repository may become outdated.
- You might miss changes made by other developers.
- Your push could be rejected because your branch is behind the remote branch.

Running `git pull` helps keep your local repository up to date.

<br>

# 📝 Syntax

Pull changes from the default remote:

```bash
git pull
```

Pull from a specific remote and branch:

```bash
git pull <remote> <branch>
```

Example:

```bash
git pull origin main
```

Fetch changes and rebase instead of merge:

```bash
git pull --rebase
```

<br>

# 💡 Real Example

Check your current status:

```bash
git status
```

Download the latest changes:

```bash
git pull origin main
```

Example output:

```text
From https://github.com/username/project
 * branch            main -> FETCH_HEAD
Updating 4d3f9a1..7a8e2bc
Fast-forward
 README.md | 8 +++++++-
```

Your local branch is now synchronized with the remote repository.

<br>

# ⚠️ Common Mistakes

❌ Thinking `git pull` only downloads changes.

`git pull` does **two** things:

1. Downloads new commits (`git fetch`)
2. Merges them into your current branch (`git merge`)

<br>

❌ Pulling with uncommitted changes.

If you have local modifications, Git may report merge conflicts or refuse to merge.

Always check:

```bash
git status
```

before pulling.

<br>

❌ Pulling the wrong branch.

Verify your current branch before running:

```bash
git pull
```

Use:

```bash
git branch
```

or

```bash
git status
```

<br>

❌ Ignoring merge conflicts.

If Git cannot merge changes automatically, you must resolve the conflicts manually before continuing.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git fetch` | Download remote changes without merging |
| `git merge` | Merge branches |
| `git push` | Upload local commits |
| `git remote` | Manage remote repositories |
| `git status` | Check repository status |
| `git log` | View commit history |

Typical workflow:

```text
Remote Repository
        ↓
    git pull
        ↓
Local Repository
        ↓
Edit Files
        ↓
git add
        ↓
git commit
        ↓
git push
```

<br>

# 🏋️ Mini Challenge

1. Clone a repository.

```bash
git clone <repository-url>
```

2. Ask a friend (or use another machine) to push a new commit.

3. In your local repository, run:

```bash
git pull
```

4. Check the history:

```bash
git log --oneline
```

Question:

Can you see the newly added commit?

<br>

# 💭 Easy To Forget

`git pull` updates **only your local repository**.

It does **not** upload your changes.

Remember:

```text
git pull ← Download changes

git push ← Upload changes
```

<br>

# 🧩 Cheat Sheet

```bash
git pull

git pull origin main

git pull --rebase

git fetch

git merge
```

<br>

# 📌 Summary

- `git pull` downloads and integrates remote changes.
- It is equivalent to `git fetch` followed by `git merge`.
- Pull before starting new work to stay up to date.
- Check `git status` before pulling.
- Use `git pull --rebase` when you prefer a cleaner, linear history.
