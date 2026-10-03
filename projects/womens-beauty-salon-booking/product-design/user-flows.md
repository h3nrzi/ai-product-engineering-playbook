# User Flows — Women’s Beauty Salon Booking

## Status and authority

Stage 07 approved and completed on 2026-10-03. After individually approving the online-booking sequence and payment-result presentation, the user explicitly delegated the remaining proposals and stage closure to the guide. The guide finalized and reviewed the flows below under that authorization.

This document turns [approved jobs and journeys](jobs-and-journeys.md) into screen-level product flows. Approved scope, customer rights, account ownership, accepted terms, specialist consent, and payment rules remain authoritative. Provider-specific operations and technical security controls belong to engineering, rather than unresolved screen-level product decisions.

Scope: one physical women's salon; one service and one specialist per appointment; customer account and salon operations area; no specialist dashboard, multi-service booking, or scheduled reminders.

## Shared rules

- Browse services, specialists, and availability publicly; authenticate customers by mobile/SMS before review/submission.
- Name/contact are minimum intake. Prefill known profile data and request extra service-specific data only for a justified need.
- A different booking contact needs SMS verification before payment/confirmation, without changing the original account's login or booking ownership.
- Service/volume/specialist changes before booking require dependent availability to be rechecked. Preserve useful selections through login and recoverable errors.
- Any-eligible selection combines valid availability, then assigns by management priority. Display the actual specialist before payment/confirmation; a named preference is honored.
- Full-duration schedule, eligibility, appointments, and active holds constrain all booking sources.
- Initial defaults: 20% deposit; 24-hour advance cancellation/rescheduling window; 10-minute payment hold; up to 5 additional minutes after hold expiry for a payment started in time whose result remains unknown.
- Before a hold exists, back navigation preserves valid choices. After holding but before payment starts, explicitly abandon/release the unpaid hold before changing its service/time/specialist and securing a new reviewed hold. Once payment is initiated or unknown, do not switch that attempt to another slot; show its status until a definitive result or deadline release. Revisiting screens never restarts deadlines.
- Accepted price/policy terms belong to the booking. Later management settings do not rewrite them.
- Payment, appointment, and refund outcomes are displayed separately. Pending payment is not confirmation; cancellation is not proof of a completed refund.
- SMS carries reception payment links and change/cancellation notices; details/payment status are also available in the customer account.

## 1. Customer books online

**Approved on 2026-10-03:** service → volume when relevant → named/any-eligible specialist → time → sign in/review customer details → final review → pay deposit → result. Service, volume, specialist, and time are sequential steps in one booking journey. Customers may go back while retaining valid selections; changes affecting availability require the time to be rechecked. Step grouping does not mandate separate routes.

**Actor/trigger:** customer chooses a service from discovery or a specialist profile.  
**Preconditions:** directly bookable service with configured price, eligible staff, and duration options.

1. Service detail: show description, fixed/approximate price basis, duration information, and relevant conditions.
2. Consultation branch: if genuinely consultation-dependent, show salon contact instead of direct booking.
3. Volume step: select a manager-defined option when duration varies; fixed-duration services skip it.
4. Specialist step: named eligible specialist or any eligible specialist.
5. Time step: show full-duration valid times; for any eligible, assign the actual specialist by management priority after time selection.
6. Sign-in/details step: mobile/SMS login if needed; preserve choices; prefill name/contact; verify a different contact separately.
7. Review step: show service, volume/duration, actual specialist, time, price basis, exact deposit, balance/estimate, accepted policies, and payment deadlines.
8. Customer selects “Pay deposit” (پرداخت بیعانه) on final review: recheck availability and secure a hold for the reviewed specialist/time; save accepted terms and start the 10-minute payment window when the hold is successfully secured. If the slot cannot be secured, preserve input and return to valid time selection without presenting it as held. Browsing, login, or opening final review does not start this hold. The payment-button trigger is approved.
9. Payment/status step: follow flow 2.
10. Success: show confirmed details, deposit, remaining balance, and My appointments.

**Branches/recovery:** no availability → another date or customer-chosen specialist; changed assignment before hold → review the changed name; SMS error → retry/correct without losing choices; slot conflict → preserve input and choose a valid time; session expiry → sign in and recheck. Back navigation preserves valid intent and invalidates dependent selections when needed. Browsing or SMS verification alone does not hold a slot.

**Exit:** confirmed appointment, recoverable unconfirmed draft, or explicit unavailable/expired result. Customer ownership and salon calendar reflect successful confirmation only.

## 2. Payment result and hold

**Actor/trigger:** customer begins deposit payment under a valid hold.  
**Preconditions:** reviewed terms, verified booking contact where required, and valid ownership of the specialist/time.

| Result/event | Booking/availability action | Customer view |
| --- | --- | --- |
| Verified success while held | Confirm reviewed specialist/time | Confirmed details and recorded deposit |
| Definitive failure | Release hold; no confirmation | Failure and route to recheck availability |
| No payment started by hold expiry | Release slot | Expired hold; choose from current availability |
| Started in time, result unknown | Keep slot while checking until verification deadline | Awaiting payment result; check existing attempt before retry |
| Still unknown at verification deadline | Release slot; payment remains under verification | Unconfirmed booking and pending payment outcome |
| Success verified after slot release | Full deposit refund; no automatic confirmation even if slot is free | Payment/refund progress and optional new booking |

### Approved payment-result presentation

Approved by the user on 2026-10-03. Display the verified result and available actions without changing the hold/confirmation rules above:

| Screen state | Customer message | Information and action |
| --- | --- | --- |
| Verified success while held | «نوبت شما تأیید شد» | Service, specialist, date/time, recorded deposit, and «مشاهده نوبت» |
| Definitive failure | «پرداخت انجام نشد؛ نوبت تأیید نشده» | «بررسی زمان و پرداخت دوباره»; recheck availability and secure a valid hold before another attempt |
| Payment result unknown while held | «در حال بررسی پرداخت هستیم» | Show whether the slot remains held and its verification deadline; allow checking status, without inviting a repeat payment |
| Hold/verification deadline expired and slot released | «زمان رزرو آزاد شد» | Show the unconfirmed booking; if payment remains unknown, show its ongoing verification separately rather than calling it failed |
| Success verified after slot release | «پرداخت دریافت شد، اما نوبت تأیید نشد؛ بیعانه کامل بازگردانده می‌شود» | Show actual refund progress separately and a route to a new booking from current availability |

Closing the result screen does not lose the outcome. After signing in, the original customer account can retrieve the same current booking-attempt, payment, and refund status, including unconfirmed attempts. Customer-facing wording must reflect the current authoritative status; a promised refund is not a completed refund. An unknown existing payment must be checked before retrying, without encouraging duplicate payment or booking.

At initial defaults, hold creation at 14:00 means 14:10 ordinary expiry and 14:15 maximum pending-result deadline. Success/failure acts immediately when definitive. Link reopening and status checks never restart deadlines.

**Recovery:** distinguish unavailable status-check service from definitive payment failure. Keep the last known outcome visible with «بررسی دوباره وضعیت» and salon contact if checking is unavailable. Do not invite a duplicate deposit while the existing attempt remains uncertain. Show the ordinary hold deadline and, when relevant, the final verification deadline in local date/time with remaining time. An unavailable gateway does not extend those deadlines. Technical checks/retry cadence and provider compatibility remain engineering tasks; refund behavior is defined in flow 9.

## 3. Reception creates a booking

**Actor/trigger:** staff creates a telephone, future in-person, or immediate walk-in appointment.  
**Preconditions:** mobile/SMS staff session with management-assigned reception or manager access.

1. Shared calendar/create screen: enter customer name/contact; select service, relevant volume, specialist preference, and valid time.
2. Review: show actual assigned specialist, duration, price basis, deposit, and applicable policies; communicate the specialist to the customer.
3. Telephone/link-payment branch: finalize initial booking and request SMS link sending; start the hold at that action. Customer opens link, authenticates for the recorded number, reviews, and pays through flow 2.
4. Future in-person branch: use the link route, or explain terms, receive the calculated deposit, and record actual amount/source before confirmation.
5. Immediate walk-in branch: check valid immediate availability, record the visit, and collect payment during the visit; no advance deposit.
6. Result: update shared calendar; customer access still requires verified ownership.

**Branches/recovery:** correct mistyped numbers before confirmation; confirmed-number correction/access transfer uses flow 7. Link opening does not extend holds. Show SMS sending/delivery status separately from booking/payment state; allow staff to retry the same link while its hold is valid without resetting expiry. If expiry passes, label the link expired and require fresh availability/review for a new attempt. Correcting the intake number does not bypass authentication. Preserve intake on conflicts. Reception cannot waive future deposits, change settings, or assert that uncertain online payment succeeded.

## 4. Customer retrieves, reschedules, or cancels

**Actor/trigger:** My appointments or booking-result link.  
**Preconditions:** valid customer session and appointment ownership; a link/reference does not grant access.

1. List → appointment detail: show service/specialist/time, appointment state, deposit, policies, and permitted actions.
2. Reschedule branch within stored cutoff: choose a valid new time → review new details/deadline → confirm replacement → transfer deposit without another charge. Keep the original slot/deposit until replacement succeeds; failure leaves them intact.
3. Keep original accepted terms; calculate the new cutoff from the new appointment time using the original window. Service/volume changes are not included in this rescheduling path.
4. Cancellation branch: show refund consequences → deliberate confirmation → cancel successfully → release availability → show separate refund progress.
5. After cutoff: online rescheduling is unavailable; show salon contact and the applicable late/no-show policy. Contact alone does not waive it.

**Cutoff:** use the appointment’s stored deadline; a customer action completed at or before that deadline qualifies. Recheck the deadline when applying the action, not just when the screen opened. After it, disable online rescheduling; customer cancellation remains available with the disclosed no-refund consequence, or the customer can contact reception for a manager-reviewed exception. A replacement may be any valid future time; show its recalculated deadline before confirmation, including when that deadline has already passed. Keep original terms.

**Recovery/exit:** while applying an action, show processing and prevent duplicate submission. A failure preserves the original appointment/deposit; an unknown outcome directs the customer to check current appointment status before retrying. Back or cancel before committing leaves the original untouched. Success displays the replacement or cancellation/refund state and updates salon availability; SMS change/cancellation notice failure does not undo the operation.

## 5. Salon replacement, cancellation, or late exception

**Actor/trigger:** reception/management handles an affected appointment or a late-change request.

- Replacement: check original appointment/deposit → find valid alternative → communicate proposed time/specialist → obtain explicit customer acceptance → recheck availability → apply replacement and send SMS outcome.
- Customer declines a salon replacement or salon cancels: full refund of deposit actually paid, irrespective of customer cutoff and online/in-salon payment source.
- No reply with deliverable original: retain original confirmed booking; do not apply replacement.
- No reply with undeliverable original: salon cancellation and full refund; do not leave appointment unresolved awaiting response.
- Late customer exception: reception routes to management → manager reviews and records reason for any authorized late change/refund → applies permitted operation. Reception cannot grant the exception independently.

**Acceptance/recovery:** show the original and proposed details together in the customer account, with Accept/Decline actions. For telephone/in-person acceptance, staff explicitly records the customer's agreement, channel, time, and reviewed replacement details; do not infer agreement from SMS delivery. Recheck the alternative when applying it; a conflict returns to proposing another valid option without replacing the original. A proposal alone does not reserve alternative availability indefinitely. If the original cannot be delivered, its cancellation/refund entitlement must not wait for customer response.

**Exception control:** only management sees an approval action; require a reason and a review of the exact booking, replacement/refund consequence, and affected availability. A failed exception action does not partially change the appointment or deposit. It does not authorize staff to fake an online payment or waive account ownership checks.

**Exit/cross-actor effects:** show the final appointment and separate refund progress, update the calendar, and send SMS change/cancellation notices. If SMS fails, retain the actual appointment outcome and flag the communication for staff follow-up. Silence is not consent or customer cancellation. Refund processing follows flow 9.

## 6. At the salon: final price and volume mismatch

**Actor/trigger:** specialist coordinates with customer before service; reception records appointment/payment outcome.

1. For an approximate-price service, communicate and obtain acceptance of final price before beginning.
2. Settle final price less deposit already paid; example: 1,000,000 toman final price minus 200,000 deposit means 800,000 payable at salon.
3. If selected volume was inaccurate, keep booked start time and duration unchanged; specialist resolves the mismatch with the customer within that interval without delaying/overlapping the next appointment.
4. If no solution fits, cancel with full deposit refund. A separate new booking is the customer's choice, with current availability; never extend or automatically move the existing booking.

**Exit/recovery:** record the agreed final price, the deposit credited, and the actual remaining payment received. If the customer declines the final price, do not start work; route to specialist/reception coordination without automatically charging or changing booked time. Apply an existing cancellation/refund rule only when its conditions hold, or request a manager exception. If the volume mismatch cannot be resolved, use the already approved full-refund cancellation rather than treating it as a late customer cancellation. Customer and salon see the same final appointment/payment state; no specialist product login is needed.

No excess-deposit refund/credit flow is introduced; that question was withdrawn. Technical receipt/refund operations continue in engineering.

## 7. Staff access, number correction, and customer recovery

**Actors/entry:** staff sign-in; intake correction; manager-assisted number correction; customer salon-contact recovery request. Entry is the staff login or an appointment/account support action. A valid staff role is required for operational actions.

### Staff sign-in

Mobile → SMS code → verify → check management-assigned role → permitted operations. Wrong/expired code offers correction/retry. A verified number with no staff role receives no operations access. Session expiry returns to staff login; preserve non-sensitive work where practical and recheck permissions/availability before saving. Only management assigns or changes staff access; lack of authority ends the flow without a partial save.

### Customer matching and contact correction

- Match staff-created appointments through verified mobile ownership, not a name match. Until customer verification, staff-entered numbers are intake data, not proof of an authenticated account.
- Before confirmation, correct intake details and require verification of the chosen number where applicable. For a held booking, a correction neither resets the deadline nor declares payment successful; any started/unknown payment must retain its existing ownership and be checked before replacement.
- For a confirmed online booking, distinguish changing its contact from changing account ownership. The original owner can verify a new contact within their session; ownership stays unchanged.
- Staff correcting a confirmed contact records the reason and obtains customer authorization plus SMS verification of the intended new contact before applying it. Where the original owner cannot be authenticated, route to manager-assisted recovery; do not grant another account access by editing the field.
- For a staff-created appointment with an incorrectly recorded owner number, management handles a separate access-correction request. Verify the requesting customer, the intended mobile, and their entitlement to the specific appointment; record evidence and reason, notify affected verified channels, then correct access. A booking reference or SMS to the intended number alone is insufficient proof of entitlement.

### Manager-assisted login-number change and recovery

Customer contacts/visits salon → manager opens support request → authenticates existing owner and verifies intended new mobile → shows affected account/appointments → customer explicitly accepts → manager records reason and applies the change → customer signs in again and checks access. Verify the original number by SMS when available. If it is unavailable, the request remains in manual identity review until management independently verifies the existing owner using established salon records and independently confirmed customer identity; merely supplying a new number, name, booking reference, or payment reference is insufficient. If ownership cannot be established, deny access transfer and explain the next support step; do not merge accounts or expose appointments. Conflicting existing-account numbers require manual resolution rather than automatic account merging.

**Back/recovery/exit:** cancel before applying leaves account/contact unchanged; failed verification preserves the request without granting access; an unknown change outcome requires checking current account status before retry. Success shows the verified contact or corrected account access, with the appropriate customer sign-in. Contact verification never signs into another account. Engineering must establish concrete independent identity-evidence procedures, security controls, and audit storage before enabling manual transfer; this product flow explicitly supports a denied/pending verification outcome.

## 8. Management maintains service and schedule information

**Actor/trigger:** manager edits service, prices/factors, volume labels/durations, eligibility, priority, schedule, or shared policy settings.

1. Inspect current values and affected bookings.
2. Edit manager-controlled information; identify genuine consultation prerequisites and expose salon contact instead of direct booking.
3. Validate entries and show any schedule conflicts.
4. If a schedule change would invalidate confirmed appointments, resolve affected appointments through flow 5 before saving the conflicting change.
5. Review/save; verify resulting public availability. Existing accepted terms and active hold deadlines remain intact.

**Conflict/recovery:** list affected appointments with customer/service/time and the conflicting change. Block that schedule save until affected bookings have valid accepted replacements or cancellations under flow 5. Include active holds in availability checks; edits must not invalidate or silently reassign them. Unsaved edits can be abandoned; failed validation/save preserves the prior published settings and keeps input for correction. Recheck conflicts at save time. Display success and current values after a successful save.

**Validation:** require a positive price basis and duration, nonempty volume labels, a priority ordering without duplicate specialists, and coherent working intervals. Deposit percentage must be greater than 0 and at most 100; hold duration must be positive and the cancellation window nonnegative. Reception cannot change these settings. Configuration values are supplied by management; retain the approved initial defaults. Settings changes affect new bookings only.

**Money presentation:** use toman in customer-facing displays; calculate the percentage and round once to the nearest whole toman, with half-toman rounded upward, before displaying/charging the exact deposit. Keep that saved amount throughout payment. Conversion to a provider's required unit is an engineering operation and must preserve the displayed payable amount.

**Exit/cross-actor effects:** successful saves update valid public availability and new-booking terms without modifying accepted appointment terms. Failed/abandoned edits do not change customer booking options.

## Appointment, payment, and refund states

Separate appointment, payment, and refund dimensions; show the same authoritative result to the owning customer and authorized salon staff.

| Appointment state | Availability and permitted transitions |
| --- | --- |
| Awaiting deposit | Valid hold blocks the reviewed interval; verified online deposit or actual eligible in-salon receipt confirms; definitive failure or deadline release expires the attempt |
| Expired/unconfirmed attempt | No calendar reservation; payment may remain under verification; late success leads to refund, never confirmation |
| Confirmed | Reserved interval; allowed reschedule replaces only on success; permitted cancellation releases it; staff may record service completion or no-show |
| Cancelled | No booked interval; refund entitlement/progress shown separately; not restored by SMS retry or late payment |
| Completed | Service and final settlement recorded; no customer booking changes |
| No-show | Staff records missed visit after its time; default deposit policy applies, with management-only reasoned exceptions |

Immediate walk-ins enter Confirmed after staff verifies immediate availability and records the visit, with payment due during the visit; this is not a future-booking deposit bypass. A pending replacement is shown as a proposal alongside the original confirmed booking.

Payment states: not started, initiated/result unknown, verified success, definitive failure. Online payment status comes from authoritative verification; staff may only record money actually received at the salon as a distinct source.

Refund states: not applicable, due/pending, completed, needs attention. Never label a refund completed merely because cancellation succeeded or a request was sent. A failure retains the entitlement and flags follow-up.

## 9. Refund and transactional communication

**Actors/entry:** system/authorized staff following an approved refund entitlement or a reasoned manager exception; customer views progress in account details.

1. Successful qualifying cancellation or late payment creates a refund entitlement for the applicable amount; no second customer request is needed for already approved full refunds.
2. Prefer return to the original payment source. Online refunds use the provider route when supported; if unavailable, flag authorized salon follow-up and independently verify the original payer/recipient before a documented manual return. An in-salon deposit follows a documented salon refund route.
3. Show amount, source, pending/completed/needs-attention status, and any actual available timing information. No unsupported instant-refund promise or automatic credit substitution.
4. Mark completed only after verified return or documented actual in-salon/manual refund receipt. Record reference, amount, and time; retry/follow-up must not refund the same entitlement twice.
5. Customer sees progress after re-login; staff see outstanding refunds. If processing fails, preserve entitlement and offer salon contact rather than rewriting the cancellation result.

**SMS:** send links and change/cancellation outcome notices to the appointment's approved contact. Do not include authentication codes or sensitive payment details in booking notices. Delivery status is independent of operation success. Retry the existing valid link/notice without recreating a booking, repeating a refund, or moving deadlines. If delivery fails, staff sees needs-follow-up and can coordinate with the customer; the authenticated account remains the route to current details. A delayed SMS must lead to current status, not imply an expired hold remains valid.

## Completed review and engineering handoff

### Product review completed

The guide checked all core journeys for actors, entry points, preconditions, decisions, alternate/error paths, preservation/recovery, outcomes, permissions, and customer/salon effects. The flows preserve the approved specialist choice/consent, fixed booked time for volume mismatches, account ownership, payment deadlines, cancellation/refund entitlements, and existing accepted terms. No specialist dashboard or scheduled reminder system is added.

### Engineering/configuration handoff

Implement authoritative availability and operation outcomes, actual provider verification/refund support, deduplication, SMS delivery, session/security controls, concrete independent identity-evidence procedures for manual recovery, and audit records. Validate the 10+5-minute payment timing against the selected provider; any required change to customer rights or approved behavior returns for approval. Management supplies actual service prices, factors, volume labels/durations, specialist eligibility, schedules, and priority.

These are implementation/configuration work, not unresolved Stage 07 flow decisions. Do not enable an unverified ownership-transfer path or label an unverified payment/refund successful.

## Completion

Stage 07 is complete on 2026-10-03 under the user's explicit authorization to finalize it using the guide's recommendations. Core flows and meaningful recovery are defined sufficiently to derive navigation and required surfaces. Proceed to Stage 08 — Information Architecture; do not mark that next stage complete without its artifact and review.

