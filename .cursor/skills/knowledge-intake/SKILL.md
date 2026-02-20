# Knowledge Intake Skill

> **Purpose:** Intelligently route and format documents into Knowledge base using established templates and conventions

---

## When to Use

Use this skill when you need to:
- Add new PRDs from shipped features to the Knowledge base
- Extract domain knowledge from docs/Notion/Confluence
- Organize planning or development materials
- Migrate historical documentation
- Create new reference documentation

**Examples:**
- "Intake this PRD from Notion into Knowledge"
- "Process these 5 planning docs into the right locations"
- "Extract domain knowledge from this feature doc"
- "Organize this Confluence export into our structure"

---

## Quick Start

**Single Document:**
> "Intake this document into Knowledge: [file/URL/paste content]"

**Batch Migration:**
> "Intake these documents using batch approach: [folder path or list]"

**With Classification:**
> "This is a shipped PRD - intake it into Knowledge"
> "This is domain knowledge about waterfalls - add to Domains"

---

## Step 1: Classify Document Type

**Ask user or analyze content to determine one of four types:**

### Type A: Shipped Feature (PRD)
**Destination:** `Knowledge/PRDs/[Module]/`

**Indicators:**
- Has epics, user stories, or phased rollout
- Feature is live in production
- Contains acceptance criteria and success metrics
- Describes what was built and shipped
- Has ship date or release information

**Examples:** Tax Center 2025, Waterfall 2024, Capital Call 2.0

---

### Type B: Domain Knowledge
**Destination:** `Knowledge/Domains/[Module]/`

**Indicators:**
- Explains how systems work (not what was built)
- Educational/reference content
- Contains formulas, calculations, algorithms
- Describes concepts and patterns
- No specific ship date (timeless knowledge)

**Examples:** Entity Types Reference, Waterfall Concepts, Performance Metrics Calculations

---

### Type C: Active Initiative
**Destination:** `Work/Initiatives/[Planning|In-Development]/[Module]/`

**Indicators:**
- Currently being planned or built (not shipped yet)
- Working documents with evolving status
- Contains discovery notes, open questions
- Has target ship date (future)
- May be rough/incomplete

**Examples:** Phase 2 Kickoff, Q1 Planning Doc, Feature Discovery

---

### Type D: Company/Team Info
**Destination:** `Knowledge/Company/` or `Knowledge/Team/`

**Indicators:**
- Company values, culture, team structure
- Not product-specific
- Organizational documentation

**Examples:** Agora Basics, Team Structure, Company Values

---

## Step 2: Determine Module

**For Types A, B, C - classify into module:**

- **Investment-Management** - Cap table, distributions, waterfalls, transactions, classes, positions
- **Accounting** - Tax services, bookkeeping, financial statements, categorization
- **CRM** - Organizations, contacts, profiles, accounts
- **Fundraising** - Smart forms, digital subscription, offerings
- **Reporting** - Report builder, statements, notices
- **Payments** - ACH, wire, checks, payment methods
- **Portal** - Investor portal, permissions, dashboards
- **Documents** - Document management, templates

**If unclear, ask user:** "Which module does this belong to? [list options]"

---

## Step 3: Apply Template & Format

### Template A: PRDs (Shipped Features)

**Source:** `Knowledge/PRDs/MIGRATION-PROGRESS.md` lines 186-262

**Structure:**
```markdown
# [Feature Name]
## PRD - Shipped [Year]

**Status:** ✅ Fully Shipped / 🔨 Partially Shipped (X epics backlogged)
**Ship Date:** [Month Year]
**Figma:** [Link if available]
**Module:** [Module Name]

---

## Executive Summary

[1-2 paragraphs: What shipped, key capabilities, user impact]

---

## Job To Be Done (JTBD)

[User goal and desired outcome in Jobs-to-be-Done format]

---

## Background & Motivation

[Why we built this, problems it solves, context]

---

## Phased Rollout / Epic Breakdown

### Epic #1 – [Name]
**Goal:** [What this epic achieves]

**Key Features:**
- Feature A: [Brief description]
- Feature B: [Brief description]

**Acceptance Criteria:**
- [ ] Criterion 1
- [ ] Criterion 2

[Repeat for each epic]

---

## Technical Implementation

**Data Model:**
[Key objects, fields, relationships]

**Integration Points:**
[External systems, APIs, dependencies]

**Technical Decisions:**
[Key architectural choices and rationale]

---

## User Research & Validation

**Interviews:**
[Customer interviews conducted, key insights]

**Testing:**
[Beta testing, user feedback, iterations]

---

## Success Metrics

**Mixpanel Events:**
- Event 1: [What it tracks]
- Event 2: [What it tracks]

**KPIs:**
- Metric 1: [Target]
- Metric 2: [Target]

---

## Assumptions

[Key assumptions made during development]

---

## Open Questions (Resolved)

[Questions that were answered during work]

---

## Related Documentation

- **Domain Knowledge:** [Link to Domains doc if applicable]
- **Related PRDs:** [Links to related features]
- **Technical Docs:** [Links to architecture docs]

---

**PRD Status:** Shipped  
**Last Updated:** [Date]
```

**Formatting Guidelines:**
- **Condense:** Aim for 30-50% reduction from source material
- **Keep all epics:** Document each epic even if brief
- **Preserve acceptance criteria:** Keep key AC for critical features
- **Remove:** Duplicate sections, excessive screenshots (note them but don't reproduce)
- **Add metadata:** Status, ship date, module clearly marked at top
- **Target size:** 400-600 lines

**Check for Domain Content:**
While processing PRD, look for:
- Educational sections explaining concepts
- Formulas or calculation logic
- System architecture explanations
- "How it works" content vs "What we built" content

**If found:** Extract to separate Domain doc (see Template B)

---

### Template B: Domain Docs (Educational Content)

**Source:** Extracted from shipped PRDs or standalone reference docs

**Structure:**
```markdown
# [Topic Name]

> **Module:** [Module Name]  
> **Last Updated:** [Date]  
> **Related PRDs:** [Links to PRDs that use these concepts]

---

## Overview

[Brief introduction: What this document covers and why it matters]

---

## Core Concepts

[Fundamental concepts, terminology, definitions]

### Concept 1: [Name]
[Explanation with context]

### Concept 2: [Name]
[Explanation with context]

---

## Calculation Methods / Formulas

[Detailed mathematical or algorithmic explanations]

### Method 1: [Name]
**Formula:**
```
[Mathematical notation or pseudocode]
```

**Explanation:**
[Step-by-step breakdown]

**Example:**
[Concrete example with numbers]

---

## System Architecture / How It Works

[Technical deep dive on how the system implements these concepts]

**Data Flow:**
[How data moves through the system]

**Key Objects:**
[Important data structures and their roles]

---

## Edge Cases & Constraints

[Important limitations, special cases, gotchas]

- Edge case 1: [Description and handling]
- Edge case 2: [Description and handling]

---

## Common Patterns

[Typical use cases, standard approaches]

### Pattern 1: [Name]
**When to use:** [Scenario]
**How it works:** [Explanation]
**Example:** [Real-world example]

---

## Technical Details

[Implementation specifics, algorithms, data structures]

---

## Examples

[Real-world scenarios with step-by-step walkthroughs]

### Example 1: [Scenario]
**Setup:** [Initial conditions]
**Process:** [Step-by-step]
**Result:** [Outcome]

---

## Related Documentation

- **PRDs:** [Features that implement these concepts]
- **Other Domains:** [Related domain knowledge]

---

**Last Updated:** [Date]
```

**Formatting Guidelines:**
- **Expand:** Add detail, examples, context (600-1000+ lines)
- **Educational focus:** Teach concepts, not just document features
- **Include formulas:** Use mathematical notation where applicable
- **Real examples:** Use anonymized real-world scenarios
- **Deep dive:** Go deeper than PRD - explain the "why" and "how"

---

### Template C: Initiatives (Active Work)

**Location:** `Work/Initiatives/[Planning|In-Development]/[Module]/`

**Structure:**
```markdown
# [Initiative Name]

**Status:** 🎯 Planning / 🚧 In Development  
**Start Date:** [Date]  
**Target Ship:** [Q or Month]  
**Owner:** [PM Name]  
**Squad:** [Engineering Squad if assigned]

---

## Problem Statement

[What problem are we solving? For whom?]

---

## Goals & Success Criteria

**Goals:**
1. Goal 1: [Specific, measurable]
2. Goal 2: [Specific, measurable]

**Success Metrics:**
- Metric 1: [How we'll measure success]
- Metric 2: [How we'll measure success]

---

## Discovery Notes

**User Research:**
[Interviews, surveys, findings]

**Competitive Analysis:**
[What others are doing, gaps, opportunities]

**Technical Research:**
[Feasibility, constraints, dependencies]

---

## Proposed Solution

[High-level approach, key features, user flows]

**Core Features:**
1. Feature 1: [Brief description]
2. Feature 2: [Brief description]

**Out of Scope (for now):**
- Item 1
- Item 2

---

## Open Questions

- [ ] Question 1: [What we need to figure out]
- [ ] Question 2: [What we need to figure out]

---

## Dependencies & Risks

**Dependencies:**
- Dependency 1: [What we need first]
- Dependency 2: [What we need first]

**Risks:**
- Risk 1: [Potential blocker and mitigation]
- Risk 2: [Potential blocker and mitigation]

---

## Next Steps

- [ ] Action 1: [Who, when]
- [ ] Action 2: [Who, when]

---

## Notes & Links

[Meeting notes, Figma links, research docs, etc.]

**Figma:** [Link]  
**Miro Board:** [Link]  
**Related Docs:** [Links]

---

**Last Updated:** [Date]
```

**Formatting Guidelines:**
- **Flexible format:** Working docs can be messy during active work
- **Status-driven:** Clear status markers (Planning vs In-Development)
- **Living document:** Expected to evolve and change
- **Action-oriented:** Focus on next steps and decisions needed

---

## Step 4: File Naming Convention

**PRDs:**
- Format: `[Feature-Name]-[ShipYear].md`
- Examples:
  - `Waterfall-2024.md`
  - `Tax-Center-2025.md`
  - `Capital-Call-2.0-2024.md`

**Domain Docs:**
- Format: `[Topic]-[Type].md`
- Types: `-Reference`, `-Architecture`, `-Calculations`, `-Concepts`
- Examples:
  - `Entity-Types-Reference.md`
  - `Cap-Table-Architecture.md`
  - `Performance-Metrics-Calculations.md`
  - `Waterfall-Concepts.md`

**Initiatives:**
- Format: `[Initiative-Name].md` (or numbered if multi-doc)
- Examples:
  - `Phase-2-Kickoff-Feb-2026.md`
  - `Q1-CRM-Redesign.md`
  - `01-Discovery.md`, `02-Solution-Design.md` (for multi-doc initiatives)

---

## Step 5: Update Index Files

**After creating PRD:**
1. Add entry to `Knowledge/PRDs/INDEX.md` in appropriate module section
2. If batch migration: Update `Knowledge/PRDs/MIGRATION-PROGRESS.md`
3. Add link from related Domain docs if applicable

**After creating Domain doc:**
1. Add entry to `Knowledge/Domains/INDEX.md`
2. Link from related PRDs in "Related Documentation" section
3. Update Domain module README if significant addition

**After creating Initiative:**
1. Update folder README if exists
2. Link from Domain docs if applicable (in "Active Initiatives" section)

---

## Batch Mode (5+ Documents)

**When processing multiple documents:**

1. **Create/Update Checkpoint File:**
   - Location: `Knowledge/PRDs/MIGRATION-PROGRESS.md` (if PRDs)
   - Or: `[Target Folder]/BATCH-INTAKE-[Date].md`

2. **Track Each Document:**
   ```markdown
   | Source | Destination | Type | Status | Notes |
   |--------|-------------|------|--------|-------|
   | doc1.md | PRDs/IM/Feature.md | PRD | ✅ Done | Split to Domain |
   | doc2.md | Domains/IM/Topic.md | Domain | ✅ Done | - |
   ```

3. **Work in Batches:** Process 3-5 documents at a time

4. **Update Checkpoint:** After each batch, update progress

5. **Enable Continuation:** Structure allows fresh context window pickup

**See:** `.cursor/skills/batch-migration/SKILL.md` for detailed batch approach

---

## Quality Checks

Before finalizing, verify:

- [ ] **Correct folder location** (PRDs/Domains/Initiatives)
- [ ] **Proper module classification** (IM/Accounting/CRM/etc)
- [ ] **File naming convention** followed
- [ ] **Metadata complete** (status, date, module)
- [ ] **Links to related docs** added
- [ ] **Index files updated** (INDEX.md, MIGRATION-PROGRESS.md)
- [ ] **Educational content extracted** if PRD with domain knowledge
- [ ] **Formatting consistent** with template
- [ ] **Target length appropriate** (PRD: 400-600 lines, Domain: 600-1000+ lines)

---

## Decision Tree Summary

```
START: New document to intake
  ↓
Is it shipped? (has ship date, live in production)
  ├─ YES → PRD Template
  │   └─ Contains educational content?
  │       ├─ YES → Split: PRD + Domain doc
  │       └─ NO → PRD only
  │
  └─ NO → Is it conceptual/educational? (formulas, how-to)
      ├─ YES → Domain doc
      │
      └─ NO → Is it active work? (planning/building)
          ├─ YES → Initiative (Planning or In-Development)
          └─ NO → Company/Team info
```

---

## Examples

### Example 1: Shipped PRD with Domain Content
**Input:** "Intake the Waterfall PRD from Notion export"

**Process:**
1. Classify: Type A (Shipped Feature) + has educational content
2. Module: Investment-Management
3. Split content:
   - PRD: Epics, user stories, what shipped
   - Domain: Waterfall logic, tier concepts, Lior's Academy
4. Create:
   - `Knowledge/PRDs/Investment-Management/Waterfall-2024.md` (action-focused, 500 lines)
   - `Knowledge/Domains/Investment-Management/Waterfall-Concepts.md` (educational, 873 lines)
5. Update: PRDs/INDEX.md, Domains/INDEX.md, link between them

---

### Example 2: Pure Domain Reference
**Input:** "Intake entity types documentation"

**Process:**
1. Classify: Type B (Domain Knowledge)
2. Module: Investment-Management
3. Apply Template B
4. Create: `Knowledge/Domains/Investment-Management/Entity-Types-Reference.md`
5. Update: Domains/INDEX.md

---

### Example 3: Planning Initiative
**Input:** "Intake Q1 planning doc for CRM redesign"

**Process:**
1. Classify: Type C (Active Initiative - Planning)
2. Module: CRM
3. Apply Template C
4. Create: `Work/Initiatives/Planning/CRM/Q1-Redesign-Planning.md`
5. Update: Folder README (if exists)

---

### Example 4: Batch Migration
**Input:** "Intake these 10 PRDs from Notion export"

**Process:**
1. Use batch mode
2. Create/update checkpoint: `Knowledge/PRDs/MIGRATION-PROGRESS.md`
3. Process in batches of 3-5
4. Track progress in checkpoint
5. Update all index files at end

---

## Integration with Existing Skills

**Works with:**
- **batch-migration** - Use for large intake projects
- **task-add** - Create tasks for follow-up work
- **jira-audit** - Cross-reference with shipped features

**References:**
- `Knowledge/REORGANIZATION-SUMMARY.md` - Overall structure
- `Knowledge/PRDs/MIGRATION-PROGRESS.md` - Template reference
- `Knowledge/PRDs/INDEX.md` - PRD catalog
- `Knowledge/Domains/INDEX.md` - Domain catalog

---

## Common Scenarios

**"I have a Notion export with 50 PRDs"**
→ Use batch mode, create MIGRATION-PROGRESS.md checkpoint

**"I want to document this shipped feature"**
→ Single PRD intake, check for domain content to extract

**"I need to organize these planning docs"**
→ Route to Work/Initiatives/Planning/[Module]/

**"I found some great educational content about IRR calculations"**
→ Create Domain doc in Domains/Investment-Management/

**"We just shipped a feature and I have the PRD"**
→ Check if already in Knowledge, if not: intake as PRD, extract domain knowledge

---

## Tips for Success

1. **Always classify first** - Don't skip the decision tree
2. **Check for duplicates** - Search Knowledge before creating
3. **Extract domain knowledge** - Don't leave educational content buried in PRDs
4. **Link liberally** - Connect related docs
5. **Update indexes** - Keep catalogs current
6. **Use batch mode** - For 5+ documents, checkpoint approach saves time
7. **Ask when unclear** - Better to ask user than guess wrong location

---

**Skill Version:** 1.0  
**Created:** Feb 14, 2026  
**Last Updated:** Feb 14, 2026
