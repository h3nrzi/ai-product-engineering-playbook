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

Whether reception-created bookings use the same no-preference option remains to be agreed in their detailed flow.

### Customer authentication

Approved by the user on 2026-10-03:

- Services, specialists, and available times can be browsed without login.
- Customers sign in with their mobile number and a one-time SMS code. Successful verification establishes the customer account/session; no password is required.
- A signed-out customer signs in before reviewing/submitting a booking. Preserve the selected service, specialist preference, and date/time across login, then recheck availability. Login does not reserve the selected time.
- A signed-in customer skips repeated phone entry and verification while the session is valid.
- Each online booking belongs to the authenticated customer account and uses that account’s verified mobile number. Do not ask for a separate booking phone number.
- “My appointments” shows appointments belonging to the signed-in account; an appointment link or reference alone does not grant access.
- SMS verification confirms control of the mobile number, not a government-verified personal identity.

Staff use their own salon access when recording a customer mobile number; this does not verify that number or create an authenticated customer session. A customer must sign in with an SMS code for that number before accessing the corresponding appointment in My appointments or through a booking link. Detailed account matching, number correction/recovery, and staff login mechanics remain for later flows.

### Deposit and confirmation

Approved by the user on 2026-10-03:

- Standard online appointments become confirmed only after a successful online deposit payment is verified. The remaining service balance is paid at the salon; the deposit is credited toward the service price.
- After the customer reviews the appointment and payment/cancellation terms, keep the selected time unavailable to other bookings for a short, explicitly displayed payment window. Merely browsing or signing in does not hold a time.
- Deposit calculation is percentage-based, as approved by the user on 2026-10-03: deposit = displayed booking price basis × deposit percentage / 100. The price basis is the fixed price for fixed-price services or the approximate usual-volume price for variable-price services. The remaining service balance is the final service price less the deposit already paid.
- Show the applicable percentage, calculated deposit, price used for calculation, remaining balance where calculable, and hold expiry before payment.
- Approved configuration: one salon-wide deposit percentage applies to all services in the MVP. Only management can set or change it; reception cannot edit it or override it for an appointment.
- Per-service deposit percentages are deferred. Management configures the salon-wide percentage, payment-hold duration, and advance cancellation window. No default numeric values are approved; currency rounding and setting validation rules remain to be defined. Reception cannot edit or override these settings.
- Approved variable-price model: management defines an approximate price for the usual service volume (for example, typical hair length/volume). The shared salon-wide percentage is applied to that approximate price to calculate the online deposit. Variable pricing alone does not require consultation before booking.
- Label the price as approximate, describe what “usual volume” means for that service, and explain relevant price factors such as hair length, volume, or materials. Show this information in service discovery and again in the booking review before payment.
- Clearly distinguish the exact deposit charged now from the approximate service price and estimated remaining balance. Explain that the final service price is determined at the salon and the balance is final price minus the deposit already paid. Do not present the estimate as a guaranteed total.
- Display the estimated-price basis and the paid deposit in appointment details after booking. A later final-price adjustment does not recalculate or retroactively increase the deposit already charged.
- Handling a final price below the paid deposit, and the procedure for agreeing the final price at the salon, remain to be defined. Services needing a genuine consultation prerequisite remain a separate decision; do not infer that requirement from variable pricing alone.
- Record the price basis, percentage, and charged deposit for the booking. Later catalog-price or percentage changes must not silently recalculate an existing appointment’s paid deposit.
- Display the configured payment-hold duration and actual expiry before payment, plus the cancellation window and refund consequences. Record the effective price basis, deposit percentage, calculated deposit, hold duration/expiry, and cancellation/refund terms when the customer accepts the review and starts the hold/payment attempt. The confirmed appointment retains those terms.
- Later changes to management settings apply only to new bookings. They must not rewrite existing appointment terms, move an active hold’s expiry, or change an existing appointment’s cancellation deadline. An accepted reschedule keeps the original policy window and recalculates the deadline relative to the new appointment time, as defined below.
- Payment that is failed, abandoned, or not completed within the hold window does not confirm an appointment; release the time when the hold ends.
- An uncertain payment result is shown as pending verification, not success or definite failure. Resolve it before encouraging another payment. A late verified payment after hold expiry must not silently claim an occupied slot; its recovery/refund policy remains open.
- The approved cancellation direction is deposit refund for customer cancellation within the permitted advance window; late customer cancellation or no-show does not refund the deposit under the disclosed salon policy. Management configures the advance cancellation cutoff. Customer rescheduling and salon-originated cancellation follow the approved rules below; refund processing details remain open.
- Temporary payment holds and confirmed appointments both constrain the shared availability used by online booking and reception.

This adds deposit collection and payment-result handling to the production MVP. Base44 may simulate the full journey and its payment/hold states without taking real payments.

### Reception-created bookings

Approved by the user on 2026-10-03:

- **Telephone booking:** reception records one service, relevant volume option, eligible specialist, valid time, and customer mobile number. The customer receives a link to review the booking and its price/payment/cancellation terms, signs in with the mobile-number/SMS-code flow, and pays the deposit. Confirm only after verified payment while the time remains valid.
- **In-person booking for a future visit:** use the same review/payment-link flow, or reception may receive and record the calculated deposit at the salon. Receipt of the deposit permits confirmation; the remaining balance is paid at the service visit. Recording receipt is not permission to waive the deposit or change the percentage.
- **Immediate walk-in:** reception checks an eligible specialist and valid time for the full selected duration, records the appointment, and payment occurs during the visit. No advance online deposit is required for this immediate-visit path. A future appointment must not use this path to bypass deposit requirements.
- All paths use the shared calendar. Future bookings awaiting deposit use the configured temporary payment hold; expiry releases the time if no payment has been verified or recorded. Do not create an indefinite reservation while waiting for the customer to open a link. The exact link-delivery channel and hold-start interaction will be specified in the flows.
- Reception shows or explains the deposit and cancellation terms before accepting an in-salon deposit. Preserve the booking’s price basis, applicable percentage, recorded payment, and accepted terms just as for online booking.
- Staff-entered mobile numbers remain unverified until the customer completes SMS-code authentication. Sending a link or recording an in-salon payment does not authenticate the customer. A link alone does not grant appointment access.
- Reception can record a deposit actually received at the salon and see the payment source/state. It cannot mark an unverified online payment as paid or alter deposit/payment/cancellation settings. This is appointment payment tracking, not a full accounting or POS system.

### Rescheduling and salon-originated cancellation

Approved by the user on 2026-10-03:

- Before the current appointment’s advance cancellation cutoff, a customer may choose a valid new time. Transfer the existing deposit to the rescheduled appointment; do not collect it again.
- Keep the original appointment and its time reserved until the replacement is confirmed. If the new time becomes unavailable or the change fails, leave the original appointment and deposit intact.
- Keep the original accepted price/deposit and policy terms. Use the original advance cancellation window to calculate the new deadline from the new appointment time, and show that deadline before the customer confirms. A manager’s later setting changes do not supply new terms to the reschedule.
- After the current cutoff, close customer online rescheduling and direct the customer to reception. Reception coordination is not an automatic exemption from the late-cancellation/no-show policy. Staff exception authority remains a separate decision; do not promise a free change.
- If the salon cancels, the customer is entitled to a full refund of the deposit actually paid, irrespective of the customer-cancellation cutoff. This applies to online and in-salon deposits; the operational refund route remains to be specified.
- The salon may propose another valid time or eligible specialist, but must obtain the customer’s acceptance before applying that alternative. Silence is not acceptance. If the customer declines, cancel with a full deposit refund. A proposed alternative must not silently release or replace a still-valid original appointment.
- Track cancellation and refund progress separately. A cancelled appointment does not imply money has already been returned. Refund timing, customer communication channel, and handling an unanswered salon proposal remain open flow details.

Changing the service or volume option during rescheduling is not included in this approval; its pricing/duration implications remain to be defined.

### Booking unit

Approved by the user on 2026-10-03: each MVP appointment contains one service with one eligible specialist. Multi-service appointments, service bundles, and coordinated appointments across specialists are deferred. This does not impose a daily booking limit; any such limit requires a separate decision.

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

Actual option labels and duration values remain service configuration, not invented defaults. Handling an inaccurate customer selection at the salon remains an open operational rule; it must not silently overlap another appointment.

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
