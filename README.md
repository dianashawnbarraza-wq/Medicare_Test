# Medicare.gov Appointment Scheduler — Zocdoc-feel explore

**This branch is an exploration fork for critique.** It is not the soft-launch Stay Put baseline.

Stay Put (calm directory + trust chips) lives on `cursor/medicare-green-trust-flow-1ef6`. This fork keeps Medicare.gov branding, Medicare Green tokens, Inter, and the 20px body floor, then pushes the flow toward **Zocdoc-class consumer booking**: results as a booking surface, day strips, on-card times, and faster tap-to-book.

Single file, no build step. Inter loads from Google Fonts when online; system sans fallbacks work offline.

## Compare this fork vs Stay Put

| | Stay Put (`cursor/medicare-green-trust-flow-1ef6`) | This fork (`cursor/zocdoc-feel-explore-450d`) |
|---|---|---|
| Intent | Soft-launch baseline. Calm, trustworthy, above-the-fold bake-in | Critique exploration. Consumer booking speed |
| Results | Compact provider rows, 3 next slots | Bigger cards: avatar, rating line, trust badges, 4 slot chips + More times |
| Date picking | None on the list | Horizontal day strip filters which times show on cards |
| Need | Reason rows + search | Grouped typeahead (Visit reasons / Specialties), larger reason rows, chronic refine in a secondary details block |
| Filters | Trust defaults only in the sheet | Trust defaults plus Morning / Afternoon, In person / Video, This week |
| Book | Next-day control, 3-column grid, 6 times | Day strip, denser grid, View more availability when a day is empty |
| Home | Simple upcoming tile | Rich card: who / when / where / Add to calendar |
| Prototype only | Sticky bar at the bottom | **Scrolls with the page** (static). Sticky Schedule / Continue / Show doctors / Book stay at `bottom: 0` |

Open both locally and flip between them:

```bash
# Stay Put baseline (other checkout / other branch)
git checkout cursor/medicare-green-trust-flow-1ef6
python3 -m http.server 8765

# This Zocdoc-feel fork
git checkout cursor/zocdoc-feel-explore-450d
python3 -m http.server 8766
```

Or open `index.html` directly in a browser on each branch. Hash routes work offline (`#home`, `#who`, `#need`, `#results`, …). Booking persists in `localStorage`.

## Open it

1. Open `index.html` in any modern browser (double-click, or drag into Chrome/Edge/Firefox/Safari).
2. Or from this folder:

```bash
python3 -m http.server 8765 --directory /workspace
# then visit http://localhost:8765/
```

## Design Lab preview (Mobile / Desktop)

A **Design Lab** bar sits above the prototype:

- **Mobile** (default) — 390×844 phone frame with safe area. A **red dashed line** labeled **ABOVE THE FOLD** is fixed at the bottom of the visible phone.
- **Desktop** — full-width **2-column** layout (list | detail), not a scaled-up phone.

Toggle **Mobile / Desktop** in the dark bar at the top. The choice sticks in `localStorage`. Deep-link: `index.html?preview=desktop` or `?preview=mobile`.

The hint text says **Zocdoc-feel explore** so it is obvious you are not on Stay Put.

## Happy path

**Book for someone else** is a secondary outline CTA on Home.

1. **Home** — Greeting, coverage note, rich upcoming card when booked, sticky **Schedule an appointment**.
2. **Who** — Me / someone else.
3. **Coverage** — Original vs Advantage (changes what “In your plan” means).
4. **ZIP** — Location for “Near you.”
5. **Need** — Search with Visit reasons / Specialties groups, large browseable reason rows, optional chronic refine.
6. **Results** — Sticky trust chips, day strip, booking cards with badges and tappable times.
7. **Book** — New / existing patient toggle, day strip, denser time grid.
8. **Review → Book** — Then **You’re booked** and the Home upcoming card.

## Prototype only + sticky CTAs

- One **Prototype only** line, in document flow at the bottom (`position: static`). It scrolls away and can pass under the sticky CTA.
- Schedule / Continue / Show doctors / Book stay `position: sticky; bottom: 0`.
- **More below** still appears when content overflows.

## Design system

Medicare Green (`#146A5D` → `#0A352F`), secondary blue for pills/alerts, Inter, 20px body floor, 16px labels/buttons, 44px targets, 3px `#2A6FB8` focus rings. Ratings stay on cards only, never as a top-level sort.

## Files

- index.html — self-contained UI
- README.md — this file
- LIZ-NOTES.md — typography + DS flags
- refs/taxonomy.md — visit reason → specialty
- refs/patterns-and-taxonomy.md — Mobbin / Zocdoc pattern research

## Out of scope

Live Medicare APIs, real eligibility, calendars or maps, front-end frameworks, auth. This fork should not be merged as the Stay Put baseline without a separate product decision.
