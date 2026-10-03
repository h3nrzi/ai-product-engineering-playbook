# Prompt 01 — Design System

## Objective

Materialize the approved reusable visual and interaction system for the Persian/RTL women’s beauty salon prototype created in Prompt 00.

Build the shared foundations and component vocabulary that all later public, booking, customer, staff and manager surfaces will use. The result should make later page prompts assemble consistent interfaces rather than inventing styles independently.

Do **not** build the full application, navigation architecture, public pages, booking journey, customer account, salon calendar workflow or manager pages in this step. Create and demonstrate reusable foundations/components only where useful to verify the system.

Preserve all product boundaries, demo fixtures, locale rules and behavior guardrails established by Prompt 00.

## Source-of-truth direction

Use the approved design direction exactly as the baseline:

- Character: calm, professional, warm and refined.
- Avoid generic “luxury salon” clichés, glossy gradients, metallic gold-heavy styling, overly decorative typography or highly saturated pink/purple palettes.
- No final salon logo or identity should be invented.
- Persian is the visible product language and the interface direction is RTL.
- Customer/public and staff/manager areas use the **same design system** even when staff surfaces later become denser.

Do not create a separate visual language per product area.

## 1. Design tokens and foundations

Implement reusable semantic tokens rather than page-specific hardcoded styling.

### Colors

Use these approved roles:

- Page background: `#FAF7F3`
- Surface: `#FFFFFF`
- Primary: `#5E3448`
- Primary hover: `#4C2939`
- Primary pressed: `#402130`
- Soft accent: `#EEDCE2`
- Main text: `#272327`
- Muted/supporting text: `#655D63`
- Essential control border: `#91848B`
- Decorative divider: `#E5DDD8`
- Success foreground/background: `#246447` / `#E8F3EC`
- Error foreground/background: `#A32638` / `#FFF0F2`
- Warning foreground/background: `#80500B` / `#FFF3D8`
- Information/pending foreground/background: `#315A7A` / `#EDF4FA`
- Disabled surface: `#EEE9E6`

Rules:

- Primary buttons use white text.
- Secondary buttons use primary text with a visible control border on a white surface.
- Text links use the primary color and remain visibly recognizable as links where context is ambiguous.
- Selected controls combine more than color: use accent surface + primary border + explicit selected/check semantics.
- Status colors are semantic feedback, not decorative brand accents.
- Never communicate appointment/payment/refund status by color alone.
- Do not reduce opacity on an entire component if it makes essential explanation/status text difficult to read.

### Typography

Use `Vazirmatn` with a Persian-capable sans-serif fallback.

Approved scale:

- Page title: 32px / 48px line-height on wide screens; 28px / 42px on narrow screens; bold.
- Section title: 24px / 36px; bold.
- Card title / key price: 20px / 32px; medium or bold.
- Body and customer controls: 16px / 28px; regular body, medium controls.
- Labels and supporting copy: 14px / 24px; medium labels, regular supporting copy.
- Staff table/calendar supporting text: 14px / 24px.

Rules:

- Essential prices, deadlines, errors and appointment details must not drop below 14px.
- Long Persian content wraps. Never shrink essential copy to force it onto one line.
- Display amount and `تومان` together and label distinct monetary meanings such as price basis, deposit and remaining balance.
- Do not rely only on font weight to distinguish consequential financial information.

### Spacing and sizing

Use this spacing scale consistently:

`4, 8, 12, 16, 24, 32, 48, 64px`

General use:

- 8–12px inside tightly related controls/content.
- 16–24px inside cards and panels.
- 32–48px between major page sections.
- Narrow-screen page gutter: 16px.
- Medium-screen gutter: 24px.
- Wide-screen gutter: 32px.
- Public content max width: 1200px.
- Booking form max width for later prompts: 680px.
- Salon operations may later use up to 1440px.

### Radius, borders and elevation

- Controls: 8px radius.
- Cards: 12px radius.
- Dialogs/drawers: 16px radius.
- Pill shapes only for compact status badges and choice chips where appropriate.
- Standard border: 1px.
- Use essential control border for interactive boundaries.
- Decorative divider is only for nonessential separation.
- Prefer bordered cards over floating/elevated cards.
- Overlays may use a restrained shadow: `0 8px 24px rgba(39,35,39,0.12)`.

Do not add heavy glassmorphism, large blurred shadows or excessive elevation.

## 2. Global interaction states

Every reusable interactive component should support only the states it genuinely needs, using the same semantics across the product.

### Default

Clear label, readable value/content and a visible boundary where the control requires one.

### Hover

Use a subtle color change on devices that support hover. No information or action may exist only on hover.

### Focus

Use a clearly visible 2px primary focus ring with approximately a 2px surface gap. Ensure it remains visible on every relevant background.

### Pressed

Use the approved darker primary or a restrained pressed surface. Do not use disruptive movement or scale effects.

### Selected

Use primary border + soft accent + explicit selected/check semantics.

### Disabled

Use the disabled surface and prevent activation. When the reason matters to the task, show an understandable nearby reason. Do not make disabled content illegible.

### Loading

Keep the original action/context visible, add a small progress indicator and prevent duplicate submission. Do not replace the control with an unrelated spinner-only layout.

### Known error

Show specific error text, relevant icon/field association and an actionable recovery path.

### Success

Name the actual operation that completed. Do not use success styling to imply a different operation also succeeded.

### Pending / unknown outcome

Show explicit `در حال بررسی` / pending semantics and a way to retrieve current status where later flows require it. Never use a success tick or definite-failure styling for an unknown outcome.

### Motion

- Ordinary feedback transitions: roughly 120–180ms.
- Drawer/dialog transitions: up to roughly 240ms.
- Respect reduced-motion preferences.
- Never animate or restart a countdown to imply that a hold/payment deadline has been extended.

## 3. Core reusable components

Create a reusable component vocabulary with coherent variants. Use realistic Persian demo copy to preview components, but do not create full application pages.

### Buttons

Variants:

- Primary
- Secondary
- Text/link-style action
- Destructive

States:

- Default
- Hover where applicable
- Focus
- Pressed
- Loading
- Disabled

Rules:

- One visually dominant primary action per task surface.
- Minimum interaction height: 44px.
- Use explicit Persian destructive verbs such as `لغو نوبت`; never generic `تأیید` or `OK` for destructive actions.
- Loading prevents repeat submission.

### Text inputs

Support:

- visible persistent label,
- entered value,
- optional help text,
- field-level error,
- disabled state,
- required/optional indication where unclear.

Validation must not clear unrelated valid fields.

### Phone and SMS-code inputs

- Place phone/code values in an LTR segment inside the RTL layout.
- Accept Persian or Latin digits.
- Preserve leading zeroes.
- Support paste and sensible mobile input behavior.
- Do not invent a fixed OTP length if the real provider is not selected.
- Later login/contact flows must be able to reuse the same component.

### Radio / visible choice / select

- Prefer visible radio/card choices for small consequential sets.
- Use select/combobox patterns for longer sets.
- Show selected state explicitly.
- Unavailable items show why they cannot be chosen when explanation matters.
- Support keyboard and touch operation.
- A choice that changes duration/price context must be able to expose that consequence.

### Checkbox

Use only for a genuine independent choice or required acceptance.

Do not preselect customer consent for salon-side specialist/time replacement.

### Card

Base card should support:

- clear heading,
- concise supporting information,
- optional media,
- one obvious primary interaction where appropriate,
- optional secondary action.

Avoid nested clickable zones that make it unclear whether the whole card or a child control is activated.

### Alerts

Variants:

- Information
- Success
- Warning
- Error

Use concise headings where useful, explanation and recovery/action when needed.

Consequential booking/payment/refund messages later must be inline or persistent rather than disappearing immediately.

### Toast

Toast is only for brief secondary feedback.

Never use a toast as the only feedback for:

- payment status,
- booking confirmation,
- cancellation consequence,
- refund status,
- validation failure that requires user correction.

### Dialog and drawer

Create reusable dialog/drawer patterns with:

- visible heading,
- close action,
- clear primary/secondary actions,
- focus management,
- return focus after close,
- content that can expand for long Persian text.

Use dialogs for focused consequential decisions and drawers for contextual detail/editing.

Safe dismissal must preserve useful unsaved context where appropriate.

Closing a dialog must never imply cancellation of an already-submitted payment or mutation.

### Status badge

Create concise text-first badges that combine label with semantic color/icon where useful.

Support distinct categories for later use:

- appointment state,
- payment state,
- refund state.

Do not merge them into one generic “وضعیت” badge.

### Loading / empty / error panel

Create distinct reusable patterns for:

- loading,
- genuine empty data,
- known fetch/read error.

Do not show an empty-state illustration when data failed to load.

Skeletons, if used, should resemble the expected content structure.

## 4. Product-specific reusable components

Create reusable components that later prompts can compose into real screens. Keep them demoable in isolation or in a small component preview area; do not build the final booking/customer/staff pages yet.

### Service card

Must be able to show:

- service name,
- honest demo image or fallback,
- fixed-price or approximate-price wording,
- duration or volume/duration context,
- direct booking/detail action,
- consultation path instead of a fake direct-booking CTA when consultation is required.

### Specialist card / specialist choice

Must support:

- specialist name,
- supported-service context,
- honest photo/fallback,
- named selection,
- the `هر متخصص واجد شرایط` option.

When explaining any-eligible behavior, state that assignment is from eligible/available specialists using salon-defined priority. The final actual assigned name will be shown in later booking UI before payment/confirmation.

Do not add ratings or fabricated reviews.

### Volume choice

Show:

- manager-defined option label,
- booking duration,
- relevant approximate-price/deposit-basis explanation.

The component must communicate that changing volume can change duration and therefore availability. It must not imply the volume choice guarantees a final variable price.

### Date/time choice

Prepare a reusable time-slot choice pattern with:

- available,
- selected,
- unavailable,
- stale/conflict recovery presentation.

Unavailable times cannot be activated/submitted.

Keyboard interaction and clear selected semantics are required.

The final booking summary later should be able to show full local date and start time.

### Assigned specialist summary

Create a reusable compact summary that can show the **actual assigned specialist name**, including when the earlier preference was `هر متخصص واجد شرایط`.

Never design the final review around an unresolved generic specialist label.

### Booking summary

Create a reusable summary structure capable of showing:

- service,
- volume/duration,
- assigned specialist,
- date/start time,
- booking contact,
- fixed vs approximate price type,
- disclosed price/deposit basis,
- exact deposit,
- remaining balance or estimate,
- cancellation/change terms and deadline,
- primary action area.

For approximate-price services, deposit basis and final price must remain clearly different concepts.

### Hold notice

Prepare a persistent notice pattern that can show:

- temporary hold status,
- actual remaining deadline,
- what action is required next,
- pending/unknown-payment extension when applicable.

Do not design the countdown to reset visually when a view is reopened.

### Payment/result panel

Prepare separate variants for:

- verified success,
- definite failure,
- checking / unknown outcome,
- released slot with continuing payment verification,
- late verified success that creates refund entitlement.

Unknown outcome must not encourage duplicate payment.

### Appointment card/detail summary

Create a reusable presentation for:

- service,
- specialist,
- date/time,
- appointment status,
- separate payment status,
- separate refund status when relevant,
- stored-policy/deadline context,
- contextual actions area.

### Replacement / reschedule comparison

Create a side-by-side or stacked comparison pattern for original vs proposed appointment data, supporting Persian/RTL and narrow screens.

It must clearly distinguish:

- original time/specialist,
- proposed time/specialist,
- deposit handling,
- explicit acceptance where required.

Do not visually imply the original is already replaced before confirmation.

### Settlement summary

Create a reusable financial summary that can show:

- accepted final service price,
- already paid deposit,
- remaining in-salon balance,
- actual received amount/source when later used by staff.

For approximate-price services, never label the earlier deposit basis as the guaranteed final price.

### Calendar primitives

Do **not** build the operational calendar page yet, but establish reusable calendar visual primitives for later Prompt 06:

- date/time axis treatment,
- specialist labels,
- full-duration appointment block,
- held vs confirmed treatment,
- conflict marker,
- clear text/state semantics in addition to color.

Do not assign arbitrary rainbow colors to specialists.

Appointment blocks must visually represent full reserved duration, not only start time.

On narrow screens, later prompts must be able to switch to a readable day/list pattern rather than squeezing a desktop grid.

## 5. Navigation visual primitives

Create only reusable visual primitives for navigation, not the actual product shell.

Support:

- labeled navigation item,
- active state with visible indicator + label,
- icon + label pattern where useful,
- narrow-screen menu treatment,
- staff/manager side/top navigation styling that can later share the same tokens.

Do not decide or implement the final public/customer/staff navigation structure here; Prompt 02 handles that.

## 6. RTL, icons and imagery rules

Apply these globally to reusable components:

- Use logical start/end alignment and spacing instead of hardcoded left/right assumptions.
- Mirror directional navigation arrows where appropriate.
- Do not mirror photographs, brand marks or nondirectional universal symbols.
- Keep phone numbers, OTPs and similar inherently LTR values isolated to preserve correct reading order.
- Use one simple consistent outline icon family.
- Essential actions should have readable labels; icon-only actions require an accessible name and at least the approved interaction target size.
- Service imagery container: 4:3.
- Specialist portrait container: 1:1.
- Crop without distorting faces.
- Missing imagery uses a neutral fallback with a simple symbol/initials and never blocks the task.
- If sample imagery is used, do not present it as proof of actual salon staff/results.
- Avoid text baked into images.
- Do not invent ratings, endorsements, awards or credentials.

## 7. Accessibility baseline

Build components so later pages can meet these prototype requirements:

- readable text and clear hierarchy,
- visible keyboard focus,
- keyboard-operable interactive controls,
- persistent labels for form fields,
- error/help association with relevant fields,
- non-color-only selected/unavailable/status feedback,
- minimum product target of approximately 44 × 44px for interactive touch areas,
- actual contrast appropriate to the approved semantic pairings,
- useful accessible names for icon-only controls,
- focus containment/return for overlays,
- compatibility with long Persian text and text zoom.

Do not announce a countdown every second to assistive technology; later hold/payment views should expose meaningful status/deadline changes without creating constant noise.

Prototype accessibility work does not claim complete production accessibility certification.

## 8. Component demonstration / review surface

If Base44 needs a place to verify the system, create a **temporary internal component-preview surface** that demonstrates:

- semantic colors,
- typography hierarchy,
- spacing/radius/elevation,
- button/input/choice variants,
- alert/status/loading/empty/error variants,
- representative service/specialist/appointment/booking-summary components,
- narrow and wide RTL behavior.

This preview is a development/demo aid, not a customer-facing product route and should not be promoted in product navigation.

Use the shared Prompt 00 demo fixtures rather than inventing a second, inconsistent dataset.

## 9. Do not change product behavior

This prompt is visual/system work only.

Do not change or reinterpret:

- one-service/one-specialist appointment scope,
- named vs any-eligible assignment semantics,
- 20% default deposit,
- 10-minute ordinary hold,
- up-to-5-minute unknown-payment extension,
- 24-hour cancellation/rescheduling default,
- deposit transfer on eligible reschedule,
- customer consent for confirmed salon-side replacements,
- separate appointment/payment/refund state models,
- contact vs account ownership boundaries,
- staff/manager permission boundaries.

Do not add deferred product features simply because a component library usually contains them.

## 10. Change discipline

- Preserve Prompt 00 foundations and fixtures.
- Do not rewrite unrelated project areas.
- Prefer shared tokens/components over one-off styles.
- Do not introduce a second theme or alternate palette.
- Do not hardcode page-specific visual exceptions unless they correspond to an approved semantic need.
- Keep component APIs/variants understandable and minimal; do not manufacture dozens of stylistic variants.
- Use realistic Persian sample copy instead of lorem ipsum.

## Acceptance check

Before considering Prompt 01 complete, verify that:

- approved semantic color tokens exist and are used consistently;
- Vazirmatn and the approved typography hierarchy are applied;
- spacing, content widths, radii, borders and restrained elevation follow the approved system;
- primary, secondary, text and destructive buttons have coherent default/focus/loading/disabled behavior;
- form controls keep visible labels and support Persian/RTL with LTR phone/code segments;
- selected, unavailable, disabled, loading, known-error, success and pending/unknown states are visually distinct without relying only on color;
- service, specialist, volume, time-slot, assigned-specialist, booking-summary, hold, payment-result, appointment, replacement/reschedule, settlement and calendar primitives exist for later prompts;
- appointment/payment/refund status presentation remains separable;
- service and specialist imagery uses the approved aspect ratios and honest fallback behavior;
- touch targets, visible focus and keyboard behavior are present at the reusable-component level;
- long Persian labels/content wrap cleanly;
- no final salon brand identity, ratings, reviews or credentials were invented;
- no full application page or flow outside the scope of this prompt was prematurely built;
- Prompt 00 product rules and shared demo fixtures remain unchanged.

Stop after the reusable design system is coherent and demonstrable. Prompt 02 will build the actual app shells and navigation from this system.