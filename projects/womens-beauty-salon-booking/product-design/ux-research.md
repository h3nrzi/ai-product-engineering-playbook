# UX / Competitive Research — Women’s Beauty Salon Booking

## Status and method

Research gathered on 2026-10-03. Stage 05 research is complete and persisted. The user approved one service per MVP appointment. Other proposed design directions remain recommendations to refine in journeys and flows, not independently approved new scope.

Scope: one women’s salon, customer self-service booking, a shared salon calendar, reception/management access levels, and no specialist dashboard in the MVP.

Evidence includes public official product documentation and direct browser inspection of one Fresha salon page and the service-selection flow at desktop and 390 × 844 mobile viewport sizes. No booking was submitted. Staff operations were studied through official documentation, not a signed-in staff workspace. These are desk-research findings, not customer interviews or usability-test results. Product claims do not establish real-world reliability or conversion gains.

## Reference set

- Direct domain / customer UI: [Silhani Beauty on Fresha](https://www.fresha.com/a/silhani-beauty-london-36a-commercial-road-pwsjjqqx). Inspect the salon-specific page rather than copying its surrounding marketplace or other-branch navigation.
- Availability reference: [Fresha appointment assignment](https://www.fresha.com/help-center/knowledge-base/calendar/102178-set-up-new-appointment-assignment).
- Operations reference: [Fresha appointment management](https://www.fresha.com/help-center/academy/run-your-business/schedule-appointments/lessons/100253).
- Role reference: [Booksy staff permissions](https://support.booksy.com/hc/en-gb/articles/16535688940946-How-do-I-manage-staff-permissions).
- Adjacent entry-point reference: [Booksy getting started](https://booksy.com/biz/en-us/lp/getting-started-on-booksy), including booking links from a website or social channels.
- Iranian-language reference: [Nobatyar](https://nobatyar-app.ir/). Its indexed public page describes Persian service/time selection, mobile-number entry, appointment tracking, and payment at the venue. Direct page retrieval failed, so these are indexed marketing claims; its live booking UI and behavior were not verified.

## Findings and project implications

### Service discovery and trust

**Observed:** The inspected Fresha salon page groups services into categories and displays name, price, and duration together. Team information, venue details, imagery, and reviews are separately discoverable. Service selection exposes additional conditions; the inspected lash service led to a prerequisite question before further booking.

**ADOPT:** Display service name, a concise explanation, pricing model, and expected duration before selection. Show relevant specialist expertise and salon contact/location information.

**ADAPT:** Make required consultation or other preparation visible on the service description as well as in booking. The reference’s specific prerequisite is not a rule for our salon. Distinguish a fixed price from an estimate or starting price; do not imply a final cost when it is unresolved.

**AVOID:** Copying review scores, badges, or portfolio claims without real supporting data. Reviews and extensive portfolios are not added to the MVP by this research.

### Specialist selection and valid availability

**Documented:** Fresha permits a named professional or no preference, assigning only an available team member who offers the service. It does not offer a slot when no eligible provider is available.

**ADOPT:** Preserve our existing service → eligible specialist or any eligible specialist → valid time direction. Named specialist selection must remain explicit.

**ADAPT:** Explain “any eligible specialist” in Persian and show the assigned specialist before final confirmation. The assignment strategy remains a later rules decision; do not introduce ranking, reviews, or load-balancing settings automatically.

**DIFFERENTIATE:** When no time is available, explain the scope of the result and offer another date or an eligible specialist alternative without silently replacing the customer’s selection. This is our proposed recovery pattern, not observed behavior in the inspected flow.

### Mobile interaction and visual reference

**Observed:** Fresha’s mobile service-selection view uses a single column, distinct service cards, a clearly highlighted selection, and a persistent bottom summary with price/duration and Continue. Category tabs can extend beyond the visible width. The desktop salon page uses neutral surfaces, clear text hierarchy, category controls, and a prominent booking action.

**ADOPT:** Keep the selected service and expected cost/duration accessible while progressing; make Back and the primary action easy to find.

**ADAPT:** Use short Persian categories, RTL ordering, explicit date/time labels, and local price units. Avoid essential categories being discoverable only by horizontal scrolling. The Persian calendar presentation and detailed digit conventions remain for the responsive/content stage.

**AVOID:** Copying the reference’s exact colors, typefaces, imagery, or marketplace navigation. This is a layout reference; brand and visual-system decisions belong to Stages 11–12.

### Salon calendar and access boundaries

**Documented:** Fresha supports appointment-detail editing, cancellations, and rescheduling from the appointment or through calendar dragging. Booksy distinguishes reception permissions from wider management controls.

**ADOPT:** One calendar across booking sources; appointment details show customer, service, specialist, time, and state. Preserve the already-approved reception/management split.

**ADAPT:** Offer a clear detail-based rescheduling action with valid alternatives and an explicit result. Calendar drag-and-drop is optional, not an MVP requirement or the only way to reschedule.

**AVOID:** Importing financial reports, inventory, marketing, commissions, broad customer databases, or competitor permission complexity. Reception must not gain service, price, specialist, or schedule-setting controls through an appointment action.

### Confirmation, appointment management, and recovery

**Local reference claim:** Nobatyar describes immediate confirmation, a tracking code, customer cancellation, and mobile-web use. Its daily-booking limit and notification channels are its own product choices.

**ADOPT:** A clear result containing service, specialist, date/time, and next steps, plus an understandable route back to the appointment.

**ADAPT:** Surface cancellation/rescheduling policy before confirmation and again beside management actions. At research time these were open. Customer mobile-number/SMS-code login, deposit-backed future bookings, and manager-configured payment/cancellation windows have since been approved. Telephone bookings use review/payment links; future in-person bookings also permit deposits received and recorded at the salon; immediate walk-ins pay during the visit. Numeric setup values, rescheduling/refund exceptions, and link-delivery channels remain open.

**AVOID:** Copying daily limits, requiring app installation, or silently adding reminders, Telegram, payments, or cancellation fees.

**DIFFERENTIATE:** If a selected time becomes unavailable, retain the service/specialist choices and explain how to choose another time. If confirmation status is unknown after a connection failure, help the customer check the appointment before submitting again. When rescheduling fails, retain the original appointment until a replacement is confirmed. These are design recommendations for later flows/states, not competitor behavior verified in this study.

## Proposed direction for the next stage

- Direct entry into this salon’s services, with an alternative entry from a specialist profile.
- Price/duration clarity and eligible specialist selection before time selection.
- Mobile booking with a persistent summary and a clear final review/result.
- One salon calendar supporting online, phone, and walk-in bookings within approved role boundaries.
- Explain unavailable times and failed changes with actionable recovery.

Approved booking boundary: one service per MVP appointment. Multi-service coordination remains deferred. This is not a restriction on how many separate appointments a customer may have; no daily limit has been approved.

## Limits and follow-up

No production guarantees, live booking completion, customer identity, payment, or cancellation behavior were tested. Mobile inspection covers the service-selection and prerequisite views, not the complete journey. Iranian demand and user preferences were not inferred from competitor claims.

Next: define Stage 06 jobs and journeys using the approved one-service booking unit. Carry consultation-dependent services, staff login mechanics, account matching/number correction, numeric setup values, rescheduling/refund exceptions, any-specialist assignment, and link-delivery/notification details as explicit open decisions. Staff-entered numbers and booking links do not grant customer account access without SMS verification. Later prototype checks should verify service clarity, slot recovery, confirmation understanding, and reception’s shared-calendar workflow.
