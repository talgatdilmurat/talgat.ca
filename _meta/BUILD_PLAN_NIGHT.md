# BUILD PLAN — Night Session (Phase 1)

> This is a deliberately conservative build phase. Everything in this plan is safe to run while Tal sleeps. Nothing in here touches the CityFlow repo, modifies the Netlify deploy, or performs irreversible operations on shared infrastructure.

---

## Working principles for this session

**Read this section first. Do not skip.**

1. **Frame the reader, not the writer.** Every change filters through this question: *"Would this help the C1425 hiring manager decide, in 90 seconds, that Tal can do the job within 6 months?"* If a change doesn't pass this filter, don't make it.

2. **Honesty over polish.** Tal explicitly does not want overclaim. Specifically: do not invent skills, projects, or experience. Do not narrate or commentate on his interpreter work beyond what's literally on the page. Do not add lines like *"Six years of professional interpretation..."* — Tal removes these every time.

3. **Voice: plain, sincere, slightly literary in select moments.** Tal's style preference: evocative phrasings like *"Beyond the one-pager"* used sparingly. Plain professional voice everywhere else. Reads like a thoughtful person wrote it on a Sunday afternoon, not like a template.

4. **Commit early, commit often.** Every meaningful change = a commit. Commit messages should describe what changed, not how. Example: `content: tighten about section to two paragraphs` not `edited index.html lines 720-735`.

5. **Update BUILD_LOG.md after every commit.** Format below in the section "BUILD_LOG protocol."

6. **Stop and wait if uncertain.** If any task in this plan is ambiguous in a way the plan doesn't resolve, write what you're uncertain about into BUILD_LOG.md as a `[NEEDS TAL]:` entry and skip that task. Better to leave it for morning than to guess.

7. **Do NOT do any of the following tonight:**
   - Do not touch any repo other than this one
   - Do not modify the Netlify deploy configuration
   - Do not push more than once at the end of the session (one push at end, not per-commit)
   - Do not delete files outside the explicit deletion list in this plan
   - Do not rename `gap.html` to `building.html` tonight — that's a Phase 2 task
   - Do not add new pages tonight — that's a Phase 2 task
   - Do not deploy or verify the live site — that happens in Phase 2

---

## BUILD_LOG protocol

After every commit, append an entry to `BUILD_LOG.md` (create it at repo root if it doesn't exist) in this format:

```
## [YYYY-MM-DD HH:MM] — Phase 1, Task N

**What:** Brief description of what was done.
**Files touched:** index.html, personal.html, [etc]
**Commit:** Exact commit message used.
**Notes:** Anything Tal should know — surprises, decisions made, anything off-script.
```

If a task is skipped because of uncertainty, log it as:

```
## [YYYY-MM-DD HH:MM] — Phase 1, Task N — SKIPPED

**[NEEDS TAL]:** What you need from Tal to resolve.
**Why skipped:** Brief explanation.
```

---

## Task list (run in order)

### Task 1 — Delete dead files

Delete the following files from the repo:
- `mock-hero.html` (development draft, not deployed)

Commit message: `cleanup: remove mock-hero.html development draft`

---

### Task 2 — Replace hero copy on index.html

Find the `#hero` section (currently lines roughly 696–717).

**Current hero text:**
```
London, Ontario
Talgat Dilmurat
Aspiring GIS Analyst · Software Engineering Graduate
GIS · Systems · The space between
focus : spatial data · automation · apps
GIS, SQL, REST APIs, CRM administration, and workflow documentation — focused on the seam between systems and the people who depend on them.
```

**Replace with:**

```
London, Ontario
Talgat Dilmurat
GIS, Systems, and the work between them
Software Engineering graduate building toward municipal systems work

focus : spatial data · process · the seam between systems and people
```

Preserve all existing CSS classes and HTML structure. Just swap the text content. Remove the longer descriptive paragraph (the "GIS, SQL, REST APIs..." line) entirely.

Also: the hero currently has an infinite breathing gradient animation. Modify the CSS animation rule so it runs *one cycle* on initial page load (14 seconds) and then settles on the final gradient state. The simplest way: change `animation-iteration-count` from `infinite` to `1`, and use `animation-fill-mode: forwards` to hold the final state.

Commit message: `hero: replace copy, change animation from infinite loop to single cycle`

---

### Task 3 — Tighten About section on index.html

Find the `#about` section.

**Replace the two existing paragraphs with:**

```
Software Engineering Technology graduate now focused on GIS and business systems analysis. I'm drawn to the space where data becomes decision-making — where a clean schema or a well-mapped workflow quietly changes how an organization works.

Before tech, the path took its time. I studied linguistics, taught languages, and worked as a certified interpreter. I ran a small e-commerce business. I worked in marketing operations and nonprofit administration. The range is the point — I can move between technical and non-technical contexts without losing either side.
```

Keep the existing `.about-text` wrapper and `.s-body` styles. Just replace the text content of the two `<p>` elements.

**Also in the about section:** the current implementation has a "Languages" pill strip and an IRB Certified callout below the about text. **Remove both of these.** Languages move entirely to the Personal page (Task 5). The about section ends after the second paragraph above.

Commit message: `about: tighten to two paragraphs, remove languages pills (moving to Personal)`

---

### Task 4 — Recalibrate Skills table on index.html

Find the `#skills` section. The current implementation has six rows of skills pills.

**Replace the entire skills-table tbody with this structure**, preserving CSS classes:

| Row label | Pills (in order) |
|---|---|
| GIS Stack | ArcGIS Pro · ArcGIS Online · Leaflet.js · ArcGIS Enterprise *(studying)* · ArcGIS Monitor *(studying)* · Spatial Data · Coordinate Systems |
| Web Application | React 18 · Node.js · .NET / C# · REST APIs · JSON · OAuth *(studying)* |
| Data | SQL · PostgreSQL · MySQL · Relational Modeling · ETL *(studying)* |
| Systems & Automation | Python · PowerShell *(studying)* · Git · Jira · Windows Server *(studying)* · IIS *(studying)* |
| Business Analysis | Process Mapping · Workflow Documentation · Requirements Gathering · Stakeholder Communication |
| Programming Foundation | Java · Spring Boot · Object-Oriented Design |

**Important treatment for `(studying)` markers:**
- The text *(studying)* sits inline after the pill text inside the same pill
- Style it with italics and a muted color
- Add a new CSS class `.pill-studying-marker` if needed: `font-style: italic; color: #b08949; font-size: 0.7em; margin-left: 4px;`
- The brass color `#b08949` is the warm accent we're introducing site-wide (Task 8)

**Skills to remove entirely:**
- MongoDB, Google BigQuery, AWS EC2/S3/RDS/Lambda, Salesforce CRM, NationBuilder CRM, Shopify, SaaS Operations, Business Analyst Pro, Story Maps, Data Management, JavaScript (as standalone — covered by React/Node), C# (standalone — covered by .NET/C#), Postman, Express (as standalone — covered by Node.js)

These removed skills can still appear in project tech-tags where they earned their place. They just don't belong in the front-page Skills summary.

Commit message: `skills: recalibrate for JD alignment, add (studying) markers, drop noise`

---

### Task 5 — Replace Personal page content

Replace the entire content of `personal.html` body with the locked Personal page prose.

**The new content** (preserve nav, scroll bar, and footer markup; replace only the page body sections):

```html
<!-- HEADER -->
<section id="header">
  <div class="wrap">
    <p class="s-label fade">Personal</p>
    <p class="page-subtitle fade" style="font-style: italic; color: var(--text-muted); font-size: 0.95rem; margin-bottom: 32px; max-width: 620px;">
      The route to here was non-linear: linguistics, interpretation, e-commerce, nonprofit work, marketing, and now software engineering.
    </p>
  </div>
</section>

<!-- PROSE -->
<section id="prose" class="section" style="border-top: none; padding-top: 0;">
  <div class="wrap">
    <div class="prose-body fade" style="max-width: 620px; font-size: 1rem; line-height: 1.85; color: var(--text-mid);">
      <p style="margin-bottom: 20px;">I'm Talgat — Tal, to most people. A Londoner.</p>

      <p style="margin-bottom: 20px;">Before tech, the path took its time. I studied linguistics, taught languages, and worked as an interpreter. I ran a small e-commerce business. I worked in marketing operations and nonprofit administration. Then I went back to school for software engineering — three years of full-time work at Frito-Lay alongside it. The schedule was extreme. I still can't quite believe I made it through. Different industries, one instinct underneath: figure out how something works, then make it work better.</p>

      <p style="margin-bottom: 20px;">London is where my daughter was born — she's two and a half, the centre of our world. I've been taking her out since she was a baby; we go to parks and ice cream shops and quiet corners of the city. This is where she's growing up, and where I want to keep building things.</p>

      <p style="margin-bottom: 20px;">I currently drive a delivery route for Frito-Lay, and the route has turned into a few hours a day of listening to lectures and podcasts — usually Open Yale Courses. Kagan's Greek History stayed with me; Shiller's Financial Markets did too. Lately I've been working through ESRI podcasts — <em>Geographical Thinking</em> and <em>Spatial Reports</em>. The bikeability project idea came from one of those episodes. I'd rather a lecture or a podcast than music, almost always.</p>

      <p style="margin-bottom: 20px;">I enjoy cooking a lot — forty dishes by now, give or take, ten of which I made up. Espresso is non-negotiable. I used to coach fitness on the side, back in school. For some reason I once took a flying lesson and learned that I find flying boring, which surprised me. Long road trips are my favourite kind of trip — Calgary to London once, and Medebach to Hamburg out to Ærø Island in Denmark on our honeymoon.</p>

      <p style="margin-bottom: 20px;">I read in several languages, mostly non-fiction — history, rhetoric, grammar, and logic. Mortimer Adler's <em>How to Read a Book</em> is the one I keep coming back to. It changed how I read everything else. Aristotle's <em>Rhetoric</em> in the everyday-readers edition is one I return to often, along with texts on logical fallacies and Geoff Colvin's <em>Talent is Overrated</em>. I keep a stack of the Oxford Very Short Introductions for when I want a quick foothold in a new subject.</p>

      <p style="margin-bottom: 0;">Builder by temperament. Lifelong learner, but specifically — I follow the <em>why</em> of things. I want to understand systems, not just operate them. That's the through-line, I think.</p>
    </div>
  </div>
</section>

<!-- LANGUAGES -->
<section id="languages" class="section">
  <div class="wrap">
    <p class="s-label fade">Languages</p>
    <table class="languages-table fade" style="max-width: 480px; border-collapse: collapse; margin-top: 12px;">
      <tbody>
        <tr><td style="padding: 8px 0; color: var(--text); font-weight: 500; width: 40%;">English</td><td style="padding: 8px 0; color: var(--text-muted);">Fluent</td></tr>
        <tr><td style="padding: 8px 0; color: var(--text); font-weight: 500;">Mandarin</td><td style="padding: 8px 0; color: var(--text-muted);">Fluent · <em style="color: #b08949;">IRB Certified</em></td></tr>
        <tr><td style="padding: 8px 0; color: var(--text); font-weight: 500;">Uyghur</td><td style="padding: 8px 0; color: var(--text-muted);">Fluent · <em style="color: #b08949;">IRB Certified</em></td></tr>
        <tr><td style="padding: 8px 0; color: var(--text); font-weight: 500;">Kazakh</td><td style="padding: 8px 0; color: var(--text-muted);">Fluent · <em style="color: #b08949;">IRB Certified</em></td></tr>
        <tr><td style="padding: 8px 0; color: var(--text); font-weight: 500;">Arabic</td><td style="padding: 8px 0; color: var(--text-muted);">Fluent (spoken) · Intermediate (written)</td></tr>
        <tr><td style="padding: 8px 0; color: var(--text); font-weight: 500;">Russian</td><td style="padding: 8px 0; color: var(--text-muted);">Intermediate</td></tr>
        <tr><td style="padding: 8px 0; color: var(--text); font-weight: 500;">Turkish</td><td style="padding: 8px 0; color: var(--text-muted);">Beginner</td></tr>
      </tbody>
    </table>
  </div>
</section>
```

**Also remove from personal.html:**
- The current "Media" section (photos/videos/Story Maps placeholders)
- The current "Reading list" placeholder cards
- The "Send me your reading list" placeholder note
- The "Independent studies" Yale courses section (keep nothing from it — the prose above absorbs the relevant mentions like Kagan and Shiller)

**Nav update in personal.html:** the current nav-right links say `Resume · Projects · gap.html (Growth) · Full Resume`. Update to:
```html
<a href="index.html#projects">Projects</a>
<a href="index.html#gis">GIS</a>
<a href="gap.html">Building</a>
<a href="resume.html" class="nav-resume">Resume →</a>
```

Page `<title>` becomes: `Personal — Talgat Dilmurat`

Commit message: `personal: replace with locked prose, languages block, remove placeholders`

---

### Task 6 — Restructure Learning Log on index.html

Find the `#learning` section.

The current Learning Log has dated entries (May 2026, 2026, 2025-26). **Remove all date stamps.** The new format:

```html
<section id="learning" class="section">
  <div class="wrap">
    <p class="s-label fade">Currently</p>
    <h2 class="s-title fade">Working notes</h2>
    <p class="s-body fade" style="max-width: 520px; margin-bottom: 32px;">
      A running record of what I'm studying and building right now.
    </p>
    <div class="log-list">

      <div class="log-item fade">
        <div class="log-content">
          <span class="log-tag">Full-Stack</span>
          <h4>Built CityFlow — Municipal Asset Management System</h4>
          <p>Full-stack app: React 18 frontend, Node.js + Express REST API, PostgreSQL database with audit log, interactive Leaflet.js map, AI-assisted triage via the Anthropic API, and a KPI dashboard.</p>
        </div>
      </div>

      <div class="log-item fade">
        <div class="log-content">
          <span class="log-tag">GIS</span>
          <h4>London ON Bikeability Analysis</h4>
          <p>Current-state spatial analysis using City of London open data. Three-tier classification, buffer analysis, gap polygon identification. Methodology, findings, and recommendations report in progress.</p>
        </div>
      </div>

      <div class="log-item fade">
        <div class="log-content">
          <span class="log-tag">ArcGIS</span>
          <h4>Working through ArcGIS Enterprise architecture</h4>
          <p>Self-directed study on Portal for ArcGIS, ArcGIS Server, licensing, patching, and geodatabases. Building familiarity beyond ArcGIS Online.</p>
        </div>
      </div>

      <div class="log-item fade">
        <div class="log-content">
          <span class="log-tag">Esri</span>
          <h4>Esri Academy — eleven courses completed</h4>
          <p>Foundational curriculum: ArcGIS Pro, ArcGIS Online, Business Analyst Pro, GIS Basics, Coordinate Systems, Data Management, AI in ArcGIS, Systems Approach to ArcGIS, ArcGIS Monitor.</p>
        </div>
      </div>

      <div class="log-item fade">
        <div class="log-content">
          <span class="log-tag">Software Engineering</span>
          <h4>Advanced Diploma — Centennial College</h4>
          <p>Three-year program covering databases, APIs, cloud, DevOps, networking, security, enterprise systems, and business analysis.</p>
        </div>
      </div>

    </div>
  </div>
</section>
```

Also update the CSS for `.log-item` — since there's no longer a date column, change the grid-template-columns from `80px 1fr` to just `1fr`. Find that rule in the stylesheet (roughly line 605) and update.

The section label is now "Currently" and the title is "Working notes" — softer than "Learning log" and matches the present-tense framing we're using site-wide.

Commit message: `learning: remove date stamps, rename to Working notes, replace CivicWorks with CityFlow`

---

### Task 7 — Rename CivicWorks → CityFlow site-wide (text-only)

**Important:** this task is ONLY the text references inside this repo (`talgat.ca`). The actual CityFlow code repo is a Phase 2 task — do not touch it tonight.

In `index.html`, find every occurrence of `CivicWorks` and replace with `CityFlow`. Verify these specific spots:
- Featured card title (currently `<h3 class="featured-title">CivicWorks</h3>`)
- The featured-tagline that mentions CivicWorks
- Any `id` attributes (e.g., `#civicworks-demo` becomes `#cityflow-demo`)
- The Learning Log entry (already handled in Task 6 if you did them in order)
- Comments in the HTML (e.g., `<!-- CIVICWORKS FEATURED CARD -->` becomes `<!-- CITYFLOW FEATURED CARD -->`)
- Any reference in the alt text on the dashboard preview image

**Do NOT change in this task:**
- The CivicWorks → CityFlow rename in the actual code repo (Phase 2)
- The GitHub URL link in the project card (Phase 2 — will update when repo exists)
- Any docs (none in this repo to worry about)

Also: the tagline currently calls the project "Full-stack municipal asset management — React frontend, Node.js API, PostgreSQL database, live GIS map, and an AI triage engine built on the Anthropic Claude API."

**Update to:** "Full-stack municipal asset management — React frontend, Node.js API, PostgreSQL database, live GIS map, and AI-assisted triage (experimental) built on the Anthropic Claude API."

The word "experimental" is the small reframe we agreed on. Don't add the full FIPPA paragraph — that lives on the deep page (Phase 2).

Commit message: `rename: CivicWorks → CityFlow throughout site (text only)`

---

### Task 8 — Introduce brass warm accent + card hover lift

Two small visual additions:

**8a. Brass accent CSS variable.** In the `:root` block at the top of index.html (and personal.html, resume.html, gap.html, csharp-projects.html — apply to all stylesheets), add this line:

```css
--accent-brass: #b08949;
```

This is the single warm color in an otherwise cool palette. The discipline is that it's *only* used for:
- The `(studying)` markers in the Skills table
- The "IRB Certified" italic text in the Languages table on personal.html
- Anywhere else: do not use this color tonight

If you find any existing `(studying)` markers using a different color, update them to use `var(--accent-brass)`.

**8b. Card hover lift.** Currently project cards and gis cards have no hover state lift. Find the `.project-item` and `.gis-card` rules and add:

```css
.project-item, .gis-card {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.project-item:hover, .gis-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(13, 36, 64, 0.08);
}
```

Test that this doesn't fight with any existing hover rules. If there are conflicts, log them in BUILD_LOG.md.

Commit message: `style: add brass accent variable, card hover lift on project and GIS cards`

---

### Task 9 — Custom favicon

Create a simple SVG favicon and reference it from all pages.

**Create file:** `favicon.svg` at repo root.

**Content:**
```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
  <rect width="32" height="32" rx="4" fill="#0d2440"/>
  <text x="16" y="22" font-family="Inter, system-ui, sans-serif" font-size="18" font-weight="700" fill="#b08949" text-anchor="middle">T</text>
</svg>
```

A navy square with a single brass "T". Initial only — Tal said his name and the domain are the brand, no need for "TD."

**Reference it from all HTML files** by adding inside each `<head>`:

```html
<link rel="icon" type="image/svg+xml" href="/favicon.svg">
```

Apply to: index.html, personal.html, resume.html, gap.html, csharp-projects.html.

Commit message: `add: custom SVG favicon — navy square with brass T`

---

### Task 10 — Custom 404 page

Create `404.html` at repo root.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page not found — Talgat Dilmurat</title>
  <link rel="icon" type="image/svg+xml" href="/favicon.svg">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --bg: #ffffff;
      --text: #0d2440;
      --text-mid: #1e3a5c;
      --text-muted: #4a6a90;
      --accent-brass: #b08949;
    }
    body {
      font-family: 'Inter', system-ui, sans-serif;
      background: var(--bg);
      color: var(--text);
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 28px;
    }
    .wrap { max-width: 480px; text-align: center; }
    .code {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.75rem;
      color: var(--accent-brass);
      letter-spacing: 0.1em;
      text-transform: uppercase;
      margin-bottom: 16px;
    }
    h1 {
      font-size: clamp(1.8rem, 4vw, 2.4rem);
      letter-spacing: -0.02em;
      margin-bottom: 20px;
      line-height: 1.2;
    }
    p {
      color: var(--text-mid);
      line-height: 1.7;
      margin-bottom: 32px;
    }
    a {
      color: var(--text);
      text-decoration: none;
      border-bottom: 1px solid var(--accent-brass);
      padding-bottom: 2px;
      font-weight: 500;
    }
    a:hover { color: var(--accent-brass); }
  </style>
</head>
<body>
  <div class="wrap">
    <p class="code">404</p>
    <h1>This page wandered off</h1>
    <p>The page you were looking for doesn't exist, or has moved. Probably the latter — this site is under active development.</p>
    <a href="/">← Back to the portfolio</a>
  </div>
</body>
</html>
```

Also create a Netlify `_redirects` file at repo root (if it doesn't exist) and add:

```
/*    /404.html   404
```

This tells Netlify to serve 404.html on any unmatched route. If `_redirects` already exists, append the line; don't overwrite.

Commit message: `add: custom 404 page with brass accent, Netlify redirect rule`

---

### Task 11 — Update meta description and site title across pages

For each HTML file (index.html, personal.html, resume.html, gap.html, csharp-projects.html), update:

**`<title>` tag:** the homepage stays `Talgat Dilmurat`, but add the subtitle. Format: `Talgat Dilmurat · Portfolio`. Other pages keep their current `Section — Talgat Dilmurat` format.

**Meta description (in `<head>`):** the current homepage description is generic. Update to:

```html
<meta name="description" content="Portfolio of Talgat Dilmurat — GIS analysis, full-stack systems, and the work between them. Based in London, Ontario.">
```

Update other pages' meta descriptions similarly (one sentence per page, matches the page topic). Skip if any page already has one — don't overwrite. Use judgment.

Commit message: `meta: update titles and descriptions for clarity and SEO`

---

### Task 12 — Footer cleanup on index.html

The footer currently says: `Talgat Dilmurat · London, ON · 2026`

**Update to:**

```html
<footer>
  <div class="footer-row" style="display: flex; gap: 24px; justify-content: center; align-items: center; flex-wrap: wrap; margin-bottom: 12px;">
    <a href="mailto:talgat.dilmurat.tech@gmail.com" style="font-size: 0.8rem; color: var(--text-muted);">talgat.dilmurat.tech@gmail.com</a>
    <span style="color: var(--text-faint);">·</span>
    <a href="https://github.com/talgatdilmurat" target="_blank" style="font-size: 0.8rem; color: var(--text-muted);">GitHub</a>
  </div>
  <p style="font-size: 0.75rem; color: var(--text-faint);">Talgat Dilmurat · London, Ontario · 2026</p>
</footer>
```

**Also: in the contact section above the footer (`#contact`), REMOVE the phone number line.** The current contact-row has email + phone + GitHub. Remove the phone link entirely, leaving just email and GitHub.

LinkedIn is intentionally not added yet — Tal's profile doesn't exist. Phase 2 task (post-LinkedIn setup) to add it.

Commit message: `contact/footer: remove phone, simplify footer to email + GitHub`

---

### Task 13 — Final commit and push (ONCE)

After all tasks complete and BUILD_LOG.md is updated for every change:

```bash
git status
git log --oneline -20  # review the work
git push origin main
```

Push **once at the end of the session.** Not per-commit. This keeps the public commit history clean and means if anything went wrong mid-build, it's still local and can be sorted in the morning.

If for any reason you cannot push (auth issue, conflict), do not force-push. Log the issue in BUILD_LOG.md as `[NEEDS TAL]` and leave the commits local. Tal will resolve in the morning.

Commit message for any final "wrap up the session" commit: `session: night phase 1 complete — content tightened, calibration done`

---

## End-of-session BUILD_LOG entry

At the very end of the session, append this summary to BUILD_LOG.md:

```
## [YYYY-MM-DD HH:MM] — Phase 1 Night Session Complete

**Tasks completed:** [list task numbers 1 through 12, marking any skipped]
**Total commits:** [number]
**Files modified:** [list]
**Files created:** [list]
**Files deleted:** [list]
**Pushed to remote:** [yes/no — if no, why]

**Outstanding for Tal in the morning:**
- [Anything flagged as NEEDS TAL during the session]
- [Anything that didn't go to plan]
- Phase 2 starts with: bikeability deep page, gap.html → building.html rename, CityFlow repo creation, architecture diagram, deploy verification.
```

---

## End of night plan
