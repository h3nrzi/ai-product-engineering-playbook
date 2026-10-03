# Prompt 00 — Project Foundation

## Objective

Create the shared foundation for a Persian/RTL prototype of a **single-location women’s beauty salon booking product**. Establish the product boundaries, shared demo fixtures, role assumptions and global implementation guardrails that later prompts will build on.

Do **not** try to finish the whole application in this step. Do not invent missing business rules. Do not replace this prompt with a generic salon template.

## Product context

The product serves one physical women’s beauty salon in Iran. Customers discover services and specialists, choose a valid appointment time, authenticate by mobile/SMS, review the actual assigned specialist and booking terms, pay a deposit in a simulated flow, and later manage their own appointment where permitted.

Salon reception works from the same appointment/calendar truth. Managers additionally maintain services, specialist eligibility/priority, working schedules, booking rules, staff access and authorized exception/support actions.

This is **not**:

- a marketplace,
- a multi-salon or multi-branch product,
- an at-home/mobile beauty workforce,
- a multi-service cart or package booking product,
- a specialist self-service dashboard,
- a CRM, accounting/POS, payroll, inventory or marketing system.

Each appointment contains exactly **one service** and **one eligible specialist**.

## Global language and locale baseline

Set the application direction to RTL and make the visible product UI Persian by default.

Use these localization rules globally:

- Persian labels and natural Persian interface copy.
- Solar Hijri dates in visible customer/staff UI.
- 24-hour time with Tehran-time meaning.
- Persian digits for displayed dates and amounts where appropriate.
- Always label monetary amounts as `تومان`.
- Phone numbers and SMS-code input should remain readable as LTR segments inside RTL forms and accept Persian or Latin digits.
- Consequential actions must show exact date/time/deadline information rather than relying only on relative phrases such as “tomorrow”.
- Long Persian text must wrap; do not shrink important text to make it fit.

Do not invent a final salon name or logo. Use a clearly temporary label such as `سالن نمونه` wherever a name is structurally required and keep it obviously replaceable.

## Approved global product rules

Treat the following as fixed product behavior for the prototype:

1. Customers may choose a named eligible specialist or `هر متخصص واجد شرایط`.
2. When any-eligible is chosen, the actual assigned specialist must be shown before payment/confirmation; never silently substitute a different specialist after review.
3. Customer login/account ownership, appointment contact and separately verified contact are distinct concepts.
4. Authentication is simulated as mobile number + one-time SMS code. Never claim that a real SMS was sent or that real identity was verified.
5. The initial salon-wide deposit default is **20%** for new bookings.
6. The ordinary slot hold default is **10 minutes**.
7. If payment started before ordinary hold expiry but the result is unknown, the prototype may retain the slot for up to **5 additional minutes**. Reopening a link/page never restarts either deadline.
8. The initial cancellation/rescheduling window is **24 hours before appointment start**.
9. Eligible rescheduling transfers the existing deposit; it does not collect a second deposit.
10. Confirmed salon-side time/specialist replacement requires explicit customer acceptance before applying.
11. Qualifying salon cancellation or customer rejection of a salon replacement creates a full-deposit refund entitlement.
12. Appointment state, payment state and refund state are separate and must never be collapsed into one ambiguous status.
13. A cancelled appointment does not by itself prove that a refund completed.
14. A failed SMS does not reverse a successful booking/payment/refund operation.
15. Real authentication/security, persistence, payment gateway execution, refunds, SMS delivery and authoritative concurrent locking are outside the proof provided by this prototype; simulate them honestly.

## Shared demo fixtures

Create coherent reusable demo data that later pages and flows can reference. Keep all fixtures explicitly sample/demo data.

### Salon

Use a temporary salon identity:

- Display name: `سالن نمونه`
- City/context: Tehran demo context
- Currency: toman
- Deposit percentage: 20%
- Ordinary hold duration: 10 minutes
- Unknown-payment extension ceiling: 5 minutes after ordinary expiry
- Cancellation/rescheduling window: 24 hours before appointment start

Do not fabricate ratings, awards, review counts or claims such as “best salon”.

### Sample specialists

Create at least three clearly fictional demo specialists, for example:

- `نیلوفر احمدی`
- `سارا محمدی`
- `مهسا کریمی`

Each specialist should have:

- short neutral demo bio,
- supported-service relationships,
- working availability fixture,
- manager assignment priority,
- optional demo image/fallback,
- no rating/review score unless real data is later supplied.

### Sample services

Create a small but behaviorally useful service fixture set covering the required prototype cases:

1. A directly bookable fixed-price service with one fixed duration.
2. A directly bookable approximate-price service whose duration varies by a manager-defined volume option.
3. A consultation-required service that shows contact guidance rather than a misleading direct-booking CTA.

Use realistic Persian names and clearly demo prices/durations. Include enough specialist eligibility overlap to support both named-specialist and any-eligible booking demonstrations.

For the duration-varying service, create three clearly labeled demo volume options such as short / medium / long hair equivalents in Persian. Volume changes duration and therefore availability. It must not be described as a guarantee of final variable price.

### Sample customer and staff contexts

Prepare reusable simulated contexts for later flows:

- signed-out customer,
- authenticated customer owning appointments/attempts,
- reception staff with assigned access,
- manager with management access,
- verified phone with no assigned staff role for permission-denied demonstrations.

Do not expose private customer/staff data in public surfaces.

### Appointment/payment/refund fixture vocabulary

Support separate demo state vocabularies so later prompts can create realistic cases.

Appointment examples:

- awaiting deposit,
- expired/unconfirmed,
- confirmed,
- cancelled,
- completed,
- no-show.

Payment examples:

- not started,
- initiated / result unknown,
- verified success,
- definite failure.

Refund examples:

- not applicable,
- due/pending,
- completed,
- needs attention.

These are independent dimensions. Do not use a single generic badge such as “done” to represent all three.

## Visual foundation

Establish these approved global design foundations, without trying to finish every component in this prompt:

- Overall character: calm, professional, warm and refined.
- Page canvas: `#FAF7F3`.
- Main surfaces: `#FFFFFF`.
- Primary: `#5E3448`.
- Primary hover: `#4C2939`.
- Primary pressed: `#402130`.
- Soft accent: `#EEDCE2`.
- Main text: `#272327`.
- Supporting text: `#655D63`.
- Control border: `#91848B`.
- Decorative divider: `#E5DDD8`.
- Typography: Vazirmatn with a Persian-capable sans-serif fallback.
- Use moderate radii, restrained borders/shadows and no glossy/luxury-gold cliché styling.
- Customer/public layouts should be mobile-first.
- Staff operations may become denser on desktop/tablet but must remain readable and usable on narrow screens.

Do not create a new palette per page. Do not use color alone to communicate state.

## Structural foundation

Prepare the project so later prompts can build these areas without reworking the foundation:

- Public discovery and booking.
- Customer account / appointments.
- Salon reception/operations.
- Manager-only controls.

Do not fully implement those areas yet. Establish reusable shared data/context and clean boundaries for them.

Manager-only actions must remain unavailable to reception. A mobile number that passes simulated SMS verification but has no assigned staff role must still be denied operations access.

## Prototype honesty rules

The prototype may simulate backend-like behavior deterministically for demonstration, but the UI must describe simulated outcomes truthfully.

Use wording such as demo/simulated state where necessary. Never claim:

- a real SMS was delivered,
- a real bank payment occurred,
- a real refund was returned,
- real identity was verified,
- concurrency/security guarantees were proven.

Do not build a salon credit-card form. Payment-card entry belongs to an external provider and will only be represented by simulated transition/result behavior later.

## Do not add

Do not add any of the following during foundation work:

- marketplace/vendor selection,
- branch selector,
- home-service addresses/workforce dispatch,
- multi-service cart,
- bundled appointments,
- loyalty points,
- wallet/store credit,
- favorites,
- chat,
- ecommerce,
- reviews/ratings,
- waitlist,
- reminder automation,
- CRM pipeline,
- accounting/POS,
- payroll,
- inventory,
- specialist dashboard,
- AI beauty advisor.

Do not invent new booking/payment/refund policies because a UI pattern would be easier to implement.

## Acceptance check

Before considering this step complete, verify that:

- the project has a coherent Persian/RTL baseline;
- the temporary salon identity is clearly demo/replaceable rather than presented as a final brand;
- theme foundations match the approved palette and Vazirmatn direction;
- shared demo services include fixed-price, duration-varying approximate-price and consultation-required examples;
- shared specialist eligibility can support named and any-eligible demonstrations;
- customer/reception/manager/no-role contexts exist for later prompts;
- appointment, payment and refund states are modeled/displayable as separate concepts;
- default 20% deposit, 10-minute hold, possible 5-minute unknown-payment extension and 24-hour change window are available as shared demo policy values;
- no deferred feature or adjacent product model has been introduced;
- nothing in the foundation falsely implies production-grade SMS, payment, identity, persistence, refund or concurrency behavior.

Stop after the foundation is coherent. Do not continue into full design-system implementation, navigation shells, public pages or booking screens; those are handled by the following prompts.
