# Information Architecture — Women’s Beauty Salon Booking

## Status and authority

Stage 08 approved and completed on 2026-10-03. The user accepted the proposed architecture after clarification of its place in the workflow. This information/navigation structure derives from [approved user flows](user-flows.md), [jobs and journeys](jobs-and-journeys.md), and [product scope](product-scope.md). Page/surface inventory follows in Stage 09; the hierarchy below does not mandate separate routes for every step or state.

Scope: one physical women's salon, one service/specialist per appointment, Persian/RTL experience, customer account, and one salon operations area with reception/management permissions.

## Product areas and audiences

| Area | Audience/access | Information and purpose |
| --- | --- | --- |
| Public discovery | Everyone; no login | Salon introduction/contact, services and pricing/duration information, specialists and supported services, valid availability |
| Booking journey | Public selection; customer login before review/payment | Service/volume/specialist/time selection, customer details, review, payment and result |
| Customer account | Authenticated original owner only | Appointments and unconfirmed booking/payment attempts, appointment details/actions, payment/refund progress, profile defaults and salon-contact recovery |
| Salon operations | SMS-authenticated staff with assigned reception or manager role | Shared calendar, appointment operations/intake, actual in-salon receipts, communication/refund follow-up |
| Management controls | Manager role within the same operations area | Services/prices/volume durations, specialists/eligibility/priority, schedules, shared booking rules, staff access, reasoned exceptions and ownership-support actions |

Specialists have public profiles and salon-coordinated responsibilities, not a separate login/dashboard. There is no separate multi-salon or branch navigation.

## Public navigation and content grouping

Proposed primary navigation: **خدمات · متخصص‌ها · درباره سالن و تماس · نوبت‌های من**, with the logo returning to home and a prominent **رزرو نوبت** action.

- **Home:** salon identity, service/specialist discovery entry points, a direct booking action, and essential location/contact information.
- **Services:** list with concise categories only when the real catalog needs them; detail templates show description, eligibility, price basis, duration/volume information, prerequisites and booking action.
- **Specialists:** list and profile templates show expertise and supported services. Specialist-first entry continues into a service that specialist actually provides.
- **About salon and contact:** one grouped surface for location, opening/contact information, and consultation/salon-support contact; avoid separate thin About and Contact pages.
- **My appointments:** visible entry even while signed out; sign in first, then return to the intended account surface. Login is an access step, not an extra main-navigation item.

Public specialist/service links cross-reference each other. A consultation-required service shows contact instead of a misleading direct booking action. Cancellation/deposit terms are accessible from booking review and appointment details, with general explanatory content linked from the footer; the saved booking terms remain authoritative.

## Booking hierarchy

One sequential journey:

Service → volume when relevant → named/any-eligible specialist → time → sign-in/customer details → final review → payment/result.

Do not add a generic booking dashboard or require repeated home-page visits between steps. Show progress and allow backward navigation while preserving valid choices and rechecking dependent availability. Fixed-duration services skip volume. Existing valid sessions skip login. Booking/result recovery follows approved user flows; a public link does not expose private details or grant appointment ownership.

Payment results are states within the booking/result surface, rather than separate public menu pages. After a hold exists, changes/abandonment follow the hold protections in the approved flows.

## Customer account hierarchy

Proposed account navigation: **نوبت‌های من · اطلاعات من**.

- **My appointments:** upcoming confirmed appointments first, with clear groups for pending/unconfirmed attempts and past/cancelled appointments. Pending payment and refund attention remain discoverable rather than disappearing with the hold.
- **Appointment/attempt detail:** service, specialist, volume/duration, date/time, accepted terms, price/deposit/balance, current appointment/payment/refund state and only permitted actions.
- **Actions from details:** reschedule, cancellation review, replacement acceptance/decline, current payment-status check, and salon contact. These are contextual steps, not unrelated menu destinations.
- **My information:** profile name and verified login number, with clear distinction from per-booking contact edits. Login-number change/recovery directs to salon coordination; no unapproved self-service ownership transfer.
- Sign-out is an account control. No wallet, loyalty, notification inbox, or forced credit system is introduced.

The original owning account controls private retrieval even if the appointment contact differs. Correcting a contact does not move a booking to that number's account.

## Salon operations hierarchy

Proposed default entry: **تقویم نوبت‌ها**. Use a shared calendar with day/date and specialist filters, and an adjacent appointment-list presentation when useful; do not make staff switch between separate source-specific calendars.

Reception-visible navigation:

- **Calendar/appointments:** today's appointments, selected date/specialist, booking-source and operational state where needed.
- **New appointment:** persistent action opening the approved telephone/future in-person/immediate walk-in intake; it need not be a separate main-menu page.
- **Follow-up:** a compact appointment-linked worklist for unresolved payment status, refund needs-attention, failed transactional SMS, and customer-response matters. Keep each item linked to its actual appointment/attempt; this is booking support, not accounting or CRM.
- **Appointment detail:** customer/service/time context and permitted reschedule/cancel/replacement operations, actual in-salon deposit/settlement receipt, contact correction/support routing, and communication/refund progress.

Manager-only navigation, within the same area:

- **Services:** prices/factors, directly bookable vs consultation-required status, service-relevant volume labels and durations.
- **Specialists:** profiles, eligibility and assignment priority.
- **Working schedules:** specialist availability inputs and conflicts with accepted appointments/active holds.
- **Booking settings:** salon-wide deposit percentage, payment-hold duration, cancellation/rescheduling window; show current defaults and effects on new bookings.
- **Staff access:** manager-assigned staff roles, without specialist dashboard access.
- Manager exceptions and ownership-support reviews are contextual actions attached to the relevant booking/account; they are not a standalone customer-facing policy.

Managers have reception capabilities. Reception may identify an issue but cannot edit manager settings or approve an exception. Unauthorized controls are unavailable, and access checks apply to direct links too.

## Conceptual sitemap

```text
Public site
├── Home
├── Services
│   └── Service detail → Booking / Consultation contact
├── Specialists
│   └── Specialist profile → Supported service → Booking
├── About salon and contact
└── Booking journey
    ├── Service / Volume / Specialist / Time
    ├── Sign-in and customer details
    ├── Final review
    └── Payment and result → Owning account details

Customer account
├── My appointments and booking attempts
│   └── Detail → Allowed changes / Status / Refund / Salon contact
└── My information → Salon-coordinated login-number support

Salon operations (reception + management)
├── Calendar / Appointments → New booking / Appointment detail
├── Follow-up → Appointment or attempt detail
└── Management only
    ├── Services
    ├── Specialists / Eligibility / Assignment priority
    ├── Working schedules / Conflicts
    ├── Booking settings
    └── Staff access
```

This is information hierarchy, not a commitment to one route per node.

## Cross-links and access boundaries

| Entry/context | Destination | Boundary/behavior |
| --- | --- | --- |
| Service detail | Eligible specialists or service booking | Public discovery; preserve service |
| Specialist profile | Supported service booking | Preserve named preference |
| SMS reception payment link | Review/payment attempt | Verify customer ownership before private review; current deadlines apply |
| Customer change/cancellation notice | Current appointment detail | Sign in and enforce original account ownership; show actual current state |
| Payment result | Account appointment/attempt detail | Include unconfirmed attempts and separate refund progress |
| Customer detail/recovery/consultation | Salon contact | Contact does not waive booking policies or prove ownership |
| Staff calendar/follow-up | Appointment detail | Role-based permitted actions |
| Conflicting manager schedule edit | Affected appointments | Resolve under approved rules before invalidating schedule save |
| Account or staff deep link | Intended surface after login | Enforce permissions; no navigation shortcut grants access |

Keep private customer details out of public pages and unauthenticated SMS-link previews. Salon staff access is separate from the customer's session.

## Flow coverage and next-stage requirements

- Online booking and payment outcomes map to public discovery, one booking journey, and account details.
- Reception bookings map to shared calendar/intake/detail; receipt and follow-up stay attached to appointments.
- Customer changes and salon proposals originate from details with clear original/proposed information.
- At-salon final price/volume coordination remains an operational detail, with no specialist dashboard.
- Identity correction/recovery and management exceptions are role-restricted contextual support actions.
- Service/schedule/settings edits sit in management controls with conflict review.

Stage 09 should enumerate necessary page/templates, steps, dialogs/drawers and important states from this hierarchy, without counting every payment status or service instance as a new page. Responsive navigation treatment and detailed visual/content decisions follow in their respective stages.

## Completion

Approved on 2026-10-03: the three-area structure, public/account navigation, the single booking journey, calendar-first salon operations, appointment-linked follow-up, and manager-only controls. Hierarchy, cross-links, access boundaries and the conceptual sitemap support the approved flows. Stage 08 is complete; proceed to Stage 09 — Page Inventory. These product-specific navigation choices are approved proposals, not generic requirements imposed by the workflow guide.
