# Two-role discovery handoff — Product Manager → Tech Lead

## Purpose

Separate decisions about **what the product must do** from decisions about **how engineering will deliver it**. The same installed `grill-with-docs` methodology can be run twice with different decision authority, source documents, outputs and exit gates. This is a **workflow pattern inside the existing three playbook phases**, not a fourth playbook phase and not a requirement to interview every small module twice.

## Where it fits

```text
Phase 01 — Product Discovery & Delivery Plan
  Product scope discussion → approved immutable PRD
  Optional detailed V1 policy discovery using grill-with-docs
  Product owner confirms the complete product behavior contract
  Artifacts: product decision log + consolidated product policies + glossary
     ↓ explicit product handoff
Phase 02 — Module-by-Module Engineering
  Tech Lead / engineering discovery using grill-with-docs
  Evaluate architecture and engineering alternatives against approved contract
  Artifacts: qualifying architectural ADRs + domain vocabulary + technical decisions
     ↓ explicit technical shared-understanding approval
  to-spec (when effort warrants) → to-tickets → implementation → review
     ↓
Phase 03 — Visual Redesign & Polish, only if needed
```

## Product-discovery interview — PM / Product Owner

**Authority:** Product Owner approves product behavior; the guide advises; the Codex executor conducts the actual skill interview when assigned. The approved PRD remains the immutable scope baseline.

**When useful:** A product has substantive open policy questions (e.g. role permissions, numerical limits, retention, failure/retry behavior, observable lifecycle). Do not force an extra interview onto a project whose approved PRD and module briefs already give sufficient product clarity.

**Run:** `grill-with-docs` with `grilling` for complete dependency-ready question frontiers and `domain-modeling` for precise vocabulary. Ask independent questions together in numbered rounds; wait for explicit user approval of each round.

**Durable implementation-repository outputs, where useful:**

- `docs/product/v1-product-discovery.md` — complete product decision/approval history and relevant question context.
- `docs/product/v1-product-policies.md` — consolidated, readable approved V1 behavior contract.
- `GLOSSARY.md` — canonical domain terms, **not** a store of implementation or numerical product policy.
- `docs/product/prd.md` — read-only copy pinned to the canonical approved PRD; **never rewrite it** merely to settle policy details.

These two `v1-*` files are **project-specific additional documents**, not mandatory outputs prescribed by the original `grill-with-docs` skill. They exist when they materially help preserve many explicit product choices; keep the format proportional to project scale. Product rules are not automatically architecture ADRs.

**Exit gate:** The product-decision frontier is empty, any deferred/open policy is stated explicitly, product/PRD conflicts are resolved with owner approval rather than silent scope expansion, and the Product Owner confirms final shared understanding. Per-round approvals alone do **not** close discovery.

## Engineering-discovery interview — Tech Lead / Software Architect

**Authority:** Engineering agent researches real options and recommends design; user approves consequential decisions with the guide reviewing trade-offs and PRD compliance. The PM-approved product contract is an input, **not** a design proposal to change silently.

**Read first:** Immutable PRD, approved policy contract (if present), product decision log, glossary, current codebase/constraints, existing engineering ADRs.

**Run:** `grill-with-docs` afresh with an **engineering design tree**: module/service boundaries, persistence and concurrency, recovery/inactivity evidence, media processing model, interfaces, deployment/runtime, failure behavior, security and testing **as relevant**. Questions must be about options that are not already fixed as product behavior. Codex asks the entire ready frontier each round, proposes a reasoned default, and waits for user approval.

**Outputs:**

- `GLOSSARY.md` updated only for genuinely new or sharpened domain terms.
- `docs/adr/NNNN-*.md` for **qualifying** architecture decisions, applying `domain-modeling`'s three-part test: hard to reverse; surprising without context; meaningful alternatives/trade-off. Do not manufacture an ADR for every question.
- Engineering decision context in the eventual spec or dedicated engineering notes if not ADR-worthy. **Never** rewrite the Product Policies as a technical design notebook.

**Conflict protocol:** If an option cannot meet the PRD or approved product policy, state the concrete conflict and options; route any proposed product change back to the Product Owner for explicit approval. The Tech Lead must not silently weaken acceptance, retention, rights, result semantics or other product guarantees to simplify architecture.

**Exit gate:** All necessary engineering decisions are resolved for the chosen scope/module, dependencies and risks are understood, ADRs and glossary are up to date, user confirms shared understanding. Then choose the smallest execution path: `implement` for genuinely bounded work; `to-spec` then `to-tickets` for larger cross-session efforts; continue with review/evidence.

## Ownership and continuity

The central playbook owns this **reusable policy and role boundary**. Each implementation repository owns its project-specific discovery records, ADRs, specs, tickets and code. The guide helps the learner review Codex recommendations; it does not start a competing interview or implement without explicit reassignment.

### Example: MediaForge

- PRD: [D03-P02 MediaForge approved product scope](https://github.com/h3nrzi/nodejs-backend-engineering-handbook/blob/main/domains/03-nodejs-internals/projects/p02-mediaforge-asset-processing-prd.md).
- PM-style product discovery: 59 decisions (Q1–Q59), [discovery record](https://github.com/h3nrzi/mediaforge/blob/main/docs/product/v1-product-discovery.md), [consolidated policies](https://github.com/h3nrzi/mediaforge/blob/main/docs/product/v1-product-policies.md), [glossary](https://github.com/h3nrzi/mediaforge/blob/main/GLOSSARY.md).
- **Current evidence:** Codex recorded all 59 approvals and an empty product-question frontier; its consolidated policy file still says **final product-owner shared-understanding confirmation pending**. This must be explicitly closed before treating Product Discovery as signed off.
- Next, when that gate is closed, start a **separate Tech Lead-led `grill-with-docs`** against the frozen product contract. Eligible technical ADRs belong in MediaForge, not the playbook. For an effort of this scope, `to-spec` following settled technical discovery is appropriate, subject to actual size/readiness.

This MediaForge example does not replace the playbook's product-specific delivery phases or its default module-by-module engineering workflow.
