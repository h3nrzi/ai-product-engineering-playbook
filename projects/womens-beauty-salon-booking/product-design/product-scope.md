# Product Strategy & Scope — Women’s Beauty Salon Booking

## Product goal

Transform the path from choosing a beauty service to securing and managing a valid appointment from a manually coordinated process into a reliable self-service experience.

For the salon, reduce repetitive booking coordination while keeping operational control over specialist eligibility, schedules, duration, and booking rules.

## Actors at a high level

- Customer
- Beauty specialist
- Salon reception / management

Detailed actor definition belongs to Stage 04.

## North-star journey

`Need beauty service → understand service options → evaluate relevant specialists → select service and relevant volume option → choose specialist or any eligible specialist → see valid availability → select date/time → sign in if needed → provide required details → review price and policies → temporary time hold → pay deposit → receive confirmed appointment`

If this journey is weak, the product has not solved its primary problem.

## Supporting journeys

- browse and compare services
- discover and evaluate specialists
- view upcoming appointments
- reschedule an appointment when allowed
- cancel an appointment when allowed
- view appointment history where useful
- salon staff review and manage appointments
- salon staff maintain specialist availability/schedules relevant to booking
- salon staff handle appointment changes or cancellations

## Product MVP

### Customer experience

The customer can:

- discover services
- understand relevant price/duration information
- discover appropriate specialists
- find valid availability
- pay the online deposit to confirm a valid appointment
- view upcoming appointment details
- manage an appointment when policy allows

### Salon operations

The salon can control the minimum information and operations required for booking:

- services
- specialists
- specialist schedules / availability inputs
- appointments

The MVP does not attempt to manage the salon’s entire business operation.

### MVP access boundary

Approved during Stage 04: customers use the booking and appointment-management experience; reception/management use one salon operations area and manage specialist schedules and appointments. Specialists retain profiles and service eligibility but have no independent login or dashboard in the MVP. Reception manages appointments, including phone and walk-in bookings in the shared calendar. Management has all reception capabilities plus control of services, prices, specialists, eligibility, working schedules, and the shared deposit percentage.

### Any eligible specialist

Approved by the user on 2026-10-03:

- If the customer selects “any eligible specialist”, show the combined set of valid times across specialists who offer the service and can accommodate the full selected duration, including any volume-specific duration. Working schedules, existing appointments, and active holds still apply.
- After the customer chooses a time, assign the first available eligible specialist in management’s configured priority order. Priority never overrides eligibility or availability.
- Show the assigned specialist’s name in the booking review before payment. If availability changes before a hold is secured and the assignment must change, present the new specialist for customer review before payment; do not hide the change.
- Secure the payment hold for the actual assigned specialist and full duration. Confirm the same reviewed specialist; do not use another specialist merely to recover a conflicting or expired hold without customer review.
- Once confirmed, “any eligible specialist” is not ongoing consent to substitute staff. Changes of specialist require customer acceptance under the salon replacement rules.
- Management controls the priority order; reception cannot edit it. Later priority edits do not reassign active held or confirmed appointments. Named-specialist selection remains honored and shows only that specialist’s valid times.

Approved on 2026-10-03: reception-created telephone, future in-person, and immediate walk-in bookings also support named-specialist and any-eligible-specialist choices, using the same manager-controlled assignment priority and valid availability. Show the final assigned specialist to reception and communicate it to the customer before confirmation; specialist changes after confirmation require customer acceptance.

### Customer authentication

Approved by the user on 2026-10-03:

- Services, specialists, and available times can be browsed without login.
- Customers sign in with their mobile number and a one-time SMS code. Successful verification establishes the customer account/session; no password is required.
- A signed-out customer signs in before reviewing/submitting a booking. Preserve the selected service, specialist preference, and date/time across login, then recheck availability. Login does not reserve the selected time.
- A signed-in customer skips repeated phone entry and verification while the session is valid.
- Each online booking belongs to the authenticated customer account. Prefill customer name and booking contact number from that account’s profile, using its verified mobile number by default. The customer may edit the booking information, including a different contact number, before confirming.
- “My appointments” shows appointments belonging to the signed-in account; an appointment link or reference alone does not grant access.
- SMS verification confirms control of the mobile number, not a government-verified personal identity.

Booking edits apply to the appointment’s contact details. They do not automatically change the profile, login mobile number, authenticated account, or appointment ownership. Show the chosen booking name/contact in the review and appointment details; the salon uses these booking details for appointment contact. “My appointments” remains tied to the original account even when the contact number differs. A booking contact number alone does not grant appointment access.

If the profile is incomplete, ask only for the missing booking information. Do not require retyping existing profile details. Approved by the user on 2026-10-03: if the customer changes the booking contact to a number different from the account’s verified mobile number, verify the new number with an SMS code before proceeding to deposit payment/confirmation. Keeping or restoring the account’s verified number requires no additional contact-verification step. Contact verification stays within the original account session and does not sign into the new number’s account or transfer appointment ownership.

Show which contact number is being verified. A successful code verifies that chosen number only; if the customer edits it again to another number, require verification for that new choice. Missing, invalid, or expired codes keep the contact unverified and offer correction/retry without discarding service, volume, specialist, or time selections. Recheck availability afterwards; contact verification alone does not create or extend a payment hold.

Staff use their own salon access when recording a customer mobile number; this does not verify that number or create an authenticated customer session. A customer must sign in with an SMS code for that number before accessing the corresponding appointment in My appointments or through a booking link. Staff mobile-number/SMS-code login and management-assigned access are approved. Before confirmation, reception can correct a mistyped number; confirmed-number corrections or account access transfer need a separate ownership-verification flow. Customer login-number changes and recovery are coordinated with the salon in the MVP. Detailed matching and ownership-review flows are defined in [user-flows.md](user-flows.md); manual identity-evidence procedures and security controls remain engineering work.

### Deposit and confirmation

Approved by the user on 2026-10-03:

- Standard online appointments become confirmed only after a successful online deposit payment is verified. The remaining service balance is paid at the salon; the deposit is credited toward the service price.
- After the customer reviews the appointment and payment/cancellation terms, keep the selected time unavailable to other bookings for a short, explicitly displayed payment window. Merely browsing or signing in does not hold a time.
- Deposit calculation is percentage-based, as approved by the user on 2026-10-03: deposit = displayed booking price basis × deposit percentage / 100. The price basis is the fixed price for fixed-price services or the approximate usual-volume price for variable-price services. The remaining service balance is the final service price less the deposit already paid.
- Show the applicable percentage, calculated deposit, price used for calculation, remaining balance where calculable, and hold expiry before payment.
- Approved configuration: one salon-wide deposit percentage applies to all services in the MVP. Only management can set or change it; reception cannot edit it or override it for an appointment.
- Per-service deposit percentages are deferred. Management configures the salon-wide percentage, payment-hold duration, and advance cancellation window. The approved initial payment-hold default is 10 minutes, with up to 5 additional minutes after hold expiry for a payment started in time whose result remains unknown. Approved by the user on 2026-10-03: the initial salon-wide deposit percentage is 20%, and the initial advance cancellation/rescheduling window is 24 hours before the appointment. The 20% applies to the fixed service price or the disclosed approximate usual-volume price. Customer cancellation within the permitted window returns the full deposit; rescheduling transfers it without collecting a second deposit. Both defaults remain configurable only by management and changes apply to new bookings; existing bookings retain accepted terms. Stage 07 defines validation and rounding: round the deposit once to the nearest whole toman, half upward, and preserve that exact displayed payable amount. Reception cannot edit or override these settings.
- Approved variable-price model: management defines an approximate price for the usual service volume (for example, typical hair length/volume). The shared salon-wide percentage is applied to that approximate price to calculate the online deposit. Variable pricing alone does not require consultation before booking.
- Label the price as approximate, describe what “usual volume” means for that service, and explain relevant price factors such as hair length, volume, or materials. Show this information in service discovery and again in the booking review before payment.
- Clearly distinguish the exact deposit charged now from the approximate service price and estimated remaining balance. Explain that the final service price is determined at the salon and the balance is final price minus the deposit already paid. Do not present the estimate as a guaranteed total.
- Display the estimated-price basis and the paid deposit in appointment details after booking. A later final-price adjustment does not recalculate or retroactively increase the deposit already charged.
- Approved by the user on 2026-10-03: for services with an approximate booking price, communicate the final price at the salon before starting the service and obtain the customer’s acceptance before proceeding. The amount payable at the salon is the final service price minus the deposit already paid. The excess-deposit question was withdrawn after clarification; no excess-deposit refund or credit rule is added. Management identifies genuine consultation prerequisites; such services direct customers to contact the salon rather than direct booking. Variable pricing alone is not a consultation prerequisite.
- Record the price basis, percentage, and charged deposit for the booking. Later catalog-price or percentage changes must not silently recalculate an existing appointment’s paid deposit.
- Display the configured payment-hold duration and actual expiry before payment, plus the cancellation window and refund consequences. Record the effective price basis, deposit percentage, calculated deposit, hold duration/expiry, and cancellation/refund terms when the customer accepts the review and starts the hold/payment attempt. The confirmed appointment retains those terms.
- Later changes to management settings apply only to new bookings. They must not rewrite existing appointment terms, move an active hold’s expiry, or change an existing appointment’s cancellation deadline. An accepted reschedule keeps the original policy window and recalculates the deadline relative to the new appointment time, as defined below.
- A definitively failed payment releases the hold without confirmation. If payment has not started by the hold deadline, release the time. A new payment attempt requires a fresh availability check and valid hold.
- Approved on 2026-10-03: a payment started within an active hold whose result remains unknown retains the reviewed specialist/time while the system checks the outcome, until a bounded verification deadline. With the initial defaults, that deadline is 15 minutes from hold creation: 10 minutes for payment plus up to 5 additional minutes for the pending result. Verified success while held confirms; definitive failure releases the slot early; an unresolved result at the verification deadline releases it without confirmation. Link opening or status checks do not restart the deadlines.
- Success verified after slot release receives a full deposit refund without automatic confirmation, even if that time remains available. The customer can make a new booking from current availability. Show payment/refund progress separately and check the existing payment status before retrying. Provider compatibility, detailed deadline setup/disclosure, retry mechanics, and refund execution remain for later flows/engineering; these timing defaults are product choices, not asserted provider limits.
- The approved cancellation direction is deposit refund for customer cancellation within the permitted advance window; late customer cancellation or no-show does not refund the deposit under the disclosed salon policy. Management configures the advance cancellation cutoff. Customer rescheduling and salon-originated cancellation follow the approved rules below; refund processing details remain open.
- Temporary payment holds and confirmed appointments both constrain the shared availability used by online booking and reception.

This adds deposit collection and payment-result handling to the production MVP. Base44 may simulate the full journey and its payment/hold states without taking real payments.

### Reception-created bookings

Approved by the user on 2026-10-03:

- **Telephone booking:** reception records one service, relevant volume option, eligible specialist, valid time, and customer mobile number. The customer receives a link to review the booking and its price/payment/cancellation terms, signs in with the mobile-number/SMS-code flow, and pays the deposit. Confirm only after verified payment while the time remains valid.
- **In-person booking for a future visit:** use the same review/payment-link flow, or reception may receive and record the calculated deposit at the salon. Receipt of the deposit permits confirmation; the remaining balance is paid at the service visit. Recording receipt is not permission to waive the deposit or change the percentage.
- **Immediate walk-in:** reception checks an eligible specialist and valid time for the full selected duration, records the appointment, and payment occurs during the visit. No advance online deposit is required for this immediate-visit path. A future appointment must not use this path to bypass deposit requirements.
- All paths use the shared calendar. Future bookings awaiting deposit use the configured temporary payment hold; expiry releases the time if payment has not started or been received and recorded. An online payment started in time with an unknown result follows the bounded pending-result hold above. Do not create an indefinite reservation while waiting for the customer to open a link. Booking-review/payment links are sent by SMS. The hold starts when reception finalizes the initial booking and requests link sending; opening/reopening the link does not extend it. The Stage 07 flow retries the same valid link without deadline resets and flags failed SMS for staff follow-up; notification failure does not change booking/payment outcomes.
- Reception shows or explains the deposit and cancellation terms before accepting an in-salon deposit. Preserve the booking’s price basis, applicable percentage, recorded payment, and accepted terms just as for online booking.
- Staff-entered mobile numbers remain unverified until the customer completes SMS-code authentication. Sending a link or recording an in-salon payment does not authenticate the customer. A link alone does not grant appointment access.
- Reception can record a deposit actually received at the salon and see the payment source/state. It cannot mark an unverified online payment as paid or alter deposit/payment/cancellation settings. This is appointment payment tracking, not a full accounting or POS system.

### Rescheduling and salon-originated cancellation

Approved by the user on 2026-10-03:

- Before the current appointment’s advance cancellation cutoff, a customer may choose a valid new time. Transfer the existing deposit to the rescheduled appointment; do not collect it again.
- Keep the original appointment and its time reserved until the replacement is confirmed. If the new time becomes unavailable or the change fails, leave the original appointment and deposit intact.
- Keep the original accepted price/deposit and policy terms. Use the original advance cancellation window to calculate the new deadline from the new appointment time, and show that deadline before the customer confirms. A manager’s later setting changes do not supply new terms to the reschedule.
- After the current cutoff, close customer online rescheduling and direct the customer to reception. Reception coordination is not an automatic exemption from the late-cancellation/no-show policy. Only management may authorize an exception for late change or refund, with a recorded reason. Reception cannot approve it independently; salon contact alone does not promise a free change.
- If the salon cancels, the customer is entitled to a full refund of the deposit actually paid, irrespective of the customer-cancellation cutoff. This applies to online and in-salon deposits; the operational refund route remains to be specified.
- The salon may propose another valid time or eligible specialist, but must obtain the customer’s acceptance before applying that alternative. Silence is not acceptance. If the customer declines, cancel with a full deposit refund. A proposed alternative must not silently release or replace a still-valid original appointment.
- Track cancellation and refund progress separately. A cancelled appointment does not imply money has already been returned. Approved on 2026-10-03: if a replacement proposal receives no response, retain the original confirmed appointment when the salon can still deliver it. If the salon cannot deliver it, cancel as a salon-originated cancellation with a full deposit refund rather than leaving the appointment unresolved while awaiting a response. Silence is not acceptance or customer-originated cancellation and does not forfeit the deposit. Changes and cancellation outcomes are communicated by SMS, with details and payment/refund state in the customer account. Stage 07 defines refund source, progress, and failure follow-up; actual provider execution/timing remain engineering work; this does not introduce scheduled reminders.

Changing the service or volume option during rescheduling is not included in this approval; its pricing/duration implications remain to be defined.

### Booking unit

Approved by the user on 2026-10-03: each MVP appointment contains one service with one eligible specialist. Multi-service appointments, service bundles, and coordinated appointments across specialists are deferred. This does not impose a daily booking limit; any such limit requires a separate decision.

### Stage 06 closure decisions

Approved on 2026-10-03: name and contact number are the minimum booking intake; request additional service-specific data only for a justified need. Management configures service prices and adjustment factors, volume options, and durations. Before saving a schedule change that conflicts with confirmed appointments, show the conflicts and require management to resolve affected appointments using the accepted replacement/customer-consent or cancellation/full-refund rules. Stage 07 is complete and defines the states, validation, rounding, identity-review outcomes, notification recovery, and payment/refund product flows in [user-flows.md](user-flows.md). Actual provider operations and concrete security/identity-evidence procedures remain engineering work, without changing approved customer rights.

### Booking rules

The product must prevent invalid combinations such as:

- a specialist who does not provide the selected service
- a time that does not fit the full service duration
- a time outside the specialist’s working schedule
- a conflicting already-booked time

Exact rules will be refined later in product discovery and engineering phases.

## Product MVP ≠ Base44 prototype scope

The production MVP eventually requires authoritative real behavior such as persistence, identity, availability validation, booking-rule enforcement, and concurrency-safe appointment operations.

The Base44 prototype may simulate those guarantees while preserving realistic product behavior and UX.

The prototype should prioritize:

- realistic screens and flows
- realistic states
- realistic demo content
- believable scheduling behavior
- clear customer and salon journeys

Production-grade persistence, authentication, concurrency protection, and other server-side guarantees are not required during the prototype phase.

## Explicitly out of scope

- multi-salon marketplace
- advanced multi-branch management
- beauty-at-home service
- beauty-product ecommerce
- payroll
- accounting
- professional inventory management
- full CRM
- marketing automation
- advanced loyalty
- staff HR management
- full chat platform
- AI beauty consultation/advisor

These can only enter scope later if a real requirement justifies them.

## Important product constraints

### Single salon

The initial product represents one physical women’s beauty salon.

### Multiple specialists

The salon has multiple beauty specialists.

### Specialist eligibility

Not every specialist provides every service.

### Variable service duration

Different services require different amounts of time.

Approved by the user on 2026-10-03: for services whose duration varies with volume, the customer selects a service-relevant volume option before time selection. Short/medium/long hair are examples, not a required set for every service. Management defines the options and a booking duration for each; reception cannot edit these settings.

Availability uses the selected option’s full duration. Show that option and duration in the booking review, appointment details, and salon calendar. If the option changes, recheck availability and require a new valid time when the original no longer fits. Preserve the selection through login.

Volume selection determines booking duration; for variable-price services the deposit still uses the disclosed approximate usual-volume price and the shared percentage. Changing volume does not automatically change the deposit basis or imply a guaranteed final price. Fixed-duration services do not require a volume-selection step.

Actual option labels and duration values remain service configuration, not invented defaults. Approved by the user on 2026-10-03: an inaccurate customer volume selection discovered at the salon does not change the booked start time or duration. Do not extend or move the appointment to accommodate the mismatch, even if later time is available. The specialist coordinates with the customer to resolve it within the reserved interval without delaying or overlapping the next appointment. For variable-price services, the final price still requires customer acceptance before service begins; a price change does not authorize more time. If the service cannot be delivered within the interval and the specialist and customer cannot agree a solution, cancel with a full deposit refund. A separate new booking requires the customer's choice; do not extend or automatically move the current appointment. This does not remove the approved customer rescheduling path.

### Schedule-driven availability

Bookable time depends on specialist schedule, service duration, existing appointments, and eligibility.

### Trust-sensitive specialist selection

Specialist expertise, style, and trust can affect customer choice; specialists should not be treated only as interchangeable resources.

### Responsive customer experience

The customer journey must work well on mobile, where salon discovery and booking are likely to occur frequently.

### Persian / RTL product direction

The portfolio product is intended to support a Persian-language RTL experience. Detailed content and responsive rules will be defined in later stages.

## Qualitative success criteria

### Customer

A first-time customer should be able to understand what the salon offers, identify a suitable service and specialist, find a valid time, and reach a confirmed appointment without outside assistance for a standard booking.

After booking, the customer should clearly understand what was booked, with whom, and when, and should be able to manage the appointment when allowed.

### Salon

Standard booking requests should be able to complete without unnecessary reception intervention while still respecting salon scheduling and eligibility constraints.
