---
industry: automotive
region: Global
updated: 2026-11-21
---

# 🏗️ Foundational repos — Automotive

> The bases to build on. Open licence, active community. Grouped by layer, because "automotive open source"
> is four unrelated stacks that are routinely confused.
> **Verification (2026-11-21):** liveness via `git ls-remote`, licences **byte-read** from
> `raw.githubusercontent.com` (HTTP 200), metadata from `gh api -X GET search/repositories`. All 174 KB
> URLs probed; 152 LICENSE files read. `github.com` and `api.github.com` remain **403**, but they are no
> longer needed.
>
> *Superseded note —* **2026-11-13:** `curl -sI` on `github.com` returns **HTTP 403** through this session's
> proxy — re-tested today on three URLs including `api.github.com`, all 403 — so figures are read from
> rendered repository pages. Where the licence was the point, the file was fetched raw from
> `raw.githubusercontent.com`; that is how `autoware-safety-island` was reclassified from GitHub's
> **"Other"** label to **verbatim Apache-2.0** (its file is `license.rst`) and how
> `autoware_latent_drive` was confirmed to have **no licence at all**.
> 🔴 **`huggingface.co` still does not resolve from this session**, so no model-weight licence was verified.
> 🆕 = added 2026-11-13. 🔄 = licence/stars re-read today. ⏸ = URL re-probed, figures carried forward.
> ⚪ = URL live, licence/stars deliberately left blank rather than guessed.

## 🆕 Added 2026-11-21 (third pass, 13:40Z) — Layer G: the plant floor, a gap this KB has carried at **zero repos for five passes**

**This closes the longest-standing supply gap in this KB.** Every prior pass measured
`plant-floor / manufacturing quality AI = 0 repos` and moved on. The gap was an artefact of **where we
were looking**: five passes searched `automotive` + `AI` + `agent`, and the plant-floor stack does not
describe itself as automotive at all — it is **industrial anomaly detection**, and it is mature,
permissive and maintained.

This matters disproportionately for this industry because **manufacturing is where the non-AV automotive
money is**, and it is the one automotive layer with a serious installed base in **every** region
including LATAM (see `intel/market.md` → Opportunities by region).

### 🆕 Layer G — Industrial visual inspection / anomaly detection (the plant-floor layer)

| Repo | Licence (byte-read) | ★ | Pushed | Why it is here |
|---|---|--:|---|---|
| [open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib) | **Apache-2.0** — `LICENSE`, 11,357 bytes, canonical | **6,414** / 1,047f | **2026-11-20** | **The anchor of this layer, and the only production-grade one.** Intel-maintained library of 20+ industrial anomaly-detection algorithms (PatchCore, PaDiM, EfficientAD…) with OpenVINO export. **Pushed yesterday**, 1,047 forks. For paint, weld, panel-gap and battery-module inspection this is the base to start from rather than build. ⚠️ **Read the dataset warning below before quoting a benchmark number.** |
| [sundyCoder/DEye](https://github.com/sundyCoder/DEye) | **Apache-2.0** — `LICENSE`, 11,357 bytes, canonical | 885 / 367f | ⚠️ **2023-03-14** | Surface-defect inspection, semiconductor-oriented. **Dormant 3.5 years — reference only, do not propose it as a base.** Listed because 885★/367f means client teams will have heard of it and will ask. |
| [awslabs/sagemaker-defect-detection](https://github.com/awslabs/sagemaker-defect-detection) | **Apache-2.0** — `LICENSE`, 10,142 bytes, canonical | 62 / 25f | ⚠️ **2022-12-21** | Supervised bounding-box defect detection on steel surfaces (NEU dataset). **Dormant 4 years and AWS-coupled** — useful as an architecture reference for a SageMaker-hosted client, not as a starting point. Default branch is `mainline`, not `main`. |

**The honest shape of this layer: one live anchor and two dormant references.** That is a finding, not a
shortfall — it means an engagement standardises on `anomalib` and treats everything else as prior art.

### 🔴 The dataset-licence trap, and it is the new error class from this pass

**`anomalib` is Apache-2.0. Its benchmark dataset is not.** **MVTec AD** — the dataset essentially every
industrial-anomaly-detection paper and tutorial reports against — is **CC BY-NC-SA 4.0: non-commercial.**

The code licence and the data licence are **independent axes**, and for an AI repo **the data licence is
usually the binding one**:

- ✅ Using `anomalib`'s **code** in a client deliverable: permitted by Apache-2.0.
- 🔴 Shipping **weights trained on MVTec AD** to a paying client: **commercial use of an NC dataset.**
- 🔴 Quoting an **MVTec AD benchmark number** in a commercial proposal: the same problem, and it is the
  form the mistake actually takes, because the benchmark table is the first thing a proposal copies.
- ✅ The clean path: train on **the client's own line images**, which is what the engagement should be
  doing anyway. The NC dataset is for *method selection*, never for the delivered model.

**Generalise this across every KB in this fleet:** a permissive SPDX on the repo says **nothing** about
the corpus the model was fitted to. Byte-reading `LICENSE` — the discipline this KB already enforces —
**does not catch this at all**, because the trap is not in `LICENSE`.

### 🔄 Two NOASSERTION rows resolved — and the resolution was already in `compose/patterns.md` P19

An internal inconsistency found by cross-reading this file against P19: **P19 records the byte-read answer
for both of these, while the rows below still tell the reader to "settle before any use."** A reader of
`foundations.md` was getting worse advice than a reader of `patterns.md`. Both rows are corrected in
place in Layer A / Layer 2 below, and the answers are:

| Repo | GitHub SPDX | Byte-read grant | What it means |
|---|---|---|---|
| [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics) | `NOASSERTION` | **MIT** — `LICENSE`, 1,170 bytes, *"The MIT License (MIT)"* | ✅ **Usable. Settled, not pending.** The largest repo in this file (**30,951★**) is cleanly permissive. |
| [autoas/as](https://github.com/autoas/as) | `NOASSERTION` | **Dual: GPL-3.0 OR Commercial** — `LICENSE`, 1,299 bytes, *"Dual License: GPLv3 and Commercial"*, © 2025 Parai Wang | 🔴 **Not usable under GPLv3 for proprietary client work — but a commercial grant exists and is offered by the author.** The "settle it" step is a **procurement conversation**, not a licence investigation. For the only substantial open AUTOSAR BSW, that is worth knowing before it is written off. |

### 🆕 The mechanism behind `NOASSERTION`, measured twice this pass — and it inverts the signal

Both NOASSERTION cases above are **verbatim licence text made non-matching by appending honest
information**. GitHub's classifier is near-exact-match, so *any* insertion drops the file to
`NOASSERTION`:

- `PythonRobotics` inserts a **contributors URL** after the copyright line.
- `MayankGangwal-code/ev-battery-soc-estimation` (probed this pass) appends a **dataset attribution**:
  *"The processed data in `data/` is derived from 'LG 18650HG2 Li-ion Battery Data' … Mendeley Data,
  doi:10.17632/cp3473x7xv.3, licensed CC BY 4.0."* Its MIT text is otherwise byte-identical to a
  canonical MIT file that GitHub classifies correctly.

**So `NOASSERTION` correlates with conscientious authorship, not with licence risk** — the careless
repos in this KB have **no licence file at all** and classify as `NONE`, not `NOASSERTION`. Sharpen the
standing rule: **`NOASSERTION` is not merely "a pointer" — it is frequently a pointer to a
*dataset* attribution**, which is exactly the axis the section above shows `LICENSE` cannot cover.

---

## 🆕 Added 2026-11-21 (second pass, verification 12:45Z) — one new reference repo, and the shelf re-measured

**This pass verified the 09:55Z base rather than rewriting it.** All 188 repo URLs across the eight files
were re-probed; **185 live, 3 dead — the same 3 already recorded as dead, none of them a recommendation.**
Every licence cell that disagreed with GitHub's measured SPDX was byte-read: **20 disagreements, 0 real
errors.** Details in `agents/top.md` §V1.

### 🆕 New reference repo — the survey layer gains a university-authored index

| Repo | Licence | ★ / forks | What it is |
|---|---|--:|---|
| 🆕 [TUM-AVS/FM-AD-Survey](https://github.com/TUM-AVS/FM-AD-Survey) | **Apache-2.0** — `LICENSE` byte-read 2026-11-21, **11,337 bytes, full canonical text** | **249★** | **Foundation-models-for-autonomous-driving survey from TU Munich's Autonomous Vehicle Systems chair (TUM-AVS).** Pushed **2026-11-19**, so it is tracking the layer in near-real time. **Prefer it over the anonymous `awesome-*` lists in "Index repos to track" below for anything client-facing**: it is attributable to a named academic group, which matters when a survey is the citation under a recommendation. Pair with `Thinklab-SJTU/Awesome-LLM4AD` (Apache-2.0, 1,906★) for breadth. |

### 🔴 This pass strengthens the standing warning about LICENSE-file-only probes — with a third example

The note below already records that `TrampolineRTOS/trampoline` and `navariltd/Fleet-Management-System`
state their grants outside a `LICENSE` file. **A third and sharper case was found this pass:**
**`autowarefoundation/autoware-safety-island` carries a full 10,894-byte Apache-2.0 text in
`license.rst`** — invisible to a probe of `LICENSE*`/`LICENCE`/`COPYING`/`NOTICE` across `main`,
`master` and `develop` (**18/18 404s**), and invisible to GitHub's matcher (`NOASSERTION`) because it is
reStructuredText. **Add `license.rst` and `LICENSE.rst` to every future probe list.** The existing row
for that repo already named `license.rst` as its evidence — **the base was right and the probe was wrong.**

### 🔴 Negative results settled 2026-11-21 (verification pass) — do not re-search these

- **No permissive dealership ERP/CRM exists — 7th consecutive negative.** Re-measured this pass:
  `Dolibarr/dolibarr` **GPL-3.0** (7,889★), `YetiForceCompany/YetiForceCRM` **`NOASSERTION`, unpushed
  since 2024-09-13**, `SuiteCRM` did not resolve. **`open-mercato/open-mercato` (MIT, 1,953★, pushed
  2026-11-21) is the only permissive option and it is a framework, not a dealership product.**
- **Two aggregator-sourced candidates evaporated under verification:** `SpaceDrive` (named as a CVPR 2026
  driving project) **resolves to no repository at all**, and the `carlover` slug cited by an ecosystems
  aggregator **does not exist** — the only matches are 0–3★ unlicensed projects. **Aggregator listings
  name papers and dead slugs as if they were repos; resolve the slug before writing the row.**
- **`huggingface.co`, `eur-lex.europa.eu`, `unece.org` and `www.federalregister.gov` are all DNS-dead from
  this environment — re-probed and re-confirmed this pass (6th consecutive).** Model **weights** licences
  therefore remain unverifiable here by construction. This is a channel limit, not a research gap.

---


## 🆕 Added 2026-11-21 — the canonical perception/benchmark layer, with honest dormancy labels

> **Verification:** `git ls-remote` for liveness, `raw.githubusercontent.com` for the byte-read licence,
> `gh api -X GET search/repositories` for stars/forks/`pushed_at`/`archived`. All first-hand.
> See `agents/top.md` → *"What changed on 2026-11-21"* for the channel table.

This base was strong on **stacks** (Autoware, Apollo, openpilot), **SDV middleware** (Eclipse) and
**bus tooling**, and thin on the **perception and benchmark repos that every ADAS engagement actually
reads**. Those are added here — **with the dormancy stated, because most of them are dormant, and that
is the finding.**

### 🆕 Layer F — Canonical perception, benchmark and dataset repos

| Repo | Licence (byte-read) | ★ | Last push | Liveness | What it is |
|---|---|--:|---|---|---|
| [waymo-research/waymo-open-dataset](https://github.com/waymo-research/waymo-open-dataset) | **Apache-2.0 *except* `src/waymo_open_dataset/wdl_limited`** (API: `NOASSERTION`) | 3,438 | 2026-01-08 | ⚠️ Slow | The reference AV dataset devkit. **Use the code, avoid that one directory**, treat the dataset as separately licensed. |
| [fundamentalvision/BEVFormer](https://github.com/fundamentalvision/BEVFormer) | **Apache-2.0** | 4,652 | 2024-08-15 | 🔴 **Dormant 2+ yrs** | Camera-only BEV perception (ECCV 2022). Still the most-cited BEV baseline — **read it, do not depend on it.** |
| [PJLab-ADG/SensorsCalibration](https://github.com/PJLab-ADG/SensorsCalibration) | **Apache-2.0** | 3,261 | 2024-06-17 | 🔴 **Dormant** | OpenCalib multi-sensor calibration toolbox. Calibration maths does not rot as fast as frameworks — **highest-value dormant repo here.** |
| [OpenDriveLab/End-to-end-Autonomous-Driving](https://github.com/OpenDriveLab/End-to-end-Autonomous-Driving) | **MIT** | 3,730 | 2025-07-02 | ⚠️ Slow | The E2E survey + curated paper list (IEEE T-PAMI 2024). MIT, so quotable in client material. |
| [hustvl/YOLOP](https://github.com/hustvl/YOLOP) | **MIT** | 2,258 | 2023-10-20 | 🔴 **Dormant 3 yrs** | Panoptic driving perception — detection + drivable area + lane in one head. Small, MIT, easy to port. |
| [daohu527/dig-into-apollo](https://github.com/daohu527/dig-into-apollo) | **MIT** | 2,457 | 2026-02-03 | ✅ Live-ish | Apollo architecture notes. **The fastest way to onboard an engineer onto Apollo** without reading 27k★ of C++. |
| [zhulf0804/3D-PointCloud](https://github.com/zhulf0804/3D-PointCloud) | 🔴 **No licence file** (API: `NONE`) | 2,949 | 2024-08-30 | 🔴 Dormant | Point-cloud papers/datasets index. **No grant — read-only reference, do not vendor it.** |
| [Ly0n/awesome-robotic-tooling](https://github.com/Ly0n/awesome-robotic-tooling) | **CC0-1.0** | 3,924 | 2023-11-20 | 🔴 Dormant | Robotics/AD tooling list. CC0 means **reusable verbatim** in internal docs. |
| [microsoft/AutonomousDrivingCookbook](https://github.com/microsoft/AutonomousDrivingCookbook) | **MIT** | 2,440 | 2025-08-25 | 🔴 **ARCHIVED** | Archived by Microsoft (`archived: true`). Tutorials only. **Listed so nobody proposes it as a base.** |

**Read this layer as a warning, not a shopping list.** Seven of the nine have not been pushed in over a
year; one is formally archived. The automotive perception commons is **largely frozen research code**,
while the *live* investment has moved to end-to-end/VLA models and the Autoware/Apollo stacks already in
this base. For an engagement that means: **take algorithms and calibration maths from Layer F; take
runnable infrastructure from Layers A–E and the stacks.** Proposing BEVFormer as a 2026 production base
would be a mistake this table exists to prevent.

### 🔄 Licence cells filled by byte-read this pass

| Repo | ★ | API `license.spdx_id` | **Byte-read grant** |
|---|--:|---|---|
| [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics) | 30,954 | `NOASSERTION` | **MIT** — *"The MIT License (MIT)"* |
| [COVESA/vss-tools](https://github.com/COVESA/vss-tools) | 81 | `MPL-2.0` | **MPL-2.0** (was *"not read this pass"* here) |
| [autoas/as](https://github.com/autoas/as) | 965 | `NOASSERTION` | **GPL-3.0 OR Commercial (dual)** |
| [openremote/fleet-management](https://github.com/openremote/fleet-management) | 51 | `NOASSERTION` | **AGPL-3.0** |

**`PythonRobotics` at 30,954★ is plain MIT and the API could not say so.** That single row is the
argument for byte-reading licences in this base rather than trusting an SPDX field.

### 🔴 Negative results settled 2026-11-21 — do not re-search these

- **`xtuple/xtuple` is gone** (404 via `git ls-remote`). Any ERP shortlist citing XTuple is stale.
- **No open-source dealership DMS exists.** See `verticals/solutions.md` and `agents/top.md` §7.
- **No LATAM-origin automotive foundation repo** surfaced across four region-scoped searches.
- **18 of 170 live repos serve no LICENSE file.** All already labelled correctly in this base; two
  (`TrampolineRTOS/trampoline`, `navariltd/Fleet-Management-System`) carry grants stated only in the
  README/source headers, so **a LICENSE-file-only probe would wrongly downgrade them.**

---

## 🆕 Added 2026-11-19 — four layers this KB did not have: SDV middleware, bus tooling, the openpilot ecosystem, and assurance

> **Verification:** every row below was re-queried by exact `repo:owner/name` through
> `gh api -X GET search/repositories` (the GitHub REST API), so licence SPDX IDs, stars, forks and push
> dates are **first-hand API fields**. 39 of 39 resolved. `curl` to `github.com`/`api.github.com` is
> **HTTP 403** (host policy); LICENSE files were settled via `raw.githubusercontent.com`.

### 🆕 Layer A — SDV middleware and in-vehicle plumbing (Apache-2.0 / MIT / BSD, all battle-tested)

This KB had Eclipse S-CORE, Kuksa, Velocitas and Ankaios. It was **missing the transport and build
layers underneath them**, which is where most SDV integration hours actually go.

| Repo | Licence | ★ / forks | Why it is foundational |
|---|---|--:|---|
| [nanomq/nanomq](https://github.com/nanomq/nanomq) | **MIT** | **2,666★** / 325f | *"Ultra-lightweight and blazing-fast Messaging Bus/MQTT Broker for Edge & SDV."* Pushed 2026-11-19. The in-vehicle/edge broker that sits under a Kuksa or Velocitas deployment. 59 open issues. |
| [eclipse-iceoryx/iceoryx](https://github.com/eclipse-iceoryx/iceoryx) | **Apache-2.0** | **2,212★** / 491f | *"True zero-copy inter-process communication."* The IPC layer AUTOSAR Adaptive and ROS 2 automotive stacks use when latency budgets are hard. 259 open issues (large, active project). |
| [eclipse-ecal/ecal](https://github.com/eclipse-ecal/ecal) | **Apache-2.0** | 1,060★ | High-performance pub/sub + client-server middleware, cross-platform. Pushed 2026-11-19. The recording/replay companion to iceoryx in AV data pipelines. |
| [eclipse-leda/leda-distro](https://github.com/eclipse-leda/leda-distro) | **Apache-2.0** | 21★ / 12f | **Yocto-based build setup for Eclipse SDV.EDGE components.** Low stars, high leverage: this is the reproducible in-vehicle Linux image that makes Kuksa/Velocitas/Ankaios actually boot on target. Siblings: [`leda`](https://github.com/eclipse-leda/leda) (docs), [`meta-leda`](https://github.com/eclipse-leda/meta-leda) (Yocto meta-layers), [`leda-utils`](https://github.com/eclipse-leda/leda-utils), [`leda-example-applications`](https://github.com/eclipse-leda/leda-example-applications). |
| [de4sdv/DE4SDV](https://github.com/de4sdv/DE4SDV) | **Apache-2.0** | 13★ / 4f | *"Open-source systems engineering for Software-Defined Vehicle — **SysML v2**, MBSE, product-line engineering, digital continuity, continuous compliance."* Pushed 2026-11-19, 11 open issues. The only open **SysML v2** automotive systems-engineering base found. Pairs directly with the assurance layer below. |
| [xronos-inc/xronos](https://github.com/xronos-inc/xronos) | **BSD-3-Clause** | 41★ | Deterministic timing + built-in observability for robotics/vehicle software — reproducible behaviour and root-cause analysis. Relevant where non-determinism is the actual defect. |
| [eclipse-sdv-landscape/sdv-landscape](https://github.com/eclipse-sdv-landscape/sdv-landscape) | **Apache-2.0** | 1★ | The Eclipse SDV landscape map itself. A navigation artefact, not code — use it to check this KB's own coverage. |

⚠️ **`vxedge/*`** (Apache-2.0, ~10 repos, all **1★ or 0★**, all pushed 2026-11-19) is a complete
manifest-driven SDV testbed — control plane, OTA server, SysML v2 models, telemetry, an **MCP server
(`vxmcp`, targeting MCP spec 2026-07-28)** and an OCI/ORAS part registry with ARINC-665-shaped part
numbers. Recorded as a **watch item, not a recommendation**: single-contributor, no community, six
weeks old. The *architecture* is worth reading before designing an SDV testbed engagement.

### 🆕 Layer B — Bus, DBC and diagnostics tooling (the unglamorous layer that every engagement touches)

| Repo | Licence | ★ / forks | Why it is foundational |
|---|---|--:|---|
| [ebroecker/canmatrix](https://github.com/ebroecker/canmatrix) | **BSD-2-Clause** | **1,093★** / 441f | Converts CAN database formats: **`.arxml` ⇄ `.dbc` ⇄ `.dbf` ⇄ `.kcd`**. Pushed 2026-11-18. **This is the ARXML bridge** — the piece that lets an agent read an OEM's AUTOSAR communication matrix. BSD-2 is the cleanest licence in this KB. |
| [iDoka/awesome-canbus](https://github.com/iDoka/awesome-canbus) | **CC0-1.0** | **3,571★** / 426f | CAN bus tools, hardware and resources, security/reverse-engineering oriented. CC0 = public domain. The index to consult before building any bus tool. |
| [Sherin-SEF-AI/CanLab](https://github.com/Sherin-SEF-AI/CanLab) | **MIT** | 94★ / 9f | PyQt6 app for reverse-engineering CAN captures: finds counters, checksums and signal boundaries; DBC builder **verified against real frames**; exports **DBC, openpilot and Wireshark dissectors**; UDS + OBD-II. **Injection is bench-only and disarmed until armed.** |
| [autoas/as](https://github.com/autoas/as) | 🔄 🔴 **GPL-3.0 OR Commercial** (byte-read 2026-11-21, 1,299 bytes, *"Dual License: GPLv3 and Commercial"*) | 965★ | *"Simple AUTOSAR Basic Software."* Pushed 2026-11-18. The only substantial open AUTOSAR BSW found. **Resolved this pass — GitHub's `NOASSERTION` was it failing to express a dual grant.** Unusable under GPLv3 for proprietary work, **but the author offers a commercial licence**, so this is a procurement conversation, not a dead end. |
| [TrampolineRTOS/trampoline](https://github.com/TrampolineRTOS/trampoline) | 🔴 **GPL-2.0** | 759★ | Static RTOS aligned to OSEK/VDX and **AUTOSAR OS 4.2**. GPL-2.0 — reference and bench only for a client deliverable. |
| [TOSUN-Shanghai/TSMaster](https://github.com/TOSUN-Shanghai/TSMaster) | ⚠️ **LGPL-2.1** + feature gating | 442★ | Bus monitoring, simulation, testing, diagnostics and calibration across TOSUN, Vector, IXXAT, PEAK, Kvaser, Intrepid, ZLG and more. Page states *"free for research and education purpose for some features"*. **Tool, never a shipped component.** |

### 🆕 Layer C — The openpilot ecosystem as a foundation layer

Previously a single row. It is a supply chain, and the hardware bundle came apart this quarter.

| Repo | Licence | ★ / forks | Role |
|---|---|--:|---|
| [commaai/openpilot](https://github.com/commaai/openpilot) | **MIT** | **64,177★** / 11,410f | Anchor. 300+ cars. Pushed 2026-11-19, 141 open issues. |
| [sunnypilot/sunnypilot](https://github.com/sunnypilot/sunnypilot) | **MIT** | 2,178★ | 350+ makes/models — **broader vehicle coverage than upstream** |
| [zoompilot/jetlink](https://github.com/zoompilot/jetlink) | **MIT** | 57★ / **40f** | Runs openpilot's large driving model on **Jetson Orin Nano, macOS, iOS, Android, CUDA laptops** with a comma device + USB3 |
| [zoompilot/zoompilot](https://github.com/zoompilot/zoompilot) | **MIT** | 37★ / 31f | ADAS for **Mazda** and others; pushed 2026-11-19 |
| [YassineYousfi/openpilot.distill](https://github.com/YassineYousfi/openpilot.distill) | **MIT** | 38★ | Distil openpilot on your own drives |
| [StarPilotHQ/StarPilot](https://github.com/StarPilotHQ/StarPilot) | **MIT** | 163★ | Tuning-focused fork |
| [commaai/connect](https://github.com/commaai/connect) | **MIT** | 153★ | openpilot fleet/experience management |
| [commaai/opendbc](https://github.com/commaai/opendbc) | **MIT** | **3,571★** / 2,408f | *"a Python API for your car"* — the DBC corpus underneath all of the above. Pushed 2026-11-19, 378 open issues. |
| [Sherin-SEF-AI/Lyne-ADAS](https://github.com/Sherin-SEF-AI/Lyne-ADAS) | **MIT** | 22★ / 7f | **100% on-device ADAS for Android**; self-tunes from budget phones to flagships |
| [eFiniLan/openpilot-ext-radar-addon](https://github.com/eFiniLan/openpilot-ext-radar-addon) | ⚠️ `NOASSERTION` | 33★ | External radar for longitudinal control — settle licence first |

**`jetlink`'s 40 forks on 57 stars** is the signal: people are porting, not bookmarking.

### 🆕 Layer D — Assurance and standards as code

| Repo | Licence | ★ / forks | Role |
|---|---|--:|---|
| [jherrodthomas/automotive-skills-suite](https://github.com/jherrodthomas/automotive-skills-suite) | **MIT** | **2,907★** / 141f | 76 builder+reviewer skill pairs → `.xlsx` artefacts across **ISO 26262 / ISO 21434 / ISO 21448 / ASPICE / AIAG-VDA**, plus CAN-LIN-FlexRay-Ethernet, UDS/ODX/DEM, AUTOSAR Classic+Adaptive, A2L/DCM, MBSE/SysML, V&V traceability. ⚠️ **No "not certified" disclaimer on the page.** |
| [jherrodthomas/LionDriver](https://github.com/jherrodthomas/LionDriver) | **MIT** | 65★ / 3f | openpilot derivative carrying a **living safety case (36 claims, 50 evidence, 42 open defeaters, 0 accepted)** and 89 V-cycle work products; cites ISO 26262/21448/21434, **ISO/PAS 8800**, **UL 4600**, ASPICE; **explicitly claims no compliance**. Use as the **template** for an assurance repository. |
| [Lieubk/automotive-safety-security-assurance-kit](https://github.com/Lieubk/automotive-safety-security-assurance-kit) | **MIT** | 2★ | ASPICE 3.1/4.0 + ISO 26262 + ISO/SAE 21434 skills, agents and a **trace engine**. Created 2026-11-19. |

### 🆕 Layer E — Simulation, benchmarking and datasets added this pass

| Repo | Licence | ★ / forks | Role |
|---|---|--:|---|
| [Farama-Foundation/HighwayEnv](https://github.com/Farama-Foundation/HighwayEnv) | **MIT** | **3,342★** / 906f | Driving and tactical decision-making environments. Farama (the Gymnasium maintainers) — stable governance. The cheapest place to prototype a planning policy. |
| [hanruihua/ir-sim](https://github.com/hanruihua/ir-sim) | **MIT** | 1,239★ | Lightweight Python simulator for navigation, control and learning |
| [ShisatoYano/AutonomousVehicleControlBeginnersGuide](https://github.com/ShisatoYano/AutonomousVehicleControlBeginnersGuide) | **MIT** | 1,963★ | Python simulations + open textbook; swap and compare localisation/planning/control in one system. **The best onboarding asset found for a studio ramp-up.** |
| [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics) | 🔄 ✅ **MIT** (byte-read 2026-11-21, 1,170 bytes, *"The MIT License (MIT)"*) | **30,951★** | Robotics algorithm reference implementations. **Resolved this pass — cleanly permissive, nothing to settle.** GitHub reported `NOASSERTION` only because the file inserts a contributors URL after the copyright line, which breaks its exact-match classifier. |
| [MRPT/mrpt](https://github.com/MRPT/mrpt) | **BSD-3-Clause** | 2,175★ | Mobile Robot Programming Toolkit — SLAM, localisation, point clouds |
| [aditya-ramabadran/drivingbench_harness_code](https://github.com/aditya-ramabadran/drivingbench_harness_code) | **MIT** | 63★ / 8f | **Agents drive real cars over MCP** (comma four, Toyota TSS2, Tesla M3 HW3) with a 3 m/s ceiling and a 6 m/s hard cutoff; Gaussian-splat simulator; full trace replay |
| [radar-lab/OpenCDA-MARL](https://github.com/radar-lab/OpenCDA-MARL) | **Apache-2.0** | 16★ | Cooperative-driving MARL benchmark on **CARLA + SUMO co-simulation** |
| [thi-ad/UrbanIng-V2X](https://github.com/thi-ad/UrbanIng-V2X) | **MIT** | 88★ / 14f | **NeurIPS 2025** multi-vehicle, multi-infrastructure cooperative-perception dataset across multiple intersections (TH Ingolstadt, **EMEA**) |
| [nv-tlabs/omni-dreams](https://github.com/nv-tlabs/omni-dreams) | **Apache-2.0** | 367★ | **NVIDIA OmniDreams** — real-time photorealistic AV-sim video world model |
| [visionpilot-project/VisionPilot](https://github.com/visionpilot-project/VisionPilot) | **MIT** | 43★ | Modular AD simulation on **BeamNG.tech** with Foxglove visualisation. ⚠️ **Not** `autowarefoundation/vision_pilot` — see the collision note below. |
| [autowarefoundation/AWSIM](https://github.com/autowarefoundation/AWSIM) | 🔴 **bespoke "AWSIM License"** | 765★ / 163f | Autoware digital-twin simulator. **Not Apache-2.0** — LICENSE read raw. Read the terms before any deliverable depends on it. |

### 🆕 Index repos to track instead of re-searching

[Thinklab-SJTU/Awesome-LLM4AD](https://github.com/Thinklab-SJTU/Awesome-LLM4AD) (**Apache-2.0,
1,906★**) is the best single map of LLM/VLM/VLA/world-model work for autonomous driving.
[worldbench/awesome-3d-4d-world-models](https://github.com/worldbench/awesome-3d-4d-world-models)
(Apache-2.0, 1,031★, TPAMI 2026) and
[leofan90/Awesome-World-Models](https://github.com/leofan90/Awesome-World-Models) (BSD-3-Clause,
2,059★) cover the world-model tier.
[szenergy/awesome-lidar](https://github.com/szenergy/awesome-lidar) (CC0-1.0, 1,373★) covers sensors.
🔴 [LMD0311/Awesome-World-Model](https://github.com/LMD0311/Awesome-World-Model) (2,304★) and
🔴 [Little-Podi/Collaborative_Perception](https://github.com/Little-Podi/Collaborative_Perception)
(639★) carry **no licence** — read, do not vendor.

### ⚠️ Name collision recorded as a procurement hazard

`visionpilot-project/VisionPilot` (**MIT, 43★**, BeamNG simulation) vs
`autowarefoundation/vision_pilot` (**Apache-2.0, 928★/197f**, productionizable L2 ADAS stack). Different
owners, licences and purposes; near-identical names; both appear for the query "VisionPilot". **Always
write the full `owner/name` in a statement of work or an architecture decision record.**

### 🔴 Negative results settled 2026-11-19 — do not re-search these

| Query (`gh api search/repositories`) | Result |
|---|---|
| `EV battery charging AI in:name,description pushed:>2026-08-01 stars:>15` | **0 repos** |
| `automotive manufacturing quality inspection AI in:name,description pushed:>2026-06-01 stars:>3` | **0 repos** — plant-floor vision is proprietary |
| `fleet management telematics in:name,description pushed:>2026-08-01 stars:>5` | **2 repos** only: `openremote/fleet-management` (51★, `NOASSERTION`), `santoshiimind/fleet-management-system` (**Apache-2.0**, 8★ — FastAPI + SQLAlchemy, OBD-II + GPS + CAN decode + DTC + driver behaviour + fuel analytics; the only permissive open fleet stack found, and it is a one-person project) |
| `car dealership management in:name,description,topics pushed:>2026-01-01` | 408 repos, **top star count 5**, nearly all unlicensed |
| `V2X cooperative perception in:name,description pushed:>2026-08-01 stars:>30` | **3 repos**; only `thi-ad/UrbanIng-V2X` is permissively licensed |
| Generic agent searches (`top open source AI agents automotive 2026 github MIT`, `github trending automotive AI 2026`) | **Still a dead end** — returns OpenHands, OpenCode, CrewAI, OpenClaw, browser-use with no automotive content. Sixth pass with this result. **Search the standard and the protocol, not the buzzword.** |

## 🆕 Added 2026-11-13 — the Autoware Foundation published a stack, not a model

Between **10 and 12 November 2026** the Autoware Foundation org pushed an entire vertical slice of ADAS:
a production L2 stack, two perception models, a trucking charter, a latent-space planner, a fork of
NVIDIA's Alpamayo, and zero-copy ROS 2 middleware. **Eight repositories, verified individually below.**
The practical consequence for this file is that **Layer 2 is no longer the interesting layer** — the new
material spans Layers 2, 3 and a new Layer 0, because a usable ADAS stack is now open.

**The single most important row added to this KB this pass** is `vision_pilot`: **Apache-2.0, 927★,
196 forks, 4,282 commits**, a *"productionizable and safety certifiable"* **L2 ADAS stack** with ACC, FCW,
AEB, LKAS, LDW, ISA and hands-free highway autopilot, running **mapless** on **a single monocular camera**
via ONNX Runtime on GPU **or CPU**. Until today the only large permissive automotive codebase in this file
was openpilot (MIT). There are now two, and the new one is Apache-2.0 under foundation governance with an
**ISO 26262 / ISO 8800** roadmap.

🔴 **One of the eight has no licence.** `autoware_latent_drive` (42★) has no sidebar licence field, no
licence statement in its README, and `LICENSE`, `LICENSE.md`, `LICENSE.txt` and `license.rst` **all 404 on
`main`**. It is excluded from every shelf in this KB and recorded in
[`../agents/top.md`](../agents/top.md) under exclusions. **A major foundation's org is not a grant.**

🟢 **And one was rescued from a wrong label.** `autoware-safety-island` reads as **"Other"** in GitHub's
org listing because its licence lives in `license.rst`. Fetched raw, it is verbatim **Apache License 2.0**.
Shelved in Layer 3. **Treat "Other" as an instruction to fetch the file, never as a verdict.**

## 🆕 Layer 0 — Production ADAS stacks (new layer 2026-11-13)

A new layer, because these are neither simulation nor research models nor in-vehicle middleware: they are
**shippable driver-assistance systems**. This is the layer a client means when they say "we want ADAS".

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🆕 [autowarefoundation/vision_pilot](https://github.com/autowarefoundation/vision_pilot) | **Apache-2.0** | **927** | *"Free and fully open-source L2 ADAS stack powered by End-to-End AI technology"*; README: *"a productionizable and safety certifiable implementation of an open-source L2 ADAS system called Vision Pilot."* **ACC, FCW, AEB, LKAS, LDW, ISA + single-lane hands-free highway Autopilot**, **mapless** (no 3D HD maps). *"Hybrid End-to-End AI Architecture"* — perception models in parallel with E2E models, *"processed in parallel by perception AI models for safety, and End-to-End AI models for performance."* Three models: **AutoSpeed** (closest in-path object), **AutoSteer** (ego path waypoints), **AutoDrive** (E2E distance + in-path presence + curvature). Input: **one front monocular camera, 52–55° HFOV, 1–2 MP**. **ONNX Runtime**, CUDA **or CPU**, Docker, optional ROS 2, CARLA 0.9.16 closed loop. v1.0 `.deb`. Roadmap: radar fusion, 8 MP/120° camera, **ISO 26262 + ISO 8800**. 196 forks, 4,282 commits. ⚠️ "Certifiable" is a roadmap item, not a status. ⚠️ README's clone URL says `autoware_vision_pilot.git`; the repo is `vision_pilot`. |
| 🆕 [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | **64.1k** | *"An operating system for robotics … upgrades the driver assistance system on 300+ supported cars."* 64.0k → 64.1k this pass. Previously recorded only in `agents/top.md`; it belongs in foundations too, since it is the largest permissive automotive codebase in existence. |
| 🆕 [sunnypilot/sunnypilot](https://github.com/sunnypilot/sunnypilot) | MIT | 2.2k | The significant openpilot fork, **same MIT grant**, advertising *"over 350 supported car makes and models"* — **more vehicle coverage than upstream's 300+**. 19,012 commits. Check here when a client's specific vehicle is unsupported upstream. |
| 🆕 [autowarefoundation/autoware.trucks](https://github.com/autowarefoundation/autoware.trucks) | Apache-2.0 | 2 | *"Everything specific to trucking autonomy."* README: open-source **highway trucking autonomy, from SAE L2+ highway piloting toward L4**. 9 commits — a charter, not yet a codebase. Watch item: North American autonomy capital is visibly moving to freight (Kodiak, see `intel/market.md`), and `Peykan` in `agents/top.md` is the only diagnostics agent covering the **J1939** truck bus. |

## 🆕 Added 2026-10-31 — the open E2E model layer doubled

Two Apache-2.0 end-to-end driving models that this file had no row for are now verified and added to
Layer 2 below: **AutoE2E** (Autoware Foundation, tagged **29 Oct 2026**) and **Qwen-Drive-1.0** (Alibaba).
On AutoE2E's own published eight-model comparison **both sit ahead of Alpamayo 1.5**, which is the stack
this KB has recommended as the reference since July — stated here because a foundations file that only
tracks one vendor's line stops being a foundations file. The comparison is **not like-for-like** (inputs
differ by model); the full table and caveats are in
[`../agents/top.md`](../agents/top.md).

A third addition sits outside every existing layer and gets its own one below: **Auto Agent Protocol**, the
open contract for reaching a dealership over MCP/A2A/PAP.

## 🆕 The biggest addition this pass: Eclipse S-CORE

The 2026-10-15 pass covered Kuksa, Ankaios and VSS but **missed the project the German OEM bloc is actually
consolidating on**. Eclipse S-CORE (*Safe Open Vehicle Core*) is the first open-source-based SDV platform
initiative designed against **ASIL-B** functional-safety requirements — a design target, **not** a
certification, and worth stating that way to a client.

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🆕🔄 [eclipse-score/score](https://github.com/eclipse-score/score) | Apache-2.0 | 111 | *"Score project main repository."* The platform root. **Release history read from the GitHub releases page today: `v0.7.3` (07 Oct), `v0.7.2` (02 Sep), `v0.7.1` and `v0.7.0` (24 Aug), `v0.6.4` (07 Aug), `v0.6.3` (31 Jul), `v0.6.2` (14 Jul), `v0.6.1` (13 Jul), `v0.6.0` (26 Jun), `v0.5.5` (26 Apr)** — the page shows dates without a year; all ten fall inside the last 12 months, so they are 2026. Cadence is roughly monthly, and it is shipping. |
| 🆕🔄 [eclipse-score/inc_feo](https://github.com/eclipse-score/inc_feo) | Apache-2.0 | 7 | *"Incubation repository for the fixed execution order framework."* Deterministic execution order — the piece that makes a safety argument tractable. Rust (inferred from `Cargo.toml`, not stated on the page). |
| 🆕 [eclipse-score/baselibs](https://github.com/eclipse-score/baselibs) | ⚪ not read this pass | — | Base libraries. Press reporting says a **Baselibs Rust** module arrived with 0.6.0. URL live 2026-10-26; licence not re-read. |
| 🆕 [eclipse-score/communication](https://github.com/eclipse-score/communication) | ⚪ not read this pass | — | Communication layer. URL live 2026-10-26. |
| 🆕 [eclipse-score/itf](https://github.com/eclipse-score/itf) | ⚪ not read this pass | — | Integration test framework — relevant to any ASIL evidence pipeline. URL live 2026-10-26. |
| 🆕 [eclipse-score/process_description](https://github.com/eclipse-score/process_description) | ⚪ not read this pass | — | The project's development process as a repository. For a client building a safety argument, **this is the artefact that matters as much as the code**. URL live 2026-10-26. |
| 🆕 [eclipse-score/module_template](https://github.com/eclipse-score/module_template) | ⚪ not read this pass | — | Template for a conforming S-CORE module — the entry point for contributing a client's own component. URL live 2026-10-26. |

**Project facts worth carrying into a conversation** (secondary sources, see the conflict note below):
Eclipse project page lists **Apache License 2.0** with the standard caveat that some sources/binaries may
carry different terms; **v0.5-alpha was the first public release (Nov 2025)**; **0.6.0 introduced full
dual-language C++ **and** Rust support, including the Ferrocene safety-critical Rust toolchain**; the
Eclipse SDV ↔ **VDA** memorandum expanded to **32 companies (Jan 2026)**; **Hyundai Mobis joined the SDV
Working Group (May 2026)**; and founding member **Qorix** sells a commercial middleware distribution built
on S-CORE — meaning the open project already has a paid-support path a risk-averse OEM can point at.

🔴 **Stated conflict, not resolved:** trade press puts 0.6.0 in **February 2026** and 0.7.0 in **May 2026**;
the **GitHub releases page read today** puts 0.6.0 at **26 Jun** and 0.7.0 at **24 Aug**. The releases page
is the primary source and is preferred here. The Eclipse project page also lists a **v1.0.0 dated
2026-12-14**, which is in the future and should be treated as a plan, not a shipped release — an ETAS
presentation separately says a complete solution is on track for **2028**. Do not quote a single 1.0 date.

## Layer 1 — Simulation & scenarios

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [carla-simulator/carla](https://github.com/carla-simulator/carla) | MIT | 14.5k | *"Open-source simulator for autonomous driving research."* The de facto standard; largest ecosystem. |
| ⏸ [carla-simulator/scenario_runner](https://github.com/carla-simulator/scenario_runner) | MIT | 683 | Traffic-scenario definition and execution engine for CARLA. |
| 🔄 [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | NVIDIA's open AV simulation platform for end-to-end policy development and testing. |
| ⏸ [eclipse-sumo/sumo](https://github.com/eclipse-sumo/sumo) | EPL-2.0 | 4.2k | Microscopic, continuous traffic simulation — city/fleet scale rather than single-vehicle. |
| ⏸ [esmini/esmini](https://github.com/esmini/esmini) | MPL-2.0 | 949 | A basic OpenSCENARIO player — the lightweight way to execute ASAM OpenSCENARIO files in CI. |
| ⏸ [erdos-project/pylot](https://github.com/erdos-project/pylot) | Apache-2.0 | 535 | Modular AD platform running on CARLA and real vehicles. |

## Layer 2 — Perception, datasets & models

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) | Apache-2.0 | 6.6k | Next-generation platform for general 3D object detection. |
| ⏸ [open-mmlab/OpenPCDet](https://github.com/open-mmlab/OpenPCDet) | Apache-2.0 | 5.7k | Toolbox for LiDAR-based 3D object detection. |
| ⏸ [nutonomy/nuscenes-devkit](https://github.com/nutonomy/nuscenes-devkit) | Apache-2.0 | 2.8k | Devkit for the nuScenes dataset. ⚠️ GitHub's sidebar shows no licence name; `LICENSE.txt` was read directly (2026-10-15) and is **Apache-2.0, © 2021 Motional**, no non-commercial clause. The *dataset* carries separate terms. |
| 🔄 [OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) | Apache-2.0 | 4.8k | Planning-oriented end-to-end AD (CVPR 2023 Best Paper). |
| 🆕🔄 [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) | Apache-2.0 | 824 | AAAI 2026 end-to-end VLA, **0.5B checkpoint on Hugging Face** — the small-model option. |
| 🆕 [autowarefoundation/auto_e2e](https://github.com/autowarefoundation/auto_e2e) | **Apache-2.0** (`LICENSE` fetched raw and read 2026-10-31) | 184 | **AutoE2E v1.0, tagged 29 Oct 2026.** Camera-first E2E driving model, **no HD maps required**: 79.9M params, six surround cameras @10 Hz → BEV grid → GRU planner → **6.4 s of acceleration and curvature**. 1 Hz World Action and Reasoning models still in development. ~76 FPS (SwinV2-Tiny, RTX 5080, batch 1 — project figure). 38 forks. **Vendor-neutral governance** (Autoware Foundation Robotaxi WG) is the reason to prefer it as a teaching/reference base over a vendor line. ⚠️ Secondary source (TIER IV exec LinkedIn) claims **OpenMDW-1.1** for the weights; the repo `LICENSE` is Apache-2.0 and the **weights licence is unresolved** — see the channel gap. |
| 🆕 [QwenLM/Qwen-Drive-1.0](https://github.com/QwenLM/Qwen-Drive-1.0) | Apache-2.0 | 537 | Alibaba's open AV vision-language foundation model: **Qwen3.5-4B** VLM + **BEV perception head** (3D detection, occupancy, map segmentation) + **flow-matching Planning Expert**. **4B fills the gap between OpenDriveVLA (0.5B) and Alpamayo 1.5 (10B)** — the practical size for a single-GPU client experiment. 56 forks. Weights advertised as `Qwen/Qwen-Drive-1.0-4B` on Hugging Face and ModelScope; repo states Apache-2.0 without separately naming the weights. |
| 🆕 [autowarefoundation/scene_3d](https://github.com/autowarefoundation/scene_3d) | Apache-2.0 | 2 | *"Open-source AI model for monocular depth estimation."* Per-pixel **relative** depth (nearer/farther) at high resolution from one camera. README states it is **part of the AutoSeg Foundation Model, the core of the vision pipeline for the Autoware Autonomous Highway Pilot System** — so this is a published component of a named foundation model, not a standalone experiment. Ships **Scene3DLite, distilled from DepthAnythingV2**; the distilled variant is the deployable one. 3 commits. Early, but it is the depth input Vision Pilot's perception half needs. |
| 🆕 [autowarefoundation/ego_lanes](https://github.com/autowarefoundation/ego_lanes) | Apache-2.0 | 1 | *"Semantic segmentation and classification of lane lines."* README: a *"legacy semantic end-to-end lane boundary segmentation network"* segmenting driving lanes from monocular frames **without HD maps**. 30 commits. ⚠️ **"Legacy" is the maintainers' own word** — use it as the baseline to beat in an LKAS/LDW engagement, not as the target architecture. |
| 🆕 [hustvl/Senna](https://github.com/hustvl/Senna) | Apache-2.0 | 559 | *"[IJCV 2026] Senna: Bridging Large Vision-Language Models and End-to-End Autonomous Driving."* **Peer-reviewed (IJCV 2026)** VLM↔E2E bridge from HUST's vision lab. The academic counterweight to the vendor lines, and a second opinion on attaching a language model to a planner without replacing it. 16 commits. Surfaced via the `DatariusAI/AI-in-Automotive` feed, which is the first time that unlicensed reading-feed has paid for itself. |
| 🆕 [autowarefoundation/alpamayo-autoware](https://github.com/autowarefoundation/alpamayo-autoware) | Apache-2.0 | 161 | **The Autoware Foundation's own fork of `NVlabs/alpamayo`**, updated 11 Nov 2026, default branch **`alpamayo2.0-edge`**, 42 commits, no description set. Matters as **governance, not science**: the vendor-neutral foundation now carries an edge branch rather than consuming NVIDIA releases. For a client who cares about vendor neutrality, track this fork rather than upstream. |

## Layer 3 — Software-defined vehicle (SDV) in-vehicle platform

The layer most relevant to OEM/Tier-1 engagements and the least known outside them. **Read the S-CORE
section above first** — it sits above this stack rather than beside it.

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification) | MPL-2.0 | 451 | *"Vehicle Signal Specification - standardized way to describe automotive data."* The common vocabulary every project below maps onto. **Start here.** COVESA hosts 100+ companies around it. |
| 🆕 [COVESA/vss-tools](https://github.com/COVESA/vss-tools) | ⚪ not read this pass | — | The tooling that turns a VSS model into generated artefacts. Needed in practice as soon as VSS is adopted; URL live 2026-10-26. |
| 🔄 [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker) | Apache-2.0 | 82 | *"A modern in-vehicle VSS server written in RUST."* gRPC, containerisable. Release 0.6.1 (Apr 2026) and a Quarkslab security audit. Low stars ≠ low importance. |
| 🆕 [eclipse-kuksa/kuksa-python-sdk](https://github.com/eclipse-kuksa/kuksa-python-sdk) | ⚪ not read this pass | — | Python client for the Databroker — the fastest way to prototype against VSS signals. URL live 2026-10-26. |
| 🔄 [eclipse-ankaios/ankaios](https://github.com/eclipse-ankaios/ankaios) | Apache-2.0 | 125 | *"Workload and container orchestration for embedded devices like automotive HPCs"* — the "Kubernetes of the car", where real Kubernetes does not fit. |
| 🆕🔄 [eclipse-sdv-blueprints/fleet-management](https://github.com/eclipse-sdv-blueprints/fleet-management) | Apache-2.0 | 27 | **The single most useful new find for engagement work.** A runnable truck-fleet reference wiring **Kuksa CSV Provider → Kuksa Databroker → FMS Forwarder → Eclipse uProtocol → FMS Consumer → InfluxDB → Grafana**, plus an **FMS Server exposing the rFMS API**. A published end-to-end topology instead of an architecture diagram. |
| ⏸ [eclipse-velocitas/cli](https://github.com/eclipse-velocitas/cli) | Apache-2.0 | 6 | CLI for the Velocitas toolchain for containerised in-vehicle apps. Very early; listed for stack completeness. |
| 🆕 [autowarefoundation/agnocast](https://github.com/autowarefoundation/agnocast) | Apache-2.0 | 212 | *"A rclcpp-compatible true zero-copy IPC middleware that supports all ROS message types."* **The most reusable piece of infrastructure added this pass.** Keeps the rclcpp API while removing message copies between ROS 2 processes — including for unsized message types, which is the case normal zero-copy approaches cannot handle. Implemented as a **kernel module (`agnocast_kmod`) plus a heaphook library**, integrates `CallbackIsolatedExecutor`, targets **ROS 2 Humble and Jazzy on Ubuntu 22.04/24.04**. 1,258 commits, and the README grounds it in the authors' published papers. Relevant far beyond ADAS: any ROS 2 perception pipeline under latency pressure. |
| 🆕 [autowarefoundation/autoware-safety-island](https://github.com/autowarefoundation/autoware-safety-island) | **Apache-2.0** (`license.rst` fetched raw and read 2026-11-13; GitHub's org listing mislabels it **"Other"**) | 8 | *"Autoware Safety Island Implementation based on ARM SoCs."* **608 commits** — by commit count the most substantial safety-relevant repo in this layer, and it was nearly lost to a bad licence label. A safety island is the independent monitoring element a functional-safety argument is built around, so this sits directly alongside **Eclipse S-CORE** above: S-CORE is the ASIL-B-targeted platform, this is a concrete ARM-SoC implementation. Pair them in any safety engagement. |
| 🆕 [autowarefoundation/autoware-index](https://github.com/autowarefoundation/autoware-index) | Apache-2.0 | 1 | *"Federated registry of community Autoware packages (`distribution.yaml` + sweep-driven validation history)."* A federated package registry **with recorded validation history** is how this ecosystem will be navigated from here — and the validation-history part is what makes it more than a list. 1★: brand new. Track it. |
| 🆕 [autowarefoundation/openadkit-rcar-x5h](https://github.com/autowarefoundation/openadkit-rcar-x5h) | Apache-2.0 | 0 | *"Board support for Open AD Kit on the Renesas R-Car X5H: AutoSD image, kernel, CR52 dual boot and demos."* **Silicon-specific board support is the step most open AV stacks never publish** — and this one includes an **AutoSD image, a kernel and CR52 dual boot**, which is what turns "runs on automotive hardware" from a claim into something a client can reproduce on a mainstream Renesas SoC. 0★ and it is still one of the most engagement-relevant repos in the org. |

## Layer 4 — Vehicle bus / diagnostics (unglamorous, highly reusable)

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [commaai/opendbc](https://github.com/commaai/opendbc) | MIT | 3.5k | *"a Python API for your car"* — CAN message definitions for production vehicles. Fastest route to real vehicle signals. |
| ⏸ [cantools/cantools](https://github.com/cantools/cantools) | MIT | 2.3k | CAN bus tools: DBC/KCD parsing, encode/decode, diagnostics. |
| ⏸ [hardbyte/python-can](https://github.com/hardbyte/python-can) | **LGPL-3.0** | 1.6k | CAN support for Python. ⚠️ LGPL — dynamic linking is fine, but flag it in any shipped client deliverable. |

## 🆕 Layer 5 — The agent-facing contract layer (new 2026-10-31)

New layer, because it belongs to none of the four above: it is neither simulation, perception, in-vehicle
platform nor vehicle bus. It is how an **external** agent is supposed to talk to an automotive *business*.

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🆕 [auto-agent-protocol/auto-agent-protocol](https://github.com/auto-agent-protocol/auto-agent-protocol) | **Apache-2.0** (specification, schemas, code) · documentation **CC BY 4.0** | 110 | *"The open automotive contract for MCP, A2A and Personal Agent Protocol: dealer discovery, inventory, evidence, pricing and consented inquiries."* README describes **v3.1** as an additive minor release that preserves the published **3.0** contract's meanings; AAP **2.x implementations must complete the 3.0 migration first**. Discovery works by the dealer domain publishing an **Agent Card**, a **Poppy document** and **`llms.txt`** that link live MCP, A2A and PAP endpoints, with the MCP tool catalogue and A2A OpenAPI served from versioned **`/v3.0/`** paths. Independent of — and built on — Google's A2A, which is Apache-2.0 under the Linux Foundation. No release tag shown on the repo page. |

**Why this earns a layer rather than a footnote.** Three passes of this KB concluded the automotive *retail*
layer is a closed oligopoly with nothing to fork, and that remains true of the **systems of record**
(CDK, Reynolds & Reynolds, Tekion, DealerSocket). But the **interface** to that layer is now specified in
the open, versioned, and separately licensed for docs. For an engagement that means a dealer-group client
can be given an agent-reachable surface **without** replacing their DMS — the integration target is a
published contract instead of a bespoke negotiation per vendor. 🔴 **Unknown, and worth saying to a client:
how many dealerships actually serve these endpoints today.** The spec's existence is verified; its
deployment is not.

## Licence flags for this industry

- **Permissive, safe to build on:** CARLA, openpilot, Autoware, Apollo, Alpamayo code / Alpamayo 2 /
  AlpaSim / AlpaGym, OpenDriveVLA, WorldEngine, OpenPCDet, mmdetection3d, opendbc, cantools,
  nuscenes-devkit, Kuksa, Ankaios, **Eclipse S-CORE**, the SDV fleet-management blueprint,
  AutoE2E, Qwen-Drive-1.0 and Auto Agent Protocol (all Apache-2.0); 🆕 **Vision Pilot**,
  🆕 **agnocast**, 🆕 **autoware-safety-island**, 🆕 **Scene3D**, 🆕 **EgoLanes**,
  🆕 **alpamayo-autoware**, 🆕 **autoware.trucks**, 🆕 **Senna** (Apache-2.0); 🆕 **sunnypilot** (MIT).
- 🆕 **A licence label is not a licence, in both directions.** `autoware-safety-island` reads as
  **"Other"** and is really **Apache-2.0** (file: `license.rst`) — a false negative that would have cost
  this KB a 608-commit safety repo. `autoware_latent_drive` sits in the **same org** with **no licence at
  all**, and `petrpatek/obd2-mcp-server` and `j2534-mcp-server` both claim MIT in a README with no file —
  false positives. **Fetch the file. Every time. The org's reputation is not a grant.**
- **Weak-copyleft / file-level — usable with care:** VSS and esmini (MPL-2.0), SUMO (EPL-2.0),
  python-can (LGPL-3.0).
- **Strong copyleft — do not put client proprietary code on top without legal sign-off:** Fleetbase and
  OpenRemote (AGPL-3.0), Odoo (LGPL-3.0 core), **OpenAutoCore (GPL-3.0)**. See `verticals/solutions.md`.
- 🆕 **Model weights are licensed separately from code.** Alpamayo 1.5: repo Apache-2.0, **weights
  OpenMDW-1.1**. Never infer the checkpoint's terms from the repository badge.
- **Non-commercial data traps:** DriveLM's language data (CC BY-NC-SA 4.0) and most AV *datasets*.

## 🆕 Negative results settled 2026-10-31 — do not re-search these

- **`Dolibarr/dolibarr`** (7.8k★, PHP, default branch `develop`) — **GPL-3.0**, read from the sidebar.
  Surfaced as an ERP/CRM base for aftersales. Ruled out on licence; **Odoo (LGPL-3.0) and Apache OFBiz
  (Apache-2.0) already cover this slot** and OFBiz is the permissive one.
- **`navariltd/Fleet-Management-System`** (12★, 18 forks, default branch `develop`) — **GPL-3.0** per README
  and badge; the GitHub sidebar shows a License link but **does not name the licence**, so the README is the
  source. Frappe-framework fleet solution. Copyleft, so not a base for a proprietary deliverable.
- **No open-source Dealership Management System exists.** Re-searched 2026-11-13 with
  `open source platform automotive ERP CRM dealership MIT Apache`; **unchanged across five passes.** The
  search returns general-purpose ERP/CRM only, and explicitly confirms the gap: none of the candidates
  carry dealership primitives — **no inventory-by-VIN, no deal jacket, no DMS integration**. A dealer
  engagement still means building those modules on a general ERP, against the Auto Agent Protocol contract
  in Layer 5.
- **No LATAM-origin automotive repository found**, in this or any previous pass. **Five passes, zero.**
  This is now a durable finding rather than a miss: see `intel/market.md` → LATAM for what it implies.
- 🆕 **Generic "AI agent" searches remain a dead end for this industry.** `top open source AI agents
  automotive 2026 github MIT` returned only general-purpose frameworks (OpenClaw, OpenCode, OpenHands,
  CrewAI, Hermes Agent) with **no automotive content**, plus the note that **AutoGPT is archived as of
  28 Jan 2026**. The productive query shape is the **protocol**, not the category — `automotive MCP server
  vehicle diagnostics` returned eight real projects. Recorded so the next pass spends its searches better.
- 🆕 **Three "MIT" ERP/CRM claims from search summaries failed verification** — `idurar-erp-crm` is
  **AGPL-3.0**, Huly is **EPL-2.0 and frozen**, `open-mercato` is MIT with a **commercial
  `packages/enterprise` carve-out**. Details in `verticals/solutions.md`. Do not re-trust secondary
  licence claims for this layer.

## Declared channel gap

🔴 **New this pass: `huggingface.co` does not resolve from this session** (DNS failure, consistent with the
proxy's allowed-domain policy). Every model-weight repository referenced in this file — AutoE2E's
`AutowareFoundation/auto_e2e` checkpoints, `Qwen/Qwen-Drive-1.0-4B`, OpenDriveVLA's 0.5B checkpoint — is
therefore **unverified as to its licence**. This is not a cosmetic gap: this KB has already caught
**Alpamayo 1.5 shipping Apache-2.0 code with OpenMDW-1.1 weights**, and a secondary source makes the same
claim about AutoE2E. **Do not ship a fine-tuned derivative of any of these to a client until the model card
is read.** Next pass: request `huggingface.co` in the session's allowed domains.

🔴 **`eclipsesdv.org` could not be fetched on 2026-10-26** (DNS resolution failure through the available
fetch channel), so S-CORE release notes were read from the **GitHub releases page** plus trade press
instead of the project's own announcements. The GitHub dates above are primary and reliable; the module
contents attributed to 0.6.0 are press-sourced and should be confirmed against the project site when it
is reachable. **`api.github.com` returns HTTP 403 for repositories not attached to this session**, which is
why licences and stars are read from rendered repository pages rather than the API — the same constraint
the 2026-10-15 pass recorded.

---
*Verified 2026-11-13 (previous passes 2026-10-31, 2026-10-26). Figures marked 🆕/🔄 were read from the rendered repository page today;
⏸ carried from an earlier pass and labelled; ⚪ URL present in the org listing but licence/stars deliberately left blank rather than guessed.
`curl` and `api.github.com` are both 403 in this session, so the rendered page and `raw.githubusercontent.com` are the verification channels.
See `verticals/solutions.md` for full customisable platforms and `agents/top.md` for the exclusion list.*

---

## 🆕 Layer H — the permissive diagnostics & ECU-tooling stack (added 2026-11-21, fourth pass)

**Why this layer did not exist until now, and it is the same cause as Layer G:** it was never absent
from the world, only from the queries. Layer G was missed because five passes said *automotive* to a
layer that calls itself *industrial anomaly detection*. Layer H was missed because the `gh` queries were
**too long** — `search/repositories` matches name/description/topics and ANDs every term, so a
five-word phrase returns a literal zero. Eight short queries returned 27 unheld repos. **Full defect
write-up: `agents/trending.md` → 2026-11-21 fourth pass.**

This is the layer a studio actually bills against: **UDS/OBD diagnostics, ECU bench tooling and
AUTOSAR data plumbing**, and unlike the AV-stack layers it is **permissively licensed nearly throughout.**

| Repo | Licence (byte-read 2026-11-21) | ★ | Pushed | Why it is here |
|---|---|--:|---|---|
| [pylessard/python-udsoncan](https://github.com/pylessard/python-udsoncan) | **MIT** — `master/LICENSE.txt`, 1,074 b | **746** | 2026-10-26 | **The anchor of this layer.** A Python implementation of **UDS (ISO-14229)**, the diagnostic protocol every ECU on a modern vehicle speaks. Clean permissive grant, actively pushed. Any diagnostics agent that needs to *do* something rather than describe it starts here. |
| [oxibus/automotive_diag](https://github.com/oxibus/automotive_diag) | **MIT** — `main/LICENSE-MIT`, 1,139 b | 105 | 2026-11-09 | **UDS (ISO-14229-1), KWP2000 (ISO-14230), OBD-II (ISO-9141) and DoIP (ISO-13400) definitions** as a Rust crate. The constants/enums layer — pairs with `python-udsoncan` rather than competing: Rust for on-vehicle/edge, Python for the bench and the agent. Dual-licensed (`LICENSE-MIT` present; Apache variant typical of Rust crates). |
| [ecubus/EcuBus-Pro](https://github.com/ecubus/EcuBus-Pro) | ⚠️ **Apache-2.0 *declared in `package.json` v0.8.68*; NO `LICENSE` FILE IN THE TREE** | **914** | 2026-11-05 | An open **CANoe/CAPL-class ECU development bench**: **UDS, CAN-TP, DoIP, LIN, TypeScript scripting "like CAPL", HIL test**. Functionally the most valuable single tool in this layer — commercial equivalents are five-figure seats. ⚠️ **Probed `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `license`, `COPYING` on `main` and `master`: all 404.** The grant is a metadata field with no licence text in the repo. **Fine to evaluate; get a `LICENSE` file added before it sits under a client deliverable.** |
| [cogu/autosar](https://github.com/cogu/autosar) | **MIT** — `master/LICENSE`, 1,088 b | 503 | 2026-10-16 | Python modules for reading/writing **AUTOSAR XML (ARXML)**. ARXML is the interchange format for AUTOSAR ECU configuration, and this is the permissive way to generate and diff it programmatically. Direct pair for `automotive-skills-suite`'s ARXML skill. |
| [COVESA/vsomeip](https://github.com/COVESA/vsomeip) | **MPL-2.0** — `master/LICENSE`, 16,725 b | **1,471** | 2026-11-13 | An implementation of **SOME/IP** (Scalable service-Oriented MiddlewarE over IP), the service protocol of automotive Ethernet. **COVESA-governed**, i.e. an actual industry consortium rather than a lone maintainer. ⚠️ **MPL-2.0 is file-level weak copyleft:** modified MPL files must stay MPL, but linking proprietary code alongside is permitted. Usable — with the file boundary respected. |
| [COVESA/dlt-viewer](https://github.com/COVESA/dlt-viewer) | **MPL-2.0** — `master/LICENSE.txt`, 372 b (short-form pointer) | 557 | 2026-11-19 | **Diagnostic Log and Trace (DLT)** viewer — AUTOSAR's standard logging transport. The companion to `vsomeip` for anything that has to read vehicle logs at scale. Same MPL file-boundary caveat. |
| [toyota-connected/ivi-homescreen](https://github.com/toyota-connected/ivi-homescreen) | **Apache-2.0** — `main/LICENSE`, 571 b | 404 | **2026-11-21** | A **Flutter embedder for automotive/embedded displays** — Wayland, DRM/KMS, EGL, Vulkan incl. zero-copy. Maintained by **Toyota Connected North America**, pushed today. The permissive route to an IVI/cluster UI without licensing a HMI stack. ⚠️ 571 bytes is the **short-form Apache notice**, not the full text — read and confirmed to grant Apache-2.0 unambiguously (*"Licensed under the Apache License, Version 2.0"*, Copyright 2020 Toyota Connected North America). |
| [OpenSparX/MasterAgent](https://github.com/OpenSparX/MasterAgent) | **Apache-2.0** — `main/LICENSE`, 11,259 b | **966** | 2026-09-28 | *"Build AI agents that run 100% on-device. Sub-100 ms latency on Qualcomm NPU. Zero cloud dependency."* **Not automotive-labelled, which is why no pass saw it** — but Qualcomm NPUs are the dominant in-cabin compute, and "no cloud" is the in-vehicle constraint. The permissive base for a cabin agent that must work in a tunnel. |
| [Chanchaldhiman/CANviz](https://github.com/Chanchaldhiman/CANviz) | **MIT** — `main/LICENSE`, 1,076 b | 299 | 2026-08-08 | Browser-based **CAN bus analyzer** working off low-cost USB hardware. The zero-install triage tool for a workshop or a demo. |
| [kkonteh97/SwiftOBD2](https://github.com/kkonteh97/SwiftOBD2) | **MIT** (API; not byte-read this pass) | 163 | 2026-01-26 | Swift **OBD-II** library — live data, DTC clearing. The iOS half of a diagnostics product; `CarDash` is the Android half. |
| [the-can-opener/simple-elm](https://github.com/the-can-opener/simple-elm) | **MIT** (API; not byte-read this pass) | 19 | 2026-04-20 | Small **ELM327** helper for serial OBD/CAN adapters. Listed for one specific reason: it is the **permissive replacement for `Ircama/ELM327-emulator`, which is CC-BY-NC** and therefore unusable in a commercial engagement. |
| [sw-mobility/open-sdv](https://github.com/sw-mobility/open-sdv) | **Apache-2.0** — `main/LICENSE`, 11,357 b, canonical | 12 | 2026-11-16 | *"Open Software Defined Vehicle Framework."* **12★ — a seed, not a platform**, recorded as a watch item because a canonical Apache grant on an SDV framework is rare (compare `de4sdv/DE4SDV` at 13★ in Layer D). |

### Perception/AV additions found by the same sweep

| Repo | Licence (byte-read) | ★ | Pushed | Note |
|---|---|--:|---|---|
| [autonomousvision/transfuser](https://github.com/autonomousvision/transfuser) | **MIT**, 1,073 b | **1,616** | 2026-09-21 | **[PAMI'23] TransFuser** — transformer-based multi-modal sensor fusion for autonomous driving (+ [CVPR'21]). One of the standard CARLA leaderboard baselines, and **MIT**, so a client prototype can start from a published baseline rather than a blank repo. |
| [sjtuyinjie/Ultra-Fusion](https://github.com/sjtuyinjie/Ultra-Fusion) | **MIT**, 1,074 b | 930 | 2026-08-29 | Tightly-coupled **multi-sensor fusion SLAM under sensor degradation** and spatiotemporal misalignment. The failure-mode case — degraded/misaligned sensors — is the one that matters in production and is usually the one no baseline handles. |
| [YuruiAI/DistillDrive](https://github.com/YuruiAI/DistillDrive) | **MIT**, 1,063 b | 127 | 2026-08-30 | **[ICCV 2025]** end-to-end multi-mode driving **distillation**. Distillation is the deployability lever: it is how an E2E planner gets small enough for vehicle compute (same role `Scene3DLite` plays in Layer F). |
| [jiachenli94/Awesome-Interaction-Aware-Trajectory-Prediction](https://github.com/jiachenli94/Awesome-Interaction-Aware-Trajectory-Prediction) | **MIT** (API) | **1,696** | 2026-08-24 | A curated state-of-the-art index for **trajectory prediction**. A reading list, not a dependency — the fastest way to brief an engagement team on the prediction literature. |

### 🔴 What this sweep refused — read before reusing any V2X or cooperative-driving code

Three grants were refused on byte-read, and **all three arrived as `NOASSERTION` from the API**:

- **[ucla-mobility/OpenCDA](https://github.com/ucla-mobility/OpenCDA)** (1,174★) — **Academic
  Software License, not open source.** Grant runs only to *"academic or nonprofit researchers"*;
  *"you are prohibited from further transferring the Software — including any derivatives you make
  thereof"*; *"Commercial entities: please contact the UCLA Mobility Lab … for licensing
  opportunities."* **Hard exclusion** — a cooperative-driving prototype built on it is undeliverable.
- **[riebl/vanetza](https://github.com/riebl/vanetza)** (231★) — **CC-BY-NC, 43,043 b.** The open
  implementation of the **ETSI C-ITS protocol stack**: non-commercial.
- **[Ircama/ELM327-emulator](https://github.com/Ircama/ELM327-emulator)** (708★) — **CC-BY-NC,
  20,849 b**, and it is what MIT-licensed `Automotive-AI` tells you to install to test without a car.

⚠️ **The V2X/C-ITS neighbourhood has no permissive anchor.** `vanetza` CC-BY-NC, `riebl/artery`
GPL-2.0, `eclipse-mosaic/mosaic` EPL-2.0, `sommer/veins` GPL-2.0, `DriveX-devs/VaN3Twin` GPL-2.0.
Permissive options exist only on the *research dataset/model* side —
[DerrickXuNu/v2x-vit](https://github.com/DerrickXuNu/v2x-vit) MIT (348★, stale 2024-09),
[DerrickXuNu/CoBEVT](https://github.com/DerrickXuNu/CoBEVT) Apache-2.0 (263★, stale 2024-08),
[ai4ce/V2X-Sim](https://github.com/ai4ce/V2X-Sim) Apache-2.0 (147★, stale 2025-01). **So a V2X
engagement in EMEA is a copyleft-compliance conversation from day one, not a licence-shopping exercise.**
The one permissive, current, policy-side asset is
[openmobilityfoundation/mobility-data-specification](https://github.com/openmobilityfoundation/mobility-data-specification)
— **CC-BY-4.0** (14,527 b), a *data specification* for right-of-way regulation and geofencing, 754★.
