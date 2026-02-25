# Skill: Project Setup

Scaffolds a new project with the correct folder structure and pre-populated documentation templates, ready to fill in.

---

## Inputs

Collect these before proceeding. If any are missing, ask for them.

| Input | Values | Required |
|-------|--------|----------|
| `PROJECT_NAME` | Any string (e.g. `my-app`) | Yes |
| `PROJECT_PATH` | Absolute path where the project folder should be created | Yes |
| `MODE` | `Full` or `Lean` | Yes |
| `TYPE` | One of the project types from the list below | Yes |
| `STACK` | Key technologies (e.g. `TypeScript, Next.js, Tailwind, Postgres`) | Yes |
| `META` | `Yes` or `No` — whether to connect to /meta cross-project layer | No (default: No) |

**Project types:**
- `Web — content site / marketing`
- `Web — application (auth, data, user state)`
- `Web — headless commerce (Shopify)`
- `Native Mac — Electrobun`
- `Native Mac — Rust`
- `Systems / Game Engine — Rust`
- `Game — web technologies`
- `Game — Rust`
- `Internal Tool — lightweight / throwaway`
- `POC / Experiment`

---

## Procedure

### Step 1 — Verify inputs and confirm

Before creating anything, output a summary of what will be created and ask for confirmation:

```
Project: [PROJECT_NAME]
Path: [PROJECT_PATH]/[PROJECT_NAME]
Mode: [MODE]
Type: [TYPE]
Stack: [STACK]
Meta connection: [META]

This will create:
[list the files and folders — see Step 2]

Proceed?
```

### Step 2 — Create directory structure

**Full mode:**
```
/[PROJECT_PATH]/[PROJECT_NAME]
├── CLAUDE.md
├── CHANGELOG.md
└── /docs
    ├── README.md
    ├── PRODUCT.md
    ├── DECISIONS.md
    ├── SPEC.md
    ├── TECH-DEBT.md
    ├── /specs           ← create empty directory
    ├── /tasks
    │   └── current.md
    └── /archive         ← create empty directory
```

**Lean mode:**
```
/[PROJECT_PATH]/[PROJECT_NAME]
├── CLAUDE.md
└── /docs
    ├── README.md
    ├── BRIEF.md
    ├── /tasks
    │   └── current.md
    └── /archive         ← create empty directory
```

### Step 3 — Read templates

Templates live at:
```
~/Documents/02_Projects/02_templates-and-skills/templates/
```

Read these template files before writing each output file:

| Output file | Template source |
|-------------|----------------|
| `CLAUDE.md` | `templates/CLAUDE.md` |
| `CHANGELOG.md` | `templates/CHANGELOG.md` |
| `docs/README.md` | `templates/docs-README.md` |
| `docs/PRODUCT.md` | `templates/PRODUCT.md` |
| `docs/BRIEF.md` | `templates/BRIEF.md` |
| `docs/DECISIONS.md` | `templates/DECISIONS.md` |
| `docs/SPEC.md` | `templates/SPEC.md` |
| `docs/TECH-DEBT.md` | `templates/TECH-DEBT.md` |
| `docs/tasks/current.md` | `templates/current.md` |

### Step 4 — Apply substitutions

When writing each file, apply these substitutions:

**Universal (all files):**
- Replace `[Project Name]` with `PROJECT_NAME`
- Replace `[YYYY-MM-DD]` with today's date

**CLAUDE.md — additional substitutions:**
- In the Project Type checklist, replace `[ ]` with `[x]` on the line matching `TYPE`. Leave all others as `[ ]`.
- Set `**Mode:** Full | Lean` → `**Mode:** Full` or `**Mode:** Lean` (remove the one that doesn't apply)
- In the Docs Structure section, if MODE is Lean: remove the `[Full]` lines, keep the `[Lean]` line, remove the `[Full only]` note. If MODE is Full: remove the `[Lean]` line, keep the `[Full]` lines.
- If META is Yes: set the cross-project patterns line to `- Cross-project patterns: ../../meta/PATTERNS.md`. If No: remove that line.
- In the Tech Stack section: delete rows that clearly don't apply to TYPE. For example, if TYPE is not Shopify, remove Commerce row. If TYPE is not native Mac, remove Native runtime row. If TYPE is not Rust/systems, remove Systems language row. Use TYPE and STACK as context for which rows are relevant. Leave applicable rows with their placeholder values — do not fill in STACK details; the user will do that.

**docs/README.md — no substitutions needed** beyond project name and date. This file explains the doc system and does not need customisation.

**docs/PRODUCT.md:**
- Set `**Project type:**` to `TYPE`
- Set `**Mode:** Full`

**docs/BRIEF.md:**
- Set `**Type:**` — choose `POC`, `Internal Tool`, or `Experiment` based on TYPE, or leave as-is if TYPE doesn't clearly map to one of these

**docs/DECISIONS.md:**
- No additional substitutions beyond project name and date

**docs/SPEC.md:**
- Set `**Project type:**` to `TYPE`
- Remove optional sections (`[WEB]`, `[SHOPIFY]`, `[NATIVE MAC]`, `[RUST / SYSTEMS]`, `[GAME]`, `[CONTENT]`) that clearly don't apply to TYPE. Keep the ones that do. If TYPE is ambiguous (e.g. a web app might also have content), keep both.
- For each kept optional section, leave all placeholder values intact — do not fill in architecture details.

**docs/tasks/current.md:**
- Set `**Session date:**` to today's date
- Leave all other fields as their placeholder values

### Step 5 — Write files

Write each file to its destination path with the substitutions applied. Do not add any content beyond what is in the templates after substitutions — the user fills in the blanks.

### Step 6 — Output summary

After all files are written, output:

```
Project scaffolded at [PROJECT_PATH]/[PROJECT_NAME]

Files created:
  CLAUDE.md
  CHANGELOG.md          ← [Full only]
  docs/README.md
  docs/PRODUCT.md       ← [Full only]
  docs/BRIEF.md         ← [Lean only]
  docs/DECISIONS.md     ← [Full only]
  docs/SPEC.md
  docs/TECH-DEBT.md     ← [Full only]
  docs/tasks/current.md
  docs/specs/           ← empty, add feature specs here
  docs/archive/         ← empty, for superseded docs

Next steps:
1. Open CLAUDE.md and fill in: Tech Stack details, Code Patterns, File & Folder Conventions, Environment & Secrets, and What Good Looks Like Here.
2. Open docs/[PRODUCT.md | BRIEF.md] and fill in the project description, goals, and constraints.
3. Open docs/SPEC.md and fill in: System Overview, Repository Structure, and Core Dependencies. Delete any architecture sections that don't apply.
4. Before your first session: write docs/tasks/current.md with your starting context.
```

---

## Notes

- Do not fill in the user's actual tech stack, architecture decisions, or product details. Scaffold only — leave placeholders for the user to complete.
- If the project directory already exists, warn the user and ask whether to proceed (risk of overwriting files) or abort.
- If the templates directory cannot be found at `~/Documents/02_Projects/02_templates-and-skills/templates/`, tell the user and ask them to provide the correct path.
