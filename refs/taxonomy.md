# Visit reason → specialty taxonomy

Aligned with Stay Put IA, Tuesday soft-launch, and `patterns-and-taxonomy.md`. Entry is **visit-reason chips + search** (Zocdoc-style, Medicare plain language). Chronic conditions are an **optional refine group**, not a separate product.

## Visit-reason chips (primary)

| Chip (plain language) | Maps to specialty |
|---|---|
| Annual wellness visit | Primary care |
| High blood pressure | Primary care · Cardiology |
| Diabetes checkup | Primary care · Endocrinology |
| Heart concerns | Cardiology (*red-flag ER banner*) |
| Joint or back pain | Orthopedics · Primary care |
| Skin rash | Dermatology |
| Breathing problems | Pulmonology · Primary care |
| Depression or anxiety | Behavioral health · Primary care (*988 crisis note*) |
| Vision | Ophthalmology |
| Hearing | Hearing / ENT (Audiology) |
| Women’s health | Obstetrics & Gynecology · Primary care |
| Stomach pain | Gastroenterology · Primary care |
| Fall or injury | Primary care · Orthopedics |
| Mammogram / breast screening | Breast imaging · Obstetrics & Gynecology |
| Something else | Primary care (free-text refine) |

Search synonyms (examples): yearly physical / AWV; hypertension / BP; A1C / blood sugar; chest / cardiac; arthritis / knee / sciatica; rash / mole; COPD / wheeze; mood / anxiety; eye / cataract; hearing aid; gyn / pap; GERD / belly; fell / sprain; mammogram / breast.

## Chronic refine (secondary, multi-select, optional)

Shown under visit reasons as “Also living with.” Does **not** replace the visit reason and does not hard-filter the directory in this prototype.

- Diabetes
- High blood pressure
- Heart disease
- COPD / lung disease
- Arthritis
- Depression

## Specialty labels used in confirm / results

Cardiology, Dermatology, Orthopedics, Ophthalmology, Hearing / ENT, Gastroenterology, Pulmonology, Behavioral health, Obstetrics & Gynecology, Breast imaging, Primary care, Something else.

## Trust defaults (sticky chips — always on)

- **In your plan** — Advantage: mock network. Original: accepts Medicare assignment.
- **Accepting new patients**
- **Near you** (~15 miles from ZIP)

Turning any off requires **Show more options** (bottom sheet) + a warning that results may include out-of-plan or not-accepting providers.

Every result card shows honest badges for plan, accepting, and near — including warn badges when a default is off.

## Ratings

Compact `★ 4.8 · 214 reviews` on the card when mock data has a rating. **Not** a top-level filter or sort. Some providers have no rating (honest empty).

## UX rules

1. After reason pick → show mapped specialty on the Need screen, then Results (no extra confirm page).
2. Prefer Primary care when in doubt; specialty when clearly specialty-led.
3. Red-flag banner for chest pain / stroke / crisis → do not complete emergency booking.
4. On-card slots (2–4) + doctor page with live slots and new/existing toggle.
5. Honest empties: no in-network+accepting combo; slot taken; clinic will call (not “You’re booked”); telehealth only; empty day.
