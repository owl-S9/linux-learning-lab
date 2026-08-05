# Git - Clean

> Remove untracked files and directories.

<br>

# 🧠 Main Idea

`git clean` deletes files that Git is **not tracking**.

Think of it as **cleaning your working directory**.

<br>

# 🤔 Why Do We Need It?

Without `git clean`:

- Temporary files accumulate.
- Build artifacts remain.
- Your repository becomes messy.

<br>

# 📝 Syntax

Preview:

```bash
git clean -n
```

Delete files:

```bash
git clean -f
```

Delete files and directories:

```bash
git clean -fd
```

Delete ignored files too:

```bash
git clean -fdx
```

<br>

# 💡 Real Example

Preview:

```bash
git clean -n
```

Output:

```text
Would remove temp.txt
Would remove build/
```

Delete:

```bash
git clean -fd
```

<br>

# ⚠️ Common Mistakes

❌ Running `git clean -f` without previewing.

Always use:

```bash
git clean -n
```

first.

<br>

❌ Thinking it removes tracked files.

It only removes **untracked** files.

<br>

❌ Using `-fdx` carelessly.

Ignored files such as build folders can be permanently deleted.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git restore` | Restore tracked files |
| `git status` | View untracked files |
| `git stash` | Save temporary work |

<br>

# 🏋️ Mini Challenge

Create an untracked file.

Preview:

```bash
git clean -n
```

Delete:

```bash
git clean -f
```

Question:

Does Git remove tracked files?

<br>

# 💭 Easy To Forget

Always preview first:

```bash
git clean -n
```

Then delete:

```bash
git clean -f
```

<br>

# 🧩 Cheat Sheet

```bash
git clean -n

git clean -f

git clean -fd

git clean -fdx
```

<br>

# 📌 Summary

- Removes untracked files.
- Doesn't affect tracked files.
- Use `-n` before `-f`.
- Be careful with `-fdx`.
