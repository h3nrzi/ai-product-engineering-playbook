# Product Requirements Document — Women’s Beauty Salon Booking

- Stage: 14 — PRD
- Status: draft for user review
- Date: 2026-10-03
- Product family: Barbershop / Beauty Salon Booking
- Selected model: Women’s single-salon
- Phase: 01 — Product Discovery & Product Design

This PRD consolidates approved product decisions through Stage 13. It becomes the authoritative consolidated definition after approval; supporting artifacts provide detail. It introduces no new business policy. Historical discovery questions already resolved by later approved stages are not reopened.

## 1. Overview, problem and solution

One physical women’s beauty salon needs a coherent customer booking experience and the operational controls that keep it reliable.

Customers currently depend on fragmented service/specialist information and repeated coordination to understand price, duration and availability. Reception manually combines service eligibility, working hours, duration and existing bookings. These are design premises, not measured research results.

The product brings service discovery, specialist choice, valid full-duration availability, deposit-based confirmation and permitted appointment management into one Persian-language experience.

Customer promise: understand what is available, choose a suitable specialist/time and know whether the appointment is confirmed.

Salon promise: reduce routine booking coordination while retaining control over service information, eligibility, working schedules, assignment priority and booking rules.

## 2. Actors and access

| Actor | Capabilities and boundary |
| --- | --- |
| Customer | Public discovery; mobile/SMS authentication; own booking review/payment, appointment/attempt retrieval, permitted changes and refund progress |
| Reception | SMS-authenticated assigned staff; shared calendar, online/telephone/in-person appointment operations, actual salon receipts and appointment-linked follow-up |
| Manager | All reception capabilities plus services/prices, volume/duration, specialists/eligibility/priority, schedules, salon-wide booking settings, staff access and reasoned exceptions/support |
| Specialist | Delivers eligible services and coordinates final price/volume with customer through salon operations; public profile, no independent product login/dashboard |

A verified staff phone without a management-assigned role grants no operations access. Reception cannot change manager settings or approve exceptions. Permissions apply to direct links and actions as well as navigation.

## 3. Scope

### Required MVP capabilities

Structured services and specialist discovery; service/volume/specialist/time selection; SMS identity and contact verification; temporary holds and deposit/payment outcomes; owning-customer account retrieval; cancellation/rescheduling; reception-created bookings; shared calendar; explicit salon-replacement consent; salon receipts/final settlement; refund and SMS follow-up; manager configuration and verified identity-support paths.

Each appointment has one service and one eligible specialist. This is not a daily customer booking limit.

### Non-goals and deferred capabilities

No marketplace, additional salon locations/branches, beauty-at-home workforce, multi-service booking, coordinated service bundles, specialist dashboard, scheduled reminders, wallet/forced credit, loyalty, notification inbox, chat, ecommerce, full CRM, accounting/POS, payroll, inventory, marketing automation or AI beauty advisor.

Per-service deposit percentages, waitlists, favorites, repeat-booking shortcuts and advanced recommendations are deferred. Changing service/volume within the approved reschedule path is not included.

Production MVP and Base44 prototype are distinct: the prototype demonstrates the intended experience using clearly simulated operations; real identity, persistence, payments, availability enforcement and concurrency guarantees belong to engineering phases.

## 4. Primary and supporting journeys

Primary journey:

Service → relevant volume → named/any-eligible specialist → valid date/time → SMS login if needed and booking information → final review → secure temporary hold and pay deposit → current result → owning account.

Supporting journeys:
- Specialist-first discovery into a service that specialist actually provides.
- Consultation-required service into salon contact, without a misleading direct-booking action.
- Reception telephone/future-in-person/immediate-walk-in booking.
- Customer appointment retrieval, reschedule, cancellation and replacement response.
- Salon replacement/cancellation, manager late exception and daily follow-up.
- At-salon price agreement, fixed-interval volume resolution and final settlement.
- Contact correction, verified ownership support, service/schedule/settings maintenance.

## 5. Product requirements

### R01 — Discovery and configuration

Show truthful service descriptions, fixed or approximate price wording, duration/volume information, relevant price factors, eligible specialists and salon contact. Public discovery and availability require no login.

Management supplies actual prices, usual-volume price bases, volume labels/durations, consultation prerequisites, specialist eligibility/priority and working schedules. Variable pricing alone does not require consultation.

Volume options are required only when duration varies. Selecting a different option rechecks dependent availability. For variable-price services, volume selection determines duration; it does not automatically change the disclosed approximate usual-volume deposit basis or guarantee a final price.

### R02 — Valid availability and assignment

A valid time fits the entire selected service duration for an eligible specialist within working schedules, without overlap with existing appointments or active holds. Customer and reception use the same availability/calendar.

Both can choose a named specialist or any eligible specialist. Any-eligible shows combined valid availability and assigns the first eligible, available specialist in management’s priority order after time selection.

Show the actual specialist before payment/confirmation; reception communicates the name to the customer. If assignment changes before securing a hold, present the changed name for review. Confirm the reviewed specialist, never silently substitute to recover a conflict.

After confirmation, any-eligible selection does not authorize future substitutions. Specialist changes require customer acceptance. Priority edits cannot reassign active holds or confirmed appointments.

### R03 — Identity, booking intake and ownership

Customers sign in using mobile number and one-time SMS code before final review/submission. Preserve valid selections through login and recheck availability; login itself never holds time.

Name and contact are minimum intake. Prefill available profile values; ask for additional service data only when justified. A contact different from the account’s verified number needs its own SMS verification before payment/confirmation. Editing it again invalidates verification for the changed choice.

Appointment contact, profile/login identity and account ownership remain distinct. Contact verification does not log into another account or transfer ownership. My appointments belongs to the original owning account, even if its booking contact changes.

Staff-entered numbers, links, references and receipt records do not authenticate a customer. A reception-created appointment is accessible only through verified ownership of its recorded number; name matching alone is insufficient.

Confirmed contact corrections require customer authorization and verification of the intended contact. Access correction/login-number recovery is salon-coordinated, with manager verification of the existing owner, intended mobile and entitlement, recorded reason/evidence and notification of affected verified channels. Unverified requests remain pending/denied; never merge accounts automatically. Concrete independent evidence procedures must be established before production manual transfers are enabled.

### R04 — Price, deposit and accepted terms

Initial salon-wide deposit: 20%. Management may configure it for new bookings only; reception cannot override it. Deposit = disclosed booking price basis × applicable percentage / 100.

Basis is the fixed price for fixed-price services or disclosed approximate usual-volume price for variable-price services. Round once to the nearest whole toman, half upward; save and preserve that exact payable amount. Provider-unit conversion must preserve it.

Review shows the basis, percentage, exact deposit, fixed/approximate price type, balance or estimate, volume/duration, actual specialist/date/time and cancellation/payment deadlines.

Final variable-service price is communicated and accepted before work begins. Salon balance = agreed final price − deposit already paid. A later final-price adjustment does not retroactively increase the collected deposit. Example: ۱٬۰۰۰٬۰۰۰ تومان final price, ۲۰۰٬۰۰۰ تومان paid deposit, ۸۰۰٬۰۰۰ تومان payable at salon.

Save accepted price/deposit/policy terms when the reviewed hold/payment attempt starts. Later catalog/settings edits do not recalculate existing paid amounts, rewrite terms or move active deadlines. No excess-deposit credit/refund policy is introduced; that question was withdrawn.

### R05 — Hold, payment and confirmation

Customer “پرداخت بیعانه” rechecks availability, secures the reviewed specialist’s full interval, saves accepted terms and starts the hold only when secured. Browsing, slot selection, login and viewing review do not hold time.

Initial hold: 10 minutes. A payment started in time with an unknown result may retain the slot for up to 5 additional minutes after ordinary expiry; initial total maximum is 15 minutes from hold creation. Definitive results act immediately. Management-configured ordinary hold durations apply to new attempts; preserve accepted deadlines.

| Event | Appointment/calendar result | Financial result |
| --- | --- | --- |
| Verified payment success while held | Same reviewed appointment confirmed | Deposit recorded as paid |
| Definitive payment failure | Release hold; no confirmation | Known failure |
| No payment started by ordinary expiry | Release hold; unconfirmed attempt | No received deposit |
| Started payment unknown at ordinary expiry | Retain only until bounded verification deadline | Continue checking |
| Unknown at final verification deadline | Release; no confirmation | Verification continues separately |
| Success verified after release | Never auto-confirm, even if slot is free | Full deposit refund entitlement |

Before payment starts, explicitly release an unpaid hold before changing held service/time/specialist. Once payment starts or is unknown, do not switch the attempt to another slot or invite duplicate payment. Show current status until a definitive outcome or release.

Opening/reopening links, back navigation, login and status checks never restart deadlines. A fresh attempt requires fresh valid availability/hold. Provider redirects/screenshots do not prove verified payment.

The owning account retains interrupted/unconfirmed attempts and ongoing payment/refund outcomes, including after closing/reopening the result page.

### R06 — Reception booking sources

- Telephone: intake/review actual specialist and terms → finalize initial booking and request SMS review/payment link → hold starts at this action → customer authenticates, reviews and pays. Confirm only on verified payment while held.
- Future in-person: same link route, or staff receives and records the calculated deposit after explaining accepted terms. Actual receipt permits confirmation; no deposit waiver.
- Immediate walk-in: validate immediate full-duration availability, record confirmed visit and collect payment during the visit. No advance deposit; future bookings cannot use this branch to bypass it.

Reception records only money actually received at the salon, with source/amount. It cannot label an uncertain online payment paid. All sources share one calendar; future unpaid reservations cannot be indefinite.

### R07 — Customer rescheduling and cancellation

Initial advance window: 24 hours before appointment. Manager changes apply to new bookings; existing bookings retain their stored terms/deadline.

An eligible customer action completed at or before the stored cutoff qualifies; recheck at application, not just screen opening. Within the window, cancellation returns the full deposit and rescheduling transfers the existing deposit without a second charge.

A reschedule uses a valid new time; original slot/deposit remain until replacement confirms. Failure leaves the original intact. Preserve original accepted price/policies and calculate the new cutoff from the replacement time using the original window. Show it before confirming, even when already passed.

After cutoff, online rescheduling is unavailable. Cancellation remains available with disclosed no-refund consequence; no-show follows the default no-refund policy. Salon contact alone is no exception. Only a manager may authorize a late-change/refund exception with a recorded reason.

### R08 — Salon replacements, cancellation and schedule edits

A salon-proposed time/specialist change requires explicit customer acceptance before applying. Show original and proposal together, recheck replacement availability and record telephone/in-person acceptance with channel/time/reviewed details.

Salon cancellation or customer rejection of a salon replacement grants full refund of deposit actually paid, irrespective of cutoff and payment source.

No reply: retain the original if deliverable; if undeliverable, salon-cancel with full refund rather than wait indefinitely. Silence is neither acceptance nor customer forfeiture. Proposals alone do not indefinitely reserve alternatives.

Schedule edits show affected confirmed appointments and active holds. Resolve affected appointments under consent/refund rules before saving an invalidating schedule change. Do not silently invalidate holds or reassign bookings. Recheck at save; failed/abandoned edits preserve published values and retain useful unsaved input.

### R09 — At-salon service and settlement

Coordinate and accept final approximate-service price before starting. Record agreed final price, credited deposit and actual remaining receipt.

An inaccurate volume choice does not move the start or extend duration, even if later time is free. Specialist/customer resolve within the reserved interval without delaying/overlapping the next appointment. If no agreed solution fits, cancel with full deposit refund; a separate new booking requires customer choice.

Final-price disagreement stops service from starting and routes to salon coordination. It does not automatically charge, extend time or establish a new refund entitlement; apply an existing approved rule where applicable or a reasoned manager exception.

### R10 — Refunds, communication and follow-up

Qualifying cancellation/late verified payment establishes refund entitlement without a second customer request. Prefer original payment source; unsupported provider refund routes need authorized salon follow-up and independent verification of original payer/recipient before a documented manual return. In-salon deposits use a documented salon return route.

Show exact amount/source and pending/completed/needs-attention separately from cancellation. Completion requires verified return or documented actual refund receipt, reference and time. Failure preserves entitlement; retries must not duplicate refunds. No forced wallet credit or unsupported instant-return promise.

SMS carries reception links and appointment change/cancellation notices to approved contact. Delivery is independent of booking/payment outcome. Retry the same still-valid link/notice without new booking, repeated refund or deadline reset. Failed delivery flags appointment-linked follow-up; the account shows actual status.

### R11 — Management validation and operations

Only managers edit services/prices/volume durations, specialist eligibility/priority, schedules, deposit percentage, ordinary hold duration, cancellation window and assigned staff roles.

Require positive bookable price basis/duration/hold duration; deposit percentage >0 and <=100; cancellation window >=0; nonempty relevant labels, coherent working intervals and a priority order without duplicate specialists. Preserve valid published settings after validation/save failure; stale edits require review of current values before save.

Reception/manager can record completion/no-show, receipts and permitted appointment actions. The operational follow-up worklist links unknown payments, refund attention, failed SMS and response issues to their exact appointment/attempt. It is not accounting, CRM or a scheduled reminder system.

## 6. Required surfaces and navigation

19 page/template groups cover the product; this does not mandate 19 routes or a route for every state.

| Area | Required templates |
| --- | --- |
| Public / booking | P01 home; P02 services; P03 service detail; P04 specialists; P05 specialist profile; P06 salon/about/contact; P07 booking/result |
| Customer | P08 appointments/attempts; P09 appointment/attempt detail; P10 profile information/support |
| Salon operations | P11 staff SMS sign-in; P12 calendar/appointments; P13 staff appointment detail; P14 appointment-linked follow-up |
| Manager only | P15 services; P16 specialists/eligibility/priority; P17 schedules/conflicts; P18 booking settings; P19 staff access/contextual ownership support |

Public navigation: خدمات · متخصص‌ها · درباره سالن و تماس · نوبت‌های من, plus رزرو نوبت. Account: نوبت‌های من · اطلاعات من. Staff entry is calendar-first, with reception operations and manager-only controls in the same area.

P07 has conditional service, volume, specialist, time, sign-in/details, final-review and payment/result steps. Reuse login/contact verification. Payment card entry belongs to the provider, not a salon-built form.

Contextual surfaces cover reception intake, reschedule/cancel, salon proposal, manager exception, receipt/settlement, volume resolution, verified contact/ownership support, refund/SMS follow-up and management conflicts. See [page inventory](page-inventory.md) for surface IDs, entry/content/actions and flow mappings.

## 7. UX principles and important states

Preserve useful intent through recoverable errors; dependent choices are revalidated. Never conceal a change of specialist, accepted terms, deadlines or ownership.

Separate appointment states (awaiting deposit, expired/unconfirmed, confirmed, cancelled, completed, no-show), payment states (not started, initiated/unknown, verified success, definite failure) and refund states (not applicable, due/pending, completed, needs attention). Immediate walk-ins can be confirmed without advance deposit; payment is due during visit.

Design distinct loading, empty, known error, unknown outcome, selected/disabled/unavailable, conflict, expired session and denied access states. A read failure is not an empty list; an unknown operation is not known failure. Prevent duplicate submission and check actual current state before retrying a possibly committed operation.

Show actual held/released status and deadlines during payment checks. A cancelled appointment is not proof a refund completed. A failed SMS never reverses a successful operation.

Use visible labels/focus, keyboard-operable controls, non-color-only statuses and readable Persian text. Denied/private links reveal no appointment details. Sign-out/account switching does not expose prior-account content.

## 8. Brand, design and device direction

Approved personality: calm, professional, warm and refined. No existing brand name/logo/colors were supplied; do not invent a final identity.

Use warm ivory #FAF7F3 canvas, white surfaces, deep plum #5E3448 primary, pale rose #EEDCE2 accent, #272327 main text and #655D63 supporting text. Typography is Vazirmatn. Use moderate rounding, restrained shadows/motion and honest actual salon photography when supplied; sample imagery is illustrative.

Apply the [design system](design-system.md) semantic colors, typography/spacing, widths, component variants, status/focus rules and accessibility baseline. Token contrast checks do not substitute for rendered interface review.

Customer/public experiences are mobile first. Booking is a readable single column on narrow screens, with adjacent summary on wider screens when appropriate. Staff desktop/tablet uses a full-duration calendar; narrow screens use a readable day list with date/specialist filters and accessible detail/actions.

Navigation adapts to labeled menus without losing approved destinations. Sticky primary actions may help booking but must not cover summary, fields, errors, policy or keyboard. Staff density may increase without sacrificing readable labels and usable targets.

## 9. Content and localization

Use clear, respectful Persian and RTL layout. Canonical labels include رزرو نوبت، هر متخصص واجد شرایط، بیعانه، پرداخت بیعانه، نوبت تأییدشده، بررسی وضعیت پرداخت، تغییر زمان نوبت and بازپرداخت بیعانه.

Display Solar Hijri dates, 24-hour time with Tehran-time meaning, Persian digits for dates/amounts and labeled toman amounts. Phone/code input accepts Persian/Latin digits while preserving leading zeroes and proper LTR reading order.

Exact dates/deadlines accompany consequential actions; relative wording alone is insufficient. Populate copy from actual saved terms, not hardcoded defaults. Approximate price, exact deposit and final salon balance remain distinguishable. No fabricated success, credentials, ratings or refund ETA.

Long names/policies wrap; essential identity, time, amount and consequences are not truncated. Optional missing imagery uses neutral fallback. Invalid required booking configuration does not become a fake bookable option.

## 10. Base44 prototype requirements

Phase 02 must demonstrate working navigation and interactions across retained surfaces, with coherent, clearly labeled demo data and simulated customer/reception/manager roles.

Demonstrate:
1. Fixed-price and volume-varying approximate-price booking, named/any-eligible assignment and consultation contact.
2. SMS login/contact-check states with selection preservation and role/ownership denial.
3. Hold creation only at the approved action, conflicts and actual countdown/status presentation.
4. Verified success, definite failure, unknown held/released outcomes and late success/full refund.
5. Account retrieval of interrupted attempts and independent refund progress.
6. Telephone link booking, future in-person actual deposit and immediate walk-in payment.
7. Eligible reschedule with deposit transfer, failed replacement preserving original, and cancellation cutoff consequences.
8. Salon replacement acceptance/decline/no reply, manager exceptions and schedule-conflict blocking.
9. Final-price settlement and fixed-interval volume mismatch/full-refund path.
10. SMS/refund needs-attention follow-up, management validation and pending/denied identity support.
11. Narrow/wide responsive layouts, long Persian content, keyboard/focus and sticky-action clearance.

Fixtures must agree across customer and staff summaries, eligibility, durations, holds and deposit arithmetic. Demonstrations can be deterministic simulations; never claim real payment/SMS transmission or verified identity from a mock interaction.

Base44 is not expected to prove real authentication/security, durable production storage, gateway/refund execution, authoritative concurrent locking or complete production accessibility. Those guarantees remain engineering work, preserving approved product behavior.

## 11. Qualitative success criteria

- A first-time customer can understand the offering and complete a standard booking without reception help.
- She can identify the actual service/specialist/time, exact deposit, price type and whether the appointment is confirmed.
- She can retrieve interrupted payment/refund outcomes and perform permitted changes without ambiguity or a second deposit.
- Staff can see one consistent schedule for all sources and distinguish held/confirmed/cancelled entries and financial progress.
- Manager edits and salon changes do not silently invalidate accepted appointments or bypass customer consent.
- Mobile layouts and Persian copy keep the core tasks readable and usable.

These are review criteria, not measured conversion or workload claims.

## 12. Assumptions, open questions and handoff

Behavioral assumptions remain unvalidated: willingness to self-book, benefits of visible availability, importance of specialist trust and reduced routine coordination. Actual staff device preference and service data need salon validation.

No unresolved product question prevents building the intended prototype. This PRD itself awaits user approval.

Production/configuration handoff includes real salon identity/contact/content, prices/volume labels/durations, eligibility/priority/schedules; payment/SMS provider compatibility and real verification/refund operations; authoritative availability, durable outcomes, deduplication and access enforcement; secure sessions, independent identity-evidence procedures and audit records. Verify the approved hold timing with the selected provider. Any required change to customer rights/business behavior returns for approval.

Do not treat historical “later/open” notes superseded by approved Stage 06/07 decisions as permission to invent different payment, refund or ownership rules.

## 13. Supporting documents and next step

- [Selected opportunity brief](../selected-opportunity-brief.md)
- [Problem definition](problem-definition.md)
- [Solution definition](solution-definition.md)
- [Product strategy and scope](product-scope.md)
- [Users and actors](user-actors.md)
- [UX / competitive research](ux-research.md)
- [Jobs and journeys](jobs-and-journeys.md)
- [User flows](user-flows.md)
- [Information architecture](information-architecture.md)
- [Page inventory](page-inventory.md)
- [UX states](ux-states.md)
- [Visual direction](visual-direction.md)
- [Design system](design-system.md)
- [Responsive and content direction](responsive-content-direction.md)

After approval, proceed to Stage 15 — Base44 Prompt Package. Prompts must preserve this PRD and link supporting details; Phase 01 remains in progress until Stage 16 review/handoff. No application implementation is authorized by this artifact.
