# Agent Guidelines for Obsidian Vault

This repository is an Obsidian knowledge vault synchronized with Git and GitHub. When assisting the user with note-taking, researching, or managing this vault, follow these guidelines:

---

## 📝 Note Creation & Formatting

- **File Location**: Save new notes directly at the vault root as `<Note Title>.md` (unless the user explicitly requests a subfolder).
- **Format**: Use clean, standard GitHub Flavored Markdown (headings, bullet lists, checkboxes `- [ ]`, tables, and fenced code blocks).
- **Tone & Style**: Keep notes clear, concise, and structured. Preserve the user's authentic thoughts, phrasing, and intent without over-polishing or adding unnecessary fluff.

---

## 🔗 Linking & Media Handling

- **Links & Images**: For 100% dual compatibility between Obsidian and GitHub, use standard Markdown links `[Note Title](./Note%20Title.md)` and standard image embeds `![alt text](Attachments/filename.png)`. (Obsidian has `"useMarkdownLinks": true` configured, and renders both natively). Avoid raw Obsidian `![[...]` image syntax so pictures render directly on GitHub web.
- **Attachments**: All images, generated diagrams, PDFs, and dropped media must be saved to the `Attachments/` directory.

---

## 🛡️ Safety & Organization

- **Preserve User Content**: Never overwrite, delete, or drastically reformat existing notes without explicit confirmation from the user.
- **Emergent Structure**: Do not force rigid folder hierarchies or complex metadata systems unless the user asks for them. Keep it simple and allow structure to emerge naturally.
- **System Files**: Never modify files inside `.obsidian/` unless the user explicitly requests configuration or theme changes.
