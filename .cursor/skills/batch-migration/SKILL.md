# Batch Migration Skill

> **Purpose:** Handle large-scale content migration/reorganization across multiple context windows using checkpoint-based approach.

---

## When to Use This Skill

Use this skill when you need to:
- Migrate 10+ documents/PRDs/files
- Reorganize large knowledge bases
- Process content that will span multiple conversations
- Maintain consistency across a long-running task
- Track progress on multi-session work

**Examples:**
- Migrating 50 PRDs from Notion to structured Knowledge base
- Consolidating 100+ meeting notes into organized summaries
- Extracting domain knowledge from multiple unstructured sources
- Batch processing documentation for consistency

---

## Core Concept: Checkpoint-Driven Continuation

**The Problem:**
- AI context windows have limits (typically 200K-1M tokens)
- Large migrations exceed single conversation capacity
- Manual handoff between sessions loses context and consistency

**The Solution:**
- Create a **checkpoint file** that acts as "save state"
- Document progress, template, and next steps
- Enable seamless continuation in fresh context windows

---

## How It Works

### Phase 1: Setup (First Session)

**Step 1: Create Checkpoint File**
- Location: `[Project Root]/MIGRATION-PROGRESS.md` or `[Target Folder]/MIGRATION-PROGRESS.md`
- Purpose: Single source of truth for all progress

**Step 2: Document Structure**
The checkpoint file must contain:

```markdown
# [Migration Name] Progress Tracker

## ✅ Completed Items (X of Y)
[Table or list of what's done with links]

## 📋 Queued Items - Priority Order
### Batch 1: [Category]
- [ ] Item A (source → destination)
- [ ] Item B (source → destination)

### Batch 2: [Category]
[Continue...]

## 📐 Template Structure
[Document the format/structure to follow]

## 🔄 Continuation Instructions
[Explicit steps for resuming in new context]

## 🗂️ File Mapping Log
[Track each completed migration]

## 📊 Overall Progress
[High-level metrics]
```

**Step 3: Process First Batch**
- Tackle 1-3 items in first session
- Prove the template works
- Update checkpoint after completion

### Phase 2: Continuation (Subsequent Sessions)

**User Says:**
> "Continue [migration name] from [CHECKPOINT-FILE-PATH]. Process Batch [N]."

**AI Does:**
1. Reads checkpoint file
2. Identifies next batch to process
3. Follows documented template
4. Processes batch items
5. Updates checkpoint with progress
6. Updates any index/master files

**Repeat until complete.**

---

## Checkpoint File Requirements

### Must Include:

**1. Completed Work Log**
- What's been processed
- Links to output files
- Date completed
- Any important notes

**2. Queued Work (Organized)**
- Batches (3-5 items per batch)
- Priority order
- Source file paths
- Destination paths
- Status indicators

**3. Template/Structure**
- Proven format from completed items
- Formatting guidelines
- What to keep vs. remove
- Metadata requirements

**4. Continuation Instructions**
- Exact phrase to resume work
- What AI should do next
- Expected output

**5. File Mapping**
- Source → Destination tracking
- Transformation notes
- Edge cases handled

**6. Progress Metrics**
- X of Y completed
- Estimated remaining work

---

## Best Practices

### Batch Sizing
- **Small batches (1-3 items):** For complex transformations
- **Medium batches (3-5 items):** For standard migrations
- **Large batches (5-10 items):** For simple copy/move operations

### Context Management
- Monitor token usage during session
- Stop before hitting 80% capacity
- Update checkpoint before ending session

### Quality Control
- Process 1-2 items first to validate template
- Review before batch processing
- Keep formatting consistent

### Organization
- Group batches by category/module
- Prioritize high-value items first
- Mark items that can be skipped

---

## Example: PRD Migration

**Scenario:** Migrate 50 PRDs from Notion export to Knowledge base

**Checkpoint File:** `Knowledge/PRDs/MIGRATION-PROGRESS.md`

**Batch Strategy:**
- Batch 1: 2 core PRDs (prove template)
- Batch 2: 3-4 related PRDs (same module)
- Batch 3: 3-4 different module
- Continue until complete

**Template Defined:**
- PRD structure (Executive Summary → JTBD → Epics → Technical → Metrics)
- Metadata requirements (Status, Ship Date, Module)
- Condensation rules (30-50% size reduction)
- What to preserve (all epics, key AC, metrics)

**Result:**
- Consistent format across all 50 PRDs
- Seamless continuation across 5-10 sessions
- No lost context or duplicate work

---

## Example: Meeting Notes Consolidation

**Scenario:** Consolidate 100+ weekly meeting notes into quarterly summaries

**Checkpoint File:** `Work/Meetings/CONSOLIDATION-PROGRESS.md`

**Batch Strategy:**
- Batch 1: Q1 2025 (10-15 notes)
- Batch 2: Q2 2025 (10-15 notes)
- Continue by quarter

**Template Defined:**
- Summary structure (Key Decisions → Action Items → Blockers)
- Date range format
- What to extract vs. skip

---

## Troubleshooting

**Problem:** Lost track of where we stopped
→ **Solution:** Check File Mapping Log for last completed item

**Problem:** Template not working well
→ **Solution:** Update template in checkpoint, reprocess last batch

**Problem:** Context window filled up mid-batch
→ **Solution:** Update checkpoint with partial progress, resume in new session

**Problem:** Inconsistent output across batches
→ **Solution:** Review first 2 completed items, refine template, consider reprocessing

---

## Anti-Patterns (Don't Do This)

❌ **Starting migration without checkpoint**
→ ✅ Always create checkpoint first

❌ **Processing too many items in one session**
→ ✅ Batch conservatively, stop before context fills

❌ **Vague continuation instructions**
→ ✅ Write explicit "say this to resume" instructions

❌ **Not updating checkpoint after each batch**
→ ✅ Update immediately after completion

❌ **Skipping template validation**
→ ✅ Process 1-2 items first, validate, then batch

---

## Skill Invocation

**To use this skill, say:**

> "Use batch-migration skill to [migrate/reorganize/consolidate] [source] to [destination]."

**AI will:**
1. Ask for source location and destination structure
2. Propose batching strategy
3. Create checkpoint file
4. Process first batch
5. Provide continuation instructions

**To resume work, say:**

> "Continue [migration name] from [checkpoint file]. Process Batch [N]."

---

## Related Skills

- **Create-Rule:** For codifying patterns discovered during migration
- **Create-Skill:** For turning migration insights into reusable skills

---

**Skill Version:** 1.0  
**Created:** Feb 13, 2026  
**Validated:** PRD migration (50+ documents), proven across context windows
