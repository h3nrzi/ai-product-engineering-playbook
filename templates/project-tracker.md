# Project Tracker — <Project Name>

## Project

- Product family: <service name + link to ../opportunities/service-products.md>
- Selected model / variant: <specific model>
- Target market / geography: <if relevant>
- Documentation root: <projects/<project-slug>/>
- PRD: <projects/<project-slug>/prd.md>
- Implementation repository: <URL / pending>
- Current playbook phase: <01–03>
- Current status: <not started / in progress / complete / blocked>

## Product boundary

- Selected: <what product/model this is>
- Explicitly not: <adjacent variants excluded from this project>

## Playbook workflow

| Phase | Status | Main result |
| --- | --- | --- |
| 01 — Product Discovery & Delivery Plan |  | Authoritative phased PRD + active-phase module map |
| 02 — Module-by-Module Engineering |  | Reviewed working modules / completed product delivery phases |
| 03 — Visual Redesign & UI Polish |  | Final polished UI when redesign is needed |

## Product Delivery Roadmap

Summarize the product-specific delivery phases from the PRD.

| Product Delivery Phase | Status | Goal |
| --- | --- | --- |
| 1 — <name> | <planned/in progress/complete> | <goal> |
| 2 — <name> | <planned/in progress/complete> | <goal> |

Add/remove rows as the product requires.

## Active Product Delivery Phase

- Phase: <number + name>
- Goal: <short goal>
- Status: <planned / in progress / complete>

## Modules

Track only the detailed modules for the active product delivery phase.

| Module | Status | Depends on | Current engineering artifact |
| --- | --- | --- | --- |
| <M01 — name> | <planned/ready/in progress/complete/blocked> | <module/none> | <spec/tickets/evidence or —> |

## Current module / activity

- Current module: <module or none>
- Current activity: <grill-with-docs / to-spec / to-tickets / implement / code-review / acceptance / UI redesign / etc.>
- Relevant artifact: <link/path>

## Next action

<One clear next action.>

## Blockers / notes

<Only meaningful blockers, migration notes, or continuation context. Do not duplicate PRD/spec contents.>

## Guide entrypoint

Read:

1. [`MASTER.md`](../MASTER.md)
2. this tracker
3. the active phase guide
4. the PRD
5. the current module's engineering artifacts / implementation output

Continue from the current module/decision without restarting product discovery.
