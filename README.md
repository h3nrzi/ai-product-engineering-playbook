# AI Product Engineering Playbook

Single source of truth for a reusable AI-assisted product engineering workflow focused on service-oriented products.

## Workflow

```text
01 Product Discovery & Delivery Plan
        ↓
02 Module-by-Module Engineering
        ↓
03 Visual Redesign & UI Polish (if needed)
```

The workflow intentionally separates three kinds of work:

- **Product decisions** belong in Discovery.
- **Architecture and implementation decisions** happen module by module during Engineering.
- **Visual redesign** happens after functional coherence exists, when the product actually needs it.

Phase 02 uses the current Matt Pocock / AI Hero methodology from <https://www.aihero.dev/>. Phase 03 uses Google Stitch (<https://stitch.withgoogle.com/>) when the implemented product needs stronger visual design.

## Repository

- [`MASTER.md`](MASTER.md) — role and authoritative workflow for Guide LLMs
- [`phases/`](phases/README.md) — phase-by-phase procedure
- [`opportunities/`](opportunities/README.md) — service-product opportunity library
- [`opportunities/service-products.md`](opportunities/service-products.md) — service products and their models, ordered roughly by demand in Iran
- [`projects/`](projects/README.md) — project trackers and durable project artifacts
- [`templates/project-tracker.md`](templates/project-tracker.md) — tracker template

## Start a project

1. Read [`MASTER.md`](MASTER.md).
2. Open [`opportunities/service-products.md`](opportunities/service-products.md).
3. Start [Phase 01](phases/01-product-discovery.md).
4. Select a **Product Family** and one specific **Product Model / Variant**.
5. Discuss the product until its problem, actors, scope, important behavior, delivery roadmap, and active-phase modules are clear.
6. Persist the final authoritative PRD under `projects/<project-slug>/prd.md` (or migrate an existing project PRD to the same structure).
7. Create/update `projects/<project-slug>.md` from the tracker template.
8. Create the implementation repository when Phase 02 is ready to begin.
9. Engineer one ready PRD module at a time using [Phase 02](phases/02-module-engineering.md).
10. When the functional product is coherent, use [Phase 03](phases/03-visual-redesign.md) only if the visual result still needs redesign/polish.

## PRD principle

The PRD must show the product's own delivery roadmap.

Example:

```text
Product Delivery Phase 1 — Core MVP
Product Delivery Phase 2 — Operational expansion
Product Delivery Phase 3 — Growth
```

Only the active product delivery phase is normally decomposed into detailed modules such as authentication, booking, customer account, staff operations, etc. The module list must be derived from the product rather than copied from a generic template.

This keeps future phases flexible and moves architecture decisions closer to implementation.

## Project documentation policy

Keep durable product intent in this playbook repository.

Preferred shape:

```text
projects/<project-slug>.md
projects/<project-slug>/prd.md
```

Additional product documents should exist only when they add durable value.

Engineering artifacts such as ADRs, specs, tickets, code-review evidence, and implementation details may live in the implementation repository, where the AI Hero workflow can read and update them alongside the code.

## Principle

> Discover the product first. Decide architecture only when a module needs it. Polish the interface after the product works.
