# AI Product Engineering Playbook

Single source of truth for a reusable AI-assisted product engineering workflow focused on service-oriented products.

## Workflow

```text
Product Family + Model Selection
        ↓
Product Discovery & Product Design
        ↓
Base44 Prototype
        ↓
React Frontend Completion
        ↓
React → Next.js Refactor
        ↓
Full-Stack Next.js Completion
```

The first phase deliberately invests in professional product discovery and produces the PRD plus the prompts used by Base44. Later phases progressively transform that intent into a prototype, an engineered React frontend, a Next.js application, and finally a real full-stack product.

Engineering phases use a lightweight Matt Pocock-style pattern where appropriate:

`Wayfinder → to-spec → to-tickets → implementation`

## Repository

- [`MASTER.md`](MASTER.md) — role and authoritative workflow for Guide LLMs
- [`phases/`](phases/README.md) — phase-by-phase procedure
- [`opportunities/service-products.md`](opportunities/service-products.md) — comprehensive service-product family catalog, Iran demand ordering, and model variants
- [`opportunities/iran-demand-methodology.md`](opportunities/iran-demand-methodology.md) — demand/digital-maturity methodology and research snapshot
- [`projects/`](projects/README.md) — project trackers plus authoritative project-specific documentation/artifacts
- [`templates/project-tracker.md`](templates/project-tracker.md) — tracker template

## Start a project

1. Read [`MASTER.md`](MASTER.md) for the guide role and workflow authority.
2. Select a **Product Family** from the [service-product library](opportunities/service-products.md).
3. Select a specific **Product Model / Variant** from that family. Do not begin Phase 01 while materially different models remain unresolved.
4. Prepare the Selected Opportunity Brief described in [Phase 01](phases/01-product-discovery.md), recording the stable product-family ID, selected model, target market when relevant, and explicit boundaries against adjacent variants.
5. Copy the [tracker template](templates/project-tracker.md) to `projects/<project-slug>.md`, create `projects/<project-slug>/`, persist the selected opportunity brief there, and add the tracker to the [project index](projects/README.md). Mark the family `selected`; use `in-progress` once project work begins.
6. Follow Phase 01 and persist each approved stage artifact under the project directory before considering that stage complete.
7. Advance through later phases only when the active phase guide's exit criteria are met and the tracker reflects the current state.

## Project documentation policy

This repository is both the reusable playbook and the authoritative archive for project documentation produced by the workflow.

Store project-specific briefs, `product-design/` artifacts, prototype handoffs, specs, tickets, and verification/evidence documents under:

`projects/<project-slug>/`

Application implementation code may live in a separate product repository later if needed, but that does not change where the playbook's project documentation is stored.

## Opportunity-library principle

A broad service category is not automatically a project definition. For example, `BEAUTY-SALON` can become a men's single barbershop, women's single salon, multi-branch salon, marketplace, independent-specialist product, or at-home service. Those models can have materially different actors, workflows, trust boundaries, logistics, and monetization.

The library therefore separates:

```text
Stable Product Family
        +
Selected Product Model / Variant
        ↓
Actual project entering Phase 01
```

Iran demand tier and digital maturity are research metadata for prioritization, not substitutes for product discovery.

## Principle

Product discovery should be deep enough to design the right product. Engineering workflow should then remain structured but lightweight enough to keep building momentum.
