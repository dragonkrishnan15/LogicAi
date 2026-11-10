# master-skill: always-on global rule (v5.3 Apex-Karpathy Overpowered Edition)

For EVERY request to write, modify, refactor, debug, fix, review, optimize, test,
explain, migrate, or deploy code, config, scripts, SQL, or infrastructure (any
language, any stack, any shell), you MUST load and follow the `master-skill`
workflow before acting. If the user types `/master-skill` or `/ms`, apply it too.

Skill locations:
- `%USERPROFILE%\.gemini\config\skills\master-skill\SKILL.md`
- `%USERPROFILE%\.gemini\antigravity\skills\master-skill\SKILL.md`
- `.agents\skills\master-skill\SKILL.md`

## 0. Gate - emit this line first, then act
`[ACCESS read|write][RUN interactive|headless][SIZE trivial|standard|complex][SHELL pwsh|ps51|cmd|posix]`

- ACCESS=read only if explaining, reviewing, auditing or finding usages AND no file changes, builds, tests, or installs are needed. Anything else is write.
- RUN=headless if running background, unattended, CI, or without user interaction channels. Else interactive.
- SIZE: trivial (local single-line/quick), standard (function/bug/feature), complex (multi-module, public API, migration, concurrency, security, data-loss risk).
- SHELL: pwsh / ps51 / cmd / posix (probe once with `$PSVersionTable` if unknown).

## Core Superpowers Enforced
1. **Radical Simplicity & 200-to-50 Rule (Karpathy Protocol)**: Minimum code that solves the problem; nothing speculative. Pass the Senior Engineer Sniff Test. If 200 lines could be 50, rewrite it. No speculative abstractions, unrequested caches, or single-use class hierarchies.
2. **Surgical Diffs & Zero Drive-by Refactoring**: Touch only what you must. Never reformat adjacent code or clean up pre-existing dead code unasked. Clean only orphans created by YOUR changes. Every changed line must trace directly to the user's prompt.
3. **Ambiguity Surfacing & Push Back**: Don't assume silently. When multiple interpretations exist, surface them before coding. If a simple 10-line solution exists, push back on over-engineered requests.
4. **Task Contract Engine**: For standard and complex tasks, write `<tmp>/ct-contract.json` defining exact permitted/forbidden paths and invariants before the first edit.
5. **Multi-Agent Mesh Locking**: Acquire decentralized mesh locks (`safety mesh lock` or `.master-skill/mesh-locks.json`) to prevent collisions across concurrent agents.
6. **Pre-Mortem Failure Stress-Test**: Stress-test concurrency, dependency drops, poison payloads, and scale before coding.
7. **Token & Context Discipline**: Treat tokens like money. Never dump files $>400$ lines; outline and slice with ripgrep. Filter logs/tests before reading into context.
8. **Circuit Breakers & Failsafes**: Auto-stop on 2 identical command failures or 3 failed approaches. Zero-destruction wall on destructive git/database commands (`safety intercept`).
9. **The Test Adversary & Goal-Driven Gate**: Turn tasks into checkable targets. Bug fix = reproduction test failing before, passing after. Attack logic with red-team fault injection.
10. **Evidence Chain & Immutable Ledger**: Append tool outcomes to `<tmp>/ct-ledger.jsonl`. Every report claim MUST cite an Evidence ID (`[EV-xxx]`).
11. **Programmatic Stop Gate**: Run `safety gate` (or `scripts/stop_gate.ps1` / `.sh`). Completion is rejected unless the stop gate script exits with code 0.
12. **1-Screen Precision Question Schema**: When user input is needed on a one-way door, ask exactly ONE question with context, trade-off matrix, clear **(Recommended)** tag, and a zero-friction default action.
13. **Autonomous Visual Verification & Anti-Slop Gate**: For Web/UI tasks, verify with real browser subagent (0 console errors, no 404s, responsive checks, screenshot proof).
14. **Diff Health & Scorecard**: Pre-commit automated scorecard auditing churn, net lines, blast radius, and 0 `DEBUG-CT` leftovers (`safety report`).

## Hard Rules
- Pre-existing dirty files are **USER-OWNED**; never touch, stage, stash, format, or revert them unasked.
- Checkpoint before every atomic step; on failure, STOP and REVERT to the checkpoint (never stack patches).
- STOP and show a one-screen trade-off matrix for one-way doors. Two-way doors are decided autonomously and logged as assumptions.
- Forbidden without explicit permission: `git reset --hard`, `git clean -fd`, `git checkout .`, stashing user changes, force-push, history rewrite, deleting files you did not create, editing tests just to turn them green.
- Report results first, short: what changed, verified how with cited Evidence IDs (`[EV-xxx]`), health scorecard, and new project memory recorded.
