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

Phase 01 remains in progress. Stages 01–04 are approved and persisted; Stage 05 research is persisted. Stage 06 — Jobs & User Journeys — is approved and complete on 2026-10-03. The user accepted the remaining proposals after withdrawing the excess-deposit question and authorized proceeding to Stage 07 — User Flows.

The approved journeys preserve one service/specialist per appointment, named/any-eligible choices for customer and reception, management priority, customer acceptance of confirmed specialist changes, account ownership with SMS-verified contacts, deposit and shared calendar constraints, rescheduling/deposit transfer, and salon-originated full refunds. Initial defaults are 20% deposit, a 24-hour cancellation/rescheduling window, and a 10-minute hold with up to 5 additional minutes for a started payment with an unknown result. Final prices are accepted before variable-price service begins.

Remaining decisions now approved: management-only late exceptions with reasons; SMS booking links and change/cancellation notices; reception holds starting at finalized initial booking/link-send request; staff SMS login with management-assigned access; salon-coordinated login-number change/recovery; name/contact minimum intake; manager-configured service/volume information and consultation contact paths; resolution of schedule conflicts before saving. Volume mismatches do not change booked time/duration; if no solution fits, cancel with a full refund and leave any new booking to the customer.

Stage 07 — User Flows — is approved and complete on 2026-10-03 under the user's explicit delegation to finalize remaining recommendations. Customer/reception booking, payment results, account status retrieval, cancellation/rescheduling, salon replacements, manager exceptions, in-salon settlement, number correction/recovery, management edits, refund progress, and SMS failure recovery are defined. Appointment/payment/refund states remain distinct; identity transfer requires verified ownership, and failed operations preserve existing bookings/entitlements. Provider-specific operations, concrete manual identity-evidence procedures, security controls, and real service configuration are engineering/configuration handoff work.

The active next stage is Stage 08 — Information Architecture, not yet started. Phase 01 remains in progress.

## Important artifacts

- Selected Opportunity Brief: [`selected-opportunity-brief.md`](womens-beauty-salon-booking/selected-opportunity-brief.md)
- Problem Definition: [`product-design/problem-definition.md`](womens-beauty-salon-booking/product-design/problem-definition.md)
- Solution Definition: [`product-design/solution-definition.md`](womens-beauty-salon-booking/product-design/solution-definition.md)
- Product Strategy & Scope: [`product-design/product-scope.md`](womens-beauty-salon-booking/product-design/product-scope.md)
- User & Actor Definition: [`product-design/user-actors.md`](womens-beauty-salon-booking/product-design/user-actors.md)
- UX / Competitive Research: [`product-design/ux-research.md`](womens-beauty-salon-booking/product-design/ux-research.md)
- Jobs & User Journeys (approved): [`product-design/jobs-and-journeys.md`](womens-beauty-salon-booking/product-design/jobs-and-journeys.md)
- User Flows (approved): [`product-design/user-flows.md`](womens-beauty-salon-booking/product-design/user-flows.md)
- PRD: pending
- Base44 prompts: pending
- Prototype/handoff: pending
- Current spec/tickets: not applicable yet

## Next action

Start Stage 08 — Information Architecture using the approved user flows: define public/customer/salon areas, information grouping, navigation, authenticated boundaries, hierarchy, cross-links, and sitemap. Preserve a short booking path and reception/management permissions. Persist `product-design/information-architecture.md` and review it before marking Stage 08 complete.

## Blockers / notes

No current blocker. Project documentation is stored in this playbook repository under the project documentation root. Application implementation code may live elsewhere later, but product documentation remains authoritative here.

## Guide entrypoint

Read [`MASTER.md`](../MASTER.md), this tracker, confirm the selected Product Family + Model, read the active phase guide, and then inspect the project artifacts under [`projects/womens-beauty-salon-booking/`](womens-beauty-salon-booking/) before making status claims or continuing the workflow.
