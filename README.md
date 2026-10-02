# Printomo — Website Prototype

A clickable prototype of the new printomo.co, built as a static site. No build step, no
dependencies to install, no server-side code. Open it or host it and it runs.

**Live demo:** https://YOUR-USERNAME.github.io/printomo-site/

---

## Publish it on GitHub Pages (about 3 minutes)

1. Create a new repository on GitHub — call it `printomo-site`. Make it **Public**
   (GitHub Pages needs a paid plan for private repos).
2. Upload every file and folder in this directory to the repository. Drag-and-drop on
   github.com works; keep the folder structure exactly as it is.
3. In the repository, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to `Deploy from a branch`, pick branch
   `main` and folder `/ (root)`, then press **Save**.
5. Wait about a minute and refresh. GitHub shows the live URL at the top of that page.

### Updating a repository you already published

Upload the whole folder again and let GitHub replace the existing files (on github.com:
**Add file → Upload files**, drag in everything, then **Commit changes**). Nothing needs
deleting first. This version adds `design.html`, `merch.html`, `signage.html`,
`events.html`, `soon.html`, and `404.html`, and changes every other page, so upload all of
it rather than picking files. GitHub Pages redeploys within a minute or two. If the old
version still shows, hard-refresh the browser (Cmd+Shift+R or Ctrl+Shift+R).

The repository must be called `printomo-site` (or any name, as long as it is a normal
project repository and not `username.github.io`). The 404 page works out its own
location from that name.

### Previewing locally

Double-clicking `index.html` will **not** work — the pages load each other and their
assets over HTTP. Run a local server instead:

```bash
cd printomo-site
python3 -m http.server 8000
```

Then open http://localhost:8000 in a browser.

---

## The pages

| File | Page | What it is |
|---|---|---|
| `index.html` | Home | Hero with the lit building, the four service statements, work, brief builder, process, FAQ |
| `work.html` | Work | All jobs, filterable, in two views (proof cards or job ledger) |
| `case-study.html` | Case study | The template every job page uses, filled in with 7th Street Burger × Avant Gardner |
| `design.html` | Design | One mark on four surfaces, what we design, process, design work, design FAQ |
| `merch.html` | Merch and print | Decoration method picker, what we make, how an order runs, reorders, merch FAQ |
| `shop.html` | The Shop | About: the story, the arm-by-arm tour, equipment, team, how we work |
| `signage.html` | Signage | Storefront anatomy, what we make, the install process, signage work, sign FAQ |
| `events.html` | Events | Countdown to doors (run of show), what we build, event work, event FAQ |
| `start.html` | Start a Project | The full work-order enquiry form |
| `soon.html` | Placeholder | Where links to unbuilt pages go; names the page that is coming |
| `404.html` | Not found | Shown by GitHub Pages for any address that does not exist |

Every link goes somewhere sensible, so stakeholders can click straight through the site
as if it were live:

- **Navigation, buttons, and footer** link to the real pages. The main navigation is the
  same on every page: Design · Merch · Signage · Events · Work · The shop, plus
  Start a project. FAQ and Journal are in the footer.
- **Pages that are not built yet** (Journal, Careers, Artwork guidelines, Privacy and
  terms) and **links still to be supplied** (Instagram, the online store) open
  `soon.html`, which says what is coming instead of doing nothing.
- **Get directions** on The Shop opens Google Maps for 308 35th Street.
- **Phone and email** links open the visitor's phone or mail app.
- **Mistyped addresses** show the branded 404 page.

### Things that are interactive

Click these when demoing — they are the parts that do not read as a flat mockup:

- **Home** — the elevator panel lights the building's floors; the four service words
  animate; the brief builder ticks, stamps RUSH, and stamps RECEIVED
- **Work** — the service filters (with live counts) and the PROOFS / JOB LEDGER toggle;
  hovering a ledger row previews that job
- **Case study** — the photo gallery thumbnails
- **The Shop** — the floor tour; each arm lights that level of the building
- **Design** — "Designed to be made": the same mark on a tee, a storefront, a backdrop,
  and a box; hover the six service cards for the design-tool selection frame
- **Merch** — the method picker; screen print, embroidery, and DTF each re-render the
  shirt and show what that method is best for
- **Signage** — the storefront anatomy; each numbered spot lights that part of the
  building and shows what goes there
- **Events** — the countdown to doors; each stop flips the departure-board clock
- **Start a Project** — the whole work order, including the self-writing brief summary

---

## What is still placeholder

Anything in `[square brackets]` is waiting on real information. The significant ones:

- **Photography.** Current images are 600px wide, which is soft on a laptop and blurry on
  a large monitor. Masters should be about 3000 × 1688 (16:9), JPEG.
- **Signage and event work.** Five of the eight jobs on the Work page are placeholders.
  These matter most, because they are what proves Printomo is more than a merch shop.
  The Signage and Events pages show the same placeholders.
- **Merch facts.** Minimums per method, turnaround, rush, blank brands, sustainable
  options, the InkSoft store link.
- **Design facts.** Number of directions and revisions, file ownership, timelines.
- **Signage and event facts.** Service area, who files sign permits, after-hours installs,
  sign removal, event staffing, teardown and storage, insurance certificates, real lead
  times. Each is marked `[Confirm …]` on the page where it appears.
- **Client logos** in the logo walls, and every **testimonial**.
- **FAQ answers** — minimums, lead times, file formats, pricing.
- **Equipment list** on The Shop. The single most persuasive block for a large buyer.
- **Company facts** — founded year, square footage, headcount, insurance and install
  certifications, team photos.

---

## Known limits of the prototype

- **Desktop only.** Pages are laid out at a fixed 1440px width and centered. They scale
  down on a phone but are not yet responsive; mobile layouts come with the production build.
- **Forms do not submit.** The brief builder and Start a Project form are front-end only.
  The RECEIVED stamp is a visual response, nothing is sent. Wiring the form to the
  Monday.com board is a production task.
- **Animations are timed or triggered by clicking and hovering.** Scroll-linked effects
  are not included here.
- **Journal, Careers, Artwork guidelines, and Privacy** are not built yet; their links open
  the placeholder page. The Instagram and online store links need their real URLs.

---

## How it is put together

```
printomo-site/
├── index.html, design.html, merch.html, signage.html, events.html,
│   work.html, case-study.html, shop.html, start.html
├── soon.html, 404.html   placeholder and not-found pages
├── assets/      images, the vectorised logo and building, fonts
├── lib/         the rendering runtime (React + the component runtime)
├── .nojekyll    tells GitHub Pages to serve files as-is (hidden on a Mac; the site
│                still works if it gets left out of an upload)
└── README.md
```

- **Self-contained.** No CDN, no analytics, and nothing loaded from another site. It works
  behind a restrictive corporate network, which is often where stakeholders are.
- **Checked as GitHub Pages serves it.** Tested from a `/printomo-site/` sub-path on a
  `github.io` address: all 9 pages, every link and anchor, the navigation from every page,
  the placeholder links, and the 404 page, with no console errors or failed requests.
- **Fonts are bundled.** Archivo and Big Shoulders Display are subset to the characters
  the site uses — 57KB for both.
- **Artwork is vector.** The logo, wordmark, and building illustration are SVG, so they
  stay sharp at any size. The building's windows are individual shapes, which is what lets
  floors light up independently.
- **Motion respects accessibility settings.** Every animation is disabled for visitors who
  have "reduce motion" turned on.

### Colours

| | Hex |
|---|---|
| Cream (page) | `#F8F4DF` |
| Tan (alternate sections) | `#EFE8CC` |
| Black | `#000000` |
| Rust (accent) | `#A84F38` |
| Amber (lights, highlights) | `#F2C46D` |
| Off-white (text on black) | `#F4F6E8` |

---

## Notes for whoever builds the production site

The prototype pages are rendered by a small component runtime in `lib/`, which is
convenient for a demo but is not what should ship. For production I would rebuild these
in **Astro**, which outputs plain static HTML with no runtime, and pair it with a
**Git-based CMS** (Keystatic) so the team can add case studies without touching code.
The markup, CSS, and interaction logic here all carry over.

Two things to handle at that point: 301 redirects from the old WordPress URLs so search
rankings survive, and the form back end.
