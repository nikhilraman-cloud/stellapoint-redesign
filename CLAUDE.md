# CLAUDE.md — stellapoint-redesign

This repo is a partner-review mockup of a redesigned stellapoint.com that will become the shipped site. Two visual directions (A and B), five pages each, static HTML/CSS/JS, hosted on GitHub Pages.

## Read first, in this order

1. `BRIEF.md` — the design brief. Both directions, page-by-page, motion, the anti-slop checklist (§6), sequencing.
2. `content/` — the copy. It is final. Do not rewrite, "improve", or add to it. `content/philosophy.md` is the only page with new content; the rest is the live site verbatim.
3. `notes/DECISIONS.md` — why things are the way they are. Don't relitigate these.

## Skills and plugins to use

- **impeccable** — the design process. Use it on every page: craft the page from the brief, then critique, then polish, then audit against `BRIEF.md` §6 before a page is considered done. If your installed version's command names differ, check its README; the sequence (make → critique → polish → audit) is what matters.
- **frontend-design** — load it at the start of each direction, before writing the first page of that direction, for the aesthetic brief. It reinforces the type and layout choices in `BRIEF.md` §3.
- Do **not** use open-design / design-canvas tooling here. The output of this repo is the shipping code.

## Repo layout

```
/                      direction switcher landing page (index.html)
/a/                    Direction A — index.html, about.html, philosophy.html, team.html, partnerships.html, news.html
/b/                    Direction B — same six files
/shared/               switcher.js (the bottom-right pill), reset.css, motion.js
/a/css/tokens.css      Direction A tokens (colors, type, spacing)
/a/css/styles.css      Direction A styles (imports tokens.css)
/b/css/tokens.css      Direction B tokens
/b/css/styles.css      Direction B styles
/assets/               logo SVGs, portfolio logos (monochrome + original), headshots, fonts (if self-hosted)
/content/              the copy (markdown + stats.json) — source of truth, not served
/notes/                decisions, discrepancies
/reference/            deck slide images for the stat block
BRIEF.md
CLAUDE.md
```

Page names are identical in `/a/` and `/b/` so the switcher can map `/a/team.html` ↔ `/b/team.html` by path.

## Hard rules

- **Copy comes from `content/`.** If a layout needs more text than exists, change the layout, not the text. No lorem ipsum, no placeholder names, no "[TBD]".
- **Stats are numbers only.** No footnote marks, disclaimer lines, or as-of dates on the Philosophy stat block. The deck footnotes are in HTML comments inside `content/philosophy.md`; carry them into the page source as comments, never into rendered output.
- **No photography except Team headshots.** No stock, no generated images, no gradient/blob backgrounds.
- **No frameworks, no build step, no Tailwind.** Vanilla CSS with custom properties; `clamp()` for fluid type; CSS grid. One `motion.js` using IntersectionObserver. Everything must open from `file://` and from GitHub Pages without a server.
- **Both directions share the same page structure.** Change A and B together when a structural change is needed. Tokens and styles differ; the HTML skeleton should be nearly identical.
- **Semantic HTML.** `header / nav / main / section / footer`, headings in order, real `alt` text, visible focus states, skip link. Lighthouse ≥ 95 performance and accessibility on every page.
- **Motion**: only what `BRIEF.md` §5 specifies. `prefers-reduced-motion: reduce` disables all of it. No count-ups, no parallax, no carousels.
- **Fonts**: Jost (Futura stand-in) and, in B only, Newsreader. Load only the weights used. Keep `--font-sans` / `--font-serif` tokens so Futura can be swapped in later with no other change.
- **Third-party logos and headshots** are pulled from the live site (URLs in `content/`). Download them into `/assets/`; don't hotlink. Normalize portfolio logos to monochrome; keep originals in `/assets/logos/original/`.

## Workflow per page

1. Read the page's `content/*.md` including the HTML comments (build notes are there).
2. Build the page in Direction A against `BRIEF.md` §3 and §5.
3. Open it in a browser at 1440, 1024 and 390 wide. Screenshot all three.
4. Critique (impeccable), fix, polish.
5. Audit against `BRIEF.md` §6. Any item on that list = not done.
6. Repeat for Direction B.
7. Commit with a message naming the page and direction, e.g. `A: philosophy — stat block + signature reveal`.

Sequencing for the week is in `BRIEF.md` §8. Steps 1–4 there are the floor.

## Before pushing to Pages

- Every page in both directions has been through critique and audit.
- Mobile pass on all ten pages + the switcher.
- Switcher pill works on every page and maps to the same page in the other direction.
- Partnerships filter works.
- No console errors; no 404s in the network tab.
- `grep -ri "lorem\|TODO\|TBD\|placeholder" a/ b/` returns nothing.

## Things that are deliberately deferred (don't "fix" them)

- Live-site Team titles and About criteria are out of date vs. the Nov-2026 deck. Using the live site as-is was a deliberate decision. See `notes/DISCREPANCIES.md`.
- Nikhil Raman's live profile slug is `/team_member/name-here/`. Leave it.
- Header and footer Investor Login links go to two different portals. Leave both.
- Stats footnotes/disclaimers. Compliance review before ship.
