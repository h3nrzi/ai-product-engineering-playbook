# Page & Surface Inventory — Women’s Beauty Salon Booking

## Status and basis

Stage 09 draft started on 2026-10-03. Derived from [approved information architecture](information-architecture.md), [user flows](user-flows.md), and [scope](product-scope.md). Page grouping and surface choices below are proposals for review; Stage 09 is not yet approved. Detailed UI states follow in Stage 10, and responsive/content/visual decisions follow their own stages.

Scope remains one physical women's salon. IDs identify design templates/surfaces, not mandated URL routes. One service-detail template serves all services; one specialist template serves all specialists; one appointment-detail template per audience serves their appointments and attempts. Booking steps, dialogs, and state variants do not inflate the page count.

Flow references below use sections F1–F9 of user-flows.md: online booking, payment, reception booking, customer changes, salon replacements/exceptions, at-salon settlement, identity/support, management settings, and refund/communication.

## Public and booking pages/templates

Audience/access: public except authenticated review/payment and private results as noted. All listed templates are required.

| ID / surface | Purpose and entry | Core content | Primary action | Secondary actions | Related flow / access |
| --- | --- | --- | --- | --- | --- |
| P01 Home | Introduce salon and provide a direct starting point; logo/direct entry | Salon identity, concise service/specialist entry points, essential location/contact | Reserve appointment | Browse services/specialists; contact salon; My appointments | F1; public |
| P02 Services list | Find a suitable service; public navigation/home | Actual service names, concise grouping when needed, fixed/approximate price and duration context | View service | Explore eligible specialists; contact for consultation | F1; public |
| P03 Service detail template | Understand one service and book correctly; list/direct/specialist link | Description, price basis/factors, duration/volume options, eligible specialists, prerequisites | Book service; consultation services instead show Contact salon | View eligible specialist; return to list | F1/F6; public |
| P04 Specialists list | Compare relevant salon specialists; navigation/home/service context | Profiles, expertise, supported services | View specialist | Browse services | F1; public |
| P05 Specialist profile template | Understand expertise and begin a named-specialist booking; list/service/direct link | Specialist information, supported services, booking eligibility | Select supported service and book | View service; return to list | F1; public |
| P06 About salon and contact | Locate/contact salon, consultation and support; navigation/footer/contextual contact links | Address, working/contact information, concise salon introduction and general booking-policy explanation | Contact salon | Start booking; directions through available address information | F1/F4/F6/F7/F9; public, no private appointment data |
| P07 Booking and result container | Complete one coherent reservation journey and retrieve current attempt outcome; booking actions/SMS payment link/payment return | Conditional steps in table below, progress, reviewed specialist/time, current payment/hold/refund outcome | Context-dependent Continue / Pay deposit / View appointment | Back; abandon unpaid selection as allowed; Check status; salon contact | F1/F2/F3; discovery public, review/payment/results require owning customer access |

The general policy explanation is a section of P06 plus linked booking-review content, not an extra legal/policy page. Existing appointment terms, shown in details, remain authoritative.

## Customer pages/templates

Audience/access: authenticated customer; own information and original-owned appointments only. All are required. Signed-out direct links return to their intended surface after SMS login.

| ID / surface | Purpose and entry | Core content | Primary action | Secondary actions | Related flows |
| --- | --- | --- | --- | --- | --- |
| P08 My appointments and attempts | Retrieve current/past appointments and interrupted payment attempts; public My appointments/account entry | Upcoming confirmed appointments first; clearly separated pending/unconfirmed attempts and past/cancelled records; payment/refund attention | Open appointment/attempt | Start new booking; view My information | F2/F4/F5/F9 |
| P09 Customer appointment/attempt detail template | Understand authoritative status and act on this exact appointment; P08/result/SMS deep link | Service, volume/duration, specialist/time, saved terms, deposit/balance, separate appointment/payment/refund state, current replacement proposal | Most relevant permitted action: view/status/reschedule/accept proposal | Cancel with consequence review; decline proposal; contact salon; return to list | F2/F4/F5/F9; actions vary by actual state and cutoff |
| P10 My information | Show profile defaults/login identity and distinguish them from appointment contact; account navigation | Profile name, verified login number, explanation of per-booking contact, salon-coordinated number-change/recovery route | Contact salon for login-number support when needed | Return to appointments; sign out | F1/F7; no automatic ownership-transfer editor |

Name/contact edits for a booking remain in P07/P09 contextual surfaces. A profile/login-number change is not triggered by those edits. No wallet, mandatory credit, loyalty page, or separate notifications inbox is required.

## Salon operations pages/templates

Reception and management share the operations area. All are required; actual action access follows the assigned role.

| ID / surface | Audience/access | Purpose and entry | Core content | Primary action | Secondary actions | Related flows |
| --- | --- | --- | --- | --- | --- | --- |
| P11 Staff sign-in | Public entry, operations access only after assigned-role check | Enter staff area; direct operations link/known staff entry | Mobile/SMS steps, role check, expired/invalid code or no-permission result | Verify/sign in | Correct mobile; resend as permitted; contact manager | F7 |
| P12 Calendar and appointments | Reception/manager | Default operations entry; review daily shared schedule | Date/day and specialist filters, shared appointment/calendar list, source/state, full duration and conflicts | New appointment / Open appointment | Change date/filter; follow-up entry | F3/F4/F5/F6 |
| P13 Staff appointment/attempt detail template | Reception/manager, with manager-only actions restricted | Coordinate exact booking; calendar/follow-up/deep link | Customer contact, service/time, saved terms, payment source/progress, proposals, actual receipts, communication and refund progress | Relevant permitted booking/receipt action | Reschedule/cancel/propose replacement; intake correction/support routing; manager exception where authorized | F3–F7/F9 |
| P14 Appointment-linked follow-up | Reception/manager | Find actionable booking issues; operations navigation/calendar cue | Unknown payments, refund needs-attention, failed SMS, customer-response issues, each linked to appointment/attempt | Open item and resolve through its detail | Filter current issues; return to calendar | F2/F5/F7/F9; no financial reporting or CRM |

The P12 calendar and list are alternate presentations of the same shared data, not separate source-specific calendar pages. P14 is a compact operational worklist, not a new reminder/automation system.

## Manager-only pages/templates

Required, inside the same operations navigation; reception cannot access them by menu or direct link.

| ID / surface | Purpose and entry | Core content | Primary action | Secondary actions | Related flow |
| --- | --- | --- | --- | --- | --- |
| P15 Services management | Maintain accurate service information; manager navigation | Service list, prices/factors, directly-bookable/consultation status, volume labels and durations | Add/edit service information | Preview public service; cancel unsaved edits | F8 |
| P16 Specialists management | Maintain profiles, service eligibility and assignment priority; manager navigation | Specialist list/detail, supported services, manager priority order | Add/edit specialist or save eligibility/priority | Preview profile; view schedule | F8 |
| P17 Working schedules and conflicts | Control bookable intervals without invalidating accepted appointments; manager navigation/specialist context | Specialist working intervals, affected bookings/holds and blocking conflicts | Review/save valid schedule | Open affected appointment; discard unsaved edits | F5/F8 |
| P18 Booking settings | Maintain salon-wide rules; manager navigation | Deposit percentage, payment-hold duration, cancellation/rescheduling window, approved defaults and new-booking effect | Save reviewed valid settings | Restore unsaved values; view rule explanation | F8 |
| P19 Staff access and ownership-support context | Assign staff permissions and handle authorized account support; manager navigation/support routing | Assigned staff roles, access edits, contextual support request/evidence review linked to relevant customer/booking | Save access / Apply verified support action | Deny or leave request pending verification; cancel edits | F7; customer ownership transfer never follows from field editing alone |

Separate editing pages per service/specialist are not required by this inventory: list + detail editor can use one reusable panel/surface. Contextual manager support and exceptions need not be extra main-navigation pages.

## Booking steps inside P07

These are required steps/states of one journey, not seven mandatory routes. A customer login component is reused rather than duplicated as another public content page.

| Surface | Condition/access | Core content | Primary / secondary action | Flow |
| --- | --- | --- | --- | --- |
| B01 Service selection | Public; preselected from service/specialist entry | One eligible directly bookable service | Continue / Change service, consultation contact when required | F1 |
| B02 Volume selection | Public; only duration-varying services | Manager-defined labels/descriptions and duration | Continue / Back | F1 |
| B03 Specialist selection | Public | Named eligible staff and Any eligible specialist | Continue / Back | F1 |
| B04 Date/time selection | Public | Full-duration valid slots for current preference | Select time / Other date, back | F1 |
| B05 Sign-in and booking information | Login if needed; then original customer account | SMS login, profile-prefilled name/contact, service-required data, different-contact SMS check | Verify/Continue / Correct or retry; back preserving choices | F1/F7 |
| B06 Final review | Authenticated owner; different contact verified if applicable | Actual specialist, service/volume/duration/time, fixed/approximate basis, exact deposit, balance/estimate, saved cancellation terms and deadline information | Pay deposit / Edit choices under hold protections | F1/F2 |
| B07 Payment/status/result | Owner; valid/current attempt | Current authoritative state, actual hold/review deadline, confirmation details or pending/expired/failure/refund information | View appointment / Check status, valid retry/new booking, contact salon as permitted | F2/F9 |

Payment-card entry happens at the payment provider, not a salon-built card form. That external screen is not counted as a product page/template.

## Contextual dialogs, drawers, and operation steps

All are required where their triggering flow applies; implementation can use inline steps or dialogs according to space/access needs. These are not new main-menu destinations.

| Surface | Host/entry and audience | Content/purpose | Primary / secondary action | Flow |
| --- | --- | --- | --- | --- |
| C01 Customer SMS login/contact verification | P07/customer deep link; customer | Target mobile, code, resend/error context; distinguish login from contact check | Verify / Correct mobile, retry, return | F1/F7 |
| C02 Reception new-booking intake | P12; staff | Name/contact, service/volume/preference/time, source-specific deposit route and final review | Create/send SMS and start hold / Record actual in-salon receipt or immediate walk-in; cancel | F3 |
| C03 Reschedule selection and review | P09/P13; owner or authorized staff | Original retained booking, valid replacement time, unchanged terms and new cutoff | Confirm replacement / Back or abandon | F4 |
| C04 Cancellation consequence review | P09/P13; permitted actor | Exact appointment, refund/no-refund consequence and separate refund state | Confirm cancellation / Keep appointment | F4/F5 |
| C05 Salon replacement proposal/review | P13 staff; P09 owner response | Original/proposed time or specialist and availability; explicit consent | Propose / Accept or decline, as actor permits | F5 |
| C06 Manager late exception | P13; manager only | Reason, exact action, availability and refund consequences | Apply authorized exception / Cancel | F5 |
| C07 Receipt and final settlement | P13; staff coordinating specialist/customer | Actual in-salon deposit/final price, agreed amount less deposit, payment source | Record actual receipt / Correct unsaved entry, cancel | F3/F6 |
| C08 Volume mismatch resolution/cancellation | P13; staff coordinating specialist/customer | Fixed booked time/duration, agreed in-slot solution or full-refund cancellation when none fits | Record outcome / Customer-chosen separate booking | F6 |
| C09 Confirmed-number correction/ownership review | P13/P19; authorized actor, manager transfer/recovery | Separate contact vs ownership, authorization, chosen-number verification, review evidence/reason | Apply verified correction / Pending/deny if evidence insufficient | F7 |
| C10 Refund progress/follow-up | P09 read-only owner; P13/P14 staff | Entitlement, amount/source, current progress, actual receipt/reference or needs-attention | Authorized processing/check status / Contact or follow-up | F9 |
| C11 Transactional SMS retry | P13/P14; staff | Failed sending/delivery and current link/notice validity | Retry same valid item / Follow up with customer; never reset hold | F3/F5/F9 |
| C12 Management edit and conflict review | P15–P19; manager | Current/proposed values, validation, affected appointments/holds | Save only when valid / Resolve affected appointment or discard | F8 |

Actions record actual operation success, not merely a button click. Disable repeated submission while applying an operation; unknown outcomes go to current status rather than a blind second mutation.

## Important states to develop in Stage 10

- Empty service/eligible-staff/availability results, loading, stale slot conflicts, and recovery with preserved choices.
- SMS invalid/expired code, session expiry, verified account but missing staff role, and denied private deep links.
- Separate awaiting-deposit/confirmed/expired/cancelled/completed/no-show appointment states, current payment result, and refund due/pending/completed/needs-attention states.
- Expired payment link, failed SMS delivery, unknown payment with retained vs released slot, and late verified success/refund.
- Reschedule/cancellation processing, failed or unknown action, declined/unanswered replacement, and original booking preservation.
- Manager invalid settings, conflicting schedule, insufficient ownership evidence, and operation save failure.
- Mobile/RTL long content, clear labels, keyboard/touch access, and readable price/time/status presentation.

These are variants of the retained surfaces rather than extra pages.

## Reusable content and controls

Reuse service and specialist summaries, appointment/attempt cards, date/time selection, price/deposit/terms summary, SMS verification, status feedback, and contextual action review. Use distinct customer/staff permissions while sharing authoritative booking information. Exact visual component design belongs to the design-system stage.

## Scope and page-count interpretation

The inventory contains 19 required page/template groups, with conditional booking steps and contextual operation surfaces. This does not mean 19 distinct URL routes or separate pages for every edit/state. The requirement is coverage of user needs, not a target route count.

Separate About and Contact pages, general dashboard charts, wallet/loyalty, a notification inbox, a specialist dashboard, full accounting/POS, CRM, marketplace, and multi-service booking pages are not required. Creating them would add scope beyond approved needs. Optional decorative content surfaces are not necessary for completion.

## Review/completion condition

Review the page/template grouping and the contextual surface boundaries. Each retained surface has a user/operational purpose, entry, content, actions, access and related flow. Stage 09 can complete after user approval of this inventory; Stage 10 then defines its meaningful states and edge cases.
