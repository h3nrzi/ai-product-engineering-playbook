# Base44 Prompt Package — Women’s Beauty Salon Booking

- Stage: 15 — Base44 Prompt Package
- Status: in progress
- Date: 2026-10-03
- Source of truth: [`../prd.md`](../prd.md)
- Product model: one physical women’s beauty salon, Persian-language product for the Iranian market

## Purpose

This package converts the approved product design into incremental prompts for a fresh Base44 session. Each prompt must be usable without hidden conversation context and must preserve decisions already approved in the PRD and supporting artifacts.

Do not merge the package into one mega-prompt. Execute prompts in order and review the result after each meaningful step before continuing.

## Execution order

| Order | Prompt | Intent | Status |
| --- | --- | --- | --- |
| 00 | [`00-project-foundation.md`](00-project-foundation.md) | Establish product boundaries, Persian/RTL baseline, shared demo fixtures and global implementation guardrails | ready |
| 01 | [`01-design-system.md`](01-design-system.md) | Materialize the approved visual system and reusable components | ready |
| 02 | [`02-app-shell-navigation.md`](02-app-shell-navigation.md) | Build public, customer and staff/manager shells and navigation boundaries | ready |
| 03 | [`03-public-discovery.md`](03-public-discovery.md) | Build home, services, specialists and salon/contact discovery surfaces | ready |
| 04 | [`04-booking-payment-flow.md`](04-booking-payment-flow.md) | Build the primary booking, identity, hold, payment and result journey | ready |
| 05 | `05-customer-area.md` | Build appointments/attempts, detail, permitted changes and account information | pending |
| 06 | `06-salon-operations.md` | Build staff sign-in, calendar, appointment operations and follow-up | pending |
| 07 | `07-manager-controls.md` | Build manager-only services, specialists, schedules, settings and staff/support controls | pending |
| 08 | `08-states-recovery.md` | Add critical loading, empty, failure, conflict, unknown-outcome and recovery behavior | pending |
| 09 | `09-responsive-rtl-accessibility.md` | Apply responsive transformations, Persian/RTL details and accessibility checks | pending |
| 10 | `10-final-consistency.md` | Run a final cross-product consistency pass without adding features | pending |

The sequence is intentionally product-specific. Staff operations and manager controls are separated because this product has meaningful operational depth and permission boundaries.

## Package-wide rules

Every prompt must preserve these rules unless an explicitly approved later decision changes them:

- One physical women’s salon; no marketplace, multi-branch network or at-home workforce.
- One service and one eligible specialist per appointment.
- Named specialist or “هر متخصص واجد شرایط” selection; actual assigned specialist is shown before confirmation.
- Customer account ownership, appointment contact and verified contact are distinct concepts.
- Deposit default is 20% for new bookings; accepted terms are preserved for existing attempts/appointments.
- Ordinary hold default is 10 minutes. A payment started in time with an unknown result may keep the slot for up to 5 additional minutes; deadlines never reset merely because a screen/link is reopened.
- Initial cancellation/rescheduling window is 24 hours before appointment. Eligible rescheduling transfers the existing deposit rather than collecting another one.
- Confirmed salon-side specialist/time changes require customer acceptance; qualifying salon cancellation/rejection produces full deposit refund entitlement.
- Appointment, payment and refund states remain separate.
- Real payment, SMS, identity verification, persistence, authoritative concurrency and security guarantees are not claimed by the Base44 prototype.
- Customer/public UI is Persian and RTL. Staff operations remain Persian/RTL while using denser desktop/tablet layouts where appropriate.
- Demo content must be realistic but explicitly treated as sample data. Do not invent ratings, reviews, verified success, refund ETA, real credentials or a final salon brand identity.
- Preserve unrelated completed work between prompts. Do not rewrite working areas unless the active prompt requires it.
- Do not add deferred features such as marketplace behavior, multi-service carts, loyalty, wallet, chat, CRM, accounting/POS, inventory, payroll, reminder automation or AI beauty advice.

## Review discipline

After each prompt:

1. Check only the scope that prompt was supposed to change.
2. Verify previously completed flows still behave consistently.
3. Record any real contradiction against the PRD before changing product behavior.
4. Prefer fixing implementation inconsistencies over inventing a new product rule.
5. Continue only when the current step is coherent enough for the next prompt.

## Completion condition

Stage 15 is complete when all required prompts are written, internally consistent, self-contained enough for a fresh Base44 session, and collectively capable of materializing the approved prototype without relying on hidden chat history or asking Base44 to rediscover product decisions.
