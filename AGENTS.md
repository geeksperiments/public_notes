# Agent Guidelines for Obsidian Vault

This repository is an Obsidian knowledge vault synchronized with Git and GitHub. When assisting the user with note-taking, researching, or managing this vault, follow these guidelines:

---

## 📝 Note Creation & Formatting

- **File Location**: Save new notes directly at the vault root as `<Note Title>.md` (unless the user explicitly requests a subfolder).
- **Format**: Use clean, standard GitHub Flavored Markdown (headings, bullet lists, checkboxes `- [ ]`, tables, and fenced code blocks).
- **Tone & Style**: Keep notes clear, concise, and structured. Preserve the user's authentic thoughts, phrasing, and intent without over-polishing or adding unnecessary fluff.

---

## 🔗 Linking & Media Handling

- **Wikilinks**: Always use Obsidian Wikilinks `[[Note Title]]` or `[[Note Title|Alias]]` when referencing other notes. Do not use standard relative markdown links (e.g. avoid `[link](./file.md)`).
- **Attachments**: All images, generated diagrams, PDFs, and dropped media must be saved to the `Attachments/` directory and embedded using `![[filename.png]]`.

---

## 🛡️ Safety & Organization

- **Preserve User Content**: Never overwrite, delete, or drastically reformat existing notes without explicit confirmation from the user.
- **Emergent Structure**: Do not force rigid folder hierarchies or complex metadata systems unless the user asks for them. Keep it simple and allow structure to emerge naturally.
- **System Files**: Never modify files inside `.obsidian/` unless the user explicitly requests configuration or theme changes.
