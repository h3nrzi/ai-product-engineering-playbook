# Phase 01 — Product Discovery & Product Design

## Goal

Turn an initial idea into a deliberately designed product before any prototype is generated.

This is the most discovery-heavy phase of the workflow. The Guide LLM should behave like an experienced product designer/product manager beside the user: ask focused questions, challenge vague assumptions, shape the product, and leave durable artifacts that make Phase 02 executable.

No application implementation happens here.

## Core questions

The phase should establish, at the level appropriate to the product:

- What problem are we solving?
- Who is the primary user?
- What outcome is that user trying to achieve?
- What is the core value proposition?
- What belongs in the first product scope and what is explicitly excluded?
- What are the primary user journeys?
- What pages/screens are required?
- What information and actions belong on each important screen?
- What important states exist: empty, loading, validation, success, failure, unavailable, etc.?
- What content, language, locale, trust, accessibility, responsive, and service-specific constraints matter?
- What visual/product direction should Base44 follow?
- What should be real in the prototype and what may remain mocked/dummy?

Do not force irrelevant questions. Discovery depth should follow product complexity.

## Product-design workflow

A typical sequence is:

```text
Idea
→ problem + audience
→ product promise
→ scope / non-scope
→ core journeys
→ information architecture
→ page inventory
→ page-level behavior/content
→ important states and edge cases
→ design direction
→ prototype boundaries
→ PRD
→ Base44 prompt package
→ Phase 02
```

The Guide should help the user make decisions rather than inventing the product alone.

## Required artifacts

### 1. PRD

Every project should leave Phase 01 with a concise but implementation-useful Product Requirements Document.

The PRD should normally include:

- product summary
- problem statement
- target users
- goals and success definition
- product scope
- explicit non-goals / deferred scope
- core user journeys
- functional requirements
- page/screen inventory
- important states and behavior
- content/locale requirements
- design/experience direction
- prototype assumptions and mock boundaries
- open questions, if any remain non-blocking

The PRD defines the intended product, not the technical architecture.

### 2. Base44 Prompt Package

Phase 01 must also produce the prompts/instructions that will be given to Base44 in Phase 02.

Do not rely on a single vague prompt such as “build this website.” The package should give Base44 enough product and design context to generate a strong React prototype that can later be engineered rather than discarded.

The package may include:

- initial build prompt
- product context and audience
- required routes/pages
- important journeys
- visual/design direction
- responsive requirements
- locale/RTL/content instructions when relevant
- realistic dummy-data guidance
- behavior that should be simulated
- things Base44 should deliberately not build
- follow-up refinement prompts when useful

Prompts should describe desired outcomes and product behavior without unnecessarily dictating internal code architecture.

### 3. Product Handoff

Create a short handoff that tells the next session/LLM:

- what product was approved
- where the PRD lives
- where the Base44 prompts live
- what must be preserved during prototyping
- what is intentionally mocked or deferred
- what would count as a good enough prototype to leave Phase 02

## Design quality bar

The discovery output should be good enough that Base44 is not being asked to discover the product for us.

Before exiting, ask:

> Could another competent product designer read these artifacts and understand what experience we intend to prototype, why it exists, and what is out of scope?

If not, discovery is incomplete.

## Avoid

- technical architecture and database design
- choosing implementation details that do not affect product intent
- endless feature ideation
- designing every hypothetical future feature
- using Base44 as a substitute for product thinking
- giant documents that repeat the same decision in multiple forms

## Exit criteria

Phase 01 is complete when the product is sufficiently defined, the PRD is approved, the Base44 prompt package is ready, and no unresolved question prevents generation of the intended prototype.

Then proceed to **Phase 02 — Base44 Prototype**.
