# Git - Tag

> Mark a specific commit with a meaningful name.

<br>

# 🧠 Main Idea

`git tag` creates a permanent label for a commit.

Tags are commonly used for marking releases such as:

```text
v1.0.0
v2.1.3
v3.0.0-beta
```

Think of a tag as **a bookmark in your Git history**.

<br>

# 🤔 Why Do We Need It?

Without tags:

- Releases are harder to identify.
- Finding important commits takes longer.
- Version management becomes confusing.

Tags make important milestones easy to locate.

<br>

# 📝 Syntax

Create a lightweight tag:

```bash
git tag v1.0
```

Create an annotated tag:

```bash
git tag -a v1.0 -m "Version 1.0"
```

List tags:

```bash
git tag
```

Show a tag:

```bash
git show v1.0
```

Push tags:

```bash
git push origin v1.0
```

Push all tags:

```bash
git push --tags
```

<br>

# 💡 Real Example

After finishing a release:

```bash
git tag -a v1.0.0 -m "First stable release"
```

Upload it:

```bash
git push origin v1.0.0
```

The release tag is now available on GitHub.

<br>

# ⚠️ Common Mistakes

❌ Thinking tags are pushed automatically.

Commits and tags are separate.

Push tags explicitly.

<br>

❌ Modifying release tags.

Avoid changing published tags.

<br>

❌ Confusing tags with branches.

Branches move.

Tags remain attached to one commit forever.

<br>

❌ Forgetting to create annotated tags for releases.

Annotated tags contain useful metadata.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git show` | Show tag details |
| `git push` | Upload tags |
| `git log` | View history |
| `git checkout` | Check out a tag |

Typical workflow:

```text
Finish Feature
      ↓
git commit
      ↓
git tag
      ↓
git push
      ↓
git push --tags
```

<br>

# 🏋️ Mini Challenge

Create:

```bash
git tag -a v1.0 -m "First release"
```

List tags:

```bash
git tag
```

Question:

Can you view the tag details?

<br>

# 💭 Easy To Forget

A tag points to **one specific commit**.

Unlike branches, it never moves automatically.

<br>

# 🧩 Cheat Sheet

```bash
git tag

git tag v1.0

git tag -a v1.0 -m "Release"

git show v1.0

git push origin v1.0

git push --tags
```

<br>

# 📌 Summary

- Tags mark important commits.
- Releases usually use annotated tags.
- Tags don't move.
- Push tags separately.
- Use semantic version names when possible.
