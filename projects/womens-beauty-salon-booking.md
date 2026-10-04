# Project Tracker — Women’s Beauty Salon Booking

## Project

- Product family: Barbershop / Beauty Salon Booking ([catalog](../opportunities/service-products.md))
- Selected model / variant: **Women’s single-salon**
- Target market / geography: Persian-language product for the Iranian market
- Documentation root: [`projects/womens-beauty-salon-booking/`](womens-beauty-salon-booking/)
- Current PRD source: [`product-design/prd.md`](womens-beauty-salon-booking/product-design/prd.md)
- New authoritative PRD target: `projects/womens-beauty-salon-booking/prd.md`
- Implementation repository: pending
- Current playbook phase: 01 — Product Discovery & Delivery Plan
- Current status: in progress (workflow migration)

## Product boundary

- **Selected:** one physical women’s beauty salon, multiple services, multiple specialists, salon-controlled schedules and appointment operations.
- **Explicitly not:** men’s barbershop, unisex salon, independent-specialist marketplace, multi-salon marketplace, multi-branch salon network, or beauty-at-home/mobile workforce product.

The approved product behavior from the existing discovery artifacts remains valid unless deliberately changed. The workflow migration must not reopen settled product decisions without a real contradiction.

## Playbook workflow

| Phase | Status | Main result |
| --- | --- | --- |
| 01 — Product Discovery & Delivery Plan | in progress | Authoritative phased PRD + active-phase module map |
| 02 — Module-by-Module Engineering | not started | Reviewed working modules / completed product delivery phases |
| 03 — Visual Redesign & UI Polish | not started | Stitch-driven visual redesign if needed |

## Existing discovery status

The previous workflow completed substantial product discovery and produced an approved consolidated PRD plus supporting product-design artifacts.

Those decisions remain useful source material, including:

- product scope and model boundaries;
- customer/reception/manager actors;
- booking, availability, deposit, payment, refund, rescheduling, ownership, and salon-change rules;
- user journeys/flows;
- information architecture and page inventory;
- UX states;
- visual/design-system/content direction.

The old Base44 Prompt Package is no longer part of the authoritative workflow and should not be continued.

## Product Delivery Roadmap

Not yet migrated into the new PRD format.

The next discovery step is to decide the product-specific delivery phases, including what the first implementation phase must achieve.

Do not invent the phase count without that discussion.

## Active Product Delivery Phase

Not yet defined under the new workflow.

## Modules

Not yet defined under the new workflow.

The approved product behavior should be decomposed into implementation-oriented product modules only after the Product Delivery Phase 1 boundary is agreed.

Examples such as authentication, booking, customer account, staff operations, management controls, payments, or communication may emerge, but the final module map must be derived from the chosen delivery-phase scope rather than copied from a generic template.

## Current activity

Migrate the approved discovery work into the new Phase 01 output format:

1. preserve settled product decisions;
2. define Product Delivery Phases;
3. define the goal/boundary of Product Delivery Phase 1;
4. decompose that active phase into coherent modules;
5. synthesize the new authoritative `projects/womens-beauty-salon-booking/prd.md`;
6. identify the first ready module for Phase 02.

## Important existing source artifacts

- Selected Opportunity Brief: [`selected-opportunity-brief.md`](womens-beauty-salon-booking/selected-opportunity-brief.md)
- Existing approved PRD: [`product-design/prd.md`](womens-beauty-salon-booking/product-design/prd.md)
- Product scope: [`product-design/product-scope.md`](womens-beauty-salon-booking/product-design/product-scope.md)
- Users/actors: [`product-design/user-actors.md`](womens-beauty-salon-booking/product-design/user-actors.md)
- Jobs/journeys: [`product-design/jobs-and-journeys.md`](womens-beauty-salon-booking/product-design/jobs-and-journeys.md)
- User flows: [`product-design/user-flows.md`](womens-beauty-salon-booking/product-design/user-flows.md)
- Information architecture: [`product-design/information-architecture.md`](womens-beauty-salon-booking/product-design/information-architecture.md)
- Page inventory: [`product-design/page-inventory.md`](womens-beauty-salon-booking/product-design/page-inventory.md)
- UX states: [`product-design/ux-states.md`](womens-beauty-salon-booking/product-design/ux-states.md)
- Visual direction: [`product-design/visual-direction.md`](womens-beauty-salon-booking/product-design/visual-direction.md)
- Design system: [`product-design/design-system.md`](womens-beauty-salon-booking/product-design/design-system.md)
- Responsive/content direction: [`product-design/responsive-content-direction.md`](womens-beauty-salon-booking/product-design/responsive-content-direction.md)

Legacy Base44 prompt artifacts may remain as historical files but are not authoritative for the new workflow.

## Next action

Define the product's **Product Delivery Phases** and the exact boundary of **Product Delivery Phase 1**. Then derive the module map and rewrite the approved product intent into the new authoritative PRD format.

## Blockers / notes

No product blocker. The only blocker to Phase 02 is the workflow migration: delivery phases and active-phase module boundaries have not yet been agreed in the new PRD format.

## Guide entrypoint

Read:

1. [`MASTER.md`](../MASTER.md)
2. this tracker
3. [`phases/01-product-discovery.md`](../phases/01-product-discovery.md)
4. the existing approved PRD and only the supporting artifacts needed for the current migration decision

Do not continue the obsolete Base44 prompt workflow.
