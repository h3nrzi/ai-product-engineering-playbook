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

Phase 01 Stages 01–04 are approved and persisted. The MVP has customer access and one salon operations area with separate reception/management permissions; specialists have no independent dashboard. Reception manages appointments, including phone/walk-in bookings; management also controls services, prices, specialists, eligibility, and working schedules. Stage 05 — UX / Competitive Research — is researched and persisted; the user approved one service per MVP appointment. Stage 06 — Jobs & User Journeys — has a persisted draft; customer mobile-number/SMS-code login and account-linked online reservations are approved. Online deposit payment for confirmation, a short payment hold, and remaining payment at the salon are approved. One shared deposit percentage for all services, configurable only by management, is approved; per-service percentages are deferred. For variable-price services, the approximate usual-volume price is the approved deposit basis; the customer must see that the final price may vary and the paid deposit is deducted at the salon. Customer volume selection with manager-defined durations is approved for variable-duration services; availability uses that duration while the deposit basis stays unchanged. Management configures the shared deposit percentage, payment-hold duration, and advance cancellation window; customers see the rules before payment and each booking retains its accepted terms when settings change. Rescheduling/refund exception details, staff authentication, and staff-created appointment linking remain open before final flows.

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

Review Stage 06 jobs and journeys, beginning with deposit collection/account linkage for phone and walk-in appointments, followed by rescheduling and salon-originated cancellation rules. Resolve journey-changing decisions before marking Stage 06 complete and moving to Stage 07 — User Flows.

## Blockers / notes

No current blocker. Project documentation is stored in this playbook repository under the project documentation root. Application implementation code may live elsewhere later, but product documentation remains authoritative here.

## Guide entrypoint

Read [`MASTER.md`](../MASTER.md), this tracker, confirm the selected Product Family + Model, read the active phase guide, and then inspect the project artifacts under [`projects/womens-beauty-salon-booking/`](womens-beauty-salon-booking/) before making status claims or continuing the workflow.
