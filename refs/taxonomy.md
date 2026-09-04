# Condition → specialty taxonomy

Aligned with Stay Put IA and `patterns-and-taxonomy.md`. Homepage shows **Top 8 + Something else**; full ~22 list under “More reasons.”

## Homepage chips (Top 8 + Something else)

| Chip (plain language) | Maps to specialty |
|---|---|
| High blood pressure | Primary care · Cardiology |
| Heart concerns | Cardiology |
| Joint or arthritis pain | Orthopedics · Primary care |
| Diabetes / blood sugar | Endocrinology · Primary care |
| Skin rash or mole check | Dermatology |
| Vision / eye exam | Ophthalmology |
| Hearing | Hearing / ENT (Audiology) |
| Annual checkup / wellness | Primary care |
| Something else | Primary care (or free-text refine) |

## Full starter list (~22)

| ID | Plain language | Maps to |
|---|---|---|
| A1 | Annual checkup / wellness visit | Primary care, Geriatrics |
| A2 | New primary doctor | Primary care, Geriatrics |
| A3 | Vaccines & shots | Primary care, Urgent care |
| A4 | Medication review / refill help | Primary care, Geriatrics |
| B1 | High blood pressure | Primary care; Cardiology if complex |
| B2 | Heart problems / chest concerns | Cardiology (*red-flag ER banner*) |
| B3 | High cholesterol | Primary care |
| C1 | Joint / arthritis pain | Primary care, Rheumatology, Orthopedics |
| C2 | Back or neck pain | Primary care, Orthopedics |
| C3 | Fall / balance / walking trouble | Primary care, Geriatrics, Neurology |
| D1 | Diabetes / blood sugar | Primary care, Endocrinology |
| D2 | Kidney concerns | Primary care, Nephrology |
| D3 | Breathing / lung problems | Primary care, Pulmonology |
| E1 | Memory or thinking changes | Primary care, Geriatrics, Neurology |
| E2 | Feeling down or anxious | Primary care, Behavioral health |
| E3 | Numbness / neuropathy | Primary care, Neurology |
| F1 | Vision / eye exam | Ophthalmology, Optometry |
| F2 | Hearing | Audiology, ENT |
| F3 | Skin check / rash | Dermatology; Primary care |
| F4 | Dental / toothache | Dentistry (coverage varies—disclose) |
| G1 | Cold, flu, sinus, UTI | Urgent care, Primary care, Telehealth |
| G2 | Minor injury | Urgent care, Orthopedics |

## Specialty labels used in confirm / results

Cardiology, Dermatology, Orthopedics, Ophthalmology, Hearing / ENT, Urology, Gastroenterology, Endocrinology, Pulmonology, Neurology, Behavioral health, Obstetrics & Gynecology, Primary care, Urgent care, Something else.

## Trust defaults (sticky chips — always on)

- **In your plan**
- **Accepting new patients**
- **Near you**

Turning any off requires **Show more options** + a warning that results may include out-of-plan or not-accepting providers.

## UX rules

1. After chip pick → **confirm mapped specialty** before Results.
2. Prefer Primary care when in doubt; specialty when clearly specialty-led.
3. Red-flag banner for chest pain / stroke / crisis → do not complete booking.
4. On-card slots (2–4) + doctor page with live slots above the fold.
5. Honest empties: no in-network+accepting combo; slot taken; clinic will call (not “You’re booked”); telehealth only; empty day.
