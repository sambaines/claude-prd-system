# Cross-Project Patterns & Lessons
**Maintained by:** [Your name]
**Last Updated:** [YYYY-MM-DD]

---

## ⚠️ Claude: Read This First
This file sits above individual projects and records knowledge that
applies across all of them. Before suggesting an approach that has
a pattern recorded here, check whether it contradicts or extends it.
If a project's CLAUDE.md conflicts with an entry here, the project-level
CLAUDE.md takes precedence — but flag the conflict so it can be reconciled.

---

## How to Use This File
- Reference from individual project CLAUDE.md files:
  `Cross-project patterns: /meta/PATTERNS.md`
- Add an entry whenever a decision made in one project
  should inform future projects
- Add to LESSONS.md when something caused a real problem
  and the fix should be institutionalised

---

## Patterns

### Authentication
**Pattern:** [Describe your standard auth approach across projects]
**Reasoning:** [Why this approach]
**Stack-specific notes:**
- Web: [e.g., Always use Clerk unless project has strong reason not to]
- Native Mac: [e.g., Keychain for token storage, never UserDefaults]
**First established:** [Project name, date]
**ADR reference:** [Link to originating project ADR if exists]

---

### Error Handling — TypeScript
**Pattern:** [Describe your standard]
**Reasoning:**
**First established:** [Project, date]

---

### Error Handling — Rust
**Pattern:** [e.g., thiserror in libraries, anyhow at application boundary]
**Reasoning:**
**First established:** [Project, date]

---

### Environment Variables
**Pattern:** [Describe your standard across all projects]
- Always document in .env.example
- [Other conventions]
**First established:** [Project, date]

---

### CSS / Design Tokens
**Pattern:** [Describe your standard]
**First established:** [Project, date]

---

### Testing Philosophy
**Pattern:** [Describe what you test and what you don't across all projects]
**First established:** [Project, date]

---

### Shopify Integration
**Pattern:** [e.g., Always headless via Storefront API, never Liquid themes]
**Reasoning:**
**Caveats:** [When this rule has exceptions]
**First established:** [Project, date]

---

### Git Conventions
**Branch naming:** [e.g., feat/, fix/, chore/]
**Commit style:** [Conventional commits / other]
**PR process:** [Solo / team]
**First established:** [Project, date]

---

## Add New Pattern

<!-- Template for adding a new entry:

### [Pattern Name]
**Pattern:** [Describe it clearly enough that it can be followed without context]
**Reasoning:** [Why — not just what]
**Stack-specific notes:** [If it varies by language/framework]
**Exceptions:** [When this rule doesn't apply]
**First established:** [Project name, date]
**ADR reference:** [If a formal ADR exists in a project]

-->