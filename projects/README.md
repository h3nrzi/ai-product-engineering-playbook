# Project Trackers

Each product using this playbook gets one lightweight tracker here plus a small project workspace under `projects/<project-slug>/`.

Projects follow three authoritative playbook phases:

1. Product Discovery & Delivery Plan
2. Module-by-Module Engineering
3. Visual Redesign & UI Polish (when needed)

The tracker is navigation/context for Guide LLMs. The PRD is the product authority. Engineering artifacts may live in the implementation repository when that is where the AI Hero workflow operates.

## Current projects

- [`Women’s Beauty Salon Booking`](womens-beauty-salon-booking.md) — Barbershop / Beauty Salon Booking → **Women’s single-salon** — Phase 02; M01 specification published, ticket decomposition next.

## Preferred project structure

```text
projects/
├── <project-slug>.md
└── <project-slug>/
    ├── README.md
    └── prd.md
```

Keep project documentation intentionally small. Add another file or folder only when it provides durable value beyond the PRD.

## Add a project

1. Start Phase 01 and choose the Product Family + Model from [`../opportunities/service-products.md`](../opportunities/service-products.md).
2. Create `projects/<project-slug>/README.md` as the lightweight workspace entrypoint.
3. Copy [`../templates/project-tracker.md`](../templates/project-tracker.md) to `projects/<project-slug>.md`.
4. Add the tracker under Current projects.
5. Discuss the product, define its Product Delivery Phases, and decompose the active phase into modules.
6. Create `projects/<project-slug>/prd.md` from [the standard PRD template](../templates/prd.md), obtain explicit product approval, and treat the approved baseline as read-only.
7. When Phase 01 is complete, create/link the implementation repository and begin engineering the first ready PRD module.
