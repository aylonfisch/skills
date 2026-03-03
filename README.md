# PM Skills for Cursor (& other AI tools)

A curated collection of PM skills for AI coding assistants — with a smart router that finds the right framework for any situation.

**93 skills across 2 libraries + 1 router to rule them all.**

---

## What's in here

| | |
|---|---|
| 🧭 **`/pmskill` router** | Dump your situation in plain language, get routed to the exact right skill — no framework knowledge required |
| 📦 **[phuryn/pm-skills](https://github.com/phuryn/pm-skills)** | 65 structured PM skills across discovery, strategy, execution, GTM, analytics, and more |
| ⚡ **[awesome-pm-skills](https://github.com/menkesu/awesome-pm-skills)** | 28 opinionated skills based on frameworks from Marty Cagan, Teresa Torres, April Dunford, and others |

---

## How the router works

Type `/pmskill` and just **dump your situation** — messy brain dump, voice note, bullet points, whatever.

The router infers what you need and picks a mode:

**Deliberate mode** (you know roughly what you need):
```
→ Use: create-prd
Why: You need a structured spec before your engineering sync tomorrow.
Load: .cursor/skills/pm-skills/pm-execution/skills/create-prd/SKILL.md
To start: Paste your feature idea and I'll build the PRD.
```

**Brainstorm mode** (you're exploring):
```
Brainstorm mode — 3 angles on your pricing problem:

1. competitor-analysis — understand what the market charges and why
2. pricing-strategy    — design your model, test willingness-to-pay
3. value-proposition   — reframe what you're selling before pricing it

Suggested chain: run 1 first → feed output into 3 → then 2.
```

No upfront questions. No framework knowledge needed. Just describe where you're stuck.

---

## Install

### Cursor

```bash
# Clone into your project's .cursor/skills folder
cd your-project/.cursor/skills
git clone --recurse-submodules https://github.com/aylonfisch/skills.git .

# Or clone anywhere and symlink
git clone --recurse-submodules https://github.com/aylonfisch/skills.git ~/pm-skills
```

Then in Cursor, type `/pmskill` to start.

### Claude Code

```bash
git clone --recurse-submodules https://github.com/aylonfisch/skills.git ~/.claude/skills/pm
```

### Gemini CLI / Codex CLI / Kiro

```bash
# Clone and copy skills to your tool's skills folder
git clone --recurse-submodules https://github.com/aylonfisch/skills.git /tmp/pm-skills
cp -r /tmp/pm-skills/.cursor/skills/* ~/.gemini/skills/   # Gemini
cp -r /tmp/pm-skills/.cursor/skills/* ~/.codex/skills/    # Codex
```

---

## What's included

### The Router — `/pmskill`
`.cursor/skills/pmskill/SKILL.md`

Takes free-form input, infers your stage + deliverable, recommends a single skill (deliberate) or a chained set (brainstorm). Max 1 clarifying question if genuinely ambiguous.

### pm-skills (65 skills, 8 plugins)
From [phuryn/pm-skills](https://github.com/phuryn/pm-skills) — built on Teresa Torres, Marty Cagan, Alberto Savoia, April Dunford frameworks.

- `pm-product-discovery` — ideation, experiments, OST, customer interviews
- `pm-product-strategy` — strategy canvas, vision, value prop, pricing, SWOT
- `pm-execution` — PRDs, OKRs, roadmaps, sprints, retros, user stories
- `pm-market-research` — personas, journey maps, market sizing, competitor analysis
- `pm-data-analytics` — SQL, cohort analysis, A/B test analysis
- `pm-go-to-market` — GTM strategy, ICP, growth loops, battlecards
- `pm-marketing-growth` — positioning, naming, North Star metric
- `pm-toolkit` — resume review, NDA, proofreading

### awesome-pm-skills (28 skills)
From [awesome-pm-skills](https://github.com/menkesu/awesome-pm-skills) — opinionated skills based on real PM playbooks.

`ai-product-patterns` · `ship-decisions` · `positioning-craft` · `strategic-storytelling` · `exec-comms` · `decision-frameworks` · `jtbd-building` · `growth-embedded` · `continuous-discovery` · and more.

### SKILLS-INDEX.md
Full lookup table with all 93 skills, paths, and pre-built chains for common situations (new feature, launch prep, quarterly planning, pricing decision, etc.).

---

## Skill chains

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

## Credits

- [phuryn/pm-skills](https://github.com/phuryn/pm-skills) by Paweł Huryn / [Product Compass](https://www.productcompass.pm)
- [awesome-pm-skills](https://github.com/menkesu/awesome-pm-skills) by menkesu
- Router and index by [@aylonfisch](https://github.com/aylonfisch)
