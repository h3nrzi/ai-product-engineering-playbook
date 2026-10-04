# Women’s Beauty Salon Booking

Project workspace for the current three-phase playbook.

## Current state

- Playbook phase: **02 — Module-by-Module Engineering**
- Product family: **Barbershop / Beauty Salon Booking**
- Selected model: **Women’s single-salon**
- Product Delivery Phase: **1 — Core Scheduling MVP**
- Current module: **M01 — Identity & Access**
- PRD: [`prd.md`](prd.md)
- Implementation repository: not linked yet

## Authority

[`prd.md`](prd.md) is the product authority.

It contains:

- product purpose and boundaries;
- users/actors;
- core behavior;
- three Product Delivery Phases;
- the complete Delivery Phase 1 module map;
- module briefs and acceptance outcomes;
- cross-module invariants;
- the Phase 02 handoff for M01.

Technical architecture is not defined here. It is decided module by module during Phase 02.

## Current engineering handoff

The first ready module is:

**M01 — Identity & Access**

Next:

1. create or link the implementation repository;
2. inspect its starting state;
3. run M01 through the Phase 02 engineering interview (`grill-with-docs`);
4. decide whether M01 needs a durable spec/tickets or can move directly to implementation;
5. implement and review before advancing the module board.

## Durable project files

```text
projects/womens-beauty-salon-booking/
├── README.md
└── prd.md
```

Keep this documentation root intentionally small. Add another artifact only when it has durable value beyond the PRD and engineering repository.
