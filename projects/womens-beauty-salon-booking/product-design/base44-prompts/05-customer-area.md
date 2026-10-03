# Prompt 05 — Customer Area

## Objective

Build the authenticated customer area for the approved **single-location women’s beauty salon booking product**.

This step completes the customer-facing account experience after Prompt 04. It must let the original owning customer retrieve current and past appointments, interrupted/unconfirmed booking attempts, payment/refund attention, permitted appointment changes, salon replacement proposals and profile/support information.

Preserve all work from Prompts 00–04. Do not redesign discovery, navigation, booking or payment behavior unless a real contradiction prevents the customer area from reflecting the approved current state.

Do **not** build salon staff operations or manager controls here; those belong to Prompts 06 and 07.

## Customer-area scope

Implement these approved customer surfaces:

- `نوبت‌های من` — appointments and booking/payment attempts.
- Appointment / attempt detail.
- Reschedule flow.
- Cancellation consequence review.
- Salon replacement proposal response.
- Payment-status retrieval where an attempt is unresolved.
- Refund progress.
- `اطلاعات من` — profile defaults, login identity and support explanation.
- Sign-out and safe customer-context switching.

Do not add wallet, loyalty, favorites, messages/chat, saved cards, notification inbox, payment-method management, subscription or ownership-transfer self-service.

## Access and ownership

Customer area is private and belongs to the **original owning customer account**.

Preserve these rules:

- A booking reference, SMS link, appointment contact or matching customer name is not ownership proof.
- Appointment contact and account ownership are distinct concepts.
- Verifying a different booking contact does not transfer the appointment to that number’s account.
- A signed-out deep link should pass through the simulated customer SMS login and then return to the intended private destination.
- A logged-in customer must not see another account’s appointment data.
- Sign-out/account switching must clear the prior account’s private presentation before the next account loads.
- The prototype may simulate ownership deterministically but must not claim production-grade identity/security enforcement.

Use the customer shell created in Prompt 02 with navigation:

- `نوبت‌های من`
- `اطلاعات من`

## 1. My appointments and attempts

Build `نوبت‌های من` as the authoritative customer retrieval surface.

Group records so customers can distinguish:

1. upcoming confirmed appointments,
2. pending/unconfirmed booking or payment attempts,
3. past/cancelled/completed/no-show records.

Do not hide an interrupted payment attempt merely because its slot expired. Do not hide a refund that still needs attention merely because its appointment was cancelled.

Each card/list item should show enough information to identify the record without opening it:

- service,
- actual specialist where assigned,
- date/time when applicable,
- appointment state,
- meaningful payment attention when applicable,
- refund attention when applicable,
- one clear action such as `مشاهده جزئیات` or `بررسی وضعیت پرداخت`.

Appointment/payment/refund status must remain separate. Avoid one combined generic status badge.

### Required list states

Include coherent demo states for:

- loading,
- no appointments at all,
- no upcoming appointments but existing history/attempts,
- read failure,
- pending payment attention,
- refund needs-attention.

`هنوز نوبتی ثبت نکرده‌اید` is valid only for a true empty account, not a failed read.

## 2. Appointment / attempt detail

Build one reusable customer detail surface for appointments and booking attempts.

Show the authoritative saved/current information:

- service,
- selected volume when relevant,
- booked duration,
- actual specialist,
- appointment date/time,
- booking contact where relevant,
- saved fixed/approximate price basis,
- exact deposit amount,
- remaining/final balance wording when known,
- stored cancellation/rescheduling terms and exact deadline,
- separate appointment state,
- separate payment state,
- separate refund state,
- active salon replacement proposal when one exists.

Use exact Solar Hijri date/time and Tehran-time meaning for consequential deadlines.

Do not recalculate an existing appointment from current manager defaults. Existing records retain their accepted terms.

### State-driven actions

Only show actions that are valid for the current record, for example:

- `تغییر زمان نوبت`
- `لغو نوبت`
- `بررسی وضعیت پرداخت`
- `پذیرش تغییر`
- `رد پیشنهاد`
- `تماس با سالن`
- optional new-booking action after a completed/cancelled record

Do not expose edit actions for completed/no-show history.

## 3. Interrupted and unresolved payment attempts

Reuse the attempt behavior from Prompt 04 inside the customer account.

The owning customer must be able to reopen and see the current state after closing/reloading the result page.

Support at least these account-retrievable cases:

- hold expired with no payment started,
- definite payment failure,
- payment result unknown while still held,
- payment result unknown after the slot was released,
- verified success while held → confirmed appointment,
- late verified success after release → no appointment confirmation plus full-refund entitlement.

For an unknown existing payment:

- show current known status,
- show whether the slot is still held or already released,
- show the actual relevant deadline if still applicable,
- offer `بررسی دوباره وضعیت`,
- do **not** present another Pay action while the same payment attempt remains uncertain.

A status-check read error is not a definitive payment failure.

## 4. Customer rescheduling

Implement customer rescheduling from an eligible confirmed appointment.

Initial approved default: rescheduling is allowed online at or before the appointment’s stored **24-hour** cutoff. Existing appointments use their stored rule even if management later changes defaults.

### Reschedule flow

1. Customer opens the original appointment.
2. Choose `تغییر زمان نوبت` when currently eligible.
3. Show the original appointment clearly.
4. Select a valid replacement date/time using the same service, volume, duration and specialist identity already attached to this appointment.
5. Show a final comparison/review with the replacement time and recalculated new cutoff.
6. Apply the replacement atomically in the simulated behavior.
7. On success, move the appointment and carry the existing deposit forward.

### Critical rules

- Do not collect a second deposit.
- Do not change service or volume through this approved reschedule path.
- Preserve the original accepted price/policy terms.
- Keep the original appointment and deposit intact until the replacement succeeds.
- Recheck availability when applying the replacement.
- If the replacement conflicts or fails, leave the original appointment unchanged.
- If the operation outcome is unknown, read current authoritative appointment state before allowing a retry.
- Back/cancel before commit leaves the original untouched.
- Calculate the new cutoff from the new appointment time using the original stored cancellation/rescheduling window and show it before confirmation, even if the recalculated deadline is already past.

### Cutoff behavior

Recheck eligibility when the action is applied, not only when the screen first opened.

If the cutoff passes while the customer is on the screen:

- online rescheduling becomes unavailable,
- retain the original appointment,
- explain the current consequence,
- offer salon contact for manager-reviewed exception routing without promising an exception.

## 5. Customer cancellation

Implement deliberate cancellation review from eligible appointment details.

Before applying cancellation show:

- exact appointment identity,
- stored cutoff/deadline,
- exact deposit amount,
- whether the approved rule grants a full refund or no refund,
- `لغو نوبت` as the explicit destructive action,
- `حفظ نوبت` as the safe alternative.

### Cancellation rules

At or before the stored cutoff:

- customer cancellation creates full-deposit refund entitlement.

After the cutoff:

- customer cancellation remains possible,
- disclose that the deposit is not returned under the default stored rule,
- online rescheduling is unavailable,
- manager exception is not implied by merely contacting the salon.

After successful cancellation:

- appointment becomes cancelled,
- slot is released,
- refund state is shown separately when applicable,
- failed SMS notification does not reverse the cancellation.

A cancelled appointment must never automatically display `بازپرداخت انجام شد` unless the refund state is actually completed in the simulated fixture.

## 6. Salon replacement proposal response

Support an appointment that has an active salon-proposed specialist/time change.

On the customer appointment detail:

- keep the current/original appointment visible,
- show the proposal separately,
- clearly compare original vs proposed specialist/time,
- explain that the change applies only after customer acceptance and successful recheck,
- provide explicit `پذیرش تغییر` and `رد پیشنهاد` actions.

### Acceptance

On accept:

- recheck replacement availability,
- apply only if still valid,
- if conflict occurs, preserve the deliverable original appointment and show recovery rather than silently choosing another option.

### Decline

If the customer declines a salon-originated replacement:

- apply the approved salon-side outcome,
- cancellation/refund entitlement is full deposit where the original cannot continue under the approved replacement/cancellation scenario,
- show refund progress independently.

Silence is never acceptance. Merely delivering an SMS is not acceptance.

Do not let the customer “accept” a generic any-specialist substitution without seeing the actual proposed specialist.

## 7. Refund progress

Where a refund entitlement exists, show a dedicated refund section/state inside the relevant appointment/attempt detail.

Support:

- `بازپرداخت در انتظار / در حال پیگیری`
- `نیازمند پیگیری`
- `بازپرداخت انجام شد`

Show where known:

- exact amount,
- source/route in general customer-readable terms,
- current progress,
- verified/documented completion reference/time only for the completed fixture.

Do not invent a refund ETA.

Do not imply that:

- cancellation equals completed refund,
- sending a refund request equals completed refund,
- a failed refund removes the entitlement,
- wallet/store credit exists.

Late verified payment after slot release should show: payment received, appointment not confirmed, full-deposit refund entitlement, and current refund progress.

## 8. My information

Build `اطلاعات من` as a simple customer information/support surface.

Show:

- customer profile name/default where available,
- verified login mobile number,
- clear explanation that booking contact may differ from login/account ownership,
- salon-coordinated support path for login-number change/recovery,
- sign-out.

Do not build a self-service account-ownership transfer editor.

Do not merge accounts automatically.

Do not imply that editing an appointment contact changes login identity or account ownership.

A login-number change/recovery request belongs to salon-coordinated manager support and will be completed operationally in later prompts. Customer UI should explain the support path without pretending it can independently verify ownership.

## 9. Cross-links and continuity

Ensure these transitions work coherently:

- Prompt 04 verified booking result → exact appointment detail.
- Prompt 04 interrupted/unknown attempt → exact attempt detail.
- `نوبت‌های من` → appointment/attempt detail.
- appointment detail → reschedule/cancel/proposal response/status check as allowed.
- cancelled/refunded/history detail → optional start-new-booking entry.
- `اطلاعات من` → salon contact/support.
- signed-out private deep link → simulated login → intended customer detail.

Do not lose the intended destination during simulated login.

## 10. Customer responsive behavior

Customer area is mobile-first.

On narrow screens:

- use grouped appointment cards,
- stack status sections clearly,
- keep the most relevant action visible without covering policy/deadline information,
- show cancellation/refund consequences in normal vertical reading order,
- avoid horizontally scrolling critical tables.

On wider screens:

- lists may expose more metadata,
- appointment detail may use a main-detail + summary arrangement,
- preserve the same action hierarchy and information.

Long Persian names, policies and statuses must wrap. Do not truncate specialist identity, appointment time, amount, cutoff or refund consequence.

## 11. Required demo scenarios

Using the shared fixtures, make the customer area capable of demonstrating at least:

1. Upcoming confirmed appointment within the change window.
2. Confirmed appointment after the change window.
3. Successful reschedule transferring the existing deposit.
4. Replacement-slot conflict preserving the original appointment.
5. Cancellation with full-refund entitlement.
6. Cancellation after cutoff with no-refund consequence.
7. Unknown payment attempt still under verification.
8. Unknown payment after slot release.
9. Late verified payment with refund pending.
10. Cancelled appointment with refund completed as a distinct later state.
11. Salon replacement proposal awaiting customer response.
12. Customer decline/accept path for a salon proposal.
13. Completed/no-show history record.
14. True empty account and separate read-error state.

Keep these fixtures coherent with Prompt 04 deposit, service, specialist and timing data.

## 12. Prototype honesty

All customer-area records are deterministic demo fixtures/simulations.

Never claim:

- real SMS authentication,
- real payment verification,
- real refund execution,
- production persistence,
- production authorization/security,
- real concurrent booking guarantees.

The UI may present realistic simulated state transitions, but customer-facing copy must not misrepresent them as actual external transactions.

## Do not add

Do not add during this step:

- wallet or credit balance,
- loyalty points,
- favorites,
- review/rating submission,
- chat/messages inbox,
- reminder preferences/notification center,
- saved payment methods,
- multi-service booking changes,
- customer-selected service/volume change during reschedule,
- self-service account ownership transfer,
- staff calendar/receipt operations,
- manager exception approval UI,
- analytics/accounting/CRM features.

Do not silently change the approved 20%/10-minute/5-minute/24-hour defaults for new demo records.

## Acceptance check

Before considering this step complete, verify that:

- `نوبت‌های من` clearly separates upcoming confirmed appointments, pending/unconfirmed attempts and history;
- true empty and read-error states are distinct;
- interrupted/unknown payment attempts remain retrievable after leaving the result screen;
- appointment detail shows service, actual specialist, date/time, saved terms, deposit and separate appointment/payment/refund states;
- customer access is restricted to the original simulated owning account;
- a different booking contact does not become account owner;
- eligible rescheduling keeps service/volume/specialist identity, transfers the existing deposit and does not charge a second deposit;
- replacement failure/conflict leaves the original appointment intact;
- cutoff eligibility is rechecked when an action is applied;
- cancellation explicitly shows full-refund vs no-refund consequence before commit;
- cancellation and refund completion are visually/semantically separate;
- a salon replacement proposal shows original vs proposed details and requires explicit customer acceptance;
- unknown payment never exposes a blind repeat-payment action;
- late verified payment after slot release never auto-confirms the appointment and instead shows refund entitlement/progress;
- `اطلاعات من` distinguishes login identity from appointment contact and routes number-change/recovery to salon support;
- sign-out/account switching removes prior private customer content;
- narrow-screen layouts keep identity, time, amount, deadlines and consequences readable;
- no deferred customer feature or salon-operations feature has been introduced.

Stop once the customer account, customer appointment actions and customer-visible payment/refund continuity are coherent. The next prompt builds salon reception/operations.