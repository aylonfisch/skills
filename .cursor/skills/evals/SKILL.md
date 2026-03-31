---
name: evals
description: Capture, diagnose, fix, and test a bad AI response. Creates an eval entry and applies the fix to the right artifact (rule, skill, or knowledge file). Use when user says "flag this", "run eval", "that didn't work", "log this failure", or when the AI auto-detects 2+ iterations on the same request. Also handles "close session" — scans the full conversation for any failures and bulk-logs them before context is lost.
---

# Evals

> **Purpose:** Turn a bad response into a permanent improvement. Capture what happened, diagnose the root cause, apply the fix to the right artifact, then generate a test to confirm it won't happen again.

---

## Step 1: Capture

Collect the following — ask only what you can't infer from context:

- **Prompt:** What did the user originally ask?
- **Initial response:** What did the AI do wrong? (summarize briefly)
- **Expected response:** What should have happened?
- **Iteration count:** How many back-and-forths before it was resolved?

If the user invoked this mid-conversation, infer these from the conversation history. Only ask to fill gaps.

---

## Step 2: Diagnose Root Cause

Categorize the failure into exactly one primary cause:

| Code | Root Cause | Fix Target |
|------|-----------|------------|
| `RC-1` | **Rule gap** — AI didn't follow a behavioral constraint | Create/update a `.cursor/rules/` file |
| `RC-2` | **Skill gap** — Workflow step was missing or wrong | Update the relevant `SKILL.md` |
| `RC-3` | **Knowledge gap** — Missing context about domain, product, or person | Update a `Knowledge/` file or add context to skill |
| `RC-4` | **Prompt ambiguity** — User's phrasing reliably misleads | Add a trigger/clarification example to the relevant skill |
| `RC-5` | **Model limit** — Structural failure unlikely to be fixed by instructions | Log only, no fix applied |

State your diagnosis clearly:
> "Root cause: RC-[N] — [one sentence explanation]"

---

## Step 3: Apply the Fix

Based on root cause, make the targeted change:

- **RC-1** → Add or update a rule in `.cursor/rules/`. Keep it behavioral and concise.
- **RC-2** → Update the failing step in the relevant `SKILL.md`. If skill is unknown, search `.cursor/skills/` by keyword.
- **RC-3** → Add the missing context to the relevant `Knowledge/` file, or to the skill's context section.
- **RC-4** → Add a disambiguation example or trigger clarification to the skill's description or Step 1.
- **RC-5** → Skip the fix step. Log only.

After applying: state exactly what file was changed and what was added/modified in one sentence.

---

## Step 4: Generate a Test Case

Write a test case in this format:

```
**Test:** [Short label]
**Trigger:** [Exact prompt or scenario that caused the failure]
**Expected:** [What the AI should now do]
**Pass condition:** [One observable thing that confirms it worked]
```

Append this test case to the eval log entry (Step 5). The test is not auto-run — it's a human-reviewable regression check.

---

## Step 5: Log to Evals

Append to `Work/Evals/evals-log.md` under the current month:

```markdown
## [Mon DD, YYYY] — [6-word-max description]

- **Iterations:** [N]
- **Root cause:** RC-[N] — [one sentence]
- **Prompt:** [what was asked]
- **What went wrong:** [what the AI did]
- **Expected:** [what should have happened]
- **Fix applied:** [file changed + what was changed] | [link if possible]
- **Test:** [label] — `[trigger prompt]` → [expected behavior]
- **Status:** [ ] Untested
```

If the month header doesn't exist yet in `evals-log.md`, create it.

---

## Step 6: Confirm

One-line summary to user:
> "Eval logged. RC-[N]: [root cause]. Fixed in [file]. Test: '[trigger]' → [expected]."

---

## Session Close Mode

Triggered by: "close session", "done for now", "wrapping up", "bye", or any natural conversation end.

**Do this automatically — don't wait to be asked.**

1. Scan the full conversation history for any moment where:
   - User corrected, redirected, or re-explained something
   - There were 2+ attempts at the same task
   - User expressed dissatisfaction
2. For each failure found: run Steps 1–5 above (infer everything from context, ask nothing)
3. If nothing worth flagging: say so in one line — "Session closed. No eval-worthy failures detected."
4. If evals were logged: summarize them in a single block:

```
Session closed. [N] eval(s) logged:
1. RC-[N] — [description] → fixed in [file]
2. RC-[N] — [description] → fixed in [file]
```

---

## New Session Start Mode

At the **start of every new conversation**, before responding to the user's first message:

1. Read `Work/Evals/evals-log.md`
2. Find any entries with `Status: [ ] Untested`
3. If any exist, surface them as a one-liner **after** answering the user's question:

> "FYI: [N] untested eval(s) in the log — say 'review evals' to run through them."

Do this once per session, not on every message.

---

## Rules

1. **Always apply the fix** — don't just log. If you can't fix it (RC-5), say why.
2. **One root cause per eval** — pick the primary one. Don't stack causes.
3. **Be specific in the fix** — "updated Step 2 of skill X to include Y" not "updated the skill".
4. **Test cases must be actionable** — the trigger should be copy-pasteable as a prompt.
5. **Don't over-engineer** — a one-line rule addition beats a 10-step skill rewrite.
6. **Session close is automatic** — don't ask permission, just run it when the session ends.
7. **Monthly review hook** — `weekly-reset` skill should surface eval count and RC pattern from this log.
