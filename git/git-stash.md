# Git - Stash

> Temporarily save uncommitted changes without creating a commit.

<br>

# 🧠 Main Idea

`git stash` temporarily stores your uncommitted changes and restores your working directory to a clean state.

You can later restore those changes whenever you're ready.

Think of it as **putting your work into a temporary drawer**.

<br>

# 🤔 Why Do We Need It?

Without `git stash`:

- You might create unnecessary commits.
- Switching branches becomes difficult when you have unfinished work.
- You could lose track of temporary changes.

`git stash` lets you pause your work safely. (ctrl-s)

<br>

# 📝 Syntax

Save changes:

```bash
git stash
```

Save with a message:

```bash
git stash push -m "Work in progress"
```

List stashes:

```bash
git stash list
```

Restore the latest stash:

```bash
git stash apply
```

Restore and remove the latest stash:

```bash
git stash pop
```

Delete a stash:

```bash
git stash drop stash@{0}
```

Delete all stashes:

```bash
git stash clear
```

<br>

# 💡 Real Example

You're working on a feature:

```bash
git status
```

Temporarily save your changes:

```bash
git stash
```

Switch branches:

```bash
git switch main
```

Return later:

```bash
git switch feature

git stash pop
```

Your unfinished work is restored.

<br>

# ⚠️ Common Mistakes

❌ Forgetting that `git stash pop` removes the stash.

If you want to keep the stash:

```bash
git stash apply
```

instead.

<br>

❌ Forgetting what each stash contains.

Use:

```bash
git stash list
```

and add messages with:

```bash
git stash push -m "..."
```

<br>

❌ Assuming stashes are shared.

Stashes exist **only in your local repository**.

They are never pushed to GitHub.

<br>

❌ Leaving old stashes forever.

Remove unused stashes regularly.

<br>

# 🔗 Related Commands

| Command | Purpose |
|----------|---------|
| `git switch` | Switch branches |
| `git status` | Check repository status |
| `git commit` | Save changes permanently |
| `git stash list` | View stashes |
| `git stash pop` | Restore and remove stash |

Typical workflow:

```text
Edit Files
      ↓
git stash
      ↓
Switch Branch
      ↓
Return
      ↓
git stash pop
```

<br>

# 🏋️ Mini Challenge

1. Modify a file.

2. Save your work:

```bash
git stash
```

3. Switch branches.

4. Return.

5. Restore your changes.

Question:

What's the difference between `apply` and `pop`?

<br>

# 💭 Easy To Forget

A stash is **temporary**, not permanent.

If the changes are important, create a real commit instead.

<br>

# 🧩 Cheat Sheet

```bash
git stash

git stash push -m "message"

git stash list

git stash apply

git stash pop

git stash clear
```

<br>

# 📌 Summary

- `git stash` temporarily saves uncommitted work.
- Use `apply` to keep the stash.
- Use `pop` to restore and remove it.
- Stashes are local only.
- Don't use stashes as permanent storage.
