# Viswa Teja Sudepalli — Portfolio Site

## What this project is
A single-page personal portfolio site for Viswa Teja Sudepalli, a Lead .NET Full
Stack Engineer (9+ years, .NET Core / Azure / React / Angular / Microservices).
The site showcases his resume content: career timeline, tech stack, case-study
projects, achievements, education, and contact info.

## Source of truth
- `index.html` — the entire site (HTML + CSS + JS in one file, no build step).
- `assets/ViswaTejaS_Resume.pdf` — the downloadable résumé linked from the
  hero and footer (two `href="assets/ViswaTejaS_Resume.pdf"` links). If the
  résumé is updated, replace this file in place and keep the filename the
  same so the download links in `index.html` don't break.
- `assets/viswa-teja-portrait.jpg` — the professional portrait used in the
  hero profile module. Keep this filename stable when replacing the image.
- Whenever the person's resume changes (new role, new project, new skill),
  update `index.html` content directly — don't regenerate the whole file from
  scratch. Treat the résumé PDF as the source of truth for facts (dates,
  titles, company names); never invent or embellish experience.

## Design standard
This project has a design skill at `skills/portfolio-design/SKILL.md`.
**Always read it before making visual or layout changes.** It defines the color system, type system, component patterns, and
the "blueprint/schematic" visual identity this site uses. Don't introduce new
colors, fonts, or component styles without checking it first — the goal is a
site that looks like it was designed once with intent, not accreted over many
edits.

## Tech constraints
- Static HTML/CSS/vanilla JS only. No build tooling, no frameworks, no
  bundler. It must run by opening the file directly or serving it from any
  static host (GitHub Pages, Azure Static Web Apps, Netlify).
- Fonts load from Google Fonts CDN (Space Grotesk, IBM Plex Sans, IBM Plex
  Mono). Keep it CDN-based — no local font files.
- No localStorage/sessionStorage dependency; the site has no persistent state.
- Respect `prefers-reduced-motion` for the animated diagram and any future
  animation — this is already implemented, keep it that way.
- Keep the whole thing accessible: sufficient color contrast, keyboard-
  reachable nav and links, semantic headings in order.
- The portrait must use descriptive alternative text, load with
  `decoding="async"`, and remain supportive of the hero copy rather than
  obscuring it.

## Content sections (current)
1. Hero — name, title, animated architecture diagram, résumé download, quick stats
2. Experience — vertical timeline, Deloitte → Cognizant → Covalence → Astoria
3. Tech Stack — grouped module cards (Languages, Frontend, Backend/.NET, Cloud,
   Database, Architecture, Security, DevOps, Reporting, IDE)
4. Full-stack Capabilities — experience, application, data, and delivery layers
5. Systems — Cloud/Azure, architecture/microservices, and AI/GenAI
6. Engineering Principles — user-centered, understandable, measurable systems
7. Projects — MIUI, AstorSafe, Pivedl case-study cards
8. Credentials — achievements + education split panel
9. Contact — email, phone, résumé download, footer

If adding a new section (e.g. blog, testimonials, certifications), follow the
existing section scaffolding pattern (`eyebrow` + `sec-title` + `sec-sub`) and
place it in the nav rail in `#rail` so the scroll-spy keeps working.

## Deployment
Default target: GitHub Pages or Azure Static Web Apps (see conversation /
deployment notes). No environment variables, no secrets, no server-side code
— any static host works.

## Tone
Copy should read as confident and factual, not salesy. Avoid buzzword
soup — every claim should trace back to something actually in the résumé.
