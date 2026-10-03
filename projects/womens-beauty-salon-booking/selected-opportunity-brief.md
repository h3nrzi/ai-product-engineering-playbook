# Selected Opportunity Brief — Women’s Beauty Salon Booking

## Product family

- **Family:** Barbershop / Beauty Salon Booking
- **Selected model / variant:** **Women’s single-salon**
- **Target market:** Persian-language product for the Iranian market

## Model boundary

This project represents **one physical women’s beauty salon** with multiple services and multiple specialists.

It is explicitly **not**:

- a men’s barbershop;
- a unisex salon;
- an independent-specialist marketplace;
- a multi-salon marketplace;
- a multi-branch salon network;
- a beauty-at-home / mobile-workforce service.

These adjacent variants remain valid models under the same product family, but they are different products with different operational and UX implications.

## Target users

- Women seeking beauty services from the salon.
- Salon reception/management responsible for appointment coordination.
- Beauty specialists whose service eligibility and schedules affect bookable appointments.

## Primary problem

Customers often need to call or message the salon to understand services, specialist fit, pricing, duration, and real availability before they can secure an appointment. The salon must repeatedly coordinate these details manually.

## Proposed solution direction

Create a self-service discovery, scheduling, and appointment-management experience that connects services, eligible specialists, and valid time slots while preserving salon booking rules.

## Why this project is worth exploring

The product has meaningful workflow depth beyond a marketing website: service discovery, specialist eligibility, schedule-based availability, appointment lifecycle, customer self-service, and salon-side operations.

## Initial product boundary

- One physical women’s beauty salon.
- Multiple services.
- Multiple specialists.
- Online appointment booking and management.
- One service per appointment in the MVP; multi-service appointments are deferred.
- Online deposit payment, calculated from one manager-controlled salon-wide percentage of the service price, confirms the appointment; the remaining service balance is paid at the salon.
- For variable-price services, the clearly disclosed approximate price for usual volume is the deposit basis; the final balance is settled at the salon after deducting the deposit.
- For variable-duration services, the customer selects a relevant volume option; management sets each option’s duration. Availability uses that duration, while the approximate usual-volume deposit basis stays unchanged.
- Phone bookings use customer review/payment links; future in-person bookings may use the same flow or a deposit received and recorded by reception. Immediate walk-ins pay during the visit.
- All booking sources share valid calendar availability; staff-entered customer numbers require customer SMS verification for account access.
- Customer rescheduling before the accepted cutoff carries the deposit to the new time; salon cancellation or customer rejection of a salon-proposed replacement returns the full deposit.
- Customer no-preference bookings use combined eligible availability and management’s specialist priority order; the assigned name is shown before payment, and confirmed specialist changes require customer acceptance.
- Booking information defaults from the customer profile and can be edited for the appointment, including its contact number; a different contact number requires SMS verification before payment/confirmation, while ownership remains with the signed-in account.
- Fixed-location service fulfillment.
- No marketplace mechanics.
- No at-home travel/service-area logistics.
