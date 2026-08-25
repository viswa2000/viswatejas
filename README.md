# Viswa Teja Sudepalli — Portfolio

Single-page portfolio site for a Lead .NET Full Stack Engineer. No build
step — just HTML, CSS, and vanilla JS in one file, plus a résumé PDF asset.

## Folder structure

```
portfolio-project/
├── index.html                        ← the entire site (HTML+CSS+JS)
├── assets/
│   ├── ViswaTejaS_Resume.pdf         ← downloadable résumé, linked from the site
│   └── viswatejaS.jpg                ← profile image
├── CLAUDE.md                         ← project context for Claude Code / AI-assisted edits
├── skills/
│   └── portfolio-design/
│       └── SKILL.md                  ← design system standard (colors, type, components)
├── .vscode/
│   ├── extensions.json               ← recommends Live Server
│   └── settings.json
└── README.md                         ← this file
```

## Running it locally

No install needed — it's a static file. Two easy options:

**Option 1 — just open it**
Double-click `index.html`, or right-click → "Open with" your browser.

**Option 2 — Live Server (recommended, auto-reloads on save)**
1. Open this folder in VS Code (`File → Open Folder…`).
2. Install the recommended **Live Server** extension when prompted (or search
   "Live Server" by Ritwick Dey in the Extensions panel).
3. Right-click `index.html` → **"Open with Live Server"**.

## Editing with Claude Code

This project includes `CLAUDE.md` and a design-standard skill at
`skills/portfolio-design/SKILL.md`. If you're using Claude Code (or another
AI coding assistant that reads these), it will automatically pick up the
project context and design rules before making changes — so new sections or
edits stay visually consistent with the rest of the site.

To ask for changes, just describe them naturally, e.g.:
- "Add a certifications section between Projects and Credentials"
- "Update the Deloitte role dates — I got promoted"
- "Add a testimonials section"

## Deploying

This is a static site — it works on any static host:
- **GitHub Pages**: push this folder to a repo, enable Pages on the `main`
  branch root.
- **Azure Static Web Apps**: point it at this folder with no build command.
- **Netlify / Vercel**: drag-and-drop deploy, no build settings needed.

If you rename or move `index.html` relative to `assets/`, update the two
`assets/ViswaTejaS_Resume.pdf` links inside `index.html` to match.
