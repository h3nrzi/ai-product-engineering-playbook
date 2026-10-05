# Project Tracker — <Project Name>

> Operational control panel for this project. Keep this file current, concise, and navigational. Product behavior belongs in the PRD; architecture belongs in module engineering artifacts.

## 1. Project Snapshot

| Field | Value |
| --- | --- |
| Product family | <service name + link to ../opportunities/service-products.md> |
| Selected model / variant | <specific model> |
| Target market / geography | <if relevant> |
| Current playbook phase | <01–03> |
| Current product delivery phase | <phase number + name / not defined> |
| Current module | <module / none> |
| Overall status | <not started / active / blocked / complete> |
| PRD | <projects/<project-slug>/prd.md / pending> |
| Implementation repository | <URL / pending> |
| Documentation root | <projects/<project-slug>/> |

### Product boundary

- **Selected:** <what this product/model is>
- **Explicitly not:** <adjacent variants excluded from this project>

A deliberate model change requires explicit user authorization for a product revision before the approved PRD can be edited. Record live progress here, never in the PRD.

---

## 2. Playbook Progress

| Playbook Phase | Status | Exit Result |
| --- | --- | --- |
| 01 — Product Discovery & Delivery Plan | <status> | Authoritative phased PRD + active-phase module map |
| 02 — Module-by-Module Engineering | <status> | Reviewed working modules / completed product delivery phases |
| 03 — Visual Redesign & UI Polish | <status> | Final visual redesign/polish when needed |

Use only these phase statuses: `not started`, `active`, `blocked`, `complete`, `skipped`.

---

## 3. Product Delivery Roadmap

Summarize the product-specific delivery phases defined by the PRD. Keep future phases high-level until they become active.

| Delivery Phase | Status | Outcome | Scope Summary |
| --- | --- | --- | --- |
| 1 — <name> | <planned/active/complete> | <what becomes usable> | <short scope> |
| 2 — <name> | <planned/active/complete> | <what becomes usable> | <short scope> |

Add or remove rows as the product requires.

### Active delivery phase

- **Phase:** <number + name>
- **Objective:** <one sentence>
- **Exit condition:** <observable condition that completes this phase>

---

## 4. Module Board

Track detailed modules only for the active Product Delivery Phase.

| ID | Module | Status | Depends On | Engineering Stage | Primary Artifact |
| --- | --- | --- | --- | --- | --- |
| M01 | <name> | <planned/ready/active/blocked/complete> | <IDs / none> | <grill / spec / tickets / implement / review / accepted / —> | <link/path / —> |

### Status rules

- `planned` — belongs to the active delivery phase but is not ready yet.
- `ready` — product boundary is clear enough to enter Phase 02.
- `active` — currently being engineered.
- `blocked` — cannot continue until a named dependency/decision is resolved.
- `complete` — implementation and acceptance are complete.

Only one module should normally be `active` unless parallel work is intentional.

---

## 5. Current Focus

- **Current module:** <module / none>
- **Current activity:** <product discussion / delivery planning / grill-with-docs / to-spec / to-tickets / implement / code-review / acceptance / Stitch redesign / etc.>
- **Immediate objective:** <what this activity must accomplish>
- **Working artifact:** <link/path / none>

### Open decisions

Track only decisions that genuinely block or materially change current work.

| Decision | Owner | Needed For | Status |
| --- | --- | --- | --- |
| <decision> | <user / engineering / design> | <phase/module> | <open / resolved> |

Remove resolved decisions once their outcome is persisted in the authoritative artifact.

---

## 6. Risks & Blockers

| Type | Item | Impact | Resolution / Next Check |
| --- | --- | --- | --- |
| <blocker/risk> | <item> | <what it prevents or threatens> | <action / none> |

If there are none, write `None` rather than keeping empty placeholder rows.

---

## 7. Authority & Artifacts

| Artifact | Role | Location |
| --- | --- | --- |
| PRD | Read-only approved product baseline | <canonical path + approved commit / pending> |
| Active module artifact | Current engineering authority | <spec/tickets/decision doc / pending> |
| Implementation repository | Source code and engineering evidence | <URL / pending> |
| Visual redesign artifact | UI authority when Phase 03 is used | <DESIGN.md / Stitch output / pending> |

Do not duplicate PRD/spec contents in the tracker. Link to them.

---

## 8. Next Action

> **<Exactly one concrete next action.>**

The next action should be executable without rediscovering project context.

---

## 9. Session Handoff

Use this section as the minimum context needed to resume work in a later session.

- **Where we are:** <phase / delivery phase / module>
- **What is settled:** <only the few decisions needed to avoid reopening work>
- **What is happening now:** <current activity>
- **What happens next:** <same action as above>

### Guide entrypoint

Read in this order:

1. [`MASTER.md`](../MASTER.md)
2. this tracker
3. the active playbook phase guide
4. the PRD
5. the active module artifact / latest engineering output, if applicable

Continue from the current decision/module. Do not restart discovery or reopen settled decisions without a real contradiction.