# User & Actor Definition — Women’s Beauty Salon Booking

## Status and evidence

Stage 04 approved. The user approved the MVP access direction and reception/management responsibilities on 2026-10-03. Detailed booking policies remain for later journey and rules stages. This document derives from the approved problem, solution, and scope artifacts. Behavioral expectations below are design assumptions, not interview or usability-research findings.

Confirmed context: one physical women’s salon, multiple services and specialists, Persian/RTL customer experience, and salon-controlled booking operations.

## Customer

**Role:** Discover a service and secure or manage her own appointment.

- Primary goal: choose a suitable service, an eligible specialist or any eligible specialist, and a valid time with clear confirmation.
- Secondary goal: view upcoming appointment details and change or cancel an appointment when policy allows.
- Needs: understandable service descriptions, pricing model, expected duration, specialist expertise, available times, and clear booking/change rules.
- Context: first-time and returning customers; routine maintenance and event-driven needs. Mobile use is a design priority.
- Decision factors: service fit, specialist trust and style, price clarity, date/time fit, and salon location.
- Pain points and objections: uncertainty about cost, choosing the wrong service or specialist, unreliable availability, and uncertainty about whether booking succeeded.
- Trust factors: truthful service/specialist information, clear confirmation, and an understandable way to contact the salon when a need cannot be handled through standard booking.
- Constraints: only eligible specialists and times that fit the full duration are bookable. Customers authenticate with a mobile number and SMS code before online booking; booking uses the verified account number. Browsing remains public. Consultation-dependent services remain unresolved.
- Accessibility direction: readable Persian content, clear form labels, understandable errors, and comfortable mobile controls; no assumed age or ability profile.

First-time and returning customers are usage contexts within this role, not separate permission roles. Repeat-booking shortcuts remain deferred unless later justified.

## Reception / salon operator

**Role:** Coordinate daily appointments and keep the booking schedule usable.

- Primary goal: maintain a reliable appointment calendar with minimal repeated calls and messages.
- Secondary goal: handle appointment changes and communicate specialist availability changes to management.
- Needs: appointment details, service/specialist/time context, appointment/payment state, payment-review links for future bookings, recording deposits actually received in the salon, and visibility into conflicts and permitted actions.
- Context assumption: work may be interrupted by in-person customers and calls; quick scanning and unambiguous action results matter.
- Pain points: fragmented requests, repeated availability checks, overlapping bookings, and changes that are not reflected in the calendar.
- Trust factors: the displayed schedule reflects accepted bookings and availability inputs; changes have clear outcomes.
- Constraints: appointment actions must respect eligibility, full service duration, working schedules, and existing bookings. Reception records phone and walk-in appointments in the same calendar used for online availability. Reception cannot change services, prices, specialist profiles/eligibility, or working schedules.
- Device context: operational layouts should be usable on desktop/tablet and accessible on mobile; actual preferred device is unvalidated.

## Salon manager / owner

**Role:** Control the information and policies needed to offer bookable services.

- Primary goal: keep service information, specialist eligibility, and schedule inputs accurate.
- Secondary goal: supervise booking operations and ensure customer-facing information matches salon practice.
- Needs: essential controls over services, specialists, availability, and appointments.
- Pain points and objections: outdated information, dependency on staff memory, and administrative work that outweighs the booking benefit.
- Trust factors: predictable booking rules and understandable consequences when changing service or schedule information.
- Constraints: payroll, accounting, inventory, full CRM, and advanced business reporting remain outside scope.

Management and reception have separate access levels within the same salon operations area. Management has all reception capabilities plus service, price, specialist, working-schedule, volume-option/duration, and shared deposit-percentage, payment-hold-duration, and cancellation-window controls. One person may perform both responsibilities using management access.

## Beauty specialist

**Role:** Deliver eligible services at the booked times; expertise and availability affect customer choice and scheduling.

- Primary goal: receive accurate service, timing, and customer context for appointments assigned to her.
- Secondary goal: have working hours and service eligibility represented accurately.
- Needs: clarity about the booked service and duration, relevant appointment changes, and a way for availability changes to reach the salon operator.
- Context assumption: specialists may be occupied during appointments, so the product should not depend on continuous specialist interaction for standard bookings.
- Pain points: unsuitable assignments, insufficient time, overlapping work, and missed schedule changes.
- Trust factors: appointments respect eligibility and availability; customer-facing expertise information is accurate.
- Constraints: a specialist is a meaningful actor even if she has no product login. The approved MVP has no independent specialist login or dashboard; reception/management maintain specialist schedules and appointments.

## Relationships

- Customer selects among salon services and eligible specialists; the salon owns the service offering and appointment operations.
- Reception coordinates the schedule; management maintains the information and rules that make booking possible.
- Specialist expertise, eligibility, and availability constrain customer booking options.
- A booking or availability change affects customer expectations and salon coordination; later journeys must show who makes the change and how affected people learn about it.

## Approved MVP access direction

Approved by the user on 2026-10-03:

- Customer-facing booking and appointment management.
- One salon operations area with two access levels.
- Reception: view, create, reschedule, cancel, and manage appointments, including phone and walk-in bookings, subject to booking rules. Provide review/payment links for telephone/future bookings and record deposits actually received at the salon for future in-person bookings. Immediate walk-ins pay during the visit. These capabilities do not include waiving future-booking deposits, asserting uncertain online payments succeeded, or changing deposit settings.
- Management: all reception capabilities plus management of services, prices, specialists, service eligibility, working schedules, service volume options and their durations, and the salon-wide deposit percentage, payment-hold duration, and advance cancellation window. Reception cannot edit or override these settings; per-service percentages are deferred.
- Phone, walk-in, and online appointments share the same calendar and constrain bookable availability.
- Specialists retain customer-facing profiles, service eligibility, and working schedules, maintained by salon staff. They have no independent login or dashboard in the MVP.
- Specialist-originated appointment changes and cancellations are handled by reception/management. Customer self-service changes remain available when salon policy allows.

Possible later specialist access is deferred, not an MVP commitment. If justified later, it could cover viewing assigned appointments and reporting unavailability; it does not imply permission to change or cancel customer appointments.

## Decisions for later stages

Customer mobile-number/SMS-code authentication and account-based appointment retrieval are approved. Staff login mechanics, detailed matching/correction of customer numbers, consultation-dependent services, deposit configuration values, rescheduling treatment, and detailed cancellation/refund policies remain open. Phone/future in-person booking payment paths and immediate walk-in payment at the salon are approved. Staff-recorded mobile numbers do not authenticate customers; customer account access requires SMS verification. Online deposit payment for confirmation and remaining payment at the salon are approved. Exact phone/walk-in intake details and appointment states will be defined with the salon journeys. These do not change the approved actor responsibilities.

## Completion

Meaningful actors, customer contexts, responsibilities, relationships, and MVP access boundaries are defined. Stage 04 is complete; proceed to Stage 05 — UX / Competitive Research.
