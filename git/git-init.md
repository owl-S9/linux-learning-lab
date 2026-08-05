# Git - Init

> Create a new Git repository in the current directory.

<br>

# 🧠 Main Idea

`git init` initializes a directory as a Git repository.

It creates a hidden **`.git`** folder that stores all of Git's data, including commits, branches, configuration, and repository history.

Think of it as **turning an ordinary folder into a Git project.**

<br>

# 🤔 Why Do We Need It?

Without `git init`:

- Git cannot track your files.
- You can't create commits.
- You can't create branches.
- Most Git commands won't work.

`git init` is the first step when starting a brand-new Git project.

<br>

# 📝 Syntax

Initialize the current directory:

```bash
git init
```

Initialize a specific directory:

```bash
git init <directory>
```


<br>

# 💡 Real Example

Create a new project:

```bash
mkdir Calculator
cd Calculator

git init
```

Output:

```text
Initialized empty Git repository in /Calculator/.git/
```

Check the repository status:

```bash
git status
```

Output:

```text
On branch main

No commits yet

nothing to commit
```

Your project is now ready to be tracked by Git.

<br>

# ⚠️ Common Mistakes

❌ Running `git init` inside another Git repository.

This creates a nested repository, which is usually not what you want.

Check first:

```bash
git status
```

or

```bash
git rev-parse --is-inside-work-tree
```

<br>

❌ Deleting the `.git` folder.

Removing `.git` permanently deletes your repository history, branches, and configuration.

<br>

❌ Assuming `git init` uploads your project to GitHub.

`git init` only creates a **local** repository.

To upload your project later, you'll use:

```bash
git remote add origin <repository-url>

git push
```

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git clone` | Copy an existing repository |
| `git status` | Check repository status |
| `git add` | Stage files |
| `git commit` | Save a snapshot |
| `git remote` | Connect to a remote repository |
| `git push` | Upload commits |

Typical workflow:

```text
Create Project
      ↓
git init
      ↓
Create Files
      ↓
git add
      ↓
git commit
```

<br>

# 🏋️ Mini Challenge

1. Create a folder named `MyProject`.

```bash
mkdir MyProject
```

2. Enter the directory.

```bash
cd MyProject
```

3. Initialize Git.

```bash
git init
```

4. Verify that Git is working.

```bash
git status
```

Question:

What message does Git display before the first commit?

<br>

# 💭 Easy To Forget

`git init` **does not create your first commit.**

After initialization, the repository is empty.

You still need to:

```bash
git add .

git commit -m "Initial commit"
```

to start your project's history.

<br>

# 🧩 Cheat Sheet

```bash
git init

git init MyProject

git status

ls -a
```

<br>

# 📌 Summary

- `git init` creates a new Git repository.
- It creates the hidden `.git` directory.
- Every new Git project starts with `git init`.
- It only initializes a local repository.
- Your first commit comes after `git add` and `git commit`.