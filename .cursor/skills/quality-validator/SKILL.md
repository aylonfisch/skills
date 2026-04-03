---
name: quality-validator
description: Generic planner + sub-agent quality validation framework. A planner agent reads any source artifact (PRD, spec, brief, initiative doc), decomposes it into validation units, spawns parallel sub-agents to check each unit against existing outputs, and synthesizes a QUALITY-REPORT.md. Works for PRD→prototype alignment, PRD→Jira tickets, spec→implementation, brief→doc coverage, or any task where "did we actually cover all of it?" requires reading many files at once. Triggers: "validate [X] against [Y]", "quality check", "audit prototypes", "does [output] cover [spec]", "sync prototypes", "prototype audit", /quality-validator.
---

# Quality Validator — Planner + Sub-Agent Framework

A reusable pattern that validates any artifact against any set of outputs using parallel sub-agents overseen by a planner.

## When to Use

- PRD → prototype alignment (are all epics covered?)
- PRD → Jira tickets (does every user story have a ticket?)
- Spec → implementation files (is everything built?)
- Initiative doc → action items (are all decisions tracked?)
- Design brief → prototype fidelity (does the prototype match the brief?)
- Any high-context quality check where one agent would run out of context

## Trigger Phrases

`"validate [X] against [Y]"` · `"quality check"` · `"audit prototypes"` · `"sync prototypes"` · `"does [output] cover [spec]"` · `/quality-validator`

---

## Step-by-Step — Planner Instructions

### Step 0: Incorporate Decisions (optional — run before everything else if decisions are provided)

If the user provides a **decisions list** — changes, corrections, or new direction from a conversation, meeting, or session — apply them to the source artifact before running any validation.

**Inputs accepted:**
- **Decisions** — bullet list of decisions/changes to apply to the source artifact

**How to run:**
1. Read the current source artifact in full
2. For each decision: identify the affected section(s), apply the change precisely
3. Append to the artifact's header: `Last Updated: [date]`
4. Append a `## Change Log` section at the bottom of the artifact:
   ```markdown
   ## Change Log
   ### [date] — quality-validator decision pass
   - [decision applied + which section changed]
   - [decision applied + which section changed]
   ```
5. Save the updated artifact
6. Continue to Step 1 using the updated artifact as the source

**Decision input format:**
```
Decisions:
- [change description] → affects [section or epic]
- [change description] → affects [section or epic]
```

If no decisions are provided, skip Step 0 and proceed directly to Step 1.

---

### Step 1: Identify Inputs

Collect from the user (ask if not provided):
- **Source artifact** — the thing to validate against (PRD, spec, brief, etc.)
- **Output type** — what we're checking (HTML prototypes, Jira tickets, implementation files, docs)
- **Output location** — folder or Jira project where outputs live
- **Mode** — `audit` (gap report only) or `build` (audit + create/patch missing outputs)
- **Decisions** *(optional)* — list of changes to apply to the source artifact before validation (triggers Step 0)

If the user says "validate [file] against [folder]" with no mode, default to `build`.

---

### Step 2: Planner — Read + Decompose

Read the source artifact in full. Extract every **validation unit** — the discrete chunk of the artifact that should map to one output. What counts as a unit depends on artifact type:

| Artifact Type | Validation Unit |
|---|---|
| PRD | Epic (each has a title, JTBD, and acceptance criteria list) |
| Spec / requirements doc | Named requirement or feature section |
| Initiative doc | Goal or deliverable |
| Design brief | Design principle or screen/flow |
| User story doc | Individual user story |

For each unit, produce a structured record:
```
{
  id: "E1",
  title: "BK Client Hub",
  jtbd: "Know exactly where every client stands without leaving the system",
  criteria: ["criterion 1", "criterion 2", ...]
}
```

---

### Step 3: Planner — Map Units to Outputs

Scan the output location. For each output file found, infer which validation unit it covers (by filename, title, or content). Produce a mapping:

```
E1 → BK-ClientHub-E1-Prototype.html  (exists)
E2 → BK-DocRequests-E2-Prototype.html (exists)
E3 → NONE (missing)
E4 → NONE (missing)
E5 → BK-Onboarding-Questionnaire-Collection-Prototype.html (exists)
```

---

### Step 4: Launch Sub-Agents (Parallel)

Launch one `Task` sub-agent per validation unit using `subagent_type: explore`, `model: fast`. Each sub-agent receives:

**Sub-agent prompt template:**
```
You are validating one unit of a source artifact against an existing output (or confirming it is missing).

SOURCE UNIT:
ID: [id]
Title: [title]
JTBD: [jtbd]
Acceptance Criteria:
[numbered list of criteria]

OUTPUT FILE: [path to file, or "NONE — this unit has no output yet"]

YOUR TASK:
1. If output file exists: Read it. For each acceptance criterion, determine if the prototype/output covers it. Mark each criterion as: COVERED, PARTIAL, or MISSING.
2. If output file is NONE: All criteria are MISSING.

Return a structured result:
{
  "unit_id": "[id]",
  "unit_title": "[title]",
  "output_file": "[filename or NONE]",
  "verdict": "aligned | partial | missing",
  "covered": ["criterion text", ...],
  "partial": ["criterion text — what's there and what's missing", ...],
  "gaps": ["criterion text", ...],
  "action": "none | patch | build"
}

Verdict rules:
- aligned: all criteria covered
- partial: some covered, some not
- missing: output file is NONE or nearly nothing covered

Action rules:
- none: verdict is aligned
- patch: verdict is partial — output exists but needs additions
- build: verdict is missing — output needs to be created from scratch
```

Collect all sub-agent results before moving to Step 5.

---

### Step 5: Synthesize + Write Report

Write `QUALITY-REPORT.md` to the output location folder.

**Report template:**
```markdown
# Quality Report — [Artifact Name]

**Run:** [date]
**Mode:** [audit | build]
**Source:** [path to artifact]
**Output location:** [path]

---

## Summary

| Unit | Title | Output File | Verdict | Gaps |
|------|-------|-------------|---------|------|
| E1   | ...   | filename    | ✅ aligned | 0 |
| E2   | ...   | filename    | ⚠️ partial | 2 |
| E3   | ...   | NONE        | ❌ missing | 5 |

**Total units:** N  |  **Aligned:** X  |  **Partial:** Y  |  **Missing:** Z

---

## Gap Details

### [Unit ID] — [Title] (verdict)
**Output:** [filename or NONE]

**Covered:**
- criterion

**Partial:**
- criterion — _present but incomplete: [what's there vs missing]_

**Gaps (missing entirely):**
- criterion

---

## Actions Taken

[In build mode — list any files created or patched with one-line description of what was added.]
[In audit mode — "No files modified. Review gaps above and run in build mode to create missing outputs."]
```

---

### Step 6: Build or Patch (Build Mode Only)

For every unit with `action: build` or `action: patch`:

1. Read the relevant skill for the output type (e.g., `prototype-feature` for HTML prototypes — skill is at `.cursor/skills/prototype-feature/SKILL.md`)
2. Launch a build sub-agent per unit, providing:
   - The full unit spec (JTBD + all acceptance criteria)
   - The existing output file content (for patches), or "new file" (for builds)
   - The output type skill instructions
   - Required file path and naming convention
3. The build sub-agent creates or updates the file
4. Add built/patched files to the Actions Taken section of the report

---

## Output Files

| File | Location | Notes |
|---|---|---|
| `QUALITY-REPORT.md` | Same folder as outputs | Always created, even in audit mode |
| New output files | Output location folder | Only in build mode, for `missing` units |
| Patched output files | Output location folder | Only in build mode, for `partial` units |

---

## Example Invocations

**PRD → Prototypes with decisions (full pipeline, build mode):**
```
/quality-validator
Source: BK-Onboarding-PRD.md
Output type: HTML prototypes
Output location: prototypes/
Mode: build
Decisions:
- E1 reframed: owns the 22 entity fields + 3 client fields directly
- Epic sequence changed: E1 (questions) → E2 (doc hub) → E3 (requests + aggregation)
- E4 removed as standalone epic — status tracking is a running AC on each epic
- E5 reframed: guided UX wizard over E1+E2, owns no new data
- E3 gains: chat uploads route to hub automatically (entity known, category = uncategorized)
```

**PRD → Prototypes (build mode, no decisions):**
> "validate BK-Onboarding-PRD.md against the prototypes folder, build mode"

**PRD → Jira (audit mode):**
> "audit whether the Jira tickets cover the BK Client Hub PRD, audit only"

**Initiative doc → Action items:**
> "quality check — does ACTION-ITEMS.md cover everything in the BK Onboarding Initiative doc?"

---

## Integration

- **prototype-feature** — used by build sub-agents when output type is HTML prototype
- **write-prd** — source artifacts are often PRDs generated by this skill
- **jira-audit** — complementary: jira-audit checks ticket quality; quality-validator checks coverage

---

**Skill Version:** 1.1
**Created:** March 24, 2026
**Updated:** March 24, 2026 — Step 0 (Incorporate Decisions) added; full pipeline now: decisions → updated artifact → audit → build
