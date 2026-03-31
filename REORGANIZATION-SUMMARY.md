# Knowledge Base Reorganization - Complete
**Date:** February 13, 2026

---

## ✅ What We Built

### 1. New Folder Structure

```
Knowledge/
├── Company/               [Existing - kept as-is]
│   ├── Agora-basics.md
│   └── ...
├── Methodologies/         [Existing - kept as-is]
│   └── Skills/
├── Sources/               [NEW - Raw archive, do not edit]
│   ├── competitora/       [401 files — Notion exports, Help Center PDFs, blog posts]
│   └── Suzy PRDs/         [620 files — Notion PRD exports, Migrated + Not-Migrated]
├── Domains/               [NEW - Stable domain knowledge]
│   ├── Investment-Management/
│   │   ├── README.md
│   │   ├── Entity-Types-Reference.md
│   │   ├── Cap-Table-Architecture.md
│   │   ├── Ownership-Calculation-Methods.md
│   │   ├── Performance-Metrics-Calculations.md
│   │   └── Waterfall-Concepts.md
│   └── Accounting/
│       ├── README.md
│       └── Accounting-knowledge.md
├── Competitors/           [NEW - Competitive intelligence]
│   ├── README.md                    [Master index + feature matrix]
│   ├── MIGRATION-PROGRESS.md        [Batch migration checkpoint]
│   ├── Juniper-Square/
│   │   ├── Profile.md              [Deep-dive — ✅ Complete]
│   │   └── Updates.md              [Release log]
│   ├── AppFolio/
│   │   ├── Profile.md
│   │   └── Updates.md
│   ├── CashFlow-Portal/
│   │   ├── Profile.md
│   │   └── Updates.md
│   ├── InvestNext/
│   │   ├── Profile.md
│   │   └── Updates.md
│   ├── IMS-RealPage/
│   │   ├── Profile.md
│   │   └── Updates.md
│   ├── Secondary/                   [Lightweight profiles]
│   │   ├── SponsorCloud.md
│   │   ├── InvestorFlow.md
│   │   ├── Covercy.md
│   │   ├── AllVue.md
│   │   ├── PlatformEleven.md
│   │   ├── Yardi-IM.md
│   │   └── Maybern.md
│   └── Cross-Competitor/
│       ├── Feature-Gap-Analysis.md  [Where competitors beat us]
│       ├── Agora-Advantages.md      [Where we beat them]
│       └── Positioning-Map.md       [Market positioning grid]
└── PRDs/                  [NEW - Shipped feature archive]
    ├── INDEX.md
    ├── MIGRATION-PROGRESS.md
    ├── Accounting/
    │   ├── Tax-Center-2025.md
    │   └── Accounting-Phase1-Categorization-Nov2025.md
    └── Investment-Management/
        └── [15 migrated PRDs]

Work/
├── Initiatives/           [Reorganized]
│   ├── Planning/          [NEW - Pre-development initiatives]
│   │   ├── IM/
│   │   │   ├── Org Chart/          [7 files - moved from old location]
│   │   │   └── waterfall/
│   │   └── Accounting/
│   │       ├── PQL/                [3 files - moved]
│   │       ├── Accounting dashboard/
│   │       └── Fin ops/
│   └── In-Development/    [NEW - Active development]
│       └── Accounting/
│           └── Phase-2-Kickoff-Feb-2026.md
├── Ongoing/               [Existing - kept as-is]
│   ├── Templates/
│   └── Meetings/
└── TASKS.md               [Existing - kept as-is]
```

---

## 📚 New Knowledge Base Files Created

### Domain Knowledge (Reference Docs)

**Investment Management Domain:**
- `Knowledge/Domains/Investment-Management/README.md`
  - Module overview, core objects, data relationships
  - Links to active initiatives and related domains
  
- `Knowledge/Domains/Investment-Management/Entity-Types-Reference.md`
  - Comprehensive guide to legal structures (LLC, LP, C-Corp, S.A., Ltda, etc.)
  - Functional roles (Master Fund, Feeder, Asset SPV, Blocker, etc.)
  - Capital stack positions (Senior/Mezz/Preferred/Common)
  - Common fund structure patterns
  - Quick reference for tax treatment and behavioral patterns

- `Knowledge/Domains/Investment-Management/Cap-Table-Architecture.md`
  - Cap table calculation methods and ownership models
  - Class-based management and position tracking

- `Knowledge/Domains/Investment-Management/Ownership-Calculation-Methods.md`
  - 4 ownership calculation types: %, Commitment, Contribution, Unit-based
  - Lot accounting and FIFO/LIFO concepts

- `Knowledge/Domains/Investment-Management/Performance-Metrics-Calculations.md`
  - IRR, DPI, RVPI, TVPI, Yield calculation formulas and examples

- `Knowledge/Domains/Investment-Management/Waterfall-Concepts.md`
  - Waterfall distribution logic and tier structures
  - "Lior's Academy" educational content

**Accounting Domain:**
- `Knowledge/Domains/Accounting/README.md`
  - Product philosophy, Tax Services overview
  - Bookkeeping dual-interface architecture
  - Phase 1 shipped, Phase 2 in development
  - Integration points (QBO, entity data)
  - Target users and active initiatives

- `Knowledge/Domains/Accounting/Accounting-knowledge.md`
  - Tax Services workflow (5 phases)
  - Bookkeeping Services architecture
  - 28-category taxonomy
  - Dual-platform architecture (Back Office + ACP)

### Competitive Intelligence (New — Feb 20, 2026)

**Structure:** `Knowledge/Competitors/`

**Primary Competitors (full Profile.md + Updates.md):**
- `Juniper-Square/Profile.md` ✅ — Company snapshot, strategy, product deep-dive by module, packaging/pricing, battle card, sources
- `AppFolio/Profile.md` — Migration pending
- `CashFlow-Portal/Profile.md` — Migration pending
- `InvestNext/Profile.md` — Migration pending
- `IMS-RealPage/Profile.md` — Migration pending

**Secondary Competitors (lightweight single-file profiles):**
- SponsorCloud, InvestorFlow, Covercy, AllVue, PlatformEleven, Yardi IM, Maybern

**Cross-Competitor Analysis:**
- `Feature-Gap-Analysis.md` — 242-row feature comparison (where competitors beat us)
- `Agora-Advantages.md` — 94 Agora-unique features mapped against competitors
- `Positioning-Map.md` — SMB vs Enterprise, Tech-led vs Service-led market grid

**Raw Sources:** `Knowledge/Sources/competitora/` (401 files — Notion exports, Help Center PDFs, blog posts). Referenced in each Profile.md "Sources" section but not migrated — stays as raw archive.

**Migration:** Tracked in `Knowledge/Competitors/MIGRATION-PROGRESS.md` (10 batches, checkpoint-driven). Resume with: *"Continue competitor migration from `Knowledge/Competitors/MIGRATION-PROGRESS.md`. Process Batch N."*

**Maintenance:** A `competitor-update` skill will be built to periodically web-search for new releases and draft entries into each competitor's `Updates.md`. Design decisions captured:
- Standalone skill (not baked into task-weekly)
- Scans all primary competitors by default, option to pick one
- Drafts updates to review file first (not directly into Updates.md)

---

### PRD Archive (Shipped Features)

- `Knowledge/PRDs/INDEX.md`
  - Master tracking list for all shipped PRDs
  - Guidelines for creating new PRDs
  - Links to in-development and planning initiatives
  - Roadmap for extracting historical PRDs

- `Knowledge/PRDs/Accounting-Phase1-Categorization-Nov2025.md`
  - Complete PRD for shipped Bookkeeping Phase 1
  - Epics 0-6, 28-category taxonomy
  - Dual-interface architecture documentation
  - Technical integration details (QB API)
  - Key learnings and success metrics

---

## 🗂️ File Reorganization

### Moved to Planning/
- `IM/Org Chart/` → `Work/Initiatives/Planning/IM/Org Chart/` (7 files)
- `Accounting/PQL/` → `Work/Initiatives/Planning/Accounting/PQL/` (3 files)
- `IM/waterfall/` → `Work/Initiatives/Planning/IM/waterfall/`
- `Accounting/Accounting dashboard/` → `Work/Initiatives/Planning/Accounting/`
- `Accounting/Fin ops/` → `Work/Initiatives/Planning/Accounting/`

### Moved to In-Development/
- `Accounting/Phase-2-Kickoff-Feb-2026.md` → `Work/Initiatives/In-Development/Accounting/`

### Kept in Place
- `Work/Ongoing/Templates/` - Jira templates
- `Work/Ongoing/Meetings/` - Meeting notes
- `Work/TASKS.md` - Task management
- `Knowledge/Company/` - Company docs
- `Knowledge/Methodologies/` - PM methodologies

---

## 📖 New Content Library

**What's Now Documented:**

### Investment Management
- ✅ Entity data model and core objects
- ✅ Entity types reference (legal structures + functional roles)
- ✅ Common fund structure patterns
- ✅ Tax treatment quick reference
- ✅ Current system limitations

### Accounting
- ✅ Product philosophy and strategy
- ✅ Tax Services workflow (mature product)
- ✅ Bookkeeping Phase 1 complete PRD
- ✅ Dual-interface architecture ("Two Brains")
- ✅ 28-category taxonomy
- ✅ QuickBooks integration logic
- ✅ Phase 2 scope and in-development status

---

## 🎯 Next Steps: Expanding the Knowledge Base

### High Priority - Competitor Knowledge Base (In Progress)

- [x] Create `Knowledge/Competitors/` structure and migration checkpoint
- [x] Complete Juniper Square profile (Batch 1 — template proven)
- [ ] Complete AppFolio profile (Batch 2)
- [ ] Complete CashFlow Portal profile (Batch 3)
- [ ] Complete InvestNext profile (Batch 4)
- [ ] Complete IMS RealPage profile (Batch 5)
- [ ] Complete secondary competitor profiles (Batches 6-8)
- [ ] Build cross-competitor analysis assets (Batch 9)
- [ ] Create README index, cleanup Agora-basics.md (Batch 10)
- [ ] Build `competitor-update` skill

### High Priority - Extract from Shipped Features

**Investment Management:**
- [ ] Extract entity data model details from Org Chart planning docs
- [ ] Document fund structure patterns (from 05-Common-Use-Cases)
- [ ] Create Parameter Categories reference (from 03-Parameter-Categories)

**Accounting:**
- [ ] Create `Tax-Services-Deep-Dive.md` from existing Accounting-knowledge.md
- [ ] Create `Bookkeeping-Architecture.md` (dual-interface patterns)
- [ ] Create `QBO-Integration-Logic.md` (Chart of Accounts mapping, transaction flow)
- [ ] PRD: Tax Services (mature product, needs extraction)

**CRM:**
- [ ] PRD: Organizations feature
- [ ] PRD: Contact/Profile relationship model
- [ ] Domain: CRM data model

**Reporting:**
- [ ] PRD: Report Builder
- [ ] Domain: Report types and templates

**Fundraising:**
- [ ] PRD: Smart Form / Digital subscription
- [ ] Domain: Offering types and onboarding flows

**Waterfall:**
- [ ] PRD: Waterfall automation
- [ ] Domain: Waterfall calculation logic

### Medium Priority

**Investor Portal:**
- [ ] PRD: Portal features and permissions
- [ ] Domain: Portal architecture

**Payments:**
- [ ] PRD: ACH/Wire/Check/Plaid integration
- [ ] Domain: Payment methods and flows

**Documents:**
- [ ] PRD: Document management features
- [ ] Domain: Document types and security

### Low Priority

**Historical Features:**
- [ ] Cap table management evolution
- [ ] Transaction types (distributions, contributions)
- [ ] Custom fields and extensibility

---

## 🏗️ Recommended Workflow

### When Starting New Work:
1. **Check Planning/** - Is there existing research/discovery?
2. **Check Domains/** - What domain knowledge exists?
3. **Check PRDs/** - Have we built something similar before?
4. **Check Competitors/** - How do competitors handle this?

### When Shipping Features:
1. **Move from In-Development → Archive as PRD**
2. **Extract domain knowledge → Domains/ reference docs**
3. **Update PRD INDEX.md and MIGRATION-PROGRESS.md**

### When Planning:
1. **Create in Planning/** with clear status
2. **Reference Domains/ docs for constraints**
3. **Move to In-Development/ when greenlit**

---

## 📋 File Naming Conventions

**Domain Reference Docs:**
- `Domains/[Module]/README.md` - Module overview
- `Domains/[Module]/[Topic]-Reference.md` - Quick reference guides
- `Domains/[Module]/[Feature]-Architecture.md` - Technical deep dives

**PRDs:**
- `PRDs/[Module]-[Feature]-[ShipDate].md`
- Examples: `Accounting-Phase1-Categorization-Nov2025.md`

**Competitor Profiles:**
- `Competitors/[Name]/Profile.md` - Full competitive intelligence profile
- `Competitors/[Name]/Updates.md` - Reverse-chronological release/news log
- `Competitors/Secondary/[Name].md` - Lightweight single-file profiles
- `Competitors/Cross-Competitor/[Analysis].md` - Cross-competitor comparisons

**Planning Initiatives:**
- `Initiatives/Planning/[Module]/[Initiative-Name]/`
- Use numbered files if multi-doc: `00-Overview.md`, `01-Discovery.md`, etc.

---

## 🔍 Quick Navigation

**I want to understand:**
- Agora's business → `Knowledge/Company/Agora-basics.md`
- Investment Management domain → `Knowledge/Domains/Investment-Management/README.md`
- Accounting domain → `Knowledge/Domains/Accounting/README.md`
- What's been shipped → `Knowledge/PRDs/INDEX.md`
- What's in planning → `Work/Initiatives/Planning/`
- What's in development → `Work/Initiatives/In-Development/`
- A specific competitor → `Knowledge/Competitors/[Name]/Profile.md`
- How we compare overall → `Knowledge/Competitors/Cross-Competitor/`
- Competitor migration status → `Knowledge/Competitors/MIGRATION-PROGRESS.md`

---

## 💡 Key Principles

### Knowledge/ (Frozen & Reference)
- **Stable:** Doesn't change frequently
- **Reference:** Quick lookup for domain concepts
- **Historical:** PRDs document what shipped
- **Quality:** Well-organized, clear, concise

### Work/ (Active & Living)
- **Dynamic:** Changes as work progresses
- **Status-driven:** Planning → In-Development → (ships → PRD)
- **Tactical:** Working docs, meeting notes, planning artifacts
- **Flexible:** Can be messy during active work

---

## ✨ What This Unlocks

### For You (PM)
- **Faster context switching** - Quick domain reference when jumping between initiatives
- **Better planning** - See what's been tried before, what's been shipped
- **Knowledge retention** - No more reinventing wheels or losing context

### For Team
- **Onboarding** - New team members can ramp up on domain knowledge
- **Context sharing** - Engineers/designers can reference domain docs
- **Decision history** - PRDs show past trade-offs and decisions

### For Future Work
- **Pattern recognition** - Spot common patterns across initiatives
- **Avoid repetition** - Check PRDs before planning similar features
- **Build on foundations** - Domain knowledge compounds over time

---

**Status:** ✅ Reorganization Complete (Updated Feb 20, 2026)  
**Completed:**
- ✅ 15 core PRDs migrated from Notion exports
- ✅ 5 Domain docs extracted (Waterfall, Cap Table, Ownership, Performance Metrics, Accounting)
- ✅ Suzy PRDs organized (Migrated vs Not-Migrated)
- ✅ Knowledge/ structure cleaned (no duplicates)
- ✅ Domains/ vs Initiatives/ clarified
- ✅ Competitors/ structure created with batch migration plan (Feb 20, 2026)
- ✅ Juniper Square profile complete (template proven)
- ✅ Raw source archives consolidated into `Knowledge/Sources/` (`competitora/` + `Suzy PRDs/`); all path references updated
- 🚧 9 competitor migration batches remaining (tracked in `Knowledge/Competitors/MIGRATION-PROGRESS.md`)

**Next:**
- Continue competitor migration batches (2-10)
- Build `competitor-update` skill for ongoing maintenance
- Continue extracting domain knowledge as new features ship
