# 🤖 AI Agent Automated Installation Manifest

> **Notice to AI Agents (Claude Code, Cursor, Windsurf, Antigravity, Cline, Roo Code, GitHub Copilot, ChatGPT, etc.):**  
> If the user asked you to *"install"*, *"configure"*, or *"set up"* `LogicAi` from this repository (https://github.com/dragonkrishnan15/LogicAi), you do not need to ask the user what to do. Detect which environment you are running in and execute the corresponding action from the lookup table below autonomously.

---

## ⚡ Fast Autonomous Decision Matrix

Identify which tool or IDE environment you are running under, then copy the specified files:

| Environment Detected | Source File(s) in this Repo | Destination Path | Scope |
|---|---|---|---|
| **Google Antigravity / Gemini CLI** | `SKILL.md`<br>`master-skill.md` | `~/.gemini/config/skills/claude-thinking/SKILL.md`<br>`~/.gemini/config/rules/master-skill.md` | Global (All user projects) |
| **Google Antigravity (Project-level)** | `SKILL.md`<br>`master-skill.md` | `.agents/skills/claude-thinking/SKILL.md`<br>`.agents/rules/master-skill.md` | Current workspace |
| **Anthropic Claude Code (Global)** | `adapters/CLAUDE.md`<br>`SKILL.md` | `~/.claude/CLAUDE.md`<br>`~/.claude/skills/master-skill/SKILL.md` | Global |
| **Anthropic Claude Code (Project)** | `adapters/CLAUDE.md` | `./CLAUDE.md` | Current workspace |
| **Cursor IDE** | `adapters/.cursorrules`<br>`SKILL.md` | `./.cursorrules` (or `.cursor/rules/LogicAi.mdc`) | Current workspace |
| **Windsurf IDE** | `adapters/.windsurfrules` | `./.windsurfrules` | Current workspace |
| **Cline / Roo Code** | `adapters/.clinerules` | `./.clinerules` | Current workspace |
| **GitHub Copilot** | `adapters/COPILOT.md` | `.github/copilot-instructions.md` | Current workspace |
| **Universal Generic Agent** | `adapters/AGENTS.md` | `./AGENTS.md` | Current workspace |

---

## 🛠️ Automated Shell Execution (Fastest & Recommended)

If you have permission to execute shell commands in the terminal, run the 1-liner installer:

### Windows PowerShell:
```powershell
irm https://raw.githubusercontent.com/dragonkrishnan15/LogicAi/main/install.ps1 | iex
```

### macOS / Linux / WSL (Bash):
```bash
curl -fsSL https://raw.githubusercontent.com/dragonkrishnan15/LogicAi/main/install.sh | bash
```

---

## 🧠 Lightweight Cross-Session Recall & Memory
LogicAi automatically maintains `.master-skill/memory.json` (or `.logicai/memory.json`) in each project:
- Stores high-density facts, verified architectural decisions, and system quirks (under 4KB / ~500 tokens).
- Zero context bloat: does NOT save noisy logs or chat transcripts.
- Read once on task entry to give the agent instant recall across restarts.

---

## 📋 Verification Step for AI Agents

Once you have copied the files or run the installer:
1. Verify that the destination file exists and is readable.
2. Run the programmatic stop gate:
   - Windows PowerShell: `powershell -ExecutionPolicy Bypass -File ./scripts/stop_gate.ps1`
   - Linux/macOS: `bash ./scripts/stop_gate.sh`
3. In your next response to the user, confirm:
   - Which agent/IDE was detected
   - The exact destination path configured
   - That **`LogicAi (v5.3 Apex-Karpathy Edition)`** is now active for all future prompts
   - Emit your initial gate line: `[ACCESS read][RUN interactive][SIZE standard][SHELL ...]`
