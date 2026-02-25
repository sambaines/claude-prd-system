# Architecture Spec
**Project:** [Project Name]
**Version:** v1.0
**Last Updated:** [YYYY-MM-DD]
**Status:** Draft | Active
**PRD reference:** /docs/PRODUCT.md
**Project type:** [from CLAUDE.md]

---

## ⚠️ Claude: Read This First
This is the implementation contract for the overall system.
Architectural decisions here take precedence over in-session suggestions.
If you believe something here is wrong or outdated, flag it — don't silently work around it.
Sections marked [OPTIONAL — not applicable] have been intentionally omitted.
Feature-level detail lives in /docs/specs/[feature].md, cross-referenced from here.

---

## 1. System Overview
[3–5 sentences describing the overall architecture.
How do the major pieces fit together? What is the data flow at a high level?]

---

## 2. Repository Structure
```
/project-root
├── CLAUDE.md
├── CHANGELOG.md
├── /docs
│   └── [doc system]
└── /src
    └── [describe your structure here]
```

---

## 3. Core Dependencies
<!-- The load-bearing dependencies. Not every package — just the ones
     that shape architecture. Explain why each was chosen.
     Link to relevant ADR if the choice was significant. -->

| Dependency | Purpose | Version | ADR |
|-----------|---------|---------|-----|
| [name] | [why] | [x.x.x] | [ADR-###] |

---

## 4. Data Model
<!-- Top-level entities and their relationships.
     Feature-level detail lives in feature specs.
     Claude treats this as authoritative schema. -->
```typescript
// or Rust structs, or plain description — match your stack
interface [Entity] {
  id: string;
  [field]: [type]; // [description]
}
```

---

## 5. Feature Specs Index
<!-- Master list of all feature specs and their status. -->

| Spec | File | Status |
|------|------|--------|
| [Feature name] | /docs/specs/[name].md | Draft / Active / Complete |

---

## [WEB] Section 6 — Web Architecture
<!-- Delete this entire section if not a web project. -->

### Routing strategy
[e.g., Next.js App Router, file-based, dynamic segments approach]

### Rendering strategy
| Route type | Strategy | Reason |
|-----------|----------|--------|
| [e.g., Marketing pages] | SSG | [SEO, no dynamic data] |
| [e.g., Dashboard] | SSR | [Auth-gated, personalised] |
| [e.g., Feed] | ISR (60s) | [Frequently updated] |

### Auth architecture
[Describe: provider, session strategy, protected route pattern]
See: [ADR-###]

### API layer
[REST / tRPC / GraphQL / Server Actions — and why]
Base path: `/api/`

### Error handling
[Describe global error boundary strategy, API error shapes]

---

## [SHOPIFY] Section 7 — Commerce Architecture
<!-- Delete this entire section if not a Shopify project. -->

### Integration type
[ ] Headless — Storefront API
[ ] Theme — Liquid
[ ] Hybrid

**API version:** [e.g., 2024-01] — See ADR-### for lock rationale.

### Storefront API usage
- Products & collections: [approach]
- Cart: [client-side / server-side / hybrid]
- Customer auth: [Storefront Customer API / third-party]
- Checkout: [Shopify-hosted — no custom checkout]

### Metafield strategy
[Describe how product/collection metafields are used and typed]

### Webhook handling
| Event | Handler | Purpose |
|-------|---------|---------|
| [e.g., orders/create] | [endpoint] | [why] |

### Sync & caching
[How product data is fetched, cached, and invalidated]

---

## [NATIVE MAC] Section 8 — Native App Architecture
<!-- Delete this entire section if not a native Mac project. -->

### Runtime
[ ] Electrobun — Bun version: [x.x.x]
[ ] Rust — see Systems section instead

### Process model
[Main process responsibilities vs renderer responsibilities]
[IPC pattern: how do they communicate?]

### Storage
| Data type | Storage mechanism | Reason |
|-----------|-----------------|--------|
| [e.g., User preferences] | [e.g., UserDefaults] | [why] |
| [e.g., Journal entries] | [e.g., SQLite via x] | [why] |

### Sandboxing & entitlements
- Sandbox enabled: [Yes / No]
- Required entitlements: [list]
- File system access: [describe scope]

### Auto-update strategy
[Describe update mechanism and distribution]

### macOS version targets
- Minimum: [e.g., 14.0]
- Tested on: [list]

---

## [RUST / SYSTEMS] Section 9 — Systems Architecture
<!-- Delete this entire section if not a Rust/systems project. -->

### Crate structure
```
/[project]
├── [crate-name]/     ← [responsibility]
│   └── src/
├── [crate-name]/     ← [responsibility]
└── Cargo.toml        ← workspace
```

### Error handling strategy
[e.g., thiserror for library errors, anyhow for binary/application errors]
[Describe error propagation philosophy]

### Memory model
[Ownership patterns used, where Arc/Rc appear and why, allocation strategy]

### Concurrency model
[Async runtime if any (Tokio?), threading model, shared state strategy]

### FFI / Interop
[Any C FFI, WASM exports, or language interop — describe boundary and safety approach]

### Performance targets
| Metric | Target | Measurement method |
|--------|--------|-------------------|
| [e.g., Frame time] | [e.g., <16ms] | [e.g., Tracy profiler] |
| [e.g., Memory ceiling] | [e.g., <512MB] | [e.g., Instruments] |

---

## [GAME] Section 10 — Game Architecture
<!-- Delete this entire section if not a game project. -->

### Engine / framework
[Custom engine / existing engine / raw APIs — see ADR-### for rationale]

### Renderer
[wgpu / WebGL / WebGPU / Canvas2D — and pipeline overview]

### Game loop
[Fixed timestep / variable / semi-fixed — describe update/render split]

### Entity / scene model
[ECS / OOP / other — describe how game objects are structured]

### Asset pipeline
[How assets are loaded, formats used, streaming strategy]

### Input handling
[Input abstraction layer, supported input methods]

### Persistence
[Save format, location, versioning strategy]

---

## [CONTENT] Section 11 — Content Model
<!-- Delete this entire section if not a content-heavy project. -->

### CMS / Source
[Platform, API type, version]

### Content types
| Type | Key fields | Relations | Source | Notes |
|------|-----------|-----------|--------|-------|
| [e.g., BlogPost] | title, slug, body, tags, publishedAt | Author | CMS | [notes] |
| [e.g., Project] | title, url, media[], tags | — | MDX | [notes] |

### Media handling
[Image CDN, formats, responsive strategy, video handling]

### Localisation
[Yes / No — if yes, describe strategy]

---

## 12. Testing Strategy
| Layer | Tool | Scope |
|-------|------|-------|
| Unit | [e.g., Vitest / cargo test] | [what] |
| Integration | [e.g., Playwright / supertest] | [what] |
| E2E | [e.g., Playwright] | [critical paths only] |
| Performance | [e.g., Lighthouse / Tracy] | [metrics] |

---

## 13. Open Questions
- [ ] [Question — do not resolve unilaterally]

---

## Changelog
| Date | Version | Change | Reason |
|------|---------|--------|--------|
| [YYYY-MM-DD] | v1.0 | Initial draft | — |