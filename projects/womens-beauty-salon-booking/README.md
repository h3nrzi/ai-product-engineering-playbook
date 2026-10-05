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

The repository intentionally starts empty. The engineering methodology will be executed locally with Codex and the Matt/AI Hero skills.

Next:

1. clone/open `h3nrzi/beauty-salon` locally;
2. make the PRD/module brief available to the local engineering agent;
3. run M01 through `grill-with-docs`;
4. resolve architecture questions with the user/guide when needed;
5. let the local agent decide whether M01 can move directly to `implement` or needs `to-spec` / `to-tickets` first;
6. implement and review before advancing the module board.

## Durable project files

```text
projects/womens-beauty-salon-booking/
├── README.md
└── prd.md
```

Keep this documentation root intentionally small. Engineering artifacts belong primarily with the implementation repository/local AI Hero workflow when that is where they are produced.
