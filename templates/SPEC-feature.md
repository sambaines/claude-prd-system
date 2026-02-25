# Feature Spec: [Feature Name]
**Spec ID:** SPEC-[###]
**Version:** v1.0
**Last Updated:** [YYYY-MM-DD]
**Status:** Draft | Approved | In Progress | Complete
**PRD reference:** /docs/PRODUCT.md#[section]
**Architecture spec:** /docs/SPEC.md#[section]
**Related ADRs:** [ADR-###]
**Related specs:** [/docs/specs/other.md]
**Project type:** [from CLAUDE.md]

---

## ⚠️ Claude: Read This First
This is the implementation contract for this feature.
Do not deviate from data models or interface contracts defined here without flagging.
Sections marked [OPTIONAL — not applicable] have been intentionally omitted.
Open Questions at the bottom are unresolved — do not make assumptions to fill them.
Cross-reference the PRD and any listed ADRs before making product-level judgements.

---

## 1. Overview
[2–3 sentences: what this feature does and why it exists.
Should connect clearly to the user journey it serves.]

---

## 2. Scope
**In scope:**
- [X]

**Out of scope:**
- [Y] — handled by [other spec / future]

---

## 3. Data Model
<!-- Claude treats this as authoritative. Be explicit about
     nullability, defaults, and units where relevant. -->
```typescript
// TypeScript / Rust / plain description — match your stack
interface [Entity] {
  id: string;         // UUID
  [field]: [type];    // [description, nullable?, default?]
  createdAt: Date;
  updatedAt: Date;
}
```

---

## [WEB/API] Section 4 — API Contract
<!-- Delete if not a web/API feature. -->

### [Endpoint name]
**Method:** GET | POST | PUT | PATCH | DELETE
**Path:** `/api/[path]`
**Auth required:** Yes | No

**Request:**
```typescript
{ [field]: [type]; }
```

**Response (success):**
```typescript
{ [field]: [type]; }
```

**Error states:**
| Code | Condition | Message |
|------|-----------|---------|
| 400 | [condition] | [message] |
| 401 | Unauthorized | — |
| 404 | Not found | [message] |

---

## [NATIVE/SYSTEMS] Section 4 — Module Interface
<!-- Delete if not a native or Rust feature. -->

### Public API
```rust
// or TypeScript module exports
pub fn [function_name]([params]) -> Result<[type], [ErrorType]>;
pub struct [TypeName] { ... }
```

### IPC / Inter-process (if Electrobun)
**Channel:** `[channel-name]`
**Direction:** Main → Renderer | Renderer → Main | Bidirectional
**Payload:**
```typescript
{ [field]: [type]; }
```

### Platform APIs used
| API | Purpose | Entitlement required |
|-----|---------|---------------------|
| [e.g., FileManager] | [why] | [e.g., com.apple.security.files.user-selected.read-write] |

---

## [GAME] Section 4 — System Interface
<!-- Delete if not a game feature. -->

### ECS components (if applicable)
```rust
#[derive(Component)]
struct [ComponentName] {
  [field]: [type],
}
```

### System signature
```rust
fn [system_name](
  [query params]
) { ... }
```

### Events
| Event | Payload | Producer | Consumer |
|-------|---------|---------|---------|
| [EventName] | [type] | [system] | [system] |

### Performance constraints
- Max entities this system should touch per frame: [N]
- Acceptable frame time budget: [Xms]

---

## [SHOPIFY] Section 4 — Commerce Interface
<!-- Delete if not a Shopify feature. -->

### Storefront API queries / mutations used
```graphql
query [QueryName] { ... }
mutation [MutationName] { ... }
```

### Metafields accessed
| Owner type | Namespace | Key | Type |
|-----------|-----------|-----|------|
| [Product] | [ns] | [key] | [type] |

### Webhook dependencies
[Does this feature require any webhooks? Which events?]

---

## 5. Component / Module Breakdown
<!-- Discrete pieces of this feature and their responsibilities. -->
- `[Name]` — [responsibility]
- `[Name]` — [responsibility]

---

## 6. State & Side Effects
<!-- What state does this feature own?
     What side effects does it produce (emails, events, files, cache)?
     What external systems does it touch? -->

---

## 7. Error Handling & Edge Cases
<!-- Claude should not invent handling for unlisted cases without flagging. -->

| Scenario | Expected behaviour |
|----------|--------------------|
| [Edge case] | [How to handle] |

---

## 8. Testing Requirements
**Unit tests required for:**
- [ ] [Function / component]

**Integration tests required for:**
- [ ] [Flow / endpoint]

**Explicitly out of scope for testing:**
- [X] — [reason]

---

## 9. Open Questions
<!-- Unresolved. Claude flags rather than decides. -->
- [ ] [Question — owner, deadline if known]

---

## Changelog
| Date | Version | Change | Reason |
|------|---------|--------|--------|
| [YYYY-MM-DD] | v1.0 | Initial draft | — |