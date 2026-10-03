# Project Tracker — Women’s Beauty Salon Booking

## Project

- Product family: Barbershop / Beauty Salon Booking ([catalog](../opportunities/service-products.md))
- Selected model / variant: **Women’s single-salon**
- Target market / geography: Persian-language product for the Iranian market
- Documentation root: [`projects/womens-beauty-salon-booking/`](womens-beauty-salon-booking/)
- Implementation repository: not yet needed
- Product type: Single-location women’s beauty service discovery, booking, and appointment-management product
- Current phase: 01
- Current status: in progress

## Model boundary

- **Selected:** one physical women’s beauty salon, multiple services, multiple specialists, salon-controlled schedules and appointment operations.
- **Explicitly not:** men’s barbershop, unisex salon, independent-specialist marketplace, multi-salon marketplace, multi-branch salon network, or beauty-at-home/mobile workforce product.

A deliberate future model change must update the Selected Opportunity Brief, this tracker, and any affected approved artifacts before the workflow continues.

## Workflow

| Phase | Status | Main artifact / result |
| --- | --- | --- |
| 01 — Product Discovery & Product Design | in progress | PRD + Base44 Prompt Package |
| 02 — Base44 Prototype | not started | Base44 prototype + React baseline/handoff |
| 03 — React Frontend Completion | not started | Completed engineered React frontend |
| 04 — React → Next.js Refactor | not started | Behaviorally equivalent Next.js frontend |
| 05 — Full-Stack Next.js Completion | not started | Completed server-backed full-stack product |

## Current activity

Phase 01 Stages 01–04 are approved and persisted; Stage 05 research is persisted. Stage 06 — Jobs & User Journeys — remains in progress. Approved decisions include one service per appointment, mobile-number/SMS-code customer login, volume-based durations, disclosed approximate-price deposits, manager-controlled deposit/payment/cancellation settings, and preservation of accepted booking terms. Telephone bookings use customer review/payment links; future in-person bookings also permit deposits received and recorded by reception; immediate walk-ins pay during the visit. All use the shared calendar, and a staff-entered customer number is not authenticated until the customer completes SMS verification. Rescheduling and salon-originated cancellation rules remain open before final flows.

## Important artifacts

- Selected Opportunity Brief: [`selected-opportunity-brief.md`](womens-beauty-salon-booking/selected-opportunity-brief.md)
- Problem Definition: [`product-design/problem-definition.md`](womens-beauty-salon-booking/product-design/problem-definition.md)
- Solution Definition: [`product-design/solution-definition.md`](womens-beauty-salon-booking/product-design/solution-definition.md)
- Product Strategy & Scope: [`product-design/product-scope.md`](womens-beauty-salon-booking/product-design/product-scope.md)
- User & Actor Definition: [`product-design/user-actors.md`](womens-beauty-salon-booking/product-design/user-actors.md)
- UX / Competitive Research: [`product-design/ux-research.md`](womens-beauty-salon-booking/product-design/ux-research.md)
- Jobs & User Journeys (draft): [`product-design/jobs-and-journeys.md`](womens-beauty-salon-booking/product-design/jobs-and-journeys.md)
- PRD: pending
- Base44 prompts: pending
- Prototype/handoff: pending
- Current spec/tickets: not applicable yet

## Next action

Review Stage 06 jobs and journeys, beginning with rescheduling and salon-originated cancellation rules. Phone/future in-person booking deposit paths and immediate walk-in payment are approved; refine link delivery, hold-start interactions, and account matching during flow definition. Resolve journey-changing decisions before marking Stage 06 complete and moving to Stage 07 — User Flows.

## Blockers / notes

No current blocker. Project documentation is stored in this playbook repository under the project documentation root. Application implementation code may live elsewhere later, but product documentation remains authoritative here.

## Guide entrypoint

Read [`MASTER.md`](../MASTER.md), this tracker, confirm the selected Product Family + Model, read the active phase guide, and then inspect the project artifacts under [`projects/womens-beauty-salon-booking/`](womens-beauty-salon-booking/) before making status claims or continuing the workflow.
