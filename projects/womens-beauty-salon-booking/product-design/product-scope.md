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

`Need beauty service → understand service options → evaluate relevant specialists → select service → choose specialist or any eligible specialist → see valid availability → select date/time → provide required details → review → confirm → receive confirmed appointment`

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
- book a valid appointment
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

Approved during Stage 04: customers use the booking and appointment-management experience; reception/management use one salon operations area and manage specialist schedules and appointments. Specialists retain profiles and service eligibility but have no independent login or dashboard in the MVP. Reception manages appointments, including phone and walk-in bookings in the shared calendar. Management has all reception capabilities plus control of services, prices, specialists, eligibility, and working schedules.

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
