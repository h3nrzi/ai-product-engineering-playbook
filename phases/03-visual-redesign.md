# Phase 03 — Visual Redesign & UI Polish

## Objective

Improve the product's visual quality, hierarchy, consistency, responsiveness, and interaction presentation **after** the product is functionally coherent.

Primary tool:

Google Stitch — <https://stitch.withgoogle.com/>

This phase is conditional.

If the product already looks and feels strong enough, keep this phase minimal or skip it.

The purpose is redesign, not product rediscovery.

---

# Entry condition

Enter Phase 03 when:

- core product behavior is implemented;
- important user journeys work;
- module contracts and business rules are stable enough;
- the main remaining weakness is visual/interaction quality rather than missing functionality.

Do not use Stitch to hide unfinished product logic.

---

# Preserve existing behavior

Visual redesign must preserve:

- PRD scope;
- module responsibilities;
- permissions and ownership;
- business rules;
- validated workflows;
- status semantics;
- forms and required information;
- meaningful error/recovery behavior;
- completed engineering acceptance.

A prettier screen is not allowed to silently change what an action means.

If a proposed redesign implies a product change, treat that as a separate explicit product decision.

---

# Step 01 — Audit the current UI

Review the implemented product on representative devices.

Identify real visual/UX problems, such as:

- weak hierarchy;
- inconsistent spacing/typography;
- generic dashboard appearance;
- poor mobile adaptation;
- overloaded cards;
- inconsistent components;
- unclear primary actions;
- dense or confusing forms;
- weak empty/error/pending states;
- visual mismatch between public/customer/staff areas;
- accessibility/readability problems;
- poor use of imagery;
- inconsistent RTL behavior when relevant.

Do not redesign screens merely because Stitch can generate alternatives.

Prioritize surfaces that most affect the product experience.

---

# Step 02 — Establish visual direction

Before redesigning many screens, define the shared visual language.

When useful, create or refine a `DESIGN.md` that captures:

- design principles;
- semantic colors;
- typography;
- spacing;
- shape/radius;
- elevation;
- component rules;
- interaction states;
- responsive principles;
- imagery/icon direction;
- accessibility constraints;
- localization/RTL rules.

The design system should support the existing product rather than force the product into a generic template.

---

# Step 03 — Redesign priority surfaces in Stitch

Bring the current product context into Stitch using the available project/design/code references.

Redesign iteratively.

Prefer a sequence like:

```text
visual system
→ primary public/customer surface
→ primary task flow
→ account/secondary surfaces
→ staff/operational surfaces
→ remaining consistency pass
```

The exact sequence depends on the product.

For each redesigned surface, provide Stitch with:

- the purpose of the surface;
- the actor;
- existing required information/actions;
- current UI problems;
- design-system context;
- responsive requirements;
- explicit behaviors that must not change.

Do not ask Stitch to rediscover the business model.

---

# Step 04 — Review design against the working product

For each proposed redesign verify:

- all required actions still exist;
- no permission boundary disappeared;
- no product state became ambiguous;
- critical information was not removed for aesthetics;
- mobile/desktop adaptations remain usable;
- long/realistic content still fits;
- destructive and consequential actions remain clear;
- loading/error/empty/pending/success states still make sense;
- accessibility basics remain intact.

Reject attractive designs that break the product.

---

# Step 05 — Implement approved visual changes

Use the engineering agent to apply approved designs to the real product repository.

Treat visual implementation as normal engineering work:

- preserve behavior;
- reuse/refine shared components;
- avoid one-off styling drift;
- keep responsive behavior intentional;
- verify accessibility;
- review diffs.

If the redesign is broad enough to require multiple sessions, use the same Phase 02 engineering discipline: spec/tickets only when the size actually needs them.

---

# Step 06 — Final UI verification

Review the integrated product for:

- visual hierarchy;
- typography;
- spacing;
- component consistency;
- CTA hierarchy;
- responsive behavior;
- RTL/localization when relevant;
- interaction states;
- focus/keyboard behavior;
- long content;
- empty/loading/error states;
- customer/staff visual coherence;
- design-system consistency.

Check real user journeys, not only isolated screenshots.

---

# Recommended artifacts

Keep only what is useful:

- `DESIGN.md` when a durable design system is needed;
- Stitch project/share link;
- final design references/screens;
- concise implementation notes when necessary.

Do not create a large design-document stack by default.

---

# Phase 03 exit criteria

Phase 03 is complete when:

- the implemented product has an intentional, coherent visual system;
- high-priority screens and flows meet the desired quality bar;
- redesign has not changed approved behavior without an explicit product decision;
- responsive and accessibility basics are verified;
- the final product is presentation-ready for the project's goal.

---

# Phase principle

> **Functionality defines the truth. Design makes that truth clear, usable, and desirable.**
