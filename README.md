# PM Skills for Cursor (& other AI tools)

A curated collection of AI skills — PM frameworks and productivity tools — with a smart router that finds the right framework for any situation.

**93 PM skills · 2 productivity tools · 1 router to rule them all.**

---

## Structure

```
.cursor/skills/
├── 🧭 pmskill/              ← router: /pmskill to start
│
├── ── PM Frameworks ──
├── pm-skills/               ← 65 skills (phuryn/pm-skills)
├── awesome-pm-skills/       ← 28 skills (menkesu/awesome-pm-skills)
│
└── ── Productivity Tools ──
    ├── knowledge-intake/    ← ingest docs into structured knowledge
    └── batch-migration/     ← migrate content in bulk
```

---

## The `/pmskill` Router

Type `/pmskill` and **dump your situation** — messy brain dump, voice note, bullets, whatever.

The router infers what you need and picks a mode:

**Deliberate** (you know roughly what you need):
```
→ Use: create-prd
Why: You need a structured spec before your engineering sync tomorrow.
Load: .cursor/skills/pm-skills/pm-execution/skills/create-prd/SKILL.md
To start: Paste your feature idea and I'll build the PRD.
```

**Brainstorm** (you're exploring):
```
3 angles on your pricing problem:

1. competitor-analysis  — understand what the market charges and why
2. pricing-strategy     — design your model, test willingness-to-pay
3. value-proposition    — reframe what you're selling before pricing it

Suggested chain: run 1 → feed into 3 → then 2.
```

No framework knowledge needed. Just describe where you're stuck.

---

## PM Skills (93 skills across 2 libraries)

### [phuryn/pm-skills](https://github.com/phuryn/pm-skills) — 65 skills, 8 plugins
Built on Teresa Torres, Marty Cagan, Alberto Savoia, April Dunford frameworks.

| Plugin | Skills |
|--------|--------|
| `pm-product-discovery` | ideation, experiments, OST, assumptions, interviews |
| `pm-product-strategy` | strategy canvas, vision, value prop, pricing, SWOT |
| `pm-execution` | PRDs, OKRs, roadmaps, sprints, retros, user stories |
| `pm-market-research` | personas, journey maps, market sizing, competitor analysis |
| `pm-data-analytics` | SQL, cohort analysis, A/B test analysis |
| `pm-go-to-market` | GTM strategy, ICP, growth loops, battlecards |
| `pm-marketing-growth` | positioning, naming, North Star metric |
| `pm-toolkit` | resume review, NDA, proofreading |

### [menkesu/awesome-pm-skills](https://github.com/menkesu/awesome-pm-skills) — 28 skills
Opinionated playbooks from real PM practitioners.

`ai-product-patterns` · `ship-decisions` · `positioning-craft` · `strategic-storytelling` · `exec-comms` · `decision-frameworks` · `jtbd-building` · `growth-embedded` · `continuous-discovery` · `quality-speed` · `influence-craft` · `strategic-pm` · and more.

---

## Productivity Tools

| Skill | What it does |
|-------|-------------|
| `knowledge-intake` | Ingest a document, meeting, or source into structured knowledge |
| `batch-migration` | Migrate content in bulk across formats or systems |

---

## Skill Chains

Pre-built sequences for common PM workflows:

| Situation | Chain |
|-----------|-------|
| New feature from scratch | `identify-assumptions` → `opportunity-solution-tree` → `create-prd` → `pre-mortem` |
| Launch prep | `positioning-craft` → `launch-execution` → `competitive-battlecard` → `release-notes` |
| Quarterly planning | `strategic-pm` → `brainstorm-okrs` → `outcome-roadmap` → `sprint-plan` |
| Validate a risky bet | `identify-assumptions` → `prioritize-assumptions` → `brainstorm-experiments` |
| Pricing decision | `competitor-analysis` → `pricing-strategy` → `monetization-strategy` → `value-prop-statements` |
| Discovery sprint | `continuous-discovery` → `interview-script` → `summarize-interview` → `user-feedback-system` |

---

## Install

### Cursor

```bash
# Clone into your project's .cursor/skills folder
cd your-project
git clone --recurse-submodules https://github.com/aylonfisch/skills.git .cursor/skills
```

Then type `/pmskill` in Cursor to start.

### Other AI tools

```bash
git clone --recurse-submodules https://github.com/aylonfisch/skills.git

# Gemini CLI
cp -r skills/.cursor/skills/* ~/.gemini/skills/

# Codex CLI
cp -r skills/.cursor/skills/* ~/.codex/skills/

# Kiro
cp -r skills/.cursor/skills/* ~/.kiro/skills/
```

---

## Credits

- [phuryn/pm-skills](https://github.com/phuryn/pm-skills) by Paweł Huryn / [Product Compass](https://www.productcompass.pm)
- [menkesu/awesome-pm-skills](https://github.com/menkesu/awesome-pm-skills)
- Router, index, and productivity skills by [@aylonfisch](https://github.com/aylonfisch)
