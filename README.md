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
- [`opportunities/`](opportunities/README.md) — entrypoint for choosing a service-product opportunity
- [`opportunities/service-products.md`](opportunities/service-products.md) — simple list of service projects and their models, ordered roughly by demand in Iran
- [`projects/`](projects/README.md) — project trackers plus authoritative project-specific documentation/artifacts
- [`templates/project-tracker.md`](templates/project-tracker.md) — tracker template

## Start a project

1. Read [`MASTER.md`](MASTER.md) for the guide role and workflow authority.
2. Open the [`opportunities/`](opportunities/README.md) index.
3. Select a **Product Family** (service name) from [`service-products.md`](opportunities/service-products.md).
4. Choose one specific **Product Model / Variant** listed under that service.
5. Prepare the Selected Opportunity Brief described in [Phase 01](phases/01-product-discovery.md), recording the service name, selected model, target market when relevant, and boundaries against adjacent variants.
6. Copy the [tracker template](templates/project-tracker.md) to `projects/<project-slug>.md`, create `projects/<project-slug>/`, persist the selected opportunity brief there, and add the tracker to the [project index](projects/README.md).
7. Follow Phase 01 and persist each approved stage artifact under the project directory before considering that stage complete.
8. Advance through later phases only when the active phase guide's exit criteria are met and the tracker reflects the current state.

## Project documentation policy

This repository is both the reusable playbook and the authoritative archive for project documentation produced by the workflow.

Store project-specific briefs, `product-design/` artifacts, prototype handoffs, specs, tickets, and verification/evidence documents under:

`projects/<project-slug>/`

Application implementation code may live in a separate product repository later if needed, but that does not change where the playbook's project documentation is stored.

## Opportunity-library principle

A broad service category is not automatically a project definition. The same family can produce fundamentally different products depending on the delivery model.

For example, **Barbershop / Beauty Salon Booking → Women’s single-salon** selects one physical women’s salon. A salon marketplace or at-home beauty service is a separate model with different users and operations.

```text
Product Family (service name)
        ↓
Variant (selected model)
        ↓
Selected Opportunity Brief
        ↓
Phase 01
```

## Principle

Product discovery should be deep enough to design the right product. Engineering workflow should then remain structured but lightweight enough to keep building momentum.
