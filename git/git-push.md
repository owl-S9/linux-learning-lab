# Git - Push

> Upload local commits to a remote repository.

<br>

# 🧠 Main Idea

`git push` sends your **local commits** to a **remote repository** such as GitHub.

It synchronizes your local repository with the remote repository.

Think of it as **publishing your local Git history**.

<br>

# 🤔 Why Do We Need It?

Without `git push`:

- Your commits remain only on your computer.
- Other people cannot see your work.
- GitHub (or another remote repository) is not updated.
- Your work is not backed up remotely.

`git push` is the final step that shares your work with others.

<br>

# 📝 Syntax

Push the current branch:

```bash
git push
```

Push a branch to a remote repository:

```bash
git push <remote> <branch>
```

Example:

```bash
git push origin main
```

Push and set the upstream branch:

```bash
git push -u origin main
```

Force push (use with caution):

```bash
git push --force
```

Safer alternative:

```bash
git push --force-with-lease
```

<br>

# 💡 Real Example

Check your status:

```bash
git status
```

Create a commit:

```bash
git add .

git commit -m "Implement login page"
```

Upload the commit to GitHub:

```bash
git push origin main
```

Output:

```text
Enumerating objects: ...
Counting objects: ...
Writing objects: ...
To https://github.com/username/project.git
```

Your commit is now available on GitHub.

<br>

# ⚠️ Common Mistakes

❌ Thinking that `git commit` automatically uploads your project to GitHub.

A commit only saves your work **locally**.

To publish your commits, you must run:

```bash
git push
```

Workflow:

```text
Working Directory
        ↓
    git add
        ↓
 Staging Area
        ↓
   git commit
        ↓
 Local Repository
        ↓
    git push
        ↓
     GitHub
```

<br>

❌ Forgetting to pull before pushing.

If someone else has pushed changes first, your push may be rejected.

Run:

```bash
git pull
```

before pushing.

<br>

❌ Using `git push --force` without understanding the consequences.

Force pushing rewrites remote history and may overwrite other people's work.

Prefer:

```bash
git push --force-with-lease
```

whenever possible.

<br>

❌ Pushing to the wrong branch.

Always verify your current branch:

```bash
git branch
```

or

```bash
git status
```

before pushing.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git remote` | Manage remote repositories |
| `git fetch` | Download remote changes |
| `git pull` | Download and merge changes |
| `git commit` | Save local changes |
| `git status` | Check repository status |
| `git branch` | List branches |

Typical workflow:

```text
Edit Files
      ↓
git add
      ↓
git commit
      ↓
git push
      ↓
GitHub Updated
```

<br>

# 🏋️ Mini Challenge

1. Create a repository on GitHub.

2. Connect your local repository:

```bash
git remote add origin <repository-url>
```

3. Push your branch:

```bash
git push -u origin main
```

4. Refresh the GitHub page.

Question:

Can you see your latest commit on GitHub?

<br>

# 💭 Easy To Forget

`git push` uploads **commits**, not your working directory.

If you forget to commit first:

```bash
git push
```

Git will have **nothing new to upload**.

Always remember:

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

# 🧩 Cheat Sheet

```bash
git push

git push origin main

git push -u origin main

git push --force

git push --force-with-lease
```

<br>

# 📌 Summary

- `git push` uploads local commits to a remote repository.
- Commits are not visible on GitHub until they are pushed.
- Use `git push -u origin <branch>` the first time you push a branch.
- Pull remote changes before pushing when collaborating.
- Avoid `--force` unless you understand its impact.
