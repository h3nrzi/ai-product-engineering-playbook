# Jobs & User Journeys — Women’s Beauty Salon Booking

## Status and boundaries

Stage 06 draft for discussion, prepared on 2026-10-03 from the approved product scope, actor definitions, and the Stage 05 research. Proposed journey details are design recommendations; they are not validated user behavior.

Confirmed: one women’s salon, one service per appointment, eligible specialist and full-duration availability, mobile-number/SMS-code customer authentication, account-linked online appointments confirmed after a verified deposit payment, customer appointment management, a shared calendar for all booking sources, reception/management access levels, and no independent specialist dashboard.

## Jobs by actor

- **Customer — critical:** understand a service, choose a suitable eligible specialist or any eligible specialist, and secure a valid appointment with clear details.
- **Customer — important:** retrieve an upcoming appointment and change or cancel it when policy allows.
- **Reception — critical:** see the salon’s appointments and create phone/walk-in bookings without conflicting with online bookings.
- **Reception — important:** manage customer-requested and salon-originated appointment changes with a clear result.
- **Manager — critical:** maintain service information, prices, specialist eligibility, working schedules, specialist assignment priority, and the shared deposit/payment/cancellation settings so customers see accurate booking options.
- **Manager — important:** perform reception operations when necessary and handle availability changes affecting appointments.
- **Specialist — supporting, without a product login:** receive the correct appointment context through salon coordination and communicate availability changes to reception/management. The communication channel remains undecided.

## Primary journey — customer books one service

Entry points: salon website/service list, a salon booking link, or a specialist profile. A social-link entry is a proposal informed by research, not an integration requirement.

| Stage | Goal and action | Information and decision | Likely friction | Expected outcome |
| --- | --- | --- | --- | --- |
| Discover | Understand and choose one service | Description, price model, expected duration, conditions; is it suitable and directly bookable? | Similar names, uncertain final price, consultation prerequisite | One understood service; prerequisites visible |
| Select volume when relevant | Choose the service-relevant volume option | Clear option descriptions and manager-defined duration for each | Customer is unsure which option fits | One volume option and booking duration retained; fixed-duration services skip this step |
| Choose specialist | Select a named eligible specialist or any eligible specialist | Expertise, supported service, explanation of no preference | Preferred specialist does not provide the service | Named preference honored or no-preference availability selected |
| Choose time | Find a time that fits | Named specialist’s times or combined valid times across eligible specialists; full selected duration | No suitable time or a slot becomes unavailable | One valid time; for no preference, actual specialist assigned by manager priority |
| Sign in / review customer details | Sign in if needed; review profile-prefilled name/contact and edit for this booking if desired | SMS login for signed-out customers; profile defaults; extra SMS contact verification only for a different booking number | Missing profile details, code/session failure, or slot loss during login | Original account owns booking; chosen booking contact retained; availability rechecked |
| Review | Check appointment and payment terms | Service, actual specialist, selected volume option where relevant, date/time, duration, fixed price or clearly labelled approximate usual-volume price, deposit percentage, calculated deposit, exact or estimated balance, and cancellation terms | Unclear price or deposit consequences | Customer knowingly proceeds to payment |
| Pay deposit | Secure the appointment within a temporary hold | Deposit amount, hold expiry, payment result | Abandoned/failed payment, expired hold, or uncertain result | Verified deposit allows confirmation; unresolved payment remains pending |
| Confirm | Understand whether booking succeeded | Confirmed appointment details, recorded deposit, balance, and a route to My appointments | Payment result is uncertain or arrives after hold expiry | Confirmed appointment only after verified payment and valid slot ownership; otherwise clear recovery |

Customer authentication is approved: mobile-number login with an SMS code, account-linked online reservations, and account-based appointment retrieval. Signed-in customers receive profile-prefilled name and contact details without repeated entry. They may edit these for the booking, including its contact number; this does not change the profile/login number or account ownership. If the chosen contact differs from the account’s verified mobile number, an SMS code verifies it before payment/confirmation; the original account still owns the appointment. Payment model is approved: online deposit for confirmation, with the remaining balance paid at the salon. The deposit is a percentage of the service price. One shared percentage applies to all services and is configurable only by management; per-service rates are deferred. For variable-price services, the approved deposit basis is the approximate price for usual volume, with the estimate and final in-salon settlement clearly disclosed before payment. Management configures the shared percentage, payment-hold duration, and advance cancellation window; they are disclosed before payment and saved with each booking. Later setting changes affect new bookings only. Numeric defaults, rounding, and detailed exception handling remain to be defined. Consultation-dependent services must not be represented as directly bookable without a defined pathway.

### Profile defaults and booking contact edits

After login, prefill booking name/contact from the customer profile. The customer can keep them, provide missing details, or edit them for this appointment. Include the chosen name/contact in final review, appointment details, and salon operations. Preserve these edits when returning to service/time selection or recovering from an interrupted step where practical.

The appointment remains owned by the original authenticated account. A changed contact number is not a profile or login-number update and does not move the appointment to another account. The approved SMS check for a different booking contact is a contact-verification step within the original account session, not login to a different account. Verify the chosen number before proceeding to deposit payment/confirmation; an unchanged or restored account number needs no extra check. Editing the contact again to another number requires verification for that choice. Preserve booking selections on code errors/retry and recheck availability afterwards; verification does not reserve a slot or extend a hold.

### Any eligible specialist path

Select one service and volume option when relevant → choose “any eligible specialist” → view combined valid times across eligible staff → choose a time → assign an available eligible specialist using management’s priority order → see the assigned name in review before payment → hold that specialist/time for the full duration → pay deposit → confirm with the reviewed specialist.

A named specialist remains an explicit choice; priority order does not replace that choice. If a proposed no-preference assignment changes before payment, show the updated name for review. Once a hold is secured, priority edits do not silently substitute another specialist. After confirmation, any specialist replacement requires customer acceptance, even if the initial preference was “any eligible specialist”.

### Variable-price service journey

Choose service → understand the approximate usual-volume price and why it can change → select volume where duration varies → select eligible specialist/time → sign in if needed → review the estimate, deposit percentage, exact deposit payable now, estimated balance, and final-price disclosure → pay deposit → receive confirmed appointment with the same disclosed price basis → attend salon → settle final service price less deposit already paid.

The final balance is calculated from the actual final price, not automatically fixed to the pre-booking estimate. A variable price does not itself turn the service into a consultation-only booking. For variable-duration services, the approved volume choice determines the manager-configured booking duration before availability is shown. It does not alter the approximate usual-volume deposit basis.

### Payment hold and pending payment result

Approved by the user on 2026-10-03: temporarily lock the reviewed specialist/time for the full service duration while payment is in progress, and tie confirmation to the verified payment result. The slot is unavailable to conflicting customer or reception bookings while this hold remains active.

- Verified successful payment while the booking still owns the slot confirms the appointment with the reviewed specialist/time.
- A definitively failed payment releases the hold without confirming. If payment has not started by the payment-hold deadline, release the slot. Recheck availability and secure a valid hold before a new payment attempt.
- If payment started within the active hold but its result remains unknown, retain the slot in “awaiting payment result” while the system checks the outcome, including when the ordinary payment-hold deadline passes. An unknown result is not a failed payment and is not confirmation.
- Waiting for a result is bounded by a defined verification deadline; it cannot lock availability indefinitely. If the result is still unresolved at that deadline, release the slot and keep the payment outcome pending verification.
- If success is verified after the slot has been released, do not automatically confirm the original booking, even if the slot is still available. Refund the entire deposit and let the customer make a new booking from current availability. Show payment and refund progress separately, and direct the customer to check the existing payment status before retrying.

This applies to customer online payments and the online-payment route for reception-created future bookings. Exact verification-deadline values, how that deadline is set and disclosed, provider checks, retry mechanics, and refund execution remain for later flow/engineering definition. Opening a link or retrying a status check does not restart either deadline.

### Alternatives and recovery

- Specialist-first entry: select a service that specialist provides, then continue to availability.
- No time available: offer another date or eligible specialist; never silently replace a named preference.
- Service, volume, or specialist changes: re-evaluate dependent availability using the selected duration; do not retain an invalid time.
- Interrupted input or login: preserve service, volume option where relevant, specialist preference, and date/time through login; recheck availability afterwards. A selected time is not held by authentication. Do not promise cross-device persistence.
- Missing, invalid, or expired SMS code: explain the problem and offer correction/retry without discarding booking choices. Resend timing and attempt limits belong to later flow/security rules.
- Existing valid session: skip repeated mobile-number entry and code verification. If the session expires, sign in again and recheck availability.
- Unknown booking/payment result: show pending verification and direct the customer to check status before retrying. An initiated payment with an unknown result retains its slot until the defined verification deadline; do not encourage duplicate deposits or bookings.
- Definitively failed payment: do not confirm; release the hold and recheck availability before a new attempt. If payment was not started before hold expiry, release the slot; if its result is unknown, use the bounded pending-result path above.
- Success verified after slot release: do not confirm automatically; refund the full deposit and offer a new booking from current availability.

## Customer retrieves or changes an appointment

Entry: “My appointments” or a booking-result link. Require a valid mobile-number/SMS-code session and show only appointments belonging to that account. Signed-out customers sign in first; a link or booking reference does not bypass ownership checks.

1. Find the appointment: show service, specialist, date/time, and state; distinguish upcoming and cancelled appointments.
2. Review permitted actions: explain the applicable cancellation/rescheduling policy and whether self-service is available.
3. Reschedule before the current appointment’s stored advance cutoff: choose a valid new time, review the changed details and new deadline, and confirm. Transfer the paid deposit without a second charge. Keep the original appointment reserved until replacement succeeds; if it fails, preserve the original time and deposit. Retain accepted price/policy terms and calculate the new cancellation deadline from the new time using the original window. Changes to service or volume are not silently included. After the current cutoff, online rescheduling is unavailable; reception coordination does not bypass late-cancellation/no-show policy.
4. Cancel: show the exact appointment and refund consequences before a deliberate cancellation action. Under the approved policy direction, cancellation within the advance window returns the deposit; late cancellation/no-show does not. Display cancellation and refund status separately: cancellation is not proof that a refund has completed. Release availability only after successful cancellation.
5. If an action is unavailable: explain why and offer salon contact information; do not imply that contacting reception bypasses policy.

Main friction: finding the right appointment, unknown rules, lost availability, and uncertainty after a failed change. Success means the customer understands the current confirmed state. The manager-configured customer cancellation window, rescheduling/deposit-transfer rules, and full deposit refund for salon-originated cancellation are approved. Refund processing details, staff exception authority, and communication channels remain open.

## Reception creates a phone or walk-in appointment

Entry: the shared salon calendar or appointment-creation action. Reception uses its own staff access, never the customer’s session.

Common preparation: capture the customer mobile number and necessary details → select one service and its volume option when relevant → choose a named eligible specialist or “any eligible specialist” → check a valid time that fits the full duration → assign the actual specialist for the any-eligible option → review customer, service, duration, actual specialist, time, and price/policy context.

Approved by the user on 2026-10-03: reception-created telephone, future in-person, and immediate walk-in bookings support both named-specialist and any-eligible-specialist booking. The any-eligible path uses the same combined valid availability and manager-controlled assignment priority as customer bookings: select a time, then assign an eligible specialist available for the full selected duration using management’s priority order. A named choice remains explicit and is not replaced by that priority order.

Show the final assigned specialist to reception before confirmation and communicate the name to the customer during telephone/in-person review; telephone customers also see it in the booking-review/payment link before payment. Confirm with that reviewed specialist. The same assignment-review and hold protections as the customer path apply: show any changed assignment before payment/confirmation, and do not silently substitute a specialist during an active hold. After confirmation, changing the specialist requires customer acceptance even when the initial choice was “any eligible specialist”.

### Telephone booking

1. Create a booking awaiting deposit within the configured temporary payment hold. The time is unavailable to conflicting online or reception bookings while the hold is active.
2. Provide the customer a booking-review/payment link with the hold expiry. Delivery channel remains to be defined.
3. Customer signs in with an SMS code for the recorded mobile number, reviews service/volume, specialist/time, price basis, exact deposit, estimated/fixed balance, and cancellation rules, then pays.
4. Confirm only after verified deposit payment within valid slot ownership. Show the result in the shared calendar and the customer’s account.
5. If payment has not started by hold expiry, release the time; a definitively failed payment also releases the hold. If payment started in time but its result is unknown, retain the slot until the defined verification deadline while checking the result. Release it if unresolved at that deadline; success verified after release receives a full deposit refund without automatic confirmation. Use the same pending-result and recovery rules as customer online booking; opening a link does not restart either deadline.

### In-person booking for a future visit

Use the same link/payment route, or explain the price and cancellation terms to the customer, receive the calculated deposit at the salon, and record actual receipt before confirming. Reception records payment source and amount; the salon-wide percentage remains unchanged. Retain the accepted terms and deposit for the future appointment. Customer account access still requires SMS verification of the recorded number.

### Immediate walk-in

Check valid immediate availability and record the appointment for the present visit; payment occurs at the salon during the visit. This path has no advance online deposit. It is not an option for confirming unpaid future reservations or overbooking a specialist. If no time fits, offer a valid alternative; a later visit follows the future-booking deposit path.

### Identity, conflicts, and recovery

Recording a mobile number, sending a link, or recording an in-salon payment does not verify ownership. Customer appointment retrieval requires SMS-code authentication for the corresponding number. Exact account matching and correcting a mistyped number remain flow decisions; no cross-number access is assumed.

Reception may be interrupted while entering a booking and online availability may change meanwhile. Preserve input when a conflict occurs, explain it, and offer a valid alternative. Reception cannot modify service/price/specialist/schedule settings to force a booking, waive the required future-booking deposit, or assert that an uncertain online payment succeeded.

## Reception manages daily appointments

Entry: today’s calendar, a date/specialist filter, or an appointment detail view.

Review the customer, service, specialist, time, and current state; choose an allowed action; review its consequences; confirm and return to the updated calendar. Online, phone, and walk-in appointments use the same availability constraints. Exact appointment states and status-transition rules will be defined in later flows.

Rescheduling should work from appointment details; dragging is optional. Apply the stored policy window and eligibility constraints; failed changes leave the existing appointment and deposit intact. Reception contact after the cutoff does not automatically waive the late-cancellation rules.

### Salon cancels or proposes a replacement

Reception/management identifies an affected appointment → checks the original booking and paid deposit → offers a valid alternative time or eligible specialist when available → presents the proposed details to the customer → records explicit acceptance before applying the change, or cancels with full deposit refund if the customer declines or the salon cancels without a replacement.

The salon’s cancellation is distinct from a late customer cancellation: refund the entire deposit paid regardless of the customer-cancellation cutoff. In-salon receipt of a deposit has the same refund entitlement as online payment. A still-valid original time remains reserved while merely proposing a replacement; if the salon has cancelled it, show that fact and refund eligibility rather than implying it still stands. No customer response is not approval; the unanswered-proposal handling remains to be defined.

Show appointment state and refund progress separately. Refund routing, timing, and customer communication channel remain flow details; this does not add a reminder system to scope.

## Manager maintains bookable information

Entry: service, specialist, or schedule settings, or the shared deposit/payment/cancellation settings in the salon operations area.

Understand the information to update → inspect existing values and affected context → edit service descriptions/prices and volume-specific durations, specialist eligibility/assignment priority, working schedules, or the shared deposit percentage, payment-hold duration, or advance cancellation window → validate → review → save → check the resulting customer booking options.

The manager needs to understand whether existing appointments are affected before saving a disruptive change. A new schedule or eligibility change must not silently cancel, move, or invalidate accepted appointments. The exact conflict-resolution policy is open and must be specified before implementation.

The customer sees the applicable deposit and timing/cancellation rules before payment. Save these terms with the booking/payment attempt. Management changes apply to future bookings; existing appointment terms and active hold expiries stay unchanged. An accepted reschedule uses the original policy window and accepted terms; only the deadline is recalculated against the new appointment time. A settings edit itself never changes an existing deadline.

Reception can identify an appointment or availability issue; management owns settings changes. Specialists communicate absence or changes through salon coordination. Reception/management then resolve affected appointments, and customers receive the resulting appointment information. This crosses actors without requiring specialist access.

## Outstanding decisions before final flows

- Staff login mechanics and detailed matching/correction of staff-entered customer numbers. Customer account access requires SMS verification; staff must not impersonate a customer session.
- Profile/account login-number change and recovery remain separate from the approved SMS verification of a different booking contact. Editing or verifying booking contact does not grant cross-account appointment access.
- Service-specific approximate usual-volume prices, their descriptions and adjustment factors; any genuine consultation prerequisite. Variable pricing alone does not require consultation.
- Numeric setup values and validation for manager-controlled deposit percentage, payment-hold duration, and advance cancellation window; currency rounding. These are settings, not fixed product constants. Per-service rates are deferred.
- How the final price is agreed at the salon and how an excess deposit is handled if the final price is lower than the deposit paid.
- Service-specific volume labels and booking durations; how reception/management handle an inaccurate customer volume selection at the salon without silently overlapping another appointment.
- Booking-link delivery channel and precise payment-hold start/retry interaction for reception-created future bookings. Confirmation/deposit paths and customer SMS verification are approved.
- Numeric verification deadline and its setup/disclosure, provider-result checks, payment retry mechanics, and refund processing details. The bounded pending-result hold and full refund for success verified after slot release are approved.
- Staff exception authority after the self-service rescheduling cutoff and handling unanswered salon replacement proposals. The approved default does not allow reception contact to bypass late-cancellation policy.
- Additional required fields, if justified, and staff-created appointment intake. Online booking name/contact default from the profile and are editable per booking; any missing data should be requested without repeating completed profile information.
- Appointment states, customer communication channel, and effects of schedule/eligibility edits on existing appointments.

Deposit collection is now approved for the production MVP; real provider selection remains for engineering. No daily booking limit, multi-service appointment, reminders, or specialist dashboard is added by this draft.

## Completion condition

Agree the major jobs/journeys and resolve the decisions that materially change the booking path before treating Stage 06 as complete. Stage 07 then expands these journeys into screen-level flows, branches, states, and recovery.
