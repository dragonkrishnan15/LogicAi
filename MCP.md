# 🌐 LogicAi Model Context Protocol (MCP) Server

Connect **LogicAi** directly to **Google Antigravity**, **Anthropic Claude Code / Desktop**, **Cursor IDE**, **Windsurf**, or any MCP-compliant agent.

---

## ⚡ Instant MCP Setup (1-Copy Configuration)

Add this block directly into your MCP configuration file:

### 1. Google Antigravity (`~/.gemini/antigravity/mcp_config.json`)
```json
{
  "mcpServers": {
    "logicai": {
      "command": "node",
      "args": ["D:/claude-thinking/bin/logicai-mcp.js"]
    }
  }
}
```

### 2. Remote / GitHub-Direct Setup (Zero Local Clone)
Any agent on any computer with Node can run it directly from GitHub:
```json
{
  "mcpServers": {
    "logicai": {
      "command": "npx",
      "args": ["-y", "github:dragonkrishnan15/LogicAi", "mcp"]
    }
  }
}
```

### 3. Cursor IDE (`.cursor/mcp.json` or Settings > Features > MCP)
```json
{
  "mcpServers": {
    "logicai": {
      "command": "node",
      "args": ["D:/claude-thinking/bin/logicai-mcp.js"]
    }
  }
}
```

### 4. Claude Desktop (`claude_desktop_config.json`)
```json
{
  "mcpServers": {
    "logicai": {
      "command": "node",
      "args": ["D:/claude-thinking/bin/logicai-mcp.js"]
    }
  }
}
```

---

## 🛠️ MCP Tools Exposed to AI Agents

Once registered, your AI assistant receives 10 superpowers:

| Tool | Description |
| :--- | :--- |
| **`logicai_remember`** | Stores concise architectural decisions, system quirks, and project invariants to persistent memory (`<4KB`, zero token bloat). |
| **`logicai_recall`** | Retrieves all remembered quirks, invariants, and architectural decisions across restarts. |
| **`logicai_simplify`** | Audits diffs or proposed code against the Karpathy Senior Engineer Sniff Test and 200-to-50 line rule (flags over-abstraction and unrequested caching). |
| **`logicai_validate_command`** | Intercepts commands against the Zero-Destruction Wall (blocks `reset --hard`, force-push, root deletes). |
| **`logicai_init_contract`** | Generates an immutable task boundary contract (`ct-contract.json`). |
| **`logicai_verify_gate`** | Executes the pre-commit quality gate verifying 0 debug tags, 0 secrets, and clean test runs. |
| **`logicai_mesh_lock`** | Acquires decentralized multi-agent file locks preventing concurrent AI conflicts. |
| **`logicai_mesh_unlock`** | Releases acquired multi-agent locks. |
| **`logicai_mesh_status`** | Displays currently active locks across all agents. |
| **`logicai_scorecard`** | Computes diff churn ratio, net lines added/deleted, and cleanliness metrics. |
