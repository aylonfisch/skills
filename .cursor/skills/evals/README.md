# Evals Skill

A self-improvement loop for AI agent systems. Captures bad responses, diagnoses root causes, applies fixes to the right artifact, and generates regression tests — so the same mistake doesn't happen twice.

---

## Install

1. Copy the entire `.cursor/skills/evals/` folder into your own `.cursor/skills/` directory
2. That's it — no dependencies

The folder includes `SKILL.md` (the workflow), `README.md` (this file), and `evals-log.md` (the log template).

---

## Usage

| Trigger | What happens |
|---|---|
| `"flag this"` | Captures the current bad response and starts the eval flow |
| `"run eval"` | Same as above, more explicit |
| `"that didn't work"` | Auto-detected as a failure trigger |
| `"close session"` | Scans the full conversation for any failures and bulk-logs before context is lost |

The skill also **auto-triggers** after 2+ iterations on the same request.

---

## How It Works

```
Bad response
    ↓
Step 1: Capture — what was asked, what went wrong, what should have happened
    ↓
Step 2: Diagnose — assign a root cause code (RC-1 through RC-5)
    ↓
Step 3: Fix — edit the right artifact (rule, skill, or knowledge file)
    ↓
Step 4: Test — generate a regression test prompt + expected output
    ↓
Step 5: Log — append entry to evals-log.md
```

---

## Root Cause Codes

| Code | Cause | Fix Target |
|---|---|---|
| RC-1 | Rule gap — AI ignored a behavioral constraint | `.cursor/rules/` |
| RC-2 | Skill gap — Workflow step missing or wrong | `SKILL.md` |
| RC-3 | Knowledge gap — Missing domain/product context | `Knowledge/` file |
| RC-4 | Prompt ambiguity — Phrasing reliably misleads | Skill trigger or Step 1 |
| RC-5 | Model limit — Not fixable by instructions | Log only |

---

## Log Format

Entries are appended to `evals-log.md` by the skill. Each entry includes:
- Date, session ID, iteration count
- Prompt, bad response summary, expected response
- Root cause code + explanation
- Fix applied (file + change)
- Regression test case + status (`[ ] Untested` → `[~] Partial` → `[x] Verified`)

---

## Adapting for Your Setup

- **Different AI tool?** The skill is written for Cursor but the logic is tool-agnostic. Adapt trigger phrases to match your system.
- **Different folder structure?** Update the log path in `SKILL.md` Step 5.
- **No skills system?** Run the steps manually — the diagnosis + fix framework works as a standalone process.
