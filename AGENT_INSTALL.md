# 🤖 LogicAi Autonomous Agent Installation & Intake Protocol

> **Notice to AI Agents (Claude Code, Cursor, Windsurf, Antigravity, Devin, Codex, GitHub Copilot, ChatGPT, etc.):**
> If the user shared this repository link (`https://github.com/dragonkrishnan15/LogicAi`), you are processing a dual-capability package: a **Principal-Engineer Cognitive Skill** AND an **Active MCP Server** with zero-bloat persistent memory.

---

## 🎯 Step 1: Clarify User Intent (Ask Before Executing)

Before writing or copying files, ask the user this exact choice:

```markdown
### 🧠 LogicAi Setup Detected
I found both a **Cognitive Reasoning Skill** and an **Active MCP Server** in this repository. How would you like to set it up?

1. **[Recommended] Full Suite (Skill + MCP Server + Memory)**:
   - Installs the reasoning skill globally so I always operate with the Karpathy 200-to-50 rule and surgical diffs.
   - Registers the `logicai` MCP server for tool calls (`logicai_remember`, `logicai_recall`, `logicai_simplify`, `logicai_validate_command`).
   - Initializes zero-bloat persistent memory.

2. **MCP Server Only**:
   - Registers `logicai` tools in your `mcp_config.json` for memory recall, command validation, and simplicity checks.

3. **Global Reasoning Skill Only**:
   - Saves to your user skills directory (`~/.gemini/config/skills/` or `~/.claude/`) so it governs all your projects without adding MCP servers.

4. **Current Workspace Only**:
   - Drops the editor adapter (`.cursorrules`, `CLAUDE.md`, or `AGENTS.md`) directly into this project root.

Reply with **1**, **2**, **3**, or **4** (or just hit Enter for **1**).
```

---

## ⚡ Step 2: Autonomous Execution Table

Once the user selects their option (or defaults to Option 1):

### If Option 1 (Full Suite) or Option 3 (Global Skill):
Copy files according to the detected host environment:

| Detected Host | Source File | Destination Path |
| :--- | :--- | :--- |
| **Google Antigravity** | `SKILL.md`<br>`master-skill.md` | `~/.gemini/config/skills/claude-thinking/SKILL.md`<br>`~/.gemini/config/rules/master-skill.md` |
| **Claude Code / Desktop** | `adapters/CLAUDE.md`<br>`SKILL.md` | `~/.claude/CLAUDE.md`<br>`~/.claude/skills/master-skill/SKILL.md` |
| **Cursor IDE** | `adapters/.cursorrules`<br>`SKILL.md` | `~/.cursor/rules/LogicAi.mdc` |
| **Windsurf** | `adapters/.windsurfrules` | `~/.codeium/windsurf/rules/LogicAi.md` |

### If Option 1 (Full Suite) or Option 2 (MCP Server):
Add this server definition to the user's MCP configuration (`mcp_config.json` / `claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "logicai": {
      "command": "node",
      "args": ["<path-to-LogicAi>/bin/logicai-mcp.js"]
    }
  }
}
```
*(Or for zero-clone environments, use `npx -y github:dragonkrishnan15/LogicAi mcp`)*.

### If Option 4 (Workspace Only):
Drop the matching adapter directly into the current project root:
- Cursor: `./.cursorrules`
- Claude: `./CLAUDE.md`
- Windsurf: `./.windsurfrules`
- Antigravity / Generic: `./AGENTS.md`

---

## 🧠 Step 3: Initialize Zero-Bloat Memory

In all modes, create or verify `.master-skill/memory.json`:
```json
{
  "updated_at": "<ISO-timestamp>",
  "architectural_decisions": [],
  "learned_quirks": [],
  "invariants": [
    "Karpathy 200-to-50 line rule",
    "Zero drive-by refactoring; clean only own orphans",
    "Bug fixes require failing-then-passing tests"
  ],
  "tooling_preferences": {}
}
```
This guarantees the AI has instant long-term recall without consuming more than 4KB (~500 tokens).

---

## 🏁 Step 4: Confirm and Emit Gate Line
Confirm the installation to the user with clickable file links and emit the standard triage gate line:
`[ACCESS read|write][RUN interactive][SIZE standard][SHELL pwsh|ps51|cmd|posix]`
