# Prompt 04 — Booking & Payment Flow

## Objective

Build the complete customer booking journey for the approved single-location women’s beauty salon prototype:

`Service → Volume when relevant → Specialist → Date/Time → SMS sign-in and booking details → Final review → Hold → Simulated deposit payment → Result`

This is the product’s primary customer flow. Preserve the public discovery work from Prompt 03, the shell/navigation from Prompt 02, the design system from Prompt 01, and the shared fixtures/policies from Prompt 00.

Do not redesign product rules to simplify implementation. Do not build the full customer account, reception workflows or manager controls yet; those are handled by later prompts.

## Scope and entry points

The booking journey may begin from:

- the global `رزرو نوبت` action,
- a directly bookable service detail,
- a supported service selected from a specialist profile.

Preserve context from the entry point:

- service-detail entry preselects that service;
- specialist-profile entry preserves the named specialist preference and requires choosing only a service that specialist actually provides;
- a consultation-required service must not enter the direct booking/payment flow and continues to the approved salon-contact path instead.

Each appointment contains exactly one service and one eligible specialist.

## Booking container

Use the existing P07 booking/result container rather than creating a separate full route for every step by default.

Required logical steps:

1. Service selection
2. Volume selection when duration varies
3. Specialist selection
4. Date/time selection
5. SMS sign-in and booking information
6. Final review
7. Hold/payment/status/result

Show a concise Persian progress indicator appropriate to the current step. On narrow screens keep one readable column. On wider screens a persistent/adjacent booking summary may be shown when there is enough room.

Back navigation should preserve still-valid choices. A changed dependency invalidates and rechecks only what depends on it.

## Step 1 — Service selection

Show one directly bookable service selection using the shared demo service data.

For every service show enough information to make a valid choice:

- service name,
- fixed vs approximate-price wording,
- relevant duration information,
- consultation prerequisite if any.

Rules:

- fixed-duration services proceed directly to specialist selection after service confirmation;
- duration-varying services require the approved volume step;
- consultation-required services do not show `پرداخت بیعانه` or a fake direct-booking path;
- changing service invalidates dependent volume, specialist and time choices where no longer valid.

## Step 2 — Volume selection

Show this step only when the selected service has manager-defined duration-varying volume options.

Use the shared realistic demo options created in Prompt 00.

Each option should show:

- Persian label,
- booking duration,
- concise relevant explanation.

Important pricing rule:

For approximate-price services, the volume choice determines booking duration and therefore availability. It does **not** automatically promise or recalculate a guaranteed final service price. Keep the approved `قیمت تقریبی مبنای بیعانه` wording distinct from final price agreed before the service starts.

Changing volume must recheck specialist/time availability and invalidate a previously selected time that no longer fits the new duration.

## Step 3 — Specialist selection

Offer:

- named eligible specialists for the selected service,
- `هر متخصص واجد شرایط`.

Do not display an ineligible specialist as selectable for the service.

For `هر متخصص واجد شرایط`:

- explain that the system chooses among eligible specialists who are free for the selected time, using salon priority;
- combined availability may be shown before assignment;
- after the customer selects a time, resolve an actual eligible specialist from the demo priority/availability data;
- the actual assigned specialist must be shown before payment/confirmation.

For a named specialist entry from Prompt 03, preserve the named preference unless the customer deliberately changes it.

Never silently replace a named specialist merely because another specialist has availability.

## Step 4 — Date and time selection

Build a clear full-duration availability selector based on the shared demo schedules, eligibility, duration and existing appointment/hold fixtures.

Use Tehran-time meaning and visible Solar Hijri date presentation.

States must distinguish:

- loading/rechecking,
- available,
- selected,
- unavailable,
- no valid times,
- stale/conflicting selected time.

Rules:

- the full selected service duration must fit;
- unavailable times cannot be submitted;
- a selected time is **not** a reservation and must not be described as held;
- when no valid time exists, offer another date or a customer-chosen specialist change rather than silently changing a named preference or shortening duration;
- when any-eligible is used, resolve and display the actual assigned specialist after time selection;
- if a previously selected time becomes invalid after a dependency change, keep valid upstream choices and ask for another time.

Use truthful copy before hold creation, such as:

`این زمان هنوز برای شما نگه داشته نشده است. هنگام پرداخت، آزاد بودن آن دوباره بررسی می‌شود.`

## Step 5 — Simulated SMS sign-in and booking information

Authentication is required before final review/submission, but discovery and availability remain public.

Use the customer authentication context established in Prompt 00.

Simulate:

- mobile number entry,
- SMS-code sending state,
- code entry,
- invalid/expired-code state,
- successful customer access.

Do not claim a real SMS was sent or real identity was verified.

Preserve the current booking selections while the user signs in. After successful sign-in, recheck dependent availability; login itself does not create a hold or extend any deadline.

### Booking information

Minimum intake:

- customer name,
- booking contact.

Prefill available demo profile values when appropriate.

If the booking contact differs from the account’s verified login number:

- require a separate simulated SMS verification for that contact before payment/confirmation;
- make clear that this verifies the booking contact only;
- do not sign into another account;
- do not transfer appointment ownership;
- editing the contact again invalidates verification for the changed value.

Account ownership, appointment contact and separately verified contact remain distinct.

## Step 6 — Final review

The final review must show the complete reviewed booking before any hold/payment attempt begins.

Show:

- service,
- selected volume when applicable,
- duration,
- actual assigned specialist by name,
- Solar Hijri date,
- exact start time with Tehran-time meaning where useful,
- customer/booking contact,
- fixed or approximate price basis,
- exact deposit amount,
- remaining fixed balance or approximate settlement explanation,
- applicable cancellation/rescheduling window and deadline information,
- clear statement that the selected slot is not held yet.

### Deposit calculation

Use the shared initial salon-wide default of 20% for new demo bookings.

Deposit basis:

- fixed-price service → fixed price;
- approximate-price service → disclosed approximate usual-volume booking price basis.

Calculate the deposit once and show the exact toman amount. Keep price basis, percentage and deposit distinguishable.

Do not describe an approximate service price as guaranteed final price.

### Primary action

Use the explicit action label:

`پرداخت بیعانه`

Place the exact deposit amount visibly near the action.

Do not create a hold merely by opening the review screen.

## Hold creation — exact trigger

When the customer selects `پرداخت بیعانه`:

1. disable duplicate submission;
2. recheck current full-duration availability for the reviewed actual specialist/time;
3. if still valid, secure the simulated hold;
4. save the reviewed booking terms for that attempt;
5. start the ordinary payment hold deadline only after the hold is successfully secured;
6. move to simulated payment/status behavior.

Initial demo ordinary hold duration: **10 minutes**.

If the hold cannot be secured:

- do not invite payment;
- do not show the time as held;
- preserve valid service/volume/specialist/customer information;
- return to time selection with a stale-slot/conflict message such as:
  `این زمان دیگر آزاد نیست. لطفاً زمان دیگری انتخاب کنید.`

## Hold state before payment starts

When a hold exists and payment has not yet started, show:

- actual held service/specialist/time,
- exact ordinary hold expiry,
- readable remaining time,
- message such as `زمان موقتاً برای شما نگه داشته شده است`,
- the next payment action.

Reopening, refreshing or navigating back must never restart the hold deadline.

If the customer wants to change service, volume, specialist or time while the hold is active **and payment has not started**:

- explicitly release/abandon the current unpaid hold first;
- then return to the requested selection step;
- any new attempt requires fresh availability and a new hold.

Do not keep multiple holds for one draft.

## Simulated external payment transition

Do not build a salon credit-card entry form.

Represent payment as a clearly simulated external-provider transition. The prototype may use deterministic demo controls/state transitions to demonstrate possible provider outcomes, but those controls must be clearly identified as prototype/demo behavior rather than customer-facing proof of a real bank transaction.

Once payment is initiated:

- mark the attempt as payment initiated;
- do not allow switching that same attempt to another service/specialist/time;
- do not show another enabled deposit-payment action while the current result is unknown;
- keep status retrieval available.

## Payment / hold outcome model

Implement all of these demonstrable states using deterministic demo data/state transitions.

### A. Verified success while slot is still held

Result:

- confirm exactly the reviewed specialist/time;
- appointment state becomes confirmed;
- payment state becomes verified success;
- deposit is recorded as paid;
- refund is not applicable.

Customer message:

`نوبت شما تأیید شد`

Show:

- service,
- actual specialist,
- date/time,
- paid deposit,
- remaining balance/estimate,
- `مشاهده نوبت` action toward the customer-area destination prepared in Prompt 02.

Do not claim real gateway verification outside the clearly simulated prototype context.

### B. Definitive payment failure

Result:

- release the hold immediately;
- appointment remains unconfirmed;
- payment state is definite failure.

Message:

`پرداخت انجام نشد؛ نوبت تأیید نشده است.`

Offer a route to current availability. A later retry must create a fresh valid hold/attempt rather than reusing an expired or released one.

### C. No payment started before ordinary hold expiry

Result:

- release the slot;
- attempt becomes expired/unconfirmed;
- no received deposit.

Message:

`زمان رزرو آزاد شد.`

Offer current availability for a fresh attempt.

### D. Payment started in time but result is unknown while held

Allow the slot to remain held only within the approved bounded extension.

Initial demo rule:

- ordinary expiry = hold creation + 10 minutes;
- final verification deadline may be up to 5 minutes after ordinary expiry **only when payment started before ordinary expiry and remains unknown**;
- initial maximum total = 15 minutes from hold creation.

Show:

`در حال بررسی پرداخت هستیم.`

Also show:

- whether the slot is still held,
- ordinary hold deadline,
- final verification deadline when applicable,
- `بررسی وضعیت پرداخت`.

Do not show a second payment button.

### E. Payment still unknown at final verification deadline

Result:

- release the slot;
- appointment remains unconfirmed;
- payment remains separately under verification.

Show both facts clearly:

- the appointment time has been released;
- the payment outcome is still unknown/checking.

Do not convert this state into a definitive payment failure merely because the slot was released.

### F. Payment success verified after the slot was already released

Result:

- **never** auto-confirm the appointment, even if the same slot currently appears free;
- appointment remains unconfirmed;
- payment becomes verified success;
- full-deposit refund entitlement is created;
- refund begins as a separate due/pending state.

Message:

`پرداخت دریافت شد، اما نوبت تأیید نشد. بیعانه کامل بازگردانده می‌شود.`

Show actual refund progress separately. Do not label the refund completed unless the simulated refund state explicitly becomes completed.

Offer an optional route to start a new booking from current availability; do not transfer the payment into a new appointment automatically.

## Payment-status read failure

Demonstrate a state where the status-check operation itself is unavailable.

In this case:

- keep the last known appointment/payment/hold state visible;
- show a recovery action such as `بررسی دوباره وضعیت`;
- offer salon contact where useful;
- do not call it a definite payment failure;
- do not extend the hold or verification deadline because status retrieval failed;
- do not invite duplicate payment.

## Result persistence in the prototype

Closing/reopening the result surface or navigating away must not visually reset an existing attempt into a fresh booking.

The simulated owning-customer context should be able to retrieve the current attempt state later. Prompt 05 will build the full account list/detail surfaces, but this prompt must preserve enough shared state so confirmed, expired, unknown-payment and late-success/refund attempts can be represented consistently later.

Do not promise real durable production persistence; this is prototype state continuity.

## Back navigation and dependency rules

Before a hold exists:

- allow back navigation;
- preserve valid upstream choices;
- invalidate only dependent values that no longer apply;
- recheck availability after service/volume/specialist changes.

After an unpaid hold exists:

- back navigation alone must not silently release or restart it;
- changing a held service/time/specialist requires explicit release first.

After payment starts or result becomes unknown:

- do not allow the current attempt to be switched to another slot;
- return the user to its authoritative status instead;
- a new booking can begin only as a separate fresh attempt when appropriate.

## Important state distinctions

Keep these concepts separately visible throughout the flow:

- selected slot ≠ held slot,
- held slot ≠ confirmed appointment,
- payment initiated ≠ payment success,
- payment success after release ≠ confirmed appointment,
- cancelled/unconfirmed attempt ≠ refund completed,
- SMS/contact verification ≠ account ownership transfer.

Do not combine appointment, payment and refund into one generic status badge.

## Responsive behavior

### Narrow screens

- one primary booking column;
- short readable progress label;
- summary may collapse/expand but must not lose entered choices;
- key actual specialist/time/deposit must remain easy to review before payment;
- final action may use a bottom action area only when it does not cover fields, errors, policy text, summary or mobile keyboard;
- use touch-friendly date/time choices and controls.

### Wider screens

- main form/step and adjacent booking summary may be shown side by side;
- keep the same step order and information;
- do not create a different desktop booking model.

## Persian / RTL content rules

Use natural Persian and the canonical terminology from the approved content direction.

Required key labels include:

- `رزرو نوبت`
- `هر متخصص واجد شرایط`
- `متخصص نوبت شما`
- `بیعانه`
- `پرداخت بیعانه`
- `قیمت تقریبی مبنای بیعانه`
- `نوبت تأییدشده`
- `در حال بررسی پرداخت`
- `بررسی وضعیت پرداخت`

Display:

- Solar Hijri dates,
- Persian digits for visible dates/amounts where appropriate,
- 24-hour time,
- `تومان` explicitly,
- phone/SMS fields as readable LTR segments inside RTL layout.

Consequential messages should include exact deadlines/date/time instead of using only relative phrases.

## Accessibility and interaction

Use the Prompt 01 design system.

- visible labels on all fields;
- visible keyboard focus;
- minimum 44 px interaction targets;
- keyboard-operable specialist and time selection;
- selected/unavailable/held/payment states must not rely on color alone;
- errors should be associated with the relevant field or state;
- move focus appropriately to major errors or confirmed outcomes;
- disable duplicate submit during hold creation/payment transition;
- do not announce a countdown every second to assistive technologies;
- respect reduced motion.

## Demo-data consistency

The same shared fixtures must produce consistent behavior across discovery and booking.

Verify that:

- selected service duration matches the availability calculation;
- specialist eligibility matches Prompt 03 public profiles;
- any-eligible assignment follows the shared manager priority and actual availability;
- shown price basis, 20% deposit and displayed amount agree;
- held interval matches the displayed full duration;
- outcome states do not contradict shared appointment/payment/refund vocabulary.

Do not invent a new service, specialist, policy or salon identity merely to make a booking screen easier to demonstrate.

## Do not add

Do not add in this prompt:

- multi-service cart or bundled appointments,
- waitlist,
- loyalty/wallet/store credit,
- saved payment methods,
- customer chat,
- real card-entry fields,
- real payment/SMS provider claims,
- scheduled reminders,
- customer rescheduling/cancellation management beyond links/placeholders needed for later Prompt 05,
- reception-created bookings,
- manager configuration forms,
- specialist dashboard,
- marketplace/branch behavior.

Do not rewrite completed public discovery or navigation unless needed to connect approved booking entry points.

## Acceptance check

Before considering this step complete, verify that:

- the booking journey follows service → conditional volume → specialist → time → sign-in/details → review → hold/payment/result;
- fixed-duration services skip volume cleanly;
- consultation-required services never enter misleading direct payment;
- named-specialist entry preserves the named preference;
- any-eligible resolves an actual eligible specialist and shows that name before payment;
- selected time is clearly not described as a hold;
- login/contact verification preserves valid choices and then rechecks availability;
- different booking contact verification does not transfer account ownership;
- final review shows service, volume/duration, actual specialist, date/time, price basis, exact deposit and applicable stored policy/deadline context;
- opening final review does not start a hold;
- `پرداخت بیعانه` rechecks availability and starts the 10-minute hold only after successful securing;
- stale/contested slot prevents payment and returns to valid time selection with useful input preserved;
- unpaid held choices require explicit release before changing service/specialist/time;
- once payment starts or becomes unknown, the attempt cannot be moved to another slot or paid again blindly;
- verified success while held confirms only the reviewed specialist/time;
- definitive failure releases the slot and remains unconfirmed;
- ordinary expiry without payment releases the slot;
- unknown payment may retain the slot only through the bounded additional verification window;
- unknown payment after final deadline releases the slot without falsely becoming definite failure;
- late verified success after release never auto-confirms and instead creates full-deposit refund entitlement;
- refund progress is distinct from appointment/payment state;
- closing/reopening does not reset an existing attempt or deadlines;
- status-check failure does not create false failure, duplicate payment or extra hold time;
- Persian/RTL, Solar Hijri, toman, Tehran-time and accessibility rules remain consistent;
- no real SMS/payment/refund/security guarantee or deferred feature has been introduced.

Stop after the primary booking/payment/result journey is coherent. Prompt 05 will build the authenticated customer account, appointment/attempt retrieval and permitted appointment-management workflows.