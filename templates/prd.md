# PRD — <Product Name>

> Product definition only. This document specifies observable behavior and business constraints, not architecture or implementation. After explicit user approval it becomes a read-only product baseline. Engineering progress belongs in the project tracker; technical decisions belong in module specs and ADRs.

## Document control

- **Product revision:** <revision>
- **Approval:** <draft / approved; never infer approval>
- **Approval evidence:** <user approval reference and date / pending>
- **Product family:** <family>
- **Selected model / variant:** <specific model>
- **Target market:** <audience and geography>
- **Delivery phase detailed in this revision:** <number and name>

The approved Git commit identifies this baseline. A copy in another repository must cite the canonical source and commit. Live delivery/module status is maintained outside this document.

## 1. Product identity

<Describe the product and selected model in one paragraph. State adjacent models that must not be assumed.>

## 2. Problem and desired outcome

- **Problem and affected users:** <concrete need>
- **Current friction:** <what fails today>
- **Desired outcome:** <observable improvement>
- **First usable version proves:** <product result>

## 3. Users and actors

| Actor | Goal | Allowed capabilities | Access / ownership boundary |
| --- | --- | --- | --- |
| <actor> | <goal> | <capabilities> | <boundary> |

## 4. Product boundary

- **In scope:** <capabilities>
- **Out of scope:** <exclusions>
- **Excluded adjacent models:** <variants>

## 5. Core product behavior

Repeat for each important journey:

### <Journey name>

- **Actor and trigger:** <who needs what, when>
- **Preconditions:** <business conditions>
- **Expected behavior and outcome:** <observable journey>
- **Business rules:** <rules to preserve>
- **Failure / edge cases:** <what the user may do and what remains true>

Describe required rights and outcomes; do not prescribe providers, schemas, endpoints, algorithms, or frameworks.

## 6. Product delivery roadmap

| Delivery phase | Objective / value | Included capabilities | Deferred capabilities | Exit condition |
| --- | --- | --- | --- | --- |
| <number — name> | <value> | <scope> | <deferrals> | <observable result> |

Use as many phases as the product needs. Future phases remain high-level.

## 7. Delivery phase detailed in this revision

- **Phase:** <number — name>
- **Objective:** <product outcome>
- **Must prove:** <required behaviors>
- **Deferrals:** <explicit exclusions>
- **Exit condition:** <observable acceptance>

This is the approved planning scope, not a live execution status.

## 8. Module map for this delivery phase

| ID | Module | Product responsibility | Product dependencies |
| --- | --- | --- | --- |
| <M01> | <name> | <responsibility> | <IDs / none> |

Derive modules from this product. Dependencies express product sequencing, not required code layers. Track readiness and completion in the tracker.

## 9. Module briefs

Repeat for each module:

### <ID — Name>

- **Purpose:** <product responsibility>
- **Actors:** <users>
- **Owns:** <capabilities>
- **Product rules:** <behavior and rights>
- **Does not own:** <boundaries>
- **Dependencies / interactions:** <other product responsibilities>
- **Acceptance outcome:** <observable result, independent of implementation technique>

## 10. Cross-module product invariants

<Only applicable rules: ownership, permissions, state transitions, money semantics, operational consistency, audit expectations, localization, or business time rules. No implementation mechanisms.>

## 11. UX / surface summary

| Surface / journey | Actor | Required information and actions | Responsible module |
| --- | --- | --- | --- |
| <surface> | <actor> | <behavior> | <module> |

Describe usability, accessibility, and language requirements when relevant. Do not choose UI libraries or implementation routes.

## 12. Product questions and assumptions

- **Blocking product questions:** <questions / none>
- **Assumptions to validate through use:** <assumptions>

Do not keep a technical-question backlog here. Engineering questions and operational prerequisites belong in module artifacts and the tracker.

## 13. Product handoff

- **Initial engineering candidate:** <module and product rationale>
- **Relevant product sections:** <references>
- **Product prerequisites:** <requirements / none>

Engineering reads this baseline and the current tracker, then resolves technical decisions in the implementation repository using the installed Matt/AI Hero skills. This handoff records the starting product context; it is not updated as engineering progresses.

## Product revision policy

Approval freezes this baseline. Only a specific, explicitly user-authorized product revision may change it. Record the approval and product reason with that revision. A technical choice, completed module, new template, or visual redesign does not authorize a PRD edit. Expanding a later delivery phase also requires an authorized product revision.
