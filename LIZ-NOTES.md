# Liz Wilson walkthrough — flags for scheduler work (Sep 4, 2026)

## Typography (critical)
- Design system has body / body-large / body-XL.
- 16px = 1rem still (do not break rem math).
- 20px is the practical body floor for most UI copy (body-large).
- 16px OK for labels, disclaimer/legal, a few chrome bits.
- CMS will call out text size. Default to 20+.

## Design system / Figma
- Liz built Triptych's Figma DS page: messy middle ground, directional for CMS DS team.
- CMS owns the real library (multiple systems in one; archaic, slowly updating).
- Pull components from Assets when doing handoff.
- Row component = Square-inspired unification (use it).
- Concepting can be freer; dev handoff must be component-perfect and consistent.
- Cursor/Claude to Figma auto-translate has been messy before. Prefer intentional Figma rebuild for handoff.

## Appointment scheduler context
- Baseline page = CMS old prototype reskinned to new DS, not deep UX rethink.
- Start a fresh v2 page rather than overloading the sensitive v1 page.
- Soft launch of v1 after Labor Day (silent/soft, not big marketing).
- Mobile styles today were done by CMS, not Triptych. Free reign on mobile; they want mobile explorations.
- Multiple different eng teams per surface. Handoff audience varies.

## Process / access
- Own Cursor / GitHub / Drive for now; Phil owns shared repo.
- Research / readouts: Box + Anya dashboard doc; Confluence often blocked.
- Personas = helpful context, not a blocker for appointment user stories.
- Condition taxonomy: ask David/CMS (or Zocdoc); Claude guess OK now, backfill later.
- Pace: fast Tue-Thu iterations; David/Anya protect focus.

## Tokens applied (Sep 4, 2026 — Tuesday soft-launch pass)
- Primary is **Medicare Green** `#146A5D` (not Ocean `#0071bc`). Header `#0A352F`.
- Inter + 20px body-large floor; 16px labels / button text.
- Visit-reason chips (Medicare Zocdoc-style) + chronic refine group.
- Trust defaults stay sticky; ratings stay on cards only.

## Open threads
- Zocdoc call on data reliability (in-network / accepting new patients).
- Ping David for condition taxonomy when ready (starter list is in `refs/taxonomy.md`).
- Figma edit access still pending (view-only for now).
