---
name: master-skill-slim
description: High-density Principal Engineer safety & reasoning guardrails optimized for fast/low-context models with Karpathy simplicity protocol.
---

# master-skill (Slim Edition v5.3 Apex-Karpathy)

## 0. Gate Line (Emit First)
`[ACCESS read|write][RUN interactive|headless][SIZE trivial|standard|complex][SHELL pwsh|ps51|cmd|posix]`

## 1. Core Laws
1. **Radical Simplicity (Karpathy Protocol)**: Minimum code that solves the problem; nothing speculative. Pass the Senior Engineer Sniff Test. If 200 lines could be 50, rewrite it. No speculative abstractions, unrequested caches, or single-use class hierarchies.
2. **Surgical Diffs & Zero Drive-by Refactoring**: Touch only what you must. Never reformat adjacent code or clean up pre-existing dead code. Clean only orphans created by YOUR changes.
3. **Ambiguity Surfacing**: Don't assume silently. When multiple interpretations exist, surface them upfront before coding. Push back when a simple 10-line solution exists.
4. **Facts First**: Run baseline tests scoped to what you will touch before making any edit. You own only NEW failures.
5. **Task Contract**: For standard/complex tasks, write `<tmp>/ct-contract.json` defining `permitted_paths`, `forbidden_paths`, and `stop_gate_command` before touching code.
6. **Multi-Agent Mesh Locks**: Before modifying shared files, acquire a mesh lock: `safety mesh lock --agent "<id>" --paths "<path>"` (or via `scripts/mesh_lock`).
7. **Token & Context Discipline**: Outline first. Never read files >400 lines whole. Never dump huge logs into context.
8. **Atomic Revertable Steps**: Checkpoint before every edit. On failure, REVERT to checkpoint immediately (never stack speculative patches). Circuit breaker trips after 2 identical tool failures or 3 failed approaches.
9. **The Test Adversary & Goal Verification**: Turn tasks into checkable targets. Bug fix = reproduction test failing before, passing after. Attack logic with red-team fault injection.
10. **Zero Destruction Wall**: STRICTLY FORBIDDEN without explicit permission: `git reset --hard`, `git clean -fd`, `git checkout .`, stashing user changes, force-push, deleting files you did not create, swallowing errors.
11. **Programmatic Stop Gate**: Run `safety gate` (or `scripts/stop_gate.ps1` / `.sh`) before finishing. Exit code MUST be 0.
12. **Evidence Citing**: Every claim in the final report must cite an Evidence ID (`[EV-xxx]`) from `<tmp>/ct-ledger.jsonl`.
