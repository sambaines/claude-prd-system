# Current Task
**Session date:** [YYYY-MM-DD]
**Working on:** [Feature or area name]
**Spec reference:** [/docs/specs/feature-name.md]
**PRD reference:** [/docs/PRODUCT.md#section]
**Related ADRs:** [ADR-###, ADR-###]

---

## ⚠️ Claude: Read This First
This is the active work queue for this session. Start here, not in the codebase.
Read the referenced spec and any linked ADRs before touching any files.
The "Do Not Touch" section is a hard boundary for this session.
When this task is complete, help me update this file and flag anything
that needs to be logged in DECISIONS.md.

---

## Context
<!-- 3–5 sentences. Where did we leave off? What decisions were made
     last session that Claude needs to carry forward?
     Assume Claude has no memory of previous sessions. -->

---

## Assumptions for This Session
<!-- State your expectations about current system state.
     If an assumption turns out to be false mid-session, surface it immediately
     rather than working around it silently. -->
- [ ] [e.g., Database migrations from last session have been applied]
- [ ] [e.g., Auth is working — not in scope to debug this session]
- [ ] [e.g., The feature branch from last session is still checked out]

---

## Goal for This Session
<!-- One clear sentence. What does done look like today?
     Be specific enough that we can verify it at the end. -->

**Done looks like:** [Concrete, verifiable statement]

---

## Task Breakdown
<!-- Ordered list of discrete steps. Claude works through these in sequence
     and checks in before moving to the next if there's any ambiguity. -->

- [ ] Step 1: [What + where]
- [ ] Step 2: [What + where]
- [ ] Step 3: [What + where]

---

## Relevant Files
<!-- The files Claude should read and may edit this session.
     Being explicit here prevents Claude from wandering into unrelated areas. -->

**Read:**
- `/docs/specs/[feature].md`
- `/src/[relevant module]`

**Will edit:**
- `/src/[file]` — [why]
- `/src/[file]` — [why]

---

## Do Not Touch This Session
<!-- Hard boundaries. Claude does not modify these without explicit instruction. -->
- `/src/[sensitive file]` — [reason, e.g., "another branch is touching this"]
- Database schema — requires migration review first

---

## Known Constraints for This Session
<!-- Anything that limits how Claude should approach this task today.
     e.g., time constraints, stability requirements, WIP dependencies. -->
- [e.g., Don't refactor anything outside the immediate task scope]
- [e.g., This will be code-reviewed — prioritise readability]

---

## Open Questions (Session-Specific)
<!-- Tactical questions that need answering before Claude can proceed.
     These are in-the-moment blockers, not long-term concerns.
     If a question won't be answered this session, promote it to the
     appropriate place: feature spec or DECISIONS.md Deferred. -->
- [ ] [Question — what information is needed to unblock it]

---

## End of Session Checklist
<!-- Run through this together at the end of each session. -->

### Document Updates
- [ ] Task steps above marked complete or carried forward
- [ ] Any new decisions logged (or flagged to log) in DECISIONS.md
- [ ] Any spec changes required noted in the relevant spec file
- [ ] PRD changelog updated if scope or requirements shifted
- [ ] New tech debt surfaced? → Log in TECH-DEBT.md
- [ ] Lessons learned? → Consider adding to /meta/LESSONS.md

### Open Questions Triage
- [ ] Session-specific questions in current.md:
  - [ ] Tactical questions → resolved and removed
  - [ ] Feature-level questions → moved to relevant spec
  - [ ] Architectural questions → moved to DECISIONS.md Deferred
- [ ] Any feature spec Open Questions now answered? → Update spec, remove question
- [ ] Any DEFERRED questions now decidable? → Create ADR

### Next Session Prep
- [ ] This file updated with next session's starting context
- [ ] Anything surprising or broken that warrants a new ADR?

---

## Carry Forward / Next Session
<!-- Notes for the next session's context section.
     Written at the END of the current session, not the start. -->

[To be filled in at session close]