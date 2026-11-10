# Simplicity & Anti-Overengineering Audit (The Karpathy Protocol)

> "Minimum code that solves the problem. Nothing speculative. Touch only what you must. Clean up only your own mess." — Andrej Karpathy

Guidelines and invariant checks to prevent common LLM pitfalls: speculative abstraction, drive-by refactoring, unverified assumptions, and cognitive bloat.

---

## 1. The Senior Engineer Sniff Test

Before writing or approving any implementation, subject it to the Sniff Test:
> **"Would a senior staff engineer review this and say it is overcomplicated?"**

If the answer is **YES** or **LIKELY**, stop and simplify immediately.

### The 200-to-50 Line Rule
If you wrote 200 lines of boilerplate, class hierarchies, or configuration factories when 50 lines of clean, idiomatic code solve the exact same problem:
- **Do not ship it.**
- Rewrite it to the 50-line version before running verification.

---

## 2. The Speculative Feature Ban (YAGNI on Steroids)

LLMs naturally tend to hallucinate future requirements and invent unrequested complexity. The following are strictly banned unless explicitly requested by the user:

| Speculative Pattern | Banned Behavior | Permitted & Encouraged Behavior |
| :--- | :--- | :--- |
| **Strategy & Factory Patterns** | Creating `DiscountStrategy(ABC)`, `PercentageDiscount`, `FixedDiscount`, `DiscountFactory` when only one discount type was requested. | Plain, standalone function: `def calculate_discount(amount, percent): return amount * (percent / 100)`. |
| **Unrequested Caching** | Adding Redis, LRU memory caches, or cache invalidation layers to standard database queries. | Direct query execution. Add caching only when a reproducible performance benchmark proves a bottleneck. |
| **Speculative Configuration** | Adding environment variables, config dictionaries, or flags for things that never change. | Pinned constant or direct parameter. |
| **Defensive Paranoia** | Writing 10 nested try/except blocks and fallback handlers for internal functions that cannot fail. | Let impossible errors bubble or validate at external input boundaries only. |
| **Generic Frameworks** | Building an extensible plugin architecture when implementing a single concrete feature. | Implement the single concrete feature directly. |

---

## 3. Surgical Changes & Zero Drive-by Refactoring

Every modification must be a surgical strike.

### The Line-by-Line Attribution Test
> **Every single changed line in `git diff` must trace directly to the user's request.**

### Rules for Touching Existing Code:
1. **Never "Improve" Adjacent Code**:
   - Do NOT reformat adjacent lines.
   - Do NOT "clean up" variable names, types, or comments you weren't asked to touch.
   - Do NOT reorganize imports across the entire file.
2. **Match Existing Style**:
   - Even if the existing file uses older syntax, 2-space indentation, tabs, or non-preferred naming, match the surrounding style perfectly.
3. **Clean Up Only Your Own Mess**:
   - If **your** change makes a variable, import, or helper unused $\rightarrow$ **remove it immediately**.
   - If you notice **pre-existing** dead code or unused variables $\rightarrow$ **do NOT delete them silently**. Mention them in your report under notes.

---

## 4. Goal-Driven Execution Loop

Never accept a vague instruction without converting it into a checkable, deterministic target:

| Vague Goal | Deterministic Success Target |
| :--- | :--- |
| *"Fix the bug where search crashes on empty string"* | Write test calling `search("")`; observe failure; implement fix; verify test passes. |
| *"Make validation stricter"* | Write tests with invalid inputs (empty string, out-of-bounds, bad types); verify rejection; write tests with valid inputs; verify acceptance. |
| *"Refactor database helper"* | Run existing test suite $\rightarrow$ verify all GREEN before touching code $\rightarrow$ refactor $\rightarrow$ verify all GREEN after. |

---

## 5. Simplicity Checklist (Run Before Every Git Commit)

- [ ] Does this diff contain any class, function, or parameter that wasn't strictly necessary?
- [ ] Could any function in this diff be rewritten in half the lines without losing clarity?
- [ ] Are all changed lines traceable directly to the user prompt?
- [ ] Did I refrain from touching or reformatting adjacent lines?
- [ ] Did I remove only the orphans created by my changes, leaving pre-existing code untouched?
- [ ] Did I prove correctness with a deterministic test rather than guessing?
