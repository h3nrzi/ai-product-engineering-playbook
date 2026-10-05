# Women’s Beauty Salon Booking

Project workspace for the current three-phase playbook.

## Current state

- Playbook phase: **02 — Module-by-Module Engineering**
- Product family: **Barbershop / Beauty Salon Booking**
- Selected model: **Women’s single-salon**
- Product Delivery Phase: **1 — Core Scheduling MVP**
- Current module: **M01 — Identity & Access**
- PRD: [`prd.md`](prd.md)
- Implementation repository: https://github.com/h3nrzi/beauty-salon

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

Implementation repository:

`https://github.com/h3nrzi/beauty-salon`

The engineering interview and M01 specification are published in implementation commit `d074f8a21649cb50c6bd9fa2084e484cb1862919`.

Next: run `to-tickets` on the [M01 spec](https://github.com/h3nrzi/beauty-salon/blob/d074f8a21649cb50c6bd9fa2084e484cb1862919/.scratch/m01-identity-access/spec.md), review the vertical slices and dependencies, then implement and review. M01 is not yet accepted; live SMS verification remains required.

The approved PRD is read-only during this work. Its original handoff describes the starting context, not current engineering status. See [the tracker](../womens-beauty-salon-booking.md) for current progress and [agent rules](../../AGENTS.md) for product revisions.

## Durable project files

```text
projects/womens-beauty-salon-booking/
├── README.md
└── prd.md
```

Keep this documentation root intentionally small. Engineering artifacts belong primarily with the implementation repository/local AI Hero workflow when that is where they are produced.
