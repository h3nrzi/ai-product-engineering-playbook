# Project Trackers

Each product using this playbook gets one lightweight tracker here plus a project documentation directory under `projects/<project-slug>/`.

Projects now follow three authoritative playbook phases:

1. Product Discovery & Delivery Plan
2. Module-by-Module Engineering
3. Visual Redesign & UI Polish (when needed)

The tracker is navigation/context for Guide LLMs. The PRD is the product authority. Engineering artifacts may live in the implementation repository when that is where the AI Hero workflow operates.

## Current projects

- [`Women’s Beauty Salon Booking`](womens-beauty-salon-booking.md) — Barbershop / Beauty Salon Booking → **Women’s single-salon** — existing discovery work must be migrated to the new phased-PRD/module format before module engineering begins.

## Preferred project structure

```text
projects/
├── <project-slug>.md
└── <project-slug>/
    └── prd.md
```

Additional files/folders are optional and should exist only when they provide durable value.

Legacy project artifacts from older workflow versions may remain for historical/reference purposes, but the tracker must identify which PRD/module artifacts are currently authoritative.

## Add a project

1. Start Phase 01 and choose the Product Family + Model from [`../opportunities/service-products.md`](../opportunities/service-products.md).
2. Create `projects/<project-slug>/`.
3. Create/update `projects/<project-slug>/prd.md` as discovery progresses.
4. Copy [`../templates/project-tracker.md`](../templates/project-tracker.md) to `projects/<project-slug>.md`.
5. Add the tracker under Current projects.
6. When Phase 01 is complete, create/link the implementation repository and begin engineering the first ready PRD module.
