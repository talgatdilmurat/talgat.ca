# BUILD PLAN — Day Session (Phase 2)

> This is the larger, eyes-on phase. Run this with Tal awake and reactive. Includes the bikeability deep page, the Building page restructure, the CityFlow repo and deploy, and the architecture diagram. **Run only after BUILD_PLAN_NIGHT.md tasks are complete and reviewed.**

---

## Working principles (re-read these)

1. **Frame the reader, not the writer.** Filter through: *"Would this help the C1425 hiring manager decide, in 90 seconds, that Tal can do the job?"*
2. **Honesty over polish.** No invented skills, no narration of interpreter work, no overclaim.
3. **Voice: plain and sincere.** Slightly literary phrasings only in select moments (e.g. "Beyond the one-pager").
4. **Commit early and often.** Every meaningful change = one commit.
5. **Update BUILD_LOG.md after every commit.**
6. **Stop and ask if uncertain.** Tal is available — don't guess.
7. **Use Opus 4.7 for design moments, Sonnet 4.6 for mechanical edits.** Switch with `/model`.

---

## Task order

Run in this sequence. Some tasks depend on earlier ones.

### Task 1 — Rename gap.html to building.html

```bash
git mv gap.html building.html
```

Update every reference site-wide:
- `index.html` — search for `gap.html` references and update
- `personal.html` — nav link
- `resume.html` — if linked
- `csharp-projects.html` — if linked (this file is being deleted in Task 9, but update anyway in case it's still around)

Inside `building.html` itself:
- `<title>` becomes `Building — Talgat Dilmurat`
- `<span class="nav-title">` becomes `Building` (was `Growth`)
- The `<h1 class="page-title">` currently says `Bridging the Gap`. **Replace with `Building`.**
- The `<p class="page-intro">` currently says *"Most BSA roles ask for three years of direct experience. This page addresses that directly — what the gap is, what's already covered, and how I'm closing the rest."* **Replace with:**

```
A working record of what's coming together right now — the technical skills, scripts, lab environments, and reference documents I'm developing alongside the portfolio itself.
```

Commit message: `rename: gap.html → building.html, reframe page intro as forward-leaning`

---

### Task 2 — Update home nav and mobile nav

In `index.html`, the current nav-links section:

```html
<a href="#projects">Projects</a>
<a href="#gis">GIS</a>
<a href="#skills">Skills</a>
<a href="personal.html" class="nav-pill">Personal</a>
<a href="resume.html" class="nav-pill nav-pill-filled">Resume →</a>
```

**Replace with:**

```html
<a href="#projects">Projects</a>
<a href="#gis">GIS</a>
<a href="building.html">Building</a>
<a href="personal.html">Personal</a>
<a href="resume.html" class="nav-resume">Resume →</a>
```

Note: Skills section removed from nav (the table stays on home, but doesn't need its own nav anchor — it's covered by Projects scrolling).

Same update for the `#mob-nav` block below it.

Commit message: `nav: replace Skills with Building, update mobile nav to match`

---

### Task 3 — Replace Building page content body

The current `building.html` (formerly `gap.html`) has good bones — a stat-bar, advantage cards, a competency progression matrix, a timeline, and a "what's being built next" list.

**Keep all the existing structural elements but make these content changes:**

**3a. Stat-bar — update numbers:**
- Keep "11 Esri Academy courses completed"
- Keep "3yr Software Engineering Technology diploma"
- The "5+ Sectors with direct systems experience" stat is fine
- The "6 Languages spoken (IRB certified ×3)" stat needs updating — IRB certification covers Mandarin, Uyghur, Kazakh (3 languages), and the count is 7 languages total. Update text to: "7 Languages (IRB Certified ×3)"

**3b. Replace the "Honest position" section** (`#position`). Currently has 2 paragraphs about not having 3 years experience. **Replace with:**

```html
<section id="position" class="section" style="background: var(--bg-warm)">
  <div class="wrap">
    <p class="s-label fade">Currently building</p>
    <h2 class="s-title fade">Where I am, where the role calls for, what's in motion</h2>
    <div class="position-text fade">
      <p>The table below maps the C1425 role's technical surface against what I currently have hands-on and what I'm actively building. It's not a confession of gaps — it's a working inventory of where I'm putting my time before May 20.</p>
    </div>

    <table class="inventory-table fade" style="margin-top: 32px; width: 100%; border-collapse: collapse; font-size: 0.88rem;">
      <thead>
        <tr style="border-bottom: 2px solid var(--border-dk);">
          <th style="text-align: left; padding: 12px 14px 12px 0; font-weight: 600; color: var(--text); width: 28%;">Job calls for</th>
          <th style="text-align: left; padding: 12px 14px; font-weight: 600; color: var(--text); width: 36%;">What I have</th>
          <th style="text-align: left; padding: 12px 0 12px 14px; font-weight: 600; color: var(--text); width: 36%;">What's in motion</th>
        </tr>
      </thead>
      <tbody>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>ArcGIS Pro</strong></td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Hands-on — using it now for the London Bikeability spatial analysis (buffer, union, erase workflow; tier-based classification; map layout)</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-mid);">Deepening through the bikeability project's remaining phases</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>ArcGIS Online · hosted feature layers · dashboards</strong></td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Hands-on — published service request layers, built an operational dashboard, content admin work</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-faint);">—</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>ArcGIS Enterprise</strong> (Portal, Server, Monitor)</td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Esri Academy Monitor course; conceptual familiarity with architecture</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-mid);">Working through Trimble and Esri Enterprise architecture documentation; writing an internal primer</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>Cityworks</strong> (AMS, PLL)</td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">No direct exposure</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-mid);">Reading Trimble's Cityworks documentation; writing a primer on AMS/PLL and ArcGIS Enterprise integration</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>REST APIs · JSON</strong></td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Built and documented full CRUD APIs in Spring Boot (Java) and Express (Node); Postman-tested</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-mid);">Adding OAuth login to CityFlow</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>OAuth · SSO · Kerberos</strong></td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Coursework exposure; conceptual familiarity</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-mid);">Implementing OAuth in CityFlow; writing a comparison cheat-sheet for the three protocols</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>SQL Server · PostgreSQL · geodatabases</strong></td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Schema design and analytical queries in PostgreSQL (CityFlow), MySQL (municipal-portfolio studies), ArcGIS Online geodatabase work</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-mid);">Adding versioning and access-control patterns to the CityFlow schema</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>Windows Server · IIS</strong></td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Coursework on enterprise infrastructure</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-mid);">Setting up a Windows Server 2022 trial lab and an IIS-hosted .NET deployment</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>PowerShell · Python · ETL</strong></td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Python for scripting and data analysis</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-mid);">Writing PowerShell scripts for AGOL backup, IIS health checks, Node-on-IIS deployment; building a Python ETL pipeline using London ON open data</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>.NET · React · Leaflet</strong></td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Three ASP.NET Core MVC apps; React + Leaflet on CityFlow; Leaflet on the inline service-request map</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-faint);">—</td>
        </tr>
        <tr>
          <td style="padding: 14px 14px 14px 0; vertical-align: top;"><strong>Business process review · workflow analysis</strong></td>
          <td style="padding: 14px; vertical-align: top; color: var(--text-mid);">Workflow Analysis study (current-state mapping, SLA design, redesigned process); CRM administration and reporting work</td>
          <td style="padding: 14px 0 14px 14px; vertical-align: top; color: var(--text-mid);">Treating the bikeability methodology decision itself as a BSA finding</td>
        </tr>
      </tbody>
    </table>
  </div>
</section>
```

**3c. Keep the existing matrix, timeline, and "next steps" sections** below this table. They already work — just verify nothing references the old "gap" framing in their text.

Commit message: `building: replace position section with inventory table, update stat-bar`

---

### Task 4 — Create the bikeability deep page

Create `bikeability.html` at repo root. This is the **grand-project treatment** Tal asked for.

Use the same stylesheet structure as `building.html` (nav, scroll-bar, footer). The body content:

```html
<!-- HEADER -->
<section id="header">
  <div class="wrap">
    <p class="s-label fade">London ON Bikeability Analysis</p>
    <h1 class="page-title fade">How bikeable is London, and where are the gaps?</h1>
    <p class="page-intro fade">
      A current-state spatial analysis of London Ontario's cycling infrastructure, built on City of London open data. The work classifies every bike route segment into a three-tier protection hierarchy, applies tier-weighted buffer analysis, identifies infrastructure gap polygons, and — equally important — audits the data infrastructure itself.
    </p>
  </div>
</section>

<!-- DATA AUDIT -->
<section id="audit" class="section" style="background: var(--bg-warm);">
  <div class="wrap">
    <p class="s-label fade">The data audit (and what it found)</p>
    <h2 class="s-title fade">Methodology choice as a BSA finding</h2>
    <div class="prose-body fade" style="max-width: 680px; color: var(--text-mid); line-height: 1.8;">
      <p>The original plan was a Level of Traffic Stress (LTS) analysis — a standard methodology in cycling network planning that classifies street segments by how stressful they are to ride, using speed limits, lane counts, and road class.</p>
      <p>The audit of London's open data found those fields aren't available in the published Road_Edges dataset. LTS wasn't feasible.</p>
      <p>This is itself a finding. The analysis pivoted to a buffer-based approach using the protection-tier metadata that <em>is</em> available — a defensible methodology in its own right. But the data limitation is worth flagging back to the open data program as a recommendation: with speed-limit and lane-count fields added, the City would unlock LTS-grade analysis for any future bikeability work.</p>
    </div>
  </div>
</section>

<!-- METHODOLOGY -->
<section id="methodology" class="section">
  <div class="wrap">
    <p class="s-label fade">Methodology</p>
    <h2 class="s-title fade">Tier classification and tier-weighted buffers</h2>
    <div class="prose-body fade" style="max-width: 680px; color: var(--text-mid); line-height: 1.8; margin-bottom: 32px;">
      <p>Every bike infrastructure segment is classified into a protection tier based on infrastructure type, then buffered by a distance calibrated to cyclist behaviour for that tier.</p>
    </div>

    <h3 style="font-size: 0.95rem; font-weight: 600; color: var(--text); margin-bottom: 12px;">Tier classification</h3>
    <table style="width: 100%; max-width: 680px; border-collapse: collapse; font-size: 0.88rem; margin-bottom: 32px;">
      <thead>
        <tr style="border-bottom: 2px solid var(--border-dk);">
          <th style="text-align: left; padding: 10px 14px 10px 0; font-weight: 600;">Tier</th>
          <th style="text-align: left; padding: 10px 14px; font-weight: 600;">Infrastructure type</th>
          <th style="text-align: left; padding: 10px 0 10px 14px; font-weight: 600;">Source</th>
        </tr>
      </thead>
      <tbody>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 10px 14px 10px 0;"><strong>1</strong></td>
          <td style="padding: 10px 14px;">Separated cycle track or multi-use path</td>
          <td style="padding: 10px 0 10px 14px; color: var(--text-mid);">On-Street (Separated) + all Multi-Use Trails</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 10px 14px 10px 0;"><strong>2</strong></td>
          <td style="padding: 10px 14px;">Designated / painted bike lane</td>
          <td style="padding: 10px 0 10px 14px; color: var(--text-mid);">On-Street (Designated)</td>
        </tr>
        <tr>
          <td style="padding: 10px 14px 10px 0;"><strong>3</strong></td>
          <td style="padding: 10px 14px;">Shared / signed route</td>
          <td style="padding: 10px 0 10px 14px; color: var(--text-mid);">On-Street (Shared)</td>
        </tr>
      </tbody>
    </table>

    <h3 style="font-size: 0.95rem; font-weight: 600; color: var(--text); margin-bottom: 12px;">Buffer distances</h3>
    <table style="width: 100%; max-width: 680px; border-collapse: collapse; font-size: 0.88rem; margin-bottom: 32px;">
      <thead>
        <tr style="border-bottom: 2px solid var(--border-dk);">
          <th style="text-align: left; padding: 10px 14px 10px 0; font-weight: 600;">Tier</th>
          <th style="text-align: left; padding: 10px 14px; font-weight: 600;">Distance</th>
          <th style="text-align: left; padding: 10px 0 10px 14px; font-weight: 600;">Rationale</th>
        </tr>
      </thead>
      <tbody>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 10px 14px 10px 0;"><strong>1</strong></td>
          <td style="padding: 10px 14px;">800 m</td>
          <td style="padding: 10px 0 10px 14px; color: var(--text-mid);">Cyclists travel further to access protected infrastructure</td>
        </tr>
        <tr style="border-bottom: 1px solid var(--border);">
          <td style="padding: 10px 14px 10px 0;"><strong>2</strong></td>
          <td style="padding: 10px 14px;">400 m</td>
          <td style="padding: 10px 0 10px 14px; color: var(--text-mid);">Standard comfortable cycling access (~¼ mile)</td>
        </tr>
        <tr>
          <td style="padding: 10px 14px 10px 0;"><strong>3</strong></td>
          <td style="padding: 10px 14px;">200 m</td>
          <td style="padding: 10px 0 10px 14px; color: var(--text-mid);">Useful only if very nearby — shared roads are less attractive</td>
        </tr>
      </tbody>
    </table>

    <div class="prose-body fade" style="max-width: 680px; color: var(--text-mid); line-height: 1.8;">
      <p>Tier-weighted distances follow standard planning practice — ¼ mile (~400 m) is the commonly cited comfortable cycling access distance in NACTO and CROW design guidance, scaled up for protected infrastructure (cyclists will travel further when the experience is safer) and down for shared-road conditions.</p>
    </div>
  </div>
</section>

<!-- ANALYSIS -->
<section id="analysis" class="section" style="background: var(--bg-warm);">
  <div class="wrap">
    <p class="s-label fade">The analysis</p>
    <h2 class="s-title fade">Tier buffers and gap surfaces</h2>
    <div class="prose-body fade" style="max-width: 680px; color: var(--text-mid); line-height: 1.8; margin-bottom: 32px;">
      <p>The workflow in ArcGIS Pro: buffer each tier of bike routes at its designated distance, union the results into a single bikeability surface, then erase that surface from the city boundary to produce gap polygons — areas of London more than the tier-appropriate distance from any bike infrastructure.</p>
    </div>

    <!-- Image placeholders — Tal will drop the actual exports into /images/bikeability/ -->
    <div class="map-outputs" style="display: grid; grid-template-columns: 1fr; gap: 24px; max-width: 800px;">
      <figure style="margin: 0;">
        <div class="img-placeholder fade" style="aspect-ratio: 16/10; background: var(--bg-soft); border: 1px solid var(--border); border-radius: var(--radius); display: flex; align-items: center; justify-content: center; color: var(--text-faint); font-family: var(--mono); font-size: 0.8rem;">
          <!-- Replace with: <img src="images/bikeability/tier-buffers.png" alt="Tier-classified bike route buffers across London ON" style="width:100%; border-radius: var(--radius);"> -->
          [tier-buffers.png — ArcGIS Pro export]
        </div>
        <figcaption style="font-size: 0.78rem; color: var(--text-muted); margin-top: 8px; font-style: italic;">Bike route tiers with buffered access areas (T1 = 800 m, T2 = 400 m, T3 = 200 m).</figcaption>
      </figure>

      <figure style="margin: 0;">
        <div class="img-placeholder fade" style="aspect-ratio: 16/10; background: var(--bg-soft); border: 1px solid var(--border); border-radius: var(--radius); display: flex; align-items: center; justify-content: center; color: var(--text-faint); font-family: var(--mono); font-size: 0.8rem;">
          <!-- Replace with: <img src="images/bikeability/gap-polygons.png" alt="Infrastructure gap polygons across London ON" style="width:100%; border-radius: var(--radius);"> -->
          [gap-polygons.png — ArcGIS Pro export]
        </div>
        <figcaption style="font-size: 0.78rem; color: var(--text-muted); margin-top: 8px; font-style: italic;">Infrastructure gap surface — areas of London not served by any tier of bike infrastructure within the tier-appropriate distance.</figcaption>
      </figure>

      <figure style="margin: 0;">
        <div class="img-placeholder fade" style="aspect-ratio: 16/10; background: var(--bg-soft); border: 1px solid var(--border); border-radius: var(--radius); display: flex; align-items: center; justify-content: center; color: var(--text-faint); font-family: var(--mono); font-size: 0.8rem;">
          <!-- Replace with: <img src="images/bikeability/final-layout.png" alt="Final map layout — London ON bikeability analysis" style="width:100%; border-radius: var(--radius);"> -->
          [final-layout.png — ArcGIS Pro export]
        </div>
        <figcaption style="font-size: 0.78rem; color: var(--text-muted); margin-top: 8px; font-style: italic;">Final composed map layout — bikeability analysis report.</figcaption>
      </figure>
    </div>
  </div>
</section>

<!-- RECOMMENDATIONS -->
<section id="recommendations" class="section">
  <div class="wrap">
    <p class="s-label fade">Recommendations</p>
    <h2 class="s-title fade">For the City</h2>
    <div class="prose-body fade" style="max-width: 680px; color: var(--text-mid); line-height: 1.8;">
      <p><strong>For the cycling network:</strong> the gap polygons identify specific neighbourhoods of London that fall outside tier-weighted access to existing bike infrastructure. These areas are candidates for investment prioritization — particularly where Tier 3 (shared-route) coverage is the only infrastructure available, since Tier 3 is the least attractive form of cycling provision.</p>
      <p><strong>For the open data program:</strong> the published Road_Edges dataset would unlock Level of Traffic Stress (LTS) analysis if it included speed-limit, lane-count, and road-class fields. Adding these would let any analyst — internal or external — produce a more sensitive bikeability assessment than the buffer methodology used here.</p>
    </div>
  </div>
</section>

<!-- ROADMAP -->
<section id="roadmap" class="section" style="background: var(--bg-warm);">
  <div class="wrap">
    <p class="s-label fade">What's next</p>
    <h2 class="s-title fade">Phase 2 and Phase 3</h2>
    <div class="prose-body fade" style="max-width: 680px; color: var(--text-mid); line-height: 1.8; margin-bottom: 32px;">
      <p>This page documents Phase 1 — a descriptive current-state analysis. The work is designed to extend in two further phases that progressively answer different questions about London's cycling network.</p>
    </div>

    <h3 style="font-size: 1rem; font-weight: 600; color: var(--text); margin-bottom: 12px;">Phase 2 — Three directions</h3>
    <ol style="padding-left: 24px; max-width: 680px; color: var(--text-mid); line-height: 1.8; margin-bottom: 32px;">
      <li style="margin-bottom: 12px;"><strong>Population overlay.</strong> Statistics Canada Census Dissemination Areas overlaid on the gap polygons — quantifies how many residents live in underserved areas.</li>
      <li style="margin-bottom: 12px;"><strong>Collision correlation.</strong> Tests whether infrastructure tier predicts cycling collision rates. A finding here would directly justify infrastructure investment priorities.</li>
      <li style="margin-bottom: 12px;"><strong>Historical reconstruction.</strong> Uses the installation and rehabilitation year fields already in the layer attribute tables to map the network at past dates, revealing the network's growth trajectory over time.</li>
    </ol>

    <h3 style="font-size: 1rem; font-weight: 600; color: var(--text); margin-bottom: 12px;">Phase 3 — Synthesis</h3>
    <div class="prose-body fade" style="max-width: 680px; color: var(--text-mid); line-height: 1.8;">
      <p>A composite bikeability scoring methodology derived from Phase 2 findings — combining access, quality, connectivity, exposure, and trajectory into a single index. Calibrated to London ON, and designed to be adaptable to any municipality with comparable open data, providing a standardized comparison metric.</p>
    </div>
  </div>
</section>
```

**Important:** make sure the nav at the top includes a "back to portfolio" link consistent with personal.html and building.html.

Commit message: `add: bikeability.html — full deep page with audit, methodology, analysis, recommendations, roadmap`

---

### Task 5 — Add bikeability featured card on home

In `index.html`, find the projects section. Currently CityFlow is the only featured card; the four supporting projects sit below.

**Insert a second featured card for Bikeability** between the CityFlow featured card and the "Earlier Work — Municipal Services Portfolio" group. The Bikeability featured card should match the visual weight of the CityFlow card.

```html
<!-- ── BIKEABILITY FEATURED CARD ── -->
<div class="featured-card fade">

  <div class="featured-banner">
    <div class="featured-eyebrow"><div class="featured-dot"></div>Featured Project</div>
    <h3 class="featured-title">London ON Bikeability Analysis</h3>
    <p class="featured-tagline">A current-state spatial analysis of London Ontario's cycling network using City of London open data — tier classification, buffer analysis, gap polygon identification, and a finding about the open data itself.</p>
    <div class="featured-chips">
      <span class="fchip">ArcGIS Pro</span>
      <span class="fchip">2,782 segments classified</span>
      <span class="fchip">3-tier methodology</span>
      <span class="fchip">Phase 2 &amp; 3 roadmap</span>
    </div>
  </div>

  <div class="featured-body">
    <div class="featured-features">
      <div class="ff-item"><span class="ff-icon">🗺️</span>Bike infrastructure classified into a protection tier hierarchy</div>
      <div class="ff-item"><span class="ff-icon">📐</span>Tier-weighted buffer analysis (800m / 400m / 200m)</div>
      <div class="ff-item"><span class="ff-icon">🔍</span>Gap polygons identifying underserved neighbourhoods</div>
      <div class="ff-item"><span class="ff-icon">📋</span>BSA-style methodology audit and recommendations report</div>
    </div>

    <div class="featured-tech">
      <span class="ftag hi">ArcGIS Pro</span>
      <span class="ftag hi">Buffer / Union / Erase workflow</span>
      <span class="ftag hi">NAD 1983 UTM Zone 17N</span>
      <span class="ftag">opendata.london.ca</span>
      <span class="ftag">Map layout</span>
    </div>

    <div class="featured-footer">
      <a href="bikeability.html" class="btn-outline">View full analysis →</a>
    </div>
  </div>

</div>
<!-- ── END BIKEABILITY ── -->
```

Note: no video/GIF placeholder for this one — the analysis is a report, not an app demo.

Commit message: `projects: add bikeability featured card on home, parity with CityFlow`

---

### Task 6 — Reframe the four supporting projects as "studies"

The four supporting projects (Work Order REST API, Municipal SQL Database, GIS Service Request Map, Workflow Analysis) currently sit below the CityFlow featured card with a label "Earlier Work — Municipal Services Portfolio."

**Replace that label** with this intro block:

```html
<div class="studies-intro fade" style="margin-top: 48px; margin-bottom: 24px; max-width: 680px;">
  <p class="s-label" style="margin-bottom: 6px;">Studies</p>
  <h3 style="font-size: 1.15rem; font-weight: 600; color: var(--text); letter-spacing: -0.01em; line-height: 1.35; margin-bottom: 10px;">Four lenses on municipal service requests</h3>
  <p style="color: var(--text-muted); font-size: 0.9rem; line-height: 1.65;">Same problem domain — municipal service requests — explored through four lenses before I assembled them into CityFlow. Each study is a stage of learning: schema design, REST API patterns, spatial publication, then process modeling.</p>
</div>
```

**Restyle the four project cards** so they appear visually lighter than the CityFlow card. Specifically: smaller, two-column grid (instead of single full-width). Reduce padding, reduce the size of the h3 inside each, and consolidate to a single shared GitHub link at the bottom of the studies group rather than four separate icons.

Suggested CSS (add to stylesheet):

```css
.studies-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 18px;
  margin-bottom: 24px;
}
@media (max-width: 700px) {
  .studies-grid { grid-template-columns: 1fr; }
}
.study-card {
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 20px;
  transition: border-color 0.2s, transform 0.2s, box-shadow 0.2s;
}
.study-card:hover {
  border-color: var(--border-dk);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(13, 36, 64, 0.06);
}
.study-card h4 {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text);
  margin-bottom: 8px;
  letter-spacing: -0.01em;
}
.study-card p {
  font-size: 0.82rem;
  color: var(--text-muted);
  line-height: 1.55;
  margin-bottom: 10px;
}
.study-card .study-stage {
  font-size: 0.68rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--accent-brass);
  margin-bottom: 8px;
  display: block;
}
.study-card .study-tech {
  font-size: 0.72rem;
  color: var(--text-faint);
  font-family: var(--mono);
}
.studies-shared-link {
  text-align: center;
  margin-top: 16px;
  font-size: 0.82rem;
}
.studies-shared-link a {
  color: var(--text-muted);
  border-bottom: 1px solid var(--border-dk);
  padding-bottom: 1px;
}
.studies-shared-link a:hover { color: var(--text); }
```

**Then restructure the four cards** into this grid:

```html
<div class="studies-grid">

  <div class="study-card fade">
    <span class="study-stage">Study 01</span>
    <h4>Schema design</h4>
    <p>First I needed to understand how municipal service request data should be structured. Designed a normalized 6-table schema with foreign keys, indexes, and a status history audit trail.</p>
    <p class="study-tech">MySQL · normalization · audit trail</p>
  </div>

  <div class="study-card fade">
    <span class="study-stage">Study 02</span>
    <h4>REST API patterns</h4>
    <p>Built an 8-endpoint Spring Boot REST API around that schema — full CRUD plus filtering, keyword search, and an analytics endpoint. Production config included.</p>
    <p class="study-tech">Java 17 · Spring Boot · Hibernate · H2 / MySQL</p>
  </div>

  <div class="study-card fade">
    <span class="study-stage">Study 03</span>
    <h4>Spatial publication</h4>
    <p>Published the data spatially in ArcGIS Online as a hosted feature layer — plus a Leaflet.js browser version loading from CSV with no backend.</p>
    <p class="study-tech">ArcGIS Online · Leaflet.js · CSV</p>
  </div>

  <div class="study-card fade">
    <span class="study-stage">Study 04</span>
    <h4>Process modeling</h4>
    <p>Stepped back and modeled the underlying business process — current-state mapping, root cause analysis of 7 pain points, redesigned workflow with SLA escalation.</p>
    <p class="study-tech">Process mapping · BPMN · SLA design</p>
  </div>

</div>

<p class="studies-shared-link"><a href="https://github.com/talgatdilmurat/municipal-portfolio" target="_blank">All four studies on GitHub →</a></p>
```

Replace the four old project-item divs entirely. Their content is now embedded in the new compact cards above.

Commit message: `projects: reframe four supporting projects as studies — pyramid visual hierarchy`

---

### Task 7 — Inline Leaflet map in GIS section

In the GIS section of `index.html`, add a working inline map below the existing GIS cards (dashboard and map).

```html
<!-- INLINE LEAFLET MAP -->
<div class="inline-map-block fade" style="margin-top: 48px;">
  <p class="s-label" style="margin-bottom: 6px;">Live data</p>
  <h3 style="font-size: 1.05rem; font-weight: 600; color: var(--text); letter-spacing: -0.01em; margin-bottom: 10px;">Service requests, inline</h3>
  <p style="color: var(--text-muted); font-size: 0.88rem; line-height: 1.6; margin-bottom: 18px; max-width: 560px;">
    The same 50 service request records published to ArcGIS Online, also rendered here as a Leaflet.js map loading directly from CSV. No backend, no plugins — just data on a basemap.
  </p>
  <div id="inline-leaflet-map" style="height: 400px; width: 100%; max-width: 800px; border: 1px solid var(--border); border-radius: var(--radius); overflow: hidden;"></div>
</div>
```

Add to `<head>`:

```html
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
```

Add to the bottom `<script>` block of index.html (before the closing `</script>` of the existing script section):

```javascript
// Inline Leaflet map — service requests
const inlineMapEl = document.getElementById('inline-leaflet-map');
if (inlineMapEl) {
  const inlineMap = L.map('inline-leaflet-map').setView([42.984, -81.246], 11);
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors',
    maxZoom: 18
  }).addTo(inlineMap);

  // If you have a service requests CSV available at /data/service-requests.csv, load it here.
  // For now: a few demo pins distributed across London ON.
  const demoRequests = [
    { lat: 42.984, lng: -81.246, type: 'pothole', priority: 'medium' },
    { lat: 43.010, lng: -81.275, type: 'streetlight', priority: 'low' },
    { lat: 42.965, lng: -81.225, type: 'graffiti', priority: 'low' },
    { lat: 42.998, lng: -81.260, type: 'drainage', priority: 'high' },
    { lat: 42.972, lng: -81.290, type: 'pothole', priority: 'high' },
  ];
  const colors = { pothole: '#c97b54', streetlight: '#5b80b8', graffiti: '#8aaad0', drainage: '#2e5496' };
  demoRequests.forEach(r => {
    L.circleMarker([r.lat, r.lng], {
      radius: 8,
      fillColor: colors[r.type] || '#64748b',
      color: '#fff',
      weight: 2,
      opacity: 1,
      fillOpacity: 0.85
    }).bindPopup(`<strong>${r.type}</strong><br>priority: ${r.priority}`).addTo(inlineMap);
  });
}
```

If there's an existing service-requests.csv anywhere in the repo, prefer loading from it via fetch instead of the demo array. Check `/data/` and `/images/` first.

Commit message: `gis: add inline Leaflet map with service request pins`

---

### Task 8 — Cross-reference line to Bikeability in GIS section

At the very bottom of the GIS section (below the inline map), add:

```html
<p class="fade" style="margin-top: 32px; font-size: 0.88rem; color: var(--text-muted); padding-top: 24px; border-top: 1px solid var(--border); max-width: 680px;">
  Also see: <a href="bikeability.html" style="color: var(--text); border-bottom: 1px solid var(--accent-brass); padding-bottom: 1px;">London Bikeability Analysis →</a> — a longer-form spatial analysis report on London's cycling network and infrastructure gaps.
</p>
```

Commit message: `gis: add cross-reference to bikeability deep page`

---

### Task 9 — Move C# apps to Coursework page, delete csharp-projects.html

The C# / ASP.NET Core projects currently sit on a separate `csharp-projects.html` page with placeholders. Per our decision: fold them into the Coursework section as evidence of degree work, not into the Projects narrative.

**On `index.html`:** find the Coursework section (`#coursework`). After the Centennial College course grid (and before the "Full transcript available on request" line), add:

```html
<!-- Capstone-style projects -->
<div style="margin-top: 48px;">
  <h3 class="fade" style="font-size: 0.88rem; font-weight: 600; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.07em; margin-bottom: 16px;">Capstone-style projects</h3>
  <div class="capstone-grid" style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px;">

    <div class="capstone-card fade" style="border: 1px solid var(--border); border-radius: var(--radius); padding: 18px; background: var(--bg);">
      <div style="aspect-ratio: 4/3; background: var(--bg-soft); border-radius: 4px; margin-bottom: 12px; display: flex; align-items: center; justify-content: center; color: var(--text-faint); font-family: var(--mono); font-size: 0.7rem;">
        <!-- Replace with: <img src="images/capstone-scheduling.png" alt="Interpreter Scheduling System" style="width:100%; height:100%; object-fit:cover; border-radius:4px;"> -->
        [screenshot]
      </div>
      <h4 style="font-size: 0.88rem; font-weight: 600; color: var(--text); margin-bottom: 6px;">Interpreter Scheduling System</h4>
      <p style="font-size: 0.78rem; color: var(--text-muted); line-height: 1.55;">Multi-language appointment scheduling with analytics dashboard, profile management, and appointment lifecycle.</p>
      <p style="font-size: 0.7rem; color: var(--text-faint); font-family: var(--mono); margin-top: 8px;">ASP.NET Core MVC · EF Core · SQL Server</p>
    </div>

    <div class="capstone-card fade" style="border: 1px solid var(--border); border-radius: var(--radius); padding: 18px; background: var(--bg);">
      <div style="aspect-ratio: 4/3; background: var(--bg-soft); border-radius: 4px; margin-bottom: 12px; display: flex; align-items: center; justify-content: center; color: var(--text-faint); font-family: var(--mono); font-size: 0.7rem;">
        [screenshot]
      </div>
      <h4 style="font-size: 0.88rem; font-weight: 600; color: var(--text); margin-bottom: 6px;">Language Learning Platform</h4>
      <p style="font-size: 0.78rem; color: var(--text-muted); line-height: 1.55;">Multi-language learning platform with structured progression, vocabulary tracking, and admin tools.</p>
      <p style="font-size: 0.7rem; color: var(--text-faint); font-family: var(--mono); margin-top: 8px;">ASP.NET Core MVC · EF Core · SQL Server</p>
    </div>

    <div class="capstone-card fade" style="border: 1px solid var(--border); border-radius: var(--radius); padding: 18px; background: var(--bg);">
      <div style="aspect-ratio: 4/3; background: var(--bg-soft); border-radius: 4px; margin-bottom: 12px; display: flex; align-items: center; justify-content: center; color: var(--text-faint); font-family: var(--mono); font-size: 0.7rem;">
        [screenshot]
      </div>
      <h4 style="font-size: 0.88rem; font-weight: 600; color: var(--text); margin-bottom: 6px;">Certification Tracker</h4>
      <p style="font-size: 0.78rem; color: var(--text-muted); line-height: 1.55;">Study and certification tracking application with progress dashboards and reminder workflows.</p>
      <p style="font-size: 0.7rem; color: var(--text-faint); font-family: var(--mono); margin-top: 8px;">ASP.NET Core MVC · EF Core · SQL Server</p>
    </div>

  </div>
</div>
```

**Also remove the existing C# project card from the projects section** (the one currently below the four studies with the cs-group class). It's now appropriately housed in Coursework, not in the projects narrative.

**Then delete `csharp-projects.html`:**

```bash
git rm csharp-projects.html
```

Commit message: `coursework: fold C# apps into Coursework as capstone projects, delete standalone page`

---

### Task 10 — Topographic line motif on section dividers

This is a subtle visual touch: replace the flat 1px section borders between major sections with a faint topographic-contour SVG pattern.

Create the SVG once, then reuse via CSS background. Add to the stylesheet:

```css
.section-divider-topo {
  position: relative;
  border-top: none;
}
.section-divider-topo::before {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  max-width: 860px;
  height: 24px;
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 860 24' preserveAspectRatio='none'><path d='M0,12 Q 60,4 120,12 T 240,12 T 360,12 T 480,12 T 600,12 T 720,12 T 840,12 L 860,12' fill='none' stroke='%23c8daf0' stroke-width='0.8' opacity='0.5'/><path d='M0,18 Q 50,12 100,18 T 200,18 T 300,18 T 400,18 T 500,18 T 600,18 T 700,18 T 800,18 L 860,18' fill='none' stroke='%23c8daf0' stroke-width='0.6' opacity='0.35'/></svg>");
  background-repeat: no-repeat;
  background-size: 100% 100%;
  pointer-events: none;
}
```

Apply the `section-divider-topo` class to the section opening between **major** sections only — not between every section. Suggested placement:
- Between #about and #projects
- Between #gis and #storymaps (or wherever the GIS area ends)
- Between #coursework and #learning
- Between #gateway and #contact

This is restraint — the motif works because it appears 4-5 times across the page, not 12. If it appears too often, dilutes the effect.

Commit message: `style: add topographic line motif to major section dividers`

---

### Task 11 — Resume page restructure: two-tier (one-page + extended)

The current `resume.html` is the extended version. Restructure as:

1. **Top of page** — a polished one-page resume version (same content as the PDF Tal submits with applications), with a download button.
2. **Divider with anchor link** — *"Beyond the one-pager ↓"*
3. **Extended version below** — the current detailed content, also with a download button.

The one-page version should match the styling shown in the current resume.html. The "extended" section below is just the current content kept intact.

The implementation: at the top of the resume body, add a new `.resume-onepager` section with the compact resume content. Below it, a divider, then keep the existing `.resume-wrap` content as the "Beyond the one-pager" section.

The one-page content matches Jake's Resume aesthetic — black serif headings, tight bullets, name and contact at top, then Education / Experience / Projects / Skills sections compact enough to fit on one page when printed.

Use this structure for the one-pager block:

```html
<!-- ONE-PAGE RESUME -->
<section id="onepager" class="resume-wrap" style="max-width: 760px; margin: 0 auto; padding: 60px 28px 40px;">

  <div style="text-align: center; margin-bottom: 28px;">
    <h1 style="font-family: Georgia, 'Times New Roman', serif; font-size: 1.9rem; font-weight: 700; color: var(--text); letter-spacing: -0.01em; margin-bottom: 6px;">Talgat Dilmurat</h1>
    <p style="font-size: 0.85rem; color: var(--text-muted);">London, Ontario · talgat.dilmurat.tech@gmail.com · talgat.ca · github.com/talgatdilmurat</p>
  </div>

  <div class="download-cta" style="text-align: center; margin-bottom: 36px;">
    <a href="/resume.pdf" download style="display: inline-block; padding: 8px 16px; border: 1px solid var(--border-dk); border-radius: 5px; font-size: 0.78rem; color: var(--text-mid); text-decoration: none;">Download PDF →</a>
  </div>

  <!-- Education -->
  <div class="r-section">
    <h2 class="r-section-title" style="font-family: Georgia, serif; font-size: 0.95rem; font-weight: 700; color: var(--text); border-bottom: 1px solid var(--border-dk); padding-bottom: 4px; margin-bottom: 12px; letter-spacing: 0.04em; text-transform: uppercase;">Education</h2>
    <p style="margin-bottom: 14px; font-size: 0.85rem;"><strong>Advanced Diploma, Software Engineering Technology</strong> · Centennial College, Toronto ON · 2023–2026<br>
    <span style="color: var(--text-muted);">Coursework: Databases, Enterprise Systems, REST APIs, Cloud Computing, Business Systems Analysis, Programming</span></p>
    <p style="margin-bottom: 0; font-size: 0.85rem;"><strong>ArcGIS Training</strong> · Esri Academy · 2026<br>
    <span style="color: var(--text-muted);">11 courses including: ArcGIS Pro / Online, Business Analyst Pro, Systems Approach to ArcGIS, Coordinate Systems, Data Management, AI in ArcGIS, Administering ArcGIS Online, ArcGIS Monitor</span></p>
  </div>

  <!-- Experience -->
  <div class="r-section" style="margin-top: 24px;">
    <h2 class="r-section-title" style="font-family: Georgia, serif; font-size: 0.95rem; font-weight: 700; color: var(--text); border-bottom: 1px solid var(--border-dk); padding-bottom: 4px; margin-bottom: 12px; letter-spacing: 0.04em; text-transform: uppercase;">Experience</h2>

    <p style="margin-bottom: 8px; font-size: 0.85rem;"><strong>Sales Delivery Specialist</strong> · Frito-Lay / PepsiCo · London ON · Aug 2023 – Present</p>
    <ul style="margin-bottom: 14px; padding-left: 22px; font-size: 0.83rem; color: var(--text-mid); line-height: 1.55;">
      <li>Operate handheld logistics systems to track deliveries, inventory, and daily transactions with high accuracy</li>
      <li>Reconcile physical stock against system records in real time, maintaining data integrity</li>
      <li>Coordinate with retail partners to resolve delivery issues and improve route efficiency</li>
    </ul>

    <p style="margin-bottom: 8px; font-size: 0.85rem;"><strong>Certified Language Interpreter</strong> · Freelance / Agency · 2020 – Present</p>
    <ul style="margin-bottom: 14px; padding-left: 22px; font-size: 0.83rem; color: var(--text-mid); line-height: 1.55;">
      <li>IRB Certified Interpreter (Mandarin · Uyghur · Kazakh); interpreted across medical, legal, government, banking, and emergency-services contexts</li>
      <li>Operate under formal procedural requirements with high accuracy and confidentiality demands</li>
    </ul>

    <p style="margin-bottom: 8px; font-size: 0.85rem;"><strong>Founder &amp; Operations Lead</strong> · Noah's Art (E-commerce) · Remote · Mar 2021 – Mar 2023</p>
    <ul style="margin-bottom: 14px; padding-left: 22px; font-size: 0.83rem; color: var(--text-mid); line-height: 1.55;">
      <li>Designed and managed end-to-end workflows: inventory, fulfillment, supplier coordination, international shipping</li>
      <li>Analyzed sales and customer data to optimize marketing spend and product performance</li>
    </ul>

    <p style="margin-bottom: 8px; font-size: 0.85rem;"><strong>Administrative &amp; Development Operations</strong> · Nonprofit / Freelance · Apr 2020 – Sep 2021</p>
    <ul style="margin-bottom: 14px; padding-left: 22px; font-size: 0.83rem; color: var(--text-mid); line-height: 1.55;">
      <li>Managed NationBuilder CRM data and produced reports for fundraising, revenue, and leadership decisions</li>
      <li>Documented operational workflows, calling procedures, and SOPs for staff and volunteer consistency</li>
      <li>Trained staff and volunteers on CRM usage, data handling, and reporting</li>
    </ul>

    <p style="margin-bottom: 8px; font-size: 0.85rem;"><strong>Marketing Operations Assistant</strong> · ONESTUDIO · Remote · Dec 2021 – Mar 2023</p>
    <ul style="margin-bottom: 0; padding-left: 22px; font-size: 0.83rem; color: var(--text-mid); line-height: 1.55;">
      <li>Generated performance reports and analyzed campaign data across CRM, CMS, and email marketing platforms</li>
      <li>Troubleshot workflow and system issues across marketing operations</li>
    </ul>
  </div>

  <!-- Projects -->
  <div class="r-section" style="margin-top: 24px;">
    <h2 class="r-section-title" style="font-family: Georgia, serif; font-size: 0.95rem; font-weight: 700; color: var(--text); border-bottom: 1px solid var(--border-dk); padding-bottom: 4px; margin-bottom: 12px; letter-spacing: 0.04em; text-transform: uppercase;">Projects</h2>

    <p style="margin-bottom: 6px; font-size: 0.85rem;"><strong>CityFlow</strong> — Full-stack municipal asset management system · React, Node.js, PostgreSQL, Leaflet, Anthropic API · <a href="https://talgat.ca" style="color: var(--text-mid);">talgat.ca</a></p>
    <p style="margin-bottom: 10px; font-size: 0.83rem; color: var(--text-mid); line-height: 1.55;">Interactive asset map, work order lifecycle, AI-assisted triage (experimental), KPI dashboard.</p>

    <p style="margin-bottom: 6px; font-size: 0.85rem;"><strong>London ON Bikeability Analysis</strong> — ArcGIS Pro spatial analysis · City of London open data</p>
    <p style="margin-bottom: 10px; font-size: 0.83rem; color: var(--text-mid); line-height: 1.55;">Tier classification, buffer analysis, gap polygon identification, and a methodology audit finding on the open data program.</p>

    <p style="margin-bottom: 6px; font-size: 0.85rem;"><strong>Municipal Service Request Studies</strong> — Four lenses: SQL schema, Spring Boot REST API, ArcGIS Online map, workflow analysis · <a href="https://github.com/talgatdilmurat/municipal-portfolio" style="color: var(--text-mid);">GitHub</a></p>
  </div>

  <!-- Skills -->
  <div class="r-section" style="margin-top: 24px;">
    <h2 class="r-section-title" style="font-family: Georgia, serif; font-size: 0.95rem; font-weight: 700; color: var(--text); border-bottom: 1px solid var(--border-dk); padding-bottom: 4px; margin-bottom: 10px; letter-spacing: 0.04em; text-transform: uppercase;">Technical Skills</h2>
    <p style="font-size: 0.82rem; color: var(--text-mid); line-height: 1.7;">
      <strong>GIS:</strong> ArcGIS Pro, ArcGIS Online, Leaflet.js, Spatial Data, Coordinate Systems<br>
      <strong>Web:</strong> React, Node.js, .NET / C#, REST APIs, JSON<br>
      <strong>Data:</strong> SQL, PostgreSQL, MySQL, Relational Modeling<br>
      <strong>Systems:</strong> Python, Git, Jira, Linux/Unix<br>
      <strong>Business Analysis:</strong> Process Mapping, Workflow Documentation, Requirements Gathering<br>
      <strong>Languages:</strong> English, Mandarin, Uyghur (IRB), Kazakh (IRB), Arabic, Russian, Turkish
    </p>
  </div>

</section>

<!-- DIVIDER + ANCHOR -->
<div style="max-width: 760px; margin: 60px auto 0; padding: 0 28px; text-align: center;">
  <div style="border-top: 1px solid var(--border); padding-top: 32px;">
    <p style="font-size: 0.82rem; color: var(--text-muted); letter-spacing: 0.04em; text-transform: uppercase;">Beyond the one-pager ↓</p>
  </div>
</div>

<!-- EXTENDED — the existing detailed content stays below this point -->
```

Below this, keep the existing extended resume content. Add a download button at the top of the extended section too (`/resume-extended.pdf`).

**PDF generation:** Tal will provide the PDFs (or Claude Code can generate them via headless Chrome later). For now, leave the `/resume.pdf` and `/resume-extended.pdf` links — they'll 404 until the PDFs are dropped in, which is fine for the build.

Commit message: `resume: restructure as two-tier (one-pager top, extended below)`

---

### Task 12 — CityFlow rename, repo creation, and deploy

**This is the cross-repo task.** Tal will need to be present to provide GitHub credentials if needed.

The CityFlow code lives locally on Tal's machine. From the earlier conversation transcripts, the local path is approximately:

```
C:\Users\Talgat\Documents\Claude\Projects\civicworks\
```

(or wherever the React/Node/PostgreSQL code is — Tal should confirm. If unsure, search for `package.json` files that mention React + Express in the Documents tree.)

**Steps:**

1. **Rename CivicWorks → CityFlow in the code** — find/replace across:
   - All `.md` files
   - `package.json` files (frontend and backend) — change `"name"` field
   - Any HTML title tags
   - Any visible UI strings (the brand displayed in the app's nav/header)
   - README files

2. **Create new GitHub repo `cityflow`** under `github.com/talgatdilmurat`:
   - Use `gh repo create cityflow --public --description "Full-stack municipal asset management system — React, Node.js, PostgreSQL, Leaflet, AI-assisted triage"` if the GitHub CLI is installed.
   - Otherwise: Tal creates manually via github.com web UI and provides the URL.

3. **Initial commit and push:**
   ```bash
   cd <cityflow-folder>
   git init
   git add .
   git commit -m "initial commit: CityFlow — full-stack municipal asset management"
   git branch -M main
   git remote add origin https://github.com/talgatdilmurat/cityflow.git
   git push -u origin main
   ```

4. **Deploy to Render** (free tier):
   - Render handles Node + PostgreSQL + static frontend cleanly in one project.
   - Tal creates a Render account if not already (use GitHub login).
   - New Web Service → connect the `cityflow` GitHub repo → choose Node environment.
   - Configure build commands (`npm install && npm run build` for frontend, etc. — depends on actual repo structure).
   - Add PostgreSQL add-on or configure external DB.
   - Set `ANTHROPIC_API_KEY` environment variable from Tal's existing setup.
   - Deploy.

5. **Note the live URL** and update the CityFlow featured card on `talgat.ca` to link to it:
   - In `index.html`, find the CityFlow featured card. Replace `https://github.com/talgatdilmurat` with the actual live deploy URL.
   - Also update or add a "View live →" link in the card footer.

6. **Add deployment disclaimer** somewhere on the CityFlow card on `talgat.ca`:
   ```html
   <p style="font-size: 0.72rem; color: var(--text-faint); margin-top: 8px;">Hosted on free-tier infrastructure — may take 30 seconds to wake up after inactivity.</p>
   ```

Commit message in talgat.ca repo: `cityflow: rename, deploy live, link from featured card`

**If Render deploy is complicated and takes more than 30 minutes:** flag it in BUILD_LOG.md as `[NEEDS TAL]` and skip — better to have the code on GitHub with a "live deployment in progress" note than to bog the entire build down.

---

### Task 13 — Architecture diagram (CityFlow)

This is a design moment. Use Opus 4.7 for this task. Create an SVG architecture diagram for the CityFlow deep page.

Create `cityflow.html` deep page first (similar structure to `bikeability.html` — Question → Constraints → Decisions → What I built → What I'd change with another month).

Inside `cityflow.html`, embed an SVG architecture diagram. Four to six boxes max. Show: React frontend → Express API → PostgreSQL → Anthropic API. Annotated with auth, data flow, and one explicit "why this layer" caption per box.

This SVG should look hand-thought, not auto-generated. Use the same palette as the site (navy, ice-blue, brass). Aim for clarity over cleverness.

Suggested structure:

```
[ React frontend ]  ←→  [ Express API ]  ←→  [ PostgreSQL ]
       (Leaflet map,        (REST endpoints,      (Service requests,
        Recharts,             validation,           work orders,
        auth UI)              business logic)       audit log)
                                   ↓
                          [ Anthropic API ]
                          (Triage suggestions,
                           experimental)
```

Also include a small data-flow diagram showing a single service request lifecycle: citizen submits → API receives → DB writes → AI triage suggests → human reviewer confirms → work order created.

Commit message: `cityflow: add deep page with architecture and data-flow diagrams`

---

### Task 14 — Final cleanup, push, and verify

1. Run `git status` — verify nothing unintended is uncommitted.
2. Run `git log --oneline -30` — review the day's work.
3. Push: `git push origin main`.
4. Wait 60 seconds for Netlify to deploy.
5. Open `talgat.ca` in a browser. Walk through the changes:
   - Hero animation runs once and settles
   - Skills table has `(studying)` markers in brass
   - Building page exists at `talgat.ca/building`
   - Bikeability deep page exists at `talgat.ca/bikeability`
   - CityFlow card links to live deploy (or has clear "in progress" if deferred)
   - Inline Leaflet map works
   - Custom 404 appears when navigating to a bad URL
   - Favicon shows in browser tab
6. Run Lighthouse from Chrome DevTools — aim for >90 accessibility.

Log results in BUILD_LOG.md, including any Lighthouse findings to address.

Commit message: `session: day phase 2 complete — bikeability, cityflow, building, deploy verified`

---

## End-of-session BUILD_LOG entry

```
## [YYYY-MM-DD HH:MM] — Phase 2 Day Session Complete

**Tasks completed:** [list 1 through 14, marking any skipped]
**Total commits:** [number]
**Files created:** building.html (renamed), bikeability.html, cityflow.html, [etc]
**Files deleted:** csharp-projects.html
**Cross-repo work:** cityflow repo created at github.com/talgatdilmurat/cityflow, deployed to [URL]
**Live site status:** [verified working / partially working / issues]

**Outstanding for Tal:**
- [Asset drops: bikeability map PNGs, CityFlow GIF, C# screenshots]
- [Any NEEDS TAL items]
- [LinkedIn profile setup]
- [Resume PDFs need to be generated and dropped at /resume.pdf and /resume-extended.pdf]
- [Walk-the-portfolio test on May 19]
```

---

## End of day plan
