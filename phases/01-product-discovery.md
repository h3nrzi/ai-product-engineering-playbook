# Phase 01 — Product Discovery & Product Design

## Purpose

Turn a selected service-product opportunity into a deliberately designed product before Base44 generates the prototype.

This is the deepest product-design phase in the workflow. The Guide LLM should work beside the user like an experienced product designer/product manager: clarify the problem, challenge assumptions, shape the solution, define the experience, establish the visual system, and produce the documents needed for Phase 02.

No application implementation happens here.

> **Phase 01 designs the product. Phase 02 materializes that design in Base44.**

Base44 must not be responsible for discovering the product, inventing its scope, deciding its information architecture, or creating its visual language from vague instructions.

---

# Pre-Phase 01 — Service Opportunity Selection

Before a project enters Phase 01, select it from the shared service-product opportunity library.

Canonical library:

`opportunities/service-products.md`

The library is portfolio-level, not project-specific. Each opportunity should capture enough information to explain why the project may be worth exploring:

- service category
- target user
- primary problem
- current workaround / alternative
- why the current approach is weak
- proposed digital solution direction
- core value
- interesting product/workflow depth
- portfolio differentiation
- status

The library is not a backlog of random website ideas. Start with a service problem worth solving.

Useful selection criteria:

- **Problem strength** — the user pain can be explained clearly
- **Product depth** — the idea supports a meaningful product, not only a landing page
- **Service workflow** — there is a real journey such as booking, requesting, scheduling, tracking, managing, or coordinating a service
- **Portfolio differentiation** — the project adds something meaningfully different from projects already built

Do not create a scoring system unless comparison genuinely benefits from one.

### Selected Opportunity Brief

Once an opportunity is selected, create a short brief containing:

- opportunity
- target user
- primary problem
- proposed solution direction
- why the project is worth exploring

This brief is the entry point to Phase 01. It is not the PRD.

---

# Phase 01 workflow

```text
Selected Opportunity
        ↓
01 Problem Discovery
        ↓
02 Solution Definition
        ↓
03 Product Strategy & Scope
        ↓
04 User & Actor Definition
        ↓
05 UX / Competitive Research
        ↓
06 Jobs & User Journeys
        ↓
07 User Flows
        ↓
08 Information Architecture
        ↓
09 Page Inventory
        ↓
10 UX States & Edge Cases
        ↓
11 Brand & Visual Direction
        ↓
12 Design System
        ↓
13 Responsive & Content Direction
        ↓
14 PRD
        ↓
15 Base44 Prompt Package
        ↓
16 Phase Review & Handoff
        ↓
Phase 02 — Base44 Prototype
```

The sequence is deliberate, but depth should match the product. A simple service product may require short artifacts; a complex multi-actor product may need deeper work. Do not manufacture documentation merely to fill sections.

---

# Stage 01 — Problem Discovery

## Objective

Understand the real user problem before committing to a solution.

Study:

- who experiences the problem
- when and in what context it occurs
- current behavior/workarounds
- primary and secondary pain points
- triggers
- constraints
- desired outcomes
- root causes and consequences
- assumptions and open questions

Avoid decorative personas and invented research facts. Distinguish known information, reasonable assumptions, and unanswered questions.

A useful final problem statement should explain:

```text
[Target user] struggles with [primary problem]
when [context/trigger]
because [root causes].
They need a way to [desired outcome]
without [current friction].
```

### Artifact

`product-design/problem-definition.md`

### Done when

The user, context, current behavior, primary friction, desired outcome, constraints, assumptions, and one clear problem statement are understood well enough to evaluate a solution.

---

# Stage 02 — Solution Definition

## Objective

Define the product direction that directly answers the problem.

Establish:

- solution thesis
- core product promise
- user/business value where relevant
- problem → solution mapping
- core capabilities
- must solve / could solve / not now
- product boundaries
- assumptions and open questions

Every major capability should connect to a real problem or desired outcome. If a feature cannot be justified, question why it is in scope.

Define what the product **is** and what it explicitly **is not**.

### Artifact

`product-design/solution-definition.md`

### Done when

The solution can be described clearly, the primary product promise exists, major capabilities map to real problems, and obvious scope creep is separated from the core solution.

---

# Stage 03 — Product Strategy & Scope

## Objective

Turn the solution into a coherent version of the product that can actually be prototyped.

Define:

- product goal
- actors at a high level
- primary / north-star journey
- supporting journeys
- core capabilities
- MVP boundary
- prototype boundary
- explicit out-of-scope/deferred work
- important product constraints
- qualitative success criteria

Keep these two concepts separate:

```text
Product MVP
≠
Base44 Prototype Scope
```

The prototype may simulate behavior that a production product would later implement for real.

Do not invent fake numerical KPIs without evidence. Early success criteria can be product-level, such as whether a first-time user understands the offering or can complete the core journey without outside help.

### Artifact

`product-design/product-scope.md`

### Done when

Actors, primary journey, MVP scope, prototype scope, non-goals, constraints, and success criteria are explicit enough to prevent uncontrolled expansion during design.

---

# Stage 04 — User & Actor Definition

## Objective

Understand the people/roles whose goals and context materially affect UX.

For each meaningful actor, capture only product-relevant information:

- role
- primary and secondary goals
- needs
- usage context
- behavior patterns
- decision factors
- pain points
- objections
- trust factors
- constraints
- device/accessibility context where relevant

Also identify important cross-actor relationships and non-target users where useful.

Do not create fictional demographic detail that has no product consequence.

### Artifact

`product-design/user-actors.md`

### Done when

Every meaningful actor has enough behavioral/contextual definition to inform later journeys, content, trust, navigation, and interaction decisions.

---

# Stage 05 — UX / Competitive Research

## Objective

Learn how this industry and adjacent products solve similar user problems without blindly copying competitors.

Use four useful reference types when relevant:

- direct competitors
- adjacent products with similar workflows
- best-in-class UX examples
- visual references

Research by task/journey, not by aesthetics alone. Examples:

- how users discover and compare services
- how pricing/duration/trust are presented
- how scheduling/booking/request flows work
- how mobile interactions behave
- how failures/recovery are communicated

Extract decisions using:

- **ADOPT** — useful and suitable
- **ADAPT** — useful but needs modification
- **AVOID** — inappropriate or friction-heavy
- **DIFFERENTIATE** — an opportunity to meaningfully improve the experience

### Artifact

`product-design/ux-research.md`

Optional screenshots/reference notes may live under `product-design/research/` when they add value.

### Done when

Relevant patterns, friction, trust conventions, mobile behavior, visual references, and meaningful differentiation opportunities are understood well enough to influence product design.

---

# Stage 06 — Jobs & User Journeys

## Objective

Describe the progress users are trying to make and the major journeys through which the product delivers that progress.

For each actor, identify meaningful jobs and classify them when useful as:

- critical
- important
- supporting

Define one primary/north-star journey and the important secondary journeys.

For important journey stages capture:

- user goal
- action
- information needed
- decision
- likely friction
- expected outcome

Also identify:

- journey entry points
- alternative paths
- interruptions/recovery
- cross-actor journeys

### Artifact

`product-design/jobs-and-journeys.md`

### Done when

The major jobs and journeys are clear enough that screen-level user flows can be drawn without inventing the product along the way.

---

# Stage 07 — User Flows

## Objective

Convert journeys into explicit flows with decisions, branches, state preservation, failure, and recovery behavior.

For each important flow define:

- actor
- trigger
- entry points
- preconditions
- happy path
- decision points
- alternative paths
- meaningful error paths
- recovery
- back/state-preservation rules
- exit points
- success outcome
- cross-actor effects

Do not add complex failure semantics where the product does not need them, but do not leave critical workflows as happy-path-only diagrams.

Useful diagrams may be written in Mermaid or simple text.

### Artifact

`product-design/user-flows.md`

### Done when

Core journeys have explicit executable flows and meaningful branches/recovery are clear enough to derive IA and page/screen requirements.

---

# Stage 08 — Information Architecture

## Objective

Organize the product so users can find, understand, and move between its important information and capabilities.

Define:

- product areas
- content types/grouping
- primary/secondary navigation
- authenticated navigation where relevant
- staff/admin navigation where relevant
- hierarchy
- entry points
- cross-links
- public/private boundaries
- sitemap

Navigation should reflect the user's mental model, not database tables or component structure.

Control unnecessary depth in the core journey.

### Artifact

`product-design/information-architecture.md`

### Done when

The product hierarchy and navigation are coherent, important content is discoverable, public/private areas make sense, and the sitemap can support the user flows without unnecessary complexity.

---

# Stage 09 — Page Inventory

## Objective

Determine exactly which product surfaces are required and why.

Distinguish:

- page / route
- screen / step
- modal / drawer
- state
- reusable section

Do not treat every state or booking step as a separate route by default.

For each important page/surface define:

- name
- product area
- audience
- purpose
- entry points
- core content
- primary CTA
- secondary actions
- access requirement
- related journeys
- priority (required / optional / deferred)

Identify dynamic templates such as service detail, specialist detail, article detail, appointment detail, etc., rather than counting each content instance as a unique design.

A useful test for every page:

> If this page disappeared, which user need or journey would break?

### Artifact

`product-design/page-inventory.md`

### Done when

Every required flow has the surfaces it needs, every retained page has a clear purpose, primary actions are understood, access is clear, and unnecessary pages have been removed.

---

# Stage 10 — UX States & Edge Cases

## Objective

Design important product behavior beyond the happy path.

Only where relevant, define:

- default
- loading/pending
- empty
- success
- known error
- validation
- disabled/selected/unavailable
- conflict/stale
- unknown outcome/reconciliation
- authentication/session transition
- permission/access
- destructive action confirmation
- responsive/content edge cases

Preserve useful user intent during recoverable failures where appropriate.

Keep concepts distinct:

```text
Empty ≠ Error
Known failure ≠ Unknown outcome
Disabled ≠ Unavailable
```

A lightweight state matrix may be used for critical surfaces; do not create one for every component.

### Artifact

`product-design/ux-states.md`

### Done when

Important journeys have the states and recovery behavior needed to avoid obvious prototype gaps, without manufacturing edge cases that do not matter to the product.

---

# Stage 11 — Brand & Visual Direction

## Objective

Define the visual personality of the product before creating the design system.

Establish:

- 3–5 core brand personality traits
- desired user perception/emotional goal
- visual positioning (e.g. minimal ↔ expressive, friendly ↔ premium)
- approved reference mood
- color direction
- typography direction
- imagery direction
- shape language
- motion direction where relevant
- explicit anti-direction / visual patterns to avoid

The goal is not “make it modern.” The direction should be explainable from the audience, service category, trust requirements, and brand character.

### Artifact

`product-design/visual-direction.md`

### Done when

The product has a distinctive and coherent visual direction strong enough to derive actual design tokens and component rules.

---

# Stage 12 — Design System

## Objective

Translate the approved visual direction into a reusable system Base44 can apply consistently.

Define at the level the project needs:

### Foundations

- semantic color roles
- typography scale and usage
- spacing scale
- layout / grid / content widths
- radius
- elevation/shadows
- borders/dividers
- responsive foundations

### Components

- core controls such as buttons, inputs, selects, cards, alerts, dialogs/drawers, navigation patterns
- important product-specific components such as service cards, specialist cards, appointment cards, time slots, booking summary, status badge
- necessary variants only

### States and rules

- default / hover / focus / active / selected / disabled / loading / error/success where relevant
- visible focus
- form labeling/error/help rules
- feedback patterns
- iconography
- imagery aspect/fallback rules
- RTL-specific behavior where relevant
- baseline accessibility (contrast, touch targets, labels, non-color-only signals, readable type)

Prefer semantic design tokens over arbitrary one-off styling.

### Artifact

`product-design/design-system.md`

A separate `design-tokens.md` is optional only when the product benefits from it.

### Done when

Base44 should not need to invent a new visual language independently on every page.

---

# Stage 13 — Responsive & Content Direction

## Objective

Define how the experience adapts across device contexts and how the product communicates.

### Responsive direction

Establish:

- customer/public/admin device priorities
- mobile-first / desktop-first / balanced strategy where meaningful
- navigation adaptation
- important layout transformations rather than only breakpoint numbers
- mobile content priority
- sticky/accessible primary actions where justified
- density differences between public, customer, and operational interfaces

### Content direction

Establish:

- tone of voice
- UI-copy principles
- CTA language
- canonical terminology
- content hierarchy
- realistic sample/demo content expectations
- localization/RTL rules
- handling of long/missing content

Avoid lorem ipsum in the prototype. Sample information should be realistic while remaining clearly demo data when not verified.

### Artifact

`product-design/responsive-content-direction.md`

### Done when

Base44 has clear guidance for important device adaptations, terminology, tone, RTL/localization, and realistic content behavior rather than having to invent these rules itself.

---

# Stage 14 — PRD

## Objective

Consolidate the approved product design into one authoritative, readable Product Requirements Document.

The PRD is a synthesis, not a second round of discovery and not a copy-paste dump of every supporting artifact.

Recommended structure:

1. Product Overview
2. Problem
3. Solution
4. Target Users & Actors
5. Product Scope / Non-goals / Deferred
6. Core Capabilities
7. Primary & Secondary Journeys
8. Product Requirements
9. Page / Surface Summary
10. UX Principles
11. Important States
12. Brand / Visual Direction
13. Design System Reference
14. Responsive Direction
15. Content & Localization
16. Prototype Requirements
17. Success Criteria
18. Assumptions
19. Open Questions
20. Supporting Documents

Product requirements should describe observable behavior and product semantics, not implementation choices such as state library, ORM, HTTP style, database, or backend architecture.

### Prototype requirements

The PRD must clearly state what Phase 02 should demonstrate, for example:

- required pages/surfaces
- primary journeys
- realistic mock data
- important states
- responsive behavior
- working navigation/interactions
- simulated product behavior

It must also make clear what Base44 is not expected to prove, such as production authentication, real database durability, payment processing, security guarantees, or distributed concurrency.

### Artifact

`product-design/prd.md`

### Done when

A competent product designer or engineering agent can understand the intended product from the PRD alone, while linked supporting artifacts provide deeper detail when needed.

---

# Stage 15 — Base44 Prompt Package

## Objective

Convert the approved product design into an incremental set of prompts that Base44 can execute without depending on conversation history.

Do not default to one mega-prompt.

A common sequence may look like:

```text
00 Project Foundation
01 Design System
02 App Shell / Navigation
03 Public Product Surfaces
04 Primary User Flow
05 Customer Area
06 Staff/Admin Area
07 States & Recovery
08 Responsive / RTL Pass
09 Final Consistency Pass
```

The actual sequence should match the product; omit or split prompts when useful.

### Each prompt should normally contain

- objective
- relevant context
- exact scope
- relevant product decisions
- pages/surfaces
- required behavior
- UX rules
- visual/design-system rules
- meaningful states
- responsive/RTL requirements
- mock-data expectations
- explicit “do not” constraints
- acceptance check

### Change discipline

Prompts should tell Base44 to:

- preserve already approved behavior
- avoid rewriting unrelated areas
- avoid inventing new scope
- use realistic mock/demo data
- keep prototype behavior honest

The final consistency pass should check design tokens, typography, spacing, CTA hierarchy, terminology, states, responsive behavior, RTL, and cross-page consistency without adding new product features.

### Artifacts

Prefer a folder when there are multiple prompts:

```text
product-design/base44-prompts/
├── README.md
├── 00-...
├── 01-...
└── ...
```

The README records execution order and brief intent of each prompt.

### Done when

A fresh Base44 session could build the intended prototype incrementally from this package without relying on hidden chat context or inventing major product/design decisions.

---

# Stage 16 — Phase Review & Handoff

## Objective

Verify coherence and readiness; do not perform new discovery unless a real contradiction/gap is found.

Review these chains:

```text
Problem
→ Desired Outcome
→ Solution
→ Capabilities
→ Journeys
→ Flows
→ Pages
```

and:

```text
Journey
→ User Flow
→ Required Surface
→ UX States
→ Base44 Prompt
```

Check:

- problem/solution consistency
- scope/non-goal consistency
- journey and page coverage
- meaningful state/recovery coverage
- IA/navigation coherence
- visual direction ↔ design system consistency
- terminology/content consistency
- PRD completeness
- Base44 prompt ownership and execution order

Resolve contradictions before handoff. Do not create a new review bureaucracy when artifacts are already coherent.

### Final package

A typical project leaves Phase 01 with:

```text
product-design/
├── problem-definition.md
├── solution-definition.md
├── product-scope.md
├── user-actors.md
├── ux-research.md
├── jobs-and-journeys.md
├── user-flows.md
├── information-architecture.md
├── page-inventory.md
├── ux-states.md
├── visual-direction.md
├── design-system.md
├── responsive-content-direction.md
├── prd.md
└── base44-prompts/
    ├── README.md
    └── ...
```

Not every artifact must be long. Keep depth proportional to the product.

### Handoff principle

Ask:

> If the current chat disappeared, could a fresh Base44 session and a new Guide LLM understand what product we designed, why, what is in/out of scope, how it should look/behave, and what prompts should be executed next?

If yes, Phase 01 is durable enough to hand off.

---

# Artifact authority

Use this simple hierarchy:

```text
Approved product decisions / supporting design artifacts
        ↓
PRD (authoritative consolidated product definition)
        ↓
Base44 Prompt Package (execution instructions for Phase 02)
```

If a prompt conflicts with the PRD, fix the prompt. If the PRD exposes a contradiction in the deeper product-design decisions, resolve that contradiction before proceeding.

Avoid maintaining duplicate versions of the same decision in several documents without purpose.

---

# Phase 01 quality principles

1. **Problem before solution.** Do not begin with pages or features.
2. **Outcome before feature.** Understand what progress the user wants.
3. **Flows before pages.** Page inventory is derived from journeys and IA.
4. **Visual direction before design system.** Tokens should express a deliberate personality.
5. **Design before Base44.** Base44 materializes decisions; it does not own them.
6. **Realistic, not fake certainty.** Record assumptions and unknowns honestly.
7. **Depth follows complexity.** Professional does not mean unnecessarily large.
8. **No premature architecture.** Database, backend architecture, framework internals, and infrastructure are not Phase 01 product decisions unless they directly constrain product experience.
9. **No feature inflation.** Every major capability should earn its place by supporting the problem, outcome, or approved scope.
10. **Durable artifacts over chat history.** A future session should recover from the repository.

---

# Phase 01 completion gate

Phase 01 is complete when:

- the selected opportunity has a clear problem worth solving
- problem and desired outcomes are understood
- solution and core product promise are clear
- users/actors and scope are explicit
- relevant UX/reference research has informed the design
- important jobs, journeys, and flows are defined
- information architecture is coherent
- final page/surface inventory is understood
- meaningful UX states/recovery are defined
- visual direction and design system are approved
- responsive/content/localization direction is clear
- the PRD is approved
- the Base44 prompt package is ready and ordered
- cross-artifact contradictions are resolved
- no unresolved question prevents the intended prototype from being built

Then proceed to **Phase 02 — Base44 Prototype**.
