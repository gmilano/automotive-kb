---
industry: automotive
region: Global
updated: 2026-11-24
---

# 📡 Trends — Automotive

> Current trends, updated 2026-11-24. Project and vendor self-reported performance figures are labelled
> as such. Dates name their instrument.

## 🆕 New on 2026-11-24 — five trends. The first two are corrections of this KB's own published claims.

### N19 — A `0-repos` gap has three shapes, and calling them all "a gap" has been costing accuracy

**N16 (2026-11-21) established that a gap can be a vocabulary artefact. This pass measured all three
standing gaps and found that only *one* was an artefact — the other two were real, but real in
different ways.** The distinction is not pedantry; each shape leads to a different sentence in a
proposal:

| Shape | Measurement signature | The sentence it licenses |
|---|---|---|
| ⚫ **ABSENT** | A **licence-filtered** query returns ~nothing. *Purpose-built automotive plant-floor inspection: `automotive manufacturing defect license:apache-2.0` → **1 repo, 1★**.* | *"One does not exist."* **Assertable in writing.** |
| 🟡 **UNMAINTAINED LONG TAIL** | Many repos, **all 0–2★**. *`battery state of health license:mit` → **98 repos**, top ten all 0–2★.* | *"Supply exists and none of it is maintained."* **Budget to build.** |
| 🔴 **ARTEFACT** | A short or re-worded query surfaces a mature anchor. *EV/battery: `PyBaMM` **BSD-3, 1,742★**; `foxBMS` **BSD-3, 512★**.* | *"There is a base. We start from it."* |

**The long tail is the dangerous shape**, because two opposite wrong answers both come out of it: a repo
count says *"98 options"* and a gap label says *"nothing exists."* Neither is true.

**Carry this into every KB in the fleet.** Any file still reading `0 repos` is making one of three very
different claims and does not yet know which.

### N20 — 🔴 This KB's six-pass "zero LATAM-origin repos" finding was an artefact of **searching in English**

**Withdrawn as stated.** `automotriz` returns **2,458 repositories**. Every prior leg across six passes
used English terms against an index that matches name, description and topics — so a repository called
`TallerAutomotriz` or `GestorVeicular`, described in Spanish or Portuguese, **was unreachable by
construction.**

**What survives, and it is sharper than what it replaces.** Licence distribution of the first 100
`automotriz` repositories, measured directly: **95 carry no licence file at all**, 4 MIT, 1 NOASSERTION.
No licence means **all rights reserved** — *legally less usable than GPL*, which at least grants rights.
Hand-inspected, the population is coursework, workshop-management MVPs and agency demo sites.

**The regional constraint was never developer supply. It is licensing hygiene** — and unlike an absence,
that is a billable problem (licence remediation, a regional permissive baseline). See `intel/market.md`
→ **LATAM** and `repos/trending.md` → 2026-11-24.

**The general lesson, which applies to every non-Anglophone region in all twelve KBs:** 🔴 **a discovery
leg run only in English cannot support a claim about regional authorship.** APAC is the next suspect —
Chinese-language queries have never been run here either, and this KB holds several APAC-origin rows
found only because their authors wrote English descriptions.

### N21 — Automotive compliance evidence is becoming **CI output** instead of a consultant's assertion

`topic:iso26262` — 73 repositories, a query this KB had never run — surfaced a permissive tool tier that
did not previously appear in any pass:
**[github/codeql-coding-standards](https://github.com/github/codeql-coding-standards) — MIT, 235★,
MISRA C/C++ and AUTOSAR C++14 implemented as CodeQL queries and maintained by GitHub itself**, plus
`useblocks/sphinx-needs` (MIT, 329★) for requirement↔code↔test traceability as docs-as-code,
`QuantumLeaps/spexygen` (MIT, 43★), and `WinterLabsHQ/maisha` (MIT, 8★, explicitly *"the vendor-neutral
alternative"* for MISRA C / CERT C / BARR-C).

**Why this is a trend and not a tool list:** the automotive assurance market is built on **paid static
analysers**, and the MISRA/AUTOSAR check has been the licence that anchors the engagement. A permissive
checker maintained by the host of the world's code moves that check into the pipeline. The deliverable
stops being *"we assessed your compliance"* and becomes *"your compliance is now a build artefact that
regenerates on every commit."*

**Direction to watch:** whether the paid analysers respond on **certification evidence** (tool
qualification per ISO 26262-8, which CodeQL does *not* have) — that is the moat, and it is a real one.
A qualified tool's output is admissible to an assessor; an unqualified tool's output is engineering
evidence that still needs a qualification argument. **Do not promise a client that an open checker
discharges a tool-qualification duty.**

### N22 — The regulatory inversion: **APAC now has the world's most concrete AI-driving obligations**, while NA is advisory and EMEA's dates are contested

For several passes this KB treated APAC regulation as unreachable and EMEA as the regime that drives
compliance work. **Both halves of that are now wrong.** Ranked by *how precisely a duty can be dated*:

1. **APAC — dated, mandatory, national.** China's **GB 44721-2026**, a *mandatory* national standard for
   L3/L4 automated-driving safety, **takes effect 1 July 2027**; **GB 47955-2026** for combined driver
   assistance (L0–L2) **applies from 1 January 2027**. First L3 conditional approvals already issued
   (**Changan/Deepal, BAIC/Arcfox**, designated roads in Beijing and Chongqing); MIIT says a second batch
   is in progress. **Korea's AI Basic Act takes effect January 2026.**
2. **EMEA — real duties, disputed dates.** AI Act Article 50 transparency has applied since
   **2 August 2026**, but the Digital Omnibus (**Reg. (EU) 2026/1744**) moved Annex III high-risk to
   **2 December 2027** and Annex I product-embedded — *where motor vehicles sit, Section B* — to
   **2 August 2028**. For vehicles the sectoral legislation carries the AI requirements, so **not every
   automotive AI feature is a high-risk system under the Act.**
3. **NA — no dated obligation at all.** AV STEP **withdrawn** (June 2026); exemptions granted
   case-by-case under **49 CFR § 555** (Zoox first); a domestic exemption pathway is *beginning*
   rulemaking. There is **no enumerated high-risk list and no filing counter.**

**The commercial consequence, and it reverses the usual assumption:** a client asking *"what must we
comply with, and by when?"* gets a **precise, dated answer in China**, a **duty-shaped but
date-contested** answer in Europe, and **"it depends on your exemption"** in the United States. **Scope
APAC work against dated standards, EMEA work against duties rather than dates, and NA work as
advisory.** Full citations per region in `intel/market.md`.

### N23 — The incumbents, not the startups, are opening the automotive tool layer

Four of this pass's strongest permissive finds come from organisations with every commercial reason not
to publish:

| Publisher | Repo | Grant (byte-read) |
|---|---|---|
| **Vector Informatik GmbH** (Tier-1 measurement/calibration tool vendor) | `vectorgrp/XCPlite` — ASAM XCP on Ethernet, 271★ | **MIT**, *"Copyright (c) 2026 Vector Informatik GmbH"* |
| **GitHub** | `github/codeql-coding-standards` — MISRA/AUTOSAR C++14, 235★ | **MIT** |
| **Fraunhofer IISB** | `foxBMS/foxbms-2` — automotive BMS hardware + software, 512★ | **BSD-3-Clause** (software) + CC-BY-4.0 (docs) |
| **IBM** | `IBM/AssetOpsBench` — Industry 4.0 agent benchmark, 2,483★ | **Apache-2.0** |
| **Toyota Connected North America** *(held)* | `toyota-connected/ivi-homescreen` — automotive display embedder, 404★ | **Apache-2.0** |

**The pattern:** incumbents are opening the **protocol, standard and benchmark** layers while keeping
the **qualified tool, the certification and the integration** proprietary. That is a rational and stable
split, and it tells a studio exactly where the margin is: **not in reimplementing XCP or MISRA — those
are now free from the people who own them — but in qualification, integration and evidence.**

**Contrast with the model tier**, where the publishers are universities and the grant is Apache-2.0 by
convention (4 of 4 new rows this pass). **Two different open-source economies in one industry:**
incumbent-opened infrastructure, and academy-published research weights whose *data* grant is usually
the binding one (**N17**).

## 🆕 New on 2026-11-21 (third pass, 13:40Z) — three trends, and the first one is about how this KB searches

### N16 — Five "zero-repo" gaps were partly artefacts of the word *automotive*

**The plant-floor quality-AI gap stood at `0 repos` for five consecutive passes.** It is not a gap.
`open-edge-platform/anomalib` is **Apache-2.0, 6,414★, 1,047 forks, pushed 2026-11-20** — mature,
maintained, permissive, and **it does not contain the word "automotive" anywhere in its pitch.** It
calls itself an industrial anomaly-detection library.

**The mechanism:** this KB's discovery legs are worded `{automotive} + AI + agent + github`. That phrasing
finds **vehicle-facing** software. It is structurally blind to **horizontal industrial software that the
automotive industry is the largest consumer of** — and plant-floor inspection, MES, PLM, logistics and
energy management are all of that shape.

**What to do with it, concretely:** for every remaining `0-repos` gap in this and the other eleven KBs,
**re-run the leg with the industry word removed and the capability word in its place** before recording
the gap again. "Zero open supply" is a strong claim and this pass shows the query can manufacture it.

**What it does *not* overturn:** the **LATAM-origin** gap (zero LATAM-authored automotive repos across
11 queries, 5 passes) is a claim about **authorship**, not vocabulary, and it survives. **But its
significance collapses** — see N18.

### N17 — The dataset licence is a second, independent axis, and byte-reading `LICENSE` cannot see it

This KB's licence discipline is byte-reading the grant file. **That discipline is blind by construction
to the licence of the data the model was fitted to**, and for an AI repo the data grant is usually the
binding one.

**The specimen:** `anomalib` is **Apache-2.0**. **MVTec AD** — the benchmark that essentially every
industrial-anomaly-detection paper, tutorial and README reports against — is **CC BY-NC-SA 4.0,
non-commercial.**

| Action | Code grant (Apache-2.0) | Data grant (CC BY-NC-SA 4.0) | Verdict |
|---|---|---|---|
| Use the library in a client deliverable | ✅ | n/a | ✅ Fine |
| Train on the **client's own** line images | ✅ | n/a | ✅ **The clean path** |
| Ship **MVTec-trained weights** to a paying client | ✅ | 🔴 commercial use of NC data | 🔴 **Blocked** |
| Quote an **MVTec benchmark number** in a proposal | ✅ | 🔴 | 🔴 **Blocked — and this is the form the mistake actually takes**, because the benchmark table is the first thing a proposal copies |

**Generalises past automotive:** every weights-shipping or benchmark-quoting engagement in every KB in
this fleet has this exposure, and **no SPDX field, and no `LICENSE` byte-read, will ever surface it.**
The diligence step is new: **enumerate the datasets, not just the repos.** Folded into `P13`/`P19`.

**The corollary found the same pass, and it inverts a standing reading:** `NOASSERTION` is often
**caused by** a dataset attribution. `MayankGangwal-code/ev-battery-soc-estimation` carries verbatim MIT
text plus an appended *"derived from 'LG 18650HG2 Li-ion Battery Data' … Mendeley Data,
doi:10.17632/cp3473x7xv.3, **licensed CC BY 4.0**"* — and that appendix is the entire reason GitHub's
near-exact-match classifier reports `NOASSERTION`. `PythonRobotics` (30,951★) is the same mechanism with
a contributors URL. **So `NOASSERTION` tracks conscientious authorship, not risk** — the careless repos
here have **no licence file at all** and measure `NONE`. Upgrade the standing rule from *"`NOASSERTION`
is a pointer"* to **"`NOASSERTION` is frequently a pointer to the dataset grant — the one axis the
`LICENSE` file cannot express."**

### N18 — A mandate with no viable open supply is a stronger sales position than a healthy commons

Two gaps were re-measured this pass rather than restated, and the contrast between them is the trend.

- **DMS (driver monitoring): mandated, supply-free.** Driver-attention monitoring is **regulatorily
  required** in the EU. The **only** framework-grade open implementation three legs could find —
  `kiralygomba/nottired_guard`, head-pose + gaze + blink + yawn with a peer-reviewed preprint behind it —
  is **GPL-3.0, 1★, unpushed since 2024-03-08.** Everything else is a single-file eye-aspect-ratio demo
  at 0–3★. **Required capability, zero adoptable open base.**
- **Plant-floor inspection: unmandated, supply-rich.** One Apache-2.0 anchor at 6,414★ that a client can
  download without us.

**Everywhere else this KB recommends "adopt the open base." DMS is the one place where the honest
recommendation is build** — and it is the only recommendation on the shelf that a client **cannot**
execute by cloning a repo. **An absence of open supply, when paired with a mandate, is the most
defensible engagement in a catalogue.** It argues for recording gaps as *assets*, with the mandate and
the measured supply failure attached, instead of filing them as research debt.

**And the inverse case is now explicit too:** LATAM's zero-origin-repo gap (N16) looked like weakness for
five passes. The moment the engagement is plant-floor rather than AV, **region-neutral open supply makes
local authorship irrelevant** — the binding LATAM facts are **where the plants are and who signs for
them**, not who writes the code. **A supply gap only matters once you know which engagement it blocks.**

---

## 🆕 New on 2026-11-21 (second pass, verification 12:45Z) — three trends, and two of them invert standing assumptions

### N13 — The EU AI Act reaches vehicles through an ENUMERATED article list, which turns a deadline argument into a triage exercise

**This file and `intel/market.md` have spent three passes arguing about a date** (2 Aug 2026 vs 2 Aug 2028
vs 2027). **The date was the wrong question.** The mechanism now resolves to a named article, and the
article is an enumeration:

- An AI system that is a **safety component of a type-approved vehicle** is a product under **AI Act
  Annex I, Section B**, which lists **Regulation (EU) 2018/858** (type approval) and **Regulation (EU)
  2019/2144** (general safety, incl. ADAS).
- For those systems, **Article 2(2) applies only Article 6(1), Articles 102–109 and Article 112
  directly**, and **there is no separate AI Act conformity assessment.** The substantive requirements
  arrive instead **via Article 109's amendments to Reg. 2019/2144**, then through **delegated and
  implementing acts under the amended Reg. 2018/858**.
- **But numerous automotive AI systems do not fall under those sector-specific regimes at all** — and
  those take the **full AI Act on the general timeline**, with no Article 2(2) relief.

**The trend, stated as a trend: automotive AI compliance is bifurcating, and the boundary is type
approval.** The same OEM will hold systems on both sides of it. **An enumerated list cuts scope in the
client's favour** — the identical shape as the enumerated high-risk list recorded in the education KB,
and argued **from the text of Art. 2(2)** rather than from a contested date.

**Why it matters commercially:** the deliverable is **the inventory and the boundary**, not a deadline
memo. See `compose/patterns.md` **P20**. It is also **robust to the date conflict**, because each column's
date follows from which column a system lands in — so the work can be sold and delivered while the
Digital Omnibus timing is still disputed.

⚠️ **All secondary.** Sources explicitly disagree on direct-vs-indirect application, and
**`eur-lex.europa.eu` is DNS-dead from this environment for the 6th consecutive pass.** Verify
**Annex I, Art. 2(2) and Art. 109** against the Official Journal before client use. Corroboration
improved this pass: **Taylor Wessing** (incl. a June 2026 automotive-specific Digital Omnibus Q&A) and
**Squire Patton Boggs** both describe the framework, and political agreement in trilogue is reported for
**7 May 2026**.

### N14 — Stop quoting market size for this industry; quote announced investment and adoption rate instead

**This KB has recorded an irreconcilable market-size spread for five passes** — 2026 automotive-AI
estimates of **US$5.8B / 6.52B / 9.13B / 27.33B**, a 4× range, because the vendors are measuring
different things. **Five passes of further searching has not narrowed it and will not.** The trend worth
recording is that **a better class of number exists and this file was not using it:**

| Class of figure | Example | Why it is more defensible |
|---|---|---|
| ❌ **Market size** | "automotive AI is US$X B in 2026" | A vendor **model** over a self-chosen definition. 4× spread. |
| ✅ **Announced investment** | **>US$80B across 2021–2025, plus ~US$30B in early 2026 alone** (PwC) | **Disclosed capital**, tallied from company announcements rather than modelled. |
| ✅ **Adoption rate** | **47% of companies today → 72% by 2030** (PwC, 2026 Global Automotive Outlook) | A **rate**, so definitional disagreement about market boundaries cancels out. |

**And the single most useful sentence found this pass is about where the money sits, not how much there
is: PwC reports OEMs deploy approximately 75% of automotive AI capital, with suppliers mainly *enabling*
that OEM work.** If three quarters of the capital is OEM-side, **a supplier-first pipeline is competing
for the remaining quarter.** The supplier opportunity is real but it is **an enablement sale** — tooling,
compliance evidence, integration for an OEM programme — **not a platform sale.** That should change which
door a studio knocks on and what it carries through it.

**Secondary signal:** multiple 2026 sources report the CES 2026 vocabulary moving from *"software-defined
vehicle"* to **"AI-defined vehicle"**. Positioning language rather than a technical category — but it is
the buyer's current language.

### N15 — LATAM has its first positive automotive-AI regulatory fact, and it is not in Brazil

**Five passes of this KB recorded LATAM as a regulatory blank** — bills pending, nothing in force, zero
origin repos. **That is now wrong in a specific and useful way.**

**Colombia already regulates the circulation of automated driving systems up to SAE Level 3** (CMS,
*Automotive Outlook 2026*, "Liability and the regulation for autonomous driving in Latin America").
Meanwhile **Brazil has the legislative debate and no operating rule** — Bill 2,338/2023 would classify
AVs as **high-risk AI systems** with **risk-management, transparency, cybersecurity and human-supervision**
duties, but it is still awaiting a rapporteur's opinion.

**The inversion, and it should change where a LATAM AV engagement starts:**

| | Operating rule for ADS | AI/AV legislation |
|---|---|---|
| **Colombia** | ✅ **regulated up to SAE L3** | 🔴 none; **not** debating one federally |
| **Brazil** | 🔴 none found | ⏳ Bill 2,338/2023 pending, AVs = high-risk |

**Deployment and homologation work points to Colombia, because something is already permitted there.
Governance and risk-framework work points to Brazil, because the draft names its own four work packages.**
This KB — like most LATAM practice — defaulted to Brazil-first for both. **A regime with no AI law but a
live ADS permission is an opportunity, not a constraint.**

⚠️ **CMS names no Colombian decree or resolution, the piece dates to ~March 2026, and no primary
Colombian source was reachable.** Good enough to open a conversation; **not** good enough for a compliance
memo. **Naming that instrument is now the highest-value LATAM verification task in this KB.**
Regional frame (Baker McKenzie): **no Latin American country has a fully mature, harmonised AI regime
across all sectors**; CMS adds that **Colombia, Peru and Mexico are not discussing federal bills**, while
**Brazil and Chile** are the two where technology and regulation are both advancing.

---


## 🆕 New on 2026-11-21 — three trends, and the first one is about the ground this KB stands on

### N10 — Capability attributed to a blocked channel was never blocked: `github.com` is 403, `raw.githubusercontent.com` is 200

For four consecutive passes (2026-10-26 → 2026-11-19) every file in this base carried a version of
*"`curl` to `github.com` and `api.github.com` returns HTTP 403, therefore licences and liveness must be
inferred from rendered pages."* The 403 was real and re-tested each time. **The conclusion was still
wrong**, because only one host was ever re-tested. Tested this pass:

| Channel | Result | Settles |
|---|---|---|
| `git ls-remote --heads https://github.com/<o>/<r>` | ✅ works | Existence/liveness — 40-hex SHA vs credential prompt. No API quota. |
| `curl https://raw.githubusercontent.com/<o>/<r>/<br>/LICENSE` | ✅ **200** | The grant, byte for byte |
| `gh api -X GET search/repositories -f q='repo:<o>/<r>'` | ✅ works | Stars, forks, `pushed_at`, `archived`, SPDX |
| `gh api repos/<o>/<r>` | 🔴 403 | Per-repo REST — scoped to the session's own repos. Use **search** instead. |
| `github.com`, `api.github.com` | 🔴 403 | Host policy. Not retryable. |

**The trend, stated generally because it is not about GitHub:** in an agent-run knowledge pipeline, a
*recorded* limitation propagates faster and lives longer than the condition that produced it. Each pass
inherited the sentence, re-tested the one host named in it, confirmed the 403, and copied it forward —
while a sibling host on the same domain answered 200 the whole time. **The costly error was not the
403; it was that the workaround became a documented property of the environment.** Operational rule now
recorded in every file's header: **when a host refuses, enumerate its siblings before writing down that
the capability is unavailable.**

This is the second base in this KB family to find that its *method*, not its data, was the defect — the
`education` base reached the same conclusion on 2026-11-21 from the opposite direction (a line-keyed
audit that had desynced). **Both corrections were found by re-deriving the measurement, not by searching
for more repos.**

### N11 — The licence-defect rate runs in both directions, and the curated shelf now wins against automation

`T5`/`N5` recorded that secondary sources misstate licences often enough to be a service line. This pass
inverts the test: an **automated classifier was run against this base's own 152 byte-read LICENSE files**,
and where it disagreed with the published cells — **8 repositories — the published cells were right every
time.**

The cause is a single structural property of licence texts, and it is permanent:

> **Every GNU-family, MPL and EPL licence names *other* licences inside its own body.** MPL-2.0 §1.12
> defines "Secondary License" as GPL/LGPL/**AGPL**. GPL-3.0 §13 references the **AGPL**. LGPL-3.0
> appends the entire GPL text. EPL-2.0 names **GPL-2.0** as a Secondary License. Apache-2.0 §4 permits
> "additional or different license terms."

So substring matching produces MPL-2.0 → AGPL (COVESA VSS, esmini), LGPL-3.0 → AGPL (**Odoo**),
GPL-3.0 → AGPL (Dolibarr, OpenAutoCore), EPL-2.0 → GPL-2.0 (SUMO, Huly). The sharpest case is
`openremote/openremote`: its `LICENSE` is **172,870 bytes** because it bundles a dependency-licence
listing containing the full Apache text, while the project's own grant — **AGPL-3.0** — is in the first
paragraph.

**The trend that matters for how these bases are maintained:** as the shelves get older and the tooling
gets cheaper, the temptation to "refresh" a curated cell with an automated read grows. **This pass is
evidence that the refresh is often the regression.** Two rows in this base carry grants stated only in a
README or source header (`TrampolineRTOS/trampoline` GPL-2.0, `navariltd/Fleet-Management-System`
GPL-3.0); a LICENSE-file-only probe downgrades both to "no licence" and calls it an update. **Automation
should propose diffs against a curated cell, never overwrite it.**

Corollary finding, same mechanism: **`license.spdx_id` is not a grant.** It returns `NOASSERTION` for
`AtsushiSakai/PythonRobotics` (30,954★, plainly **MIT**), for `autoas/as` (**GPL-3.0 OR Commercial**,
a dual licence the field cannot express), for `openremote/fleet-management` (**AGPL-3.0**), and for
`waymo-research/waymo-open-dataset` (**Apache-2.0 except a named carve-out directory**). A carve-out is
actionable; `NOASSERTION` is noise.

### N12 — The automotive open-source commons has split: frozen research, live infrastructure

Measured first-hand this pass across the canonical perception repos the `autonomous-driving` topic
surfaces (★2.2k–4.7k): **7 of 9 have not been pushed in over a year, and 1 is formally archived.**
BEVFormer last pushed **2024-08-15**; SensorsCalibration **2024-06-17**; YOLOP **2023-10-20**;
awesome-robotic-tooling **2023-11-20**; 3D-PointCloud **2024-08-30** (and carries **no licence at all**);
microsoft/AutonomousDrivingCookbook **archived**.

Against that, the infrastructure layer is pushing continuously: **CARLA 2026-11-21, Autoware 2026-11-20,
PythonRobotics 2026-11-16, autoas/as 2026-11-18, iDempiere 2026-11-20, COVESA/vss-tools 2026-11-17.**

**The trend is a build-vs-adopt rule, not a lament.** The academic perception commons did its job and
stopped moving, because the capability frontier moved to **end-to-end/VLA models and productised stacks**
(`NVlabs/alpamayo*`, `Qwen-Drive-1.0`, `hustvl/Senna`, Autoware, Apollo). For an engagement:
**take algorithms and calibration mathematics from the frozen layer — that knowledge does not rot — and
take every runnable component from the live layer.** Proposing a 2024-dormant perception repo as a 2026
production base is the specific mistake this trend exists to prevent.

**One liveness caveat this pass had to correct in its own base:** a *hosted service* shutting down is not
a *project* dying. Huly (`hcengineering/platform`, 28,161★, EPL-2.0) was recorded here as "frozen"; the
notice is that the **hosted service** is discontinued for lack of hosting funding, while the repository
was **pushed 2026-11-09**, is **`archived: false`**, and its recent commits are real fixes. **Check
`pushed_at` and `archived` before converting a service notice into a project obituary.**

---

## 🆕 New on 2026-11-19 — four trends, and the first one corrects a claim this file has made three times

### N6 — The automotive agent layer is 2,907★, and it lives in the engineering office, not the vehicle

**Supersedes:** the "0–8★", then "0–26★" ceiling recorded in **N2** (2026-10-31) and carried forward on
2026-11-13. Those numbers were correctly counted and wrongly scoped.

[`jherrodthomas/automotive-skills-suite`](https://github.com/jherrodthomas/automotive-skills-suite) —
**MIT, 2,907★, 141 forks** — is 76 builder+reviewer agent-skill pairs that emit the **ISO 26262 /
ISO/SAE 21434 / ISO 21448 SOTIF / Automotive SPICE / AIAG-VDA (APQP, DFMEA, PFMEA, control plans, PPAP)**
artefact pack as `.xlsx`, plus CAN/LIN/FlexRay/Ethernet and K-Matrix work, UDS/ODX/DEM diagnostics,
AUTOSAR Classic and Adaptive, A2L/DCM calibration, MBSE/SysML and V&V traceability matrices.

**Why every prior pass missed it:** the searches were all shaped like the *vehicle* — "in-car agent",
"diagnostics MCP", "driving policy". The query that finds it is shaped like the *standard*:

```
AUTOSAR OR ISO26262 OR "ISO 21434" in:name,description,readme pushed:>2026-08-01 stars:>15
```

**Method change for every future pass of this KB: search the standard, not only the protocol, and never
the buzzword.** The same query also returned `iDoka/awesome-canbus` (CC0, 3,571★),
`ebroecker/canmatrix` (BSD-2, 1,093★), `eclipse-iceoryx/iceoryx` (Apache-2.0, 2,212★) and `autoas/as`
(965★) — four more repos above 900★ that five previous passes never surfaced.

**The commercial reading:** the open automotive agent value is in the **artefact pack a programme
ships**, not in the car. That is consultable, reviewable, billable work with no vehicle access required
— and it is the same deliverable in all four regions (see **N9**).

⚠️ **And the risk, stated once:** the repository page carries **no "not certified" disclaimer** and no
requirement that a qualified engineer validate outputs, while advertising coverage of six standards and
the word "compliance". A generated safety case is a **draft with a named owner**, or it is a liability.

### N7 — "Assurance-as-code" became a category in six weeks, and the honest one is the small one

Three independent MIT projects, none older than 2026-05-01:

| Project | ★ | Epistemic posture |
|---|--:|---|
| `jherrodthomas/automotive-skills-suite` | 2,907★ | Advertises coverage of six standards. **No disclaimer.** |
| `jherrodthomas/LionDriver` | 65★ | **Publishes 42 unresolved defeaters against its own safety case** and states no compliance is claimed because no assessment was performed |
| `Lieubk/automotive-safety-security-assurance-kit` | 2★ | *"The toolkit drafts and checks; people decide"* — created **2026-11-19** |

**LionDriver is the template; the skills suite is the tool.** LionDriver ships a living safety case of
**36 claims and 50 evidence items with 0 accepted and 42 open defeaters**, **89 V-cycle work products
(85 draft, 4 skeleton)**, citations to ISO 26262 / ISO 21448 / ISO/SAE 21434 / **ISO/PAS 8800** /
**UL 4600** / Automotive SPICE, a statement that no release build exists and that development builds
must not be used on public roads outside a controlled test regime, a named first *evaluated*
configuration (**Toyota Corolla E210**) with **no configuration yet assurance-supported**, automated
checks of inherited openpilot safety code running in CI but **not yet reviewed as evidence**, and a
field-monitoring process whose first live case is tied to **NHTSA PE26007**.

**The trend is not that the tooling exists. It is that publishing your own open defeaters has become a
credibility move.** Expect clients to start asking for the defeater list, and expect the vendors who
cannot produce one to lose on that question. Globant should arrive with one.

**Two data points is coincidence; three in six weeks is a category.** Watch for a fourth.

### N8 — Agents now actuate real vehicles, and the safety envelope — not the model — is the published artefact

[`aditya-ramabadran/drivingbench_harness_code`](https://github.com/aditya-ramabadran/drivingbench_harness_code)
— **MIT, 63★** — closes the gap recorded in earlier passes ("no benchmark where an LLM agent actually
controls a vehicle"). An MCP server named `drivingbench_sandbox` exposes exactly three tools —
`observe()`, `set_motion()`, `stop_now()` — and **chat models (Codex, Claude Code, Cursor), API models
(OpenRouter, Gemini) and trained VLA policies served over HTTP all drive the same course through the
same interface.** Real platforms: **comma four** on pinned openpilot `59fcd340`, **Toyota TSS2**,
**Tesla Model 3 HW3**. The simulator is the course as a **Gaussian splat** running the real control
stack, scored identically to the car.

**The three design decisions worth copying into any Globant vehicle-agent architecture:**
1. **The `reason` string is logged for the operator and never sent to the controller.** Prompt text
   cannot become actuation. This is the cleanest statement of the agent/actuator boundary found in this
   KB.
2. **`observe()` returns image age.** Staleness is an input, not an assumption.
3. **Layered limits:** operator-set ceiling (default **3 m/s**), **hard cutoff at 6 m/s**, command
   expiry, and cancellation on brake / gas / steering override / disengagement. Four independent
   stoppers, not one.

⚠️ **No scores and no leaderboard are published; Releases is empty.** So **N8 is a feasibility trend,
not a capability trend.** Do not quote a DrivingBench result; `drivingbench.com` was not fetched this
pass.

**Corollary, and it is the one with budget attached:** this is the shape of the *evaluation harness*
that every ADAS client will need once a safety case is a regulatory deliverable (**see N9**). The
harness is more sellable than the model.

### N9 — One artefact factory, four regional buyers: regulation diverged in form and converged in output

For five passes this file treated regional regulation as four separate compliance stories. 2026 ended
that. **UNECE WP.29's approval of the ADS Global Technical Regulation (22–26 June 2026, all contracting
parties, co-developed by China, the EU, the UK, the US, Canada and Japan)** means the *technical target*
is now shared, while **authorisation stays national**. Layer that over what each region is actually
buying:

| Region | The instrument that pays for it | The deliverable |
|---|---|---|
| **North America** | **15 of the 2026 NHTSA/FMCSA rulemakings are AV-focused**; SELF DRIVE Act 2026 (H.R. 7390) reported to require a **safety case for SAE L3–L5**; NHTSA **EA26002** (~3.2M vehicles) shows enforcement is live; Zoox's first-ever FMVSS robotaxi exemption shows the exemption path works | Safety case + **field-monitoring evidence** |
| **EMEA** | EU AI Act (timeline contested), absorbed through **UNECE type-approval**; OEMs with **UNECE R151** docs must add **bias testing and AI Act risk-management language** | The **delta** on top of existing type-approval |
| **APAC** | The GTR China co-led, **plus stricter domestic rules**: public-beta ban, marketing-terminology limits, **heavily regulated OTA**; **Japan requires remote monitoring for all L4**; **Korea has issued accident-decision ethics guidelines** | Release-engineering evidence, OTA governance, remote-ops software, an **ethics rationale document** |
| **LATAM** | **Nothing mandates it.** Binding constraints are **LGPD** and **USMCA (review July 2026)** | **Export-readiness** for suppliers shipping into the other three regions |

**The trend: the artefact is the same in all four; only the buyer's reason differs.** That makes the
assurance factory of **N6/N7** a single reusable asset rather than four regional builds — and it makes
**LATAM sellable on a compliance story even though LATAM has no compliance mandate**, because the
Bajío's customers are in North America.

⚠️ **Source discipline:** every regulatory date above is from a law-firm briefing, a compliance-vendor
page or a trade outlet. **No primary register was fetched this pass.** Confirm once before any client
deck. The EU AI Act timeline specifically remains **three-way contested** (2 Aug 2026 / Annex III to
2 Dec 2027 via Regulation (EU) 2026/1744 / Omnibus adopted June 2026) — six days after this file first
recorded the conflict, it has not resolved.

### 🆕 Three smaller movements worth recording

- **The research tier became licence-safe by convention.** Of the 14 new driving-policy / world-model
  rows admitted this pass, **11 are Apache-2.0**, 1 is MIT, 2 have none. Two passes ago the no-licence
  rate in this tier was the single largest obstacle to using it. It is now the exception. **This
  materially lowers the cost of a model-selection engagement** (**P9**).
- **openpilot is unbundling from comma's hardware.** `zoompilot/jetlink` (MIT) runs openpilot's large
  driving model on **Jetson Orin Nano, macOS, iOS, Android and CUDA laptops** with only a comma device
  and a USB3 cable — and carries **40 forks on 57 stars**, a build signal rather than a bookmark
  signal. With `YassineYousfi/openpilot.distill` (MIT) and `Sherin-SEF-AI/Lyne-ADAS` (MIT, on-device
  Android ADAS), "can a real driving model run on the client's compute?" has become an integration
  question. **This is the supply-side mirror of the Mercedes × Liquid AI on-device programme** — the
  direction of travel in both the OEM tier and the open tier is **small, local, no cloud fallback**.
- **The vehicle-data MCP convention is now in the code, not just the README.** `wtfault-scanner`
  (*"never makes anything up"*, every number clickable to raw bytes) and `CanLab` (**injection is
  bench-only and stays disarmed until armed**) are the reference implementations. `cobanov/teslamate-mcp`
  (MIT, **142★**) is now the category leader at 5× the previous high. **T8** (every credible automotive
  agent has a human gate) is confirmed from the supply side.

### 🔴 Gaps opened or closed on 2026-11-19

**Closed:**
- *"No benchmark where an agent actually actuates a vehicle"* → **closed** by DrivingBench (**N8**),
  with the caveat that no scores are published.
- *"The automotive agent category has no large repo"* → **closed, and the earlier claim corrected**
  (**N6**).
- *"No open SysML v2 automotive systems-engineering base"* → **closed** by `de4sdv/DE4SDV`
  (Apache-2.0).

**Still open, re-measured this pass with the query stated:**
- **EV charging / battery AI:** `EV battery charging AI … stars:>15 pushed:>2026-08-01` → **0 repos.**
- **Plant-floor quality / inspection AI:** `… stars:>3 pushed:>2026-06-01` → **0 repos.** The nearest
  asset is `aws-samples/sample-manufacturing-automotive-ai-toolkit` (**MIT-0**, 19★) — samples, not a
  platform.
- **Fleet telematics:** **2 repos** above 5★ in the last quarter. Fifth pass.
- **DMS:** 408 repos, **top star count 5**, nearly all unlicensed. Fifth pass. Now a measured finding.
- **LATAM-origin supply:** **zero** across eleven queries. Fifth consecutive snapshot.
- **Model weight licences:** `huggingface.co` unreachable from this session. **None verified
  first-hand**, this pass or any previous pass.

**Newly opened:**
- **Primary-register verification is now the binding constraint on this file's regulatory content, not
  search coverage.** Three incompatible AI Act timelines have survived two passes. The next pass should
  spend its budget on one primary source (Official Journal for Regulation (EU) 2026/1744) rather than
  on more secondary reading.
- **Licence-unclassified high-star repos are accumulating:** `AtsushiSakai/PythonRobotics` (**30,951★**,
  `NOASSERTION`), `autoas/as` (965★, the only substantial open AUTOSAR BSW), `autowarefoundation/AWSIM`
  (765★, confirmed **bespoke licence**, *not* Apache-2.0), `openremote/fleet-management` (51★,
  unclassified for five passes). **A licence-resolution pass on these four would unblock more
  engagement surface than any new search.**

## 🆕 New on 2026-11-13 — three trends, and the first one supersedes a standing conclusion

### N3 — Open automotive AI crossed from "research models" to "a shippable product stack"

**The evidence.** In three days (10–12 Nov 2026) the Autoware Foundation published
[`vision_pilot`](https://github.com/autowarefoundation/vision_pilot) — **Apache-2.0, 927★, 196 forks,
4,282 commits** — described in its own README as *"a productionizable and safety certifiable
implementation of an open-source L2 ADAS system."* It ships **ACC, FCW, AEB, LKAS, LDW, ISA and
single-lane hands-free highway Autopilot**, **mapless**, from **a single 1–2 MP monocular camera** on
**ONNX Runtime, GPU or CPU**. Around it: `agnocast` (zero-copy ROS 2 IPC, 212★, 1,258 commits),
`autoware-safety-island` (ARM SoC, 608 commits), `scene_3d` and `ego_lanes` (perception),
`autoware.trucks` (freight charter), `alpamayo-autoware` (foundation-owned Alpamayo fork).

**What it supersedes.** Four passes of this KB concluded that *"the buildable open assets in automotive are
driving policies and SDV infrastructure"* — i.e. **research models and middleware, with the product layer
closed.** That conclusion is now obsolete at the L2 tier. There is an open product layer.

**Why it is a trend and not a release.** Three signals distinguish them: a **feature list expressed in
regulatory vocabulary** (AEB, ISA, LDW are homologation terms, not research terms); a **certification
roadmap** naming **ISO 26262 and ISO 8800**; and **silicon board support** (`openadkit-rcar-x5h`, Renesas
R-Car X5H). Research projects do not publish board support for mainstream automotive SoCs.

**Implication for an engagement.** The answer to *"can we build ADAS on open source?"* changes from "only
the research scaffolding" to "there is a stack with the features, and the gap is integration,
homologation evidence and your sensor set." ⚠️ **"Certifiable" is aspiration, not status** — and the
current input is one narrow-FOV camera with no radar until the roadmap lands. Pitch an **L2 base**, never
an L3 shortcut.

### N4 — The open automotive AI supply chain is APAC-led, which reframes every region's engagement

Every pass of this KB has placed **APAC as the largest automotive AI market**. This pass places it as the
**producer of the open supply**: the entire release wave above comes from the **Autoware Foundation**,
anchored by **TIER IV (Japan)**; **Qwen-Drive-1.0** is Alibaba's; **Senna (IJCV 2026)** is HUST's. Against
that, NVIDIA's Alpamayo line is now **forked into the foundation** (`alpamayo-autoware`) rather than
consumed from the vendor.

**Why Japan specifically.** Three things coincide: a **light-touch domestic regime** (the AI Promotion Act,
in force since June 2025, is a framework law **with no penalties**), a national industrial strength in
**safety-critical engineering and Tier-1 integration**, and a vendor-neutral foundation with OEM
membership. `autoware-safety-island` plus an ISO 26262/8800 roadmap is that combination expressed as code.

**Implication.** Upstream partnership and contribution strategy belongs in APAC **regardless of where the
client sits**. A North American or EMEA ADAS engagement now has an APAC dependency in its supply chain —
which is a governance fact to put in front of a client before they discover it, and an argument for
contributing upstream rather than forking privately.

### N5 — The licence-defect rate in this industry is high enough to be a service line, and it fails in both directions

This pass probed 19 repositories and **six carried a licence defect** — roughly a third:

| Defect | Specimen | Shape |
|---|---|---|
| **No licence at all, inside a major foundation** | `autoware_latent_drive` (42★) | No field, no README statement, `LICENSE`/`.md`/`.txt`/`license.rst` **all 404** |
| **README claims MIT, no file** | `petrpatek/obd2-mcp-server` (12★) | Third instance of this exact defect in this KB |
| **No licence + gated on proprietary software** | `tars-car-mcp` (0★) | Needs the closed TARS desktop app |
| **Secondary source claims MIT; repo is AGPL-3.0** | `idurar/idurar-erp-crm` (9.0k★) | Strong copyleft presented as permissive |
| **Secondary source claims Apache-2.0; repo is EPL-2.0 *and frozen*** | Huly / `hcengineering/platform` (28.1k★) | Wrong licence **and** abandoned |
| **MIT badge with an undisclosed commercial carve-out** | `open-mercato` (1.9k★) | `packages/enterprise` is not MIT |

**And the inverse defect, which is new and just as expensive.**
[`autoware-safety-island`](https://github.com/autowarefoundation/autoware-safety-island) shows as
**"Other"** in GitHub's org listing purely because its licence file is named **`license.rst`**. Read raw,
it is **verbatim Apache-2.0**. A pipeline that trusts the label **silently discards** a usable, 608-commit
safety repository — and silent loss is harder to catch than a false positive, because nothing looks wrong.

**The operational rule this hardens into:** *fetch the file; the README is not a grant, the search summary
is not a grant, the org's reputation is not a grant, and GitHub's label is not a verdict in either
direction.* **Of four ERP/CRM licence claims probed this pass, exactly one held as stated.**

**Commercially:** three of four ERP/CRM bases and one in three repos overall carrying a licence defect is
not a curiosity, it is a diligence service a client can verify and a reason to be the firm that reads
licences.

---

## 🆕 New on 2026-10-31 — two trends that sit above the numbered list below

The numbered T0–T8 sections that follow are kept as written on 2026-10-26 and are **not renumbered**, so
the record stays comparable pass to pass. These two are new.

### N1 — The open end-to-end driving model became a three-supplier commodity, and NVIDIA is no longer top of the table

For three passes this KB has described **one** open AV reference line: NVIDIA's Alpamayo. As of this pass
there are **three independent Apache-2.0 suppliers**, and on the only published multi-model comparison the
NVIDIA model is **third**:

| Model | Supplier | Params | Licence | ★ | ADE @ 3 s | FDE @ 3 s |
|---|---|---|---|--:|--:|--:|
| **Qwen Drive 1.0** | Alibaba | 4B | Apache-2.0 | 537 | **0.565 m** | **1.397 m** |
| **AutoE2E v1.0** | Autoware Foundation | **79.9M** | Apache-2.0 | 184 | 0.744 m | 1.980 m |
| **Alpamayo 1.5** | NVIDIA | 10B | Apache-2.0 code · **OpenMDW-1.1 weights** | 370 | behind AutoE2E | — |

Source: AutoE2E's own README, read 2026-10-31, on **KITScenes-Multimodal** validation, open-loop, 3 s
horizon, eight open-weights models compared (SimForge and METEOR also behind AutoE2E).

🔴 **It is not a clean ranking and must not be sold as one.** The README states that **inputs differ by
model** — AutoE2E itself receives an HD map and the route — and the Qwen Drive row uses a **different
evaluation setting** (first-of-6-trajectories checkpoint, 202 keyframes). What it *is*: the **first
vendor-neutral multi-model comparison in open AV**, published by a foundation that sells no model, and
**reproducible** (issue **#210** coordinates the community benchmark; PRs **#220** and **#229** added the
Qwen Drive and Alpamayo evaluation scripts).

**Three commercial reads:**
1. **Parameter count is not the axis.** AutoE2E beats a 10B model with **79.9M parameters** and runs at
   **~76 FPS on an RTX 5080** (project figure). For a client who must ship on automotive silicon rather
   than a datacentre GPU, that is the more important number than any benchmark row.
2. **Vendor neutrality is now purchasable.** An OEM that does not want to look captured by NVIDIA has a
   foundation-governed option with the same licence. Expect this to come up in procurement before it comes
   up in engineering.
3. **"Model-agnostic" stops being a slide and becomes a deliverable.** With three free suppliers whose
   relative quality is contested, the defensible architecture puts the policy behind an interface and
   swaps it — which is what the revised P6 and the new P9 below do.

### N2 — The automotive agent layer finally appeared, as MCP servers, at 0–8 stars

Three passes recorded *"no permissively-licensed automotive AI agents exist."* That is **no longer true**,
and the correction has to carry its own scale: `Vehicle-Diagnostic-Assistant` (MIT, **8★**), `obd2-mcp`
(MIT, **2★**), `automotive-ai-skills` (MIT), `j2534-mcp-server` (**0★**, and **no LICENSE file**),
`carvector-mcp` (MIT client, **1★**, keyed proprietary API). The one real-traction project in the space is
a **protocol, not an agent**: **Auto Agent Protocol** (Apache-2.0, **110★**, v3.1).

**The signal is the convergence, not the stars.** Every project is an **MCP server**. The physical layer
has settled: **ELM327/OBD-II** for consumer-grade access, **J2534 PassThru** for professional-grade
(UDS, KWP2000, DTC lookup, PID decoding). Independently, two of these projects arrived at the **human
approval gate before any vehicle action** that this KB has recommended since July.

**Why this is the favourable shape of a market for a services firm:** the integration contracts are
standardised and free, and **the differentiated product does not exist yet**. Compare the LMS-agent cluster
in the education KB — same MCP-first shape, same small star counts, same conclusion. 🟡 **Caveat worth
stating internally:** a 0–8★ category is a *watch* item. It justifies a demo and a point of view; it does
not yet justify a practice. Re-measure next pass — these numbers are the baseline.

## T0 — The open SDV *core* arrived (recorded 2026-10-26)

The previous pass tracked the SDV **data layer** (VSS, Kuksa, Ankaios) and missed the **platform core**.
**Eclipse S-CORE** (*Safe Open Vehicle Core*, Apache-2.0) is the first open-source-based SDV platform
designed against **ASIL-B** functional-safety requirements — a design target, not a certification, and that
distinction belongs in any client conversation.

Why it is credible rather than aspirational:
- **It ships.** Ten releases are listed on its GitHub releases page, latest **`v0.7.3` on 07 Oct 2026**,
  roughly monthly since `v0.5.5` in April.
- **Dual-language, safety-grade.** `0.6.0` introduced full **C++ and Rust** support including the
  **Ferrocene** safety-critical Rust toolchain, plus Baselibs Rust and Lifecycle & Health Management.
- **The OEM bloc is behind it.** The Eclipse SDV ↔ **VDA** memorandum expanded to **32 companies**
  (Jan 2026); **Hyundai Mobis joined the SDV Working Group** (May 2026).
- **It has a commercial escape hatch.** Founding member **Qorix** sells a commercial middleware
  distribution built on S-CORE — which removes the "unsupported open source" procurement objection.
- **Its process is a repository.** `eclipse-score/process_description` publishes the development process
  itself; for a safety argument that artefact is worth as much as the code.

⚠️ **Do not quote a 1.0 date.** The Eclipse project page lists **v1.0.0 at 2026-12-14**, the Eclipse
newsroom says a full release is planned for 2026 targeting vehicle programmes reaching market by 2030, and
an ETAS presentation says a complete solution is on track for **2028**. Three sources, three horizons.
Separately, trade press dates 0.6.0 to Feb 2026 and 0.7.0 to May 2026 while **the GitHub releases page
says 26 Jun and 24 Aug** — prefer the releases page.

**Commercial read:** 111 stars on the platform a VDA-backed, 32-company bloc is standardising on. The
mindshare gap between the repository's visibility and its industrial weight is the clearest arbitrage in
this KB.

## T1 — A global AV regulation now sits above the regional patchwork

🆕 **UNECE adopted the first global technical regulation for automated driving systems on 24 June 2026**,
reported as **UN GTR No. 26** with **UN Regulation No. 185**, endorsed by Canada, China, the EU, Japan, the
UK and the US; NHTSA voted in favour for the US in June 2026. China's forthcoming mandatory L3/L4 standard
is reported to reference it.

This changes the shape of multi-region compliance work: the regions are no longer purely divergent, so the
offering shifts from "translate between four regimes" toward "map one global baseline onto four national
implementations" — with the national deltas, not the baseline, as the billable surface.
⚠️ The GTR and regulation numbers come from secondary/vendor sources. **Confirm against UNECE publications
before putting them in a deliverable.**

## T2 — The open reference AV stack is vendor-published, Apache-2.0, and now 34B

**NVIDIA's Alpamayo family** remains the defining open AV model line. Verified state on 2026-10-26:
**Alpamayo 2 Super** (`NVlabs/alpamayo2`, Apache-2.0, 287★) is an open **34B** multi-task foundation model
— a 32B VLM backbone plus a 2B diffusion expert. **Alpamayo 1.5** (370★) remains the practical entry point
and the one the published recipes target. **Alpamayo 1 Nano** (2.1k★) now carries an explicit banner:
*"no longer under active development … limited maintenance updates."*

🔴 **Licence nuance the previous pass missed:** the Alpamayo 1.5 repository is Apache-2.0, **but its README
states the model weights are OpenMDW-1.1.** Code licence ≠ weight licence. Read OpenMDW-1.1 before
distributing fine-tuned derivatives.

🆕 **A second open VLA line now exists:** `DriveVLA/OpenDriveVLA` (Apache-2.0, 824★, **AAAI 2026**) with a
**0.5B checkpoint on Hugging Face**. That matters practically — Alpamayo 1 Nano alone wants ≥24 GB VRAM, so
a 0.5B open VLA is the realistic candidate for on-target experiments and for teaching.

**Why it matters commercially:** NVIDIA positions Alpamayo as a **teacher model, not in-car software**. The
weights are free; integration, distillation, quantization, validation and homologation are not. That is the
billable surface.

## T3 — Post-training, not pre-training, is where AV capability is won

**OpenDriveLab's WorldEngine** (Apache-2.0, 528★, stable checkpoints 2026/09/15) frames this directly:
imitation-learn a base policy, run open-loop rollouts over real logs to **automatically surface
failure-prone scenarios**, rebuild those scenes with **3D Gaussian Splatting**, refine with RL under a
shaped safety/efficiency/comfort reward. Project's own figures: post-training from a 50k-scene base gives
gains equivalent to **~14× more pre-training data**, simulated collision rate down up to **45.5%**, zero
disengagements over a 200 km on-road test — **not independently verified**.

Paired with **AlpaGym** (RL on AlpaSim), the closed-loop post-training pipeline is fully open-source. The
scarce input is no longer compute or architecture — it is **failure-case data and the pipeline to mine it**.
🆕 And NHTSA is now **explicitly assessing AI training and validation strategies** within ADS, which turns
that pipeline from an engineering nicety into a regulatory artefact.

## T4 — "Software-defined" is being restated as "AI-defined"

🆕 **At CES 2026, automakers emphasised AI rather than electrification** as EV demand softened (S&P
Global), positioning vehicles as software-defined rather than fixed hardware. Perforce's 2026 survey:
**71% implementing AI in their vehicles**, **57% currently working on SDV architectures**, **70%** using AI
for SDV optimisation (vendor survey — directional).

The open plumbing matured to match: **Kuksa Databroker** at 0.6.1 with a **Quarkslab security audit**
(82★), **Ankaios** at 125★, **COVESA VSS** at 451★ with 100+ companies around it, and 🆕 a **runnable
`eclipse-sdv-blueprints/fleet-management` reference** wiring Kuksa → FMS Forwarder → **Eclipse uProtocol**
→ InfluxDB → Grafana with an **rFMS API** server. Published topology, not an architecture slide.

**The signal to read:** these repos carry 7–451 stars. **Star count is a terrible proxy for importance in
this industry.**

## T5 — Compliance is the 2026 budget line in EMEA, and the calendar got denser

Dated obligations inside a 12-month window: **EDR mandatory 7 Jan 2026** · **ADDW mandatory 7 Jul 2026** ·
**EU AI Act general application 2 Aug 2026** · **UNECE R155/R156 for new types from 1 Jun 2026** (GB) ·
🆕 **UK Automated Vehicles (Permits for Automated Passenger Services) Regulations 2026 in force since
15 May 2026** · 🆕 **UN GTR No. 26 adopted 24 Jun 2026**.

**ISO/PAS 8800** (AI safety for road vehicles) complements ISO 26262 and ISO 21448/SOTIF without replacing
them; the AI Act adds governance on top — risk management, data quality, transparency, human oversight,
robustness, cybersecurity, post-market monitoring, with a technical file and serious-incident pipeline per
high-risk system, and it does not displace ISO/SAE 21434, UN R155 or UN R156.

⚠️ **The timeline is genuinely contested.** Safety-component AI (most ADAS/AD) appears to start **Aug
2027**, and one source cites **2 Dec 2027** for standalone Annex III systems via the Digital Omnibus —
unverified against the Official Journal. **Do not put a single date in a client deliverable.**

## T6 🆕 — APAC's rules became binding in 2026, not "coming"

Three state changes the previous pass had as future tense:
- **South Korea's AI Basic Act took effect 22 January 2026** (transparency for generative/high-impact AI,
  safety duties for frontier models, governance duties for high-impact systems in sensitive sectors;
  decree and ministry guidelines are **interpretive, not binding**).
- **China issued mandatory standards for combined driving assistance and automated driving** (reported
  July 2026), after an April 2026 analysis found no nationwide mandatory rule and **Beijing among
  municipalities pulling back** from unfettered autonomous operation. **L2 penetration is past 70% of new
  passenger vehicles** (MIIT). A mandatory **L3/L4 standard referencing the UN GTR from 1 Jul 2027** is
  reported — ⚠️ unverified.
- **India**: BNCAP incentivises camera ADAS and **BNCAP 2.0 is reported to require multiple ADAS features**
  for a high rating; Mobileye calls **2026–2027 the defining years for ADAS in India**.

Industry signals from the 2026 World Intelligent Connected Vehicles Conference: **BYD announced a 4nm
intelligent-driving chip in mass production** claimed to support L3/L4, and **XPeng's CEO said the company
would "skip L3"** — i.e. the region is not converging on a single autonomy ladder even as its regulation
centralises.

## T7 — Aftersales and warranty remains the commercial beachhead, and it is agentic

**43% of dealers** already deploy AI. The use cases are unglamorous and high-volume: warranty eligibility
checks, claim submission and validation against repair orders and OEM rules, parts substitution, fraud and
anomaly detection on claim patterns, service scheduling. Vendors integrate into **CDK, Reynolds &
Reynolds, Tekion and DealerSocket** at VIN level.

🆕 **The "no open-source DMS" finding is now precise rather than absolute:** open-source *repair-shop*
managers do exist — `winterautollc/OpenAutoCore` (**GPL-3.0**, 9★, live), `GarageBuddy` (work in progress),
and the most complete one, `ChanMeng666/Automotive-Repair-Management-System`, **archived by its owner on
2026-07-08**. None scales into a DMS, and the one that is alive is GPL. **Automotive retail AI is an
integration market and will stay one.** See `verticals/solutions.md`.

## T8 — Every credible automotive agent design has a human gate

Consistent across every agent implementation reviewed in this KB: the architecturally serious ones put a
**human sign-off between the model and the vehicle**. The clearest example calls it
"Technician-in-the-Loop" — low-confidence or safety-critical cases route to a technician before any
over-the-air action. Treat the gate as a required architectural element, not a nice-to-have; it is also
what makes the AI Act's human-oversight requirement **demonstrable** rather than asserted.

## T9 — Market-size numbers are still not trustworthy; adoption numbers are

2026 "AI in automotive" estimates now span **$5.80B** (Precedence) to **$26.98B** (TBRC) to **$38.45B by
2030** (MarketsandMarkets) — while a separate report puts **China alone at ~$4.9B** and **India at
~$0.96B** for 2026. Those cannot all be true of the same market. Use adoption figures (71% in-vehicle AI,
47%→72% by 2030 per PwC, ~26% sector-leading adoption) and cite market size only with its source attached.
Detail and the full conflict table in `intel/market.md`.

## T10 — Declared gaps this pass

Recording these because an unstated gap is indistinguishable from coverage.

1. 🟢 **Closed since last pass:** the LATAM regulatory question. Searching in **Portuguese and Spanish**
   (the channel the previous pass named as missing) established that **Brazil's PL 2338/2023 is not law**
   (Senate 10 Dec 2024; Câmara *"Aguardando Parecer"*, last movement 2 Sep 2026) and **Mexico has no
   general AI law** (85 initiatives since Apr 2023, 67 pending). **A LATAM "AI compliance" pitch has no
   legal hook; a data-protection one (LGPD/Anatel) does.**
2. 🔴 **Still missing in LATAM:** any **CONTRAN** resolution on AVs in Brazil, any **NOM** for AVs in
   Mexico, any AMIA/ANFAVEA position, and **any AI-adoption data for Mexican or Brazilian auto plants**.
   Closing it needs Diário Oficial / DOF / CONTRAN / industry-body primary sources, not web search.
3. 🔴 **No open-source Dealership Management System** — re-searched and re-confirmed, now with the
   repair-shop near-misses named (T7) so the search is not repeated from scratch.
4. 🟡 **No mature, permissively-licensed automotive-specific *agent* framework.** Re-confirmed: the top
   search hits are general-purpose agent frameworks with no automotive content, plus 0-star unlicensed
   hobby projects. The buildable layer is policies/VLAs and SDV infrastructure.
5. 🟡 **GitHub trending still cannot be filtered for automotive.** `github.com/trending` has no automotive
   topic filter and the topic pages surface mostly 0–5 star projects. Trend detection here has to come
   from foundations and vendor releases — see `repos/trending.md` for the method note.
6. 🔴 **Two channels are blocked, which constrains everything above:** `api.github.com` returns **HTTP 403**
   for repositories not attached to this session (so licences and stars are read from rendered repository
   pages), and **`eclipsesdv.org` failed DNS resolution** this pass (so S-CORE release notes came from the
   GitHub releases page plus trade press rather than the project's own announcements).
7. 🟡 **Japan is the thinnest major market in this KB.** Beyond "first to permit L3" and "remote monitoring
   required for all L4", searches returned almost nothing dated 2026. Named here so the next pass targets
   MLIT/METI sources directly.

---
*Updated 2026-10-31 (previous pass 2026-10-26). N1–N2 are new this pass; T0–T8 are preserved as written on
2026-10-26 and deliberately not renumbered. ⚠️ marks a claim this pass could not verify against a primary
source; 🔴 an open gap; 🟢 a gap closed since the previous pass.*

## 🆕 Gaps opened or closed on 2026-10-31

- 🟢 **Closed — China's mandatory standards have numbers.** **GB 44721-2026** (L3/L4, effective
  **1 July 2027**, MIIT, Class M and N, one-year transition) and **GB 47955-2026** (combined driver
  assistance, effective **1 January 2027**). The 2026-10-26 pass carried this as "⚠️ unverified".
- 🟢 **Closed — the AutoE2E licence conflict.** Secondary sources said OpenMDW-1.1; the repository's
  `LICENSE`, fetched raw, is **verbatim Apache-2.0**. Settled by reading the file.
- 🟢 **Partially closed — Japan, previously "the thinnest major market in this KB".** Now dated and named:
  **Phase II AI Basic Plan** (non-binding national strategy) and **AI Business Guidelines v1.2**, which
  cover **AI agents and physical AI** specifically. Level 4 remains **ODD-bounded**. MLIT/METI primary
  sources still not read directly.
- 🟢 **Partially closed — Brazil's AV instrument.** **PL 1317/2023** would add licensing, reporting and AI
  governance duties to the **Código de Trânsito** — distinct from PL 2338/2023 and previously missed here.
  Still no CONTRAN resolution; still no regulation of AV testing or circulation on any Brazilian road.
- 🔴 **Opened — model weights cannot be verified from this session.** `huggingface.co` **does not resolve**
  (DNS failure, consistent with the proxy's allowed-domain policy). Given the Alpamayo code/weights split
  this KB already caught, the weights licences for **AutoE2E** and **Qwen-Drive-1.0** are **unresolved**.
  Next pass: request `huggingface.co` in the session's allowed domains before relying on either.
- 🔴 **Opened — EU AI Act automotive date may have moved to 2 August 2028** via the **Digital Omnibus**
  (reported adopted June 2026, Annex I type-approval route). Two independent sources agree; **neither is the
  Official Journal.** Article 50 transparency reported as applying since **2 August 2026**.
- 🔴 **Open — Auto Agent Protocol adoption is unverified.** The spec, licence split and version are
  verified; **how many dealerships serve the endpoints is not.** Highest-value question for the next pass.
- 🔴 **Open, and now with a US instrument attached — LATAM.** The **Connected Vehicle Security Act of
  2026** advanced unanimously from Senate committee in July 2026 and is expected to reach EV imports
  **assembled in Brazil**. No LATAM-origin automotive repository has been found in any pass.
- 🟡 **Watch — North America AV transparency is narrowing.** One analysis notes 2025's reporting changes
  imply **decreasing public visibility of AV failure modes as fleets grow**, which shrinks the public
  corpus a scenario-mining offering can draw on and raises the value of a client's own logs.

## 🆕 Gaps opened or closed on 2026-11-13

**Closed:**
- 🟢 *"Is there any open automotive product-tier software, or only research code?"* — **closed by
  `vision_pilot`.** There is an Apache-2.0 L2 ADAS stack with 927★ and 4,282 commits.
- 🟢 *"Does the diagnostics-agent category have anything above single-digit stars?"* — **closed.**
  `farzadnadiri/Peykan` (MIT, 26★), which also covers **J1939**, the commercial-vehicle bus no other
  agent in this KB touches. ⚠️ It is reachable at `farzadnadiri/mcp-can` in every search result; that
  address is a **rename** and will eventually rot.

**Opened:**
- 🔴 **Can `vision_pilot`'s safety claim be substantiated?** The roadmap names ISO 26262 and ISO 8800;
  nothing published shows progress against them. This is the question that decides whether it is an OEM
  conversation or a prototype conversation.
- 🔴 **No benchmark exists for any model in the new release wave.** `vision_pilot` publishes none;
  `autoware_latent_drive` explicitly publishes none and offers only qualitative open-loop replays. The
  eight-model ADE/FDE table carried from AutoE2E's README (2026-10-31) is **still the only published
  multi-model open comparison in this field**, was never like-for-like, and now covers a **minority** of
  available models. **It is ageing badly.**
- 🔴 **Model weights remain unverified for a fourth consecutive pass** (`huggingface.co` does not resolve).
  This now blocks a specific decision: `autoware_latent_drive` has **no repository licence**, and its two
  ONNX models and all training detail live **only** on Hugging Face — so the model card is the **only**
  place a grant could exist, and it cannot be read.
- 🔴 **`autoware.trucks` is a charter, not a codebase** (9 commits). North American freight demand is
  visible (Kodiak in Indiana and Ohio; California's heavy-duty AV rules of 28 April 2026) and the open
  supply is not there yet. **That gap is the opportunity, and it has a clock on it.**

---
*Updated 2026-11-13 (previous passes 2026-10-31, 2026-10-26). Every repository claim in this file was read from the rendered repository page
or a raw licence file today; `curl` and `api.github.com` are both HTTP 403 in this session. Regulatory and
market claims are secondary-sourced unless stated otherwise, and the 🔴 markers flag what could not be verified.*

---

## 🆕 2026-11-21 (fourth pass) — trends with the evidence attached

### 📡 "AI-defined vehicle" replaces "software-defined vehicle" in the industry's own language

CES 2026 coverage reports the framing moving from **software-defined** to **AI-defined**; NTT DATA calls
the same shift **"from software-defined to AI-native."** AI is being described as core infrastructure
spanning design, manufacturing and predictive maintenance rather than an in-cabin feature.
🟢 **Why it matters for a studio:** it changes the buying centre. "Software-defined" was a platform/E-E
architecture conversation owned by engineering; "AI-defined" pulls in manufacturing and aftersales
budgets too. **The vocabulary is worth adopting; the underlying stacks are the ones in Layer F and the
new Layer H.**

### 📊 Agentic AI has arrived in automotive *engineering*, not in the car

The most load-bearing adoption datapoint found this pass: Capgemini Research Institute, **800 senior
automotive executives, July 2026** (400 OEM / 160 Tier-1 / 240 technology providers) — **35% report
using agentic AI in engineering processes, 33% beginning pilots**, with value realisation strongest in
**software-focused environments.** 🟢 **Note where the agents are: in the V-cycle, not the vehicle.**
That is precisely the surface `jherrodthomas/automotive-skills-suite` (MIT, 2,907★, 76
builder+reviewer pairs → ISO 26262 / 21434 / 21448 / ASPICE / AIAG-VDA `.xlsx` artefacts) addresses, and
it is why that repo remains the highest-relevance single asset in this KB for an AI studio.

### 📊 Readiness ≠ results — the gap is the engagement

PwC projects adoption rising **47% → 72% of companies by 2030**. Deloitte's readiness work finds that
**some firms score well on readiness while realising the fewest benefits.** KPMG (via Bloomberg Línea)
names the mechanism in LATAM specifically: **AI scales poorly when data is fragmented across systems
and supply-chain players.** 🟢 **Three independent houses describing one shape — pilots exist,
consolidation does not.** Treat "we already have pilots" as the *starting* condition, and sell
consolidation. **This is the same adoption-without-governance pattern the education KB recorded across
all four regions; it is one pattern across industries, not an automotive peculiarity.**

### 📡 Edge inference moves in-vehicle, and the open base is no longer missing

Market commentary flags the shift to **edge AI processed inside the vehicle**, with implementation cost
(hardware + software) as the main brake. The permissive base now exists:
[OpenSparX/MasterAgent](https://github.com/OpenSparX/MasterAgent) (Apache-2.0, 966★) —
*"100% on-device, sub-100 ms on Qualcomm NPU, zero cloud dependency"* — plus
[toyota-connected/ivi-homescreen](https://github.com/toyota-connected/ivi-homescreen) (Apache-2.0,
pushed today) for the display layer. 🟢 **An in-cabin agent that degrades gracefully with no
connectivity is now buildable entirely from permissive parts.**

### ⚠️ Margin pressure is reshaping *which* AI gets bought

RSM reports **NA suppliers** pushed by OEM pricing pressure and margin compression toward data
investments with **immediate operational value: forecasting, scrap reduction, predictive maintenance,
energy optimisation.** Ward's notes **tariffs weighing on profits** and a **record average new-vehicle
cost above US$50,000**. 🔴 **Consequence for proposals: the horizon has shortened.** An AI proposal that
cannot name a cost line it reduces this fiscal year is competing against one that can. Of those four
named cost lines, **scrap/rework is the one with a production-grade permissive base already in this KB**
(`anomalib`, Apache-2.0, 6,414★, Layer G).

### 🔴 A licence trend, and it is the actionable one for a studio

Across this pass's sweep, **the automotive open-source licence picture splits by layer, and the split is
sharp**: the **diagnostics / ECU-tooling layer is permissive nearly throughout** (MIT and Apache-2.0 —
`python-udsoncan`, `automotive_diag`, `cogu/autosar`, `CarDash`, `CANviz`, `SwiftOBD2`), while the
**V2X / cooperative-driving layer has no permissive anchor at all** (`vanetza` CC-BY-NC, `artery`
GPL-2.0, `mosaic` EPL-2.0, `veins` GPL-2.0, `OpenCDA` academic-only). 🟢 **So licence risk in automotive
is predictable by layer, and it is a planning input: diagnostics and bench work can be quoted as
build-on-open-source; V2X work must be quoted with legal review in the SOW.**
