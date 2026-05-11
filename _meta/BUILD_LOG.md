# BUILD LOG — talgat.ca

Running record of all build activity. Each entry is a commit (or a logged event for actions that didn't produce a commit). Newest entries appended at the bottom.

---

## [2026-05-11 17:29] — Phase 1, Task 1

**What:** Deleted `mock-hero.html` development draft from the repo.
**Files touched:** mock-hero.html (deleted)
**Commit:** No commit produced — file was untracked (never previously committed), so removing it leaves no diff. End result is identical: file is gone from the working tree.
**Notes:** The plan assumed the file was tracked. It wasn't. No action needed beyond deletion. `csharp-projects.html` is also untracked — flagging for awareness; Phase 2 plan says it's slated for deletion (C# apps fold into Coursework on home), so leaving it in place for tonight per scope of this session.

---

## [2026-05-11 17:34] — Phase 1, Task 2

**What:** Replaced hero copy on index.html and changed the breathing-gradient animation from `infinite` to `1` cycle with `animation-fill-mode: forwards` so it runs once on load and holds the final state. Removed the longer `hero-intro` paragraph entirely. Preserved all CSS classes and HTML structure.
**Files touched:** index.html
**Commit:** `hero: replace copy, change animation from infinite loop to single cycle` (0d68b7a)
**Notes:** Kept `<br>` in hero-name so visual line-break treatment is preserved. Hero `hero-links` block (with phone) was not touched — Task 12 only asks to remove phone from the `#contact` section above the footer, so the hero contact strip stays as-is unless Tal flags otherwise.

---

## [2026-05-11 17:36] — Phase 1, Task 3

**What:** Replaced the two About paragraphs with the locked tightened version. Removed the entire `lang-strip` block (Languages pills + IRB callout) from the About section — both move to Personal page per Task 5.
**Files touched:** index.html
**Commit:** `about: tighten to two paragraphs, remove languages pills (moving to Personal)` (286beab)
**Notes:** Orphaned CSS rules `.lang-strip`, `.lang-pills`, `.lang-pill`, `.irb-callout`, `.irb-icon` may still exist in the stylesheet block. Leaving them in place tonight — they're dead but harmless, and removing them is out of scope for Task 3. Worth a sweep in Phase 2 cleanup.

---

## [2026-05-11 17:41] — Phase 1, Task 4 (+ Task 8a pulled in early)

**What:** Replaced the entire Skills tbody with the six new rows: GIS Stack, Web Application, Data, Systems & Automation, Business Analysis, Programming Foundation. Added `(studying)` markers inline inside the relevant pills. Pulled Task 8a forward into the same commit since the studying markers depend on the brass accent: added `--accent-brass: #b08949` to `:root` and a new `.pill-studying-marker` CSS rule (italic, brass, 0.7em, 4px margin-left). Removed all the dropped skills (MongoDB, BigQuery, AWS, Salesforce, NationBuilder, Shopify, JavaScript/C#/Express/Postman as standalone pills, Business Analyst Pro, Story Maps, Data Management, SaaS Operations, User Training, Reporting).
**Files touched:** index.html
**Commit:** `skills: recalibrate for JD alignment, add (studying) markers, drop noise` (e7b80ce)
**Notes:** Task 8 is now effectively just "card hover lift" — brass variable already in place. Will reflect that when I get there. Studying markers are inline `<span>` inside each pill, which keeps the pill as a single visual unit rather than two adjacent pills. Verified the marker class uses `var(--accent-brass)` not a hardcoded hex.

---

## [2026-05-11 17:48] — Phase 1, Task 5

**What:** Rewrote `personal.html` body: replaced HEADER, MEDIA, INDEPENDENT STUDIES, and READING LIST sections with the locked HEADER (italic epigraph subtitle), PROSE (seven paragraphs), and LANGUAGES (seven-row table with IRB Certified markers in brass). Updated nav-right links to `Projects · GIS · Building · Resume →`. Added `--accent-brass: #b08949` to `personal.html` `:root`. Preserved scroll-bar, nav shell, footer, and fade script. Page title was already `Personal — Talgat Dilmurat`, left as-is.
**Files touched:** personal.html
**Commit:** `personal: replace with locked prose, languages block, remove placeholders` (ec16a24)
**Notes:** Several CSS rules for the deleted sections (media grids, course-list, reading-grid, badge-*, photo-*, video-card, map-card) are now orphans in the stylesheet. Harmless and not in scope tonight; clean up in Phase 2 if desired. The new `#languages` section has a `.section` class which applies a top border — visually separates it from the prose, which feels right. Used inline styles for the prose and languages table per the plan rather than introducing new CSS classes.

---

## [2026-05-11 17:52] — Phase 1, Task 6

**What:** Renamed Learning Log section to "Working notes" (label still "Currently"). Replaced intro line. Replaced five log entries with the new five (CityFlow, Bikeability, Enterprise architecture, Esri Academy, Centennial). Removed all `<span class="log-date">` elements from each item. Updated `.log-item` `grid-template-columns` from `80px 1fr` to `1fr` to reflect single-column layout. Also handles the Task 7 rename inside this section (CivicWorks → CityFlow in the entry title and body).
**Files touched:** index.html
**Commit:** `learning: remove date stamps, rename to Working notes, replace CivicWorks with CityFlow` (a857a18)
**Notes:** Left the `.log-date` CSS rule in place — orphaned but harmless. The mobile media query for `.log-item` was already `grid-template-columns: 1fr`, no change needed there. The "AI triage via Anthropic Claude API" wording in the entry was tightened to "AI-assisted triage via the Anthropic API" to match the new framing introduced in Task 7.

---

## [2026-05-11 17:55] — Phase 1, Task 7

**What:** Renamed CivicWorks → CityFlow site-wide (text-only references in this repo): CSS comment header, HTML comments wrapping the featured card, `featured-title` text, video-placeholder `id` attribute (`civicworks-demo` → `cityflow-demo`), and the featured-tagline. Tagline reframed: "AI triage engine" → "AI-assisted triage (experimental)" per the FIPPA-aware framing. Did NOT touch the GitHub URL on the project card — that's a Phase 2 task (repo doesn't exist yet).
**Files touched:** index.html
**Commit:** `rename: CivicWorks → CityFlow throughout site (text only)` (9dc734e)
**Notes:** Verified zero remaining CivicWorks/civicworks references across all *.html in the repo via case-insensitive search. The Phase 2 plan owns the actual repo rename + deploy.

---

## [2026-05-11 17:58] — Phase 1, Task 8

**What:** Completed Task 8b — added `transform: translateY(-2px)` + `box-shadow: 0 4px 12px rgba(13, 36, 64, 0.08)` to `.project-item:hover` and added the matching `transform` and `box-shadow` properties to its `transition` rule (alongside existing border-left-color and background transitions, so the hover state animates cleanly). `.gis-card` already had a translateY(-2px) + box-shadow lift in place — left untouched rather than risk a regression. Also added `--accent-brass: #b08949` to `resume.html` (next to `--accent`) and `gap.html` (next to `--silver`). Skipped `csharp-projects.html` — it's untracked and the master plan slates it for deletion in Phase 2.
**Files touched:** index.html, resume.html, gap.html
**Commit:** `style: add brass accent variable, card hover lift on project and GIS cards` (89c490d)
**Notes:** Possible visual concern: `.project-item` cards in the home Projects list share `border-bottom` dividers between adjacent items. When one lifts on hover, a small gap will visually open between it and the next card. Decision: leave as-is per plan and let Tal eyeball it. If he doesn't like it, the simplest revert is to remove the transform from `.project-item:hover` and keep the box-shadow alone, or move the lift behavior to the featured-card only.

---

## [2026-05-11 18:01] — Phase 1, Task 9

**What:** Created `favicon.svg` at repo root (navy square `#0d2440` with a centered brass `T` `#b08949`). Added `<link rel="icon" type="image/svg+xml" href="/favicon.svg" />` to the `<head>` of index.html, personal.html, resume.html, gap.html. Skipped csharp-projects.html (untracked, scheduled for deletion in Phase 2).
**Files touched:** index.html, personal.html, resume.html, gap.html
**Files created:** favicon.svg
**Commit:** `add: custom SVG favicon — navy square with brass T` (649a3fe)
**Notes:** None.

---

## [2026-05-11 18:03] — Phase 1, Task 10

**What:** Created `404.html` with the locked content (404 eyebrow in brass, "This page wandered off" heading, brass-underlined back link to /). Created Netlify `_redirects` file at repo root with the catch-all rule `/*    /404.html   404`.
**Files touched:** —
**Files created:** 404.html, _redirects
**Commit:** `add: custom 404 page with brass accent, Netlify redirect rule` (fd70652)
**Notes:** `_redirects` didn't exist previously, so created fresh rather than appended. Live verification deferred to Phase 2 (no deploy this session).

---

## [2026-05-11 18:06] — Phase 1, Task 11

**What:** Updated `<title>` on index.html from `Talgat Dilmurat` to `Talgat Dilmurat · Portfolio`. Replaced the homepage meta description with the locked text. Added per-page meta descriptions to personal.html, resume.html, and gap.html (none had one previously) — one sentence each, matched to the page topic. Other titles left in their `Section — Talgat Dilmurat` format per plan.
**Files touched:** index.html, personal.html, resume.html, gap.html
**Commit:** `meta: update titles and descriptions for clarity and SEO` (4784b95)
**Notes:** `gap.html`'s title still reads "Growth" — the rename to "Building" is a Phase 2 task per the plan. Left as-is.

---

## [2026-05-11 18:08] — Phase 1, Task 12

**What:** Removed the phone link (`tel:4169099610`) from the `#contact` section on index.html, leaving email + GitHub. Replaced the bare-string footer with the two-line locked footer (centered email · GitHub row + Talgat Dilmurat · London, Ontario · 2026 underline). LinkedIn intentionally not added — profile doesn't exist yet (Phase 2 work).
**Files touched:** index.html
**Commit:** `contact/footer: remove phone, simplify footer to email + GitHub` (370d7b9)
**Notes:** Hero `hero-links` still has the phone link — Task 12 specifically scoped to `#contact` and the footer. If Tal wants phone removed from hero too, that's a one-line follow-up.

---

## [2026-05-11 18:10] — Phase 1 Night Session Complete

**Tasks completed:** 1 through 12 — all complete, none skipped.
**Total commits this session:** 11 (Task 1 produced no commit since `mock-hero.html` was untracked; all other tasks produced one commit each).
**Files modified:** index.html, personal.html, resume.html, gap.html
**Files created:** favicon.svg, 404.html, _redirects, BUILD_LOG.md
**Files deleted:** mock-hero.html (was untracked — no diff in git history)
**Pushed to remote:** pending — Task 13 push happens after this entry is written.

**Carry-overs and notes for Tal in the morning:**
- `csharp-projects.html` is untracked in the repo and slated for deletion in Phase 2. Left alone tonight.
- Several CSS rules are orphaned after content changes (`.lang-*`, `.irb-*` in index.html; `.photo-*`, `.video-*`, `.map-*`, `.course-*`, `.reading-*`, `.book-*`, `.badge-*` in personal.html; `.log-date` in index.html). Harmless; clean in Phase 2 if desired.
- The `.project-item` hover lift might create a small visual gap between items on hover because items share `border-bottom` dividers. Eyeball it; if you don't like it, removing the `transform: translateY(-2px)` line keeps the shadow without the lift.
- Hero `hero-links` still has the phone number (`(416) 909-9610`). Task 12 only scoped to `#contact` and footer; if you want phone gone from hero too, one-line revert.
- **[NEEDS TAL]:** `BUILD_LOG.md`, `BUILD_PLAN_DAY.md`, `BUILD_PLAN_NIGHT.md`, `MASTER_CONTEXT.md`, `NEXT_STEPS.md` are all untracked planning/log files at the repo root. Netlify deploys everything in the repo by default, so committing these would publish them at `talgat.ca/MASTER_CONTEXT.md` etc. Choices: (a) gitignore them and keep local-only, (b) move into a `_meta/` folder and add a Netlify ignore rule, or (c) commit anyway if you don't mind the exposure. Did not push these tonight.
- Phase 2 starts with: bikeability deep page, gap.html → building.html rename, CityFlow repo creation, architecture diagram, deploy verification.

---

## [2026-05-11 18:18] — Post-push cleanup, Step 1: move planning docs into `/_meta/`

**What:** Created `/_meta/` directory at repo root. Moved five planning/log files into it: `MASTER_CONTEXT.md`, `BUILD_PLAN_NIGHT.md`, `BUILD_PLAN_DAY.md`, `NEXT_STEPS.md`, `BUILD_LOG.md`. Files were previously untracked so this move appears as new-file adds under `_meta/` in git.
**Files moved:** MASTER_CONTEXT.md, BUILD_PLAN_NIGHT.md, BUILD_PLAN_DAY.md, NEXT_STEPS.md, BUILD_LOG.md → all into `_meta/`
**Commit pairing:** the move ships together with the `netlify.toml` exclusion in the next commit so a public deploy can never serve these files before the redirect rule is in place.
**Notes:** Future Claude sessions should look at `/_meta/BUILD_LOG.md` (and the other planning docs). The master plan's reference to "BUILD_LOG.md at repo root" is now `/_meta/BUILD_LOG.md` — worth a one-line update in MASTER_CONTEXT.md if Tal cares; not done tonight.

---

## [2026-05-11 18:22] — Post-push cleanup, Step 2: drop orphan CSS

**What:** Removed CSS rules left dangling by Phase 1 content changes.

`index.html` — removed:
- `.lang-strip`, `.lang-pills`, `.lang-pill`, `.lang-pill:hover` (from old Languages strip in About)
- `.irb-callout`, `.irb-callout .irb-icon`, `.irb-callout p`, `.irb-callout p span` (old IRB callout)
- `.log-date` (dropped when Working notes lost the date column)
- `.lang-chip` rule inside the `@media (max-width: 700px)` block (referred to a class that no longer exists anywhere)

`personal.html` — removed:
- `.s-title`, `.s-sub` (no longer used in the new minimal page)
- `.page-title`, `.page-intro` (old "Beyond the work" hero classes)
- All `.media-type-*`, `.photo-*`, `.ph-*` rules (Photos block deleted)
- All `.video-*`, `.vid-*` rules (Videos block deleted)
- All `.map-*` rules including `.map-card::before` (Story Maps block deleted)
- All `.course-*`, `.badge-done`, `.badge-progress`, `.badge-placeholder` rules and `@keyframes pulse-border` (Independent studies block deleted)
- All `.reading-grid`, `.book-*`, `.add-placeholder` rules (Reading list block deleted)
- Both `@media` query blocks that only contained references to the deleted classes — removed entirely

**Kept intentionally in personal.html:** the `#header` noise-texture background image and `#header::after` fade-out gradient. The new minimal header still uses the `#header` section; whether the noise texture suits the new shorter header is a visual judgment call I didn't want to make unilaterally. Eyeball in the morning — if it looks heavy, swap to a flat `var(--bg)` background.

**Files touched:** index.html, personal.html
**Commit:** `cleanup: drop orphan CSS rules from removed sections` (f069367)
**Net change:** 189 deletions, 0 insertions.

---

## [2026-05-11 18:23] — Post-push cleanup, Step 3: fix `.project-item:hover` gap

**What:** Removed `transform: translateY(-2px)` and `box-shadow: 0 4px 12px rgba(13, 36, 64, 0.08)` from `.project-item:hover`. Also removed `transform` and `box-shadow` from the `.project-item` `transition` rule since they're no longer animated. The hover state keeps its `border-left-color` change to silver and its `var(--bg-soft)` background — the affordance is still there without breaking the connected-list visual.
**Why:** `.project-item` cards in the Projects list share a `border-bottom` divider with the next item. Lifting one card on hover opened a small visible gap between it and the item below. `.gis-card` lift was left intact — those cards live in an isolated grid where the lift reads cleanly.
**Files touched:** index.html
**Commit:** `fix: drop translateY/box-shadow from .project-item:hover` (bedb542)
**Notes:** None.
