# Medicare.gov Appointment Scheduler — Prototype

**Stay Put** concept: a calm, mobile-first Medicare appointment flow that aims for **care need → booked in about 3 minutes**, with Zocdoc-class live slots and CMS Design System chrome.

Single file, no build step, no network required.

## Open it

1. Open `index.html` in any modern browser (double-click, or drag into Chrome/Edge/Firefox/Safari).
2. Or from this folder:

```bash
python3 -m http.server 8765 --directory /workspace/scheduler-prototype
# then visit http://localhost:8765/
```

Hash routes work offline (`#home`, `#need`, `#results`, …). Booking persists in `localStorage` so a refresh still shows the Home tile.

## Happy path (Stay Put)

**Book for someone** is a **secondary grey CTA** on Home — not required for clickthrough.

1. **Home** — Greeting, coverage note (Advantage vs Original Medicare), primary **Schedule an appointment**.
2. **Care need** — Top 8 plain-language chips + Something else (+ More reasons). Optional facility type / search.
3. **Specialty confirm** — Shows mapped specialty before results.
4. **Results** — Sticky trust chips always on: In your plan, Accepting new patients, Near you. On-card openings. Show more options + warning to turn defaults off.
5. **Doctor / pick time** — Live slots above the fold. New-patient note. Empty days say No times.
6. **Review** — One summary + optional note, then Book appointment.
7. **You are booked** — Add to calendar stub + Get directions stub, then Home.
8. **Home tile** + **My appointments** in nav. Reschedule Next is a disabled stub.

## Concept bets

| Bet | Why |
|---|---|
| Trust defaults as sticky chips | In-plan + accepting before browse |
| Slots on card + hero on doctor page | Fewer screens; Zocdoc-class |
| Specialty confirm before results | Plain language without surprise |
| Home appointment tile | No message-center digging |
| Caregiver as secondary fork | Happy path stays short |
| Honest empties / clinic will call | Do not fake You are booked |


## Honest states (demo on Home)

- No in-plan + accepting — empty results
- Slot taken — conflict screen
- Clinic will call — not You are booked
- Telehealth only
- Clear booking — resets saved booking


## Design system

CMS blues (#0071bc to #00395e), 18px body mobile, 44px targets, 3px #02bfe7 focus rings, skip link, live region for view changes, reduced-motion respect, text badges. Desktop from 960px: max-width about 1100px, list plus sticky map placeholder (not map-only).


## Files

- index.html — self-contained UI
- README.md — this file
- refs/taxonomy.md — condition to specialty
- refs/patterns-and-taxonomy.md — pattern research

## Out of scope

Live Medicare APIs, real eligibility, calendars or maps, front-end frameworks, auth.

