# Product Requirements Document
**Project:** [Project Name]
**Version:** v1.0
**Last Updated:** [YYYY-MM-DD]
**Status:** Draft | Active | Superseded
**Project type:** [from CLAUDE.md]
**Mode:** Full

---

## ⚠️ Claude: Read This First
This is the source of truth for *why* this product exists and *what* it does.
Do not make architectural or implementation decisions that contradict this document.
If you identify a conflict between this PRD and a spec or task, flag it — do not
silently pick a side.
All changes are versioned in the Changelog at the bottom — read it before
assuming anything is current.

---

## 1. Problem Statement
**The problem:** [One clear sentence]
**Who has it:** [User type / persona]
**Current workaround:** [How they solve it today]
**Why now:** [Why this is worth solving at this moment]

---

## 2. Goals
- [ ] Goal 1
- [ ] Goal 2

---

## 3. Non-Goals
<!-- As important as Goals. Prevents scope creep.
     Tells Claude what not to build toward. -->
- This product will not [X]
- [Y] is out of scope until v2

---

## 4. Definition of Done
<!-- Project-level, not session-level.
     What does "this project is complete" actually mean?
     For POCs: "hypothesis validated" may be sufficient.
     For shipped products: be specific about quality bar. -->

This project is done when:
- [ ] [Criterion 1 — e.g., All must-have features from section 6 are complete]
- [ ] [Criterion 2 — e.g., Deployed to production and accessible at URL]
- [ ] [Criterion 3 — e.g., Core user journeys work on target platforms]
- [ ] [Criterion 4 — e.g., No known P1 bugs]

---

## 5. Users
**Primary user:** [Role, context, technical level, key needs]
**Secondary user:** [If any]
**Environment:** [Web / Mac app / API / etc.]

---

## 6. Core User Journeys
<!-- 2–4 outcomes. Not features — outcomes.
     "A [user] should be able to [action] so that [outcome]." -->
1. A [user] should be able to [action] so that [outcome].
2. A [user] should be able to [action] so that [outcome].

---

## 7. Features
<!-- Each feature traces back to at least one journey.
     If a feature doesn't serve a journey, question whether it belongs. -->

### 7.1 [Feature Name]
**Priority:** Must-have | Should-have | Nice-to-have
**Status:** Not started | In progress | Complete
**Serves journey:** [#]
**Description:** [Plain language]
**Acceptance criteria:**
- [ ] Criterion 1

---

## 8. Milestones
<!-- Group features into phases to define delivery order.
     Phases don't need dates — relative ordering is enough.
     Claude: complete earlier phases before starting later ones unless told otherwise. -->

| Phase | Description | Features | Target | Status |
|-------|-------------|----------|--------|--------|
| Phase 1 | [name / theme] | [7.1, 7.2] | [date or milestone] | Not started |
| Phase 2 | [name / theme] | [7.3] | [—] | Not started |

---

## 9. Constraints & Assumptions
**Hard constraints:**
- [e.g., Must comply with GDPR]
- [e.g., Shopify checkout — no custom checkout logic]
- [e.g., App Store guidelines apply]

**Working assumptions:**
- [e.g., Users are on macOS 14+]
- [e.g., Auth handled by third-party provider]

---

## 10. Platform-Specific Considerations
<!-- Delete sections that don't apply. -->

**If Shopify:**
- Theme vs headless decision: [See ADR-###]
- Store currency / markets: [describe]
- Tax / shipping handled by: [Shopify native / custom]

**If native Mac app:**
- Distribution method: [App Store / direct]
- iCloud sync: [Yes / No]
- Offline capability: [Full / Partial / None]

**If content site:**
- CMS: [platform]
- Localisation required: [Yes / No]

**If game / engine:**
- Target platforms: [list]
- Multiplayer: [Yes / No]
- Persistence: [local save / cloud / none]

---

## 11. Success Metrics
- [e.g., 80% of users complete onboarding without support]
- [For POC: e.g., Hypothesis X confirmed or refuted with evidence]

---

## 12. Open Questions
<!-- Claude does not resolve these unilaterally. Flag and ask. -->
- [ ] [Question]

---

## Changelog
| Date | Version | Change | Reason | Impact |
|------|---------|--------|--------|--------|
| [YYYY-MM-DD] | v1.0 | Initial draft | — | — |