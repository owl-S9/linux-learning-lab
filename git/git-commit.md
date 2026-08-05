# Git - Commit

> Save a snapshot of the staged changes into the repository history.

<br>

# 🧠 Main Idea

`git commit` creates a permanent snapshot of everything currently in the **Staging Area**.

Each commit becomes a checkpoint in your project's history that you can revisit, compare, or restore later.

Think of it as **saving a new version of your project**.

<br>

# 🤔 Why Do We Need It?

Without `git commit`:

- Your staged changes are not saved in Git history.
- You can't return to previous versions.
- Collaboration becomes difficult.
- Git has no history to track your project's evolution.

Commits are the foundation of every Git repository.

<br>

# 📝 Syntax

Create a commit with a message:

```bash
git commit -m "Your commit message"
```

Open the default editor to write a detailed commit message:

```bash
git commit
```

Modify the most recent commit:

```bash
git commit --amend
```

Amend the last commit without changing its message:

```bash
git commit --amend --no-edit
```

Commit all tracked modified files without using `git add`:

```bash
git commit -a -m "Your commit message"
```

> **Note:** `-a` only stages **tracked** files. It does **not** include new untracked files.

<br>

# 💡 Real Example

Check your changes:

```bash
git status
```

Stage the files:

```bash
git add main.c
git add README.md
```

Create a commit:

```bash
git commit -m "Add UART initialization"
```

Verify the commit:

```bash
git log --oneline
```

Output:

```text
a3f9c8d Add UART initialization
```

A new snapshot has now been added to the repository history.

<br>

# ⚠️ Common Mistakes

❌ Forgetting to stage files before committing.

```bash
git commit -m "Update project"
```

If nothing is staged, Git will not create a commit.

<br>

❌ Writing meaningless commit messages.

Bad:

```text
update
```

Better:

```text
Implement PID controller
```

A good commit message explains **what changed**, not just that something changed.

<br>

❌ Creating huge commits.

Avoid committing dozens of unrelated changes together.

Prefer small, logical commits that are easy to understand and review.

<br>

❌ Using `--amend` after pushing.

Changing a commit that has already been pushed may require a force push and can affect collaborators.

<br>

❌ Confusing `git commit` with `git push`.

`git commit` saves your work **locally**.

Your commits are **NOT** visible on GitHub until you push them.

<br>
# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git status` | Check repository status |
| `git add` | Stage changes |
| `git log` | View commit history |
| `git show` | Display commit details |
| `git restore` | Undo changes |
| `git reset` | Move to another commit |
| `git push` | Upload commits |

Typical workflow:

```text
Edit Files
      ↓
git status
      ↓
git add
      ↓
git commit
      ↓
git log
      ↓
git push
```

<br>

# 🏋️ Mini Challenge

1. Create a new repository.

2. Create a file named:

```text
README.md
```

3. Stage it:

```bash
git add README.md
```

4. Create your first commit:

```bash
git commit -m "Initial commit"
```

5. View the history:

```bash
git log --oneline
```

Question:

How many commits are shown?

<br>

# 💭 Easy To Forget

A commit saves **only staged changes**.

Any unstaged modifications remain in your working directory and are **not** included in the commit.

Always check before committing:

```bash
git status
```

<br>

# 🧩 Cheat Sheet

```bash
git commit -m "Message"

git commit

git commit --amend

git commit --amend --no-edit

git commit -a -m "Message"

git log --oneline
```

<br>

# 📌 Summary

- `git commit` creates a permanent snapshot of staged changes.
- Every commit becomes part of the repository history.
- Write clear, meaningful commit messages.
- Make small, focused commits whenever possible.
- Only staged files are included in a commit.
