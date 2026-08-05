# tmux

> Terminal Multiplexer

Run multiple terminal sessions inside a single terminal while keeping them alive even after disconnecting.

<br>

# 🧠 Main Idea

Imagine tmux as a desktop environment inside your terminal.

```text
tmux Server
    │
    ├── Session (Workspace)
    │      │
    │      ├── Window (Tab)
    │      │      │
    │      │      ├── Pane (Split Terminal)
    │      │      └── Pane
    │      │
    │      └── Window
    │
    └── Session
```

You don't interact directly with the **server**.

You usually work with:

- Sessions
- Windows
- Panes

<br>

# 🤔 Why tmux?

tmux solves several problems:

- Continue running programs after SSH disconnects.
- Access the same session from different computers.
- Run multiple terminals in one window.
- Organize development environments.
- Increase productivity.

<br>

# 🧩 Core Concepts

## Server

A background process.

Stores every session.

<br>

## Session

A workspace.

Contains multiple windows.


<br>

## Window

Like a browser tab.

Contains one or more panes.

<br>

## Pane

A split inside a window.

Each pane runs its own shell.

<br>

<br>

# 🚀 Basic Workflow

```text
Create Session

↓

Open Windows

↓

Split Panes

↓

Do Your Work

↓

Detach

↓

Attach Later
```

<br>

# 🔑 Prefix Key

Every tmux shortcut starts with:

```
Ctrl+b
```

then another key.

Example:

```
Ctrl+b c
```

Create a new window.

<br>

# 📦 Session Commands

Create:

```bash
tmux new

tmux new -s mysession
```

List:

```bash
tmux ls
```

Attach:

```bash
tmux attach

tmux attach -t mysession
```

Create or attach:

```bash
tmux new -As dev
```

Detach:

```
Ctrl+b d
```


Rename:

```
Ctrl+b $
```

Kill:

```bash
tmux kill-session -t mysession
```

Kill everything:

```bash
tmux kill-server
```

<br>


# 🪟 Windows

Create:

```
Ctrl+b c
```

Rename:

```
Ctrl+b ,
```

Next:

```
Ctrl+b n
```

Previous:

```
Ctrl+b p
```

Choose window:

```
Ctrl+b w
```

Kill:

```
Ctrl+b &
```

<br>


# 🧱 Panes

Vertical Split:

```
Ctrl+b %
```

Horizontal Split:

```
Ctrl+b "
```

Move:

```
Ctrl+b ←
Ctrl+b →
Ctrl+b ↑
Ctrl+b ↓
```

Choose by number:

```
Ctrl+b q
```

Next Pane:

```
Ctrl+b o
```

Zoom:

```
Ctrl+b z
```

Change Layout:

```
Ctrl+b Space
```

Kill Pane:

```
Ctrl+b x
```

<br>

# 📋 Copy Mode

Enter Copy Mode:

```
Ctrl+b [
```

im working on it...


<br>

# 📺 Clients

Multiple terminals can connect to the same session.

Useful for pair programming or reconnecting from another computer.

List clients:

```
Ctrl+b D
```

use `d` to detach selected client.
use `x` to detach selected client and kill its shell.

<br>

# ⚠️ Detach vs Kill

Detach:

```
Ctrl+b d
```

✔ Programs continue running.

<br>

Kill Pane:

```
Ctrl+b x
```

Stops only one pane.

<br>

Kill Window:

```
Ctrl+b &
```

Stops the current window.

<br>

Kill Session:

```bash
tmux kill-session
```

Stops the whole workspace.

<br>

Kill Server:

```bash
tmux kill-server
```

Everything is gone.

<br>

# 💡 Daily Workflow

```text
tmux new -As dev

↓

Ctrl+b c

↓

Ctrl+b %

↓

Ctrl+b "

↓

Work...

↓

Ctrl+b d

↓

tmux attach
```

---

# ⭐ The 10 Shortcuts You'll Use Every Day

| Shortcut | Action |
|----------|--------|
| `Ctrl+b c` | New Window |
| `Ctrl+b d` | Detach |
| `Ctrl+b %` | Vertical Split |
| `Ctrl+b "` | Horizontal Split |
| `Ctrl+b o` | Next Pane |
| `Ctrl+b z` | Zoom Pane |
| `Ctrl+b q` | Pane Numbers |
| `Ctrl+b w` | Window List |
| `Ctrl+b ,` | Rename Window |
| `Ctrl+b $` | Rename Session |

---

# 📌 Summary

```
tmux Server
      │
      └── Sessions
             │
             └── Windows
                    │
                    └── Panes
```

Always remember:

```
Create Session

↓

Open Windows

↓

Split Panes

↓

Detach

↓

Attach Later
```
