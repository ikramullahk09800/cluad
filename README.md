# FastVPS.com — Website Documentation

> ⚠️ **READ THIS FILE FIRST — BEFORE MAKING ANY EDIT.**
> Any person or AI assistant (including Claude) working on this repo must read this
> README in full before changing any file. After making changes, update the
> **Changelog** section at the bottom of this file so the design record stays accurate.
> This keeps the whole site visually and structurally consistent over time.

---

## 1. Project Overview

Static marketing website for **FastVPS.com**, a VPS hosting provider. Pure HTML/CSS/JS
(no build step, no framework) — hosted on **GitHub Pages**.

Live site: `https://ikramullahk09800.github.io/cluad/`

## 2. File Structure

```
├── index.html              Home page (hero, features, pricing preview, OS options, guarantee)
├── pricing.html            Dedicated pricing page (full plan grid, 2GB–32GB)
├── login.html              Login page
├── signup.html             Signup page
├── style.css                Global stylesheet — shared by ALL pages
├── auth.css                  Extra styles for login.html / signup.html only
├── rack-illustration.svg     Original custom server-rack illustration (index.html hero visual)
├── hero-illustration.svg     unDraw-based illustration (MIT licensed, recolored) — used as pricing.html hero visual (kept distinct from index.html's illustration)
└── README.md                This file
```

**Every HTML page loads `style.css`.** `login.html` and `signup.html` additionally load
`auth.css` for form-specific styling. Always keep the `?v=N` cache-busting query string
on `style.css` links in sync across **all** pages — if you edit `style.css`, bump the
version number on every page that references it (see Changelog for current version).

## 3. Design System

### Color Palette (brand = warm coral/cream, "Claude-inspired")

| Color | Hex | Usage |
|---|---|---|
| Coral (primary brand) | `#CC785C` | Buttons, links, accents, logo |
| Coral dark (hover) | `#B8694F` | Button hover states |
| Coral light | `#E8B49A` / `#D98F6F` | Secondary accents, gradients |
| Cream background | `#F5F5F0` | Page background |
| Off-white panel | `#EDE8E3` / `#E8E4DF` | Card/section backgrounds, borders |
| Charcoal text | `#2D2D2D` | Headings, primary text |
| Muted gray text | `#6B6B6B` / `#4A4A4A` | Body/paragraph text |
| Dark hero background | `#1A1713` → `#2E2A24` (radial gradient) | Hero sections (`.hero-dark`), pricing hero, guarantee accents |
| Cream on dark | `#F5F1EA` | Headings on dark hero backgrounds |
| Muted on dark | `#B8B0A3` | Paragraph text on dark hero backgrounds |

**Rule:** Never introduce a new color outside this palette without a reason. If a new
shade is genuinely needed, add it to this table.

### Typography

- **Body/UI font:** `-apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Helvetica Neue', Arial, sans-serif`
- **Monospace (terminal/code accents):** `'SF Mono', 'Consolas', 'Menlo', monospace`
- Headings are bold (700), tight letter-spacing (`-0.5px` to `-1px`) on large sizes.

### Key Reusable Components (defined in `style.css`)

| Class | Purpose |
|---|---|
| `.hero` / `.hero-dark` | Dark isometric hero section (used on `index.html` top and `pricing.html` top) |
| `.hero-inner` | Two-column grid: `.hero-visual` (illustration) + `.hero-content` (copy) |
| `.hero-h1-dark` / `.hero-p-dark` | Heading/paragraph styles for the dark hero |
| `.eyebrow` / `.eyebrow-light` | Small uppercase label above headings (light = for dark backgrounds) |
| `.btn-primary` | Solid coral CTA button |
| `.btn-secondary` | Text-link style CTA (underline on hover) |
| `.btn-outline-light` | Outlined button for dark backgrounds |
| `.section-head` | Centered heading block used above Features / Pricing / OS sections (eyebrow + h2 + p) |
| `.pricing-cards` / `.price-card` | Pricing card grid (flex-wrap, centers automatically) |
| `.guarantee-section` | Coral-gradient "30-day money-back guarantee" banner (reused on `index.html` and `pricing.html`) |
| `.auth-card` / `.auth-form` | Login/signup card styling (in `auth.css`) |
| `.nav-toggle` / `.nav-links` / `.nav-overlay` | Mobile hamburger menu — slides in **from the right side** on screens ≤768px |

### Illustrations

- `rack-illustration.svg` — hand-built original isometric server-rack graphic (cabinet,
  rack units, vents, LEDs). Used as the hero visual. **100% original, no copyright risk.**
- Do **not** embed images from stock sites (Freepik, Pngtree, CleanPNG, Vecteezy, iStock,
  premium theme demos, etc.) without a verified, explicit commercial license. When in
  doubt, build an original SVG or use a properly MIT/CC0-licensed source instead.

## 4. Pages

| Page | Purpose | Nav link |
|---|---|---|
| `index.html` | Home — hero, features, pricing preview (3 plans), OS options, guarantee | Home |
| `pricing.html` | Full pricing grid — 5 plans, 2GB to 32GB RAM | Pricing |
| `login.html` | Login form (**static/demo only — no real backend auth yet**) | Log In |
| `signup.html` | Signup form (**static/demo only — no real backend auth yet**) | Get Started / Sign Up |

⚠️ Login/signup forms are currently **frontend-only** — they show a demo message on
submit. No database or auth backend is connected (GitHub Pages is static hosting).
If real auth is added later (e.g. Firebase/Supabase), update this section.

## 5. Current Pricing Plans (as of latest edit — keep this table in sync with the HTML!)

| Plan | RAM | vCPU | SSD | Bandwidth | Price |
|---|---|---|---|---|---|
| Starter | 2 GB | 1 | 50 GB | 2 TB | $5/mo |
| Standard (Most Popular) | 4 GB | 2 | 80 GB | 4 TB | $10/mo |
| Business | 8 GB | 4 | 160 GB | 6 TB | $20/mo |
| Professional | 16 GB | 6 | 320 GB | 8 TB | $40/mo |
| Enterprise | 32 GB | 8 | 640 GB | Unlimited | $75/mo |

(`index.html` shows only Starter / Standard / Premium as a shorter preview; the full
5-plan grid lives on `pricing.html`.)

## 6. Mobile Behavior

- Nav collapses to a **hamburger icon** below 768px width.
- Tapping it slides the menu **in from the right edge** with a dark overlay behind it;
  tapping the overlay or a link closes it.
- Hero stacks to a single column (illustration above text) below 900px.
- Hero illustration max-width: 190px (tablet), 160px (small phones) — keep it modest,
  it should never dominate the hero.

## 7. Rules for Future Edits (for any human or AI, including Claude)

1.  **Read this README before editing anything.**
2.  Reuse existing classes/components listed above instead of inventing new ones when a
    suitable one already exists — this is what keeps every page visually consistent.
3.  Stick to the color palette in Section 3 unless there's a good reason to expand it —
    and if you do, document the new color here.
4.  Never copy images/illustrations from stock or template sites without a verified
    license. Prefer original SVGs or MIT/CC0-licensed assets.
5.  When you edit `style.css`, bump the `?v=N` query string on **every** HTML page that
    loads it, so browsers don't serve a stale cached copy.
6.  **After finishing any change, add a dated entry to the Changelog below** describing
    what changed and why — this file is the single source of truth for the site's design
    history.

---

## 8. Changelog

| Date | Change |
|---|---|
| 2026-08-19 | Initial site uploaded (index.html, style.css) |
| 2026-08-19 | Added login.html / signup.html (static demo forms) + auth.css |
| 2026-08-20 | Full redesign: warm cream + terracotta ("Claude-inspired") theme applied site-wide |
| 2026-08-20 | Added dark isometric hero section (illustration + copy), replacing the terminal-card hero |
| 2026-08-20 | Added 30-day money-back guarantee section to `index.html` |
| 2026-08-20 | Fixed broken guarantee badge text and hero illustration shapes |
| 2026-08-20 | Replaced hero illustration with unDraw MIT-licensed server-cluster graphic, recolored to brand palette (`hero-illustration.svg`) |
| 2026-08-20 | Replaced hero illustration with an original hand-built server-rack SVG (`rack-illustration.svg`), sized down for better proportion |
| 2026-08-21 | Added mobile hamburger menu (slides in from the right) + fixed hero responsive stacking and illustration sizing on small screens |
| 2026-08-21 | Added dedicated `pricing.html` with 5 plans from 2GB to 32GB RAM |
| 2026-08-21 | Rebuilt `pricing.html` hero to reuse the same `.hero-dark` component as `index.html`; synced `style.css?v=` cache-busting number across all pages |
| 2026-08-21 | Added this `README.md` design/documentation file |
| 2026-08-21 | Made pricing cards smaller/cuter and single-row on `pricing.html` (5 plans fit one line on desktop, stack on mobile); shrank hero illustration further on all pages; gave `pricing.html` a different hero illustration (`hero-illustration.svg`, unDraw-based) than `index.html` (`rack-illustration.svg`) so the two pages don't look identical |
| 2026-08-22 | Added "Available OS" section (Ubuntu, Debian, CentOS, AlmaLinux, Windows Server, Fedora) below pricing plans on `pricing.html` to match the layout and consistency of `index.html` |

*(Add new rows above this line as the site evolves — most recent last.)*
