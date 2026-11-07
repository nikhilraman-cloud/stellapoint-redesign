# stellapoint.com redesign — build pack

Handoff from the 2026-11-07 planning session to the Claude Code build session.

## What's in here

```
BRIEF.md                 the design brief — read first
CLAUDE.md                drop at the root of the new repo; it drives the build session
content/                 final copy for all five pages + global nav/footer + stats.json
  home.md
  about.md
  philosophy.md          the one page with new content; eight stats; deck footnotes as HTML comments
  team.md                13 people, headshot URLs
  partnerships.md        9 companies, logo URLs, filter spec
  news.md
  global.md              nav, footer, titles, portal links
  stats.json             the eight stats with origin + footnotes, machine-readable
notes/
  DECISIONS.md           the 19 decisions from the planning interview and why
  DISCREPANCIES.md       live site vs. Nov-2026 deck — things to settle before ship, not on the mockup
reference/
  deck-slide-06-partnership-model.png     source of the six deck stats
  deck-slide-05-key-characteristics.png   source of the "Partners who care" list and culture language
```

## Starting the build session

1. Create the repo (`stellapoint-redesign`), copy this folder's contents into it, keep `CLAUDE.md` at the root.
2. Open Claude Code in the repo with impeccable and frontend-design available.
3. First prompt, roughly:

   > Read CLAUDE.md, then BRIEF.md in full, then every file in content/ and notes/. Then scaffold the repo per CLAUDE.md (switcher landing page, /a and /b folders, tokens.css for each direction, shared header/footer, motion.js) and build Direction A's Home and Philosophy pages. Run the impeccable critique and polish on both, audit them against BRIEF.md §6, and show me screenshots at 1440 and 390 before continuing.

4. Review Home + Philosophy in A before letting it continue to the other three pages, then B.

## Things to decide outside the build

See `notes/DISCREPANCIES.md` and `BRIEF.md` §9: Team titles, About criteria, the two investor portals, Futura licensing, and stat footnotes (Howard).
