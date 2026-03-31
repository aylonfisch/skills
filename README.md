# AI Skills for Cursor (& other AI tools)

A collection of shareable agent skills — PM workflows, productivity tools, and a self-improvement loop for AI systems.

Built for Cursor but adaptable to any AI tool that supports skill/command files.

---

## What's Here

```
.cursor/skills/
├── pmskill/              ← Router: finds the right PM framework for any situation
├── evals/                ← Self-improvement loop: capture bad responses, fix the root cause
├── knowledge-intake/     ← Ingest documents into a structured knowledge base
├── batch-migration/      ← Migrate items in bulk across systems
│
├── pm-skills/            ← 65 PM framework skills (via submodule)
└── awesome-pm-skills/    ← 28 PM craft skills (via submodule)
```

**93 PM framework skills · 4 productivity skills · 1 router**

See [SKILLS-INDEX.md](SKILLS-INDEX.md) for the full lookup table.

---

## Install a Skill

Copy any skill folder into your `.cursor/skills/` directory (or equivalent for your AI tool):

```bash
# Example: install the evals skill
cp -r .cursor/skills/evals/ /your-project/.cursor/skills/evals/
```

Each skill folder contains a `SKILL.md` with full instructions. Some also include:
- `README.md` — install guide and usage notes
- `evals-log.md` — log template (evals skill only)

---

## Skills

### `evals` — Self-Improvement Loop

Captures bad AI responses, diagnoses root causes, applies fixes to the right artifact, and generates regression tests.

**Trigger:** `"flag this"` / `"run eval"` / `"close session"`

[→ Install guide](.cursor/skills/evals/README.md)

---

### `pmskill` — PM Framework Router

Finds the right PM framework for any situation across 93 skills. Describe what you're trying to do and it routes you to the right skill.

**Trigger:** `"what framework should I use for..."` or `/pmskill`

---

### `knowledge-intake` — Document Ingestion

Routes and formats documents into a structured knowledge base using established templates and conventions.

**Trigger:** `"intake this doc"` / `"add to knowledge base"`

---

### `batch-migration` — Bulk Migration

Migrates items in bulk across systems with validation and rollback support.

**Trigger:** `"batch migrate [items]"`

---

## PM Skill Libraries (Submodules)

This repo includes two external PM skill libraries as git submodules:

| Library | Skills | Source |
|---|---|---|
| `pm-skills` | 65 skills across Discovery, Strategy, Execution, Research, Analytics, GTM | [phuryn/pm-skills](https://github.com/phuryn/pm-skills) |
| `awesome-pm-skills` | 28 skills across craft, leadership, communication | [menkesu/awesome-pm-skills](https://github.com/menkesu/awesome-pm-skills) |

To pull submodules after cloning:

```bash
git clone --recurse-submodules https://github.com/aylonfisch/skills.git
```

---

## Contributing

Skills should be:
- **Self-contained** — one folder, one `SKILL.md`, no external dependencies
- **Tool-agnostic** — written in plain markdown, adaptable beyond Cursor
- **Trigger-driven** — clear natural language phrases that activate the skill
