# Brand & Visual Direction — Women’s Beauty Salon Booking

## Status and inputs

Stage 11 approved and completed on 2026-10-03. The user confirmed that no existing salon name/logo/colors need to be preserved, authorized inspiration from Dribbble, and accepted the proposed calm, warm, refined and professional direction. No new salon name or final logo is invented.

Basis: [approved information architecture](information-architecture.md), [page inventory](page-inventory.md), [UX states](ux-states.md), and [Stage 05 research](ux-research.md). Dribbble examples inform visual mood; they do not validate booking behavior or override approved product scope. Stage 12 turns an approved direction into semantic tokens and component rules.

## Proposed personality and intended perception

- **Calm:** choosing a service/time and understanding payment terms should feel unhurried.
- **Professional:** prices, specialist identity, duration and current booking state are clear.
- **Warm:** inviting photography and soft neutral surfaces without relying on gender stereotypes.
- **Refined:** restrained detail, balanced spacing and one strong action color.
- **Honest:** approximate prices, unavailable times and pending payment/refund states are explicit.

Desired customer perception: “This salon is considered and professional; I can understand the choices and trust the status of my booking.” Desired staff perception: “I can scan today's schedule quickly and resolve the exact appointment issue.”

These are intended design effects, not findings from user research.

## Positioning

Prefer minimal, warm and refined over highly decorative or ostentatiously luxurious. Use a welcoming customer presentation with room for service/specialist photography; make booking and account screens quieter and more task-focused.

Salon operations share the same typography and primary color but use denser neutral layouts, clear time columns and status labels. Reception speed and legibility outrank marketing decoration. A separate brand for the staff area is unnecessary.

## Inspiration references and adaptation

Reviewed public descriptions and published palettes on 2026-10-03; these concept pages are visual inspiration, not usability or production evidence. No claim is made that their full booking flows were tested.

| Reference | Published reference direction | Proposed adaptation for this product |
| --- | --- | --- |
| [Beauty Salon One-Page Website Design — CodePulseWorks](https://dribbble.com/shots/26644839-Beauty-Salon-One-Page-Website-Design) | Describes a minimalist palette; published neutral, warm beige and brown colors | Warm neutral ground and a restrained prominent booking action; retain our approved multi-surface architecture rather than a one-page-only product |
| [Elegant Beauty Salon Website Concept — Hanna Yereshchenko](https://dribbble.com/shots/26029114-Elegant-Beauty-Salon-Website-Concept) | Publishes gray/warm brown tones and describes an elegant service/pricing/booking presentation | Refined service discovery and truthful pricing hierarchy; do not import galleries/testimonials or unsupported trust claims as new MVP requirements |
| [Salon Booking Flow — Mobile UI — Vikky / Lu-lu-loom](https://dribbble.com/shots/27583590-Salon-Booking-Flow-Mobile-UI) | Describes a calmer pastel booking concept and publishes soft rose/pink/brown tones | Soft secondary accent for selected contexts; use solid legible surfaces instead of glass effects behind essential price/time/payment information |

The actual proposed palette, Persian typography and operational density are project decisions. Do not copy layouts, logos, images, ratings, marketplace navigation or unrelated features. The prior Fresha research remains a booking-layout reference; these Dribbble references add visual mood.

## Proposed color direction

A light presentation with warm ivory, white surfaces, deep plum for primary actions, and pale rose used sparingly. These are candidate anchors, not the final semantic token set.

| Role/direction | Candidate | Use |
| --- | --- | --- |
| Warm ivory ground | #FAF7F3 | Public/customer background; restrained staff background |
| Clear surface | #FFFFFF | Forms, booking summary and operational content surfaces |
| Deep plum primary | #5E3448 | Main booking/payment action, active emphasis, focus direction |
| Pale rose accent | #EEDCE2 | Subtle selected/summary background and small decorative accents |
| Dark neutral text | #272327 | Titles, essential body text, prices and time |
| Muted readable text | #655D63 | Secondary descriptions and metadata |
| Quiet neutral divider | #E5DDD8 | Decorative separation; controls requiring visible boundaries need stronger contrast |

Computed contrast checks for candidate pairs: white on plum about 10.19:1; dark text on ivory about 14.50:1; muted text on ivory about 5.96:1; plum on pale rose about 7.75:1. These checks cover those pairs only, not a completed accessible interface. Stage 12 must check actual component states, controls and focus contrast.

Semantic success, warning, pending/info and error colors remain separate from the brand accent. Status always includes text/icon, not color alone. Do not use pale rose text on white for essential content. Dark mode is not added as a Stage 11 requirement.

## Typography direction

Proposed UI family: [Vazirmatn](https://github.com/rastikerdar/vazirmatn), whose official repository describes a Persian/Arabic typeface intended for readable web/app use. Use one coherent Persian family across public, booking and operations screens; readable system fallback must keep the product usable if the font is unavailable.

- Regular body text; medium emphasis for controls/metadata; semibold/bold for hierarchy.
- Avoid calligraphic/display fonts for forms, prices, deadlines and calendar labels.
- Spacious Persian line height and wrapping; no letter-spacing effects that disrupt connected Persian script.
- Use weight/size/spacing hierarchy instead of excessive competing font families.
- Keep phone/code fields and financial/date values readable and unambiguous. Final digit/date conventions and exact type scale follow Stages 12–13.
- More expressive public headlines may use the same family at larger sizes; booking/status screens prioritize compact clarity.

No font package version or technical delivery mechanism is selected here.

## Imagery direction

Prefer real, authorized salon and specialist photography when supplied: natural light, believable service context, consistent crop/color balance and professional presentation. Service imagery supports understanding rather than implying guaranteed cosmetic results.

Without salon assets, prototype imagery must be clearly illustrative/demo material and never passed off as this salon's actual staff, premises or work. Do not invent ratings, client testimonials, before/after evidence, certifications or claims to fill space. Text-first fallbacks must remain useful.

Use photography mainly in discovery/service/specialist surfaces. Keep login, review, payment/result and staff calendar free of competing hero imagery. Large images must not push the service choice or booking action out of practical reach.

## Shape, layout and elevation

- Moderately rounded controls and bounded content; reserve pill treatment for compact chips/status where useful.
- Light dividers and minimal shadow. Avoid heavy outlines, nested decorative cards and translucent panels for critical information.
- Customer discovery can use generous spacing and a balanced photo/text composition. Booking stays single-column and step-based on small screens, with a clear selected summary.
- Calendar and staff tables use tighter but readable spacing, aligned time/data and distinguishable booked/held/status cues.
- Keep named/any-eligible choices, selected times and prices visibly distinct without turning every item into a different colored card.
- One clear primary action per task. Destructive and exception actions remain visually distinct and reviewed.
- RTL hierarchy applies throughout; the public visual style does not justify reversing approved step order or hiding important category/navigation options.

Exact radii, spacing, control sizing and component layout rules belong to Stage 12.

## Motion direction

Use short, purposeful feedback for step changes, selection, loading and outcome updates. Motion must not delay booking actions or conceal a changed status. Avoid looping background animation, parallax-heavy hero sections, decorative animated cursors and celebration effects around uncertain payments.

Honor reduced-motion preferences. Timer updates remain readable without flashing or constantly interrupting assistive announcements. Exact motion values follow the design system.

## Patterns to avoid

- Saturated pink everywhere, rose-gold/glitter or black-and-gold styling used as a substitute for a clear identity.
- Glass effects or low-contrast pastel text behind dates, prices, form input or payment outcomes.
- Oversized decorative headlines that bury service selection or booking.
- Generic dashboard charts, animated counters or unsupported “best salon”/rating claims.
- Different visual languages for every page or an ornamental reception calendar.
- Competitor marketplace/filter/reward patterns that add unapproved features.
- Using success styling for pending payment or implying cancellation means money has already returned.

## Approved direction and completion

Approved direction: warm, calm and professional; ivory/white surfaces, deep-plum primary, pale-rose accent, Vazirmatn and honest photography, with moderately rounded shapes, restrained shadows and purposeful short motion. This establishes the project's visual mood; final tokens/components follow in Stage 12.

The salon name/logo and real media can be supplied later without being invented in this stage. Any later identity should be reconciled with the approved direction before changing the design system. Stage 11 is complete; proceed to Stage 12 — Design System to define semantic tokens, foundations, components, variants and interaction/accessibility states.
