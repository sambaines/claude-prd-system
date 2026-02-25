# CLAUDE.md
<!-- This file is read at the start of every session.
     Keep it current. It is your standing orders.
     When in doubt about anything, check here first. -->

## Project Overview
[2–3 sentences: what this project is, who it's for, what stage it's at]

## Project Type
<!-- Choose one. This tells Claude which reasoning mode to apply. -->
[ ] Web — content site / marketing
[ ] Web — application (auth, data, user state)
[ ] Web — headless commerce (Shopify)
[ ] Native Mac — Electrobun
[ ] Native Mac — Rust
[ ] Systems / Game Engine — Rust
[ ] Game — web technologies
[ ] Game — Rust
[ ] Internal Tool — lightweight / throwaway
[ ] POC / Experiment

**Mode:** Full | Lean
<!-- Full: complete doc system (PRD, SPECS, DECISIONS, Tasks)
     Lean: BRIEF.md only. Use for POCs, internal tools, experiments. -->

---

## Docs Structure
- System overview: /docs/README.md
- [Full] PRD: /docs/PRODUCT.md
- [Full] Architecture spec: /docs/SPEC.md
- [Full] Feature specs: /docs/specs/
- [Full] Decision log: /docs/DECISIONS.md
- [Lean] Brief: /docs/BRIEF.md
- Active tasks: /docs/tasks/current.md
- Cross-project patterns: [/meta/PATTERNS.md if applicable]

---

## Tech Stack
<!-- Be explicit about what we use AND what we have ruled out.
     The "not X" framing is as important as the "yes X." -->

**Language(s):** [e.g., TypeScript — not JavaScript]
**Framework(s):** [e.g., Next.js 14 App Router — not Pages Router]
**Styling:** [e.g., Tailwind — not CSS modules, not styled-components]
**State management:** [e.g., Zustand — not Redux, not Context for global state]
**Data / DB:** [e.g., PostgreSQL via Prisma — not raw SQL]
**Auth:** [e.g., Clerk — do not implement custom auth]
**CMS:** [e.g., Sanity — not Contentful]
**Commerce:** [e.g., Shopify Storefront API v2024-01 — not Liquid theme]
**Native runtime:** [e.g., Electrobun — not Electron, not Tauri]
**Systems language:** [e.g., Rust stable — not nightly unless specified]
**Testing:** [e.g., Vitest + Playwright]
**Deployment:** [e.g., Vercel / App Store / crates.io]
**Package manager:** [e.g., pnpm — not npm, not yarn]

<!-- Delete rows that don't apply to this project type. -->

---

## Platform Constraints
<!-- Hard limits imposed by the platform, not by choice.
     Claude treats these as non-negotiable.
     See DECISIONS.md for why this platform was chosen. -->

<!-- Web: -->
- Target browsers: [e.g., last 2 versions, no IE]
- [If Shopify] API version locked to: [e.g., 2024-01]
- [If Shopify] Checkout extensibility: [UI Extensions only / no custom checkout]
- [If Shopify] Metafield strategy: [describe]

<!-- Native Mac: -->
- macOS minimum version: [e.g., 14.0 Sonoma]
- Sandbox: [Yes / No — affects file system, network, keychain access]
- Distribution: [App Store / Direct / Both]
- [If Electrobun] Bun version: [x.x.x]

<!-- Rust / Systems: -->
- Rust edition: [e.g., 2021]
- Target(s): [e.g., aarch64-apple-darwin, x86_64-unknown-linux-gnu]
- WASM target: [Yes / No]
- no_std: [Yes / No]

<!-- Game: -->
- Target platform(s): [Desktop / Web / Both]
- Renderer: [e.g., wgpu / WebGL / WebGPU]
- Performance budget: [e.g., 60fps at 1080p on M1 / target frame time Xms]

<!-- Delete sections that don't apply. -->

---

## Code Patterns
<!-- Patterns to follow consistently. State both the pattern and the reason. -->

**General:**
- [e.g., Explicit over implicit — avoid magic, favour readable over clever]
- [e.g., No magic numbers — use named constants]
- [e.g., All errors are handled explicitly — no silent catches]

**TypeScript (if applicable):**
- [e.g., Strict mode on — no `any`, no `as` casting without comment]
- [e.g., Zod for all external data validation before it enters the app]
- [e.g., Named exports only — no default exports except pages/routes]

**Rust (if applicable):**
- [e.g., Use thiserror for error types, anyhow for application-level errors]
- [e.g., Prefer Result over panic in library code]
- [e.g., Document all public API items]
- [e.g., No unwrap() in production paths — use expect() with message or handle]

**CSS / Styling (if applicable):**
- [e.g., Mobile-first breakpoints]
- [e.g., Design tokens via CSS custom properties, not hardcoded values]

---

## File & Folder Conventions
- [e.g., Feature folders not type folders: /features/auth not /components/auth]
- [e.g., kebab-case for files, PascalCase for components, snake_case for Rust]
- [e.g., Co-locate tests with source: auth.ts + auth.test.ts]
- [e.g., Index files only for public API of a module, not for convenience]

---

## Environment & Secrets
<!-- Prevents credentials ever being hardcoded. -->

- Env vars via: [e.g., .env.local (dev) / Vercel env (prod) / Doppler]
- Required env vars documented in: [e.g., .env.example at project root]
- Never hardcode: API keys, tokens, connection strings, secrets of any kind
- Keychain (native apps): [describe pattern if applicable]
- Claude should never output a real secret in any file or suggestion

---

## Content Model (if applicable)
<!-- For content-heavy projects. Delete if not relevant. -->
See /docs/SPEC.md#content-model for full content type definitions.
CMS: [Platform]
Key content types: [list briefly, full detail in SPEC]

---

## What Requires Human Approval Before Proceeding
<!-- Claude stops and asks rather than deciding unilaterally. -->
- Any change to the database schema or content model
- Adding a new dependency (any language)
- Changes that affect a public API or interface contract
- Anything touching auth, payments, or user data
- Resolving any Open Question from a spec
- Deviating from a pattern in this file
- Any decision that should be logged as an ADR

---

## Known Gotchas
<!-- Things that have caused problems or are non-obvious.
     Add to this list during development — don't just fix and forget. -->
- [e.g., Dates are stored UTC, displayed in user timezone — don't conflate]
- [e.g., The legacy X module uses a different error shape — see spec note]

---

## What Good Looks Like Here
- Optimise for: [e.g., readability / performance / rapid iteration]
- This codebase is: [e.g., production / prototype / personal / client]
- When in doubt: [e.g., do less and ask rather than over-engineer]
- Code review standard: [e.g., Solo project — clarity over formality /
  Team project — changes need to be reviewable by others]