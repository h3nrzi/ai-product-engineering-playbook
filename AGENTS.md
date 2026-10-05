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

These are agent/workflow rules, not a filesystem or GitHub permission lock.
