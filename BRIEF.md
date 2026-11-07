# Stella Point Capital — website redesign brief

Prepared 2026-11-07 for the Claude Code build session. Read this whole file before writing any HTML. Then read `content/` (the copy is final; do not rewrite it) and `CLAUDE.md` (the workflow).

## 1. What this is

A partner-review mockup of a redesigned stellapoint.com, built as real static HTML/CSS so that the winning direction becomes the shipped site with no rebuild. Two visual directions, five pages each, behind one private URL with a direction switcher. Partners see it this week.

The one content change on the whole site is the **Our Philosophy** page, which now carries eight stats from the Nov-2026 Fund II deck and the live site. Every other page uses the live site's copy verbatim.

Audience for the *site* (not the mockup): families, founders and management teams considering selling to / partnering with a lower-middle-market PE firm, plus LPs and intermediaries checking the firm out. The site has to read as **professional and personal at once** — a serious firm that people actually like working with. The firm's own words for this: "Experienced investors. Invested in people." and "constructive, not instructive."

## 2. Non-negotiables

1. **It must not read as AI-generated or templated.** Section 6 is the specific list. Every page goes through impeccable's critique and audit before it is shown to anyone.
2. **Ten pages, one system.** A single `tokens.css` per direction; shared header, footer, type scale, spacing scale, and components. A page that looks "designed on its own" fails.
3. **Copy is final.** It lives in `content/`. The only writing the build session does is microcopy (button labels, alt text, filter labels), and even those are in `content/` where they exist.
4. **Numbers only on the Philosophy stats.** No footnote marks, no disclaimer line, no as-of date on the mockup. The deck footnotes are preserved as HTML comments in `content/philosophy.md`; compliance treatment is decided by the CFO/CCO before ship.
5. **Minimal photography.** Headshots on Team only. No stock, no generated imagery, no abstract gradient blobs, no "team collaborating" illustrations. Everything else is type, color, rules, and the nine portfolio logos.
6. **Motion is restrained.** Scroll reveals, hover/focus states, and one signature moment per direction (section 5). Nothing moves on the page by default; `prefers-reduced-motion` disables all of it.

## 3. The two directions

Both share: the Stella Point mark (pull the SVG from the live site, do not redraw), navy `#003768` as the brand anchor, Futura as the house sans (Jost from Google Fonts as the web stand-in until a Futura web license is sorted — see §4), the same page structures, and the same content. They differ in palette temperature, headline typeface, and the character of the layout.

### Direction A — "Keep identity, rebuild execution"

The current brand, done properly. Partners should recognize it instantly and think "that's us, finally looking the part."

- **Palette:** navy `#003768` (primary), white `#FFFFFF`, a light sky tint `#E8EFF7` for alternating sections, slate text `#1E2A3A`, mid-slate `#5B6B7E` for secondary text, and a single mountain blue `#7A9CC6` used sparingly for rules and small accents. No gradients. The mountain ridge may appear once, as a thin line illustration or a tinted band, not as a full-bleed background on every page.
- **Type:** Jost (Futura stand-in) for everything. Headlines: Jost 400 at large sizes with tight tracking (−0.01 to −0.02em); the current site's all-caps display is retained only for eyebrows and group labels (letter-spaced small caps at 11–12px). Body: Jost 400, 17–18px, line-height 1.6, max measure ~65ch. Stats: Jost 300 at 64–96px, tabular numerals.
- **Layout:** a 12-column grid, max content width ~1200px, generous section padding (96–128px desktop). Left-aligned text throughout; no centered paragraphs except the home hero. Sections alternate white and sky tint instead of using cards.
- **Feel:** crisp, calm, institutional-but-warm. Closer to a well-set annual report than a SaaS site.

### Direction B — "Warm editorial on a navy base"

A new chapter that still belongs to the same firm. Navy stays the dominant color; warmth comes from the ground color, the serif, and the spacing.

- **Palette:** navy `#003768` (dominant — hero band, footer, headings, stats), warm cream ground `#F5F1EA`, ink `#14213D` for body text (not pure black), warm gray `#8C8577` for secondary text and rules, and one accent only: a muted brass `#B08D57`, used for the signature moment, link underlines, and the active filter — nowhere else. No gradients.
- **Type:** a real serif for headlines and stat numerals, Jost for body, labels and navigation. Serif choice, in order of preference: **Newsreader** (Google Fonts; optical sizes; warm without being precious), then Source Serif 4, then Fraunces at low "SOFT"/"WONK" settings if more character is wanted. Headlines: serif 400–500, large (56–88px on desktop), line-height 1.05–1.1, tracking −0.01em. Stats: serif 300–400 at 72–112px, old-style or tabular numerals — pick one and keep it. Body: Jost 400, 17–18px, line-height 1.65, max measure ~62ch. Eyebrows and group labels: Jost 500 small caps, letter-spaced.
- **Layout:** asymmetric — text columns offset from a 12-col grid (e.g., headline spanning cols 1–7, body in cols 2–8, stats in cols 5–12), wide outer margins, hairline rules in warm gray to separate sections instead of background changes. Big type, lots of air.
- **Feel:** a letter from a partner, not a brochure. The thing to beat is the opening pages of a good annual letter.

### Direction switcher

A tiny landing page at `/` (the repo root) with the firm name, a one-line explanation ("Two directions for the redesigned stellapoint.com — click either to browse all five pages"), and two large links: Direction A, Direction B. Each direction lives in its own folder (`/a/`, `/b/`) with identical page names. A fixed, unobtrusive pill in the bottom-right of every page lets a reviewer jump to the same page in the other direction. That is the only chrome that isn't part of the site design.

## 4. Typography and fonts — practical notes

- **Jost** via Google Fonts (weights 300, 400, 500). It is the closest open stand-in for Futura. When the firm licenses Futura (Adobe Fonts "Futura PT" is the easy route; the house Excel font is Futura Std Book), swap the `--font-sans` token and nothing else changes.
- **Newsreader** via Google Fonts (opsz axis on; weights 300–500). Load only the weights used.
- Self-host the font files in `/assets/fonts/` for the shipped site; Google Fonts links are acceptable for the mockup.
- Set `font-display: swap`; preload the two primary files.
- Numerals: `font-variant-numeric: tabular-nums` on all stat blocks and tables.

## 5. Page-by-page

All pages: header (mark left, five nav items right, Investor Login as a quiet text link), footer per `content/global.md`. The header is not sticky in Direction B; sticky-with-shrink is acceptable in A.

**Home** (`content/home.md`) — The tagline is the hero: large, left-aligned (A) or offset (B), with the single CTA "Discover More About Us". Below it, four sections in the live order — philosophy, team, partnerships, news — each one headline plus one link, separated by alternating tints (A) or hairlines (B). The partnerships section shows the nine logos as one monochrome row. **No carousel.** The page is short on purpose; the live site's five-slide carousel becomes five stacked moments.

**About** (`content/about.md`) — Three prose sections, then "The Criteria" as three stacked rows (label left, value right, hairline between — not icon cards), "Our Sectors" as three columns of text with the sector name as a small heading, closing with the "What We Believe In" statement and link. No photos.

**Our Philosophy** (`content/philosophy.md`) — The showpiece. Order: hero → "We Invest in People" with the "People first. Always." pull line set at display size → **the stat block** (eight stats in four labelled groups; layout is free — 2×4 on desktop is the baseline, stacked groups on mobile) → "Culture is at Our Core" with the optional three proof points → "Partners who care" as a plain three-item list → closing + CTA. The stat block is the signature moment (below). Group labels and stat labels are small; the numerals do the talking.

**Team** (`content/team.md`) — Intro paragraph, then the thirteen headshots in a consistent crop with name and title beneath. Order by seniority or alphabetically (pick one; apply to both directions; not the live order). No round masks, no hover zoom; a simple underline or color shift on the name is enough. Closing "Extended Team" paragraph and link.

**Partnerships** (`content/partnerships.md`) — Intro line, a working All / Unrealized / Realized filter as three text buttons, then nine logo tiles (monochrome, consistent box) with the one-line description and a small text status label. The filter animates the grid with a short fade; nothing else moves.

**News** (`content/news.md`) — A dated index, newest first: date in small caps, headline as a link, one-line lead. Featured item set larger at the top. No thumbnails.

### Signature moments (one per direction)

- **Direction A — "The numbers arrive."** On the Philosophy stat block, as it enters the viewport, each numeral fades up 8px and settles, staggered 60ms left-to-right, once. A hairline draws across the top of the block from left to right over 600ms. No count-ups.
- **Direction B — "The rule draws."** On every page, the primary hairline under the hero headline draws from 0 to 100% width over 700ms as the page loads, and the Philosophy stats share this: each group's rule draws as the group enters the viewport, with the numerals fading in behind it. Brass accent on the rule only here, nowhere else.

Everything else is: 150–200ms hover transitions on links and buttons; a 300ms opacity/translate reveal (≤12px) on sections entering the viewport, once, threshold 0.15; filter fade on Partnerships. `@media (prefers-reduced-motion: reduce)` turns all of it off.

## 6. Anti-slop rules (the checklist impeccable's audit runs against)

Fail any page that has:

- A hero with a gradient background, a blurred color blob, or a dark overlay on a stock photo.
- Three-up (or four-up) feature cards with icons, especially with rounded corners and drop shadows.
- Centered paragraphs of body text, or centered everything.
- Inter, Roboto, Open Sans, Poppins, Montserrat, or system-ui as the display face.
- Pure black text on pure white in Direction B; pure black anywhere.
- Rounded pill buttons with gradients or glows. Buttons are rectangles (A) or text links with an underline (B).
- Decorative emoji or icon fonts used as bullets.
- A carousel, slider, or auto-advancing anything.
- Count-up number animations; parallax; elements that keep moving after the page has settled.
- Lorem ipsum, placeholder names, or "[Insert]" anywhere.
- Generic copy added by the build ("Empowering businesses to reach their full potential"). The copy is in `content/`; if a section seems to need more words, it doesn't.
- Identical section rhythm on every page (heading → paragraph → three cards → CTA, repeat).
- Drop shadows deeper than 1px on anything.
- Uniform 16/24/32px spacing with no larger values — the space between sections must be visibly larger than the space within them.
- Headshots in circles.
- Colored status pills, badges, or tags. Status is text.
- An "AI-generated" tell in the markup: `div` soup with no semantic landmarks, `class="container mx-auto"` everywhere, inline styles. Use `header / nav / main / section / footer`, real headings in order, and the token system.

Pass criteria, per page: a reviewer can tell which direction they're in within one second; the page uses at most two typefaces and five colors; there is one obvious thing to read first; the layout has at least one deliberate asymmetry (B) or one deliberate full-width band (A); nothing on the page would need to change if the firm's name were covered up — the copy, logos and headshots carry the identity, not decoration.

## 7. Technical envelope

- Static HTML, one shared `styles.css` per direction importing `tokens.css`, one small `motion.js` (IntersectionObserver reveals, filter, direction switcher). No framework, no build step, no Tailwind. Vanilla CSS with custom properties, grid, and `clamp()` for fluid type.
- Responsive from 360px to 1600px. Mobile is a first-class view — partners will open this on their phones.
- Lighthouse ≥ 95 on performance and accessibility. Real alt text (names for headshots, company names for logos). Focus states visible. Color contrast ≥ 4.5:1 for body, ≥ 3:1 for large display text.
- Hosted on GitHub Pages from the repo's `main` branch (or `/docs`). Note: Pages from a *private* repo requires a paid GitHub plan; on a free account the repo must be public. Nothing in the mockup is non-public — the deck stats are the only new content and they are being put on the public site anyway — but confirm with Howard before the repo goes public if that is the route.

## 8. Sequencing (this week)

1. Repo scaffold, tokens for both directions, shared header/footer, direction switcher landing page.
2. Direction A: Home, Philosophy. Run critique + polish. Show Nikhil.
3. Direction A: About, Team, Partnerships, News. Critique + polish.
4. Direction B: Home, Philosophy (the comparison partners will actually make). Critique + polish. Show Nikhil.
5. Direction B: About, Team, Partnerships, News.
6. Audit every page in both directions against §6. Mobile pass. Lighthouse pass.
7. Push to Pages; send the URL.

If time runs out, steps 1–4 are the floor: all five pages in A, the two that matter in B. Do not ship a page that hasn't had a critique pass to save time; drop the page instead.

## 9. Open items (not blockers)

- Team titles and About criteria on the live site differ from the Nov-2026 deck. Logged in `notes/DISCREPANCIES.md`; the mockup uses the live site as instructed. Decide before ship.
- Futura web license (Adobe Fonts "Futura PT" or a Monotype web license). Jost until then.
- Whether the 40+ and 150% live-site stats are still accurate and need an as-of date — Howard.
- Which investor portal (CSC Viewpoint vs. AltaReturn) is current — the live header and footer link to different ones. Maisie/Howard.
- Contact Us is a footer anchor on the live site; decide whether it gets a real page.
