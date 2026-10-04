# Phase 01 — Product Discovery & Delivery Plan

## Objective

Choose a product, understand what should actually be built, define a sensible product delivery roadmap, and finish with one authoritative PRD that can feed module-by-module engineering.

This phase is about **product decisions**.

Do not design technical architecture here.

Do not choose database schemas, API style, framework structure, deployment topology, state libraries, authentication implementation, queueing strategy, or other engineering details unless a product decision genuinely depends on them.

Architecture belongs to Phase 02, when the relevant module is being engineered.

---

# Stage 01 — Select Product Family + Model

Start from [`../opportunities/service-products.md`](../opportunities/service-products.md).

Choose:

1. one Product Family;
2. one Product Model / Variant.

Examples of distinct variants inside one family may include single-location, multi-branch, marketplace, independent-provider, or at-home models.

Record clearly:

- selected family;
- selected model;
- target market/geography when relevant;
- explicit adjacent models that are **not** part of this product.

### Done when

The project has one clear business/product model and will not silently drift into adjacent variants during discovery.

---

# Stage 02 — Product Conversation

Discuss the product until the intended experience and business behavior are clear enough to plan delivery.

The conversation should resolve what matters for the specific product, including:

- What problem are we solving?
- Who experiences the problem?
- What outcome should the product enable?
- Who are the actors?
- What does each actor need to do?
- What is the product responsible for?
- What is explicitly outside scope?
- What are the most important journeys?
- What business rules materially affect those journeys?
- What permissions/ownership boundaries matter?
- What failures or edge cases can change user rights or operational correctness?
- What should the first usable version prove?

Do not force a fixed questionnaire onto every product. Ask the questions that change the product.

Prefer concrete decisions over generic feature brainstorming.

### Useful outputs during the conversation

Temporary notes are fine, but Phase 01 does not require a separate permanent document for every topic.

Persist a separate artifact only when it will remain useful after the PRD exists.

### Done when

The user and guide can explain the product, its actors, its core behavior, and its boundaries without relying on vague assumptions.

---

# Stage 03 — Define Product Delivery Phases

Decide how the product should be delivered in product-specific phases/releases.

These are **Product Delivery Phases**, not playbook phases.

Example:

```text
Product Delivery Phase 1 — Core MVP
Product Delivery Phase 2 — Operational expansion
Product Delivery Phase 3 — Growth capabilities
```

There is no required number of product phases.

For each phase define:

- name;
- objective;
- customer/business value;
- what capabilities enter in that phase;
- what stays deferred;
- completion/exit condition.

### Planning depth rule

Fully plan the active delivery phase.

Keep later phases intentionally higher-level unless a future dependency must be decided now.

Do not over-specify future architecture or detailed feature behavior just because it may eventually be needed.

### Done when

The PRD can show a believable sequence from the first usable product to later planned capabilities, without pretending future work is already fully designed.

---

# Stage 04 — Decompose the Active Product Phase into Modules

Break the active Product Delivery Phase into coherent modules that can be engineered one at a time.

A module should own a meaningful product responsibility with a reasonably clear boundary.

Possible examples include:

- authentication and identity;
- service catalog;
- booking and availability;
- customer account;
- staff operations;
- management settings;
- payments;
- notifications;
- search;
- content management.

These are examples only.

Do not force them onto a product that needs different boundaries.

## Good module properties

A useful module:

- has one understandable product responsibility;
- has a clear reason to exist;
- exposes a relatively simple contract to the rest of the product;
- hides internal complexity where possible;
- can be discussed and implemented without reopening the entire product;
- has identifiable dependencies;
- has acceptance criteria based on observable behavior.

Avoid splitting purely by technical layer such as “database module”, “API module”, and “frontend module” when they are merely implementation layers of the same capability.

## For each active-phase module define

- module name;
- purpose;
- actors/users;
- capabilities it owns;
- important product rules;
- what it does **not** own;
- upstream/downstream dependencies;
- important cross-module interactions;
- acceptance outcome;
- status: planned / ready / in progress / complete / blocked.

Do not decide internal architecture here.

The detailed technical design of each module is deliberately deferred to Phase 02.

### Done when

The active product phase is decomposed enough that the next ready module can enter an engineering interview without asking “what product are we building?”

---

# Stage 05 — Write the Authoritative PRD

Synthesize the decisions into one readable PRD.

Preferred location:

`projects/<project-slug>/prd.md`

The PRD is the product authority for implementation.

It should be concise enough to remain usable and detailed enough to prevent product rediscovery during engineering.

## Required PRD structure

### 1. Product identity

- Product Family
- Selected Model / Variant
- Target market/geography when relevant
- One-paragraph product summary

### 2. Problem and desired outcome

- problem;
- who has it;
- current friction;
- intended outcome;
- assumptions that are not yet validated.

### 3. Users and actors

For each important actor:

- goal;
- capabilities;
- access/ownership boundary.

### 4. Product boundary

- in scope;
- explicitly out of scope;
- adjacent product models excluded.

### 5. Core product behavior

Capture the important journeys and business rules that implementation must preserve.

Do not turn this into technical architecture.

### 6. Product Delivery Roadmap

Use a table similar to:

| Product Delivery Phase | Objective | Main capabilities | Exit condition |
| --- | --- | --- | --- |
| 1 — ... | ... | ... | ... |
| 2 — ... | ... | ... | ... |

The number of phases is product-specific.

### 7. Active Delivery Phase

State which Product Delivery Phase is currently being built and what success for that phase means.

### 8. Active-Phase Module Map

Use a table similar to:

| Module | Purpose | Depends on | Status |
| --- | --- | --- | --- |
| M01 — ... | ... | ... | ready |
| M02 — ... | ... | ... | planned |

Module IDs are optional but useful for tracking.

### 9. Module Briefs

For every module in the active product phase include:

- purpose;
- actors;
- owned capabilities;
- important product rules;
- boundaries/non-responsibilities;
- dependencies/interactions;
- acceptance outcome.

Keep architecture open unless a technical constraint is already an unavoidable product requirement.

### 10. Cross-module invariants

Record product rules that multiple modules must preserve, such as:

- ownership;
- permissions;
- money semantics;
- appointment/order state semantics;
- time-zone rules;
- audit expectations;
- consistency requirements.

Only include what actually applies.

### 11. UX / surface summary

List the important user-facing and operational surfaces needed for the active product phase at a level sufficient to understand module responsibilities.

Do not fully design every screen unless the product requires that decision before engineering.

### 12. Open questions and assumptions

Distinguish:

- product questions that block engineering;
- assumptions that can be tested later;
- technical questions intentionally deferred to the relevant module's Phase 02 interview.

### 13. Phase 02 handoff

Identify:

- the first ready module;
- why it is ready;
- relevant PRD sections;
- any dependencies the engineering agent must inspect first.

---

# Phase 01 exit criteria

Phase 01 is complete when:

- one Product Family + Model is clearly selected;
- the product's purpose, actors, boundaries, and core behavior are understood;
- Product Delivery Phases are visible in the PRD;
- the active product phase is fully decomposed into modules;
- each active-phase module has a useful product brief;
- module dependencies are clear enough to choose the next ready module;
- no unresolved product question blocks the first engineering module;
- technical architecture questions are deliberately left for Phase 02 unless already constrained by the product;
- the PRD is persisted and linked from the project tracker.

Then proceed to [`02-module-engineering.md`](02-module-engineering.md).

---

# Phase principle

> **Discovery decides what the product must do. Engineering decides how each module should do it.**
