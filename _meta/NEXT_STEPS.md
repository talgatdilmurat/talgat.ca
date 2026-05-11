# NEXT STEPS — Talgat's runway to May 20

> Everything that needs to happen between now and the application deadline. Items in date order, with effort estimates and dependencies. Use this to plan your week and to brief Claude in a new chat if needed.

---

## Current date: May 11, 2026
## Deadline: May 20, 2026
## Working days remaining: 9

---

## Today / Tonight (May 11)

**☐ Sleep.** Five hours of strategy is enough. The night build is optional — see below.

**☐ (Optional, low-risk) Run BUILD_PLAN_NIGHT.md overnight in Claude Code.** Phase 1 is conservative content work. Switch on auto-accept mode in Claude Code, stay awake for 10 minutes to confirm Task 1–2 execute correctly, then sleep. If you'd rather not, save the plan and run it tomorrow morning.

---

## Tomorrow (May 12)

**☐ Review what (if anything) the night build produced.** Read `BUILD_LOG.md` first to see what was done. Visit `talgat.ca` to see live changes. If anything looks wrong, `git revert` the offending commit.

**☐ Begin Phase 2 day build** — run `BUILD_PLAN_DAY.md` in Claude Code. Use Opus 4.7. Estimate: 3–5 hours of attended work. You can pause and resume; BUILD_LOG.md preserves state.

**☐ While the day build runs:** start working on Bikeability ArcGIS Pro completion (the buffer/union/erase steps remaining from the handoff doc). Map exports needed for the bikeability deep page.

---

## May 13

**☐ Bikeability ArcGIS Pro work** — complete the buffer/union/erase workflow, style layers, build the map layout, export to PDF + PNG. Save to `/images/bikeability/`:
- `tier-buffers.png`
- `gap-polygons.png`
- `final-layout.png`

Drop these into the repo, commit, push. The deep page picks them up automatically (image slots are already named in BUILD_PLAN_DAY.md).

**☐ CityFlow GIF** — record a 60-second silent screen recording walking through the app: map, work order creation, AI triage suggestion, dashboard. Convert to GIF (free tool: ScreenToGif on Windows, or `ffmpeg -i input.mp4 -vf "fps=15,scale=800:-1" cityflow-demo.gif`). Drop into `/images/cityflow-demo.gif`. Commit and push.

---

## May 14

**☐ PowerShell scripts** — write the three small scripts in a new `/scripts/` folder of an appropriate repo (could go in talgat.ca repo as a portfolio asset, or in cityflow):
- `Backup-AGOLLayer.ps1` — backs up an ArcGIS Online feature layer to local geojson
- `Check-IISHealth.ps1` — pings IIS site bindings and reports status
- `Deploy-NodeApp-IIS.ps1` — stops/starts a Node app behind IIS

Add a README. Reference from the Building page in the "What's in motion" inventory.

**☐ Three C# app screenshots** — take a clean home/dashboard screenshot of each ASP.NET Core app. Drop into `/images/`:
- `capstone-scheduling.png`
- `capstone-learning.png`
- `capstone-certification.png`

---

## May 15

**☐ Resume rewrite (with Claude in a new chat using MASTER_CONTEXT.md).** The one-page version needs:
- College dates updated to 2023–2026
- IRB Certified interpreter credential added
- CityFlow and Bikeability added to Projects
- Skills recalibrated per new taxonomy
- 500+ outreach bullet moved to extended version only
- Frito-Lay/Marketing dates overlap clarified

Generate PDF. Save to `/resume.pdf` in the repo. The site already links to it.

**☐ Cover letter rewrite (same chat).** Needs:
- C1425 reference
- CityFlow and Bikeability named
- 2–3 specific JD items referenced
- One page, four short paragraphs
- Plain language

Save to a private location — not pushed to GitHub.

---

## May 16

**☐ LinkedIn profile setup (separate Claude chat, ~60 min).** Bring `MASTER_CONTEXT.md` to give Claude the context it needs to draft.
- Headline matching hero subtitle
- About section: 3 sentences max
- Experience matching resume
- Skills: top 10 from refined matrix
- Profile photo or none

Do not connect with anyone at the City of London yet.

**☐ ETL pipeline (optional, high-signal)** — if time allows: build the small Python ETL pipeline pulling London ON open data → PostgreSQL → ArcGIS Online. This hits ETL, Python, PostgreSQL, REST, and ArcGIS in one project. Could be deferred to post-application without hurting the application.

---

## May 17–18 (weekend)

**☐ Cityworks platform primer** — write a one-page overview of Trimble's Cityworks AMS/PLL platform and its ArcGIS Enterprise integration. Drop into the Building page as a section. This shows you've researched the platform you'd be administering.

**☐ OAuth/SSO/Kerberos cheat-sheet** — short comparison document. Drop into the Building page.

**☐ Build the Languages of my life story map (if time allows, otherwise defer).** Three story maps were planned: London ward density, Enterprise architecture, languages-of-my-life. Build whichever is closest to ready. Defer the others to post-application.

**☐ Interview prep document.** Write `interview-prep.md` (private, not pushed). For each featured project (CityFlow, Bikeability) and each of the four studies: prepared 2-minute answer, 3 likely follow-up questions with brief answers. Read it the night before any interview.

**☐ Reach out to references.** Email each: brief context on the role, attach the JD, give them your application timeline. Confirm they're available if contacted.

---

## May 19 (one day before deadline)

**☐ The walk-the-portfolio test.** Morning ritual:
1. Open `talgat.ca` on phone in Chrome incognito.
2. Start a 90-second timer.
3. Scroll once through home only. Don't click deep pages.
4. After 90 seconds, write down:
   - The three most memorable things
   - Anything that confused you
   - Anything that felt thin
5. Fix any (b) or (c) issues that same day.

**☐ Lighthouse audit** — Chrome DevTools → Lighthouse. Aim for >90 on accessibility. Fix any issues.

**☐ Final review of resume + cover letter.** One last pass with fresh eyes.

---

## May 20 (deadline day)

**☐ Submit application** through City of London's career portal.

**☐ Save copies** of everything submitted to your private archives.

**☐ Take the rest of the day.**

---

## Post-application (May 21 onwards)

Things to defer to after submission, in case you want to keep building:

- Phase 2 of Bikeability (population overlay, collision correlation, historical reconstruction)
- The bikeability scoring methodology (Phase 3)
- Windows Server / IIS lab
- The remaining Story Maps
- Connecting with City of London people on LinkedIn (now appropriate, since application is in)

---

## If you need to start a new Claude chat

Paste this as your first message:

```
I'm continuing work on my City of London BSA application (C1425).

Please read these documents from my repo before responding:
1. MASTER_CONTEXT.md — everything you need to know about me, the application, and decisions we've locked
2. NEXT_STEPS.md — my timeline and where I am right now
3. BUILD_LOG.md — what's been built so far

After reading, summarize the current state back to me in 5 lines so I can confirm you're oriented, then we'll continue.
```

The fresh Claude will have the full context. No re-explaining needed.

---

## Emergency tactics if you fall behind

If the May 20 deadline is at risk, here's what to cut in order of acceptability:

**Safe to cut:**
- ETL pipeline (signal-positive but not required)
- Windows Server lab (the JD lists it; OK to flag as "studying")
- Personal Story Maps (defer)
- The "Beyond the one-pager" extended resume PDF (one-pager alone is enough)
- The C# app gifs/screenshots (the cards work without them)
- Lighthouse audit (do quick fix; full audit can be post-application)

**Don't cut:**
- The Personal page (it's lockable as-is)
- The Building page (essential to the honesty narrative)
- The Bikeability deep page (highest-signal project)
- The CityFlow deploy (if it fails, link to GitHub repo only)
- The application submission itself
- The walk-the-portfolio test

The minimum viable submission: working `talgat.ca` with hero, About, Skills calibrated, Building page existing, two featured projects (CityFlow + Bikeability) clickable to working content, Personal page, Resume page with one-pager visible, updated PDF resume submitted via portal, cover letter, references confirmed.

Everything else is signal-additive but not deal-breaking.

---

## End of next-steps document
