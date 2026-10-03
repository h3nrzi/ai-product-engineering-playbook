# Responsive & Content Direction — Women’s Beauty Salon Booking

- Stage: 13 — Responsive & Content Direction
- Status: draft for user review
- Date: 2026-10-03
- Model: one physical women’s salon, Persian-language product for the Iranian market
- Basis: approved [information architecture](information-architecture.md), [page inventory](page-inventory.md), [UX states](ux-states.md) and [design system](design-system.md).

This document proposes device adaptations and interface language for the approved product. Business rules and customer rights remain as defined in the approved journeys and flows.

## 1. Device priorities

- Public discovery, customer booking and account: mobile first. Customers must complete discovery, SMS login, review/payment and appointment actions on a narrow screen.
- Reception and manager operations: desktop/tablet for the full calendar and longer configuration tasks; mobile remains usable for daily appointments, intake, follow-up and contextual actions.
- Use the same information hierarchy across devices. Adapt presentation rather than creating separate products or removing permitted actions on mobile.
- Keep the approved design-system dimensions and touch targets. Choose layout changes when content no longer fits, rather than relying on device names alone.
- Prototype review should include representative narrow (360 px), medium (768 px) and wide (1440 px) widths, plus text enlargement and long content. These are review samples, not exclusive supported widths.

## 2. Navigation and layout adaptations

| Surface | Narrow screens | Wider screens | Information retained |
| --- | --- | --- | --- |
| Public navigation | Compact header, visible booking action and labeled menu. Menu contains the approved destinations including “نوبت‌های من”. | Visible primary navigation and booking action where space allows. | Services, specialists, salon/contact and account access |
| Public discovery | Single-column service cards; short introduction before useful service/booking content. Specialist cards may use two columns only when labels fit. | Multi-column cards and balanced image/text sections. | Price type, eligibility and practical next action |
| Service / specialist detail | Key service information and booking/contact action before decorative content; images do not dominate the first screen. | Image and content may sit side by side. | Service/volume duration, price basis, supported specialist/service relationships |
| Booking steps | One main column; short progress label such as “انتخاب زمان”. A compact summary can expand without losing entered choices. | Form with adjacent summary when comfortably readable. | Actual specialist, duration, date/time and exact deposit before payment |
| Review / payment result | Full review immediately before action; outcome and recovery first on result screens. | Same hierarchy; summary and supporting policy may sit side by side. | Appointment/payment/refund state and actual deadlines |
| Customer appointments | Cards grouped by upcoming, pending/unconfirmed and history; refunds needing attention remain discoverable. | Cards or a readable list with more metadata. | Identity, time, state and relevant next action |
| Salon navigation | Labeled menu/drawer, current section title and accessible “نوبت جدید” action. | Persistent side navigation with manager-only sections by role. | Approved calendar/follow-up/management hierarchy |
| Salon calendar | Default readable day appointment list, date control and specialist filter. Optional grid only if usable; do not shrink a full multi-column calendar. | Time grid with specialist columns and full-duration appointment bars; list alternative remains available. | Holds, confirmed entries, source in detail, conflicts and full booked interval |
| Appointment detail | Full-width page or drawer with stacked sections and relevant actions. | Contextual drawer beside calendar where practical. | Customer/service/time, separate financial states and permitted operations |
| Management forms | Stacked labeled fields and grouped sections; conflict list links to affected bookings. | Wider grouped forms and tables. | Validation, conflicts, role restrictions and effect on new bookings |

Menus/overlays remain keyboard operable and return focus when closed. Filters can wrap or move into a labeled filter panel; the currently applied selection stays visible. Do not hide a filter state inside an unlabeled icon.

## 3. Primary actions and density

- Public service detail may show a compact sticky booking/contact action after the main action scrolls out of view.
- Booking steps may use a bottom action area on narrow screens. Final review uses “پرداخت بیعانه” with the exact amount nearby. Review information and accepted terms must remain accessible before submitting.
- Reserve enough bottom space so a sticky action never covers the last field, error, policy or summary. Adapt to the on-screen keyboard and safe areas; avoid stacking a sticky navigation bar and sticky booking bar.
- A sticky action is a second presentation of the same action/state, not another submission path. Loading and disabled states remain synchronized.
- Payment uncertainty shows checking/status retrieval instead of an enabled second-payment action.
- Staff calendar/detail can be denser than public pages. Keep readable labels and touch targets; use a secondary action menu for less frequent operations with explicit labels.
- Do not make critical cancellation, refund or replacement consequences depend on horizontally scrolling a table. On narrow screens show these in detail/cards.
- Essential information must survive text enlargement. Wrapping or deliberate local grid scrolling is preferable to shrinking all text.

## 4. Voice and content hierarchy

Tone: clear, respectful, calm and direct Persian. Use natural wording, short sentences and a consistent respectful form. Avoid slang in consequential messages, exaggerated luxury claims, blame and technical provider terminology.

For task screens, show:
1. What the user is choosing or what happened.
2. The relevant service/specialist/time, amount or deadline.
3. The practical consequence.
4. The next action.

Errors say what needs correction and how to continue. Unknown outcomes say what is being checked. Do not claim success from a button click, redirect, screenshot or SMS delivery alone.

Use “نوبت” for the appointment, and qualify temporary reservation explicitly. Avoid “رزرو موفق” for a temporary hold or an uncertain payment. Keep salon communication separate from guaranteed system outcomes.

## 5. Canonical terminology and actions

| Concept | Persian label / copy rule |
| --- | --- |
| Book an appointment | “رزرو نوبت” |
| Named specialist | “متخصص مشخص” |
| Any eligible specialist | “هر متخصص واجد شرایط” with help: “از میان متخصص‌های این خدمت که در زمان انتخابی آزادند، بر اساس اولویت سالن انتخاب می‌شود.” |
| Assigned specialist | “متخصص نوبت شما” followed by the actual name before payment/confirmation |
| Deposit | “بیعانه” (not the misspelling “بیانیه”) |
| Fixed price | “قیمت نهایی” only for a genuinely fixed-price service |
| Approximate-price basis | “قیمت تقریبی برای حجم انتخابی”; explain final price is accepted before service begins |
| Remaining in-person balance | “باقی‌مانده قابل پرداخت در سالن” after final price is known |
| Temporary hold | “زمان موقتاً برای شما نگه داشته شده است” plus actual remaining deadline |
| Confirmed appointment | “نوبت تأییدشده” |
| Payment unknown | “در حال بررسی پرداخت” |
| Refund | “بازپرداخت بیعانه”; distinguish pending from completed |
| Reschedule | “تغییر زمان نوبت” |
| Cancellation | “لغو نوبت” |
| Salon replacement | “پیشنهاد تغییر نوبت”; clearly compare original and proposal |
| Account | “نوبت‌های من” and “اطلاعات من” |
| Staff sections | “تقویم نوبت‌ها”، “پیگیری‌ها”، “خدمات”، “متخصص‌ها”، “برنامه کاری”، “تنظیمات رزرو”، “دسترسی کارکنان” |

Action labels describe the result: “انتخاب زمان”، “ادامه”، “پرداخت بیعانه”، “بررسی وضعیت پرداخت”، “پذیرش تغییر”، “رد پیشنهاد”، “لغو نوبت” and “حفظ نوبت”. Do not use generic “تأیید” where it obscures a payment, cancellation or specialist change.

## 6. Sample consequential messages

These are reusable copy patterns, populated with actual booking state and saved terms.

| Context | Sample copy |
| --- | --- |
| Selected slot, before hold | “این زمان هنوز برای شما نگه داشته نشده است. هنگام پرداخت، آزاد بودن آن دوباره بررسی می‌شود.” |
| Hold active | “این زمان تا ساعت {deadline} موقتاً برای شما نگه داشته شده است. برای تأیید نوبت، بیعانه را پرداخت کنید.” |
| Unknown payment, held | “در حال بررسی پرداخت هستیم. زمان نوبت تا ساعت {verificationDeadline} برای شما نگه داشته شده است.” Only use the deadline that actually applies. |
| Unknown payment, released | “زمان نوبت آزاد شده است؛ نتیجه پرداخت هنوز در حال بررسی است.” |
| Definite payment failure | “پرداخت انجام نشد و نوبت تأیید نشده است. برای رزرو دوباره، زمان‌های آزاد را بررسی کنید.” |
| Verified confirmation | “نوبت شما تأیید شد.” Follow with service, actual specialist, date/time and deposit. |
| Late verified success | “پرداخت دریافت شد، اما نوبت تأیید نشد. بیعانه کامل بازگردانده می‌شود.” Show actual refund progress separately. |
| Slot conflict | “این زمان دیگر آزاد نیست. لطفاً زمان دیگری انتخاب کنید.” |
| Cancellation with full refund | “با لغو این نوبت، بیعانه کامل بازگردانده می‌شود.” Show the applicable saved cutoff and exact amount. |
| Cancellation after cutoff | “مهلت لغو با بازپرداخت گذشته است. با لغو نوبت، بیعانه بازگردانده نمی‌شود.” Show the applicable cutoff and “حفظ نوبت” alternative. |
| Refund pending | “بازپرداخت بیعانه در حال پیگیری است.” Do not invent a completion date. |
| Refund completed | “بیعانه بازگردانده شد.” Only after the actual return is verified/documented. |
| SMS delivery failed | “پیامک ارسال نشد؛ وضعیت نوبت تغییری نکرده است.” Staff can retry the relevant notice/link under its existing deadline. |
| No available times | “برای این انتخاب در این تاریخ وقت آزاد نداریم.” Offer another date or customer-chosen specialist change. |
| Data read failed | “دریافت اطلاعات ممکن نشد. دوباره تلاش کنید.” Do not present an empty list. |

For original appointment changes, explicitly disclose specialist changes and require the approved customer acceptance. Silence is never phrased as acceptance. A volume mismatch at the salon does not produce copy promising an extended or moved appointment.

## 7. Persian localization and formats

Proposed product presentation:
- Persian language and RTL interface; Vazirmatn as approved.
- Display dates in the Solar Hijri calendar, with weekday and month name in key summaries (for example “پنجشنبه ۱۶ مهر ۱۴۰۵”). Date values must be converted consistently; avoid mixing calendars without labels.
- Use 24-hour time and state “به وقت تهران” where needed in review, deadlines and cross-device ambiguity. The salon’s Tehran time governs displayed appointment/deadline meaning, not a device’s unrelated zone.
- Use Persian digits for human-readable dates, times and amounts. Phone/code entry accepts both Persian and Latin digits and displays an unambiguous value; preserve leading zeroes.
- Currency is toman, labeled “تومان”, with readable digit grouping. Do not silently switch display units to rial. Provider-unit handling remains engineering work.
- Use explicit dates/deadlines for consequential actions; “امروز” and “فردا” may supplement, but never replace the exact date in final review or cancellation terms.
- Isolate phone numbers, codes, references and other LTR content within the RTL layout. Do not reverse their character order.
- Use Persian characters consistently and sensible half-spaces. Keep service/specialist names as configured, without rewriting real identities.
- Saved booking policy values drive copy. Do not hardcode 20%, 24 hours or 10 minutes into reusable messages when management may configure new-booking terms.

## 8. Realistic content, long values and missing data

- Prototype content should cover fixed-price, approximate-price/volume and consultation-required services, with coherent eligibility, duration, price/deposit and calendar examples.
- Label the environment and invented salon/service/staff examples as demo content. No fabricated ratings, actual credentials, address, contact number or photographic proof of results.
- Demonstrate the accepted deposit example: final fixed price ۱٬۰۰۰٬۰۰۰ تومان, 20% deposit ۲۰۰٬۰۰۰ تومان, in-salon balance ۸۰۰٬۰۰۰ تومان. Approximate-price examples must label their basis and final settlement separately.
- Ensure displayed amounts, summaries, deposit calculation and calendar duration agree. Use valid full-duration availability; do not create contradictory fake samples.
- Use real Persian task copy rather than lorem ipsum. Pending, failure and refund examples stay clearly simulated in the prototype.
- Wrap long names, policy text and errors. Cards may show a shortened description with a detail link, but never truncate the actual specialist identity, time, monetary consequence or required acceptance.
- Missing optional images/biography use the approved neutral fallback or omit the optional section. Missing required customer name/contact requests those fields.
- Missing or invalid required service price/duration/eligibility prevents a bookable demonstration rather than substituting an invented value.
- Before launch, unverified operational details need real salon configuration. The prototype must not present fake address/contact/working hours as verified facts.

## 9. Review and completion boundary

Review the draft for mobile booking clarity, readable salon operations, terminology, Solar Hijri/Tehran-time presentation and truthful payment/refund language. On the prototype, verify narrow/wide layouts, long Persian text, the mobile keyboard, sticky-action clearance, menu/focus behavior and coherent demo data.

Stage 13 remains in progress until user approval. After approval, proceed to Stage 14 — PRD, consolidating approved decisions rather than reopening discovery. No application implementation is part of this stage.
