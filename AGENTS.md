# Agent instructions

Read [MASTER.md](MASTER.md), the relevant phase guide, and the project tracker before project work.

## Approved PRDs are read-only

- An approved PRD is the product baseline. Never edit it during engineering, implementation, review, acceptance, or visual redesign, including to update progress or record technical decisions.
- Only an explicit user instruction authorizing a specific product revision permits changing an approved PRD. Permission to implement a module, resolve architecture, update documentation, or fix a bug is not permission to revise product scope.
- If a real product contradiction appears, record a proposed change outside the PRD, explain the affected behavior, and request that specific product decision. Continue independent work; do not silently implement the conflicting behavior.
- Frameworks, databases, schemas, APIs, providers, sessions, deployment, and test strategies belong in the implementation repository's module specs and appropriate ADRs. Domain vocabulary belongs in its glossary. Progress and evidence links belong in the tracker.
- A PRD's historical engineering handoff is not a live list of unresolved technical questions. Never update it just because engineering has settled those questions.
- Start new PRDs from [templates/prd.md](templates/prd.md). Do not migrate approved PRDs merely to match a new template.
- Implementation-repository copies are read-only references to a pinned approved PRD revision, never independent product authorities. Include this rule in the implementation repository's agent instructions when setting it up.

## Pre-implementation skill gate

- Before the engineering agent writes application code, inspect the stack and architecture decisions already settled for the current module/ticket and ensure the relevant repository-level skills are installed, reviewed, and available.
- Skill installation follows confirmed architecture decisions; skills must never create, force, or silently change architecture decisions, framework/library choices, or version requirements.
- If a skill has prerequisites that conflict with the settled architecture or would introduce a new unresolved choice, do not change the product or architecture merely to satisfy the skill. Keep that skill inactive until the relevant engineering decision is actually made.
- If implementation genuinely requires a new major framework, library, provider, persistence layer, test tool, or other technology that has not been decided yet, stop before adopting it, resolve that decision through the existing module engineering process, then install/review the matching skill before implementation continues.
- Do not add planning ceremony merely because a skill or tool exists. A separate `grill-with-docs` pass is not required for every ticket; use it only when a real material ambiguity needs user-level engineering/architecture resolution.
- Global documentation/research skills may supplement repository-pinned skills but do not replace this repository-level gate.
- Review third-party skill instructions before trusting them and keep their repository lock/pin metadata current when the skill system supports it.

These are agent/workflow rules, not a filesystem or GitHub permission lock.
