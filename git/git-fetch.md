# Git - Fetch

> Download changes from a remote repository without modifying your current branch.

<br>

# 🧠 Main Idea

`git fetch` downloads commits, branches, and tags from a remote repository.

Unlike `git pull`, it **does not merge** the downloaded changes into your current branch.

Think of it as **checking for updates without installing them**.

<br>

# 🤔 Why Do We Need It?

Without `git fetch`:

- You can't safely inspect remote changes before merging.
- You may accidentally merge changes you haven't reviewed.
- Comparing local and remote history becomes harder.

`git fetch` gives you complete control over when and how to integrate remote changes.

<br>

# 📝 Syntax

Fetch from the default remote:

```bash
git fetch
```

Fetch from a specific remote:

```bash
git fetch origin
```

Fetch all remotes:

```bash
git fetch --all
```

Prune deleted remote branches:

```bash
git fetch --prune
```

<br>

# 💡 Real Example

Download the latest changes:

```bash
git fetch origin
```

Check the history:

```bash
git log --oneline --all --graph
```

Merge the downloaded changes:

```bash
git merge origin/main
```

Your local branch is updated only after the merge.

<br>

# ⚠️  Common Mistakes

❌ Confusing `git fetch` with `git pull`.

```text
git fetch → Download only

git pull → Download + Merge
```

<br>

❌ Assuming your local branch is updated after fetching.

After:

```bash
git fetch
```

your current branch remains unchanged.

<br>

❌ Forgetting to review changes before merging.

Compare branches:

```bash
git log main..origin/main
```

or

```bash
git diff main origin/main
```

<br>

❌ Thinking `git fetch` modifies your files.

It only updates your remote-tracking branches.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git pull` | Fetch and merge |
| `git merge` | Merge downloaded changes |
| `git remote` | Manage remotes |
| `git log` | View history |
| `git diff` | Compare changes |

Typical workflow:

```text
Remote Repository
        ↓
git fetch
        ↓
Review Changes
        ↓
git merge
        ↓
Continue Working
```

<br>

# 🏋️ Mini Challenge

1. Clone a repository.

2. Ask someone to push a new commit.

3. Run:

```bash
git fetch
```

4. Compare:

```bash
git log --oneline main..origin/main
```

Question:

Did your working files change after fetching?

<br>

# 💭 Easy To Forget

`git fetch` is **completely safe**.

It never modifies:

- Your working directory.
- Your current branch.
- Your commits.

It only downloads new information.

<br>

# 🧩 Cheat Sheet

```bash
git fetch

git fetch origin

git fetch --all

git fetch --prune

git merge origin/main
```

<br>

# 📌 Summary

- `git fetch` downloads remote changes only.
- It never merges changes automatically.
- Review downloaded commits before merging.
- Use `git pull` when you want to fetch and merge in one step.
- `git fetch` is one of the safest Git commands.
