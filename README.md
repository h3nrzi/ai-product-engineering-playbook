# AI Product Engineering Playbook

Single source of truth for a reusable AI-assisted product engineering workflow focused on service-oriented products.

## Workflow

```text
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
- [`opportunities/service-products.md`](opportunities/service-products.md) — 40 service-product opportunities and selection guidance
- [`projects/`](projects/README.md) — trackers for real projects using the playbook
- [`templates/project-tracker.md`](templates/project-tracker.md) — tracker template

## Start a project

1. Read [`MASTER.md`](MASTER.md) for the guide role and workflow authority.
2. Select an opportunity from the [service-product library](opportunities/service-products.md) and prepare the selected opportunity brief described in [Phase 01](phases/01-product-discovery.md).
3. Copy the [tracker template](templates/project-tracker.md) to `projects/<project-slug>.md`, link the selected opportunity and available product artifacts, and add the tracker to the [project index](projects/README.md). Mark the opportunity as `selected`; use `in-progress` once project work begins.
4. Follow Phase 01, then advance through the remaining phases when each guide's exit criteria are met. Update the tracker and opportunity status as work progresses.

Keep reusable guidance and opportunity descriptions in this repository. Store project-specific briefs, `product-design/` artifacts, prototype handoffs, specs, tickets, and implementation evidence in the product repository; link them from the tracker. If that repository does not exist yet, record the repository link as pending and move any initial project artifacts there once it is created.

## Principle

Product discovery should be deep enough to design the right product. Engineering workflow should then remain structured but lightweight enough to keep building momentum.
