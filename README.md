# Project System — Templates & Skills

This repository contains the complete documentation and automation system for all my projects. It defines **how projects are structured, documented, and managed** when working with Claude as a development collaborator.

---

## What This Is

A standardized approach to project setup and documentation that:

- Creates traceable decision-making (every line of code traces back through specs → decisions → product requirements)
- Enables effective human-AI collaboration across sessions (Claude has no memory; these docs provide context)
- Scales from quick POCs to production systems (two modes: Full and Lean)
- Works across project types (web, native Mac, Rust/systems, games, commerce, tools)
- Captures cross-project knowledge so lessons learned compound over time

This system was designed through iterative conversation with Claude to solve the core problems of LLM-assisted development: context loss between sessions, architectural drift, and undocumented decisions.

---

## Repository Structure
```
/templates-and-skills
├── README.md              ← this file
├── /templates
│   ├── CLAUDE.md          ← Project guardrails, tech stack, patterns
│   ├── PRODUCT.md         ← PRD template (Full mode)
│   ├── BRIEF.md           ← One-page brief (Lean mode)
│   ├── SPEC.md            ← Architecture spec with modular sections
│   ├── SPEC-feature.md    ← Per-feature spec template
│   ├── DECISIONS.md       ← ADR log template
│   ├── TECH-DEBT.md       ← Technical debt register
│   ├── current.md         ← Session handoff template
│   ├── CHANGELOG.md       ← Release notes template
│   ├── docs-README.md     ← System explainer for /docs folder
│   ├── meta-PATTERNS.md   ← Cross-project patterns template
│   └── meta-LESSONS.md    ← Cross-project lessons template
└── /skills
    ├── project-setup/
    │   └── SKILL.md
    ├── patch-notes-generator/
    │   └── SKILL.md
    ├── document-spinner/
    │   └── SKILL.md
    └── codebase-health-review/
        └── SKILL.md
```

---

## How to Use This System

### Starting a New Project

1. **Decide on mode:**
   - **Full mode** — for websites, apps, shipped products, anything long-lived
   - **Lean mode** — for POCs, experiments, internal tools, throwaway work

2. **Use the Project Setup skill** (or manually copy templates):
```
   PROJECT_NAME: [name]
   MODE: Full | Lean
   TYPE: [web app | Shopify | native Mac | Rust | game | tool | etc.]
   STACK: [key technologies]
   META: Yes | No (connect to cross-project patterns?)
```

3. **The skill scaffolds:**
```
   /your-new-project
   ├── CLAUDE.md
   ├── CHANGELOG.md (if Full mode)
   └── /docs
       ├── README.md
       ├── PRODUCT.md (Full) OR BRIEF.md (Lean)
       ├── DECISIONS.md (Full only)
       ├── SPEC.md
       ├── TECH-DEBT.md (Full only)
       ├── /specs (as needed)
       ├── /tasks
       │   └── current.md
       └── /archive
```

4. **Fill in the templates** with your actual project details. The templates are heavily commented with instructions for what goes in each section.

5. **Start building.** Claude reads `CLAUDE.md` at the start of every session. You write `current.md` to define what you're doing each session.

---

## The Two Modes

### Full Mode
Complete documentation system for projects that will be maintained, shipped, or collaborated on.

**Documents:**
- `PRODUCT.md` — why this exists, what it does, for whom
- `SPEC.md` — overall architecture, with modular sections by project type
- `DECISIONS.md` — every significant decision, logged as ADRs
- `TECH-DEBT.md` — inventory of known debt and deferred fixes
- `/specs/*.md` — per-feature implementation contracts
- `/tasks/current.md` — session-to-session handoff

**Use when:** Building something real that will last beyond a few weeks.

### Lean Mode
Streamlined for fast iteration and experimentation.

**Documents:**
- `BRIEF.md` — replaces PRD + SPEC. One page: goals, constraints, done criteria.
- `/tasks/current.md` — session handoff (same as Full mode)

**Use when:** POCs, experiments, internal tools, learning projects.

---

## Key Documents Explained

### `CLAUDE.md` (Project Root)
**Purpose:** Standing orders for every session. Claude reads this first.
**Contains:** Tech stack, code patterns, file conventions, what requires approval, known gotchas, project type.
**Lives at:** Project root (not in `/docs`)

### `PRODUCT.md` (Full mode)
**Purpose:** The PRD. Why this product exists and what it does.
**Contains:** Problem statement, goals, non-goals, users, features, constraints, success metrics.
**Changes:** Versioned inline via changelog table. Never silently edited.

### `BRIEF.md` (Lean mode)
**Purpose:** Lightweight PRD+SPEC combined.
**Contains:** What this is, goals, non-goals, done criteria, tech stack, constraints.
**Changes:** Append findings during development. Brief becomes a record of what was learned.

### `DECISIONS.md` (Full mode)
**Purpose:** Architecture Decision Record log. Every significant decision.
**Format:** ADR-### entries with: context, decision, reasoning, tradeoffs, alternatives considered.
**Never delete:** Amended or reversed decisions are preserved, not removed.

### `SPEC.md`
**Purpose:** Overall system architecture.
**Contains:** Modular sections by project type — only relevant sections are included. Delete sections that don't apply.
**Sections:** `[WEB]`, `[SHOPIFY]`, `[NATIVE MAC]`, `[RUST/SYSTEMS]`, `[GAME]`, `[CONTENT]`

### `SPEC-feature.md`
**Purpose:** Per-feature implementation contract.
**Contains:** Data model, API/module interface, component breakdown, error handling, edge cases, tests.
**Also modular:** Same optional sections as SPEC.md, keyed to project type.

### `TECH-DEBT.md` (Full mode)
**Purpose:** Inventory of known technical debt and deferred fixes.
**Format:** Severity, location, issue, why it exists, fix approach, effort estimate.
**Maintained:** Updated during sessions, reviewed periodically via Codebase Health Review skill.

### `current.md`
**Purpose:** Session handoff. What we're doing right now.
**Owned by:** You (with collaborative end-of-session rewrite with Claude).
**Ephemeral:** Rewritten each session. Not an archive — that's DECISIONS.md.

### `CHANGELOG.md` (Project Root)
**Purpose:** User-facing release notes for shipped products.
**Format:** [Keep a Changelog](https://keepachangelog.com/) standard.
**Lives at:** Project root (not in `/docs`)

---

## Cross-Project Layer (Optional)

For maintaining knowledge across multiple projects:
```
/your-work-root
├── /meta
│   ├── PATTERNS.md    ← Conventions that apply to all projects
│   └── LESSONS.md     ← Things that caused problems, not to be repeated
├── /templates-and-skills (this repo)
├── /project-one
├── /project-two
└── [etc.]
```

Individual project `CLAUDE.md` files reference `/meta/PATTERNS.md` via relative path:
```markdown
## Docs Structure
- Cross-project patterns: ../../meta/PATTERNS.md
```

**Use when:** You have 3+ projects and patterns are emerging that should be standardized.

---

## The Skills

Skills automate parts of the system. They live in Claude's skill system (uploaded once, available everywhere) but their source lives here for version control.

### Project Setup
**What it does:** Scaffolds a new project with the full folder structure and pre-populated templates.
**Inputs:** Project name, mode (Full/Lean), type, stack, meta connection.
**Output:** Complete `/docs` folder ready to fill in.

### Patch Notes Generator
**What it does:** Converts `CHANGELOG.md` into user-facing patch notes or release announcements.
**Inputs:** CHANGELOG.md, tone (game/app/web/technical), scope (latest/all/range), output format.
**Output:** Formatted markdown, HTML, or plain text ready to publish.

### Document Spinner
**What it does:** Generates a pre-filled document from templates.
**Inputs:** Doc type (feature spec, ADR, brief, etc.), project type, name, references.
**Output:** Document with relevant sections included, irrelevant sections removed, references pre-populated.

### Codebase Health Review
**What it does:** Scans codebase for technical debt, stale decisions, and unresolved questions.
**Inputs:** Project root, scope (full/area/recent), depth (surface/deep).
**Output:** Structured report of TODOs, debt not logged, stale open questions, PRD items never addressed.

---

## Uploading and Updating Skills

Skills are stored in `/skills/[name]/SKILL.md` in this repo. To use them:

1. **Create or edit** the SKILL.md file locally
2. **Upload to Claude:**
   - Use the skill-creator skill: "Create a new skill from /path/to/SKILL.md"
   - Or manually copy-paste the skill content into Claude and ask to create it
3. **Test** the skill in a conversation
4. **Commit** the working version to this repo
5. **Re-upload** if you make changes

The repo is your source of truth. The uploaded version in Claude is the "deployed" version.

---

## Working With Claude

### Session Start Routine
1. Claude reads `CLAUDE.md` at project root (automatically, if using Claude Code or if you reference it)
2. You've written `current.md` before the session (or at session start together)
3. Claude reads `current.md` to understand what we're doing today
4. Claude reads any referenced specs or ADRs from `current.md`
5. Work begins

### Session End Routine
Run through the End of Session Checklist in `current.md` together:
- New decisions made? → Log in DECISIONS.md
- Specs changed? → Update changelog
- PRD shifted? → Version it in PRODUCT.md
- New debt surfaced? → Log in TECH-DEBT.md
- Lessons learned? → Consider adding to /meta/LESSONS.md
- Ready for next session? → Rewrite current.md context and carry-forward

### Claude's Role
- **Executes** against specs and tasks
- **Flags** conflicts between docs, ADRs, and current work
- **Reminds** you to log decisions, debt, and findings
- **Does not** unilaterally resolve Open Questions or override ADRs

### Your Role
- **Owns** product direction and priorities
- **Writes** current.md (what we're doing next)
- **Decides** when to resolve Open Questions
- **Maintains** the docs via the end-of-session checklist

---

## When to Use Plan Mode

With this system in place, Plan Mode shifts from a general habit to a specific-purpose tool:

**Use Plan Mode when:**
- Speccing a new feature before writing the spec (exploratory thinking)
- Something unexpected surfaces mid-session that the docs don't cover (circuit breaker)

**Don't use Plan Mode for:**
- General "what should I build" thinking (that's `current.md`)
- Architecture decisions (that's the speccing process + DECISIONS.md)
- Keeping Claude on track (that's CLAUDE.md + task breakdown)

---

## Maintenance

### Monthly (for Full mode projects)
- Run **Codebase Health Review** skill
- Triage TECH-DEBT.md — prioritize P1/P2 items
- Review DECISIONS.md Deferred section before planning new features

### Quarterly
- Review `/meta/PATTERNS.md` — are there new patterns from recent projects to add?
- Review `/meta/LESSONS.md` — capture anything significant that happened
- Review this repo — are the templates still working? Do skills need updates?

---

## Philosophy

This system exists because **LLMs have no memory, but projects have history.**

The discipline is not in following templates rigidly — it's in **capturing the thinking behind decisions** so that context persists across sessions, collaborators, and time.

Good documentation enables good AI collaboration. This system is the structure that makes good documentation achievable without it becoming a burden.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-02-25 | Initial system established through iterative design conversation |

---

## References

- [Keep a Changelog](https://keepachangelog.com/) — changelog format standard
- [Semantic Versioning](https://semver.org/) — versioning standard
- Architecture Decision Records concept — [Joel Parker Henderson's ADR repo](https://github.com/joelparkerhenderson/architecture-decision-record)

---

*This system was designed collaboratively with Claude (Sonnet 4) over [date]. It reflects hard-won lessons about what makes human-AI collaboration effective for software development.*