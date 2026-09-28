# Obsidian Basics

Welcome to Obsidian! Unlike traditional note-taking apps that trap your notes in proprietary databases or rigid folders, Obsidian works directly with plain text Markdown files saved locally on your computer.

Think of it as a **second brain**: instead of organizing notes like files in a filing cabinet, you connect ideas organically like pages on Wikipedia.

---

## ⚡ The 3 Essential Shortcuts

If you only remember three shortcuts, remember these:

| Shortcut (macOS) | Shortcut (Win / Linux) | Action | What It Does |
| :--- | :--- | :--- | :--- |
| `Cmd + N` | `Ctrl + N` | **New Note** | Instantly create a blank note |
| `Cmd + O` | `Ctrl + O` | **Quick Switcher** | Jump to any note or create a new one by typing its title |
| `Cmd + P` | `Ctrl + P` | **Command Palette** | Search and run any Obsidian action or plugin command |

> [!tip] Quick Switcher is Your Best Friend
> Press `Cmd + O` and start typing. If the note exists, hit `Enter` to open it. If it doesn't exist, hit `Enter` to create it on the spot!

---

## 🔗 The Core Power: Wikilinks

The superpower of Obsidian is **bidirectional linking**. You can connect any note to another without moving files around.

### 1. Basic Link
Type two opening brackets `[[` anywhere in a note. A list of existing notes will pop up. Select one or type a name:
```markdown
[[Obsidian Basics]]
```

### 2. Linking Before Creating
You don't need to create a note before linking to it! Type a name for an idea you want to explore later:
```markdown
[[My Future Project]]
```
The link will show up slightly dimmed. Whenever you're ready, click it and Obsidian will create that note instantly.

### 3. Display Aliases (Piped Links)
If you want the link to read naturally in a sentence:
```markdown
Read our [[Obsidian Basics|starter guide]] to learn more.
```
In reading view, this displays only as **starter guide**, but links directly to `Obsidian Basics`.

### 4. Embedding Notes & Media
Prefix any link with an exclamation point `!` to embed its contents directly into the page:
- `![[Another Note]]` — Renders the content of another note inline.
- `![[Attachments/screenshot.png]]` — Embeds an image from your attachments folder.

---

## 👁️ Reading vs. Editing View

Obsidian has two main viewing modes for notes:

- **Live Preview (Editing View)**: Lets you edit text while rendering bold, headers, math, and checklists inline.
- **Reading View**: A clean, distraction-free rendered view (ideal for pure reading or presenting).

Toggle between them anytime with **`Cmd + E`** (`Ctrl + E`), or click the book/pencil icon in the top-right corner of the tab.

---

## 🕸️ Visualizing Connections: Graph View

- **Global Graph (`Cmd + G` / `Ctrl + G`)**: Shows an interactive map of every note in your vault and the links between them.
- **Local Graph**: Shows only the active note and everything directly connected to it.
  - To open it: click the three dots `...` in the top-right corner of this note -> select **Open linked view** -> **Open local graph**. Drag it into the right sidebar for real-time context as you write.

---

## 📝 Markdown Essentials in Obsidian

### Checkboxes / Interactive Tasks
In Live Preview or Reading View, you can click these to mark them complete:
- [x] Read this guide
- [x] Try creating your first link
- [x] Open the Quick Switcher (`Cmd + O`)

### Obsidian Callouts
Add highlighted callout boxes to emphasize key ideas:

> [!note] Useful Note
> Obsidian notes are standard `.md` files. You can open and read them in VS Code, Vim, or any plain text editor at any time.

> [!tip] Flat is Better than Nested
> Don't spend time creating complex folder hierarchies early on. Keep notes at the root and let links and search do the organizing.

---

## 🔄 How Your Vault Syncs

Your vault is already set up with **Obsidian Git**:

- **Automatic Backups**: Notes are committed and pushed to GitHub automatically in the background.
- **Manual Backup**: Press `Cmd + P`, search for `Git: Commit and push all changes`, and press `Enter`.
- **Media & Images**: When you paste or drop an image into a note, Obsidian places it neatly into the `Attachments/` folder and links it automatically.

---

## 🎯 Quick 2-Minute Practice

Try these 4 steps right now:

1. **Create a link**: Edit this note, go to the bottom, type `[[My Notes Journal]]`, and click it to create your first personal note.
2. **Jump back**: Press `Cmd + O`, type `Obsidian Basics`, and hit `Enter` to return here.
3. **Check off a task**: Click one of the checkboxes under the Markdown Essentials section above.
4. **Try the Command Palette**: Press `Cmd + P`, type `toggle fold`, or search for any action you want to try.

[[Obsidian Practice]]