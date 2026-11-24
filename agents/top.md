---
industry: automotive
region: Global
updated: 2026-11-24
---

# 🎯 AI agents & models — Automotive

> Open-source AI agents, policies and models for the automotive industry. Focus: MIT / Apache 2.0 / BSD.
> **Verification method this pass (2026-11-21):** all 174 repository URLs in this KB were probed with
> `git ls-remote` (existence/liveness) and 152 LICENSE files were byte-read from
> `raw.githubusercontent.com` (**HTTP 200** — it works, unlike `github.com`). Stars, forks, `pushed_at`
> and `archived` come from `gh api -X GET search/repositories`. See the channel table under **"What changed on 2026-11-21"**
> for the full channel table. **Nothing below is a page-read guess any more.**
>
> *Superseded note, kept for the record —* **2026-11-13:** `curl -sI` against `github.com` returns **HTTP 403**
> through this session's proxy — re-tested today on three URLs, including `api.github.com`, all 403. So
> licence and star figures are read from the **rendered repository page**, and where a licence had to be
> settled the file was fetched raw from `raw.githubusercontent.com` and read directly. That is how
> `autoware-safety-island` (Apache-2.0, not "Other") and `autoware_latent_drive` (**no licence at all**)
> were decided below.
> **`huggingface.co` still does not resolve in this session**, so no model-weight licence was verified
> first-hand. Every weights claim remains labelled unverified. `www.manilatimes.net` also failed to
> resolve, so the TIER IV press announcement was replaced with the primary source: the repositories.
>
> 🆕 = new this pass. 🔄 = licence/stars re-read today. ⏸ = URL re-probed, figures carried from an
> earlier pass and labelled rather than silently refreshed. **No row is a placeholder.**

## 🆕 What changed on 2026-11-24 — the V2X licence verdict reverses, and the model tier gains four permissive rows

**Window:** 2026-11-21 14:52Z → 2026-11-24. First pass since the four same-day passes of 2026-11-21.
**Channel:** `gh api -X GET search/repositories` for stars/forks/SPDX/`pushed_at`; every licence below
**byte-read** from `raw.githubusercontent.com`; every address probed with `git ls-remote`
(**47 new addresses probed, 47 live, 0 dead**).

### ⚠️ W1. 🔴 CORRECTION TO THIS KB — "the V2X/C-ITS layer has no permissive anchor at all" is **false**

The 2026-11-21 pass wrote, as a planning input, that the V2X layer *"has NO PERMISSIVE ANCHOR AT ALL"*
and that V2X work must therefore quote legal review in the SOW. **That is wrong as stated.**

[ika-rwth-aachen/etsi_its_messages](https://github.com/ika-rwth-aachen/etsi_its_messages) is **MIT**
— byte-read, `LICENSE`, 1,117 bytes, *"Copyright (c) Institute for Automotive Engineering (ika), RWTH
Aachen University"* — 83★, pushed 2026-10-28. It is ROS 2 support for **ETSI ITS messages** (CAM, DENM,
CPM, VAM): the encode/decode layer of the C-ITS stack, from a named automotive-engineering institute.

**The accurate claim is layered, not blanket:**

| C-ITS sub-layer | Licence reality (byte-read) | How to quote it |
|---|---|---|
| **Message / encoding** | **Permissive.** `etsi_its_messages` **MIT**; [VjiaLi/V2U4Real](https://github.com/VjiaLi/V2U4Real) **MIT** (75★, CVPR 2026 V2X-UAV dataset) | Build-on-open-source. No legal review needed for the message layer. |
| **Protocol stack** | **Non-commercial.** `riebl/vanetza` **CC-BY-NC** (231★) | Hard exclusion. Not a licence question, a prohibition. |
| **Simulation** | **Copyleft throughout.** `riebl/artery` GPL-2.0 (234★); `sommer/veins` GPL-2.0 (331★); 🆕 `DriveX-devs/VaN3Twin` **GPL-2.0** (167★, byte-read 17,987 B); `eclipse-mosaic/mosaic` EPL-2.0 (118★) | Legal review in the SOW — but for *simulation*, which is a tool, not shipped product. |

**Why the error mattered:** the blanket version priced legal review into every V2X engagement. The
layered version says a C-ITS **message-handling** deliverable is clean, and only the simulation and
stack layers carry the cost. *General lesson: a layer-wide licence verdict is only as good as the
sub-layer with the most rows — re-check it when any new row lands in that layer.*

### 🆕 W2. Model tier — four permissive driving-model rows, all byte-read Apache-2.0

| Repo | Licence (byte-read) | ★ | Pushed | What it is |
|---|---|--:|---|---|
| [fudan-generative-vision/WAM-Flow](https://github.com/fudan-generative-vision/WAM-Flow) | **Apache-2.0** — `LICENSE`, 11,357 B, canonical | 376 | 2026-09-03 | **CVPR 2026.** Parallel coarse-to-fine motion planning via discrete flow matching. The planner tier, not the perception tier. APAC-origin (Fudan). |
| [RenzKa/simlingo](https://github.com/RenzKa/simlingo) | **Apache-2.0** — `LICENSE`, 11,380 B | 480 | ⏸ 2025-08-25 | **CVPR 2025 Spotlight.** SimLingo/CarLLaVA — vision-only *closed-loop* driving with language. Closed-loop is the part that matters: most VLA repos are open-loop benchmarks. ⚠️ 15 months since last push. |
| [AutoLab-SAI-SJTU/GE2EAD](https://github.com/AutoLab-SAI-SJTU/GE2EAD) | **Apache-2.0** — `LICENSE`, 11,357 B | 218 | 2026-10-29 | Curated corpus of E2E / VLM / VLA / hybrid driving papers with organised taxonomy. A survey index, **not** runnable code — use it to pick a teacher model for **P6**, not as a base. |
| [fudan-generative-vision/WAM-Diff2](https://github.com/fudan-generative-vision/WAM-Diff2) | **Apache-2.0** — `LICENSE`, 11,357 B | 105 | 2026-08-19 | Hierarchical AR-to-diffusion distillation for efficient driving VLA. The *distillation* step of **P6** published as code. |

**The Apache-2.0-by-convention pattern holds for a third consecutive pass:** 4 of 4 new model rows are
Apache-2.0. The research tier of this industry is licence-safe by convention — but see the standing
caveat: **the weights are a separate grant and `huggingface.co` still does not resolve from this
session**, so no weights claim below is first-hand.

### 🆕 W3. Agent / skill tier — five new rows, and the honest note is that four of them are tiny

| Repo | Licence (byte-read) | ★ | Pushed | What it is, and what it is worth |
|---|---|--:|---|---|
| [LGDiMaggio/predictive-maintenance-mcp](https://github.com/LGDiMaggio/predictive-maintenance-mcp) | **MIT** — `LICENSE`, 1,080 B | **118** | 2026-11-23 | **The real one.** MCP server turning an LLM into a condition-monitoring assistant for reliability engineers. Pushed yesterday. First maintained MCP server for the *plant-floor* side of automotive — see **P27**. |
| [Nemeson/C-ITS-Expert](https://github.com/Nemeson/C-ITS-Expert) | **MIT** — `LICENSE`, 1,069 B | 1 | 2026-10-10 | V2X / C-ITS protocol-engineering skill suite **and validator** (CLI + MCP). ⚠️ **1★.** Recorded because it is the only agent-shaped artefact in the C-ITS layer and it pairs with `etsi_its_messages` (W1) — read it as a design reference, not a dependency. |
| [dsdtsolutionsllc/manus-automotive-skills-suite](https://github.com/dsdtsolutionsllc/manus-automotive-skills-suite) | **MIT** — index-reported | 2 | 2026-08-15 | Manus-compatible conversion of the **152 skills (76 builder/reviewer pairs)** of `jherrodthomas/automotive-skills-suite`. Useful as evidence the skills-suite format is being **ported across agent runtimes**; no new content of its own. |
| [eric-rolph/beamng-mcp](https://github.com/eric-rolph/beamng-mcp) | **MIT** — index-reported | 2 | 2026-11-23 | Local-first MCP server for **BeamNG.drive** via BeamNGpy. ⚠️ 2★. Relevant only because it is a *second* sim-behind-MCP design after `drivingbench_harness_code`, which is the pattern **P15** rests on. |
| [SrinivasReddyMudem/automotive-lifecycle-agents](https://github.com/SrinivasReddyMudem/automotive-lifecycle-agents) | **MIT** — index-reported | 0 | 2026-10-21 | Agents for automotive SW engineering roles (developer, tester, integrator, project lead). ⚠️ **0★.** Recorded as a shape, not a recommendation. |
| [decionis/kervix](https://github.com/decionis/kervix) | **Apache-2.0** — `LICENSE`, 11,358 B | 0 | 2026-11-21 | **Kernel-enforced execution authority for AI agents on QNX 8.0** — *"agents propose; QNX decides."* ⚠️ **0★, created three days ago.** Recorded because the **architecture** is the one **P16** argues for (the reason never reaches the controller) and this is the first repo to put it in the kernel. Watch, do not adopt. |

**Say the quiet part out loud:** one of these six has a community (118★). The other five are 0–2★. They
are recorded because *the shapes* are the finding — an MCP-wrapped simulator, a kernel-gated agent, a
ported skill suite — and shapes are what a studio reuses. **Do not put a 0★ repo in a client proposal
as a dependency.**

### 🔄 W4. Anchor re-measurement — one instrument only, and openpilot moved

All four read from `gh api search/repositories` on 2026-11-24 (**not** page-rendered — see the standing
rule in `intel/trends.md` **N15** about never refreshing a count with a different instrument):

| Anchor | ★ (search index) | Forks | Licence | Pushed |
|---|--:|--:|---|---|
| [commaai/openpilot](https://github.com/commaai/openpilot) | **64,220** ⬆ from ~63,000 | 11,407 | MIT | **2026-11-24** (today) |
| [carla-simulator/carla](https://github.com/carla-simulator/carla) | 14,692 | 4,753 | MIT | 2026-11-23 |
| [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | 12,275 | 3,753 | Apache-2.0 | 2026-11-20 |
| [autowarefoundation/vision_pilot](https://github.com/autowarefoundation/vision_pilot) | 929 | 198 | Apache-2.0 | 2026-11-23 |

**[cobanov/teslamate-mcp](https://github.com/cobanov/teslamate-mcp) holds its title: 142★, MIT, pushed
2026-11-14 — still the largest automotive MCP server by an order of magnitude.** Verified by enumerating
the field rather than asserting it: `MyTeslaMate/mcp-tesla` 5★, `lodordev/mcp-teslamate-fleet` 2★,
`xalc/teslamate-mcp` 0★, `volspan-deployments/teslamateapi-mcp` 0★ (NOASSERTION). **The automotive MCP
ecosystem is one repo and a tail.**

## 🆕 What changed on 2026-11-21 — third pass (13:40Z)

**No new agent rows this pass, and that is the accurate result** — the discovery legs went after three
standing gaps rather than at the agent layer, which was swept twice already today (09:55Z, 12:45Z).
What changed is **two gap verdicts, one licence axis, and one method correction.**

### W1. ✅ Shelf re-verified independently — 193 slugs, 190 live, 3 dead, 0 licence errors

Re-probed every repository reference in all eight files (**193 distinct owner/name slugs**) with a **different liveness oracle**
than the 12:45Z pass used. **190 live, 3 dead — the same three already recorded, none a recommendation.**
A claimed-vs-measured differ flagged **25 rows; all 25 were the differ's own artefact** (a line naming
several repos and several licences, or the base's own claimed-vs-measured table being read as data).
**The KB was correct in 25 of 25.** Two independent re-measurements 55 minutes apart agree exactly, so
**further whole-shelf re-probing is now low-value** — discovery and primary-source access are the binding
constraints, not rot.

### W2. 🔴 Method correction — the standing instruction to verify URLs with `curl -sI` returns no information here

The fleet's task spec says *"verify every URL before writing it (`curl -sI`)."* Executed literally
against `github.com` from this environment, **it cannot distinguish a live repo from one that does not
exist**: the proxy answers **403 for `torvalds/linux`** and **403 for a nonsense slug**, identically.
This KB already knew `github.com` is 403 (**N10**); what is new is that **the 403 is uniform, so the
probe is not a weak test but a null one.**

**Use `git ls-remote --symref https://github.com/<o>/<r> HEAD`.** It discriminates correctly **and**
returns the **default branch**, which the `raw.githubusercontent.com` licence read needs. Guessing that
branch `main`-then-`master` is a silent false-negative generator — measured this pass:
`anomalib` = `main`, `awslabs/sagemaker-defect-detection` = **`mainline`**, `hcengineering/platform` =
**`develop`**. `compose/patterns.md` **P19** channel 1 updated accordingly.

### W3. 🔴 A licence axis this KB's discipline cannot see: the dataset grant

Byte-reading `LICENSE` — this file's core discipline — is **blind by construction** to the licence of the
data a model was fitted to, and for an AI repo **that is usually the binding grant.** The specimen:
`anomalib` is **Apache-2.0**, while **MVTec AD**, the benchmark the whole industrial-inspection layer
reports against, is **CC BY-NC-SA 4.0 — non-commercial.** Shipping weights trained on it, or **quoting
its benchmark number in a commercial proposal**, is NC-data commercial use. Full treatment:
`intel/trends.md` **N17**; diligence step folded into **P13**/**P19**.

**Corollary that inverts a standing reading:** `NOASSERTION` is frequently **caused by** a dataset
attribution appended to otherwise-verbatim licence text (`MayankGangwal-code/ev-battery-soc-estimation`
appends an *LG 18650HG2 … CC BY 4.0* credit; `PythonRobotics` inserts a contributors URL). GitHub's
classifier is near-exact-match, so **`NOASSERTION` tracks conscientious authorship, not risk** — the
careless repos here have no licence file at all and measure `NONE`.

### W4. 🔄 Two `NOASSERTION` rows resolved, fixing an internal contradiction

`compose/patterns.md` **P19** already recorded the byte-read answers for both, while
`repos/foundations.md` still told readers to *"settle before any use."* **A reader of one file was
getting worse advice than a reader of the other.** Both rows are now corrected in place:
**`AtsushiSakai/PythonRobotics` = MIT** (30,951★, cleanly usable, nothing pending) and
**`autoas/as` = dual GPL-3.0 **OR** Commercial** (so the "settle it" step is a procurement conversation,
not a licence investigation — worth knowing for the only substantial open AUTOSAR BSW).

### W5. 🔴 Gap verdicts — one closed, one confirmed-with-a-reason, one restated correctly

| Gap | Standing record | This pass |
|---|---|---|
| **Plant-floor / manufacturing quality AI** | `0 repos`, 5 passes | ✅ **CLOSED.** `open-edge-platform/anomalib`, Apache-2.0, **6,414★**, pushed 2026-11-20. **Five passes missed it because every query said *automotive*; it calls itself industrial anomaly detection.** `repos/foundations.md` Layer G |
| **DMS (driver monitoring)** | "none", 7 passes | 🔴 **CONFIRMED OPEN, with the reason.** The only framework-grade open DMS is GPL-3.0, **1★**, unpushed since **2024-03-08**. Everything else is a 0–3★ eye-aspect-ratio demo. **Mandated capability, zero adoptable open supply → this KB's strongest build-vs-adopt case** (`intel/trends.md` **N18**) |
| **EV / battery AI** | `0 repos`, 5 passes | 🔄 **RESTATED.** The layer is populated but **uniformly sub-scale** — best candidates 83★ (dormant 22 months) and 0★. Correct statement: **"nothing above hobby scale," not "nothing exists."** The consensus architecture (EKF for state, ML for residual) is worth taking even though no code is |

### W6. 🔴 Declared gaps 2026-11-21 (third pass) — searched, found nothing, recorded

- **UAW contract language on AI/automation** — nothing found. Live question for any US plant engagement.
- **AI quality inspection in Chinese / Japanese / Korean auto plants**, as distinct from robotics —
  very little. APAC's plant story is robot density; inspection judgement is the gap.
- **Brazilian automotive AI inspection deployments** — nothing. Brazil appears only in aggregate
  investment figures; **no measured AI-adoption rate exists for any LATAM country** in this KB.
- **2026 AV regulation for Thailand, Indonesia or Vietnam** — none found; the authoritative ASEAN AV
  landscape report is **2024** and stale.
- **`Reg. (EU) 2026/1744`** — second secondary sighting, still no primary source (`eur-lex` DNS-dead,
  7th pass). **Two secondary sightings sharing one possible upstream is not corroboration.**
- **Excluded sources now three:** `coldai.org` (uncorroborable AIAG attribution) joins `x-pilot` and
  `streamlinefeed.co.ke`.

---

## 🆕 What changed on 2026-11-21 — second pass (verification, 12:45Z)

**Rotation sent a second pass at automotive on the same day.** The 09:55Z base was **verified, not
rewritten**. Two new permissive rows, one rejection, and a licence layer that held up under independent
re-measurement.

### V1. ✅ The licence layer was re-measured from scratch and came back clean — 0 errors in 182 rows

All 188 `github.com/<owner>/<repo>` URLs in the eight files were re-probed via batched
`gh api -X GET search/repositories` (8 slugs per query), returning measured stars, forks, SPDX,
`pushed_at` and `archived` for **182 rows**. Every row whose written licence disagreed with the measured
SPDX was then **byte-read from `raw.githubusercontent.com`**.

| Result | Count |
|---|--:|
| URLs probed | **188** |
| Live | **185** |
| Dead | **3** — *the same 3 the 09:55Z pass already recorded*, none a recommendation |
| Rows where written licence ≠ measured SPDX | **20** |
| **Of those, real errors in this base** | **0** |
| Archived repos presented as live | **0** |

**All 20 flags resolved in the base's favour, in two distinct ways** — and the split is the useful part:

- **13 flags were `NOASSERTION`-as-pointer**, exactly as this KB's standing rule predicts. Byte-read
  verdicts: `nutonomy/nuscenes-devkit` **is** Apache-2.0 (549-byte pointer header); `odoo/odoo` **is**
  LGPL-3.0 (43,529 bytes); `auto-agent-protocol` **is** Apache-2.0 for code/schemas with **CC BY 4.0
  documentation** — a dual arrangement, which is why its `LICENSE` is a short 5,290 bytes and why the API
  cannot classify it. **The written rows were right and the API was wrong in every case.**
- **7 flags were the detector catching the base's own warning prose.** `petrpatek/obd2-mcp-server` and
  `cyrusdavirusss/j2534-mcp-server` are flagged because their cells contain the word *MIT* — inside the
  sentence **"README says MIT; there is NO `LICENSE` file"**. `autowarefoundation/AWSIM` is flagged for
  containing *Apache-2.0* inside **"🔴 bespoke AWSIM License — **Not Apache-2.0**"**.
  `waymo-research/waymo-open-dataset` already carries the **`wdl_limited/` carve-out**. **A base that
  states its own exceptions precisely will trip a naive licence differ; that is a feature of the base, not
  a defect.** Any future automated checker must read the cell, not grep it.

### V2. 🔴 Method finding: the licence-filename list is not the instrument — the row is

Probing `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `LICENCE`, `COPYING` and `NOTICE` on `main`, `master` and
`develop` returned **404 on all 18 combinations** for `autowarefoundation/autoware-safety-island`, which
would have been written up as *"claimed Apache-2.0, no licence file exists"* — **a false correction
against a correct base.** The repo carries a **full 10,894-byte Apache-2.0 text in `license.rst`**
(reStructuredText, hence GitHub's `NOASSERTION`), and its README header carries
`SPDX-License-Identifier: Apache-2.0` under an **Arm Limited** copyright.

**The row already said `license.rst`.** The rule for every later pass: **read the evidence a row cites
before re-probing it.** Extend the probe list with `license.rst` / `LICENSE.rst`.

### V3. 🆕 Two new rows, both permissive, both byte-read

| Repo | Licence (byte-read 2026-11-21) | ★ | Why it is here |
|---|---|--:|---|
| [LogosIntelligenceLab/SGDrive](https://github.com/LogosIntelligenceLab/SGDrive) | **MIT**, 1,077 bytes | 81 | **The only MIT-licensed driving model in this KB.** See *Driving policies & VLA models*. |
| [TUM-AVS/FM-AD-Survey](https://github.com/TUM-AVS/FM-AD-Survey) | **Apache-2.0**, 11,337 bytes (canonical) | 249 | TU Munich foundation-models-for-AD survey, pushed 2026-11-19. See *Survey/index layer*. |

### V4. 🔴 Rejected on licence: Xiaomi's L3 org shipped a 147★ model with no grant

[XiaomiAutoL3/DriveZero](https://github.com/XiaomiAutoL3/DriveZero) — **147★, measured `NONE`, no licence
file.** *"End-to-end driving beyond human demonstrations."* **Rejected.** Noteworthy because this KB
already holds **Xiaomi's `recogdrive` as Apache-2.0 (631★)**: **the same vendor is inconsistent across its
own repositories, so vendor reputation is not a licence signal.** Re-probe later — an unlicensed 147★
model is a plausible candidate for a grant being added.

### V5. 📈 Drift: the shelf is stable, and the movement is concentrated in one cluster

Of rows with ≥200 claimed stars, **the largest absolute moves are all in the VLA / world-model layer**:
`NVlabs/alpamayo-recipes` **205 → 245 (+40)**, `NVlabs/alpamayo2` **287 → 314 (+27)**,
`QwenLM/Qwen-Drive-1.0` **537 → 563 (+26)**, `OpenDriveLab/WorldEngine` **520 → 542 (+22)**. Everything
else with a large base moved by single digits (`openpilot` **64,192**, `PythonRobotics` 30,951 → 30,953).
**Attention is concentrating on the open VLA/world-model frontier, not on the stacks** — and the NVIDIA
Alpamayo line is the centre of it. Fast movers on a small base: `autowarefoundation/autoware_latent_drive`
**42 → 95**, `superdeman/cockpit-agent` **1 → 30**.
⚠️ **These are drift-since-the-row-was-written, not a measured growth rate** — rows carry snapshot dates
from 2026-10-31 through 2026-11-21. Direction is sound; do not quote a per-day figure.

### V6. 🔴 Declared gaps 2026-11-21 (verification pass) — searched, found nothing, recorded

| Query / target | Result |
|---|---|
| `SpaceDrive in:name` (named as a CVPR 2026 driving paper by an aggregator) | **No such repository resolves.** The aggregator named a paper, not a reachable repo. |
| `carlover` (named MIT automotive assistant via an ecosystems aggregator) | **5 repos, all 0–3★, all unlicensed junk.** The specific slug the aggregator cited does not resolve. **Second aggregator-sourced candidate to evaporate in one pass.** |
| Dealership ERP/CRM, permissive | **7th consecutive negative.** Leg returned general-purpose ERP only: `Dolibarr` **GPL-3.0** (7,889★, correctly held as copyleft), `YetiForceCRM` **`NOASSERTION` and unpushed since Sep 2024**, `SuiteCRM` did not resolve. **`open-mercato` (MIT, 1,953★) remains the only permissive option and it is a framework, not a dealership product.** |
| Model **weights** licences | **Unverifiable from this environment, 6th consecutive pass** — `huggingface.co` DNS-dead, re-probed this pass. |

---


## 🆕 What changed on 2026-11-21

**Channel breakthrough — the verification problem this file has carried since 2026-10-26 is solved.**
Every pass since then recorded that `curl -sI https://github.com` is **HTTP 403** and concluded that
licences and liveness therefore had to be inferred from rendered pages. Re-tested today: `github.com`
and `api.github.com` are still 403, **but two channels do work and were never tried together.**

| Channel | Status today | What it settles authoritatively |
|---|---|---|
| `git ls-remote --heads https://github.com/<owner>/<repo>` | ✅ works | **Existence and liveness.** Returns a 40-hex SHA for a live repo; fails with a credential prompt for one that is gone. Distinguishes live from 404 with no API quota. |
| `curl https://raw.githubusercontent.com/<o>/<r>/<branch>/LICENSE` | ✅ **HTTP 200** | **The licence grant, byte for byte.** No SPDX guessing. |
| `gh api -X GET search/repositories -f q='repo:<o>/<r>'` | ✅ works | Stars, forks, `pushed_at`, `archived`, `license.spdx_id`. |
| `gh api repos/<o>/<r>` | 🔴 403 | Per-repo REST is scoped to this session's own repositories. Use the **search** endpoint instead. |
| `curl -sI https://github.com` / `api.github.com` | 🔴 403 | Host policy. Not retryable — do not route around it. |
| `huggingface.co` | 🔴 does not resolve | Still no first-hand model-weight licence. Unchanged. |

**Consequence: this pass verified all 174 repository URLs in the KB and byte-read 152 LICENSE files.**
No row in this base is now a page-read guess. Future passes should start from these four channels.

### 1. 🔴 URL sweep: 174 URLs probed, 170 live, 3 genuinely dead, 1 false positive

All 174 distinct `github.com/<owner>/<repo>` URLs across the eight KB files were probed with
`git ls-remote`. **The result is better than it looks:** of the 3 dead URLs, **none is a recommendation.**

| Dead URL | Where it sits | Status |
|---|---|---|
| [RobertSloan22/tars-car-mcp](https://github.com/RobertSloan22/tars-car-mcp) | `agents/top.md` **exclusions** table + `agents/trending.md` as *"Rejected"* | Gone. It was already excluded for having no licence and being gated on a proprietary desktop app. **Its removal confirms the exclusion** — kept as a record, not promoted. |
| [luca1234413/MotionBastard](https://github.com/luca1234413/MotionBastard) | Legacy *"Pipeline automático"* block (2026-07-02) in both trending files | Gone. Already flagged in-file as **not automotive software** (After Effects motion design). |
| [vaisakhvenugopal/Deconstructing-BYD-s-Technology-Architecture](https://github.com/vaisakhvenugopal/Deconstructing-BYD-s-Technology-Architecture) | Same legacy block | Gone. Licence was `?` — never a usable grant. |

**Known false positives for the next sweep** (these are valid URLs that are not repositories, so
`git ls-remote` correctly fails on them — do not re-flag them):
`github.com/orgs/autowarefoundation` (organisation listing), `github.com/topics/automotive-ai` and
`github.com/topics/autonomous-driving` (topic pages — both verified to render, and both are **working
discovery channels** for this industry; see `repos/trending.md`). A sweep script should skip the
`orgs/` and `topics/` path prefixes.

**The pattern worth keeping:** all three dead URLs were **0★ rows added by an automated discovery pass**,
and all three had already been labelled unusable by a later human-grade pass. 0★ repositories are not
merely low-signal — **they are the ones that vanish.** Every repository in this base with ≥1★ is live.

### 2. ✅ Licence census by byte-read — and the published shelf beat the automated read 8 times

152 of the 170 live repos serve a LICENSE file; **18 serve none** (all 18 already labelled "no licence"
or licence-from-README in this base — see §4). Census of the 152:

| Grant (byte-read) | Count | Buildable for Globant? |
|---|--:|---|
| Apache-2.0 | 79 | ✅ Yes |
| MIT | 52 | ✅ Yes |
| MPL-2.0 | 3 | ✅ Yes — file-level copyleft only |
| BSD-3-Clause / BSD-2-Clause | 3 / 1 | ✅ Yes |
| EPL-2.0 | 2 | ✅ Yes — weak, file-level copyleft |
| CC0-1.0 | 3 | ✅ Yes (these are lists, not code) |
| AGPL-3.0 | 3 | ⚠️ Network copyleft — service-boundary risk |
| GPL-3.0 / GPL-2.0 | 3 / 2 | ⚠️ Strong copyleft |
| LGPL-3.0 / LGPL-2.1 | 2 / 1 | ⚠️ Linking exception only |
| **Total** | **152** | **143 permissive-or-weak (94%)** |

**The important result is a negative one.** An automated licence classifier run over these same 152 files
disagreed with this base's published cells on 8 repositories — **and the published cells were right every
time.** The cause is a single trap worth recording permanently:

> **Every GNU-family, MPL and EPL licence text names *other* licences inside its own body.**
> MPL-2.0 §1.12 defines "Secondary License" as the GPL/LGPL/**AGPL**. GPL-3.0 §13 references the
> **AGPL**. LGPL-3.0 appends the full GPL text. EPL-2.0 names **GPL-2.0** as a Secondary License.
> So *any* classifier that substring-matches a licence name anywhere in the file misclassifies.
> **Key on the document's title line, never on names appearing in the body.**

| Repo | Naive automated read | Published here (correct) |
|---|---|---|
| [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification) | AGPL-3.0 | **MPL-2.0** |
| [esmini/esmini](https://github.com/esmini/esmini) | AGPL-3.0 | **MPL-2.0** |
| [odoo/odoo](https://github.com/odoo/odoo) | AGPL-3.0 | **LGPL-3.0** |
| [Dolibarr/dolibarr](https://github.com/Dolibarr/dolibarr) | AGPL-3.0 | **GPL-3.0** |
| [winterautollc/OpenAutoCore](https://github.com/winterautollc/OpenAutoCore) | AGPL-3.0 | **GPL-3.0** |
| [eclipse-sumo/sumo](https://github.com/eclipse-sumo/sumo) | GPL-2.0 | **EPL-2.0** |
| [hcengineering/platform](https://github.com/hcengineering/platform) | GPL-2.0 | **EPL-2.0** |
| [openremote/openremote](https://github.com/openremote/openremote) | Apache-2.0 | **AGPL-3.0** |

The `openremote` case is the sharpest: its `LICENSE` is **172,870 bytes** because it bundles a full
dependency-licence listing that contains the Apache text. The project's *own* grant is in the first
paragraph — **AGPL-3.0**. A size-aware reader catches this; a substring matcher cannot.

**`odoo/odoo` is worth stating plainly**, because the rotation brief names Odoo as the ERP exemplar:
its LICENSE header reads *"Odoo is published under the GNU LESSER GENERAL PUBLIC LICENSE, Version 3
(LGPLv3) … Since the LGPL is a set of additional permissions on top of the GPL, the text of the GPL is
included at the bottom as well."* **LGPL-3.0, byte-confirmed** — which is precisely why proprietary Odoo
modules are viable where they would not be under GPL or AGPL.

### 3. 🔴 Four licence cells the API cannot answer and this pass filled by byte-read

`license.spdx_id` returns `NOASSERTION` or `NONE` for these. The byte-read settles all four:

| Repo | ★ | API says | **Byte-read grant** | Why it matters |
|---|--:|---|---|---|
| [autoas/as](https://github.com/autoas/as) | 965 | `NOASSERTION` | **GPL-3.0 *OR* Commercial (dual)** — LICENSE opens *"Dual License: GPLv3 and Commercial"* | Was `NOASSERTION` here too. An AUTOSAR-class stack with a **commercial escape hatch** is a materially different procurement conversation from GPL-only. |
| [openremote/fleet-management](https://github.com/openremote/fleet-management) | 51 | `NOASSERTION` | **AGPL-3.0** | Was `NOASSERTION` here. Network copyleft on a fleet backend — now a known constraint, not an unknown. |
| [COVESA/vss-tools](https://github.com/COVESA/vss-tools) | 81 | `MPL-2.0` | **MPL-2.0** | Was *"⚪ not read this pass"*. Cell now filled. |
| [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics) | 30,954 | `NOASSERTION` | **MIT** (*"The MIT License (MIT)"*) | The largest repo touching this base had no usable licence field. It is plain MIT. |

[waymo-research/waymo-open-dataset](https://github.com/waymo-research/waymo-open-dataset) (3,438★) shows
why `NOASSERTION` happens and why it must not be read as "no licence": the LICENSE states the repo is
**Apache-2.0 *excluding* `src/waymo_open_dataset/wdl_limited`**, which carries its own terms. A named
carve-out directory is actionable; `NOASSERTION` is not. **Use the code, avoid that one directory, and
treat the dataset itself as separately licensed.**

### 4. ✅ The 18 repos with no LICENSE file — this base already had them right

All 18 were cross-checked against their published cells. **No corrections needed.** Two are worth noting
because their cells are *better* than a LICENSE-file probe can be:
[TrampolineRTOS/trampoline](https://github.com/TrampolineRTOS/trampoline) (**GPL-2.0**) and
[navariltd/Fleet-Management-System](https://github.com/navariltd/Fleet-Management-System) (**GPL-3.0**)
serve no LICENSE file; this base read their grant from the README and source headers. A probe that only
fetches `LICENSE` would have downgraded both to "no licence" — **a regression dressed as a refresh.**

### 5. 🔄 Correction that changes a decision: Huly's *repo* is not frozen — its *hosted service* is

This base records `hcengineering/platform` (28,161★, EPL-2.0) as *"frozen and no longer actively
maintained"*, and `compose/patterns.md` cites it as the cautionary liveness example. **The underlying
notice says something different.** The README banner reads: *"The hosted Huly service is being
discontinued because its hosting is no longer being funded … migrate as soon as possible — we can help
you move to either a self-hosted setup or a hosted option."*

First-hand repository state today: `pushed_at` **2026-11-09**, `archived` **false**, and the last five
commits are real fixes, not README edits alone — `fix(github): do not persist the Octokit client in the
user integration secret` (2026-11-05), `fix(gantt)` (2026-11-04), `fix(contact)` (2026-11-02).

**The conflation was "hosted SaaS shutting down" → "project dead", and it runs the wrong way for us.**
The vendor's own recommended path is now **self-hosting**, the code is live, and EPL-2.0 is weak
file-level copyleft. For a Globant engagement that would self-host anyway, Huly moved from *avoid* to
*viable*. The genuine risk is commercial sustainability of the upstream, not abandonment of the code.
The liveness lesson in `compose/patterns.md` still stands — **but it needs a different example**, because
this one was never a case of a dead repo.

### 6. 🆕 New rows this pass — four small agents, one rejection

| Agent | Repo | Licence (byte-read) | ★ | Last push | What it does | Origin |
|---|---|---|--:|---|---|---|
| 🆕 Dealer AI Skills | [arielcoro/dealer-ai-skills](https://github.com/arielcoro/dealer-ai-skills) | **MIT** | 3 | 2026-10-21 | Installable agent skills for **car-dealer retail ops**: SEO/AEO/GEO, BDC, F&I, fixed ops, equity mining, customer lifecycle. Runs on Claude Code, Codex, Cursor, Gemini CLI. | **North America** — US franchise/independent dealer vocabulary (BDC, F&I, equity mining) throughout |
| 🆕 Waypoint | [rogue-media-lab/waypoint](https://github.com/rogue-media-lab/waypoint) | **MIT** | 1 | 2026-11-13 | Service-advisor assistant over SQLite with **VIN decoding and labour-time lookup**. | North America (service-advisor / labour-guide model) |
| 🆕 OmniIntent | [neura-edit/omni-intent](https://github.com/neura-edit/omni-intent) | **MIT** | 1 | 2026-10-03 | **On-device multi-intent routing + deterministic slot extraction** for cockpits, Kotlin. Explicitly *"zero auto-regressive generation delay, automotive-grade determinism"* — no LLM in the hot path. | Not stated |
| 🆕 deeptest-talking-manual | [keklikci/deeptest-talking-manual-26](https://github.com/keklikci/deeptest-talking-manual-26) | **MIT** | 0 | 2026-08-20 | Test generator that hunts **omitted safety warnings** in LLM-backed owner's-manual assistants. | Not stated |
| 🔴 **REJECTED** | [mikko-lab/kopilotti-sales-demo](https://github.com/mikko-lab/kopilotti-sales-demo) | 🔴 **"All Rights Reserved"** | 0 | 2026-10-14 | Used-car price negotiation with rule-based safety bounds. Interesting design; **no grant whatsoever** — LICENSE reads *"No part … may be copied, distributed, modified, or used commercially without prior written permission."* | — |

**`omni-intent` is the one with a design idea worth stealing even at 1★:** it treats cockpit intent as a
*routing* problem with deterministic slot extraction rather than a generation problem, which is the only
shape that survives an automotive latency budget. It pairs directly with the C1–C5 cockpit-AI grading
China published this year (see `intel/market.md`).

**`dealer-ai-skills` is the first dealer-retail agent in this base with a real MIT grant.** It is 3★ and
single-author — but the §1 finding applies in reverse: it is ≥1★, live, and licensed, and it occupies the
dealership-operations slot this base previously had to fill with general-purpose ERP/CRM.

### 7. 🔴 Declared gaps 2026-11-21 — searched, found nothing, recorded

- **No open-source dealership DMS exists.** Searched `open source platform automotive ERP CRM dealership
  MIT Apache` plus iDempiere / XTuple / Compiere / OFBiz / Krayin / Huly / Open Mercato. Every result is a
  **general-purpose** ERP/CRM. There is no open DMS with inventory, F&I and deal-desk modules. `xtuple/xtuple`
  is **gone** (404 today). [idempiere/idempiere](https://github.com/idempiere/idempiere) is live (678★,
  pushed 2026-11-20) but **GPL-2.0** — see `verticals/solutions.md`.
- **No LATAM-origin automotive AI repository found.** Four region-scoped searches run. Not one
  LATAM-origin automotive agent or platform surfaced. This is an **informed gap, not coverage** — see the
  LATAM subsection of `intel/market.md` for what the region does have (industrial policy, no AI-specific
  automotive rule).
- **No GitHub "trending for automotive" feed** — sixth consecutive pass recording this. The working
  substitute remains the search API with star and date floors, documented in `repos/trending.md`.
- **`huggingface.co` still does not resolve**, so no model-weight licence is first-hand. Unchanged since
  2026-10-26.

---

## 🆕 What changed on 2026-11-19

> **Verification method this pass.** `curl -sI https://github.com/...` and `https://api.github.com/...`
> both return **HTTP 403** through this session's egress proxy (re-tested today, host-level policy
> denial — not a GitHub rate limit). Two channels do work and both were used:
> 1. **`gh api -X GET search/repositories`** — this is the GitHub REST API itself, so
>    `license.spdx_id`, `stargazers_count`, `forks_count`, `pushed_at`, `created_at` and
>    `open_issues_count` below are **first-hand API fields**, not scraped numbers. Every repo in this
>    section was re-queried by exact `repo:owner/name` and **returned**; a 404 would have returned
>    nothing. 39 of 39 resolved.
> 2. **rendered repository page** (for README substance) and **`raw.githubusercontent.com`** (for the
>    LICENSE file byte-for-byte, which is how `AWSIM` was settled below).
>
> `huggingface.co` still does not resolve in this session, so **no model-weight licence was verified
> first-hand** this pass either. Weights claims stay labelled unverified.

### 1. 🆕 The headline: the automotive agent layer is no longer a 0–26★ curiosity. It is 2,907★, and it is a *compliance* agent, not a driving agent.

For four passes this KB has recorded the automotive agent layer as real but tiny — "0–8 stars",
then "0–26 stars". That framing is now wrong, and it was wrong because the KB was looking in the
vehicle and not in the engineering office.

**[jherrodthomas/automotive-skills-suite](https://github.com/jherrodthomas/automotive-skills-suite)** —
**MIT, 2,907★, 141 forks**, created 2026-05-01, last push 2026-10-16 — is **two orders of magnitude
larger than anything previously recorded in this category**. It is 76 *builder + reviewer* skill pairs
(the About line says "100+", the page header says 152 — the count is inconsistent on the repo's own
page, recorded here as found) covering, read from the rendered page:

- **ISO 26262** functional safety — HARA, FSC/TSC, hardware and software lanes, FMEDA, safety case
- **ISO/SAE 21434** cybersecurity — TARA, cybersecurity goals, incident response, secure coding
- **ISO 21448 (SOTIF)** for ADAS/AV
- **AIAG-VDA / IATF 16949** — APQP, DFMEA, PFMEA, control plans, PPAP
- **Automotive SPICE** — assessment, gap analysis, improvement plans
- **Bus & diagnostics** — CAN/DBC, LIN, FlexRay, automotive Ethernet, K-Matrix, bus load, gateway
  routing; UDS, DTCs, CDD, ODX, DEM configuration
- **AUTOSAR** Classic and Adaptive; **calibration** (A2L, DCM); **MBSE/SysML**; **V&V** with
  traceability matrices; programme management (risk registers, gate reviews, change impact)

Each builder takes JSON input plus an upstream artefact and **emits `.xlsx`**; each builder is paired
with a reviewer skill that checks the builder's output and produces a dashboard, and **reviewers never
modify source artefacts** — gaps become recommended actions. Installation is "Save skill" in Cowork or
Claude Desktop; **the page does not mention Claude Code or any non-Claude runtime.**

**Why this matters more than its star count:** this is the *deliverable* side of an automotive
engagement, not the vehicle side. It is the artefact pack a Tier-1 programme actually ships.

**🔴 Engagement risk, stated plainly:** the repository page carries **no disclaimer that outputs are
not certified** and no statement that a qualified engineer must validate them — while advertising
coverage of six safety/quality standards and the word "compliance". Treat generated artefacts as
**drafts for a named responsible engineer to own**. Do not let a client see an ISO 26262 safety-case
spreadsheet whose provenance is an unreviewed skill run. See `compose/patterns.md` → **P14**.

### 2. 🆕 "Assurance-as-code" is now a category, not an anecdote — three independent projects, one of them created today

| Repo | Licence | ★ / forks | Created | What it actually ships |
|---|---|---|---|---|
| [jherrodthomas/automotive-skills-suite](https://github.com/jherrodthomas/automotive-skills-suite) | **MIT** | 2,907★ / 141f | 2026-05-01 | 76 builder+reviewer skill pairs → `.xlsx` artefacts across ISO 26262 / 21434 / 21448 / ASPICE / AIAG-VDA |
| [jherrodthomas/LionDriver](https://github.com/jherrodthomas/LionDriver) | **MIT** | 65★ / 3f | 2026-10-09 | openpilot derivative carrying a **living safety case: 36 claims, 50 evidence items, 42 open defeaters, 0 accepted**; 89 V-cycle work products (85 draft, 4 skeleton) |
| [Lieubk/automotive-safety-security-assurance-kit](https://github.com/Lieubk/automotive-safety-security-assurance-kit) | **MIT** | 2★ / 0f | **2026-11-19 (today)** | Claude Code skills, agents and a **trace engine** for Automotive SPICE 3.1/4.0, ISO 26262, ISO/SAE 21434 — "the toolkit drafts and checks; people decide" |

**The contrast between rows 1 and 2 is the finding.** Same author, same month, opposite epistemics:

- **LionDriver** cites ISO 26262, ISO 21448, ISO/SAE 21434, **ISO/PAS 8800**, **UL 4600** and
  Automotive SPICE, and then **explicitly claims no compliance, because no assessment has been
  performed**. It publishes **42 unresolved defeaters** against its own safety case, says no release
  build exists, says development builds must not be used on public roads outside a controlled test
  regime, names its first *evaluated* configuration (**Toyota Corolla E210**) and states that **no
  configuration is yet assurance-supported**. Its field-monitoring process has a first live case tied
  to **NHTSA PE26007**. Automated checks of inherited safety code run in CI but are **not yet reviewed
  as evidence**.
- **automotive-skills-suite** has 45× the stars and none of that hedging.

For a studio, LionDriver is the better *template* and the skills suite is the better *tool*. Row 3
(created today, 2★) matters only as the third independent data point: **two projects is a coincidence,
three in six weeks is a category.** Expect clients to arrive holding one of these.

### 3. 🆕 Agents now drive real cars, on a published harness, with a hard speed ceiling — this closes a standing gap

**[aditya-ramabadran/drivingbench_harness_code](https://github.com/aditya-ramabadran/drivingbench_harness_code)**
— **MIT, 63★, 8 forks**, created 2026-09-18, pushed 2026-11-11. Earlier passes recorded that there was
no benchmark in which an LLM agent actually actuates a vehicle. There is now.

- **MCP server name:** `drivingbench_sandbox`. Three tools, read from the page:
  `observe()` → road image(s) + state summary (speed, measured steering, whether a command is
  executing, timestamp, **image age**); `set_motion(direction, steering_pct 0–100, speed 0.5–3.5 m/s,
  duration 5–60 s, reason)` where **the `reason` string is logged for the operator and never sent to
  the controller**; `stop_now()` → cancel + brake.
- **Safety envelope:** operator-set speed ceiling (**default 3 m/s**), **hard cutoff at 6 m/s**,
  command expiry, and cancellation on brake / gas / steering override / disengagement. Described as
  *"research software for closed courses"*, parking-lot speed, human supervising.
- **Real platforms:** a **comma four** on a pinned openpilot build (upstream `59fcd340`); a **Toyota
  with torque steering** (recent TSS2, developed on a Corolla); a **Tesla Model 3 HW3** with angle
  steering. Laptop side: macOS + Python 3.12 + `uv`; Linux can run the gateway in the foreground.
- **Simulator:** the v1.1 course as a **Gaussian splat**, real control stack over a Tesla model fitted
  from logs, scored on progress / cone contacts / finish exactly as the real car. Runs with placeholder
  frames if you have no splat.
- **Three client classes benchmarked:** chat models via MCP clients (Codex, Claude Code, Cursor); API
  models via a runner loop (OpenRouter, Gemini API); and **trained driving policies / VLAs served over
  HTTP returning timed curvature + speed plans** — so an open VLA and a chat model compete on one
  harness.
- **Traces:** every tool call, telemetry sample, settings change and **image the model saw** is
  recorded and replayable in a browser viewer.
- ⚠️ **No results and no leaderboard are published on the repository page.** It links `drivingbench.com`;
  no scores are visible, Releases is empty. So this is a **harness finding, not a ranking finding** —
  do not quote a DrivingBench score to a client.

The `reason`-is-never-sent design and the image-age field are the two details worth copying into any
Globant vehicle-agent architecture: the first stops prompt text reaching an actuator, the second makes
staleness a first-class input.

### 4. 🆕 The openpilot ecosystem is a layer, and the hardware bundle is coming apart

Previous passes treated openpilot as a single row. It is a supply chain, and this pass it visibly
*unbundled from comma's hardware*:

| Repo | Licence | ★ / forks | What it is |
|---|---|---|---|
| [commaai/openpilot](https://github.com/commaai/openpilot) | **MIT** | **64,177★** / 11,410f | The anchor. 300+ supported cars. Pushed 2026-11-19. |
| [sunnypilot/sunnypilot](https://github.com/sunnypilot/sunnypilot) | **MIT** | 2,178★ / — | 350+ makes/models, tracks comma's safety policy |
| [zoompilot/jetlink](https://github.com/zoompilot/jetlink) | **MIT** | 57★ / **40f** | **Runs openpilot's large driving model on Jetson Orin Nano, macOS, iOS, Android and CUDA laptops** with only a comma device and a USB3 cable |
| [zoompilot/zoompilot](https://github.com/zoompilot/zoompilot) | **MIT** | 37★ / 31f | Driver-assistance for **Mazda** and others; pushed 2026-11-19 |
| [StarPilotHQ/StarPilot](https://github.com/StarPilotHQ/StarPilot) | **MIT** | 163★ | Tuning-focused fork |
| [YassineYousfi/openpilot.distill](https://github.com/YassineYousfi/openpilot.distill) | **MIT** | 38★ | **Distil openpilot using your own drives** |
| [commaai/connect](https://github.com/commaai/connect) | **MIT** | 153★ | Fleet/experience management for openpilot |

**Read `jetlink`'s fork-to-star ratio (40 forks on 57 stars).** That is a *build* signal, not a
bookmarking signal — people are porting it. Combined with `openpilot.distill`, the MIT driving model is
becoming portable to hardware a client already owns. For a Globant engagement this moves "can we run a
real driving model on the client's compute?" from a research question to an integration question.

### 5. 🆕 The vehicle-data MCP layer grew a 142★ leader, and the useful ones are read-only by default

| Repo | Licence | ★ | What it exposes |
|---|---|---|---|
| [cobanov/teslamate-mcp](https://github.com/cobanov/teslamate-mcp) | **MIT** | **142★** / 25f | Queries a **TeslaMate** database — drive/charge history and analytics. **Now the largest automotive MCP server recorded in this KB.** 0 open issues. |
| [cyanheads/nhtsa-vehicle-safety-mcp-server](https://github.com/cyanheads/nhtsa-vehicle-safety-mcp-server) | **Apache-2.0** | 3★ | **VIN decode, recalls, complaints, crash ratings, investigations** over NHTSA data. STDIO or Streamable HTTP. |
| [AbbottDevelopments/shopmonkey-mcp-server](https://github.com/AbbottDevelopments/shopmonkey-mcp-server) | **MIT** | 3★ / 8f | **69 tools** over the Shopmonkey REST API v3 — work orders, customers, vehicles, inventory, appointments, labour |
| [october-dev/car-use](https://github.com/october-dev/car-use) | **MIT** | 7★ | "Let your agent use your car" — reads and diagnoses real cars over **OBD-II**, with a **built-in virtual car**. 36 open issues (very young, created 2026-11-11). |
| [christianOrona/wtfault-scanner](https://github.com/christianOrona/wtfault-scanner) | **Apache-2.0** | 3★ | Agentic OBD-II scanner, *"never makes anything up"* — reads every module on the bus and **every number is clickable back to the raw bytes** |
| [Sherin-SEF-AI/CanLab](https://github.com/Sherin-SEF-AI/CanLab) | **MIT** | 94★ / 9f | CAN-capture reverse engineering: finds counters/checksums/signal boundaries, DBC builder verified against real frames, exports **DBC + openpilot + Wireshark** dissectors. **Injection is bench-only and stays disarmed until armed.** |
| [bpawnzZ/lemonwrench](https://github.com/bpawnzZ/lemonwrench) | **MIT** | 21★ | Agent skill: **free OEM service manuals → procedure, torque table, labelled figures. 69 makes, 1960–2025.** |
| [zimconsulting-ops/med-vehicle-intelligence](https://github.com/zimconsulting-ops/med-vehicle-intelligence) | **MIT** | 1★ | 4-tool repair/maintenance advisory MCP server |

The **design convention has settled**: read-only by default, injection/actuation explicitly disarmed,
provenance clickable to raw bytes. `wtfault-scanner` and `CanLab` are the two to copy. This is the same
human-gate pattern recorded as **T8** in `intel/trends.md`, now visible in the code rather than the
README.

### 6. 🆕 Cockpit, requirements and procurement agents — the non-driving automotive agent spread

| Repo | Licence | ★ | Role |
|---|---|---|---|
| [yancent-dao/cockpit-agent-sim](https://github.com/yancent-dao/cockpit-agent-sim) | **MIT** | 98★ | Smart-cockpit agent framework (CN): zero-backend, **tiered permissions, confirmation flow**, card orchestration, **fast/slow dual-layer**, real third-party integrations; "add a capability = add data, not code" |
| [yorkeccak/takt](https://github.com/yorkeccak/takt) | **MIT** | 19★ | Deep-research agent for **automotive procurement and R&D** — one prompt → board-ready PDF/PPTX/DOCX/CSV from 100+ sources (patents, SEC filings, papers) |
| [BUAksakal/reqlens](https://github.com/BUAksakal/reqlens) | **MIT** | 3★ | **LangGraph supervisor + LlamaIndex RAG** agents extract requirements from PDF specs and flag conflicts and vague wording, **engineer in the loop** |
| [aws-samples/sample-manufacturing-automotive-ai-toolkit](https://github.com/aws-samples/sample-manufacturing-automotive-ai-toolkit) | **MIT-0** | 19★ / 7f | **First hyperscaler-published** automotive + manufacturing agent sample set. **MIT-0 = no attribution requirement**, the most permissive licence in this KB. |
| [LeventKent/automotive-sdlc-agent-for-mil-sil-hil](https://github.com/LeventKent/automotive-sdlc-agent-for-mil-sil-hil) | **MIT** | 2★ | V-model MIL/SIL/HIL tooling agent |
| [ThinkOffApp/CarWatch](https://github.com/ThinkOffApp/CarWatch) | 🔴 **AGPL-3.0** | **306★** / 20f | "Your car as a chat-room agent": Raspberry Pi 5 + dashcam + local AI. **Highest-starred automotive agent after the skills suite — and unusable in a client deliverable.** |

`cockpit-agent-sim`'s **fast/slow dual layer + confirmation flow + tiered permissions** is the most
directly reusable in-vehicle HMI agent architecture found so far, and it is MIT.

### 7. 🆕 Driving-policy and world-model layer — this is where APAC and the labs are

| Repo | Licence | ★ | Venue / note |
|---|---|---|---|
| [xiaomi-research/recogdrive](https://github.com/xiaomi-research/recogdrive) | **Apache-2.0** | **631★** / 78f | **ICLR 2026** — reinforced cognitive framework for end-to-end AD. **Xiaomi Research.** Pushed 2026-11-19. |
| [nv-tlabs/omni-dreams](https://github.com/nv-tlabs/omni-dreams) | **Apache-2.0** | 367★ | **NVIDIA OmniDreams** — world model generating photorealistic AV-sim video **in real time** |
| [LMD0311/HERMES](https://github.com/LMD0311/HERMES) | **Apache-2.0** | 265★ | ICCV 2025 — unified driving world model, 3D understanding + generation |
| [H-EmbodVis/SimWAM](https://github.com/H-EmbodVis/SimWAM) | **MIT** (LICENSE read raw; GitHub API says `NOASSERTION`) | 212★ | Simple World Action Model for E2E AD |
| [curryqka/AgentThink](https://github.com/curryqka/AgentThink) | **Apache-2.0** | 154★ | **EMNLP 2025** — agent-style VQA for autonomous driving |
| [TabGuigui/WorldDrive](https://github.com/TabGuigui/WorldDrive) | **Apache-2.0** | 85★ | **NeurIPS 2026** — unifies scene generation and planning |
| [AFARI-Research/WA-JEPA](https://github.com/AFARI-Research/WA-JEPA) | **Apache-2.0** | 89★ | Video-JEPA rethought for world-action modelling |
| [HaoranZhuExplorer/AD-E2E-JEPA](https://github.com/HaoranZhuExplorer/AD-E2E-JEPA) | **Apache-2.0** | 82★ | JEPA for E2E AD |
| [H-EmbodVis/HERMESV2](https://github.com/H-EmbodVis/HERMESV2) | **Apache-2.0** | 73★ | **IEEE TPAMI** — HERMES++ |
| [chenshi3/DriveWAM](https://github.com/chenshi3/DriveWAM) | **Apache-2.0** | 70★ | **NeurIPS 2026** — video generative priors for world-action modelling |
| [ASGuard-UCI/safedrive-vla](https://github.com/ASGuard-UCI/safedrive-vla) | **Apache-2.0** | 36★ | **CoRL 2026** — navigation-conditioned world-model dreaming, conflict-aware |
| [OpenDriveLab/ViRA](https://github.com/OpenDriveLab/ViRA) | **Apache-2.0** | 38★ | *"Do better visual representations always lead to better end-to-end AD?"* |
| [FrankRun/WCog-VLA](https://github.com/FrankRun/WCog-VLA) | 🔴 **no licence** | 76★ | Dual-level world-cognitive VLA — **do not use** |
| [xiongqi123123/MarginAD](https://github.com/xiongqi123123/MarginAD) | 🔴 **no licence** | 41★ | Safety- and physics-aware planning — **do not use** |

**Apache-2.0 is now the overwhelming default in this layer** (11 of 14 rows), which is a change worth
recording: the research tier has become *licence-safe by convention*. The two no-licence rows are
listed so nobody re-searches them.

### 8. 🆕 Survey/index layer — the cheapest way to stay current between passes

| Repo | Licence | ★ | Why track it |
|---|---|---|---|
| 🆕 [TUM-AVS/FM-AD-Survey](https://github.com/TUM-AVS/FM-AD-Survey) | **Apache-2.0** (`LICENSE` byte-read 2026-11-21, 11,337 bytes — full canonical text) | **249★** | **New to this KB, and it is the academically strongest index in this layer.** Foundation-models-for-autonomous-driving survey from **TU Munich's Autonomous Vehicle Systems chair** — a named university group rather than an anonymous awesome-list, which is why it is worth tracking separately from the lists above. **Pushed 2026-11-19, i.e. actively maintained.** Use it as the between-pass reading list for the VLA/world-model layer in section 7. |
| [Thinklab-SJTU/Awesome-LLM4AD](https://github.com/Thinklab-SJTU/Awesome-LLM4AD) | **Apache-2.0** | **1,906★** / 115f | LLM/VLM/VLA/world-model for AD, continually updated. **The single best map of this space.** |
| [iDoka/awesome-canbus](https://github.com/iDoka/awesome-canbus) | **CC0-1.0** | **3,571★** / 426f | CAN bus tools, hardware, resources — security/RE oriented |
| [worldbench/awesome-3d-4d-world-models](https://github.com/worldbench/awesome-3d-4d-world-models) | **Apache-2.0** | 1,031★ | **TPAMI 2026** survey of 3D/4D world modelling |
| [leofan90/Awesome-World-Models](https://github.com/leofan90/Awesome-World-Models) | **BSD-3-Clause** | 2,059★ | World models incl. AD |
| [LMD0311/Awesome-World-Model](https://github.com/LMD0311/Awesome-World-Model) | 🔴 no licence | 2,304★ | Reference only — **do not vendor the list** |
| [Little-Podi/Collaborative_Perception](https://github.com/Little-Podi/Collaborative_Perception) | 🔴 no licence | 639★ | V2I/V2V/V2X cooperative-perception digest. Reference only. |
| [szenergy/awesome-lidar](https://github.com/szenergy/awesome-lidar) | **CC0-1.0** | 1,373★ | LiDAR vendors, datasets, algorithms |
| [RYNing/Awesome-Post-Training-In-Autonomous-Driving-Papers](https://github.com/RYNing/Awesome-Post-Training-In-Autonomous-Driving-Papers) | `NOASSERTION` | 43★ | Post-training for E2E AD — distillation, preference alignment, RL, test-time refinement. Supports **T3**. |

### 9. 🔴 Licence findings that change a decision this pass

1. **`autowarefoundation/AWSIM` is NOT Apache-2.0.** The GitHub API reports `NOASSERTION`; the LICENSE
   file fetched raw from `raw.githubusercontent.com/autowarefoundation/AWSIM/main/LICENSE` begins
   *"AWSIM Licenses — AWSIM License Applies to autowarefoundation/AWSIM repositories and all content
   contained in the Releases"*. It is a **bespoke licence**, 765★/163f. Autoware itself
   (Apache-2.0) and `autoware_universe` (Apache-2.0) are unaffected. **Read the AWSIM terms before any
   client simulation deliverable depends on it.**
2. **`auto-agent-protocol/auto-agent-protocol`** — API reports `NOASSERTION`; the LICENSE file at
   `main` is the **Apache License 2.0 verbatim**. GitHub's classifier is producing a false negative,
   as recorded on 2026-11-13 for other repos. Figures today: **112★, pushed 2026-11-19.**
   Still: confirm there is no second licence file before relying on it.
3. **🆕 Name collision, and it is a procurement hazard.**
   [visionpilot-project/VisionPilot](https://github.com/visionpilot-project/VisionPilot) — **MIT, 43★**,
   a BeamNG.tech-based modular AD *simulation* platform with Foxglove visualisation — is **a different
   project** from
   [autowarefoundation/vision_pilot](https://github.com/autowarefoundation/vision_pilot) —
   **Apache-2.0, 928★/197f**, the productionizable L2 ADAS stack. Different owners, different licences,
   different purpose, near-identical names. **Always paste the full `owner/name`** in a statement of
   work.
4. **`TOSUN-Shanghai/TSMaster`** — **LGPL-2.1, 442★** — bus monitoring/simulation/diagnostics/
   calibration across Vector, IXXAT, PEAK, Kvaser and others. The page states it is **free for research
   and education for some features**. LGPL **plus** feature-gating: treat as a tool, never as a
   component of a shipped product.
5. **`ThinkOffApp/CarWatch` — AGPL-3.0, 306★.** Strong network copyleft. Reference architecture only.

### 10. 🔴 Declared gaps 2026-11-19 — searched, found nothing, recorded so nobody re-runs it

These are **informed gaps**, with the query that produced them:

| Query run (`gh api search/repositories`) | Result |
|---|---|
| `EV battery charging AI in:name,description pushed:>2026-08-01 stars:>15` | **0 repos.** There is no maintained, non-trivial open EV-charging/battery-AI project above 15★ in the last quarter. |
| `automotive manufacturing quality inspection AI in:name,description pushed:>2026-06-01 stars:>3` | **0 repos.** The plant-floor vision/quality layer is **entirely proprietary** in open source terms. |
| `fleet management telematics in:name,description pushed:>2026-08-01 stars:>5` | **2 repos only** (`openremote/fleet-management` 51★ `NOASSERTION`; `santoshiimind/fleet-management-system` Apache-2.0 8★). Confirms the telematics gap for a fifth pass. |
| `car dealership management in:name,description,topics pushed:>2026-01-01` | 408 repos, **highest star count = 5**, overwhelmingly unlicensed student projects. **The DMS gap is re-confirmed with a fresh query** — see `verticals/solutions.md`. |
| Region of origin, automotive agents | **No LATAM-origin automotive AI repository was found in any query this pass.** Origins observed: US, China, Germany, Türkiye, Korea, India. This is a real gap, not an absence of searching — see `intel/market.md` → LATAM. |
| Model weights | `huggingface.co` does not resolve through this session's proxy. **No weight licence verified first-hand.** |

## What changed on 2026-11-13

1. 🆕 **The headline: there is now a credible Apache-2.0 production L2 ADAS stack, and it is not a research
   model.** `autowarefoundation/vision_pilot` — **Apache-2.0, 927★, 196 forks, 4,282 commits** — is
   *"a productionizable and safety certifiable implementation of an open-source L2 ADAS system."* It ships
   **ACC, FCW, AEB, LKAS, LDW, ISA and single-lane hands-free highway Autopilot**, runs **mapless** (no HD
   maps), and its roadmap names **ISO 26262 and ISO 8800** verification. For four passes this KB has said
   the only large permissive automotive codebase was openpilot (MIT). That is no longer the only one, and
   the new one is **Apache-2.0 and foundation-governed**.
2. 🆕 **The Autoware Foundation shipped an entire E2E model zoo in three days (10–12 Nov 2026).** Not one
   release: `vision_pilot`, `alpamayo-autoware`, `autoware_latent_drive`, `scene_3d`, `ego_lanes`,
   `autoware.trucks`, plus `agnocast` infrastructure. Eight repositories verified below. The open E2E
   driving field stopped being "a few competing models" and became **one vendor-neutral org publishing a
   stack**.
3. 🔴 **And one of them cannot be used.** `autoware_latent_drive` (42★) has **no licence**: no sidebar
   field, no statement in the README, and `LICENSE`, `LICENSE.md`, `LICENSE.txt` and `license.rst` all
   **404 on `main`**. It is the third instance of this exact defect in this KB (after `j2534-mcp-server`
   and, in the education KB, `mcp-canvas-lms`) — and the first time it has happened **inside a major
   foundation's own org**. A repository being published by the Autoware Foundation is not a licence.
4. 🟢 **A GitHub "Other" licence label was wrong, and reading the file fixed it.**
   `autoware-safety-island` (8★, 608 commits) shows as **"Other"** in the org listing because its licence
   lives in **`license.rst`**, not `LICENSE`. Fetched raw, it is **verbatim Apache License 2.0**. Shelved
   as Apache-2.0. GitHub's detector is not the licence.
5. 🆕 **The diagnostics-agent category got its first double-digit-star real agent, and it moved under a new
   name.** `farzadnadiri/mcp-can` — the URL every search result still gives — **now resolves to
   `farzadnadiri/Peykan`** (MIT, 26★). A rename, same defect class as the `openedx/edx-platform` →
   `openedx/openedx-platform` rename this pipeline recorded in the education KB. **26★ makes it the
   highest-starred actual diagnostic agent found in four passes** (Auto Agent Protocol's 110★ is a *spec*,
   not an agent).
6. ⬆️ **openpilot 64.0k → 64.1k**, and it now says **300+** supported cars. 🆕 Its fork
   **`sunnypilot/sunnypilot` (MIT, 2.2k★, 19,012 commits) claims 350+ car makes and models** — more
   vehicle coverage than upstream, under the same MIT grant. This KB had no row for it.
7. 🔄 **Autoware 12.2k★ — unchanged** from 2026-10-31.

## Headline finding — revised this pass

For three passes this KB recorded: *"the automotive AI agent category is not where the permissively-licensed
value is; the buildable assets are driving policies and SDV infrastructure."* **That is now half wrong, and
the half that changed is the important one.**

Repeating the mandated searches (`top open source AI agents automotive 2026 github MIT`,
`github trending automotive AI 2026`) *still* returns general-purpose agent frameworks with no automotive
content — OpenClaw, OpenCode, OpenHands, CrewAI, Hermes Agent, AutoGPT (the last reported **archived
28 Jan 2026**). The generic-agent search channel remains a dead end for this industry and should be
treated as such.

**But the industry-specific channel is now productive.** Searching for the *mechanism* rather than the
category — `automotive MCP server vehicle diagnostics agent open source github 2026` — returned **eight
distinct vehicle-diagnostics MCP servers**, five of which this KB had no row for. The lesson for the next
pass is methodological: **in automotive, search the protocol, not the buzzword.**

## Production & reference ADAS stacks

| Agent / stack | Repo | Licence | Stars | What it is |
|---|---|---|--:|---|
| 🆕🔄 **Vision Pilot** | [autowarefoundation/vision_pilot](https://github.com/autowarefoundation/vision_pilot) | Apache-2.0 | 927 | **The most consequential new row in this KB this pass.** *"Free and fully open-source L2 ADAS stack powered by End-to-End AI technology"* — and in the README, *"a productionizable and safety certifiable implementation."* Features: **ACC, FCW, AEB, LKAS, LDW, ISA, single-lane hands-free highway Autopilot**, **mapless** (no 3D HD maps). Architecture is a *"Hybrid End-to-End AI Architecture"*: data *"processed in parallel by perception AI models for safety, and End-to-End AI models for performance"* — three models: **AutoSpeed** (closest in-path object), **AutoSteer** (ego path waypoints), **AutoDrive** (E2E distance + in-path presence + road curvature). Input: **a single front monocular camera, 52–55° HFOV, 1–2 MP**. Runs on **ONNX Runtime**, GPU (CUDA) or **CPU**, Docker, optional ROS 2, closed-loop in **CARLA 0.9.16**. v1.0 artifacts (`VisionPilot-1.0-x86_64.deb`). Roadmap: radar fusion, 8 MP/120° camera, **ISO 26262 + ISO 8800**. 196 forks, 4,282 commits. ⚠️ "Safety certifiable" is an aspiration — certification is a roadmap item, not a status. Note the README's clone command says `autoware_vision_pilot.git` while the repo is `vision_pilot`. |
| 🔄 **openpilot** | [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | 64.1k | *"openpilot is an operating system for robotics. Currently, it upgrades the driver assistance system on 300+ supported cars."* Still the largest permissive automotive codebase. 64.0k → **64.1k** this pass. |
| 🆕 **sunnypilot** | [sunnypilot/sunnypilot](https://github.com/sunnypilot/sunnypilot) | MIT | 2.2k | *"sunnypilot is an open source driver assistance system."* The significant openpilot fork, **MIT like upstream**, and it advertises *"over 350 supported car makes and models"* — **broader vehicle coverage than openpilot's own 300+**. 19,012 commits. For an engagement whose blocker is "is this client's vehicle supported", the fork may answer yes where upstream answers no. |
| 🔄 **Autoware** | [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | Apache-2.0 | 12.2k | *"Autoware - the world's leading open-source software project for autonomous driving."* ROS 2 based, vendor-neutral foundation governance. Unchanged this pass. |
| 🔄 **Apollo** | [ApolloAuto/apollo](https://github.com/ApolloAuto/apollo) | Apache-2.0 | 26.9k | Baidu's open AV platform; README line is **Apollo 11.0**, *"focuses on the large-scale deployment of functional autonomous vehicles."* ⚠️ Partially open — HD maps and cloud services retained. Figures carried from 2026-10-31. |
| 🆕 **autoware.trucks** | [autowarefoundation/autoware.trucks](https://github.com/autowarefoundation/autoware.trucks) | Apache-2.0 | 2 | *"Everything specific to trucking autonomy."* README: an open-source system for **highway trucking autonomy, starting at SAE Level 2+ highway piloting and working toward Level 4**. 9 commits — this is a charter, not a codebase, and is listed as a **watch item** because trucking is where North American autonomy money is actually moving (see Kodiak in `intel/market.md`). |

## Driving policies & VLA models

| Agent / model | Repo | Licence | Stars | What it is |
|---|---|---|--:|---|
| 🆕 **SGDrive** | [LogosIntelligenceLab/SGDrive](https://github.com/LogosIntelligenceLab/SGDrive) | **MIT** (`LICENSE` byte-read 2026-11-21, 1,077 bytes, *"Copyright (c) 2025 Logos Robotics Group"*) | 81 | **New to this KB.** CVPR-2026-cited driving model from Logos Robotics Group. **The reason to care is the licence, not the star count: MIT is the most permissive grant in this entire table** — every other model row here is Apache-2.0 at best, and several carry no grant at all. For a client deliverable that must be sublicensed or shipped inside a proprietary stack, **an 81★ MIT model can be worth more than an 800★ Apache-2.0 one**. Last pushed 2026-10-23. ⚠️ Small project, single-org provenance, no independent reproduction found — treat as a licence-safe starting point, not a production policy. |
| 🆕 **alpamayo-autoware** | [autowarefoundation/alpamayo-autoware](https://github.com/autowarefoundation/alpamayo-autoware) | Apache-2.0 | 161 | **Autoware Foundation's fork of `NVlabs/alpamayo`**, updated 11 Nov 2026, default branch **`alpamayo2.0-edge`**, 42 commits, no description set. Significant as *governance*, not as new science: the vendor-neutral foundation is now carrying its own edge branch of NVIDIA's model rather than consuming releases. If you build on Alpamayo for a client who cares about vendor neutrality, **this is the fork to track**. |
| 🆕 **autoware_latent_drive** | [autowarefoundation/autoware_latent_drive](https://github.com/autowarefoundation/autoware_latent_drive) | 🔴 **NO LICENCE** — see exclusions | 42 | Listed here for findability and **excluded from use below**. LatentDrive: a **camera-only** E2E planner whose video encoder is a **V-JEPA ViT-L**, planning *"in that latent space"* with *"no object detection or tracking in between"*. Takes the **last 2 s of front-camera video + six route points + ego motion**, outputs a **4 s ego trajectory at 10 Hz**. Ships a **TensorRT C++ inference library with no ROS dependency**, plus an offline sample and a ROS 2 node. Targets ROS 2 Jazzy, CUDA 13.0, TensorRT 10.13. Two ONNX models on HF (3-camera and 1-camera). README: *"This is a research model: it is not a certified driving system and must not control a vehicle on public roads."* **No benchmarks** — evidence is qualitative open-loop replay; the plan *"is drawn, not executed."* |
| 🆕 **Senna** | [hustvl/Senna](https://github.com/hustvl/Senna) | Apache-2.0 | 559 | *"[IJCV 2026] Senna: Bridging Large Vision-Language Models and End-to-End Autonomous Driving."* A peer-reviewed (IJCV 2026) VLM↔E2E bridge from HUST's vision lab — the academic line alongside OpenDriveVLA, and a useful second opinion on how to attach a language model to a planner without replacing it. 16 commits. |
| ⏸ **Alpamayo 2 Super** | [NVlabs/alpamayo2](https://github.com/NVlabs/alpamayo2) | Apache-2.0 | 287 | Open **34B** multi-task AV foundation model: 32B VLM backbone + 2B diffusion expert. Largest open AV model in this KB. Figures carried from 2026-10-31. |
| ⏸ **Alpamayo 1.5** | [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) | Apache-2.0 (code) · ⚠️ **OpenMDW-1.1 (weights)** | 370 | Open 10B reasoning VLA: RL-enhanced reasoning, navigation guidance, VQA. The practical starting point of NVIDIA's line and the one the published recipes target. |
| ⏸ **Alpamayo 1 Nano** | [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) | Apache-2.0 | 2.1k | Original 10B reasoning VLA, driving trajectories + Chain-of-Causation reasoning. ⚠️ Banner: *"no longer under active development and will receive only limited maintenance updates."* **Do not start here** — start from `alpamayo-autoware` or `alpamayo2`. |
| ⏸ **Alpamayo Recipes** | [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | Apache-2.0 | 217 | The developer hub: Alpamayo 1 / 1.5 SFT (HF Trainer + DeepSpeed), 1.x RL post-training (Cosmos-RL + GRPO), **1.5 quantization (FP8, NVFP4+FP8 mixed)** via Model Optimizer Toolkit, dataset curation and checkpoint conversion. |
| ⏸ **OpenDriveVLA** | [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) | Apache-2.0 | 824 | **[AAAI 2026]** E2E driving with a large VLA. A **0.5B checkpoint** is published — the smallest open AV VLA here, so the realistic candidate where Alpamayo needs ≥24 GB VRAM. |
| ⏸ **AutoE2E v1.0** | [autowarefoundation/auto_e2e](https://github.com/autowarefoundation/auto_e2e) | Apache-2.0 (`LICENSE` read raw 2026-10-31) | 184 | Autoware Foundation's camera-first E2E model, first tagged 29 Oct 2026. **79.9M parameters**, six surround cameras at 10 Hz → BEV grid, optional map raster, GRU planner emitting **6.4 s of acceleration and curvature**. ~76 FPS (SwinV2-Tiny, RTX 5080, batch 1 — project's own figure). Org listing shows it updated **10 Nov 2026**. |
| ⏸ **Qwen-Drive-1.0** | [QwenLM/Qwen-Drive-1.0](https://github.com/QwenLM/Qwen-Drive-1.0) | Apache-2.0 | 537 | Alibaba's **Qwen3.5-4B** VLM + BEV perception head + flow-matching Planning Expert. Leads AutoE2E's own eight-model benchmark (ADE 0.565 m / FDE 1.397 m @ 3 s). The 4B middle rung between OpenDriveVLA (0.5B) and Alpamayo 1.5 (10B). |
| ⏸ **WorldEngine** | [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 528 | Post-training for AD: imitation-learn a base policy, mine failure-prone scenarios from real logs, rebuild with 3D Gaussian Splatting, refine with RL. |
| ⏸ **UniAD** | [OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) | Apache-2.0 | 4.8k | *"[CVPR 2023 Best Paper Award] Planning-oriented Autonomous Driving."* Reference architecture for unified perception→prediction→planning. |
| ⏸ **DriveLM** | [OpenDriveLab/DriveLM](https://github.com/OpenDriveLab/DriveLM) | Apache-2.0 (code) | 1.4k | ECCV 2024 Oral: driving with graph VQA. ⚠️ Language **data** is CC BY-NC-SA 4.0 — non-commercial. Code reusable, dataset not. |

## 🆕 Perception models from the Autoware stack (new layer this pass)

These are the components *under* Vision Pilot. Both are **early** (1–2★) but both are Apache-2.0 and both
are the published pieces of a named foundation model, which makes them more credible than their star
counts suggest.

| Model | Repo | Licence | ★ | What it is |
|---|---|---|--:|---|
| 🆕 **Scene3D** | [autowarefoundation/scene_3d](https://github.com/autowarefoundation/scene_3d) | Apache-2.0 | 2 | *"Open-source AI model for monocular depth estimation."* Produces **high-resolution relative depth maps** (per-pixel nearer/farther) from a single camera. README states it is **part of the AutoSeg Foundation Model, the core of the vision pipeline for the Autoware Autonomous Highway Pilot System**. Includes **Scene3DLite, distilled from DepthAnythingV2** — the distilled variant is the deployable one. 3 commits. |
| 🆕 **EgoLanes** | [autowarefoundation/ego_lanes](https://github.com/autowarefoundation/ego_lanes) | Apache-2.0 | 1 | *"Semantic segmentation and classification of lane lines."* README calls it a *"legacy semantic end-to-end lane boundary segmentation network"* — segments driving lanes from monocular frames **without HD maps**. 30 commits. The word "legacy" is the maintainers' own; treat it as a baseline to beat, not a target. |

## 🆕 Vehicle-diagnostics agents — the category grew, and got its first real contender

Last pass recorded this category as *"real but pre-traction, 0–8★."* It is now **0–26★** and there are
**eight** distinct MCP servers in it. Still small. But the shape changed: there is now one agent with
double-digit stars, a dual-licensed safety-first implementation, and a clear convergence on
**simulator-first** design so the thing can be demonstrated without a vehicle.

| Agent | Repo | Licence | ★ | Region | What it is |
|---|---|---|--:|---|---|
| 🆕 **Peykan** (was `mcp-can`) | [farzadnadiri/Peykan](https://github.com/farzadnadiri/Peykan) | MIT | 26 | EMEA | **Highest-starred real diagnostic agent in this KB.** *"Talk to Your Car Using AI."* Covers **CAN bus, OBD-II, UDS and SAE J1939** — J1939 is the **commercial-vehicle/truck** bus, which no other agent here touches, and it pairs directly with the trucking autonomy line above. Ships a **simulator, a Docker setup and a live dashboard**. 29 commits. 🔴 **Addressing note: every search result still points at `farzadnadiri/mcp-can`, which now resolves to `Peykan`.** Record the new name; the old one will rot. |
| ⏸ **Vehicle Diagnostic Assistant** | [castlebbs/Vehicle-Diagnostic-Assistant](https://github.com/castlebbs/Vehicle-Diagnostic-Assistant) | MIT (`LICENSE` read raw; © 2025 Ghislaine and David Robert) | 8 | EMEA | **Still the most complete reference design in the category.** Gradio UI → **LangGraph** agent (InMemorySaver, UUID sessions) → **MCP server over streamable HTTP / JSON-RPC 2.0** with `get_system_status`, `send_elm327_command`, `get_history`. Sandboxed OBD-II formula evaluator, VIN decoder against the **NHTSA vPIC API**, repair-tutorial search. Hardware: W600-B800 MCU (FreeRTOS + lwIP) → UART 38400 → ELM327 → CAN. |
| 🆕 **obd-mcp-server** | [ayhammouda/obd-mcp-server](https://github.com/ayhammouda/obd-mcp-server) | **Apache-2.0 + MIT (dual — "Apache-2.0, MIT licenses found")** | 1 | Global | *"Safety-first, read-only MCP server for vehicle diagnostics with simulator-first OBD-II, ELM327, and extensible UDS profiles."* The **design** is the contribution: **read-only by construction**, a **deterministic simulator as the default backend**, and **seven typed MCP tools** for discovery, signal reads and DTC reads. Dual Apache-2.0/MIT is the most permissive grant in the category. 19 commits, 1★ — so: borrow the architecture, do not depend on the project. Not on PyPI or the MCP Registry. |
| ⏸ **obd2-mcp** | [shoka-jp/obd2-mcp](https://github.com/shoka-jp/obd2-mcp) | MIT (`LICENSE` read raw; © 2026 Sho Kamakura) | 2 | APAC | *"MCP server: let AI assistants read your car via ELM327 — DTCs, live data, freeze frame, VIN."* **Bundles a mock vehicle, so it runs with no hardware** — still the cheapest way to put a real vehicle-signal tool in front of a client in a workshop. |
| ⏸ **automotive-ai-skills** | [shoka-jp/automotive-ai-skills](https://github.com/shoka-jp/automotive-ai-skills) | MIT (`LICENSE` read raw) | — | APAC | Companion skill pack to `obd2-mcp` from the same author: diagnostics, maintenance, repair, EV topics. Star count not re-read this pass. |
| 🆕 **vehicle-mcp** | [vehicle-platform/vehicle-mcp](https://github.com/vehicle-platform/vehicle-mcp) | MIT | 0 | Global | **A secondary-source correction.** A search summary described this as *"a skeleton, with no code yet."* The repository page contradicts that: **v0.2.0**, a stdio MCP server with `src/vehicle_mcp`, a `tests` directory, **CI workflows**, a table of read-only tools, and **51 commits**. Read-only telemetry, originally aimed at motorcycle projects. 0★. It is small, not empty — and "no code yet" would have been wrong data in this KB. |
| ⏸ **Auto Agent Protocol** | [auto-agent-protocol/auto-agent-protocol](https://github.com/auto-agent-protocol/auto-agent-protocol) | **Apache-2.0** (spec, schemas, code) · docs **CC BY 4.0** | 110 | Global | Not an agent — the **contract agents use to reach a dealership**. Dealer discovery, inventory, evidence, pricing and consented inquiries over **MCP + A2A + PAP**. v3.1 is additive over the published 3.0 contract; AAP 2.x must complete the 3.0 migration first. Discovery = dealer domain publishes an Agent Card, a Poppy document and `llms.txt` pointing at live MCP/A2A/PAP endpoints. Still the only thing here with a governance story. |

**How to read this section in a client conversation — unchanged and now better evidenced.** The plumbing
standardised before the agents arrived: **MCP is settled as the transport** (all eight projects use it),
ELM327/OBD-II, J2534 and now **J1939** are settled as the physical layer, and the convention is converging
on **read-only + simulator-first**. Nobody has built the diagnostic agent that wins. The integration
contracts exist; the differentiated product does not.

## Perception toolboxes

| Toolbox | Repo | Licence | Stars | What it is |
|---|---|---|--:|---|
| ⏸ **mmdetection3d** | [open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) | Apache-2.0 | 6.6k | OpenMMLab's platform for general 3D object detection. |
| ⏸ **OpenPCDet** | [open-mmlab/OpenPCDet](https://github.com/open-mmlab/OpenPCDet) | Apache-2.0 | 5.7k | Toolbox for LiDAR-based 3D object detection. |
| ⏸ **Pylot** | [erdos-project/pylot](https://github.com/erdos-project/pylot) | Apache-2.0 | 535 | Modular AD platform running on CARLA **and real vehicles**. |

## Simulation & closed-loop evaluation

| Tool | Repo | Licence | Stars | What it is |
|---|---|---|--:|---|
| ⏸ **AlpaSim** | [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | AV simulation platform for developing and testing E2E AV policies. Pairs with Alpamayo. |
| ⏸ **AlpaGym** | [NVlabs/alpagym](https://github.com/NVlabs/alpagym) | Apache-2.0 | 163 | RL framework for E2E driving policies; runs closed-loop on AlpaSim. |
| ⏸ **PCLA** | [MasoudJTehrani/PCLA](https://github.com/MasoudJTehrani/PCLA) | Apache-2.0 | 104 | Framework for testing autonomous agents in CARLA. |
| 🆕 **autoware_carla_scenario** | [autowarefoundation/autoware_carla_scenario](https://github.com/autowarefoundation/autoware_carla_scenario) | Apache-2.0 | 0 | Pushed **13 Nov 2026** — today — and **0★ with no description set**, so this is a repository being created as this pass was written. Relevant because Vision Pilot's closed-loop story is **CARLA 0.9.16**, and scenario definitions are what a regression factory (P1) consumes. Watch it; do not plan on it. |

## 🆕 Survey indexes worth tracking (not code, but the best map of the model space)

| Index | Repo | Licence | ★ | What it is |
|---|---|---|--:|---|
| 🆕 **Awesome-VLA4AD** | [JohnsonJiang1996/Awesome-VLA4AD](https://github.com/JohnsonJiang1996/Awesome-VLA4AD) | Apache-2.0 | 631 | Companion repo to the survey *"A Survey on Vision–Language–Action Models for Autonomous Driving."* Groups work into pre-VLA VLM explainers, modular VLA4AD and end-to-end VLA4AD; indexes DriveGPT-4, OpenDriveVLA, DriveMoE, ReCogDrive, SimLingo. |
| 🆕 **awesome-vla-for-ad** | [worldbench/awesome-vla-for-ad](https://github.com/worldbench/awesome-vla-for-ad) | MIT | 524 | *"Vision-Language-Action Models for Autonomous Driving: Past, Present, and Future."* 103 commits; separates vision-action from VLA models; carries 2026 entries (AutoMoT, ChainFlow-VLA, SafeDriveVLA, Scene-Adaptive VLA, HiST-VLA). ⚠️ **At least five near-identical forks of this list exist** (`776styjsu`, `tongnie`, `ruiguoz`, `mengmengliu1998`, `worldbench`) with differing entries. `worldbench` appears to be the upstream (it links `worldbench.github.io/vla4ad`). **Cite the upstream, not whichever fork a search returns** — otherwise this KB acquires five rows for one artefact. |

## ⚠️ Verified but NOT usable — do not queue these for a licence probe

All exist; none can be built on. Re-confirmed or newly probed 2026-11-13.

| Repo | ★ | Licence state | Why it is excluded |
|---|--:|---|---|
| 🆕 [autowarefoundation/autoware_latent_drive](https://github.com/autowarefoundation/autoware_latent_drive) | 42 | 🔴 **NO LICENCE.** No sidebar field; **no licence statement anywhere in the README**; `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `license.rst` **all 404 on `main`** (probed raw, 2026-11-13) | **The most important exclusion this pass, because of who published it.** A V-JEPA-based camera-only latent planner inside the **Autoware Foundation's own org** — and there is no grant. Its sibling `autoware-safety-island` *does* have a licence, in `license.rst`, which proves the org knows how; this repo simply has none. Also self-declared research-only: *"must not control a vehicle on public roads."* **Read as a design reference. Ask the foundation to add the file.** |
| 🆕 [petrpatek/obd2-mcp-server](https://github.com/petrpatek/obd2-mcp-server) | 12 | ⚠️ **README has a "License" section saying MIT; there is NO licence field and no `LICENSE` file** | Connects Claude to OBD-II via `python-obd` and a $15 Bluetooth ELM327; ships a **1,937-code Ford-specific DTC database**, which is the genuinely useful asset here. Only 5 commits. **Identical defect to `j2534-mcp-server` below — a licence sentence in a README is not a grant.** This is now the **third** occurrence of this pattern in the automotive KB alone. |
| 🆕 [RobertSloan22/tars-car-mcp](https://github.com/RobertSloan22/tars-car-mcp) | 0 | 🔴 **No licence field** | Exposes OBD-II, UDS, **GM bidirectional** and CAN diagnostics to Claude. GM bidirectional control is a deep capability — and it is **gated on the proprietary TARS desktop app being installed and running**, so even with a licence it would be a client for closed software. **1 commit.** |
| ⏸ [cyrusdavirusss/j2534-mcp-server](https://github.com/cyrusdavirusss/j2534-mcp-server) | 0 | ⚠️ **README says "MIT"; NO `LICENSE` file** — probed `LICENSE`, `LICENSE.md`, `LICENSE.txt` on `main` and `master`, all 404 | Still the technically deepest agent that cannot be used. J2534 PassThru: adapter control, CAN channels, UDS/OBD-II/KWP2000, DTC lookup, PID decoding; tested on Toyota/Lexus. **J2534 is the professional diagnostic interface** — far deeper into the vehicle than ELM327. |
| ⏸ [carvectorio/carvector-mcp](https://github.com/carvectorio/carvector-mcp) | 1 | MIT (client only) | The MIT grant is real but nearly empty: the client *"bundles no data"*, every call forwards to the keyed CarVector API, and it **exits without `CARVECTOR_API_KEY`**. A proprietary data service with an open client. |
| ⏸ [rgy2291929165-boop/vehicle-diagnosis-agent](https://github.com/rgy2291929165-boop/vehicle-diagnosis-agent) | — | not read | EV fault analysis with RAG + LangGraph + MCP **and a human-approval gate** — the gate pattern this KB recommends, arrived at independently. README calls it a learning project on **simulated data catalogues**. |
| ⏸ [Hemanth-N-code/Connected-Car-AI-Support-Agent](https://github.com/Hemanth-N-code/Connected-Car-AI-Support-Agent) | 0 | **No licence** (README badge: "Academic Evaluation") | LangGraph state machine, intent routing over CRM + telematics + subscription data, ChromaDB RAG over service manuals, human technician sign-off before any vehicle action. Data sources are mock JSON. **Design reference only.** |
| ⏸ [JeffreyYu-Dev/Car](https://github.com/JeffreyYu-Dev/Car) | 0 | **No licence** | LLM vehicle diagnostics, small in-car + large cloud model split. No grant. |
| ⏸ [DatariusAI/AI-in-Automotive](https://github.com/DatariusAI/AI-in-Automotive) | 0 | **No licence** | Daily-refreshed feed of automotive AI papers/code from arXiv and GitHub. Usable as a **reading feed**, not as code — and it is a genuinely good one: it surfaced `hustvl/Senna` above. |

## Licence flags that decide an engagement

- **Clean for a proprietary client deliverable:** 🆕 **Vision Pilot**, 🆕 **alpamayo-autoware**,
  🆕 **Scene3D**, 🆕 **EgoLanes**, 🆕 **autoware.trucks**, 🆕 **agnocast**, 🆕 **autoware-safety-island**,
  🆕 **Senna**, 🆕 **Awesome-VLA4AD** (all Apache-2.0); Autoware, Apollo code, AlpaSim, AlpaGym, Alpamayo
  *code*, Alpamayo 2, OpenDriveVLA, WorldEngine, UniAD, mmdetection3d, OpenPCDet, AutoE2E, Qwen-Drive-1.0,
  Auto Agent Protocol spec/schemas/code (Apache-2.0); openpilot, 🆕 **sunnypilot**, 🆕 **Peykan**,
  🆕 **vehicle-mcp**, 🆕 **awesome-vla-for-ad**, `obd2-mcp`, `automotive-ai-skills`,
  `Vehicle-Diagnostic-Assistant` (MIT); 🆕 **obd-mcp-server** (dual Apache-2.0/MIT).
- 🆕 **Three licence traps that look like grants, all the same shape.** `autoware_latent_drive` (**no file,
  no statement, major foundation**), `petrpatek/obd2-mcp-server` (**README says MIT, no file**),
  `j2534-mcp-server` (**README says MIT, no file**). Plus `tars-car-mcp` (no licence *and* gated on
  proprietary software) and `carvector-mcp` (real MIT, keyed proprietary data). **The recurring rule: read
  the file, not the README, and not the org's reputation.**
- 🆕 **GitHub's licence detector produces false negatives too.** `autoware-safety-island` reads as
  **"Other"** in the org listing purely because the file is named `license.rst`. It is verbatim
  Apache-2.0. A KB that trusts the label loses a usable Apache-2.0 repo; a KB that reads the file keeps it.
  **"Other" is a prompt to fetch the file, not a verdict.**
- **Model-weight licences remain a separate question from code licences.** Alpamayo 1.5's weights are
  **OpenMDW-1.1**, not Apache-2.0. Do not assume a repository badge covers a checkpoint.
- **Non-commercial data traps:** DriveLM's language data (CC BY-NC-SA 4.0), and most AV *datasets*.
  Code licence and dataset licence are routinely different — check both, every time.
- **Documentation can be licensed apart from the spec.** Auto Agent Protocol: Apache-2.0 for spec/schemas/
  code, **CC BY 4.0 for documentation prose**.
- 🆕 **Watch for enterprise carve-outs in "MIT" platforms.** `open-mercato` is MIT with
  `packages/enterprise` under a **separate commercial licence** (see `verticals/solutions.md`). The repo
  badge says MIT; the directory tree says otherwise.

## 🔴 Declared gaps this pass

1. **Model weights still unverified.** `huggingface.co` does not resolve from this session (consistent with
   the proxy's allowed-domain policy), so **no model-weight licence on this page was read first-hand**.
   This matters because the KB has already caught one code/weights split (Alpamayo 1.5) and because
   `autoware_latent_drive`'s training details and both ONNX models live **only** on Hugging Face —
   its repo has no licence, so **the model card is the only place a grant could exist**.
   **Action:** ask for `huggingface.co` to be added to the session's allowed domains. Until then, do not
   ship a fine-tuned derivative of any model on this page.
2. **The TIER IV announcement itself could not be read.** `www.manilatimes.net` does not resolve, and the
   release was reported on 11 Nov 2026 as covering *"multiple end-to-end autonomous driving AI models."*
   The repositories were used as the primary source instead, which is the better source — but the
   announcement's own framing (and any licence statement in it) is **unread**.
3. **No benchmark comparison was published for the new models.** `vision_pilot` ships no benchmark;
   `autoware_latent_drive` explicitly ships none. So the eight-model ADE/FDE table carried in this KB
   from AutoE2E's README on 2026-10-31 is **still the only published multi-model open comparison**, and it
   now covers a *minority* of the available models. **It is ageing, and it was never like-for-like.**

---
*Verified 2026-11-13 (previous pass 2026-10-31). 🆕 = new this pass. 🔄 = licence and stars re-read from the repository page today. ⏸ = carried from an earlier pass with the figures labelled. Stars are GitHub's rounded display values.*

---

## 🆕 Added 2026-11-21 (fourth pass) — in-vehicle diagnostics agents, byte-read

Three real agents, all **MIT** and all byte-read this pass. They were found by **short** `gh` queries
after the long-query defect was identified (`agents/trending.md` → this date). Only the first is a
recommendation; the other two are recorded because a 2026 listicle presents them as current and
**their own bytes say otherwise.**

| Agent | Repo | Licence (byte-read) | ★ / forks | Verdict |
|---|---|---|--:|---|
| 🆕 **CarDash** | [surendranb/CarDash](https://github.com/surendranb/CarDash) | **MIT** — `main/LICENSE`, 1,079 b | **61** / — | ✅ **Use this one.** Android (Kotlin + Jetpack Compose) OBD-II dashboard, **pushed 2026-08-03**. Real-time metrics + deep diagnostics over the OBD-II port, a **persistent local vehicle-health ledger in Room/SQLite**, and **Google Gemini as an on-demand assistant** — i.e. the LLM is a *feature of a working telemetry app*, not the app. Privacy posture is stated in the README and is unusually strong for this category: *"No Account Required"*, *"No Data Collection"*, *"No Analytics"*, *"No Advertisements"*, *"100% Local Storage … Your vehicle data belongs to you alone."* **That architecture — local ledger, cloud LLM only on demand — is the one to copy for any consumer-facing vehicle agent under GDPR or Brazil's LGPD.** |
| 🆕 **Automotive-AI** | [Eloquent-Algorithmics/Automotive-AI](https://github.com/Eloquent-Algorithmics/Automotive-AI) | **MIT** — `main/LICENSE`, 1,061 b | 38 / 14 | ⚠️ **Reference implementation, stale model.** *"Developed to assist in managing day-to-day operations of a mobile automotive diagnostic, and car key replacement business."* Voice-activated hands-free diagnostics: NLP + TTS + STT + an **OBD-II ELM327** dongle, 127 commits. Voice commands are concrete and worth copying as a command surface — `read trouble codes`, `freeze frame data`, `pending trouble codes`, `clear trouble codes`, `engine coolant temperature`, `time run with MIL on`. ⚠️ **README's newest dated entry is 2024-03-17 and it pins `gpt-3.5-turbo-0125`.** The *shape* is current; the model and SDK are two years old. 🔴 **And its documented no-car test path is `Ircama/ELM327-emulator`, which is CC-BY-NC — unusable in a paid engagement.** Substitute `the-can-opener/simple-elm` (MIT) or real hardware. |
| 🆕 **VIA-AI** | [via-intelligent-vision/VIA-AI](https://github.com/via-intelligent-vision/VIA-AI) | **MIT** — `master/LICENSE`, 1,079 b | 59 / 26 | ⛔ **Historical interest only — do not propose.** *"Open source driver assistance app"* with **ACC, LKAS and CAN bus integration** running on an Android phone. The licence file reads **`Copyright (c) 2019 VIA, Inc.`**, the repo shows **1 commit**, and the hardware requirements are **comma.ai White Panda + Giraffe** (both long discontinued) on an **HTC U11+, U12+ or Pixel 2** with Android 8.0. **A phone-based L2 stack is a dead branch; `autowarefoundation/vision_pilot` (Apache-2.0, 927★) is the live answer to the same question.** |

> ⚠️ **Freshness trap, logged as a recurring class.** `medevel.com`'s *"Top 15 Open-Source Car AI
> Projects … (2026)"* presents VIA-AI as a current option. **The article's year is not the repo's
> freshness.** This is the licence-badge-on-a-listicle pathology one layer up — same fix: open the
> bytes. (That article could not be read first-hand; `medevel.com` does not resolve from this session.
> Names came from snippets, then every row above was verified against `raw.githubusercontent.com` and
> the rendered repo page.)

### ❌ Negative results from this leg

- **`DriveSense`** → [TensorTrove/DriveSense](https://github.com/TensorTrove/DriveSense): real and
  **MIT**, but **4★ and last pushed 2024-08-09.** Too small and too stale to carry a row.
- **`XiaomiAutoL3/DriveZero` re-probed as the third pass requested: still no licence file.** Both
  `main` and `master` serve a README; no `LICENSE`/`LICENSE.md`/`LICENSE.txt`/`COPYING` on either.
  **Open item stays open; still excluded** (147★, unlicensed).
- 🔴 **`hypery11/flipper-tesla-fsd`** (1,336★, `NOASSERTION`) surfaced on stars and is **excluded on
  suitability, not only licence**: *"nag killer, FSD region unlock"* defeats manufacturer restrictions
  and driver-attention monitoring. **Not appropriate for a client engagement whatever its grant.**
  Recorded so a later pass does not surface it as a find.

---

## 🔌 New on 2026-11-24 (second pass) — the charging-interface plane, and why its agent tier is empty

**Plane opened this pass.** Control before searching: `OCPP`, `OCPI`, `EVerest`, `SteVe` and
`charging station` returned **0 mentions across all 9 files** of this KB. The charging interface is
virgin ground here, and it sits inside this KB's own charter (*"EV ecosistema"*).

### The finding that shapes the whole plane: a 765× asymmetry, and the agent tier is keyword collisions

One instrument (`gh api -X GET search/repositories`, 2026-11-24) across both layers:

| Query | Repos | Top repo by stars | What the top repo actually is |
|---|---|---|---|
| `ocpp` | 1,863 | **7,654★** `evcc-io/evcc` | Real. Smart-charging daemon, MIT. |
| `ocpi` | 437 | 602★ `ocpi/ocpi` | Real — but it is the *specification*, not software. |
| `iso15118` | 85 | 250★ `ecog-io/iso15118` | Real. Protocol implementation, Apache-2.0. |
| `csms ev charging` | 48 | 1,154★ `steve-community/steve` | Real. CSMS, **GPL-3.0**. |
| `ev charging agent` | 224 | 538★ `AndyShaman/BYDMate` | ❌ **Collision** — a BYD DiLink head-unit app, no licence. |
| `ev charging llm` | 33 | 32★ `NERVsystems/osmmcp` | ❌ **Collision** — an OpenStreetMap MCP; EV charging is one tool among many. |
| `ocpp agent` | 10 | 48★ `shiv3/ocpp-cp-simulator` | Partly — a *simulator for testing* agents, not an agent. |
| `charging station copilot` | 3 | 229★ `danderfer/Comp_Sci_Sem_2` | ❌ **Collision** — a university coursework repo. |
| `charging station agent license:apache-2.0` | **0** | — | — |

**Say it precisely:** it is not that the operator-side charging agent is rare. It is that the category
does not exist, and the search index fills the hole with collisions — a map server, a phone app, a
student's coursework. `7,654★` of protocol software against a best honest agent-tier figure of `10★`
is **765×**. The licence-filtered probe closes it: `charging station agent license:apache-2.0` = **0**
means *one does not exist*, not *we did not find one*.

### What the agent tier really contains: driver-side MCP servers, single-author, byte-read MIT

All eight licences below were **byte-read** from `raw.githubusercontent.com`; none came from the API field.

| Repo | ★ | Licence (byte-read) | What it does |
|---|---|---|---|
| [shiv3/ocpp-cp-simulator](https://github.com/shiv3/ocpp-cp-simulator) | 48 | ✅ Apache-2.0 (11,356 B, `main/LICENSE`) | OCPP charge-point simulator **explicitly for AI-agent testing** + CSMS development. The test harness, not the agent. |
| [Casperjuel/abrp-mcp](https://github.com/Casperjuel/abrp-mcp) | 10 | ✅ MIT (1,067 B, `main/LICENSE`) | MCP server for A Better Route Planner (Iternio) — charging-stop routing. |
| [mattoddie/bluelink-mcp](https://github.com/mattoddie/bluelink-mcp) | 3 | ✅ MIT (1,066 B) | MCP for Hyundai Bluelink / Kia Connect — charge state. |
| [holger1411/unofficialzaptecMCP](https://github.com/holger1411/unofficialzaptecMCP) | 2 | ✅ MIT (1,072 B) | MCP for Zaptec chargers (status, history). |
| [Zenotech-bv/teslafi-mcp](https://github.com/Zenotech-bv/teslafi-mcp) | 2 | ✅ MIT (1,068 B) | MCP over the TeslaFi API. |
| [stuchapin909/open-charge-finder](https://github.com/stuchapin909/open-charge-finder) | 1 | ✅ MIT (1,069 B) | MCP giving agents charging-station location data. |
| [mahrukhzulfiqar/gridwise](https://github.com/mahrukhzulfiqar/gridwise) | 1 | ✅ MIT (1,063 B) | Cheapest/greenest time to charge, Denmark. |
| [winsparking/chargingnearme-mcp](https://github.com/winsparking/chargingnearme-mcp) | 0 | ✅ MIT (1,073 B) | Hosted MCP, US public stations. |
| [javierojan/askacharge-mcp](https://github.com/javierojan/askacharge-mcp) | 0 | ✅ MIT (1,091 B) | MCP to let an agent **operate** a network of chargers. |

**Every one is driver-side.** They answer *where do I charge* and *what is my car doing*. **Not one is
operator-side** — nothing prices a session, dispatches a technician, or clears a roaming dispute.
Median 1★, max 10★, all single-author. Treat them as **interface references, never as dependencies**.

### The optimization tier is real — and it is RL/MPC, not LLM

This is where the plane's genuine intelligence lives. Calling these "agents" without the caveat would
misdescribe the ecosystem, so the caveat is the point: **they decide setpoints by optimization, and no
language model is in the loop.**

| Repo | ★ | Licence (byte-read) | Role |
|---|---|---|---|
| [StavrosOrf/EV2Gym](https://github.com/StavrosOrf/EV2Gym) | 250 | ✅ MIT (1,076 B, `main/LICENSE`) | V2G simulation environment for **large-scale EV charging optimization**; multi-agent RL gym. The anchor of this tier. |
| [StavrosOrf/EV-GNN](https://github.com/StavrosOrf/EV-GNN) | 34 | ✅ MIT (1,076 B) | Graph neural nets to make RL scale in optimal charging. |
| [StavrosOrf/DT4EVs](https://github.com/StavrosOrf/DT4EVs) | 23 | ✅ MIT (1,076 B) | Decision Transformer, **offline** RL for charging problems. |
| [TUMFTM/REVOL-E-TION](https://github.com/TUMFTM/REVOL-E-TION) | 17 | ✅ Apache-2.0 (11,364 B) | Site-level energy-system optimization toolbox including EV fleets (TU München). |

One author (`StavrosOrf`) holds three of the four. **Single-maintainer concentration risk, stated.**

### ⛔ Excluded this pass, with the reason

| Repo | ★ | Licence (byte-read) | Why excluded |
|---|---|---|---|
| [nader0913/ocpp-rag](https://github.com/nader0913/ocpp-rag) | 48 | 🔴 **PolyForm Noncommercial 1.0.0** (4,712 B, `main/LICENSE`) | The **most-starred OCPP knowledge/RAG/MCP repo there is** — and it is non-commercial. API field says `NOASSERTION`, so nothing warns you. **Hard exclusion for a consultancy.** Second PolyForm-NC sighting in this fleet (first: `squid-protocol/gitgalaxy`, technology plane). |
| [AndyShaman/BYDMate](https://github.com/AndyShaman/BYDMate) | 538 | 🔴 No licence field | Not an agent framework — a BYD DiLink head-unit app with a voice feature. Keyword collision; recorded so the next pass does not re-find it. |
