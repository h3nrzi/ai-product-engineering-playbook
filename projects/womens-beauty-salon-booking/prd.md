# PRD — Women’s Beauty Salon Booking

## Document control

- **Product revision:** 1.0 — Final product baseline
- **Approval:** Approved baseline; this structural revision is explicitly user-authorized.
- **Authorization evidence:** User request on 2026-10-05: “prd سالن رو با این تصمیم اخیری ک گرفتیم ورژن نهایش رو بساز”. Authorization covers applying the product-only template and revision policy, not new product scope.
- **Product Family:** Barbershop / Beauty Salon Booking
- **Selected Model / Variant:** Women’s single-salon
- **Target Market:** Persian-language product for the Iranian market
- **Delivery phase detailed in this revision:** 1 — Core Scheduling MVP
- **Canonical repository:** https://github.com/h3nrzi/ai-product-engineering-playbook
- **Canonical path:** `projects/womens-beauty-salon-booking/prd.md`

This document defines required product behavior, business boundaries, delivery scope, and observable acceptance outcomes. It is read-only during engineering, review, acceptance, and visual redesign. Only an explicitly user-authorized product revision may change it.

Technical decisions belong in module specs and appropriate ADRs in the implementation repository. Current module status, execution plans, operational prerequisites, and acceptance evidence belong in the project tracker and engineering artifacts. They are not maintained in this PRD.

The publishing Git commit identifies this baseline. Copies must reference that canonical commit and must not evolve independently.

---

# 1. Product Identity

This product is a booking and appointment-operations system for **one physical women’s beauty salon**.

Customers should be able to understand the salon’s bookable services and specialists, find valid availability, create an appointment, and later retrieve their own appointments.

Salon staff should operate the same scheduling truth: managers configure the salon’s offering and working schedules, while authorized staff can see and manage appointments on the salon calendar.

The product is not a marketplace and does not represent multiple independent salons or branches.

---

# 2. Problem and Desired Outcome

## Problem

Beauty-salon appointments are often coordinated through fragmented channels such as calls, direct messages, or manual notes. This creates avoidable friction:

- customers do not know which services, specialists, or times are genuinely available;
- salon staff repeatedly answer routine availability questions;
- customer and staff scheduling views can diverge;
- conflicting or incomplete bookings are easier to create;
- managers lack a single controlled place to define what can actually be booked.

## Desired outcome

Create a shared scheduling product where:

- the salon controls what services and specialists are bookable;
- availability is derived from salon-controlled schedules and existing appointments;
- customers can independently discover and book valid appointments;
- customers and salon staff see the same appointment truth;
- authorization boundaries prevent customers or staff from accessing capabilities they do not own.

## First-version proof

Delivery Phase 1 succeeds when one real salon could use the product for the complete **non-payment appointment loop** without depending on manual schedule duplication.

---

# 3. Users and Actors

## Customer

### Goal
Find a suitable service, specialist, and time, create a valid appointment, and retrieve their own appointments later.

### Capabilities

- browse public salon/service/specialist information;
- inspect valid bookable availability;
- identify themselves when booking requires ownership;
- create an appointment;
- view appointments belonging to their account;
- see the current status and details of those appointments.

### Boundary

A customer can access only appointments owned by their identity. A public booking reference or another person’s name/contact is not sufficient authorization.

---

## Reception staff

### Goal
Operate the salon’s daily appointment schedule.

### Capabilities

- sign in to the salon operations area;
- view the shared salon appointment calendar;
- inspect appointment details;
- create an appointment on behalf of a customer when needed;
- perform Phase-1 operational status changes that do not require manager authority.

### Boundary

Reception staff cannot change manager-only salon configuration or staff access.

---

## Manager

### Goal
Control what the salon offers, when specialists work, who may use salon operations, and the operational schedule.

### Capabilities

All reception capabilities plus:

- manage services;
- manage specialists;
- define service-to-specialist eligibility;
- manage specialist working schedules;
- manage salon staff access/roles required by Phase 1.

### Boundary

Manager authority applies only to this salon. No marketplace, branch-network, or external-provider administration exists.

---

## Specialist

### Goal
Be represented as an eligible service provider in customer discovery and scheduling.

### Phase 1 boundary

Specialists do **not** receive a dedicated login/dashboard in Delivery Phase 1. Their bookable services and schedules are managed by salon management.

---

# 4. Product Boundary

## In scope for the product roadmap

- public salon/service/specialist discovery;
- customer identity and appointment ownership;
- staff identity and role-based access;
- salon service catalog;
- specialist profiles and service eligibility;
- specialist work schedules;
- availability computation;
- online appointment creation;
- customer appointment retrieval;
- salon appointment calendar and operational appointment handling;
- later deposit/payment/refund flows;
- later cancellation/rescheduling policy enforcement and operational communication;
- later operational/growth improvements justified by use.

## Explicitly out of scope

- multi-salon marketplace;
- multi-branch salon network;
- independent-specialist marketplace;
- at-home/mobile beauty workforce;
- multi-service shopping cart;
- ecommerce;
- accounting/POS replacement;
- payroll;
- inventory management;
- general-purpose CRM;
- chat platform;
- loyalty wallet as a core requirement;
- specialist self-service dashboard in Delivery Phase 1.

## Adjacent product models excluded

The product must not silently evolve into a men’s barbershop, unisex salon, marketplace, branch-management product, or at-home service product without an explicit product-model change.

---

# 5. Core Product Behavior

## 5.1 Single salon, shared scheduling truth

There is exactly one salon context in the current product model.

Customer booking and salon operations must consume the same underlying service, specialist, schedule, availability, and appointment truth. A time shown as available to a customer cannot be treated as separately available by staff once it is validly booked, and vice versa.

---

## 5.2 Services and specialists

A manager can define services offered by the salon.

Each bookable service must have enough product information to support scheduling, including at minimum:

- name;
- public/bookable status;
- duration;
- price presentation appropriate for discovery;
- eligible specialists.

A specialist may support multiple services and a service may be supported by multiple specialists.

Only eligible specialists may be booked for a service.

Phase 1 does not require multi-service appointments.

Each appointment represents **one service with one specialist**.

---

## 5.3 Working schedules and availability

Managers define when specialists are available to work.

Bookable availability must account for:

- the selected service duration;
- the specialist’s working schedule;
- existing appointments;
- the requirement that the full appointment duration fits without overlap.

The product must not present a time as valid if the appointment cannot fit in the specialist’s available interval.

Availability is a shared capability used by both customer booking and salon appointment operations.

---

## 5.4 Public discovery

Visitors can browse the salon’s public offering without staff access.

Phase 1 public discovery should make it possible to understand:

- the salon identity/context;
- available services;
- service details;
- specialists;
- which services each specialist can perform;
- entry into the booking journey.

The public experience must not expose salon-management controls or private appointment information.

---

## 5.5 Customer booking

A customer can start from a service or other valid public booking entry point and create one appointment.

A Phase 1 booking must resolve:

1. service;
2. eligible specialist;
3. valid date/time;
4. customer identity/contact required for ownership;
5. appointment creation result.

Before appointment creation is accepted, the chosen specialist/time must still be valid against current availability.

If the slot is no longer valid, the product must reject the conflicting creation rather than create overlapping appointments.

Phase 1 has **no online deposit/payment requirement**. A successfully created valid booking becomes a confirmed Phase-1 appointment without passing through a payment gateway.

---

## 5.6 Customer appointment retrieval

An authenticated customer can retrieve appointments owned by their account.

The customer view must show enough information to identify the appointment, including:

- service;
- specialist;
- date/time;
- duration;
- current appointment status.

Phase 1 does not need to implement the full future financial cancellation/rescheduling policy.

If a basic customer cancellation is explicitly selected by the user during module planning, it must release the appointment’s availability and must not imply refund/payment behavior that does not yet exist.

Customer rescheduling may remain deferred to Delivery Phase 2. Selecting it for Phase 1 requires an explicit user product decision and must not introduce premature policy semantics.

---

## 5.7 Salon appointment operations

Authorized reception/manager users can view the salon’s shared appointment schedule.

Phase 1 staff operations must support:

- calendar/day schedule visibility;
- appointment detail;
- creating an appointment on behalf of a customer;
- changing operational appointment status where appropriate;
- cancelling an appointment when operationally necessary;
- reflecting changes in availability and customer-visible appointment state.

Staff-created appointments must use the same service/specialist/schedule constraints as customer-created appointments.

Staff must not be able to bypass specialist eligibility or create overlapping appointments through a separate path.

---

## 5.8 Appointment states

Phase 1 should use a small, coherent appointment lifecycle sufficient for non-payment scheduling.

At minimum the product must distinguish:

- confirmed/upcoming;
- cancelled;
- completed;
- no-show.

The user-visible appointment lifecycle must preserve these distinctions. Changes to that product lifecycle require an explicitly authorized product revision.

---

## 5.9 Identity and access

Customers and salon staff have different access contexts.

### Customer identity

The product should use a stable customer identity suitable for the Iranian market, centered on a mobile number/contact flow.

A customer account owns its appointments.

### Staff identity

Salon operations require authenticated staff identity and an assigned role.

Phase 1 staff roles:

- reception;
- manager.

A successfully authenticated person without an appropriate salon role must not gain salon-operations access.

### Authorization principle

Authentication proves who is acting; authorization determines which customer data or salon capabilities that identity may access.

---

# 6. Product Delivery Roadmap

| Product Delivery Phase | Objective | Main capabilities | Exit condition |
| --- | --- | --- | --- |
| **1 — Core Scheduling MVP** | Prove the complete non-payment scheduling loop for one operational salon. | Identity/access, catalog/specialists, schedules/availability, public discovery, booking lifecycle, customer appointment retrieval, salon appointment operations. | A configured salon can publish bookable services, customers can create valid appointments, and staff can operate the same persistent schedule with correct access boundaries. |
| **2 — Transactions & Reliability** | Make booking financially and operationally robust for deposit-based real-world use. | Deposits/payments, uncertain payment outcomes, refunds, cancellation/rescheduling policy, salon-proposed changes, communication/SMS delivery and recovery, stronger operational edge cases. | Payment and change/refund workflows can be used without ambiguous money or appointment state. |
| **3 — Operations & Growth** | Add higher-leverage operational and growth capabilities after core usage is proven. | Reporting, workflow improvements, customer retention/growth capabilities, and additional features supported by observed use. | Scope is defined from evidence and delivered without compromising the proven booking core. |

Later delivery phases remain intentionally high-level until they become active.

---

# 7. Delivery Phase Detailed in This Revision — Core Scheduling MVP

## Objective

Make the product usable by one salon for the complete non-payment appointment loop:

**configure offering and schedules → customer discovers → customer books valid time → customer retrieves booking → salon sees and operates the same appointment.**

## Phase 1 must prove

- one coherent source of service/specialist/schedule truth;
- correct availability for full appointment duration;
- conflict-safe appointment creation;
- customer appointment ownership;
- staff role boundaries;
- persistent shared appointment state between customer and salon operations;
- a usable public-to-booking-to-operations loop.

## Explicit Phase 1 deferrals

- online deposit/payment gateway;
- refund processing;
- payment reconciliation/unknown-result handling;
- advanced financial cancellation/rescheduling policy;
- salon replacement/refund policy;
- full operational SMS notification system;
- loyalty/wallet/packages;
- CRM/accounting/POS/inventory/payroll;
- advanced reporting and growth automation;
- marketplace/branch/home-service behavior.

## Exit condition

Delivery Phase 1 is complete when a configured salon can operate a coherent end-to-end schedule with real customer/staff access boundaries, valid availability, persistent appointments, and consistent customer/reception views without relying on online payment or future-phase integrations.

---

# 8. Module Map — Delivery Phase 1

| ID | Module | Purpose | Product Dependencies |
| --- | --- | --- | --- |
| **M01** | Identity & Access | Establish customer identity, staff identity, sessions, and role/ownership boundaries. | none |
| **M02** | Salon Catalog & Specialists | Define the salon’s services, specialists, eligibility, and publishable offering. | M01 |
| **M03** | Scheduling & Availability | Define specialist schedules and compute valid shared availability. | M02 |
| **M04** | Public Discovery | Present salon/services/specialists publicly and provide booking entry points. | M02 |
| **M05** | Booking Lifecycle | Create conflict-safe appointments from valid service/specialist/time selections. | M01, M02, M03 |
| **M06** | Customer Appointments | Let customers retrieve and understand appointments they own. | M01, M05 |
| **M07** | Salon Appointment Operations | Let authorized staff view and operate the shared appointment schedule. | M01, M03, M05 |

Module dependencies express product sequencing. Live readiness, engineering stage, and completion are maintained in the project tracker; this map records the approved product scope.

---

# 9. Module Briefs

## M01 — Identity & Access

### Purpose
Establish trustworthy actor identity and access boundaries for customers, reception staff, and managers.

### Actors
Customer, reception staff, manager.

### Owns

- customer sign-in identity;
- staff sign-in identity;
- authenticated session context;
- customer appointment ownership boundary;
- salon role assignment/use required by Phase 1;
- authorization distinction between reception and manager.

### Important product rules

- customer identity is centered on a stable mobile/contact identity appropriate to the target market;
- an authenticated customer can access only their own private appointment data;
- a staff user needs an assigned salon role to access salon operations;
- reception does not inherit manager-only configuration authority;
- a public identifier/reference must not grant private access by itself.

### Does not own

- booking rules;
- schedules/availability;
- service configuration;
- payment;
- operational notification delivery system.

### Interactions
Provides actor identity and authorization context to M02, M05, M06, and M07.

### Acceptance outcome
A customer and authorized staff member can be identified in distinct contexts, unauthorized users cannot access private customer/salon surfaces, and reception/manager permissions can be distinguished without requiring booking logic.

---

## M02 — Salon Catalog & Specialists

### Purpose
Define what the salon offers and who is eligible to perform each service.

### Actors
Manager; public/customer as consumers of published data.

### Owns

- services;
- public/bookable state;
- service duration;
- price presentation needed for Phase 1 discovery;
- specialists;
- specialist public information;
- service-to-specialist eligibility.

### Important product rules

- only published/bookable services appear as bookable;
- one appointment contains one service;
- only eligible specialists may perform a service;
- specialists may support multiple services;
- managers own configuration changes.

### Does not own

- specialist working hours;
- availability computation;
- appointment creation;
- customer authentication;
- online payment.

### Dependencies/interactions
Depends on M01 for manager access. Supplies catalog and eligibility data to M03, M04, M05, and M07.

### Acceptance outcome
A manager can configure a coherent salon offering that can be safely consumed by discovery and scheduling modules without those modules inventing service/specialist eligibility.

---

## M03 — Scheduling & Availability

### Purpose
Own specialist working schedules and determine which appointment times are actually valid.

### Actors
Manager; customer/reception as consumers of availability.

### Owns

- specialist working intervals;
- schedule exceptions required for Phase 1;
- full-duration slot validation;
- overlap prevention inputs;
- availability queries used by customer and staff flows.

### Important product rules

- service duration must fully fit the specialist schedule;
- existing appointments block overlapping availability;
- ineligible specialists never produce valid availability for a service;
- customer and salon operations use the same scheduling truth;
- availability is not an independent copy maintained by each surface.

### Does not own

- service definitions;
- appointment ownership;
- appointment lifecycle mutation beyond supplying/validating scheduling constraints;
- payments.

### Dependencies/interactions
Depends on M02 for service duration and eligibility. Supplies availability validation to M05 and M07.

### Acceptance outcome
For the same inputs, customer booking and salon operations receive consistent valid availability, and invalid overlaps/full-duration violations are rejected.

---

## M04 — Public Discovery

### Purpose
Help visitors understand the salon offering and enter booking with useful context.

### Actors
Public visitor/customer.

### Owns

- public salon presentation;
- service listing/detail;
- specialist listing/detail;
- visible service-specialist relationships;
- booking entry points.

### Important product rules

- only public/published catalog data is exposed;
- public surfaces do not expose private appointments or management controls;
- booking entry can carry selected service/specialist context forward;
- the experience remains specific to one salon, not a marketplace.

### Does not own

- service/specialist configuration;
- identity internals;
- appointment creation;
- schedule management.

### Dependencies/interactions
Consumes M02. May use read-only availability hints from M03 if useful, but appointment creation remains M05 responsibility.

### Acceptance outcome
A visitor can understand the salon’s bookable offering and reach the correct booking journey with service/specialist context intact.

---

## M05 — Booking Lifecycle

### Purpose
Turn a valid customer or staff booking intent into one persistent, conflict-safe appointment.

### Actors
Customer; reception/manager for staff-created booking entry.

### Owns

- booking selection state needed for appointment creation;
- final service/specialist/time validation;
- appointment creation;
- initial appointment status;
- conflict-safe creation result;
- booking success/failure outcome.

### Important product rules

- exactly one service and one eligible specialist per appointment;
- selected time must remain valid at creation time;
- full service duration must fit;
- overlapping appointments must not be created;
- Phase 1 successful booking becomes confirmed without online payment;
- customer-created appointments belong to the authenticated customer;
- staff-created appointments must obey the same eligibility and availability constraints.

### Does not own

- payment/deposit/refund;
- future financial cancellation policy;
- catalog configuration;
- specialist schedule configuration;
- long-term customer account UI;
- staff calendar UI.

### Dependencies/interactions
Depends on M01 identity/ownership, M02 catalog/eligibility, and M03 availability. Produces appointments consumed by M06 and M07.

### Acceptance outcome
A valid booking creates exactly one persistent confirmed appointment; a stale/conflicting booking does not create an overlapping appointment and returns a recoverable failure outcome.

---

## M06 — Customer Appointments

### Purpose
Give customers an authoritative private view of appointments they own.

### Actors
Customer.

### Owns

- customer appointment list;
- appointment detail;
- visible appointment status;
- Phase-1-safe customer actions if included without introducing future financial policy.

### Important product rules

- only the owning customer can access an appointment through the customer area;
- customer presentation reflects the same appointment state operated by salon staff;
- cancelled/completed/no-show records remain distinguishable;
- Phase 1 must not imply payment/refund state that does not exist yet.

### Does not own

- authentication implementation;
- appointment creation rules;
- staff operations;
- payment/refund UI;
- advanced rescheduling policy.

### Dependencies/interactions
Depends on M01 and M05. Reads operational state changed through M07.

### Acceptance outcome
A customer can sign in and reliably retrieve only their own appointments with current details/status consistent with salon operations.

---

## M07 — Salon Appointment Operations

### Purpose
Allow authorized salon staff to operate the shared appointment schedule.

### Actors
Reception staff and manager.

### Owns

- calendar/day schedule presentation;
- appointment detail for authorized staff;
- staff-created appointment entry;
- Phase-1 operational status updates;
- operational cancellation;
- shared schedule refresh after mutations.

### Important product rules

- staff-created appointments use the same availability and eligibility rules as customer bookings;
- staff cannot create overlaps by bypassing customer-facing validation;
- reception and manager can view the operational schedule;
- manager-only product configuration remains outside reception permissions;
- staff changes are reflected in customer appointment state where relevant.

### Does not own

- catalog configuration;
- schedule configuration itself;
- payment/refund/reconciliation;
- advanced CRM or reminder workflows.

### Dependencies/interactions
Depends on M01 for staff roles, M03 for availability, and M05 for appointment creation/lifecycle. Shares appointment truth with M06.

### Acceptance outcome
Authorized staff can operate the daily schedule, create valid appointments, inspect appointments, and apply allowed status/cancellation changes without creating a separate scheduling truth.

---

# 10. Cross-Module Invariants

These rules must remain true across module boundaries.

## Identity and ownership

- customer and staff identity contexts are distinct;
- private customer data is scoped to the owning customer;
- salon operations require an authorized staff role;
- reception cannot silently gain manager authority.

## Appointment integrity

- one appointment = one service + one eligible specialist + one scheduled interval;
- the full interval must fit valid specialist availability;
- overlapping appointments are not valid;
- customer and staff booking use the same appointment/availability truth.

## State consistency

- customer and salon surfaces show the same authoritative appointment state;
- cancellation releases the appointment interval for future availability;
- completed and no-show are operationally distinct from cancelled.

## Product model

- exactly one salon context;
- no marketplace/branch/home-service assumptions may enter module design accidentally.

## Financial boundary

- Phase 1 has no authoritative online-payment/refund state;
- modules must not invent deposit/refund semantics before Delivery Phase 2.

## Localization

- customer-facing and salon-facing product UI is Persian/RTL;
- dates/times/phone presentation must be appropriate for Iranian users.

---

# 11. UX / Surface Summary — Delivery Phase 1

This is a responsibility map, not a finished visual specification.

## Public/customer surfaces

- Home / salon overview
- Services list
- Service detail
- Specialists list
- Specialist detail
- Booking flow
- Customer sign-in/authentication surface
- My appointments
- Customer appointment detail

## Salon surfaces

- Staff sign-in
- Shared appointment calendar / day schedule
- Staff appointment detail
- New appointment flow
- Services management
- Specialists management
- Specialist schedule management
- Staff access management required for Phase 1

The surfaces must preserve the journeys, information, actions, and access boundaries defined above.

---

# 12. Open Questions and Assumptions

## Product questions blocking engineering

None currently block **M01 — Identity & Access**.

If later module interviews reveal a true product contradiction, escalate it before silently changing this PRD.

## Assumptions to validate through use

- customers will find self-service availability/booking materially easier than message/call coordination;
- reception benefits from customer and staff bookings sharing one calendar truth;
- the seven Phase 1 module boundaries are sufficiently independent for incremental engineering;
- deposit/payment integration can be deferred without preventing validation of the core scheduling product.

---

# 13. Product Handoff

## Initial engineering candidate

**M01 — Identity & Access** is the initial candidate because the remaining private customer and staff capabilities depend on trustworthy identity, ownership, and permissions. It has no upstream product module dependency.

## Product context to preserve

- customer-owned appointments and staff operations have distinct access boundaries;
- salon staff require an assigned role;
- Phase 1 roles are reception and manager;
- reception has no manager-only authority;
- the product serves Persian-speaking mobile users in Iran, with customer identity centered on mobile/contact;
- booking rules remain owned by the booking modules.

## Relevant PRD sections

- Section 3 — Users and Actors
- Section 5.9 — Identity and Access
- Section 8 — Module Map
- Section 9 — M01 Module Brief
- Section 10 — Cross-Module Invariants

This handoff records the product starting point. Read the current project tracker and module artifacts to resume engineering; do not treat this section as a live engineering backlog or reopen settled technical decisions from it.

---

# Product Revision Policy

This final baseline is read-only for agents during engineering, implementation, review, acceptance, and visual redesign. Permission to perform those activities or update documentation does not authorize editing the PRD.

If work reveals a genuine product contradiction, describe the proposed product change outside this document, identify affected behavior and modules, and obtain explicit user authorization for that revision. Continue independent work without implementing the conflicting behavior.

For an authorized revision, record its product reason and approval evidence, increment the product revision, and synchronize reference copies to the new canonical commit. Expanding a later delivery phase into detailed modules also requires an authorized product revision. Technical decisions and progress never justify a PRD edit on their own.

Revision 1.0 applies the product-only structure and read-only policy to the existing product definition. The product model, three delivery phases, seven Phase 1 modules, existing optional/deferred capabilities, and acceptance outcomes are preserved.

---

# Phase 1 Product Principle

> **First make scheduling correct and operational. Add money and advanced workflow complexity only after the shared booking core is proven.**
