# Project Brief: [Project Name]
**Date:** [YYYY-MM-DD]
**Mode:** Lean
**Type:** POC | Internal Tool | Experiment
**Estimated scope:** [Hours / Days / Weeks]

---

## ⚠️ Claude: Read This First
This is a lean-mode project. There is no full PRD or spec structure.
This document is the single source of truth for what we're building.
Do not over-engineer. Prefer the simplest implementation that satisfies
the goals below. Flag anything that would significantly expand scope.
CLAUDE.md at project root still applies — check it first.

---

## What Is This
[2–4 sentences. What does this do? Why does it exist?
Be specific enough that we can tell when we're done.]

---

## Goals
<!-- Keep it tight. 1–3 goals max for a lean project. -->
- [ ] Goal 1
- [ ] Goal 2

## Non-Goals
<!-- Explicitly rule out anything that could creep in. -->
- Not trying to [X]
- [Y] is out of scope — if it comes up, flag it rather than building it

---

## Definition of Done
<!-- For a POC: "Hypothesis validated" is a legitimate answer.
     For a tool: describe the minimum useful outcome. -->
This is done when:
- [ ] [Criterion 1]
- [ ] [Criterion 2]

---

## Tech Stack
<!-- Even throwaway projects need this.
     What are we using? What are we explicitly not using? -->
- [e.g., Vanilla JS — no framework overhead for this scale]
- [e.g., Rust + wgpu — no game engine abstraction, raw GPU]
- [e.g., Single HTML file — no build step]

---

## Constraints
<!-- Hard limits: time, platform, dependencies, resources. -->
- [e.g., Must run in browser with no install]
- [e.g., Target: aarch64-apple-darwin only]
- [e.g., No external API calls — fully offline]
- [e.g., Complete in one session]

---

## Known Risks / Open Questions
<!-- Things that might block progress or require a decision.
     Claude flags these rather than deciding unilaterally. -->
- [ ] [Risk or question]

---

## Notes & Findings
<!-- Append findings during development.
     For POCs especially: capture what was learned, not just what was built.
     This becomes the carry-forward context if the POC grows into a full project. -->

[YYYY-MM-DD] [Finding or decision made during this session]