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

Phase 01 Stages 01–04 are approved and persisted; Stage 05 research is persisted. Stage 06 — Jobs & User Journeys — remains in progress. Approved decisions include one service per appointment, mobile-number/SMS-code customer login, volume-based durations, disclosed approximate-price deposits, manager-controlled deposit/payment/cancellation settings, and preservation of accepted booking terms. Telephone bookings use customer review/payment links; future in-person bookings also permit deposits received and recorded by reception; immediate walk-ins pay during the visit. All use the shared calendar, and a staff-entered customer number is not authenticated until the customer completes SMS verification. Customer rescheduling before the stored cutoff transfers the deposit and retains the original appointment until replacement confirms. Original terms remain, with the cutoff recalculated against the new time. Salon cancellation or rejection of a salon-proposed time/specialist replacement gives a full deposit refund; replacements require customer acceptance. Customer no-preference booking combines valid eligible times and assigns a specialist by management priority, showing the name before payment. Reception-created bookings also offer named-specialist and any-eligible-specialist options, using the same manager-controlled assignment priority; the final specialist is shown to reception and communicated to the customer before confirmation. Confirmed specialist changes require customer acceptance for both paths. Booking information defaults from the customer profile and is editable per appointment, including the contact number; these edits do not change profile/login details or account ownership. A different booking contact requires SMS verification before payment/confirmation, without changing the original account’s login or ownership. Started payments with unknown results retain the specialist/time until a defined verification deadline; verified success while held confirms, definitive failure or the unresolved-result deadline releases the slot, and success verified after release receives a full deposit refund without automatic confirmation. Stage 06 remains a draft while outstanding journey/flow decisions are resolved.

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

Review remaining Stage 06 decisions. Reception-created named/any-eligible specialist booking and changed-contact SMS verification are approved; rescheduling, salon-originated cancellation, and bounded pending-payment holds with full refunds for success verified after slot release are approved; define the verification deadline and refine refund execution, late-change exceptions, unanswered proposals, link delivery, hold-start interactions, and account matching during flow definition. Resolve journey-changing decisions before marking Stage 06 complete and moving to Stage 07 — User Flows.

## Blockers / notes

No current blocker. Project documentation is stored in this playbook repository under the project documentation root. Application implementation code may live elsewhere later, but product documentation remains authoritative here.

## Guide entrypoint

Read [`MASTER.md`](../MASTER.md), this tracker, confirm the selected Product Family + Model, read the active phase guide, and then inspect the project artifacts under [`projects/womens-beauty-salon-booking/`](womens-beauty-salon-booking/) before making status claims or continuing the workflow.
