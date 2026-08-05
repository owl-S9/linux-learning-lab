# Git - Add

> Stage changes to be included in the next commit.

<br>

# 🧠 Main Idea

`git add` moves changes from the **Working Directory** to the **Staging Area**.

It tells Git exactly which changes should be included in the next commit.

Think of it as **selecting files before taking a snapshot**.

<br>

# 🤔 Why Do We Need It?

Without `git add`:

- Git doesn't know which changes you want to commit.
- You can't choose specific files for a commit.
- Every commit would either contain everything or nothing.

The staging area gives you precise control over what becomes part of your project's history.

<br>

# 📝 Syntax

Stage a specific file:

```bash
git add <file>
```

Stage multiple files:

```bash
git add file1 file2 file3
```

Stage an entire directory:

```bash
git add <directory>
```

Stage all changes in the current directory:

```bash
git add .
```

Stage all tracked and untracked files (including deletions):

```bash
git add -A
```

Stage only modified and deleted tracked files:

```bash
git add -u
```

Interactively choose changes to stage:

```bash
git add -p
```

<br>

# 💡 Real Example

Create a project file:

```bash
touch main.c
```

Check the status:

```bash
git status
```

Stage the file:

```bash
git add main.c
```

Verify the result:

```bash
git status
```

Output:

```text
Changes to be committed:
    new file: main.c
```

The file is now in the staging area and ready to be committed.

<br>

# ⚠️ Common Mistakes

❌ Forgetting to stage files before committing.

```bash
git commit -m "Initial commit"
```

Nothing will be committed if no files are staged.

<br>

❌ Forgetting to stage changes after editing a staged file.

If you modify a file **after** running `git add`, the new changes are **not** staged automatically.

Run:

```bash
git add <file>
```

again to include the latest modifications.

<br>

❌ Using `git add -A` without checking what changed.

Always verify with:

```bash
git status
```

before committing.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git status` | View repository status |
| `git commit` | Save staged changes |
| `git restore --staged` | Unstage files |
| `git diff` | View unstaged changes |
| `git diff --staged` | View staged changes |
| `git rm` | Remove tracked files |

Typical workflow:

```text
Edit Files
      ↓
git status
      ↓
git add
      ↓
git status
      ↓
git commit
```

<br>

# 🏋️ Mini Challenge

1. Initialize a new repository.

```bash
git init
```

2. Create two files:

```text
README.md
main.c
```

3. Stage only `README.md`.

```bash
git add README.md
```

4. Run:

```bash
git status
```

Question:

- Which file is staged?
- Which file remains untracked?

<br>

# 💭 Easy To Forget

`git add` **does NOT save your work permanently.**

It only moves changes into the staging area.

Your changes become part of the repository history **only after**:

```bash
git commit
```

<br>

# 🧩 Cheat Sheet

```bash
git add <file>

git add .

git add -A

git add -u

git add -p

git status

git diff --staged
```

<br>

# 📌 Summary

- `git add` stages changes for the next commit.
- Only staged changes are included in a commit.
- Use `git status` to verify what is staged.
- Run `git add` again after modifying a staged file.
- `git add` prepares changes; `git commit` saves them permanently.
