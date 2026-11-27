<p align="center">
  <b>English</b> | <a href="README_TH.md">ภาษาไทย</a>
</p>

# Noah Ark Code Studio

**A lightweight, standalone Windows AI Coding IDE — Diff-First editing, 1-click Checkpoint Rollback, Anti-Burn API guardrails, Local & Cloud BYOK, and a One-Time Offline License (no monthly subscription).**

- **Latest Release (Windows 64-bit):** [Download `NoahArkCodeStudio_Setup_v1.0.0.exe`](https://github.com/Nightlance-Official/noah-ark-code-studio/releases/latest)
- **Purchase License Key / Official Page:** [Nightlance Official (Facebook)](https://www.facebook.com/NightlanceOfficial)
- **Free Companion Chat App:** [Noah Ark AI Chat](https://github.com/Nightlance-Official/noah-ark-ai-chat)

---

## Screenshots

### Interactive Hunk-Level Diff Review (`Edit` Mode)
<img width="2880" height="1704" alt="Noah Ark Code Studio en test1" src="https://github.com/user-attachments/assets/3b1fcb13-063b-4c41-9762-d7ac2eed38fb" />

### `Auto (Safe)` Mode + Automatic Verification & Checkpoints
<img width="2880" height="1704" alt="Noah Ark Code Studio en test2" src="https://github.com/user-attachments/assets/941ec58b-5912-4d6f-b7f3-2aae7867a8cd" />

### 100% Offline Coding with Local Ollama
<img width="2880" height="1704" alt="Noah Ark Code Studio image" src="https://github.com/user-attachments/assets/5c0b4751-0462-4c8e-aeff-d7361c21a623" />

---

## Why Noah Ark Code Studio?

- **One-Time Offline License (No Subscription, No Server Lock-In):** Verified 100% locally via Ed25519 cryptographic signatures. No monthly IDE fees, no cloud account login, and your license stays active even when working completely offline.
- **Bring Your Own AI (Local + Cloud):** Code offline with **Ollama** or **LM Studio**, or plug in your own API keys for **Google Gemini, OpenRouter, NVIDIA NIM, Groq, DeepSeek, OpenAI, Mistral AI**, and custom OpenAI-compatible endpoints.
- **Built for Safety & Cost Control:** Every AI edit is protected by **Diff-First Review** or **Automatic Checkpoints**, **Workspace Jail**, **Sensitive File Guards (`.env`, `.key`, `.pem`)**, and **Anti-Burn** token/cost/round checkpoints so AI loops never drain your API credits.

---

## Key Features

### 1. Three Controlled AI Coding Modes
- **`Plan` Mode (Default):** Read-only project exploration, code explanation, and step-by-step architecture planning.
- **`Edit` Mode (Diff-First):** AI inspects your project and queues proposed changes as Unified Diffs in the **Diff Review** tab. Review, accept, or reject individual hunks before touching any file on disk.
- **`Auto (Safe)` Mode:** Enables hands-free `Edit -> Test -> Fix` loops with layered guardrails:
  - Automatic **Checkpoint backup** before every single file write.
  - **Dirty-Tab Guard:** Never overwrites a file you are actively editing unsaved in a tab (routes to Diff Review instead).
  - **Safe Command Allowlist:** Auto-runs only safe verification/test commands (`py_compile`, `pytest`, `unittest`, `ruff check`, `flake8`, `mypy`, `git status/diff/log`) with shell chaining/redirection blocked; all other commands still require explicit confirmation.
  - **Consecutive Fail-Streak Breaker:** Stops and summarizes automatically after N failed test attempts (`0–30`, default `8`).

### 2. Interactive Diff Viewer, Checkpoints & External Drift Protection
- **Hunk-Level Diff Review:** Inspect multi-file patch queues, toggle individual hunks, and apply safely with SHA-256 original-file verification and atomic file writes.
- **1-Click Checkpoint Rollback:** Browse every saved checkpoint's Unified Diff and roll back any file in one click.
- **External File Drift Watcher:** Detects if a file was modified outside the IDE and warns before overwriting.

### 3. Essential IDE Workspace Tools
- **Project Explorer & Multi-Tab Code Editor:** Hierarchical file tree with `🔒` sensitive file indicators, Pygments syntax highlighting across programming languages, automatic preservation of original line endings (`CRLF`/`LF`) and `UTF-8 BOM`, `Ctrl+F` find/replace, and `Ctrl+Shift+F` project-wide search.
- **Safe Test & Command Runner:** Automatically resolves your project's own Python environment (`.venv` / `venv` / `PATH`), scrubs API keys from subprocess environments, terminates full process trees cleanly via Windows Job Objects, and provides **Populate-Only** Quick Presets & *"Send Error to AI"* (`<= 100` tail lines) so nothing executes or spends tokens without your review.
- **Async Git Panel:** Runs all `git` commands in background threads (zero UI freeze), warns/generates `.gitignore` when `.venv` or `node_modules` exist, blocks accidental staging of sensitive files (`.env`, `.key`, `.pem`), supports unborn-HEAD unstaging, and prompts for Git `user.name`/`user.email` if not yet configured.

### 4. Multi-Provider AI & Anti-Burn Guardrails
- Supports **Ollama**, **LM Studio** (auto load/unload), **Google Gemini**, **OpenRouter**, and **3 Custom OpenAI-Compatible Slots** (7 quick presets).
- Configurable limits: Local Context up to `1,048,576`, Cloud Context up to `1,048,576`, Cloud Max Tokens (`0 = Provider Default` up to `131,072`), per-turn Cloud token limit, API round checkpoint, OpenRouter USD cost limit, and automatic Loop Breaker.
- Live **English | ไทย** UI switching, Pure Black (`OLED #000000`) / Dark / Light themes, and isolated per-project chat history in `%LOCALAPPDATA%\NoahArkCodeStudio\studio_chats.sqlite3` with lock-safe `VACUUM`.

### 5. Standalone OR Paired with Noah Ark AI Chat
- Works completely standalone, or pairs automatically with [Noah Ark AI Chat](https://github.com/Nightlance-Official/noah-ark-ai-chat) via Windows Registry discovery — hand off workspace folder, target file/line, active model, and sanitized conversation context in one click.

---

## Installation & Offline License Activation

1. Download **`NoahArkCodeStudio_Setup_v1.0.0.exe`** from the [Releases page](https://github.com/Nightlance-Official/noah-ark-code-studio/releases/latest) and run the installer.
2. Launch **Noah Ark Code Studio** — the **License Activation** window will display your unique **Machine ID** (`NCS-XXXX-XXXX-XXXX`).
3. Click **Copy Machine ID** and send it via our official page to purchase your License Key:
   - **Official Facebook Page:** https://www.facebook.com/NightlanceOfficial
4. Paste your received **License Key** (`NACS1....`) and click **Activate License** — unlocks immediately and runs **100% offline**.
5. **Updating to a newer version:** Use **Settings -> Check for Updates**, download the latest installer, and install over the existing installation. Your `license.key`, settings, project chats, and checkpoints in `%LOCALAPPDATA%\NoahArkCodeStudio\` are preserved automatically.

### System Requirements
- **OS:** Windows 10 / Windows 11 (64-bit)
- **RAM:** 4 GB minimum (8 GB+ recommended; 16 GB+ if running local Ollama models)
- **Optional:** [Git for Windows](https://git-scm.com/) (for the Git tab), Python/Node/etc. for running your own projects, and [Ollama](https://ollama.com/) / [LM Studio](https://lmstudio.ai/) for local offline AI.

---

## License & Open Source Notices

Noah Ark Code Studio is proprietary commercial software requiring a valid License Key per machine.

This application dynamically links to **Qt for Python (PySide6)** and **Qt6** libraries licensed under the **GNU Lesser General Public License v3.0 (LGPLv3)**. All Qt/PySide6 shared libraries (`.dll` / `.pyd`) remain separate, replaceable files inside the installation directory in compliance with LGPLv3 Section 4(d)(1). Full third-party notices are included in `THIRD-PARTY-LICENSES.txt` and viewable inside **Settings -> Open Source Licenses**.

---

## Contact & Support

- **License Purchase & Official Page:** https://www.facebook.com/NightlanceOfficial
- **Bug Reports & Feature Requests:** [GitHub Issues](https://github.com/Nightlance-Official/noah-ark-code-studio/issues)
