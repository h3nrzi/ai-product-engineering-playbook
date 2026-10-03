# Jobs & User Journeys — Women’s Beauty Salon Booking

## Status and boundaries

Stage 06 draft for discussion, prepared on 2026-10-03 from the approved product scope, actor definitions, and the Stage 05 research. Proposed journey details are design recommendations; they are not validated user behavior.

Confirmed: one women’s salon, one service per appointment, eligible specialist and full-duration availability, mobile-number/SMS-code customer authentication, account-linked online appointments confirmed after a verified deposit payment, customer appointment management, a shared calendar for all booking sources, reception/management access levels, and no independent specialist dashboard.

## Jobs by actor

- **Customer — critical:** understand a service, choose a suitable eligible specialist or any eligible specialist, and secure a valid appointment with clear details.
- **Customer — important:** retrieve an upcoming appointment and change or cancel it when policy allows.
- **Reception — critical:** see the salon’s appointments and create phone/walk-in bookings without conflicting with online bookings.
- **Reception — important:** manage customer-requested and salon-originated appointment changes with a clear result.
- **Manager — critical:** maintain service information, prices, specialist eligibility, and working schedules so customers see accurate booking options.
- **Manager — important:** perform reception operations when necessary and handle availability changes affecting appointments.
- **Specialist — supporting, without a product login:** receive the correct appointment context through salon coordination and communicate availability changes to reception/management. The communication channel remains undecided.

## Primary journey — customer books one service

Entry points: salon website/service list, a salon booking link, or a specialist profile. A social-link entry is a proposal informed by research, not an integration requirement.

| Stage | Goal and action | Information and decision | Likely friction | Expected outcome |
| --- | --- | --- | --- | --- |
| Discover | Understand and choose one service | Description, price model, expected duration, conditions; is it suitable and directly bookable? | Similar names, uncertain final price, consultation prerequisite | One understood service; prerequisites visible |
| Choose specialist | Select an eligible specialist or no preference | Expertise, supported service, preference meaning | Preferred specialist does not provide the service | Valid preference retained |
| Choose time | Find a time that fits | Date, available start times, full duration, specialist context | No suitable time or a slot becomes unavailable | One valid selected time |
| Sign in / provide details | Sign in if needed; reuse verified account details | Mobile number and SMS code for signed-out customers; any further required details remain to be decided | Missing/expired code, session expiry, or slot loss during login | Authenticated account; selections preserved and availability rechecked |
| Review | Check appointment and payment terms | Service, actual specialist, date/time, duration, expected price, deposit percentage, price basis, calculated deposit, balance, and cancellation terms | Unclear price or deposit consequences | Customer knowingly proceeds to payment |
| Pay deposit | Secure the appointment within a temporary hold | Deposit amount, hold expiry, payment result | Abandoned/failed payment, expired hold, or uncertain result | Verified deposit allows confirmation; unresolved payment remains pending |
| Confirm | Understand whether booking succeeded | Confirmed appointment details, recorded deposit, balance, and a route to My appointments | Payment result is uncertain or arrives after hold expiry | Confirmed appointment only after verified payment and valid slot ownership; otherwise clear recovery |

Customer authentication is approved: mobile-number login with an SMS code, account-linked online reservations, and account-based appointment retrieval. Signed-in customers reuse their verified number without repeated entry. Payment model is approved: online deposit for confirmation, with the remaining balance paid at the salon. The deposit is a percentage of the service price. The percentage value, salon-wide versus service-specific configuration, price basis for variable-price services, rounding, hold duration, and detailed exception handling remain open before final flows. Consultation-dependent services must not be represented as directly bookable without a defined pathway.

### Alternatives and recovery

- Specialist-first entry: select a service that specialist provides, then continue to availability.
- No time available: offer another date or eligible specialist; never silently replace a named preference.
- Service or specialist changes: re-evaluate dependent availability; do not retain an invalid time.
- Interrupted input or login: preserve service, specialist preference, and date/time through login; recheck availability afterwards. A selected time is not held by authentication. Do not promise cross-device persistence.
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
2. Select one service and an eligible specialist or supported assignment option.
3. Check a valid time that fits the full duration and existing schedule. A walk-in is not permission to overbook; if no valid time exists, explain alternatives.
4. Review customer, service, specialist, and time, then create the appointment.
5. Record the appointment in the shared calendar under the phone/walk-in deposit policy still to be decided. A staff-created booking is not an approved way to bypass deposit requirements. Show its appointment/payment state accurately; both active holds and confirmed appointments constrain online availability.

Decision factors: actual availability, service eligibility, time constraints, and customer preference. Friction: interruptions at reception and online bookings changing availability while staff enter details. Keep input when a conflict occurs and offer a valid alternative. Reception cannot modify service/price/specialist/schedule settings to force a booking.

## Reception manages daily appointments

Entry: today’s calendar, a date/specialist filter, or an appointment detail view.

Review the customer, service, specialist, time, and current state; choose an allowed action; review its consequences; confirm and return to the updated calendar. Online, phone, and walk-in appointments use the same availability constraints. Exact appointment states and status-transition rules will be defined in later flows.

Rescheduling should work from appointment details; dragging is optional. Failed changes leave the existing appointment intact. Salon-originated changes must be communicated to the customer through a channel still to be selected; this does not add a reminder system to scope.

## Manager maintains bookable information

Entry: service, specialist, or schedule settings in the salon operations area.

Understand the information to update → inspect existing values and affected context → edit service descriptions/prices, specialist eligibility, or working schedules → validate → review → save → check the resulting customer booking options.

The manager needs to understand whether existing appointments are affected before saving a disruptive change. A new schedule or eligibility change must not silently cancel, move, or invalidate accepted appointments. The exact conflict-resolution policy is open and must be specified before implementation.

Reception can identify an appointment or availability issue; management owns settings changes. Specialists communicate absence or changes through salon coordination. Reception/management then resolve affected appointments, and customers receive the resulting appointment information. This crosses actors without requiring specialist access.

## Outstanding decisions before final flows

- Staff authentication and how phone/walk-in appointments are linked to customer accounts; staff must not impersonate a customer session.
- Customer mobile-number change/recovery policy; no cross-number appointment access is assumed.
- Fixed, starting, or estimate-based service prices; any consultation prerequisite.
- Deposit percentage value, salon-wide versus service-specific configuration, configuration permissions, and currency rounding.
- Explicit price basis for variable-price services and treatment of price adjustments after payment.
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
