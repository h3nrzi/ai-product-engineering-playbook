# AI Product Engineering Playbook

Single source of truth for a reusable AI-assisted product-engineering workflow.

This repository is designed so a guide LLM can quickly understand:

- what role it should play,
- where a project currently is in the workflow,
- which phase guide governs the next work,
- what tools/agents are responsible for execution,
- how project progress is tracked across phases.

## Read order for any guide LLM

1. Read [`MASTER.md`](MASTER.md).
2. Read the relevant project tracker under [`projects/`](projects/README.md).
3. Read the phase document linked by that tracker.
4. Help the user reason, review, prompt, and decide. Do not take over implementation work unless explicitly asked for a small illustrative example.

## Workflow

1. Product Discovery & Rapid Prototype
2. Frontend Product Definition
3. Frontend Specification & Decomposition
4. Frontend Engineering
5. Frontend Acceptance & Backend Handoff
6. Backend Product & Architecture Definition
7. Backend Specification & Decomposition
8. Backend Engineering
9. Full-Stack Integration & Verification
10. Production Hardening & Readiness

Detailed phase documents will live under [`phases/`](phases/README.md) and will be created/reviewed one at a time.

## Project tracking

Each real project gets a tracker under [`projects/`](projects/README.md). The tracker records:

- product repository,
- current workflow phase,
- status of every phase,
- current activity,
- important artifacts,
- next action,
- blockers/notes.

Use [`templates/project-tracker.md`](templates/project-tracker.md) when onboarding a new project.

## Current projects

- [`The Gentleman`](projects/the-gentleman.md)
