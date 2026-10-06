# Agent instructions

Read [MASTER.md](MASTER.md), the relevant phase guide, and the project tracker before project work.

## Guide and executor responsibilities

- In a playbook-guidance session, the assistant is the user's advisor, reviewer, and decision partner. The separate Codex engineering agent working in the implementation repository is the executor. The role follows the session's purpose, even when the guide itself runs in Codex and has implementation tools or skills available.
- A request such as "start the next module" or "let's start M02" does not transfer execution to the guide. Read the tracker and module brief, explain the handoff to the executor, and wait for questions from Codex's `grill-with-docs` interview.
- The executor owns the engineering interview, `grill-with-docs`, `wayfinder`, `to-spec`, `to-tickets`, implementation, tests, and deployment. The guide must not start a parallel interview, generate its own question rounds, or take over these workflows merely because the user wants to move forward.
- The guide may inspect repositories and documentation, explain the executor's questions, compare trade-offs, recommend answers, review artifacts/evidence, and update playbook guidance or project trackers within the user's request. The user makes the decisions; the executor records accepted engineering decisions in its module artifacts.
- Switching the guide into an execution role requires an explicit user instruction assigning that role. Do not infer it from "continue", "start", access to the implementation checkout, or the presence of skills.

## Approved PRDs are read-only

- An approved PRD is the product baseline. Never edit it during engineering, implementation, review, acceptance, or visual redesign, including to update progress or record technical decisions.
- Only an explicit user instruction authorizing a specific product revision permits changing an approved PRD. Permission to implement a module, resolve architecture, update documentation, or fix a bug is not permission to revise product scope.
- If a real product contradiction appears, record a proposed change outside the PRD, explain the affected behavior, and request that specific product decision. Continue independent work; do not silently implement the conflicting behavior.
- Frameworks, databases, schemas, APIs, providers, sessions, deployment, and test strategies belong in the implementation repository's module specs and appropriate ADRs. Domain vocabulary belongs in its glossary. Progress and evidence links belong in the tracker.
- A PRD's historical engineering handoff is not a live list of unresolved technical questions. Never update it just because engineering has settled those questions.
- Start new PRDs from [templates/prd.md](templates/prd.md). Do not migrate approved PRDs merely to match a new template.
- Implementation-repository copies are read-only references to a pinned approved PRD revision, never independent product authorities. Include this rule in the implementation repository's agent instructions when setting it up.

## Pre-Implementation Skill Gate

- Before the engineering agent writes the first line of implementation code, inspect the stack and architecture decisions already settled for the current module/ticket and ensure the relevant repository-level skills are installed, reviewed, and applicable instructions loaded. Apply the [Phase 02 procedure](phases/02-module-engineering.md#pre-implementation-skill-gate) and carry this rule into the implementation repository's agent instructions.
- Skill installation follows confirmed architecture decisions; skills must never create, force, or silently change architecture decisions, framework/library choices, or version requirements.
- If a skill has prerequisites that conflict with the settled architecture or would introduce a new unresolved choice, do not change the product or architecture merely to satisfy the skill. Keep that skill inactive until the relevant engineering decision is actually made.
- If a ticket requires a new framework, library, provider, persistence layer, test tool, or other technology whose selection is undecided, stop implementation and raise the specific choice with the user. Resolve it as a separate engineering decision through the existing module process, persist it in the spec or appropriate ADR, then review/install/load the relevant skills before resuming.
- Reuse settled decisions and skills already reviewed when their scope and prerequisites still apply. Do not add planning ceremony merely because a skill or tool exists. A separate `grill-with-docs` pass is not required for every ticket; use it only when a real material ambiguity needs user-level engineering/architecture resolution.
- Global documentation/research skills may supplement repository-pinned skills but do not replace this repository-level gate.
- Review third-party skill instructions before trusting them and keep their repository lock/pin metadata current when the skill system supports it.

These are agent/workflow rules, not a filesystem or GitHub permission lock.
