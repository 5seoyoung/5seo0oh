# Seoyoung Oh — Personal Website

Static personal site (Medical AI). No build step, no dependencies — just HTML + CSS.
Open `index.html` in a browser to preview, or serve locally:

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Structure

```
.
├── index.html            # Home page
├── experience.html       # ┐
├── publications.html     # ├─ Section pages (one per nav button)
├── projects.html         # │
├── awards.html           # ┘
├── assets/
│   ├── css/
│   │   ├── base.css      # Design tokens (colours/fonts), layout, animation — shared by ALL pages
│   │   ├── home.css      # Styles only for index.html
│   │   └── section.css   # Styles only for the section pages
│   └── img/
│       └── profile.jpg   # Profile photo
└── README.md
```

## How to maintain it

**Change a colour or font (whole site at once)**
Edit the variables at the top of `assets/css/base.css` (`--ink`, `--bg`, `--soft`, …).
Both light and dark mode values live there. Nothing else needs touching.

**Add / edit content on a section page**
Open the section's `.html` file and copy an existing `<article class="entry"> … </article>`
block. Each entry has:
- `.when`   → date / year
- `.entry-title` → title
- `.entry-org`   → org / venue / stack
- `.entry-desc`  → one-line description
- `.entry-links` → optional links (Paper, Code, Demo, …)

**Add a brand-new section (new nav button)**
1. Copy an existing section page (e.g. `awards.html`) to `newsection.html`.
2. Update its `<title>`, the `<h1>`, and mark its own link `class="on"` in the `.subnav`.
3. Add the same link to the `.subnav` of every other section page.
4. Add `<a class="sec" href="newsection.html">New Section</a>` to the `.sections` nav in `index.html`.

**Replace the profile photo**
Drop the new file in `assets/img/` and update the `src` in `index.html` (keep it named
`profile.jpg` to change nothing else).

**Update the "Last updated" date**
It appears in the `<footer>` of `index.html` and each section page.

## Conventions
- One page = one `.html` file at the repo root (keeps URLs clean, e.g. `/projects.html`).
- All shared design lives in `base.css` — never hard-code a colour in a page or a page-specific CSS file; use a `var(--…)` token.
- Every page loads `base.css` first, then its own stylesheet.
