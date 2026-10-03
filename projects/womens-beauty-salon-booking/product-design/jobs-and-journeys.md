# Jobs & User Journeys — Women’s Beauty Salon Booking

## Status and boundaries

Stage 06 draft for discussion, prepared on 2026-10-03 from the approved product scope, actor definitions, and the Stage 05 research. Proposed journey details are design recommendations; they are not validated user behavior.

Confirmed: one women’s salon, one service per appointment, eligible specialist and full-duration availability, mobile-number/SMS-code customer authentication, account-linked online appointments confirmed after a verified deposit payment, customer appointment management, a shared calendar for all booking sources, reception/management access levels, and no independent specialist dashboard.

## Jobs by actor

- **Customer — critical:** understand a service, choose a suitable eligible specialist or any eligible specialist, and secure a valid appointment with clear details.
- **Customer — important:** retrieve an upcoming appointment and change or cancel it when policy allows.
- **Reception — critical:** see the salon’s appointments and create phone/walk-in bookings without conflicting with online bookings.
- **Reception — important:** manage customer-requested and salon-originated appointment changes with a clear result.
- **Manager — critical:** maintain service information, prices, specialist eligibility, working schedules, and the shared deposit percentage so customers see accurate booking options.
- **Manager — important:** perform reception operations when necessary and handle availability changes affecting appointments.
- **Specialist — supporting, without a product login:** receive the correct appointment context through salon coordination and communicate availability changes to reception/management. The communication channel remains undecided.

## Primary journey — customer books one service

Entry points: salon website/service list, a salon booking link, or a specialist profile. A social-link entry is a proposal informed by research, not an integration requirement.

| Stage | Goal and action | Information and decision | Likely friction | Expected outcome |
| --- | --- | --- | --- | --- |
| Discover | Understand and choose one service | Description, price model, expected duration, conditions; is it suitable and directly bookable? | Similar names, uncertain final price, consultation prerequisite | One understood service; prerequisites visible |
| Select volume when relevant | Choose the service-relevant volume option | Clear option descriptions and manager-defined duration for each | Customer is unsure which option fits | One volume option and booking duration retained; fixed-duration services skip this step |
| Choose specialist | Select an eligible specialist or no preference | Expertise, supported service, preference meaning | Preferred specialist does not provide the service | Valid preference retained |
| Choose time | Find a time that fits | Date, available start times, full duration, specialist context | No suitable time or a slot becomes unavailable | One valid selected time |
| Sign in / provide details | Sign in if needed; reuse verified account details | Mobile number and SMS code for signed-out customers; any further required details remain to be decided | Missing/expired code, session expiry, or slot loss during login | Authenticated account; selections preserved and availability rechecked |
| Review | Check appointment and payment terms | Service, actual specialist, selected volume option where relevant, date/time, duration, fixed price or clearly labelled approximate usual-volume price, deposit percentage, calculated deposit, exact or estimated balance, and cancellation terms | Unclear price or deposit consequences | Customer knowingly proceeds to payment |
| Pay deposit | Secure the appointment within a temporary hold | Deposit amount, hold expiry, payment result | Abandoned/failed payment, expired hold, or uncertain result | Verified deposit allows confirmation; unresolved payment remains pending |
| Confirm | Understand whether booking succeeded | Confirmed appointment details, recorded deposit, balance, and a route to My appointments | Payment result is uncertain or arrives after hold expiry | Confirmed appointment only after verified payment and valid slot ownership; otherwise clear recovery |

Customer authentication is approved: mobile-number login with an SMS code, account-linked online reservations, and account-based appointment retrieval. Signed-in customers reuse their verified number without repeated entry. Payment model is approved: online deposit for confirmation, with the remaining balance paid at the salon. The deposit is a percentage of the service price. One shared percentage applies to all services and is configurable only by management; per-service rates are deferred. For variable-price services, the approved deposit basis is the approximate price for usual volume, with the estimate and final in-salon settlement clearly disclosed before payment. The percentage value, rounding, hold duration, and detailed exception handling remain open before final flows. Consultation-dependent services must not be represented as directly bookable without a defined pathway.

### Variable-price service journey

Choose service → understand the approximate usual-volume price and why it can change → select volume where duration varies → select eligible specialist/time → sign in if needed → review the estimate, deposit percentage, exact deposit payable now, estimated balance, and final-price disclosure → pay deposit → receive confirmed appointment with the same disclosed price basis → attend salon → settle final service price less deposit already paid.

The final balance is calculated from the actual final price, not automatically fixed to the pre-booking estimate. A variable price does not itself turn the service into a consultation-only booking. For variable-duration services, the approved volume choice determines the manager-configured booking duration before availability is shown. It does not alter the approximate usual-volume deposit basis.

### Alternatives and recovery

- Specialist-first entry: select a service that specialist provides, then continue to availability.
- No time available: offer another date or eligible specialist; never silently replace a named preference.
- Service, volume, or specialist changes: re-evaluate dependent availability using the selected duration; do not retain an invalid time.
- Interrupted input or login: preserve service, volume option where relevant, specialist preference, and date/time through login; recheck availability afterwards. A selected time is not held by authentication. Do not promise cross-device persistence.
- Missing, invalid, or expired SMS code: explain the problem and offer correction/retry without discarding booking choices. Resend timing and attempt limits belong to later flow/security rules.
- Existing valid session: skip repeated mobile-number entry and code verification. If the session expires, sign in again and recheck availability.
- Unknown booking/payment result: show pending verification and direct the customer to check status before retrying. Do not encourage duplicate deposits or bookings.
- Failed or abandoned payment: do not show a confirmed appointment. Explain the remaining hold time and valid retry path; once expired, release the time and recheck availability before restarting.
- Late verified payment after hold expiry: do not silently confirm over another appointment; offer the recovery/refund route once that policy is defined.

## Customer retrieves or changes an appointment

Entry: “My appointments” or a booking-result link. Require a valid mobile-number/SMS-code session and show only appointments belonging to that account. Signed-out customers sign in first; a link or booking reference does not bypass ownership checks.

1. Find the appointment: show service, specialist, date/time, and state; distinguish upcoming and cancelled appointments.
2. Review permitted actions: explain the applicable cancellation/rescheduling policy and whether self-service is available.
3. Reschedule: choose a valid alternative, review the changed details, and confirm. Preserve the original appointment if the replacement fails. Changing the service is not silently included in rescheduling; that behavior remains a later decision.
4. Cancel: show the exact appointment and refund consequences before a deliberate cancellation action. Under the approved policy direction, cancellation within the advance window returns the deposit; late cancellation/no-show does not. Display cancellation and refund status separately: cancellation is not proof that a refund has completed. Release availability only after successful cancellation.
5. If an action is unavailable: explain why and offer salon contact information; do not imply that contacting reception bypasses policy.

Main friction: finding the right appointment, unknown rules, lost availability, and uncertainty after a failed change. Success means the customer understands the current confirmed state. Refund eligibility direction is approved; the cutoff, processing details, rescheduling treatment, salon-originated cancellation policy, and communication channels remain undecided.

## Reception creates a phone or walk-in appointment

Entry: the shared salon calendar or appointment-creation action.

1. Understand the request and capture the necessary customer/contact context; exact required fields remain open.
2. Select one service, its volume option when duration varies, and an eligible specialist or supported assignment option.
3. Check a valid time that fits the full duration and existing schedule. A walk-in is not permission to overbook; if no valid time exists, explain alternatives.
4. Review customer, service, specialist, and time, then create the appointment.
5. Record the appointment in the shared calendar under the phone/walk-in deposit policy still to be decided. A staff-created booking is not an approved way to bypass deposit requirements. Show its appointment/payment state accurately; both active holds and confirmed appointments constrain online availability.

Decision factors: actual availability, service eligibility, time constraints, and customer preference. Friction: interruptions at reception and online bookings changing availability while staff enter details. Keep input when a conflict occurs and offer a valid alternative. Reception cannot modify service/price/specialist/schedule settings to force a booking.

## Reception manages daily appointments

Entry: today’s calendar, a date/specialist filter, or an appointment detail view.

Review the customer, service, specialist, time, and current state; choose an allowed action; review its consequences; confirm and return to the updated calendar. Online, phone, and walk-in appointments use the same availability constraints. Exact appointment states and status-transition rules will be defined in later flows.

Rescheduling should work from appointment details; dragging is optional. Failed changes leave the existing appointment intact. Salon-originated changes must be communicated to the customer through a channel still to be selected; this does not add a reminder system to scope.

## Manager maintains bookable information

Entry: service, specialist, or schedule settings, or the shared deposit-percentage setting in the salon operations area.

Understand the information to update → inspect existing values and affected context → edit service descriptions/prices and volume-specific durations, specialist eligibility, working schedules, or the shared deposit percentage → validate → review → save → check the resulting customer booking options.

The manager needs to understand whether existing appointments are affected before saving a disruptive change. A new schedule or eligibility change must not silently cancel, move, or invalidate accepted appointments. The exact conflict-resolution policy is open and must be specified before implementation.

Reception can identify an appointment or availability issue; management owns settings changes. Specialists communicate absence or changes through salon coordination. Reception/management then resolve affected appointments, and customers receive the resulting appointment information. This crosses actors without requiring specialist access.

## Outstanding decisions before final flows

- Staff authentication and how phone/walk-in appointments are linked to customer accounts; staff must not impersonate a customer session.
- Customer mobile-number change/recovery policy; no cross-number appointment access is assumed.
- Service-specific approximate usual-volume prices, their descriptions and adjustment factors; any genuine consultation prerequisite. Variable pricing alone does not require consultation.
- Value of the manager-controlled salon-wide deposit percentage and currency rounding. Per-service rates are deferred.
- How the final price is agreed at the salon and how an excess deposit is handled if the final price is lower than the deposit paid.
- Service-specific volume labels and booking durations; how reception/management handle an inaccurate customer volume selection at the salon without silently overlapping another appointment.
- Temporary hold duration.
- Deposit collection and account linkage for phone/walk-in bookings.
- Late/uncertain payment recovery and refund processing details.
- Advance cancellation cutoff, rescheduling treatment, and salon-originated cancellation/change handling. Customer no-show/late-cancellation deposit retention is approved as the disclosed policy direction.
- Any-specialist assignment strategy and whether staff booking uses the same choice.
- Required customer fields for online and staff-created appointments.
- Appointment states, customer communication channel, and effects of schedule/eligibility edits on existing appointments.

Deposit collection is now approved for the production MVP; real provider selection remains for engineering. No daily booking limit, multi-service appointment, reminders, or specialist dashboard is added by this draft.

## Completion condition

Agree the major jobs/journeys and resolve the decisions that materially change the booking path before treating Stage 06 as complete. Stage 07 then expands these journeys into screen-level flows, branches, states, and recovery.
