# User Flows — Women’s Beauty Salon Booking

## Status and authority

Stage 07 draft in progress, started on 2026-10-03 after the user approved and completed Stage 06. The online-booking step sequence, sequential selection steps, back-navigation preservation/revalidation, payment-button hold trigger, payment-result screen presentation, and account retrieval of payment/refund outcomes are approved on 2026-10-03; other screen/state details still require review. This document translates [approved jobs and journeys](jobs-and-journeys.md) into proposed screen-level flows. Approved business rules remain authoritative; screen grouping, exact states, recovery mechanics, and deferred operational details below require Stage 07 review. No application implementation is introduced.

Scope: one physical women's salon; one service and one specialist per appointment; customer account and salon operations area; no specialist dashboard, multi-service booking, or scheduled reminders.

## Shared rules

- Browse services, specialists, and availability publicly; authenticate customers by mobile/SMS before review/submission.
- Name/contact are minimum intake. Prefill known profile data and request extra service-specific data only for a justified need.
- A different booking contact needs SMS verification before payment/confirmation, without changing the original account's login or booking ownership.
- Service/volume/specialist changes before booking require dependent availability to be rechecked. Preserve useful selections through login and recoverable errors.
- Any-eligible selection combines valid availability, then assigns by management priority. Display the actual specialist before payment/confirmation; a named preference is honored.
- Full-duration schedule, eligibility, appointments, and active holds constrain all booking sources.
- Initial defaults: 20% deposit; 24-hour advance cancellation/rescheduling window; 10-minute payment hold; up to 5 additional minutes after hold expiry for a payment started in time whose result remains unknown.
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

**Recovery:** distinguish unavailable status-check service from definitive payment failure. Do not invite a duplicate deposit while the existing attempt remains uncertain. Exact checks, retry cadence, deadline configuration/disclosure, provider compatibility, and refund execution are deferred.

## 3. Reception creates a booking

**Actor/trigger:** staff creates a telephone, future in-person, or immediate walk-in appointment.  
**Preconditions:** mobile/SMS staff session with management-assigned reception or manager access.

1. Shared calendar/create screen: enter customer name/contact; select service, relevant volume, specialist preference, and valid time.
2. Review: show actual assigned specialist, duration, price basis, deposit, and applicable policies; communicate the specialist to the customer.
3. Telephone/link-payment branch: finalize initial booking and request SMS link sending; start the hold at that action. Customer opens link, authenticates for the recorded number, reviews, and pays through flow 2.
4. Future in-person branch: use the link route, or explain terms, receive the calculated deposit, and record actual amount/source before confirmation.
5. Immediate walk-in branch: check valid immediate availability, record the visit, and collect payment during the visit; no advance deposit.
6. Result: update shared calendar; customer access still requires verified ownership.

**Branches/recovery:** correct mistyped numbers before confirmation; confirmed-number correction/access transfer uses flow 7. Link opening does not extend holds. SMS delivery failure/retry is deferred and must not silently reset a deadline. Preserve intake on conflicts. Reception cannot waive future deposits, change settings, or assert that uncertain online payment succeeded.

## 4. Customer retrieves, reschedules, or cancels

**Actor/trigger:** My appointments or booking-result link.  
**Preconditions:** valid customer session and appointment ownership; a link/reference does not grant access.

1. List → appointment detail: show service/specialist/time, appointment state, deposit, policies, and permitted actions.
2. Reschedule branch within stored cutoff: choose a valid new time → review new details/deadline → confirm replacement → transfer deposit without another charge. Keep the original slot/deposit until replacement succeeds; failure leaves them intact.
3. Keep original accepted terms; calculate the new cutoff from the new appointment time using the original window. Service/volume changes are not included in this rescheduling path.
4. Cancellation branch: show refund consequences → deliberate confirmation → cancel successfully → release availability → show separate refund progress.
5. After cutoff: online rescheduling is unavailable; show salon contact and the applicable late/no-show policy. Contact alone does not waive it.

**Exit:** preserved original appointment, successful replacement, or cancelled appointment with refund state. Exact cutoff-boundary behavior and action-state design continue in review.

## 5. Salon replacement, cancellation, or late exception

**Actor/trigger:** reception/management handles an affected appointment or a late-change request.

- Replacement: check original appointment/deposit → find valid alternative → communicate proposed time/specialist → obtain explicit customer acceptance → recheck availability → apply replacement and send SMS outcome.
- Customer declines a salon replacement or salon cancels: full refund of deposit actually paid, irrespective of customer cutoff and online/in-salon payment source.
- No reply with deliverable original: retain original confirmed booking; do not apply replacement.
- No reply with undeliverable original: salon cancellation and full refund; do not leave appointment unresolved awaiting response.
- Late customer exception: reception routes to management → manager reviews and records reason for any authorized late change/refund → applies permitted operation. Reception cannot grant the exception independently.

Silence is not consent or customer cancellation. Show cancellation and refund progress separately. Exact acceptance capture, notification failures, exception controls, and refund route/timing continue in Stage 07.

## 6. At the salon: final price and volume mismatch

**Actor/trigger:** specialist coordinates with customer before service; reception records appointment/payment outcome.

1. For an approximate-price service, communicate and obtain acceptance of final price before beginning.
2. Settle final price less deposit already paid; example: 1,000,000 toman final price minus 200,000 deposit means 800,000 payable at salon.
3. If selected volume was inaccurate, keep booked start time and duration unchanged; specialist resolves the mismatch with the customer within that interval without delaying/overlapping the next appointment.
4. If no solution fits, cancel with full deposit refund. A separate new booking is the customer's choice, with current availability; never extend or automatically move the existing booking.

No excess-deposit refund/credit flow is introduced; that question was withdrawn. Detailed receipt/refund operations continue in engineering.

## 7. Staff access, number correction, and customer recovery

**Actor/trigger:** staff login, mistyped booking number, or customer login-number/recovery request.

- Staff mobile/SMS sign-in → verify number → check management-assigned access → open permitted salon operations. A valid mobile login alone does not create staff authorization.
- Before confirmation: correct customer number in intake; require the applicable customer verification before account access/payment.
- After confirmation or for account access transfer: use a separate correction/ownership-verification flow; editing a number alone cannot expose an appointment to another account.
- Customer login-number change/recovery in MVP: coordinate with salon; ownership checks must precede any change.
- Per-booking contact verification remains within the original customer account; it is not login to or ownership transfer toward that number's account.

Exact ownership evidence, authorized correction controls, account matching, and recovery steps require Stage 07 review; no insecure recovery shortcut is defined here.

## 8. Management maintains service and schedule information

**Actor/trigger:** manager edits service, prices/factors, volume labels/durations, eligibility, priority, schedule, or shared policy settings.

1. Inspect current values and affected bookings.
2. Edit manager-controlled information; identify genuine consultation prerequisites and expose salon contact instead of direct booking.
3. Validate entries and show any schedule conflicts.
4. If a schedule change would invalidate confirmed appointments, resolve affected appointments through flow 5 before saving the conflicting change.
5. Review/save; verify resulting public availability. Existing accepted terms and active hold deadlines remain intact.

Reception cannot change these settings. Numeric validation, rounding, actual service configuration values, and detailed conflict-screen behavior continue in Stage 07.

## Proposed states for review

Use separate dimensions rather than treating every payment event as a booking state:

- Appointment: awaiting deposit, confirmed, cancelled, completed; details for expired/unconfirmed attempts and immediate visits to be refined.
- Payment: not started, in progress/unknown, verified success, definitive failure.
- Refund: not applicable, pending, completed, failed/needs attention.

These labels and transition details are draft screen semantics, not Stage 07 approval. A pending replacement does not silently change the confirmed original booking.

## Review work carried forward

- Online-booking order, sequential selection steps, back-navigation preservation/revalidation, payment-button hold trigger, and payment-result presentation/account retrieval are approved. Refine the remaining screen grouping, exact state transitions, and operation failure recovery.
- Define verified ownership for matching, confirmed-number corrections/access transfer, and salon-coordinated account recovery.
- Define SMS sending/retry and delivery failure without deadline resets.
- Define validation/currency rounding, refund routing/timing, and detailed exception permission handling.
- Check selected payment provider compatibility and verification/recovery operations during engineering.
- Supply real service prices/factors, volume labels/durations, and specialist schedules through manager configuration.

Return changes to customer rights, accepted terms, consent, or other approved business rules for explicit user approval. Stage 07 remains a draft until reviewed and approved.
