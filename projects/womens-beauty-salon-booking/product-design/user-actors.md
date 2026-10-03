# User & Actor Definition — Women’s Beauty Salon Booking

## Status and evidence

Stage 04 in progress. The user has approved the MVP access direction below; remaining operational decisions are still open. This document derives from the approved problem, solution, and scope artifacts. Behavioral expectations below are design assumptions, not interview or usability-research findings.

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
- Constraints: only eligible specialists and times that fit the full duration are bookable. Consultation-dependent services and account/guest requirements remain unresolved.
- Accessibility direction: readable Persian content, clear form labels, understandable errors, and comfortable mobile controls; no assumed age or ability profile.

First-time and returning customers are usage contexts within this role, not separate permission roles. Repeat-booking shortcuts remain deferred unless later justified.

## Reception / salon operator

**Role:** Coordinate daily appointments and keep the booking schedule usable.

- Primary goal: maintain a reliable appointment calendar with minimal repeated calls and messages.
- Secondary goal: handle appointment changes and reflect specialist availability changes accurately.
- Needs: appointment details, service/specialist/time context, clear appointment state, and visibility into booking conflicts and permitted actions.
- Context assumption: work may be interrupted by in-person customers and calls; quick scanning and unambiguous action results matter.
- Pain points: fragmented requests, repeated availability checks, overlapping bookings, and changes that are not reflected in the calendar.
- Trust factors: the displayed schedule reflects accepted bookings and availability inputs; changes have clear outcomes.
- Constraints: salon-side actions must respect booking rules. Handling phone or walk-in appointments inside the product needs an explicit later decision so external bookings do not silently undermine availability.
- Device context: operational layouts should be usable on desktop/tablet and accessible on mobile; actual preferred device is unvalidated.

## Salon manager / owner

**Role:** Control the information and policies needed to offer bookable services.

- Primary goal: keep service information, specialist eligibility, and schedule inputs accurate.
- Secondary goal: supervise booking operations and ensure customer-facing information matches salon practice.
- Needs: essential controls over services, specialists, availability, and appointments.
- Pain points and objections: outdated information, dependency on staff memory, and administrative work that outweighs the booking benefit.
- Trust factors: predictable booking rules and understandable consequences when changing service or schedule information.
- Constraints: payroll, accounting, inventory, full CRM, and advanced business reporting remain outside scope.

Management and reception are distinct responsibilities. One person may perform both. Whether they require separate permissions is an open product decision, not an established requirement.

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
- One salon operations area used by reception/management to coordinate appointments and specialist schedules.
- Specialists retain customer-facing profiles, service eligibility, and working schedules, maintained by salon staff. They have no independent login or dashboard in the MVP.
- Specialist-originated appointment changes and cancellations are handled by reception/management. Customer self-service changes remain available when salon policy allows.

Possible later specialist access is deferred, not an MVP commitment. If justified later, it could cover viewing assigned appointments and reporting unavailability; it does not imply permission to change or cancel customer appointments.

## Open decisions

1. Do reception and management need different permissions, or can one salon operator role cover the initial product?
2. How are phone/walk-in appointments reflected in bookable availability?

Customer identity, consultation-dependent services, payment, and cancellation/rescheduling policies remain open from earlier discovery. Resolve them in the relevant journey and rules stages rather than inventing answers here.

## Completion condition

The MVP access direction is approved. Stage 04 remains in progress while reception/management permissions and operational booking responsibilities are clarified. Then update this document and the tracker before proceeding to Stage 05 — UX / Competitive Research.
