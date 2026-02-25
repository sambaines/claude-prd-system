# /docs — Project Intelligence Layer

This folder is the source of truth for **why** this project exists,
**what** it is supposed to do, and **how** it has been built.
It is not documentation generated after the fact — it is the thinking
that drives development forward.

If you are a collaborator, start here before touching any code.
If you are Claude, read `CLAUDE.md` at the project root first,
then return here.

---

## Two Modes

This documentation system operates in one of two modes, set in `CLAUDE.md`:

**Full mode** — for websites, apps, and shipped products. Uses the complete
document hierarchy: PRD, architecture spec, feature specs, decision log, tasks.

**Lean mode** — for POCs, experiments, and internal tools. Replaces PRD +
architecture spec with a single `BRIEF.md`. Decision log is omitted unless
something worth carrying forward is decided.

---

## Full Mode Structure
```
/docs
├── README.md            ← this file
├── PRODUCT.md           ← PRD: why, what, for whom
├── DECISIONS.md         ← ADR log: every significant decision and its reasoning
├── SPEC.md              ← architecture spec: overall system design
├── /specs
│   └── [feature].md    ← per-feature implementation contracts
├── /tasks
│   └── current.md      ← active session handoff
└── /archive
    └── [old versions]  ← superseded documents, never deleted
```

## Lean Mode Structure
```
/docs
├── README.md
├── BRIEF.md             ← single doc: what, goals, done criteria, constraints
├── /tasks
│   └── current.md
└── /archive
```

---

## The Documents and How They Relate

### `PRODUCT.md` — The Why and What
The Product Requirements Document. Non-technical, plain language.
Describes the problem being solved, the users it serves, the features
required, and explicit non-goals.

**It answers:** Why does this exist? What does it do? What does it
deliberately not do? What does done look like at the project level?

**Stability:** High. All changes are versioned inline in its Changelog
section — never silently edited.

---

### `BRIEF.md` — The Lean Alternative
One-page version of PRD + spec for small-scope work.
Goals, constraints, tech stack, done criteria, open questions.
Findings are appended during development so the brief becomes a record
of what was learned, not just what was built.

**Used when:** Project type is POC, experiment, or internal tool.

---

### `DECISIONS.md` — The Because
Architecture Decision Record log. Every significant decision — a
technology chosen, a pattern adopted, an approach ruled out — is
recorded here with reasoning, alternatives considered, and tradeoffs
accepted.

**It answers:** Why is it built this way? What did we rule out and why?
What does a past decision constrain going forward?

**Stability:** Append-only. Decisions are never deleted — only amended
or reversed, with the original preserved.

**How to reference:** Decisions are numbered (ADR-001, ADR-002).
Specs and tasks reference them by ID. When working on a feature, check
for relevant ADRs before proposing an approach.

---

### `SPEC.md` — The How (System Level)
Top-level architecture spec. Covers system overview, repository structure,
core dependencies, top-level data model, and the feature specs index.

Contains **modular optional sections** for the project's type — only
the relevant sections are filled in. Sections not applicable are removed
or marked as omitted:

- `[WEB]` — routing, rendering strategy, auth architecture, API layer
- `[SHOPIFY]` — integration type, Storefront API usage, metafields, webhooks
- `[NATIVE MAC]` — process model, storage, sandboxing, auto-update
- `[RUST/SYSTEMS]` — crate structure, error handling, memory model, concurrency
- `[GAME]` — game loop, entity model, renderer, asset pipeline
- `[CONTENT]` — content types, CMS, media handling, localisation

**Stability:** Medium. Changes are deliberate. The feature specs index
here is the master list of all specs and their status.

---

### `/specs/[feature].md` — The How (Feature Level)
Implementation contracts for discrete features. Each spec defines
the data model, interface contract, component breakdown, error handling,
and edge cases for one feature.

Like `SPEC.md`, feature specs use modular optional sections keyed to
project type: `[WEB/API]`, `[NATIVE/SYSTEMS]`, `[GAME]`, `[SHOPIFY]`.

**Specs are written before code, not after.**

**Cross-referencing:** Each spec links to its PRD section and relevant
ADRs, creating a traceable line:
```
Code → implements /docs/specs/[feature].md
         → references DECISIONS.md ADR-###
              → traces back to PRODUCT.md section
```
If you cannot trace a piece of code back to the PRD, either the docs
are out of date or the code should not exist.

---

### `/tasks/current.md` — The Now
Active session handoff. Written at the end of one session to set up
the next. Scopes exactly what is being built, which files are in play,
what is off-limits, and what done looks like for this session.

**Stability:** Ephemeral. Rewritten each session.
Completed tasks are not the historical record — that's DECISIONS.md.

---

## Working With Claude

This folder is designed for Claude (claude.ai or Claude Code) as a
primary collaborator. A few principles that make the system work:

**Claude has no memory between sessions.** The `/tasks/current.md` file
re-establishes context at the start of each session. Write it as if
Claude knows nothing about what happened before — because it doesn't.

**Claude reads `CLAUDE.md` at the project root first.** That file
contains guardrails, tech stack constraints, project type, and standing
orders. This `/docs` folder contains the project intelligence.
They work together.

**Claude should not resolve Open Questions unilaterally.** Any section
marked Open Questions in a spec or task is a flag to stop and ask.

**Claude should flag conflicts between documents.** If a spec contradicts
the PRD, or a task asks for something that violates an ADR, Claude
surfaces the conflict rather than silently picking a side.

**Claude uses the project type field in `CLAUDE.md`** to know which
reasoning mode applies — web tradeoffs differ from systems tradeoffs,
which differ from game engine tradeoffs.

---

## Cross-Project Layer (Optional)

For maintaining knowledge across multiple projects, a `/meta` folder
sits above individual project roots:
```
/meta
├── PATTERNS.md    ← decisions and conventions that apply to all projects
└── LESSONS.md     ← things that caused real problems, not to be repeated
```

Individual project `CLAUDE.md` files reference `/meta/PATTERNS.md`.
Project-level decisions override meta patterns, but conflicts should
be flagged and reconciled.

---

## Document Lifecycle
```
Draft → Active → Amended / Superseded → Archived
```

- **Draft:** Being written, not yet driving decisions.
- **Active:** Current and authoritative.
- **Amended:** A later document changed or extended this one.
  Original preserved with link to amendment.
- **Superseded:** Replaced wholesale. Original moved to `/archive`
  with date and reason noted.

Never delete documents. The history of what was decided and why is
one of the most valuable things this folder contains.

---

## Keeping This System Alive

The most common failure mode: the docs start accurate and go stale.
The End of Session Checklist in `/tasks/current.md` is the maintenance
mechanism — five minutes at the end of every session:

- New decisions made? → Log in `DECISIONS.md`
- Specs changed? → Update spec + its changelog
- PRD shifted? → Add versioned entry to `PRODUCT.md` changelog
- Something worth carrying to future projects? → Add to `/meta/PATTERNS.md`
- `current.md` ready for next session? → Update context and carry-forward

A trustworthy doc system is what makes Claude a reliable long-term
collaborator rather than a stateless code generator. The discipline
is the upkeep.

---

## Templates

All document templates are available at:
[link to your templates repo / Notion / storage location]

Templates included:
- `CLAUDE.md`
- `PRODUCT.md` (full PRD)
- `BRIEF.md` (lean mode)
- `SPEC.md` (architecture, with modular sections)
- `SPEC-feature.md` (feature spec, with modular sections)
- `DECISIONS.md` (ADR log)
- `tasks/current.md` (session handoff)
- `CHANGELOG.md` (release log)
- `/meta/PATTERNS.md`
- `/meta/LESSONS.md`