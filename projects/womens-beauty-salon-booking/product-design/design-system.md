# Design System — Women’s Beauty Salon Booking

- Stage: 12 — Design System
- Status: draft for user review
- Date: 2026-10-03
- Model: one physical women’s salon, Persian-language product for the Iranian market
- Basis: approved [visual direction](visual-direction.md), [UX states](ux-states.md), [page inventory](page-inventory.md), and [user flows](user-flows.md).

This document translates the approved warm, calm and professional direction into reusable foundations and components for the Base44 prototype. It does not change booking, identity, payment or refund rules. No salon name or final logo is invented.

## 1. Semantic colors

Use these roles consistently; do not introduce a different palette per page.

| Role | Value | Use |
| --- | --- | --- |
| Background | #FAF7F3 | Warm page canvas |
| Surface | #FFFFFF | Cards, forms, drawers and dialogs |
| Primary | #5E3448 | Main action, selected emphasis and focus |
| Primary hover | #4C2939 | Pointer hover on primary controls |
| Primary pressed | #402130 | Pressed primary controls |
| Soft accent | #EEDCE2 | Selected backgrounds and restrained accents |
| Text | #272327 | Headings, body and prices |
| Muted text | #655D63 | Supporting information, still readable |
| Control border | #91848B | Essential input/control boundaries |
| Decorative divider | #E5DDD8 | Nonessential separators, never the only control boundary |
| Success foreground / background | #246447 / #E8F3EC | Verified successful outcomes |
| Error foreground / background | #A32638 / #FFF0F2 | Known failures and field errors |
| Warning foreground / background | #80500B / #FFF3D8 | Time limits, conflict and attention |
| Information foreground / background | #315A7A / #EDF4FA | Pending/checking outcomes and neutral notices |
| Disabled surface | #EEE9E6 | Inactive controls with an understandable reason |

Primary buttons use white text. Secondary buttons use primary text and a control border on a white surface. Text links use primary and an underline where needed to distinguish them from surrounding text. Selected controls combine the accent surface, primary border and a check/selection indicator.

Status colors describe outcomes, not brand decoration. A successful payment does not independently mean a confirmed appointment or completed refund. Always name the relevant status in text. Do not apply reduced opacity to whole controls containing essential explanations.

### Contrast checks

Calculated sRGB contrast ratios for the proposed opaque pairs:

| Pair | Ratio |
| --- | --- |
| White / primary | 10.19:1 |
| Text / background | 14.50:1 |
| Muted text / background | 5.96:1 |
| Control border / white | 3.57:1 |
| Control border / background | 3.35:1 |
| Success foreground / its background | 6.18:1 |
| Error foreground / its background | 6.57:1 |
| Warning foreground / its background | 6.21:1 |
| Information foreground / its background | 6.58:1 |

These checks verify token pairs, not a rendered interface. Later prototype review must check actual text, focus, opacity, imagery, overlapping layers and component combinations.

## 2. Typography

Use [Vazirmatn](https://github.com/rastikerdar/vazirmatn) with a suitable Persian-capable sans-serif fallback. Use regular, medium and bold weights; avoid synthetic ornamentation and excessive weight changes.

| Role | Font size / line height | Weight |
| --- | --- | --- |
| Page title | 32 / 48 px; 28 / 42 px on narrow screens | Bold |
| Section title | 24 / 36 px | Bold |
| Card title / key price | 20 / 32 px | Medium or bold |
| Body and customer controls | 16 / 28 px | Regular; controls medium |
| Labels and supporting copy | 14 / 24 px | Medium labels; regular copy |
| Staff table/calendar supporting text | 14 / 24 px | Regular |

Keep essential prices, deadlines, errors and appointment details at least 14 px. Do not shrink text to fit long Persian content: wrap or expand the surface. Display amount and “تومان” together; separate final price, deposit and remaining balance by labels. Monetary and duration values remain readable without relying on font weight alone.

## 3. Spacing, layout and surfaces

- Spacing scale: 4, 8, 12, 16, 24, 32, 48 and 64 px. Use 8–12 within related controls, 16–24 within cards and 32–48 between sections.
- Page gutters: 16 px on narrow screens, 24 px on medium screens and 32 px on wide screens.
- Public content maximum width: 1200 px. Booking form maximum width: 680 px; a separate summary may sit beside it when there is enough room. Salon operations may use up to 1440 px.
- Use one booking column on narrow screens. Staff views can be denser, but must retain readable text and usable action targets.
- Control radius: 8 px; cards: 12 px; dialogs/drawers: 16 px. Reserve pill shapes for compact status badges and choice chips.
- Borders: 1 px. Use the control-border role for essential boundaries and decorative-divider role only for nonessential separation.
- Cards normally use borders rather than shadows. Elevated overlays may use a restrained shadow: 0 8px 24px rgba(39,35,39,0.12).
- Use intrinsic wrapping and available width to adapt components; avoid a fixed-width desktop layout squeezed onto mobile.
- Stage 13 will define page-level navigation changes, sticky actions and content priorities. This stage establishes reusable sizing and layout foundations.

## 4. Shared interaction states

| State | Presentation and behavior |
| --- | --- |
| Default | Clear label, readable content and visible control boundary where needed |
| Hover | Subtle color change on devices that support hover; no information available only on hover |
| Focus | Visible 2 px primary ring with a 2 px surface gap; check visibility on all adjacent backgrounds |
| Pressed | Darker primary or a restrained pressed surface; no disruptive movement |
| Selected | Primary border, soft-accent background and explicit check/selection semantics |
| Disabled | Disabled surface, understandable reason nearby, no misleading clickable styling |
| Loading | Keep the action label/context, add a small progress indicator, prevent duplicate submission |
| Error | Error text with an icon/field association and a specific recovery action |
| Success | State the actual completed operation; persistent outcomes remain in appointment detail |
| Pending / unknown | Explicit checking/pending label and status retrieval; never a success tick or known-failure message |

Ordinary feedback transitions may use 120–180 ms; drawer transitions up to 240 ms. Respect reduced-motion preferences. Never use animation or fake countdown resets to imply a verified booking/payment outcome.

## 5. Core components

| Component | Necessary variants and rules |
| --- | --- |
| Button | Primary, secondary, text and destructive; default/loading/disabled. Use one visually dominant action per task. Minimum 44 px interaction height. Destructive actions use explicit verbs, not a generic “OK”. |
| Text input | Label, value, optional help and field error. Labels stay visible. Required/optional status is explicit where unclear. Validate without clearing other fields. |
| Phone / SMS code input | Preserve booking context; phone/code content uses an LTR segment within the RTL form. Support paste and appropriate mobile input/autofill. Code length follows the authentication provider, not an invented design constraint. |
| Select / radio choice | Use visible options for a small consequential choice; use selects for longer lists. Show selected state, unavailable reasons and relevant duration/price changes. Keyboard and touch operation must work. |
| Checkbox | Use for a genuine independent choice or required acceptance; descriptive label, no preselected customer consent to a specialist change. |
| Card | Clear title, key information and appropriate action. Avoid nested clickable regions with ambiguous behavior. |
| Alert | Information, success, warning or error; heading when useful, concise explanation and recovery action. Inline/persistent for booking or payment consequences. |
| Toast | Brief secondary confirmation only. Do not use as the sole payment, cancellation, refund or validation feedback. |
| Dialog / drawer | Dialog for a focused consequential decision; drawer for contextual detail/editing. Visible heading/close action, managed keyboard focus and return focus on close. Safe dismissal preserves useful intent. Closing is never implied cancellation of a submitted payment. |
| Navigation | Reuse the approved public/customer/staff hierarchy. Active item has a visible indicator and label. Manager-only actions follow assigned access. |
| Status badge | Short text plus color and optional icon. Separate appointment, payment and refund badges rather than one combined ambiguous status. |
| Empty / error / loading panel | Distinguish no data, known fetch failure and loading. Include only a relevant next action; skeletons should match the expected content structure. |

Confirmations follow the approved critical/destructive flows; do not add a modal before every ordinary action.

## 6. Booking and salon components

| Component | Information and behavior |
| --- | --- |
| Service card | Service name, truthful image if available, fixed or approximate price wording, relevant duration/volume explanation and one booking/detail action. Consultation-only services use the approved contact path. |
| Specialist card / choice | Name, service eligibility and honest photo/fallback. Named specialist and “هر متخصص واجد شرایط” are available for customer and reception. Explain that the system selects by management priority among eligible, available specialists. |
| Volume choice | Show option, booking duration and price/deposit basis before selecting availability; changing the option rechecks dependent availability. |
| Date / time picker | Distinct available, selected and unavailable states. Show full local date and start time in the summary. Unavailable times cannot be submitted; stale selection shows a recovery message. Keyboard access is required. |
| Assigned specialist summary | Display the actual assigned name before payment/confirmation, including bookings using any eligible specialist. Do not present an unresolved generic specialist choice as a final assignment. |
| Booking summary | Service, volume/duration, assigned specialist, date/start time, contact, price type, deposit, policy and primary action. Approximate-price bookings clearly distinguish the deposit basis from the final price accepted before service. |
| Hold notice | Label the temporary reservation, show the actual remaining deadline and explain the next step. A started payment with unknown outcome may receive only the approved additional window. Reopening a link does not reset it. |
| Payment result panel | Separate verified success, known failure, checking and late success/refund. Preserve status retrieval and avoid inviting a second payment while the previous outcome remains unknown. |
| Appointment card / detail | Service, specialist, date/time and appointment state; show separate deposit/payment/refund information where relevant. Available actions follow the stored policy and deadline. |
| Replacement / rescheduling comparison | Clearly compare original and proposed appointment, including specialist/time changes and deposit handling. Require explicit acceptance where the approved flow requires it; keep the original until the replacement confirms. |
| Settlement panel | Show accepted final service price, paid deposit and remaining in-person balance. Do not label the deposit basis as a guaranteed final price for approximate-price services. |
| Salon calendar | One shared operational calendar for customer and reception bookings; visible date/time axis and specialist labels. Appointment bars represent the full reserved duration. Include service/customer identity appropriate to staff access, status and booking source in detail. |
| Calendar hold / conflict | Held entries differ from confirmed entries using text/pattern as well as color. Show overlapping/stale conflicts explicitly. Manager schedule edits cannot silently remove holds or change affected confirmed appointments. |

Calendar colors represent meaningful states; do not assign an arbitrary rainbow to specialists. On small screens use readable day/appointment-list presentations when a full grid cannot fit. Staff must be able to open an appointment without dragging; drag interactions must not bypass approved change/consent rules.

A volume mismatch at the salon does not permit moving the reserved start or extending duration. The settlement/change interface preserves this rule and the approved full-refund cancellation path when no solution fits.

## 7. RTL, icons and imagery

- Persian is the primary language and page direction is RTL. Use logical start/end placement for spacing, navigation and alignment.
- Mirror directional navigation arrows where appropriate; do not mirror brand marks, photographs or universally recognized nondirectional symbols.
- Keep phone numbers, verification codes and other inherently LTR values isolated so punctuation does not corrupt reading order. Visually and semantically retain the correct number.
- Use one consistent simple outline icon family. Essential actions need readable labels; icon-only controls require accessible names and sufficient target size.
- Service photos: stable 4:3 containers. Specialist portraits: 1:1 containers. Crop without distorting faces or making all cards depend on image availability.
- Prefer actual supplied salon/service/staff photographs. If using sample imagery, label it as illustrative and do not represent it as actual salon staff or evidence of real results.
- Missing image: neutral surface with a service symbol or initials; do not block booking. Decorative images have empty alternative text; informative images have concise relevant descriptions.
- Avoid text baked into images and invented ratings, endorsements or salon credentials.

## 8. Accessibility baseline and prototype review

Target readable text, keyboard-operable controls, visible focus, labels and non-color-only feedback. W3C guidance specifies at least 4.5:1 for normal text and 3:1 for large text, and 3:1 for essential non-text control/state information against adjacent colors: [text contrast](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html), [non-text contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).

Use a product target of at least 44 × 44 px for interactive touch areas, including small icons and calendar actions. This is our usability choice; it is not a claim that WCAG 2.2 AA universally requires 44 px. See [target-size guidance](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html).

During prototype review:

- Check keyboard ordering, focus visibility and return focus for overlays.
- Check text zoom, narrow screens and long Persian labels without loss of essential controls.
- Check form labels/error associations and readable status updates for assistive technologies; do not announce a countdown every second.
- Check selected/unavailable slots and held/confirmed appointments without color.
- Check that disabled, loading, unknown and known-failure states remain distinct.
- Check actual contrast on all used component combinations, not just foundation tokens.
- Check that customer/public and denser staff surfaces use the same visual system while preserving different information priorities.

Prototype demonstration does not prove production accessibility, secure role enforcement, verified payments or concurrent slot locking.

## 9. Review boundary

The proposed palette, type scale, dimensions and component rules await user approval. Brand direction and business rules remain approved. No separate token file is needed at this stage.

After approval, proceed to Stage 13 — Responsive & Content Direction. Application implementation remains outside Phase 01.
