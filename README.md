# Medicare.gov Appointment Scheduler — Prototype

**Stay Put** concept: a calm, mobile-first Medicare appointment flow that aims for **care need → booked in about 3 minutes**, with Zocdoc-class live slots and the July Medicare Green UI system.

Single file, no build step. Inter font loads from Google Fonts when online; system sans fallbacks work offline.

## Open it

1. Open `index.html` in any modern browser (double-click, or drag into Chrome/Edge/Firefox/Safari).
2. Or from this folder:

```bash
python3 -m http.server 8765 --directory /workspace
# then visit http://localhost:8765/
```

Hash routes work offline (`#home`, `#who`, `#need`, `#results`, …). Booking persists in `localStorage` so a refresh still shows the Home tile.

## Design Lab preview (Mobile / Desktop)

A **Design Lab** bar sits above the prototype:

- **Mobile** (default) — 390×844 phone frame with safe area. A **red dashed line** labeled **ABOVE THE FOLD** is fixed at the bottom of the visible phone (above the home indicator). Results and Book are baked so the first doctor’s times and Continue sit above that line — no scroll required for the pass/fail.
- **Desktop** — full-width **2-column** layout (list | detail), not a scaled-up phone.

Toggle **Mobile / Desktop** in the dark bar at the top. The choice sticks in `localStorage`. Deep-link: `index.html?preview=desktop` or `?preview=mobile`.

**Results pass/fail:** tap a time on doctor #1 without scrolling.  
**Book pass/fail:** select a slot and see **Continue** without scrolling. Empty days show **No times** + **Show next day** above the fold. Continue is hidden until a time is selected so the slot grid keeps the pixels.

## Happy path (Stay Put)

**Book for someone I help** is a **secondary outline CTA** on Home — Who stays a light first step.

1. **Home** — Greeting, coverage note (Advantage vs Original), upcoming tile, primary **Schedule an appointment**.
2. **Who** — Me / someone I help.
3. **Coverage** — Original vs Advantage (changes what “In your plan” means).
4. **ZIP** — Location for “Near you.”
5. **Need** — Visit-reason list + search (Zocdoc-style). Optional chronic-condition refine chips. Mapped specialty shown before results.
6. **Results** — Sticky trust chips always on: In your plan · Accepting new patients · Near you. Badges on every card. Compact rating on the card when mock data has it (not a filter). Show more options (bottom sheet) + warning to turn defaults off.
7. **Select appointment** — New / existing patient toggle changes slot inventory. Results already filtered for accepting when that default is on.
8. **Review → Book** — Then **You’re booked** and a Home upcoming tile. Reschedule Next is a disabled stub.

## Concept bets

| Bet | Why |
|---|---|
| Trust defaults as sticky chips + on-card badges | In-plan + accepting before browse; turning off is explicit |
| Visit-reason chips + search | Plain language in, specialty out — chronic refine is secondary |
| Coverage before search | Advantage network ≠ Original assignment |
| Slots on card + hero on doctor page | Fewer screens; Zocdoc-class |
| New/existing toggle on picker | Inventory, not a substitute for the accepting-new default |
| Home appointment tile | No message-center digging |
| Ratings on cards only | Signal without becoming a sort/filter |
| Caregiver as light Who step | Happy path stays short |

## Honest states (demo on Home)

- No in-plan + accepting — empty results
- Slot taken — conflict screen
- Clinic will call — not You are booked
- Telehealth only
- Clear booking — resets saved booking
- Providers that are out-of-plan, not accepting, or farther appear only after defaults are turned off

## Design system

Medicare Green (`#146A5D` → `#0A352F`), secondary blue for pills/alerts, Inter, 20px body floor, 16px labels/buttons, 44px targets, 3px `#2A6FB8` focus rings, skip link, live region for view changes, reduced-motion respect, text badges. Mobile critique uses a 390×844 phone + fold line. Desktop preview is an intentional 2-column list | detail (no map on Results/Book). Filters stay chips + sheet below the fold — not a left rail.

## Files

- index.html — self-contained UI
- README.md — this file
- LIZ-NOTES.md — typography + DS flags
- refs/taxonomy.md — visit reason → specialty
- refs/patterns-and-taxonomy.md — pattern research

## Out of scope

Live Medicare APIs, real eligibility, calendars or maps, front-end frameworks, auth.
