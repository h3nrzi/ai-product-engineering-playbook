# Phase Guides

This directory contains the deliberately designed phase guides for the workflow.

The master prompt defines the Guide LLM's role. These documents define the procedure for each approved phase.

## Current authoritative phases

1. [`01-product-discovery-prototype.md`](01-product-discovery-prototype.md)
2. [`02-frontend-product-definition.md`](02-frontend-product-definition.md)
3. [`03-frontend-specification.md`](03-frontend-specification.md)
4. [`04-frontend-engineering.md`](04-frontend-engineering.md)

**Phase 04 / Frontend Accepted is the current official boundary of the playbook.**

The immediate objective is to bring multiple real projects through these four phases. Reaching this boundary is intentionally considered a major successful project milestone; a project may remain parked there while other projects move through the same workflow.

## Just-in-time phase design

> **A future phase should be designed when a real project reaches its boundary and is ready to enter it, rather than specifying the entire lifecycle upfront.**

Backend definition, backend specification/engineering, full-stack integration, production hardening, and any other later phases may eventually be added, but they are **not currently designed or authoritative**.

An LLM must not:

- assume a missing future phase is already defined
- fabricate its procedure from general software-engineering knowledge
- automatically push a Phase 04-complete project into backend work
- create placeholder phase guides merely to make the lifecycle look complete

When the user explicitly chooses a real Phase 04-complete project to continue, the Guide should help deliberately design the next phase using that project's actual frontend handoff and lessons from the projects already completed through Phase 04. The new phase becomes part of the SSOT only after the user approves it.

## Rule

Do not fill phase guides with guessed process details. Each phase guide is created, reviewed, and approved deliberately before it becomes part of the playbook.

When a project is active in a phase, its project tracker links to the governing phase document.

When a project completes Phase 04, `Frontend Accepted` is a valid stopping state. The tracker may remain at that milestone until the user explicitly decides to continue the project beyond the current playbook boundary.
