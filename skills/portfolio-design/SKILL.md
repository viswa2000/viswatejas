---
name: portfolio-design
description: Design standard for Viswa Teja Sudepalli's personal portfolio website (index.html) — a "blueprint/schematic" themed dark UI for a .NET/Azure full-stack engineer. Use this skill whenever creating, editing, extending, or restyling this portfolio site, adding new sections, building new pages for it, or making any HTML/CSS/JS change that affects its look and feel. Also use it if asked to build a similar personal/professional portfolio site "in the same style" or to keep a new page "consistent with the existing design." Covers color tokens, typography, spacing, component patterns (cards, timeline, tags, nav rail, diagram), motion rules, and accessibility requirements. Do not invent new colors, fonts, or component styles without checking this first.
---

# Portfolio Design Standard — Blueprint/Schematic System

## Concept
The site's visual identity is a technical **engineering blueprint / schematic
diagram** aesthetic — deep navy "drafting table" background, cyan circuit-style
linework, corner brackets like those on architectural drawings, and monospace
labels like part numbers on a schematic. This is deliberate: the subject is a
cloud architect who designs system diagrams for a living, so the site itself
reads like one of his own architecture diagrams brought to life.

**Do not drift toward generic templates.** Specifically avoid: cream
background + serif + terracotta accent (generic "editorial" template), pure
black + neon purple/pink glow (generic "SaaS dark mode" template), or a plain
white card-grid resume layout. If a change would nudge the site toward any of
those, stop and reconsider — it breaks the concept.

## Color tokens
Always use CSS custom properties, never hard-code hex values inline.

```css
--void:      #0A1420   /* page background */
--panel:     #101F32   /* card / panel background */
--panel-alt: #0C1928   /* alt panel, chips, stripes */
--grid-line: rgba(79,209,197,0.07)  /* faint background dot/line grid */
--hairline:  #1E3348   /* borders, dividers */
--cyan:      #4FD1C5   /* primary accent — links, active states, glow */
--cyan-dim:  #2B6F6A   /* secondary/muted accent */
--cyan-glow: rgba(79,209,197,0.35)  /* box/drop-shadow glow color */
--amber:     #F0A84E   /* SPARING use only — achievements/awards highlight */
--text-hi:   #EDF3F8   /* primary text */
--text-mid:  #93A9C4   /* secondary text, descriptions */
--text-low:  #54677F   /* tertiary text, captions, eyebrow labels */
```

Rules:
- `--amber` is a highlight-only color. It appears in exactly two places today
  (achievement star markers). Do not use it for general accents, buttons, or
  links — that dilutes it as a signal. Cyan is the workhorse accent.
- Never place `--text-low` text on `--panel-alt` or lighter — check contrast;
  `--text-low` is for text sitting directly on `--void` or `--panel`.
- New sections must use `--panel` (or `--panel-alt` for nested/inset areas),
  never a new background color.

## Typography
```
Display (headings, name, section titles): 'Space Grotesk', 600–700 weight
Body (paragraphs, descriptions):           'IBM Plex Sans', 400–500 weight
Mono (labels, tags, dates, nav, eyebrows):  'IBM Plex Mono', 400–600 weight
```
Loaded via Google Fonts CDN — keep it CDN-based, don't self-host or swap in
different families.

- Section eyebrows (small label above every `h2`) are always mono, uppercase,
  cyan, prefixed with `//` — this is a signature recurring motif, keep it.
- Body copy stays in `--text-mid`, never full white — full white (`--text-hi`)
  is reserved for headings, names, and emphasis.
- Letter-spacing on mono labels: `.08em`–`.12em`. Don't tighten this; the
  slight spread is what makes it read as "technical labeling" rather than
  ordinary UI copy.

## Signature component patterns

**Corner-bracket panel** (`.bracket` / stack cards / project cards): a card
with small L-shaped cyan brackets at each corner, evoking drafting-sheet
frame marks. Use this treatment for any new "featured" card-level content.
Don't substitute a generic `border-radius` rounded card for it — sharp
corners + bracket marks are core to the concept.

**Nav rail**: fixed vertical dot-and-label rail on desktop, hidden below
900px, with scroll-spy (IntersectionObserver) highlighting the active
section in cyan. Any new top-level section must get an entry here.

**Timeline**: vertical line + hollow circles at each entry, with a horizontal
"duration bar" (`.t-bar`) whose fill width roughly represents relative
tenure. The current/active role gets a solid cyan ring and an "ACTIVE" mono
badge. Reuse this pattern for any new chronological content (don't invent a
different timeline style).

**Tag chips** (`.tag`): mono font, `--panel-alt` background, `--hairline`
border, small radius (3px). Used for every skill/tech label across the site.
Keep radius small — large rounded pill chips break the "schematic" feel.

**Diagram (hero signature element)**: an SVG "orchestration" diagram — a
central node representing the person, connected via dashed lines to
satellite nodes (tech/skills), with small pulse dots animated along the
connector paths via `animateMotion`. This is the single most important
visual on the page — if the hero is ever redesigned, this diagram (or a
clear evolution of it) should stay, since it's the concept's clearest
expression. Always wrap the pulse animation in a
`prefers-reduced-motion` check and skip rendering it for reduced-motion users
(static nodes/lines still show).

**Portrait (hero profile module)**: when a professional portrait is available,
place it beside the hero copy in a sharp `.bracket` panel using the project's
existing panel tokens. Use a restrained crop, a thin cyan frame, and no
decorative filters that reduce recognition. The image must have descriptive
alt text and `decoding="async"`; never let it replace the text introduction.

## Layout & spacing
- Content max-width: `1080px`, centered, `32px` side padding (`.wrap`).
- Section vertical rhythm: `96px` top/bottom padding per `section`.
- Grouped cards (stack modules, split panels) use a `1px` gap filled with
  `--hairline` color so borders between cards render as thin schematic
  divider lines rather than doubled borders.
- Background: a very faint `42px` grid of `--grid-line` covers the whole
  page (`background-image` with two linear-gradients) — keep this on `body`
  globally, don't scope it to individual sections.

## Motion
- Keep motion minimal and purposeful: the hero diagram's pulse dots, a
  blinking "status" dot in the topbar/hero-kicker, and hover states
  (`translateY(-1px)` + glow on primary buttons). Don't add decorative
  scroll animations, parallax, or entrance fade-ins beyond this — the
  restraint is part of the "engineering precision" feel.
- Every animation must respect `prefers-reduced-motion: reduce`.

## Accessibility requirements (non-negotiable)
- Maintain heading order (one `h1` in hero, `h2` per section).
- All interactive elements (nav links, buttons, download links) must be
  reachable by keyboard and show the `:focus-visible` cyan outline already
  defined globally — don't override it away on new elements.
- Text contrast: body text is `--text-mid` (#93A9C4) on `--void`/`--panel`
  (#0A1420/#101F32), which passes AA for normal text size — don't go dimmer
  than that for body copy. Only decorative/caption text may use `--text-low`.
- Decorative SVG (the hero diagram) must be `aria-hidden="true"` since it's
  purely illustrative and its content (tech names) is already present as
  text elsewhere on the page.

## When extending the site
1. Re-read this file before adding a section, page, or component.
2. Reuse an existing pattern (bracket card, timeline, tag row, split panel)
   before inventing a new one. This is a small, single-purpose site — pattern
   reuse is more valuable here than novelty.
3. If a genuinely new pattern is needed, it must still resolve to the same
   token set (colors/type above) and keep sharp corners / mono labels /
   cyan-accent conventions.
4. Update `CLAUDE.md`'s "Content sections" list if you add or remove a
   top-level section.
5. Keep the portrait asset at `assets/viswa-teja-portrait.jpg` so the hero
  markup and future edits have one stable reference.
