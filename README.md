# Public Notes

A curated collection of public technical notes, architecture cheat sheets, and masterclass takeaways, organized as an Obsidian knowledge vault synced with Git and GitHub.

---

## 🚀 Quick Reference

| Action | macOS | Windows / Linux | What It Does |
| :--- | :--- | :--- | :--- |
| **New Note** | `Cmd + N` | `Ctrl + N` | Create a new blank note immediately |
| **Quick Switcher** | `Cmd + O` | `Ctrl + O` | Find any note by name, or create one |
| **Command Palette** | `Cmd + P` | `Ctrl + P` | Access all Obsidian and Git commands |
| **Wikilink** | `[[Note Name]]` | `[[Note Name]]` | Connect one note to another |
| **Backup / Sync** | `Cmd + P` -> `Git: Commit-and-sync` | `Ctrl + P` -> `Git: Commit-and-sync` | Push notes to GitHub (also auto-syncs) |

---

## 📁 How It Works

- **Write freely**: Just create notes whenever an idea strikes (`Cmd + N` / `Ctrl + N`).
- **Pasted Images & Media**: Automatically stored in `Attachments/` to keep your workspace tidy.
- **Organic Structure**: When patterns or recurring themes emerge, group or link them naturally!
- **Guide**: Read [[Obsidian Basics]] for a starter guide on shortcuts, links, and graph view.

---

## 📚 Available Notes

- [[ContainerDays Singapore 2026|**ContainerDays & AI Context Singapore 2026 (Executive Conference Summary)**]] — Comprehensive 2-day conference digest across 16 attended sessions, keynotes, and workshops at Suntec Singapore. Focuses on Kubernetes agent sandboxes (`agents.x-k8s.io`), disaggregated Token Factories, agent-native developer platforms, and LLM gateway governance.
  - [Building a High-Performance Token Factory (Jerry Chen · DaoCloud / d.run)](./Building%20a%20High-Performance%20Token%20Factory%20(Jerry%20Chen).md) — Heterogeneous compute pooling (HAMi/DRA/Kueue), 4-tier KV cache inventory (ContextStore), and MatrixHub model hydration.
  - [Your Next Platform User Isn't Human (Yashod Perera · OpenChoreo)](./Your%20Next%20Platform%20User%20Isn%27t%20Human%20-%20Building%20an%20AI-Native%20Developer%20Platform%20(Yashod%20Perera).md) — Moving past human portals; exposing Control Plane & Observability MCP servers with CEL-rendered abstractions.
  - [Operating Agentic Software Factories (Carl Ross · OpenAI)](./When%20Tokens%20Stop%20Being%20the%20Bottleneck%20-%20Operating%20Agentic%20Software%20Factories%20(Carl%20Ross).md) — Asymptotic token economics, WASM actor swarms, and deterministic verification harnesses.
  - [Governing the Agentic Stack on Kubernetes (Robin Cher · Kong)](./Governing%20the%20Agentic%20Stack%20on%20Kubernetes%20-%20MCP%2C%20A2A%2C%20and%20LLM%20Traffic%20(Robin%20Cher).md) — 1 Gateway, 3 Profiles (LLM, MCP, A2A) enforcing token budgets, prompt injection guards, and tool RBAC.
  - [Securing AI Coding Agents with Kubernetes Sandboxes (Ryan Djurovich)](./Securing%20AI%20Coding%20Agents%20with%20Kubernetes%20Sandboxes%20(Ryan%20Djurovich).md) — Ephemeral Kubernetes Sandbox CRD, Linux Landlock filesystem restrictions, and SPIFFE mTLS identities.
  - [[Fireside Chat with Kelsey Hightower & Geet Bhanawat]] — Infrastructure fundamentals, 1-5-60 telecom triage benchmarks, and 5G network slicing.
- [[Obsidian in 10 Mins - From Notes to Knowledge Graph & AI|**Obsidian in 10 Minutes: From Manual Notes to Linked Thinking & AI**]] — 10-minute presentation outline on OneNote vs. Obsidian, linked thinking vs. folders, knowledge graphs, and local AI agent workflows.
- [[AI-Generated Code == Code You Can Trust - AISG & Sonar at EDB|**AI-Generated Code == Code You Can Trust? (AISG & Sonar at EDB)**]] — Harness engineering (Flue, dsh), context engineering, production reliability, and autonomous code review with AI Singapore and Sonar.
- [[Build Agents with Google Agent CLI|**Build Agents with Google Agent CLI**]] — Notes, setup guide, architecture flow, and takeaways for `google/agents-cli` and Google ADK.
- [**Shipping Reliable AI Agents - Building with Langfuse and ClickHouse (Max Deichmann)**](./Shipping%20Reliable%20AI%20Agents%20-%20Building%20with%20Langfuse%20and%20ClickHouse%20(Max%20Deichmann).md) — Observability, trace-level debugging, evaluation loops, and ClickHouse columnar scale by Max Deichmann (CTO, Langfuse).

---

## 💻 Multi-Platform Setup Guide

When setting up this vault on your other devices, follow these steps:

### 1. Linux: Ubuntu & Arch / Omarchy

1. **Install Git & SSH**:
   - **Ubuntu**: `sudo apt update && sudo apt install -y git openssh-client`
   - **Arch / Omarchy**: `sudo pacman -S git openssh`
2. **Configure GitHub SSH Key**:
   - Ensure your SSH key is added to GitHub:
     ```bash
     ssh -T git@github.com
     ```
3. **Clone the Vault**:
   ```bash
   git clone git@github.com:geeksperiments/public_notes.git ~/public_notes
   ```
4. **Install Obsidian**:
   - **Arch / Omarchy**: `yay -S obsidian` (or from official package manager)
   - **Ubuntu**: Install via deb package or Flatpak: `flatpak install flathub md.obsidian.Obsidian`
5. **Open Vault**:
   - Launch Obsidian -> Click **Open folder as vault** -> Select `~/public_notes`.
   - Settings and theme will load automatically. Enable the **Git** plugin under **Community plugins** if prompted.

---

### 2. Windows

1. **Install Git for Windows**:
   - In PowerShell: `winget install --id Git.Git -e` (or download from [git-scm.com](https://git-scm.com)).
2. **Configure GitHub SSH**:
   - Open Git Bash or PowerShell and verify your SSH connection:
     ```powershell
     ssh -T git@github.com
     ```
3. **Clone the Vault**:
   ```powershell
   git clone git@github.com:geeksperiments/public_notes.git "$HOME\Documents\public_notes"
   ```
4. **Install Obsidian**:
   - In PowerShell: `winget install Obsidian.Obsidian` (or from [obsidian.md](https://obsidian.md)).
5. **Open Vault**:
   - Launch Obsidian -> Click **Open folder as vault** -> Select `Documents\public_notes`.

---

### 3. Android (Mobile)

Because Android runs in a sandboxed mobile environment without a system Git CLI, the **Obsidian Git** community plugin uses a built-in mobile Git engine via a **GitHub Personal Access Token (PAT)**:

#### Step A: Generate a GitHub Personal Access Token (PAT)
1. On your computer or mobile browser, go to **GitHub.com** -> **Settings** -> **Developer settings** -> **Personal access tokens** -> **Tokens (classic)**.
2. Click **Generate new token (classic)**.
3. Name it: `Obsidian Android Sync`.
4. Scope: Check the **`repo`** checkbox (gives full control of private repositories).
5. Generate and copy the token (starts with `ghp_...`).

#### Step B: Set Up Obsidian on Android
1. Install **Obsidian** from the Google Play Store.
2. Open Obsidian and create an empty vault named `public_notes` (choose internal storage / Documents).
3. Go to **Settings** -> **Community plugins** -> Turn off Restricted mode.
4. Search for and install **Git** (by *Vinzent*), then **Enable** it.
5. In Obsidian on Android, open the Command Palette (swipe down from top):
   - Run: **`Git: Clone an existing remote repo`**
   - Enter repo URL: `https://github.com/geeksperiments/public_notes.git`
   - Enter your GitHub username: `geeksperiments` (or your GitHub handle)
   - Enter your Personal Access Token (the `ghp_...` token from Step A).
   - Enter depth: `1` (or leave default).
6. Once cloned, your notes, theme, and settings will sync!
7. In the **Git** plugin settings on mobile:
   - Set **Vault backup interval**: `10` minutes.
   - Set **Auto pull interval**: `10` minutes.
   - Set **Auto pull on startup**: `ON`.

---

## 🛡️ Multi-Device Conflict Prevention Tips

- **Keep Auto-Pull on Startup ON**: This ensures that whenever you open Obsidian on any device (Mac, Windows, Linux, Android), it fetches the latest notes from GitHub before you begin typing.
- **Don't Commit Workspace Files**: `.obsidian/workspace.json` and `.obsidian/workspace-mobile.json` are already in `.gitignore`. This ensures that open tabs and panel layouts on your laptop won't conflict with your mobile screen.
- **If a Conflict Ever Occurs**:
  - Obsidian Git will notify you.
  - Conflict files are saved with standard Git conflict markers (`<<<<<<< HEAD`), making it easy to keep the content you want.
