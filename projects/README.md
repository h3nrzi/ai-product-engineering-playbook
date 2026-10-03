# Project Trackers

Each product using this playbook gets one lightweight tracker here plus a project documentation directory under `projects/<project-slug>/`.

Before Phase 01, every project must identify both:

- a **Product Family** (service name) from [`../opportunities/service-products.md`](../opportunities/service-products.md);
- a specific **Product Model / Variant** within that family.

Track the project through the five authoritative phases:

1. Product Discovery & Product Design
2. Base44 Prototype
3. React Frontend Completion
4. React → Next.js Refactor
5. Full-Stack Next.js Completion

The tracker is navigation/context for Guide LLMs. The project directory is the authoritative home for project-specific documentation and artifacts produced by the workflow.

## Current projects

- [`Women’s Beauty Salon Booking`](womens-beauty-salon-booking.md) — Barbershop / Beauty Salon Booking → **Women’s single-salon** — Phase 01 in progress; Stages 01–03 persisted.

## Project structure

Use this pattern:

```text
projects/
├── <project-slug>.md
└── <project-slug>/
    ├── selected-opportunity-brief.md
    ├── product-design/
    ├── prototype/
    ├── specs/
    ├── tickets/
    └── evidence/
```

Only create subdirectories when the active workflow actually needs them.

## Add or remove a tracker

Copy [`../templates/project-tracker.md`](../templates/project-tracker.md) to `<project-slug>.md`, create the sibling `projects/<project-slug>/` documentation root, fill in the Product Family + selected Model, and add the tracker under Current projects.

When a project is deleted, remove its tracker and project documentation directory, then update this index. Keep the service and its models in the [service-product list](../opportunities/service-products.md) for future projects.
