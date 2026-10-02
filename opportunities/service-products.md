# Service Product Opportunity Library

This is the portfolio-level catalog of **service-product families and their viable product models**.

The catalog is designed to be archetype-complete rather than limited to a short backlog. A very narrow niche should normally map to one of these product families as a model/vertical variant; genuinely new service archetypes can still be added later.

Before Phase 01 starts, select **two things**:

1. a **Product Family** from this library;
2. a **Product Model / Variant** for that family.

Example:

```text
Product Family: BEAUTY-SALON — Barbershop / Beauty Salon Booking
Selected Model: Women’s single-salon
```

Do not enter Phase 01 with only a broad family such as “salon”, “healthcare”, or “home services” when materially different models still exist.

## Iran demand ordering

The catalog is sorted by estimated demand for the **underlying service in Iran**, from `D5` to `D0`.

- `D5` — very high / mass-market
- `D4` — high
- `D3` — medium / established
- `D2` — low / niche
- `D1` — very low / emerging
- `D0` — no meaningful Iranian demand validated in the current research snapshot

Digital maturity is tracked separately:

- `M5` — mainstream digital market
- `M4` — strong digital market
- `M3` — emerging/credible digital market
- `M2` — limited digital market
- `M1` — mostly offline
- `M0` — no meaningful local digital model validated

See [`iran-demand-methodology.md`](iran-demand-methodology.md) for the methodology, evidence signals, sources, and caveats.

> Demand tiers are directional portfolio-research labels, not audited market-size estimates. Ordering inside the same tier is approximate.

## Opportunity status

`candidate | selected | in-progress | completed | deferred`

Status belongs to the **product family in the portfolio**. The project tracker records the exact model selected for a real implementation.

---

# Service Product Catalog

| Stable ID | Product family | Category | Iran demand | Digital maturity | Common product models / variants | Core workflow | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| MOBILITY-RIDE | Ride-hailing / Taxi | Mobility | D5 | M5 | open driver marketplace; managed drivers; women-only ride; corporate rides; intercity ride; fixed fleet | request → match → pickup → trip → payment | candidate |
| FOOD-DELIVERY | Restaurant Ordering & Food Delivery | Food / local commerce | D5 | M5 | restaurant-direct; multi-restaurant marketplace; pickup-only; cloud-kitchen marketplace; corporate meals; scheduled delivery | discover → order → dispatch → delivery | candidate |
| HEALTH-DOCTOR | Doctor Appointment & Telemedicine | Healthcare | D5 | M5 | single clinic; hospital scheduling; multi-clinic network; doctor marketplace; telemedicine-only; hybrid | need → provider → slot → consultation | candidate |
| HOME-MARKETPLACE | Home Services Marketplace | Home services | D5 | M4 | lead marketplace; managed marketplace; instant fixed-price; quote-first; subscription home-care; B2B facilities | request → match/quote → service → completion | candidate |
| HOME-PLUMBING | Plumbing & Emergency Home Service | Home services | D5 | M4 | single company; technician marketplace; emergency dispatch; scheduled service; maintenance subscription | issue → urgency → dispatch/schedule → resolution | candidate |
| HOME-ELECTRICAL | Electrician / Building Electrical Service | Home services | D5 | M4 | single contractor; technician marketplace; emergency callout; project quote; building contract | issue → triage → quote/schedule → service | candidate |
| HOME-HVAC | Cooling / Heating / HVAC Service | Home services | D5 | M4 | AC repair; evaporative-cooler service; boiler/package service; seasonal maintenance; technician marketplace; B2B contract | asset → issue/maintenance → technician → resolution | candidate |
| HOME-APPLIANCE | Appliance Repair | Repair | D5 | M4 | brand-authorized; independent technician; marketplace; in-home repair; pickup/workshop repair; warranty service | appliance → diagnose request → visit/quote → repair | candidate |
| HOME-CLEANING | Home & Office Cleaning | Home services | D5 | M4 | one-time home cleaning; recurring subscription; office contract; deep cleaning; move-in/out; managed cleaner marketplace | scope → quote → schedule → repeat/manage | candidate |
| LOGISTICS-MOVING | Moving / Household Relocation | Logistics | D5 | M4 | truck-only; full-service moving; labor-only; quote marketplace; managed mover; office relocation | inventory → quote → schedule → coordinate move | candidate |
| AUTO-REPAIR | Auto Repair Workshop | Automotive | D5 | M4 | single workshop; workshop chain; repair marketplace; pickup/drop-off; specialist shop; fleet workshop | issue → intake → inspection → approval → repair tracking | candidate |
| AUTO-QUICK | Tire / Battery / Quick Auto Service | Automotive | D5 | M4 | shop appointment; mobile battery; mobile tire; roadside dispatch; chain marketplace; fleet plan | vehicle → need → fit/availability → service | candidate |
| TRAVEL-TICKETS | Travel Ticket Booking | Travel | D5 | M5 | flight OTA; train booking; bus booking; multimodal aggregator; corporate travel; charter/deal marketplace | search → compare → book → manage/refund | candidate |
| TRAVEL-STAY | Hotel & Accommodation Booking | Travel | D5 | M5 | hotel OTA; villa marketplace; eco-lodge marketplace; hotel-direct; corporate stays; long-stay | destination → availability → booking → stay management | candidate |
| EDU-TUTOR | Private Tutoring | Education | D5 | M4 | tutor marketplace; managed matching; online-only; in-person; subject specialist; package/subscription | subject/goal → tutor fit → schedule → recurring lessons | candidate |
| HEALTH-DENTAL | Dental Clinic Appointment | Healthcare | D5 | M4 | single clinic; multi-branch; dentist marketplace; emergency dental; cosmetic dental; treatment-plan follow-up | need → provider → slot → visit/treatment plan | candidate |
| TECH-DEVICE-REPAIR | Mobile / Computer Repair | Technology services | D5 | M4 | walk-in shop; pickup/delivery; technician marketplace; on-site repair; brand-authorized; B2B fleet | device → issue → quote → repair → return | candidate |
| PROPERTY-AGENT | Real Estate Agent / Property Brokerage | Property | D5 | M4 | single agency; multi-agency marketplace; owner-direct; rental-focused; sales-focused; managed broker | discover → inquire → viewing → negotiation/application | candidate |
| LOGISTICS-FREIGHT | Freight / Cargo Transport | Logistics / B2B | D5 | M4 | truck marketplace; broker/forwarder; scheduled route; city freight; B2B contract; partial-load | shipment → quote/match → pickup → track → proof | candidate |
| HEALTH-PHARMACY | Pharmacy & Prescription Fulfillment | Healthcare / delivery | D5 | M4 | pharmacy-direct; pharmacy marketplace; prescription upload; recurring medication; same-day delivery; pickup | prescription/need → pharmacy → fulfill → delivery/pickup | candidate |
| BEAUTY-SALON | Barbershop / Beauty Salon Booking | Beauty / personal care | D5 | M3 | men’s single barbershop; women’s single salon; unisex salon; specialist studio; multi-branch salon; salon marketplace; at-home beauty | discover → service/specialist → schedule → manage appointment | in-progress |
| AUTO-WASH | Car Wash & Detailing | Automotive | D4 | M3 | fixed car wash; mobile wash; detailing studio; wash subscription; marketplace; fleet washing | vehicle/package → location → schedule → service | candidate |
| AUTO-ROADSIDE | Roadside Assistance & Towing | Automotive emergency | D4 | M4 | towing dispatch; roadside membership; insurer-connected; marketplace dispatch; battery/tire-only; heavy vehicle | incident → location → dispatch → arrival → resolution | candidate |
| HOME-RENOVATION | Renovation / General Contractor | Home / construction | D4 | M3 | general contractor; contractor marketplace; room-specific renovation; design-build; managed project; B2B fit-out | brief → site visit → quote → project → milestones | candidate |
| HOME-PAINT | Painting / Wall Finishing | Home services | D4 | M3 | painter marketplace; fixed package; quote-first; commercial contract; decorative specialist | scope → estimate → schedule → completion | candidate |
| HOME-CARPENTRY | Carpentry / Cabinets / Furniture Build | Home services | D4 | M3 | custom cabinet; carpenter marketplace; repair-only; design-build; modular install; B2B shopfit | measure → design/quote → build → install | candidate |
| HOME-LOCKSMITH | Locksmith / Door Service | Home emergency | D4 | M3 | emergency dispatch; scheduled lock change; smart-lock install; automotive locksmith; B2B access | issue → location → dispatch → service | candidate |
| HOME-PEST | Pest Control | Home services | D4 | M3 | one-time treatment; subscription; residential; commercial; specialist pest; marketplace | problem → assessment → treatment → follow-up | candidate |
| HOME-CCTV | Security / CCTV / Smart-Home Installation | Home services | D4 | M3 | CCTV install; alarm install; smart-home setup; maintenance contract; marketplace; B2B systems | site need → survey → quote → install → support | candidate |
| HOME-ELEVATOR | Elevator Maintenance & Repair | Building services | D4 | M3 | building contract; emergency repair; inspection/maintenance; installer; parts/service company | asset → maintenance/issue → technician → report | candidate |
| LOGISTICS-COURIER | Courier / Local Delivery | Logistics | D4 | M5 | on-demand bike courier; car courier; scheduled delivery; business API; document courier; same-day marketplace | pickup → quote → dispatch → track → proof | candidate |
| LAUNDRY | Laundry / Dry Cleaning | Local services | D4 | M3 | walk-in; pickup/delivery; subscription; B2B laundry; specialty garment; marketplace | order → pickup/drop-off → process → return | candidate |
| EVENT-WEDDING | Wedding / Event Planning | Events | D4 | M3 | full-service planner; day-of coordinator; vendor marketplace; package planner; corporate event; wedding-only | brief → consultation → proposal → milestones | candidate |
| EVENT-CATERING | Catering Service | Events / food | D4 | M3 | event catering; corporate meals; wedding catering; chef marketplace; menu configurator; drop-off catering | event details → menu → quote → confirm → fulfill | candidate |
| EVENT-VENUE | Venue / Hall / Studio Rental | Events / resource booking | D4 | M4 | wedding hall; meeting room; photo studio; event-space marketplace; hourly rental; package venue | requirements → availability → book → access | candidate |
| CREATIVE-PHOTO | Photography / Videography Service | Creative services | D4 | M3 | wedding studio; portrait studio; freelancer marketplace; commercial; event; package booking | occasion/brief → portfolio → package → availability → delivery | candidate |
| EDU-LANGUAGE | Language School / Private Language Lessons | Education | D4 | M4 | school cohorts; private tutor; online; hybrid; exam prep; conversation subscription | level → course/tutor → schedule → enrollment | candidate |
| EDU-TESTPREP | Exam / Entrance-Test Preparation | Education | D4 | M4 | 1:1 tutor; cohort course; online subscription; mock-test service; counseling+plan; hybrid institute | goal → assessment → plan/course → progress | candidate |
| EDU-DRIVING | Driving School | Education | D4 | M3 | school package; instructor marketplace; women-only instructor option; theory+practice; lesson credits; resource scheduling | package → instructor/car → lessons → progress | candidate |
| EDU-VOCATIONAL | Vocational / Skills Training | Education | D4 | M3 | institute cohorts; instructor marketplace; workshop booking; apprenticeship matching; online/hybrid; certification prep | skill goal → course → schedule → completion | candidate |
| CARE-ELDER | Elderly Home Care | Care services | D4 | M3 | hourly caregiver; live-in caregiver; managed agency; recurring schedule; family dashboard; nurse+care hybrid | care need → caregiver → schedule → family visibility | candidate |
| HEALTH-HOME | Doctor / Nurse / Clinical Service at Home | Healthcare | D4 | M4 | doctor visit; nursing procedures; injection/IV; lab sampling; physiotherapy; managed home-care network | need → clinical service → schedule/dispatch → follow-up | candidate |
| HEALTH-PHYSIO | Physiotherapy / Rehabilitation | Healthcare | D4 | M4 | clinic booking; home physiotherapy; practitioner marketplace; multi-session plan; sports rehab; package | need → practitioner → session series → follow-up | candidate |
| HEALTH-AESTHETIC | Aesthetic / Dermatology Clinic Booking | Healthcare / beauty | D4 | M3 | single clinic; multi-branch; doctor marketplace; treatment consultation; packages; follow-up | concern → treatment/provider → consultation → sessions | candidate |
| BEAUTY-BRIDAL | Bridal Beauty Services | Beauty | D4 | M3 | single-salon package; specialist marketplace; freelance makeup artist; at-home; trial+event; team booking | event → style/provider → trial → booking → event | candidate |
| PRO-LEGAL | Legal Consultation / Lawyer Service | Professional services | D4 | M3 | law-firm booking; lawyer marketplace; paid call/chat; case intake; document review; SME subscription | matter → intake → lawyer fit → consultation/case | candidate |
| PRO-ACCOUNTING | Accounting / Tax Service | Professional services | D4 | M3 | individual tax; SME bookkeeping; accountant marketplace; monthly subscription; document workflow; payroll add-on | need → document intake → service → status/filing | candidate |
| PRO-IMMIGRATION | Visa / Immigration Service | Professional services | D4 | M3 | consultancy firm; consultant marketplace; case workflow; document-only; study migration; work migration | case type → intake → documents → milestones | candidate |
| B2B-RECRUIT | Recruitment / Staffing Service | B2B / HR | D4 | M4 | job marketplace; recruitment agency; temporary staffing; executive search; blue-collar staffing; managed hiring | role/need → candidates → screening → placement | candidate |
| PROPERTY-MAINT | Property / Building Maintenance | Property operations | D4 | M3 | residential building; commercial facility; tenant portal; vendor marketplace; subscription; managed service | issue → triage → vendor → track → completion | candidate |
| PROPERTY-MGMT | Property Management | Property | D4 | M3 | rental management; condominium management; landlord portal; short-term rental management; commercial property | property/tenant → requests/payments → maintenance → reporting | candidate |
| TRAVEL-TOUR | Tour / Package Travel Booking | Travel | D4 | M4 | domestic; outbound; pilgrimage; adventure; group; customized package | destination/theme → dates → package → booking | candidate |
| TRAVEL-VISA | Travel Visa / Document Assistance | Travel / professional | D4 | M3 | agency-managed; document checklist; appointment support; multi-country marketplace; corporate visa; concierge | destination/case → requirements → documents → status | candidate |
| TRAVEL-CAR | Car Rental | Mobility / rental | D4 | M4 | rental company; multi-company marketplace; chauffeur-driven; airport rental; monthly; luxury | vehicle/date → availability → reserve → pickup/return | candidate |
| TRAVEL-PILGRIMAGE | Pilgrimage Travel Service | Travel | D4 | M3 | group pilgrimage; hotel+transport package; guide-led; organization-managed; family package | destination/date → package → registration → trip | candidate |
| AUTO-BODY | Body Shop / Paint / Collision Repair | Automotive | D4 | M3 | single shop; insurer referral; quote marketplace; pickup/drop-off; cosmetic repair; fleet service | damage → estimate → approval → repair → handoff | candidate |
| AUTO-INSPECT | Vehicle Inspection / Pre-Purchase Check | Automotive | D4 | M3 | inspection center; mobile inspector; marketplace; dealership B2B; report-only; premium diagnostic | vehicle → schedule/location → inspection → report | candidate |
| AUTO-MOBILE-MECH | Mobile Mechanic | Automotive | D4 | M3 | on-demand dispatch; scheduled mobile service; mechanic marketplace; fleet mobile service; emergency-only | issue → location → mechanic → diagnose/fix | candidate |
| HOME-FURNITURE | Furniture Repair / Upholstery | Home services | D4 | M3 | pickup workshop; on-site; marketplace; custom restoration; B2B furniture maintenance | item → assessment → quote → repair → return | candidate |
| B2B-WAREHOUSE | Warehousing / Fulfillment Service | Logistics / B2B | D4 | M4 | 3PL; storage-only; ecommerce fulfillment; cold chain; cross-dock; shared warehouse | inventory → inbound → store/pick-pack → dispatch | candidate |
| B2B-CUSTOMS | Customs / Freight Forwarding Service | Logistics / B2B | D4 | M3 | customs broker; freight forwarder; import concierge; export documentation; multimodal forwarder | shipment → documents/quote → clearance → delivery | candidate |
| FITNESS-GYM | Gym / Fitness Class Booking | Fitness | D3 | M4 | single gym; multi-branch; class booking; trainer marketplace; pay-per-class; corporate fitness | membership/goal → class/trainer → schedule → attendance | candidate |
| FITNESS-TRAINER | Personal Trainer / Fitness Coaching | Fitness | D3 | M3 | in-gym trainer; marketplace; online coach; home trainer; session packages; hybrid plan+sessions | goal → coach fit → plan/sessions → progress | candidate |
| HEALTH-MENTAL | Mental Wellness / Counseling Booking | Healthcare / wellness | D3 | M4 | clinic; therapist marketplace; online-only; in-person; couples/family; employer program | need → therapist fit → schedule → session continuity | candidate |
| HEALTH-NUTRITION | Nutritionist / Dietitian Service | Healthcare / wellness | D3 | M3 | clinic; online consult; diet-plan subscription; sports nutrition; condition-specific; marketplace | goal/context → practitioner → consultation → follow-up | candidate |
| HEALTH-DIAGNOSTIC | Lab / Imaging Appointment | Healthcare | D3 | M3 | lab booking; home sampling; imaging center; multi-center marketplace; corporate screening; checkup package | test/order → center/time → preparation → result | candidate |
| HEALTH-OPTICAL | Optometry / Optical Service | Healthcare / retail service | D3 | M3 | optometrist appointment; optical-shop exam; home eye test; marketplace; contact-lens follow-up | need → exam/provider → appointment → prescription | candidate |
| HEALTH-THERAPY | Speech / Occupational Therapy | Healthcare | D3 | M3 | clinic; home visit; therapist marketplace; child-focused; multi-session; teletherapy | need → therapist → assessment → session series | candidate |
| CARE-CHILD | Babysitting / Nanny Service | Care services | D3 | M2 | hourly sitter; nanny placement; managed agency; recurring after-school; event babysitting; live-in nanny | care need → caregiver trust/fit → schedule → handoff | candidate |
| CARE-DISABILITY | Disability Support / Personal Assistance | Care services | D3 | M2 | hourly support; recurring caregiver; transport assistance; respite care; agency-managed; family dashboard | support need → caregiver → schedule → visit reporting | candidate |
| PET-VET | Veterinary Appointment | Pet services | D3 | M3 | clinic; vet marketplace; emergency discovery; mobile vet; vaccination plan; tele-vet triage | pet context → provider → appointment → follow-up | candidate |
| PET-BOARD | Pet Boarding / Daycare | Pet services | D3 | M2 | kennel; home-boarding marketplace; daycare; cat-only; dog-only; long-stay | pet profile → facility/provider → dates → handoff | candidate |
| PET-GROOM | Pet Grooming | Pet services | D3 | M2 | grooming salon; mobile groomer; vet-clinic grooming; marketplace; recurring package | pet profile → service → schedule → history | candidate |
| PROPERTY-VIEW | Property Viewing Scheduling | Property | D3 | M3 | single agency; listing portal; open-house; agent calendar; self-guided viewing; new-build sales center | listing → viewing slot → visit → application/offer | candidate |
| PROPERTY-SHORTSTAY | Short-Term Rental Management | Property / travel | D3 | M3 | host-direct operations; managed host service; multi-property operator; corporate stays; turnover service | property → availability → guest → turnover/operations | candidate |
| PRO-TRANSLATION | Translation / Interpretation Service | Professional services | D3 | M3 | document translation; certified translation; interpreter booking; remote interpretation; marketplace; B2B localization | request → scope/quote → assignment → delivery | candidate |
| PRO-NOTARY | Notary / Official Document Appointment | Professional / administrative | D3 | M2 | office appointment; document precheck; queue booking; corporate bulk; document-status flow | document need → requirements → appointment → completion | candidate |
| PRO-INSURANCE | Insurance Broker / Claims Assistance | Financial services | D3 | M4 | comparison; broker advisory; corporate insurance; claims concierge; renewal subscription | need → compare/advice → purchase/renew → claim support | candidate |
| PRO-FREELANCE | Freelancer / Expert Marketplace | Professional services | D3 | M4 | open bidding; curated experts; fixed-price gigs; hourly talent; managed project; local-only | brief → proposals/match → contract → delivery | candidate |
| B2B-AGENCY | Creative / Design Agency Client Portal | B2B creative | D3 | M2 | single-agency portal; managed marketplace; retainer; project-based; review/approval workspace | brief → estimate → project → review/approval | candidate |
| B2B-MARKETING | Marketing / Advertising Service | B2B | D3 | M3 | agency retainer; campaign project; freelancer marketplace; performance marketing; content studio; local-business marketing | goal → brief → proposal → campaign → reporting | candidate |
| B2B-IT | IT Support / Managed Service Desk | B2B technology | D3 | M4 | MSP contract; on-demand technician; remote support; field dispatch; device fleet; internal service desk | issue → priority → assignment → resolution | candidate |
| TECH-DATA | Data Recovery Service | Technology services | D3 | M2 | walk-in lab; pickup courier; enterprise incident; phone recovery; disk recovery; quote-first | device/media → diagnose → quote → recover → return | candidate |
| TECH-INTERNET | Home Internet Installation / Field Support | Utilities / technology | D3 | M3 | ISP-direct; installer network; address eligibility; appointment scheduling; field repair; business internet | address → eligibility → service → appointment → install | candidate |
| LOCAL-TAILOR | Tailor / Alteration Service | Local personal services | D3 | M2 | tailor shop; fitting appointment; pickup/delivery; custom tailoring; marketplace; bridal alterations | garment need → fitting → estimate → pickup | candidate |
| LOCAL-MEALPREP | Meal Prep / Subscription Cooking | Food services | D3 | M3 | weekly subscription; diet meals; family meals; corporate meals; chef-prepared; pickup/delivery | preferences → plan → recurring order → delivery | candidate |
| LOCAL-FLORIST | Florist / Event Flower Service | Local services | D3 | M4 | flower delivery; subscription; wedding florist; funeral flowers; corporate flowers; marketplace | occasion → design/product → schedule → delivery/setup | candidate |
| LOCAL-FUNERAL | Funeral / Memorial Service Coordination | Local / care | D3 | M1 | funeral coordinator; cemetery service portal; transport+ceremony package; memorial service; document concierge | need → arrangements → vendors/schedule → ceremony | candidate |
| EVENT-RENTAL | Party / Event Equipment Rental | Events / rental | D3 | M3 | furniture; sound/light; tent; decor; full package; marketplace | event/date → equipment → availability → delivery/return | candidate |
| EVENT-DJ | DJ / Music / Entertainment Booking | Events | D3 | M2 | DJ marketplace; band booking; wedding entertainment; corporate event; package agency | event → style/provider → quote → booking | candidate |
| EDU-MUSIC | Music Lessons | Education | D3 | M2 | private teacher; music school; online; home lessons; instrument-specific; group class | instrument/level → teacher → schedule → recurring lessons | candidate |
| EDU-CODING | Coding / Digital Skills Training | Education | D3 | M4 | bootcamp; cohort; private mentor; online course+mentor; corporate; kids coding | goal → course/mentor → cohort/sessions → project | candidate |
| EDU-ADMISSION | University / Study-Abroad Counseling | Education / professional | D3 | M3 | admission consultant; document editing; university matching; full application; country specialist | profile/goal → strategy → documents → applications | candidate |
| EDU-AFTERSCHOOL | Daycare / After-School Program | Education / care | D3 | M2 | daycare center; after-school club; activity classes; school transport add-on; hourly care | child/profile → program → schedule/enroll → attendance | candidate |
| TRAVEL-GUIDE | Local Tour Guide / Experience Booking | Travel | D3 | M3 | guide marketplace; city tour; private guide; food tour; heritage tour; custom itinerary | destination → experience/guide → date → booking | candidate |
| TRAVEL-TRANSFER | Airport Transfer / Chauffeur Service | Travel / mobility | D3 | M4 | airport taxi; chauffeur; hotel transfer; corporate driver; luxury car; intercity transfer | pickup/dropoff → vehicle → schedule → trip | candidate |
| AUTO-CLAIM | Auto Insurance Claim Assistance | Automotive / insurance | D3 | M2 | claims concierge; repair-network integration; inspection booking; document workflow; fleet claims | incident → documents/inspection → approval → repair/payment | candidate |
| AUTO-FLEET | Fleet Maintenance Service | Automotive / B2B | D3 | M3 | scheduled maintenance; mobile fleet service; workshop network; tire/battery plan; telematics-triggered | fleet → maintenance plan → work order → reporting | candidate |
| B2B-PRINT | Printing / Signage / Promotional Production | B2B / local | D3 | M3 | digital print; signage project; packaging; corporate portal; design+print; marketplace | spec/file → quote → proof → production → delivery | candidate |
| B2B-SECURITY | Security Guard / Building Security Service | B2B / property | D3 | M2 | guard staffing; event security; residential building; corporate contract; patrol | site need → staffing plan → schedule → reporting | candidate |
| B2B-FACILITY | Facility Management | B2B / property | D3 | M2 | commercial FM; residential complex; hospital/office; outsourced maintenance; integrated cleaning/security | site/assets → tasks → vendors → SLA/reporting | candidate |
| B2B-EQUIP | Equipment Maintenance / Field Service | Industrial / B2B | D3 | M2 | OEM service; independent technicians; preventive contract; emergency repair; multi-vendor | asset → issue/maintenance → dispatch → work order | candidate |
| RENT-EQUIPMENT | Equipment / Tool Rental | Rental | D3 | M3 | construction tools; event gear; camera gear; industrial equipment; marketplace; B2B long-term | asset/date → availability → reserve → pickup/return | candidate |
| SPACE-COWORK | Coworking / Desk / Meeting-Room Booking | Workspace | D3 | M4 | membership; day pass; desk booking; meeting room; marketplace; corporate access | location/resource → availability → book/access | candidate |
| SPACE-SPORT | Sports Court / Facility Booking | Sports / resource booking | D3 | M3 | futsal/football; tennis; padel; pool lane; multi-venue marketplace; league blocks | sport/location → slot → reserve → play | candidate |
| HOME-GARDEN | Gardening / Landscaping | Home services | D2 | M2 | garden maintenance; landscaping project; gardener marketplace; villa subscription; commercial grounds | site → scope → quote/schedule → recurring/project | candidate |
| HOME-POOL | Pool Maintenance | Home services | D2 | M1 | villa pool; commercial pool; seasonal opening; repair; subscription | pool → service plan/issue → visit → log | candidate |
| HOME-ORGANIZE | Home Organization / Decluttering | Home services | D2 | M1 | organizer booking; move organization; wardrobe; kitchen; premium concierge | space/goal → consultant → session/project | candidate |
| HOME-INSPECT | Home / Property Inspection | Property services | D2 | M1 | pre-purchase; handover; rental; defect report; commercial inspection | property → inspector → visit → report | candidate |
| LOCAL-SHOE | Shoe / Leather Repair | Local services | D2 | M1 | walk-in; pickup/delivery; premium restoration; bag/leather repair | item → quote → repair → return | candidate |
| LOCAL-PERSONAL-CHEF | Personal Chef | Food services | D2 | M1 | home dinner; weekly prep; event chef; diet chef; chef marketplace | occasion/preferences → chef → menu/quote → service | candidate |
| LOCAL-STYLIST | Personal Stylist / Wardrobe Consultant | Personal services | D2 | M1 | in-person; online styling; shopping concierge; bridal styling; subscription | goal/profile → stylist → session → recommendations | candidate |
| BEAUTY-SPA | Spa / Massage Booking | Wellness / beauty | D2 | M2 | spa center; therapist; hotel spa; at-home where lawful; membership; marketplace | service → provider/location → schedule → visit | candidate |
| BEAUTY-TATTOO | Tattoo / Piercing Studio Booking | Personal services | D2 | M1 | studio; artist marketplace; consultation-first; custom design; piercing-only | style/idea → artist → consultation → appointment | candidate |
| PET-TRAIN | Pet Training | Pet services | D2 | M1 | trainer marketplace; home trainer; group class; board-and-train; online consult | pet/behavior → trainer/program → sessions → progress | candidate |
| PET-WALK | Dog Walking / Pet Sitting | Pet services | D2 | M1 | walker marketplace; sitter marketplace; recurring walk; home visit; overnight sitting | pet → schedule → sitter/walker → visit updates | candidate |
| PET-TRANSPORT | Pet Taxi / Transport | Pet services | D2 | M1 | vet transfer; airport transfer; scheduled pet taxi; rescue transport | pet/location → vehicle → schedule → transport | candidate |
| CARE-POSTPARTUM | Postpartum / Newborn Support | Care services | D2 | M1 | newborn caregiver; lactation consultant; postpartum helper; night nurse; package | family need → specialist → schedule → support | candidate |
| CARE-RESPITE | Respite / Temporary Care | Care services | D2 | M1 | elder respite; disability respite; hourly backup; managed agency | care context → caregiver → short-term schedule | candidate |
| HEALTH-ADDICTION | Addiction Treatment Service Intake | Healthcare | D2 | M1 | center discovery; confidential intake; appointment; family consultation; follow-up program | need → center/program → confidential intake → appointment | candidate |
| HEALTH-SLEEP | Sleep Clinic / Sleep Coaching | Healthcare / wellness | D2 | M1 | clinic; sleep test; remote coaching; device follow-up | problem → assessment/test → plan → follow-up | candidate |
| FITNESS-SPORTCOACH | Sports Coach / Lesson Booking | Sports | D2 | M2 | swim coach; tennis coach; martial arts; ski coach; kids coach; marketplace | sport/level → coach → facility/time → lessons | candidate |
| EDU-CAREER | Career Coaching / Mentoring | Professional development | D2 | M2 | 1:1 coach; mentor marketplace; interview prep; CV service; package | goal → mentor/coach → sessions → action plan | candidate |
| EDU-CORPORATE | Corporate Training Service | B2B education | D2 | M2 | trainer marketplace; custom workshop; LMS+live; leadership coaching; technical training | company need → proposal → schedule → delivery | candidate |
| PRO-FINANCE | Personal Financial Advisory | Financial services | D2 | M1 | advisor booking; goal-based planning; investment education; family finance; SME-owner advisory | goal → advisor → plan → follow-up | candidate |
| PRO-BUSINESS | Business / Management Consulting | Professional services | D2 | M2 | independent consultant; boutique firm; expert marketplace; project; retainer | problem → expert → diagnosis/proposal → project | candidate |
| PRO-DEBT | Debt Collection / Receivables Service | Professional / B2B | D2 | M1 | agency; legal escalation; invoice collection; subscription; success-fee | debt case → intake → outreach/escalation → status | candidate |
| B2B-CYBER | Cybersecurity Consulting / Incident Response | B2B technology | D2 | M2 | assessment; pentest; incident response; managed security; compliance consulting | risk/incident → scope → engagement → remediation | candidate |
| B2B-CLOUD | Cloud / DevOps Managed Service | B2B technology | D2 | M2 | managed hosting; DevOps retainer; migration; on-call support; cost optimization | system need → assessment → project/retainer → operations | candidate |
| B2B-PROCURE | Procurement / Sourcing Service | B2B | D2 | M1 | supplier sourcing; RFQ marketplace; import sourcing; managed procurement; category specialist | need/spec → suppliers/quotes → select → procure | candidate |
| B2B-INSPECT | Inspection / Certification Service | Industrial / B2B | D2 | M2 | building; equipment; quality audit; safety certification; third-party inspection | asset/site → standard → schedule → inspect → report | candidate |
| B2B-CALIBRATE | Calibration / Metrology Service | Industrial | D2 | M1 | lab calibration; on-site; recurring compliance; equipment pickup | instrument → schedule → calibrate → certificate | candidate |
| AGRI-MACH | Agricultural Machinery Service | Agriculture | D2 | M1 | mobile mechanic; dealer service; seasonal maintenance; parts+service; farm fleet | machine → issue/maintenance → technician → repair | candidate |
| AGRI-IRRIGATION | Irrigation / Greenhouse Service | Agriculture | D2 | M1 | design/install; maintenance; greenhouse climate; pump service; farm contract | farm need → survey → quote → install/maintain | candidate |
| AGRI-CONSULT | Agricultural Consulting | Agriculture | D2 | M1 | crop consultant; soil expert; greenhouse advisor; farm management; remote advisory | farm/context → expert → assessment → plan | candidate |
| SPACE-STUDIO | Recording / Rehearsal / Podcast Studio Booking | Creative / resource booking | D2 | M2 | recording studio; rehearsal room; podcast studio; marketplace; engineer-included | resource/service → slot → book → session | candidate |
| SPACE-STORAGE | Self-Storage / Storage Unit Rental | Property / rental | D2 | M2 | personal storage; business storage; pickup+storage; student storage; marketplace | space need → unit → dates → access | candidate |
| LOCAL-QUEUE | Appointment / Virtual Queue for Local Businesses | Horizontal local services | D2 | M2 | single-business booking; multi-business directory; ticketed queue; appointment-only; virtual queue | business/service → slot/queue → check-in → serve | candidate |
| GOV-ADMIN | Administrative / Government-Service Concierge | Administrative services | D2 | M1 | document checklist; appointment help; form filing; expat admin; business licensing help | need → requirements → documents → submission/status | candidate |
| RELIGIOUS-SERVICE | Religious Ceremony / Service Coordination | Community services | D2 | M1 | ceremony venue; speaker/officiant; catering bundle; memorial/religious event; pilgrimage support | occasion → providers/package → schedule → event | candidate |
| TRAVEL-LUGGAGE | Luggage Storage Service | Travel | D1 | M1 | city lockers; partner-shop network; hotel storage; airport storage | location/time → storage spot → reserve → drop/pickup | candidate |
| TRAVEL-CAMP | Camping / Campsite Booking | Travel / outdoor | D1 | M1 | campsite; eco-camp; glamping; guided camping; equipment bundle | destination/date → site/package → reserve | candidate |
| TRAVEL-RV | RV / Campervan Rental | Travel / rental | D1 | M0 | rental operator; peer-to-peer; driver+RV; camping package | vehicle/date → reserve → pickup/return | candidate |
| TRAVEL-BOAT | Boat / Yacht Rental | Travel / leisure | D1 | M1 | hourly boat; yacht charter; fishing boat; captain-included; marketplace | location/date → vessel → quote/book → trip | candidate |
| TRAVEL-ADVENTURE | Adventure Activity Booking | Travel / leisure | D1 | M2 | paragliding; rafting; diving; climbing guide; multi-activity marketplace | activity/location → provider/date → book → experience | candidate |
| LOCAL-HOUSESIT | House Sitting | Home / trust marketplace | D1 | M0 | traveler sitter; paid sitter; pet+house sitting; long-stay | home/dates → sitter trust → handoff → updates | candidate |
| LOCAL-CONCIERGE | Personal Concierge / Errand Service | Personal services | D1 | M1 | hourly errands; premium concierge; senior errands; corporate concierge; subscription | request → assign → execute → proof | candidate |
| LOCAL-LINE | Line-Waiting / Queue Proxy Service | Personal services | D1 | M0 | government queue; event/ticket line; lawful appointment proxy | request/location → runner → wait → handoff | candidate |
| LOCAL-MATCHMAKER | Matchmaking / Marriage Introduction Service | Personal / social service | D1 | M1 | traditional agency digitization; counselor-led; premium curated; community-specific | profile → screening → match → introduction | candidate |
| CARE-DOULA | Doula / Birth-Coach Service | Care / wellness | D1 | M0 | birth doula; prenatal coach; postpartum package; remote education | pregnancy stage → doula fit → package → support | candidate |
| PET-DAYCARE | Pet Daycare / Activity Club | Pet services | D1 | M1 | dog daycare; training daycare; pickup/drop-off; membership | pet → facility → day/package → attendance | candidate |
| PET-MEMORIAL | Pet Memorial / Aftercare Service | Pet services | D1 | M0 | cremation coordination; burial support; keepsake; pickup | loss → service choice → logistics → memorial | candidate |
| SPACE-PARK | Parking Reservation | Mobility / resource booking | D1 | M2 | airport parking; city lot; private-space marketplace; monthly; event parking | location/time → space → reserve → access | candidate |
| SPACE-MARINA | Marina / Berth Booking | Marine resource booking | D1 | M0 | daily berth; seasonal berth; service+berth; transient boat | vessel/date → berth → reserve | candidate |
| SPACE-OFFICE | Private Office / Flexible Workspace Marketplace | Workspace | D1 | M2 | office-by-day; monthly private office; team room; multi-operator marketplace | location/team → space → tour/book → access | candidate |
| B2B-VA | Virtual Assistant Service | B2B / remote | D1 | M1 | hourly VA; dedicated assistant; task marketplace; executive assistant; bilingual | tasks → assistant match → recurring work | candidate |
| B2B-AI | AI Consulting / Automation Service | B2B technology | D1 | M2 | AI strategy; workflow automation; chatbot agency; model integration; retainer support | process → assessment → prototype/project → support | candidate |
| AGRI-DRONE | Agricultural Drone Service | Agriculture | D1 | M1 | spraying; mapping; crop monitoring; operator marketplace; seasonal contract | farm/area → mission → schedule → flight/report | candidate |
| AGRI-HARVEST | Harvest Labor / Seasonal Farm Staffing | Agriculture | D1 | M0 | labor crew marketplace; contractor; transport+crew; seasonal contract | crop/date → crew → schedule → completion | candidate |
| INDUSTRIAL-WASTE | Industrial Waste / Recycling Service | Industrial | D1 | M1 | scheduled pickup; hazardous specialist; recycling broker; compliance reporting | waste type → quote → pickup → certificate | candidate |
| CLIMATE-SNOW | Snow Removal Service | Climate / property | D0 | M0 | residential; commercial contract; on-demand dispatch; seasonal subscription | weather/event → route/request → clear → proof | candidate |
| HOME-LAWN | Lawn-Care Subscription | Home services | D0 | M0 | mowing subscription; landscaping maintenance; on-demand; neighborhood route | property → plan → recurring visits | candidate |
| TRAVEL-SKI-CONCIERGE | Ski Resort Concierge / Lesson + Equipment Bundle | Travel / leisure | D0 | M0 | lesson+equipment; resort transfer; pass bundle; family package | resort/date → package → booking | candidate |
| MARINE-BOATCARE | Boat Maintenance Service | Marine | D0 | M0 | mobile mechanic; marina contract; detailing; seasonal maintenance | vessel → maintenance/issue → technician → report | candidate |
| HOME-CHIMNEY | Chimney Sweep Service | Home services | D0 | M0 | inspection; cleaning; recurring safety; fireplace repair | home → schedule → inspect/clean | candidate |
| HOME-SEPTIC | Septic Tank Service | Home / utility | D0 | M0 | pump-out; inspection; emergency; recurring rural service | property → tank/service → dispatch → completion | candidate |
| PET-WEDDING | Wedding Pet Attendant Service | Pet / events | D0 | M0 | event pet handler; transport; photo support; overnight care | event/pet → package → schedule | candidate |
| LOCAL-MOBILE-NOTARY | Mobile Notary Marketplace | Administrative services | D0 | M0 | on-demand notary; scheduled mobile notary; business bulk | document/location → notary → visit → completion | candidate |
| SPACE-BOAT-COWORK | Floating / Boat Coworking Space | Workspace / novelty | D0 | M0 | day pass; event workspace; tourism+work package | date → space → reserve | candidate |
| LOCAL-LUXURY-CONCIERGE | Luxury Lifestyle Concierge | Personal services | D0 | M0 | membership; travel/reservation concierge; personal shopping; VIP errands | member request → concierge → fulfillment | candidate |

---

# Model-selection guidance

A product family is **not sufficiently selected** while materially different models remain unresolved.

For example, `BEAUTY-SALON` can produce products with very different actors and workflows:

```text
Men’s single barbershop
Women’s single salon
Unisex salon
Independent specialist/studio
Multi-branch salon
Multi-salon marketplace
At-home beauty service
```

A marketplace must not be treated as merely a larger version of a single-provider product. It introduces provider acquisition, listing/discovery, trust, marketplace supply/demand, potentially commissions/payouts, cross-provider availability, moderation, and different operational boundaries.

Likewise, fixed-location and at-home models may share a service category while requiring very different scheduling and logistics.

## Selection criteria

When choosing the next portfolio project, consider:

- **Iran demand:** how prevalent the underlying service currently is;
- **digital maturity:** whether the market is already productized or still manually coordinated;
- **problem strength:** whether the pain is clear and meaningful;
- **workflow depth:** whether the service supports real product behavior beyond a landing page;
- **portfolio differentiation:** whether its workflow differs from projects already built;
- **model differentiation:** whether another variant of the same family would create a genuinely different product.

Do not use a mechanical score unless comparison genuinely benefits from one.

## Selected model rule

The Selected Opportunity Brief must record:

- stable product-family ID;
- product-family name;
- selected model / variant;
- target market / geography when relevant;
- target user;
- primary problem;
- proposed solution direction;
- why the project is worth exploring;
- explicit boundaries against adjacent variants.

Detailed feature scope still begins in Phase 01; the model selection step defines **what kind of product is being discovered**, not its full feature list.

---

# Current portfolio selection

- `BEAUTY-SALON` — **Women’s single-salon** model — `in-progress` via [`projects/womens-beauty-salon-booking.md`](../projects/womens-beauty-salon-booking.md).
