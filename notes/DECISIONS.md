# Decisions log — 2026-11-07 planning session

Resolved in a structured interview (grill-me) before the build. Do not relitigate in the build session; if one of these turns out to be wrong in practice, note it and ask Nikhil.

| # | Question | Decision |
|---|---|---|
| 1 | Purpose | Partner buy-in on a redesign, then ship it ourselves. The mockup code is the production code. |
| 2 | Scope | All five nav pages (About, Our Philosophy, Team, Partnerships, News). |
| 3 | Brand distance | Show two directions: A keeps the identity and rebuilds execution; B is bolder. |
| 4 | Direction distribution | All five pages in both directions (ten pages). Given the one-week timeline, sequence: A ×5 → B Home + Philosophy → B remaining three. |
| 5 | Philosophy content | Incorporate the six partnership-slide stats. Layout does not need to mirror the slide. |
| 6 | Existing stats | Keep the two existing site stats (40+, 150%). Eight stats total. |
| 7 | Philosophy copy | Light edit of the existing copy, tightened, with concrete language lifted from deck slides 5, 6 and 35. |
| 8 | Other pages' content | Current live-site copy only, verbatim. Nothing new from the deck outside Philosophy. |
| 9 | Imagery | Mostly typographic; headshots on Team only; no stock or generated imagery. |
| 10 | Stack | Whatever is easiest to show partners while allowing animation → static HTML/CSS with a small vanilla-JS motion layer. |
| 11 | Delivery | One private URL with a Direction A / Direction B switcher. |
| 12 | Direction B character | Warm editorial, but navy stays the base color so A and B read as siblings. |
| 13 | Typography | A: Futura (Jost stand-in) everywhere. B: serif headlines + Futura/Jost body and labels. |
| 14 | Motion | Restrained: scroll reveals, hover states, one signature moment per direction. |
| 15 | Tooling | impeccable for process (craft → critique → polish → audit); frontend-design loaded alongside for aesthetic direction; open-design skipped because the mockup code ships. |
| 16 | Handoff | This pack: brief, content, CLAUDE.md, notes. |
| 17 | Hosting | GitHub repo + GitHub Pages. (Pages from a private repo needs a paid plan; otherwise the repo is public.) |
| 18 | Footnotes / disclaimers | Numbers only on the mockup. Treatment decided at compliance review (Howard) before ship. |
| 19 | Timing | Partners see it this week. |

## Reasoning worth keeping

- **Why warm editorial for B:** the audience is families, founders and management teams choosing a partner. A serif, warm neutrals and generous space read as considered and human; a strict Swiss grid reads quantitative and cool (right for a credit fund); dark/high-contrast reads as a tech VC. Warm editorial also carries eight stats best — large serif numerals feel like an annual letter, not a pricing page — and it is the direction least likely to be mistaken for a template.
- **Why real HTML from day one:** the decision to ship it ourselves means a design-canvas output would have to be rebuilt. Building in the shipping medium removes a whole translation step and lets impeccable's critique loop run on the real thing.
- **Why no carousel on Home:** the live site's five-slide hero is the single most "template" element it has. Five stacked moments say the same five things and are readable, linkable and accessible.
- **Why stats are numbers-only on the mockup:** the footnote/disclaimer treatment is a compliance decision, and designing it in before Howard has weighed in risks anchoring him to a layout. The footnotes are preserved in source comments so nothing is lost.
