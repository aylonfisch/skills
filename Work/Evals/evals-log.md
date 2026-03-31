# Evals Log

> Tracks bad AI responses, root causes, fixes applied, and regression tests.
> Updated by the `evals` skill. Reviewed monthly during weekly-reset.

---

## Root Cause Key

| Code | Root Cause | Fix Target |
|------|-----------|------------|
| RC-1 | Rule gap — AI didn't follow behavioral constraint | `.cursor/rules/` |
| RC-2 | Skill gap — Workflow step missing or wrong | `.cursor/skills/` |
| RC-3 | Knowledge gap — Missing domain/product/person context | `Knowledge/` or skill context section |
| RC-4 | Prompt ambiguity — Phrasing reliably misleads | Skill trigger or Step 1 |
| RC-5 | Model limit — Structural, not fixable by instructions | Log only |

---

## Test Status Key

- `[ ] Untested` — Fix applied, test not yet run
- `[~] Partial` — Fix helped but not fully resolved
- `[x] Verified` — Test passed, regression confirmed closed

---

<!-- Entries appended below by evals skill -->
