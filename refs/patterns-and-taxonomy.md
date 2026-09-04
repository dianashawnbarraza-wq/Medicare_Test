# Medicare Appointment Scheduler — UX Patterns & Condition Taxonomy

**Concept:** Mobile-first, accessible Medicare appointment scheduler for adults 65+.  
**Research date:** September 3, 2026 (PT)  
**Sources:** Mobbin.com Zocdoc collections (public screen/flow pages), Zocdoc product writeups, Solv / One Medical public app descriptions, senior-accessible UX literature, CMS chronic-condition prevalence summaries.

---

## 1) Provider search results with availability on the card

### Pattern (Zocdoc-class / Mobbin)

Consumer booking apps treat the **result card as a booking surface**, not just a directory row. Availability is visible *before* opening the profile.

| Card element | Typical treatment | Notes for 65+ |
|---|---|---|
| Photo + name + specialty | Top of card, large type | Prefer specialty in plain language (“Heart doctor”) with formal label secondary |
| Rating / review count | Adjacent to name | Keep; don’t rely on stars alone—show numeric score + “reviews” |
| Insurance / network signal | Badge under score or near CTA (“In-network”, “Accepts Medicare”) | Critical for Medicare; see §2 |
| Distance / location | One line (miles + neighborhood) | Avoid burying under accordion |
| **Next available slots** | Horizontal date/time chips or mini carousel on the card | Mobbin: Zocdoc doctor lists tagged with Carousel + Date Picker UI |
| Visit modality | “In person” / “Video” chip | Filterable; show on card when both exist |
| Trust badges | “Accepting new patients”, “Highly recommended”, wait-time cues | Zocdoc marketplace cards surface these as scannable chips |

**Mobbin evidence**

- [Zocdoc iOS Doctor List — available appointments + filter](https://mobbin.com/explore/screens/842a4d90-2e64-49d4-9ee6-836e8c700705) — list shows available appointments on-card with a filter control.
- [Zocdoc iOS Doctor List — carousel / date picker](https://mobbin.com/explore/screens/6464e6a2-e0e8-4ad8-a983-5f07dba884b4) — doctor list with carousel + date picker for slot picking from results.
- [Zocdoc iOS Doctor List — after filters / badge](https://mobbin.com/explore/screens/4cd7ff88-c90e-4e26-99b7-7df29959ceda) — updated list with filter/sort badge UI.

**Implications for Medicare scheduler**

1. Show **2–4 next bookable slots** on every card (e.g., “Thu 10:00a · Fri 2:30p · Mon 9:00a”) with a “More times” link—not a blank “View availability” dead-end.
2. Prefer **tappable slot chips** that jump straight into confirm (fewer screens).
3. If no near-term slots, still show “Next: Oct 12” rather than hiding the provider—older adults often need continuity over “soonest.”
4. Keep card height generous; avoid dense multi-column layouts that force precision reading.

---

## 2) Filter chips vs defaults (insurance / network, accepting patients)

### Defaults (apply silently or as sticky chips)

Zocdoc-class search is **patient-centric by default**: location, insurance plan, visit reason, and live availability drive ranking and visibility ([How Search Works](https://www.zocdoc.com/about/how-search-works/)).

Recommended **defaults for Medicare concept** (pre-applied; visible as removable chips):

| Default | Why | Chip label example |
|---|---|---|
| User’s Medicare plan (MA / Medigap / Original + Part D context) | Plan-level network, not carrier-only | `Medicare Advantage — Humana Gold` |
| Accepting new patients | Marketplace norm; Zocdoc lists providers open to new patients | `Accepting patients` (locked or hard-default) |
| Within reasonable distance | Reduce overwhelm | `Within 15 miles` |
| In-person preferred (toggle) | Many 65+ prefer clinic over video first | `In person` |

### Explicit filter sheet (Mobbin)

- [Zocdoc iOS Doctor Filters](https://mobbin.com/explore/screens/4dcbe827-28bb-45dd-bc63-92c983c33ecf) — timeframe, time of day, distance, in-person/video.
- Active filters return as **badges** on the list ([filter/sort badge screen](https://mobbin.com/explore/screens/4cd7ff88-c90e-4e26-99b7-7df29959ceda)).

**Chip vs sheet rules**

- **Chips (always visible):** insurance/network, accepting patients, modality, distance—these are trust/eligibility constraints.
- **Sheet / bottom sheet:** time of day, gender, language, rating floor, “today / this week / next 2 weeks”—refinement, not eligibility.
- **Do not hide insurance behind “More filters.”** In-network status should be a first-class chip + on-card badge ([Zocdoc insurance guide](https://www.zocdoc.com/blog/guides/find-a-doctor-that-accepts-your-insurance/), [in-network guide](https://www.zocdoc.com/blog/guides/how-to-know-if-a-doctor-is-in-network/)).
- Photo/scan of insurance card (Zocdoc / Solv pattern) reduces plan-name anxiety for seniors.

**Wrong-fit controls (from Zocdoc practice guidance)**

Visit reasons, age preferences, referral requirements, and accurate accepted-insurance data reduce misbookings ([Wrong-fit bookings](https://www.zocdoc.com/blog/facts/wrong-fit-bookings-lead-quality/)). For Medicare, surface **“Sees adults 65+”** as a soft default when specialty lists pediatric mixes.

---

## 3) Condition / symptom search taxonomy UX

### Pattern

Patients search in **colloquial language** (symptoms, nicknames, misspellings), not specialty codes. Zocdoc’s Patient-Powered Search maps phrases like “gyno”, “hurt wrist”, misspellings, even emoji → specialties/taxonomy ([Built In NYC](https://www.builtinnyc.com/articles/zocdoc-patient-powered-search), [How Search Works](https://www.zocdoc.com/about/how-search-works/)).

Pratt IXD critique of Zocdoc iOS: constrained specialty/symptom selection (search + pick from suggestions) reduces execution errors vs free-text-only ([Design Critique](https://ixd.prattsi.org/2024/01/design-critique-zocdoc-ios-app/)).

### Recommended UX structure

1. **Single search field** with placeholder: “What’s going on? e.g., knee pain, blood pressure check”
2. **Typeahead groups:** Suggested conditions → Visit reasons → Specialties → Provider names
3. **Homepage shortcuts:** large icon tiles for top Medicare reasons (Annual checkup, Joint pain, Heart, Diabetes, Mental health)—mirrors Zocdoc “top-searched specialties” affordance
4. After pick: ask **one** clarifying question if needed (“Is this new or a follow-up?”) then show providers—avoid long decision trees
5. Always show **plain-language label → mapped specialty** in results (“Knee pain → Orthopedics / Primary care”)

### Accessibility notes for taxonomy UI

- Large suggestion rows (≥48×48 dp tap targets)
- No reliance on autocomplete alone—browseable groups for users who don’t type well
- Voice input optional augment, not replacement for visible controls

---

## 4) Booking confirmation + post-book home access (appointment tile)

### Confirmation flow (Mobbin)

- [Zocdoc iOS — Making a doctor appointment flow](https://mobbin.com/explore/flows/26c741b6-0231-4040-b5e9-890f0b6db100): select details → insurance → confirm → **add to calendar** + upload insurance.
- Success screen should answer: **Who, when, where, how to prepare, what to do next**—in that order.

**Confirmation checklist (65+)**

- Provider name + specialty (large)
- Date/time in full words (“Thursday, September 10 · 10:00 AM”)
- Location with map + “Get directions” (or “Video visit — Join link sent day-of”)
- Insurance on file status
- Primary CTAs: **Add to calendar** · **Set reminder** · **Go to home**
- Secondary: Reschedule · Cancel · Upload insurance card · Complete forms

### Post-book home: appointment tile

- [Zocdoc Android Upcoming Appointments](https://mobbin.com/explore/screens/09d40d23-ab5b-41b0-88a9-c96f3cdedb6a) — upcoming appointments with details + insurance upload prompt.
- Solv / One Medical position home around **upcoming visit management**, check-in, reminders ([Solv App Store](https://apps.apple.com/us/app/solv-easy-same-day-healthcare/id1464601606), [One Medical App Store](https://apps.apple.com/us/app/one-medical/id393507802)).

**Home tile hierarchy (recommended)**

```
┌─────────────────────────────────────┐
│ Upcoming appointment                │
│ Dr. Rivera · Primary care           │
│ Thu, Sep 10 · 10:00 AM              │
│ Downtown Clinic · 2.1 mi            │
│ [ Directions ]  [ Details ]         │
└─────────────────────────────────────┘
```

- Persistent on home until visit completes (not buried in a “Appointments” tab only).
- After visit: convert tile to “Rate visit / Book follow-up” or archive to history.
- Optional caregiver/proxy visibility for family helpers (senior booking pattern).

---

## 5) Minimal-scroll mobile hierarchy for older adults

### Design principles (research-backed)

| Principle | Guidance | Sources |
|---|---|---|
| One primary job per screen | Wizard steps beat dense dashboards | [Accessible portals guide](https://tecksite.com/designing-accessible-patient-caregiver-portals-for-the-elder), telehealth UX for older adults |
| Large tap targets | ≥44×44 dp (WCAG); prefer 48×48+; full-width primary buttons | [arXiv senior mobile a11y](https://arxiv.org/html/2504.12690v1), Android/Apple a11y |
| Readable type | Base ≥18–20 pt; support dynamic type / 200% zoom | Senior booking UX summaries |
| High contrast | Black-on-white or WCAG AA+; live contrast checks where theming exists | WCAG / SSA-style booking a11y notes |
| Shallow scroll | Above-the-fold: search + next appointment + 1–2 shortcuts; list cards tall but few fields | Cognitive load reduction |
| Plain labels | Outcome language: “Book visit”, “Join video visit”—not “Continue” / “Submit” | Telehealth older-adult guides |
| Predictable chrome | Stable nav; same positions for Back / Home / Help | Patient portal senior UX |

### Suggested screen stack (minimal scroll)

1. **Home** — Next appointment tile + “Find care” search + 4–6 condition shortcuts (no feed).
2. **Results** — Sticky filter chips; cards with slots; infinite scroll OK but first card fully visible without scroll.
3. **Confirm** — Single column summary; one primary “Confirm appointment” button pinned bottom.
4. **Done** — Confirmation + calendar; auto-return path to home with tile updated.

Avoid: multi-panel dashboards, hover-only hints, gesture-only navigation, tiny chip grids, time-limited modals.

---

## Starter CONDITION TAXONOMY (Medicare beneficiaries)

Plain-language groups for search shortcuts and typeahead. ~22 entries. Each maps example queries → likely provider types. Prefer routing to **Primary care** when in doubt; specialty when symptom is clearly specialty-led.

Prevalence grounding: hypertension, hyperlipidemia, arthritis, ischemic heart disease, diabetes, CKD, depression, COPD, heart failure, and related CCW conditions are among the most common for Medicare FFS/MA populations ([Abarca / CMS summary](https://www.abarcahealth.com/common-conditions-medicare/), CCW chronic conditions methodology, Milliman/Medicare market prevalence writeups).

### A. Everyday / preventive care

| ID | Plain-language condition | Example queries | Maps to |
|---|---|---|---|
| A1 | Annual checkup / wellness visit | “yearly physical”, “Medicare wellness”, “checkup” | Primary care (PCP), Geriatrics |
| A2 | New primary doctor | “find a doctor”, “new PCP”, “family doctor” | Primary care, Geriatrics |
| A3 | Vaccines & shots | “flu shot”, “COVID vaccine”, “shingles shot” | Primary care, Pharmacy clinic, Urgent care |
| A4 | Medication review / refill help | “med check”, “too many pills”, “refill” | Primary care, Geriatrics, Pharmacist (MTM) |

### B. Heart & circulation

| ID | Plain-language condition | Example queries | Maps to |
|---|---|---|---|
| B1 | High blood pressure | “blood pressure”, “hypertension”, “BP check” | Primary care; Cardiology if complex/follow-up |
| B2 | Heart problems / chest concerns* | “heart doctor”, “chest pain follow-up”, “heart failure” | Cardiology; *urgent red-flag → ER guidance, not book |
| B3 | High cholesterol | “cholesterol”, “lipids”, “statin check” | Primary care |

### C. Bones, joints & movement

| ID | Plain-language condition | Example queries | Maps to |
|---|---|---|---|
| C1 | Joint / arthritis pain | “arthritis”, “stiff joints”, “knee pain”, “hip pain” | Primary care, Rheumatology, Orthopedics |
| C2 | Back or neck pain | “back pain”, “sciatica”, “neck pain” | Primary care, Orthopedics, Spine, PT |
| C3 | Fall / balance / walking trouble | “fell”, “unsteady”, “walker”, “balance” | Primary care, Geriatrics, PT, Neurology |

### D. Metabolism & organs

| ID | Plain-language condition | Example queries | Maps to |
|---|---|---|---|
| D1 | Diabetes / blood sugar | “diabetes”, “blood sugar”, “A1C” | Primary care, Endocrinology |
| D2 | Kidney concerns | “kidney”, “CKD”, “swelling legs” | Primary care, Nephrology |
| D3 | Breathing / lung problems | “COPD”, “short of breath”, “wheeze”, “asthma” | Primary care, Pulmonology |

### E. Brain, mood & nerves

| ID | Plain-language condition | Example queries | Maps to |
|---|---|---|---|
| E1 | Memory or thinking changes | “memory”, “forgetful”, “dementia check” | Primary care, Geriatrics, Neurology |
| E2 | Feeling down or anxious | “depression”, “anxious”, “can’t sleep from worry” | Primary care, Behavioral health, Psychiatry |
| E3 | Numbness / neuropathy | “numb feet”, “tingling”, “neuropathy” | Primary care, Neurology, Endocrinology (if diabetic) |

### F. Eyes, ears, skin, teeth

| ID | Plain-language condition | Example queries | Maps to |
|---|---|---|---|
| F1 | Vision / eye exam | “eye doctor”, “cataracts”, “blurry vision” | Ophthalmology, Optometry |
| F2 | Hearing | “hearing aid”, “can’t hear”, “ear ringing” | Audiology, ENT |
| F3 | Skin check / rash | “mole check”, “rash”, “itchy skin” | Dermatology; Primary care for simple rash |
| F4 | Dental / toothache | “dentist”, “tooth pain”, “dentures” | Dentistry (Medicare dental coverage varies—disclose) |

### G. Urgent but non-ER (same-day)

| ID | Plain-language condition | Example queries | Maps to |
|---|---|---|---|
| G1 | Cold, flu, sinus, UTI | “sinus”, “UTI”, “sore throat”, “cough” | Urgent care, Primary care, Telehealth |
| G2 | Minor injury | “sprain”, “cut”, “bruise after fall”† | Urgent care, Orthopedics; †screen for ER if head injury / can’t walk |

### Taxonomy UX rules

1. Cap homepage shortcuts at **6–8**; put full list behind “More reasons.”
2. Synonym dictionary: hypertension ↔ high blood pressure; PCP ↔ family doctor; COPD ↔ breathing problems.
3. Always pair selection with **provider-type explanation** (“We’ll show primary care doctors first; specialists if needed”).
4. Red-flag banner for chest pain, stroke symptoms, suicidal ideation, severe shortness of breath → call 911 / crisis resources—do not complete booking.

---

## Source links (quick index)

### Mobbin (Zocdoc)

- https://mobbin.com/explore/screens/842a4d90-2e64-49d4-9ee6-836e8c700705 — Doctor list + availability  
- https://mobbin.com/explore/screens/6464e6a2-e0e8-4ad8-a983-5f07dba884b4 — Doctor list + carousel/date picker  
- https://mobbin.com/explore/screens/4cd7ff88-c90e-4e26-99b7-7df29959ceda — Filtered list + badges  
- https://mobbin.com/explore/screens/4dcbe827-28bb-45dd-bc63-92c983c33ecf — Doctor filters sheet  
- https://mobbin.com/explore/flows/26c741b6-0231-4040-b5e9-890f0b6db100 — Booking confirmation flow  
- https://mobbin.com/explore/screens/09d40d23-ab5b-41b0-88a9-c96f3cdedb6a — Upcoming appointments  
- https://mobbin.com/explore/mobile/app-categories/medical — Medical app category browse  

### Zocdoc / marketplace product

- https://www.zocdoc.com/about/how-search-works/  
- https://www.builtinnyc.com/articles/zocdoc-patient-powered-search  
- https://www.zocdoc.com/blog/guides/find-a-doctor-that-accepts-your-insurance/  
- https://www.zocdoc.com/blog/guides/how-to-know-if-a-doctor-is-in-network/  
- https://www.zocdoc.com/blog/facts/wrong-fit-bookings-lead-quality/  
- https://ixd.prattsi.org/2024/01/design-critique-zocdoc-ios-app/  
- https://book.zocdoc.com/get-started  

### Peer apps

- https://apps.apple.com/us/app/solv-easy-same-day-healthcare/id1464601606  
- https://apps.apple.com/us/app/one-medical/id393507802  

### Accessibility / senior UX

- https://arxiv.org/html/2504.12690v1  
- https://tecksite.com/designing-accessible-patient-caregiver-portals-for-the-elder  

### Medicare condition prevalence

- https://www.abarcahealth.com/common-conditions-medicare/  
- https://data.cms.gov/sites/default/files/2021-01/Medicare%20Chronic%20Conditions%20Methodology%202020.pdf  
- https://www.medicaremarketinsights.com/p/where-disease-prevalence-meets-market-potential  

---

*Compiled for scheduler-prototype · Sep 3, 2026. Mobbin screens require account for full image gallery; pattern summaries derived from public Mobbin page titles/descriptions and complementary public writeups/screenshots.*
