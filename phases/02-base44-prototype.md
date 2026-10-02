# Phase 02 — Base44 Prototype

## Goal

Use the approved Phase 01 PRD and prompt package to produce a strong, inspectable React prototype in Base44.

Base44 is an implementation/prototyping tool here, not the product designer. Phase 01 defines what should exist; Phase 02 turns it into a tangible product experience.

## Workflow

```text
PRD + Base44 prompts
→ generate initial prototype
→ inspect core journeys/pages
→ identify meaningful gaps
→ targeted Base44 refinement prompts
→ repeat only as needed
→ export/sync usable React project
→ prototype handoff
```

## Guide LLM role

Help the user:

- choose which prepared prompt to send
- evaluate Base44 output against the PRD
- identify missing/broken journeys and important UI problems
- write concise refinement prompts
- avoid wasting iterations on low-value polish
- prevent Base44 from expanding product scope
- decide when the prototype is good enough to engineer outside Base44

Do not rewrite the application yourself.

## Prototype expectations

The prototype should demonstrate the important routes, journeys, responsive layout, product vocabulary, content direction, and meaningful UI states needed to understand the product.

Real production backend behavior is not required. Realistic dummy/mock data and simulated flows are acceptable when clearly understood as prototype behavior.

The objective is **not production code quality**. The objective is a strong React product baseline that Phase 03 can systematically complete and engineer.

## Exit criteria

Leave Base44 when the product is visually and behaviorally representative enough that further progress is better achieved in the real repository with engineering agents.

Produce a concise prototype handoff: what works, known gaps, important prototype assumptions, and the repository/export to continue from.

Then proceed to **Phase 03 — React Frontend Completion**.
