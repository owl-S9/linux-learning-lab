# Git - Clone

> Create a local copy of an existing Git repository.

<br>

# 🧠 Main Idea

`git clone` downloads an existing Git repository from a remote source (such as GitHub) to your local machine.

Unlike `git init`, which starts a brand-new repository, `git clone` copies an existing repository **including its commits, branches, and history**.

Think of it as **making an exact copy of someone else's Git repository.**

<br>

# 🤔 Why Do We Need It?

Without `git clone`:

- You would have to create the repository manually.
- You wouldn't have the project's commit history.
- Collaboration would be much harder.

`git clone` is the standard way to start working on an existing project.

<br>

# 📝 Syntax

Clone a repository:

```bash
git clone <repository-url>
```

Clone into a custom directory:

```bash
git clone <repository-url> <directory-name>
```

Clone a specific branch:

```bash
git clone --branch <branch-name> <repository-url>
```

Clone only the latest commit (shallow clone):

```bash
git clone --depth 1 <repository-url>
```

<br>

# 💡 Real Example

Clone a GitHub repository:

```bash
git clone https://github.com/octocat/Hello-World.git
```

Output:

```text
Cloning into 'Hello-World'...
Receiving objects: 100% (...)
Resolving deltas: 100% (...)
```

Enter the project:

```bash
cd Hello-World
```

Check the repository status:

```bash
git status
```

The repository is now fully available on your local machine.

<br>

# ⚠️ Common Mistakes

❌ Using `git init` instead of `git clone`.

If the project already exists on GitHub, use:

```bash
git clone
```

instead of creating an empty repository with `git init`.

<br>

❌ Cloning into a non-empty directory.

Git expects the destination directory to be empty.

<br>

❌ Editing files before entering the cloned directory.

Always move into the repository first:

```bash
cd <repository-name>
```

<br>

❌ Assuming clone only downloads the latest files.

`git clone` downloads the **entire repository history** (unless you use `--depth`).

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git init` | Create a new repository |
| `git remote -v` | View remote repositories |
| `git fetch` | Download new changes |
| `git pull` | Download and merge changes |
| `git push` | Upload commits |
| `git status` | Check repository status |

Typical workflow:

```text
Find Repository
        ↓
git clone
        ↓
cd Repository
        ↓
git status
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

1. Find a public GitHub repository.
2. Copy its HTTPS URL.
3. Clone it:

```bash
git clone <repository-url>
```

4. Enter the project:

```bash
cd <repository-name>
```

5. Check the status:

```bash
git status
```

Question:

Which branch are you currently on?

<br>

# 💭 Easy To Forget

`git clone` automatically:

- Creates the project directory.
- Initializes Git.
- Downloads all commits.
- Sets up the remote named **origin**.
- Checks out the default branch.

You **do not** need to run:

```bash
git init
```

after cloning.

<br>

# 🧩 Cheat Sheet

```bash
git clone <repository-url>

git clone <repository-url> MyProject

git clone --branch develop <repository-url>

git clone --depth 1 <repository-url>

git remote -v
```

<br>

# 📌 Summary

- `git clone` copies an existing repository.
- It downloads the complete Git history by default.
- It automatically creates the `.git` directory.
- It automatically configures the remote named `origin`.
- Use `git clone` for existing projects and `git init` for new ones.
