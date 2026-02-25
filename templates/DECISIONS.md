# Architecture Decision Records
**Project:** [Project Name]
**Last Updated:** [YYYY-MM-DD]

---

## ⚠️ Claude: Read This First
This is the historical record of significant decisions made during development.
Before suggesting an approach that involves a major architectural or product choice,
check here first. If a relevant ADR exists, respect it or explicitly flag that you
believe it should be revisited and why. Do not silently re-litigate closed decisions.

When a new decision is made during a session, remind the human to log it here.

---

## How to Use This File

**When to add an ADR:**
- A technology or library is chosen (or ruled out)
- A structural or architectural pattern is adopted
- A meaningful product or UX decision is locked in
- A previous decision is reversed or amended

**When NOT to add an ADR:**
- Routine implementation details
- Decisions that are trivially reversible
- Style/formatting choices (those live in CLAUDE.md)

**Status types:**
- `Active` — current and in force
- `Amended` — superseded by a later ADR (link to it)
- `Reversed` — no longer in effect (reason recorded)
- `Proposed` — under discussion, not yet locked in

---

## ADR Index

| ID | Title | Status | Date |
|----|-------|--------|------|
| [ADR-001](#adr-001) | [Title] | Active | [YYYY-MM-DD] |
| [ADR-002](#adr-002) | [Title] | Active | [YYYY-MM-DD] |

---

## Active Decisions

---

### ADR-001
**Title:** [Short descriptive title, e.g. "Use JWT over server-side sessions"]
**Date:** [YYYY-MM-DD]
**Status:** Active
**Decided by:** [Human / Claude / Joint]
**Affects:** [Files or areas: /docs/specs/auth.md, /src/lib/auth/]

#### Context
<!-- What situation required a decision? What options were on the table?
     What constraints or pressures shaped the choice? -->

#### Decision
<!-- What was decided, stated plainly and unambiguously. -->

#### Reasoning
<!-- Why this option over the alternatives?
     Vague reasoning is useless to future readers — be specific. -->

#### Tradeoffs Accepted
<!-- Known downsides of this decision. What did we give up?
     Claude should not try to quietly "fix" these without flagging this ADR. -->
- [Downside 1]
- [Downside 2]

#### Consequences
<!-- What does this decision constrain or enable going forward?
     What follow-on decisions does it force or foreclose? -->

#### Alternatives Considered
| Option | Why rejected |
|--------|-------------|
| [Alternative 1] | [Reason] |
| [Alternative 2] | [Reason] |

---

### ADR-002
**Title:** [Title]
**Date:** [YYYY-MM-DD]
**Status:** Active
**Decided by:** [Human / Claude / Joint]
**Affects:** [Files or areas]

#### Context

#### Decision

#### Reasoning

#### Tradeoffs Accepted
-

#### Consequences

#### Alternatives Considered
| Option | Why rejected |
|--------|-------------|
| [Alternative 1] | [Reason] |

---

## Deferred / Unresolved

<!-- Questions that need deciding but aren't blocking current work.
     Review this section before planning new features or milestones.
     When a deferred question is answered, create an ADR above and remove it from here. -->

### DEFERRED-001
**Topic:** [What needs deciding]
**Context:** [Why it matters]
**Options under consideration:**
- Option A: [brief description]
- Option B: [brief description]
**Blocking:** [What can't be done until resolved, or "Nothing immediately"]
**Deferred because:** [Why not deciding now — lack of info, not critical yet, waiting on X]
**Revisit by:** [Date or milestone]
**Origin:** [Spec/PRD section that raised this]
**Added:** [YYYY-MM-DD]

---

<!-- Template for new deferred questions:

### DEFERRED-###
**Topic:**
**Context:**
**Options under consideration:**
-
**Blocking:**
**Deferred because:**
**Revisit by:**
**Origin:**
**Added:**

-->

---

## Amended & Reversed Decisions
<!-- Move ADRs here when no longer active.
     Always preserve the original — never delete history. -->

### ADR-000 [AMENDED by ADR-###]
**Title:** [Original title]
**Original date:** [YYYY-MM-DD]
**Amended:** [YYYY-MM-DD] by [ADR-###]

#### Original Decision
[Preserved verbatim]

#### Why It Changed
[New information, user feedback, scaling issue, changed requirements, etc.]