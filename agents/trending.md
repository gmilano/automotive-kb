---
industry: automotive
region: Global
updated: 2026-11-24
---

# 📈 Trending AI agents & models — Automotive

> **APPEND-ONLY.** Newest dated section on top; history preserved below. Never rewrite earlier sections.

## 2026-11-24 (third pass) — the data-space / supply-chain agent plane

**Window:** 2026-11-24 ~02:00Z. **Third pass of today**; the second pass (charging interface) and the
first pass are preserved immediately below, unchanged, as is all earlier history.
**Why a third plane:** control grep across all 9 files = **0 mentions** of `Catena-X`, `Tractus-X`,
`dataspace`, `data space`, `battery passport`, `Lanelet2`, `intrusion detection`, `UBI`,
`insurance telematics`. Virgin ground, and it is where the **18 Feb 2027 battery-passport duty** lands.
**Channel:** `gh api -X GET search/repositories` for stars/SPDX/`pushed_at`; **every licence byte-read**
from `raw.githubusercontent.com` (8 filenames × default-branch-resolved + `main` + `master`); liveness
via `git ls-remote --exit-code`; **control: a fabricated slug returned DEAD.**

### 🔴 Headline — the most-starred EDC distribution is *not open source*, and a correct byte-read said it was

`sovity/edc-ce` (96★, top hit for `topic:catena-x`) byte-reads at **439 B** and defaults to
**Elastic License 2.0**, naming Apache-2.0 only as an alternative for header-marked files. The grep
matched `Apache License` and mislabelled it. **New standing rule: compare the licence file's size to the
canonical length of the licence it names** — canonical Apache-2.0 measured at **10,141–11,559 B** this
pass, so **439 B naming Apache is a pointer, not a grant.** Any sub-2 KB file naming Apache/GPL/MPL/EPL
must be read as prose. Full write-up at `agents/top.md` **T1**.

### Agent tier, measured rather than described

**`catena-x agent` → 4 repositories total**, top result 1★, two unrelated. **There is no Catena-X-native
agent framework.** The adapter tier over AAS and EDC is what exists:

| Repo | ★ | Licence (byte-read) | Note |
|---|---|---|---|
| [SAP/aas-mcp-server](https://github.com/SAP/aas-mcp-server) | 9 | ✅ Apache-2.0 (11,356 B) | OpenAPI→MCP bridge for AAS APIs; backend-agnostic (SAP BNAC / BaSyx / FA³ST). **Vendor-maintained — the strongest row here.** |
| [eclipse-basyx/basyx-pdf-to-aas](https://github.com/eclipse-basyx/basyx-pdf-to-aas) | 17 | ✅ MIT (1,081 B) | PDF datasheet → AAS submodel via LLM + ECLASS. Attacks the costliest manual step in onboarding. |
| [artamrj/tractusx-rag-mcp](https://github.com/artamrj/tractusx-rag-mcp) | 1 | ✅ Apache-2.0 (11,357 B) | Tractus-X docs RAG + MCP. **Publishes a 60-question eval: 100 % Hit@8, 98 % faithfulness, 80 % correctness.** |
| [artiso-ai/dppvalidator](https://github.com/artiso-ai/dppvalidator) | 10 | ✅ MIT (1,065 B) | Digital Product Passport validator. |
| [hadijannat/aas-ai-editor](https://github.com/hadijannat/aas-ai-editor) | 3 | ✅ MIT (1,083 B) | LLM-assisted AAS editing. |
| [soofi-project/edc-mcp](https://github.com/soofi-project/edc-mcp) | 3 | ✅ MIT (1,065 B) | MCP over EDC. |
| [Pareo-AI/pythia-edc](https://github.com/Pareo-AI/pythia-edc) | 2 | ✅ MIT (1,079 B) | EDC agent tooling; **pushed 2026-11-23**. |
| [connected-intelligent-systems/edc-mcp](https://github.com/connected-intelligent-systems/edc-mcp) | 0 | ✅ MIT (1,065 B) | Second independent MIT EDC-MCP — convergence signal. |
| [dungnotnull/scope3-carbon-emissions-tracking-agent-skill](https://github.com/dungnotnull/scope3-carbon-emissions-tracking-agent-skill) | 4 | ✅ MIT | Scope-3 emissions as an agent skill (the PCF leg of the passport). |

⚠️ **Median of the eight non-SAP rows = 3★.** This tier is pre-product while the platform beneath it is
production-grade — so the engagement shape is **"build the agent, adopt the platform."**

### Rejected this pass, with the reason

| Repo | ★ | Verdict |
|---|---|---|
| [sovity/edc-ce](https://github.com/sovity/edc-ce) | 96 | 🔴 **Elastic License 2.0** by default — not open source. Hard exclusion for hosted delivery. |
| [Mobile-Telematics/TelematicsApp-Android](https://github.com/Mobile-Telematics/TelematicsApp-Android) | 76 | 🔴 **Proprietary "Damoov Service Terms"** (18,721 B). Top hit for `insurance telematics` is a commercial SDK. |
| [batterypass/BatteryPassDataModel](https://github.com/batterypass/BatteryPassDataModel) | 70 | 🔴 **No licence file** (8 names × 3 branches) — the data model for a *mandated* passport carries no grant. |
| [open-dpp/open-dpp](https://github.com/open-dpp/open-dpp) | 35 | ⚠️ **AGPL-3.0** (34,522 B). Most-starred maintained DPP app; self-host only. |
| [YuchenXia/AASbyLLM](https://github.com/YuchenXia/AASbyLLM) | 21 | ⚠️ **CC-BY-4.0 on code** (no NC/ND verified). Cite, don't vendor. |
| [EunomiaUPM/ds-agent](https://github.com/EunomiaUPM/ds-agent) | 5 | ⚠️ **AGPL-3.0** (35,148 B). |
| [quickhdsdc/AAS_LLMAgent_MCP_Server](https://github.com/quickhdsdc/AAS_LLMAgent_MCP_Server) | 1 | 🔴 **Bespoke "Dachuan Shi Non-Commercial Research License 1.0"** (`LicenseRef-Dachuan-Shi-NC-1.0`, 4,789 B). |

### ✅ CC-BY-4.0 inside Tractus-X is the house convention, not a defect

Four CC files byte-read, **all four plain CC-BY-4.0 with zero NonCommercial and zero NoDerivatives**
(checked by string). `industry-core-hub` carries **both** badges: Apache-2.0 for code, CC-BY-4.0 for
non-code. So CC-BY on a spec/semantic-model repo here is the rule — **flag it only when the repo ships
executable code.**

## 2026-11-24 (second pass) — the charging-interface plane

**Window:** 2026-11-24 00:56Z → 01:3xZ. This is the **second pass of 2026-11-24**; the first pass's
section is preserved immediately below, unchanged, as is all earlier history.
**Why a new plane and not a rewrite:** the first pass of today had already swept this KB's 277 addresses
47 min earlier. Re-verified independently rather than re-run (**272 live / 3 dead of 275 extracted
slugs, and the 3 dead are exactly the 3 this KB already publishes as dead** at `repos/trending.md`
— address hygiene confirmed, 0 new dead). So this pass opened virgin ground instead: control grep for
`OCPP`/`OCPI`/`EVerest`/`SteVe`/`charging station` = **0 mentions in all 9 files**.
**Channel:** `gh api -X GET search/repositories` for stars/SPDX/`pushed_at`; **every licence byte-read**
from `raw.githubusercontent.com` with the **default branch resolved by `git ls-remote --symref HEAD`**;
liveness via `git ls-remote --exit-code` (control: a fabricated slug returned DEAD).

### The agent tier of this plane, measured rather than described

**`charging station agent license:apache-2.0` → 0 repos.** The operator-side charging agent does not
exist. What exists is nine **driver-side** MCP servers, median 1★, max 10★, all single-author, and
**all nine byte-read MIT**:

| Repo | ★ | Licence (byte-read) | Note |
|---|---|---|---|
| [shiv3/ocpp-cp-simulator](https://github.com/shiv3/ocpp-cp-simulator) | 48 | ✅ Apache-2.0 (11,356 B) | Simulator built *for AI-agent testing* — the harness, not the agent |
| [Casperjuel/abrp-mcp](https://github.com/Casperjuel/abrp-mcp) | 10 | ✅ MIT (1,067 B) | A Better Route Planner |
| [mattoddie/bluelink-mcp](https://github.com/mattoddie/bluelink-mcp) | 3 | ✅ MIT (1,066 B) | Hyundai/Kia charge state |
| [holger1411/unofficialzaptecMCP](https://github.com/holger1411/unofficialzaptecMCP) | 2 | ✅ MIT (1,072 B) | Zaptec chargers |
| [Zenotech-bv/teslafi-mcp](https://github.com/Zenotech-bv/teslafi-mcp) | 2 | ✅ MIT (1,068 B) | TeslaFi API |
| [stuchapin909/open-charge-finder](https://github.com/stuchapin909/open-charge-finder) | 1 | ✅ MIT (1,069 B) | Station location data |
| [mahrukhzulfiqar/gridwise](https://github.com/mahrukhzulfiqar/gridwise) | 1 | ✅ MIT (1,063 B) | Cheapest/greenest charge window, Denmark |
| [winsparking/chargingnearme-mcp](https://github.com/winsparking/chargingnearme-mcp) | 0 | ✅ MIT (1,073 B) | US public stations |
| [javierojan/askacharge-mcp](https://github.com/javierojan/askacharge-mcp) | 0 | ✅ MIT (1,091 B) | The only one that *operates* chargers |

### Optimization tier — real, and deliberately not called "LLM agents"

| Repo | ★ | Licence (byte-read) | Note |
|---|---|---|---|
| [StavrosOrf/EV2Gym](https://github.com/StavrosOrf/EV2Gym) | 250 | ✅ MIT (1,076 B) | V2G env for large-scale charging optimization; multi-agent RL |
| [StavrosOrf/EV-GNN](https://github.com/StavrosOrf/EV-GNN) | 34 | ✅ MIT (1,076 B) | GNNs to scale RL |
| [StavrosOrf/DT4EVs](https://github.com/StavrosOrf/DT4EVs) | 23 | ✅ MIT (1,076 B) | Decision Transformer, offline RL |
| [TUMFTM/REVOL-E-TION](https://github.com/TUMFTM/REVOL-E-TION) | 17 | ✅ Apache-2.0 (11,364 B) | Site-level energy optimization (TU München) |

⚠️ **Three of these four share one maintainer** (`StavrosOrf`) — concentration risk, stated.

### Rejected this pass, with the reason

| Repo | ★ | Verdict |
|---|---|---|
| [nader0913/ocpp-rag](https://github.com/nader0913/ocpp-rag) | 48 | 🔴 **PolyForm Noncommercial 1.0.0** (byte-read, 4,712 B). The most-starred OCPP RAG/MCP repo; API says `NOASSERTION`. Hard exclusion. 2nd PolyForm-NC sighting in this fleet. |
| [AndyShaman/BYDMate](https://github.com/AndyShaman/BYDMate) | 538 | 🔴 No licence, and **not an agent** — a BYD DiLink head-unit app. Keyword collision; recorded so it is not re-found. |
| [NERVsystems/osmmcp](https://github.com/NERVsystems/osmmcp) | 32 | ⚪ MIT but **out of plane** — an OpenStreetMap MCP where EV charging is one tool. The top hit for `ev charging llm`, which is the measurement, not a recommendation. |

### 🔴 Correction to this pass's own instrument (detail as N26 in `intel/trends.md`)

An earlier draft labelled **SteVe, OCPP.Core, pyPLC and ccs32clara as AGPL-3.0**. All four are
**GPL-3.0**. Cause: **GPL-3.0 §13 contains the string "GNU Affero General Public License"**, so a
detector that matches `AFFERO` before `GENERAL PUBLIC` inverts them — the exact mirror of the
`LGPL`→`GPL` bug this KB recorded on 2026-11-21. **Ordering body-text matches has no correct answer;
anchor on the title line.** Corrected before commit; 0 wrong licences published.

## 2026-11-24

**Window:** 2026-11-21 14:52Z → 2026-11-24. The four sections below are preserved unchanged.
**Channel:** `gh api -X GET search/repositories` for metadata; **every licence byte-read** from
`raw.githubusercontent.com`; liveness via `git ls-remote --exit-code`. **47 new addresses → 47 live.**

### 🔴 THE CORRECTION OF THIS PASS: this KB published a wrong layer-wide licence verdict three days ago

On 2026-11-21 this KB wrote, as finding (7) and as a **planning input for pricing**, that *"the V2X/C-ITS
layer has **NO PERMISSIVE ANCHOR AT ALL**"*, concluding: *"V2X work must quote legal review in the SOW."*

**One short query (`topic:v2x stars:>50`) falsified it:**
[ika-rwth-aachen/etsi_its_messages](https://github.com/ika-rwth-aachen/etsi_its_messages) — **MIT**,
byte-read `LICENSE` 1,117 bytes, *"Institute for Automotive Engineering (ika), RWTH Aachen University"*,
83★, pushed 2026-10-28. ROS 2 support for ETSI ITS messages. Plus
[VjiaLi/V2U4Real](https://github.com/VjiaLi/V2U4Real) — **MIT**, 75★, CVPR 2026.

**How the error was produced, because the mechanism is reusable and will recur:** the 2026-11-21 verdict
was assembled from the rows *that pass happened to touch* — `vanetza`, `artery`, `mosaic`, `veins`,
`OpenCDA` — all of which are stack-and-simulation projects, and all of which are non-permissive. The
sample was real; the **quantifier** was invented. "Every row I looked at is copyleft" became "the layer
has no permissive anchor."

**The rule this KB now carries:** 🔴 **never write a layer-wide licence quantifier from a sample.** A
statement of the form *"layer X has no permissive option"* requires a **licence-filtered query that
returns ~nothing** — `topic:v2x license:mit` — exactly the instrument that closed the DMS question
honestly on 2026-11-21. That pass had the right tool in its hand for one gap and asserted from a sample
on another, in the same hour. **The corrected, layered verdict is in `agents/top.md` → W1.** It is also
commercially better news: the message layer is clean, so only simulation carries legal review.

### 🔴 Second defect: the discovery legs are **monolingual**, and six passes of "zero LATAM-origin repos" was its output

`automotriz` → **2,458 repositories.** Every prior leg searched in English. Full write-up, licence
distribution (**95 of the first 100 carry no licence at all**) and the corrected client sentence are in
`repos/trending.md` → this date. Recorded here because it is the **same class of error as the V2X one**:
a confident negative produced by an instrument that could not have found a positive.

**Both defects this pass, and the four from 2026-11-21, are one failure mode:** this KB is reliable when
it *measures* and unreliable when it *generalises from what it measured*. The measurements have all held
up under re-test. The quantifiers around them keep breaking.

### 🆕 New agent-tier rows — six, and only one has a community

Full table with licences in `agents/top.md` → W3. Summary: **`LGDiMaggio/predictive-maintenance-mcp`**
(MIT, **118★**, pushed 2026-11-23) is the only one with traction — an MCP server for condition
monitoring, and the first maintained MCP on the *plant-floor* side of automotive.
`Nemeson/C-ITS-Expert` (MIT, 1★) is a V2X/C-ITS validator as CLI+MCP. `decionis/kervix` (Apache-2.0,
**0★, created 2026-11-21**) puts agent execution authority **in the QNX kernel** — *"agents propose; QNX
decides"* — which is architecturally the thing **P16** argues for and the first repo to implement it
below user space. `eric-rolph/beamng-mcp` (MIT, 2★) is a second sim-behind-MCP after
`drivingbench_harness_code`. `dsdtsolutionsllc/manus-automotive-skills-suite` (MIT, 2★) ports the
152-skill suite to another agent runtime. `SrinivasReddyMudem/automotive-lifecycle-agents` (MIT, 0★).

**The honest headline is the distribution, not the count:** one repo at 118★, five at 0–2★. The
automotive agent layer is still *shapes being tried*, not a market. Said plainly so that a later pass
does not read six rows as six options.

### 🆕 The agent-layer gap that moved: **the assurance tier now has tools, not just skills**

`topic:iso26262` — a query never run before in this KB — returned 73 repositories and with them the
answer to a standing weakness in **P14**. Until today, the assurance-artefact factory rested entirely on
**skill suites that write documents**. It now has four permissive tools that **check code against a
standard**, led by **[github/codeql-coding-standards](https://github.com/github/codeql-coding-standards)
— MIT, 235★, MISRA C/C++ and AUTOSAR C++14 as CodeQL queries, maintained by GitHub.**

This changes the shape of an ISO 26262 engagement: compliance evidence becomes **CI output** rather than
a consultant's assertion or a static-analyser licence resale. Full tier in
`repos/foundations.md` → Layer I; the pattern rewrite is **P26**.

### 🔄 Anchor check — one instrument, and the standing no-cross-write rule honoured

`gh api search/repositories`, 2026-11-24: **openpilot 64,220★** (⬆ from ~63,000) / 11,407 forks / MIT /
pushed **today**; carla 14,692★; autoware 12,275★; vision_pilot 929★; **teslamate-mcp 142★ — still the
largest automotive MCP**, verified by enumerating the field (next largest 5★, then 2★, 0★, 0★).

⚠️ **`jherrodthomas/automotive-skills-suite` reads 2,878★ from the search index today.** The KB's
standing figure is **2,907★ page-rendered (p941)**. Per the rule recorded on 2026-11-21 —
**never refresh a star count with a different instrument than the one that set it** — the 2,907 figure
**is left standing** and the index reading is recorded here, labelled, as a separate observation. The
~29-count difference is index lag, not a decline. *This is the second pass to confirm the gap and the
direction, which is now enough to call it a stable property of the two channels rather than a one-off.*

### ⏸ Verified-and-stale, because stars are not maintenance

[vietanhdev/open-adas](https://github.com/vietanhdev/open-adas) — MIT, **509★**, pushed **2023-10-24**.
[Lyric0620/ETSAuto](https://github.com/Lyric0620/ETSAuto) — MIT, 184★, pushed **2024-03-12**; its grant
file is spelled **`LICENCE`**, so a probe list without the British spelling reports "no licence" on an
MIT repo. Both now carry ⏸ in `repos/foundations.md`.

## 2026-11-21 — fourth pass (14:50Z)

**Window:** 2026-11-21 13:54Z → 14:50Z (≈1 hour, same day — the **fourth** automotive pass today; the
three sections below are preserved unchanged). **Channel:** byte-read `LICENSE` from
`raw.githubusercontent.com`, `gh api -X GET search/repositories` for metadata, `WebFetch` on
`github.com` for page-rendered star/fork counts.

**This pass did not re-measure the shelf.** p941 rewrote this base 56 minutes earlier. It went after the
*shape of the queries* instead, and that turned out to be where the KB's "discovery ceiling" actually lived.

### 🔴 METHOD DEFECT FOUND IN THIS KB'S OWN INSTRUMENT — long `gh` queries return a FALSE ZERO

The single most important finding of this pass, because it has been silently capping discovery.

`gh api -X GET search/repositories` with a long natural-language `q` returns **zero items** — not few, zero:

| Query sent | Result |
|---|---|
| `automotive manufacturing quality inspection AI pushed:>2026-06-01 stars:>100` | **0 items** |
| `vehicle predictive maintenance machine learning pushed:>2026-06-01 stars:>50` | **0 items** |
| `software defined vehicle SDV platform pushed:>2026-06-01 stars:>50` | **0 items** |
| `AUTOSAR adaptive pushed:>2026-01-01 stars:>100` | **0 items** |
| `in-vehicle voice assistant LLM cockpit pushed:>2026-06-01 stars:>30` | **0 items** |

Re-run **short**, the same index is dense:

| Query sent | Result |
|---|---|
| `autosar stars:>50` | **10 items**, incl. `cogu/autosar` MIT 503★ and `autoas/as` 966★ |
| `software-defined-vehicle` | **10 items**, incl. `eclipse-leda/leda`, `sw-mobility/open-sdv` |
| `topic:adas stars:>50` | **10 items** |
| `topic:v2x stars:>50` | **10 items**, incl. the `riebl` ETSI C-ITS stack |

**`search/repositories` matches name, description and topics — not README prose — and ANDs every
term.** A five-word phrase therefore demands all five words inside one short description field, which
almost nothing satisfies. **The zero is an artifact of query length, not a statement about the world.**

⚠️ **This is the `anomalib` lesson a second time, and it generalises past automotive: a `0 repos` cell
is a claim about the instrument until a SHORT query has been tried.** Any KB in this fleet carrying
`0 repos` gaps gathered from long queries should re-probe them short before trusting the gap. Had this
pass written those five zeros down as findings, it would have published five fabricated gaps — and an
informed gap is only information when the instrument was actually pointed at the question.

### 🆕 Discovery: 27 unheld repos from eight short queries

Deduped against all **202** github addresses this KB already holds: **49 unique hits → 22 already held →
27 genuinely new.** The ceiling was query shape. Rows written to `repos/foundations.md` → **Layer H**.
The two that matter most for a studio:

| Repo | Licence (byte-read) | ★ | Note |
|---|---|--:|---|
| [ecubus/EcuBus-Pro](https://github.com/ecubus/EcuBus-Pro) | ⚠️ **Apache-2.0 declared in `package.json` only — NO `LICENSE` FILE** | 914 | UDS, CAN-TP, DoIP, LIN, TS scripting "like CAPL", HIL test. An open CANoe-class bench. **See the licence caveat below — it is not a clean grant.** |
| [pylessard/python-udsoncan](https://github.com/pylessard/python-udsoncan) | **MIT**, `master/LICENSE.txt`, 1,074 b | 746 | UDS (ISO-14229) in Python. The clean permissive anchor for any diagnostics agent. |

### 🔴 Three licence traps, and one of them sits inside a repo this KB was about to recommend

**1. `Ircama/ELM327-emulator` is CC BY-NC — and it is the documented test path of an MIT agent.**
[Eloquent-Algorithmics/Automotive-AI](https://github.com/Eloquent-Algorithmics/Automotive-AI) is
genuinely **MIT** (byte-read, 1,061 b). Its README tells you to test without a car using
[Ircama/ELM327-emulator](https://github.com/Ircama/ELM327-emulator) — which byte-reads as
**CC-BY-NC, 20,849 bytes**. A client engagement is commercial use **by its own definition**, so *the
permissive agent's recommended development workflow is unusable as shipped.* The grant on the repo you
clone does not cover the tools its README tells you to install. **Licence-check the dev dependencies,
not just the deliverable.** (Mitigation: a real ELM327 dongle, or `the-can-opener/simple-elm`, MIT.)

**2. `ucla-mobility/OpenCDA` is not open source at all.** 1,174★, API reports `NOASSERTION`. The
byte-read is an **Academic Software License**: grant runs only to *"academic or nonprofit researchers"*,
*"you are prohibited from further transferring the Software — including any derivatives you make
thereof"*, and *"Commercial entities: please contact the UCLA Mobility Lab … for licensing
opportunities."* **Hard exclusion.** A cooperative-driving prototype built on it could not be delivered.

**3. `riebl/vanetza` is CC BY-NC.** The widely-used open implementation of the **ETSI C-ITS protocol
stack** (231★) byte-reads **CC-BY-NC, 43,043 bytes**. This bites precisely where EMEA V2X work lands.
Peer check: `riebl/artery` GPL-2.0, `eclipse-mosaic/mosaic` EPL-2.0 — the whole ETSI V2X simulation
neighbourhood is copyleft-or-worse, with **no permissive anchor found**.

> **Pattern across all three:** every one arrived as `NOASSERTION` or `None` from the API. The standing
> rule holds and is now 3-for-3 this pass — **a short or absent SPDX is a pointer, not a licence.**

### ⚠️ `EcuBus-Pro`: the API's Apache-2.0 came from `package.json`, not a licence file

Probed `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `license`, `COPYING` on both `main` and `master`: **all
404.** The repo's `package.json` (v0.8.68) declares `"license": "Apache-2.0"`. So the grant exists as a
**metadata field with no licence text in the tree** — weaker than a `LICENSE` file, and the first time
this KB has recorded that specific state. Usable for evaluation; **ask the maintainer to add a `LICENSE`
file before it goes under a client deliverable.** Recorded as *declared* Apache-2.0, not *byte-read*.

### 📉 Two instruments disagree on star counts — do NOT cross-write them

`jherrodthomas/automotive-skills-suite` is recorded in this KB at **2,907★** (p941, page-rendered). The
`gh` **search index** returns **2,876★** for the same repo in the same hour — **31 fewer (1.1%)**.

**This is not a 31-star decline.** It is two instruments: the search index lags the rendered page.
**Rule, and it is a correction to this KB's own practice: never refresh a star count with a different
instrument than the one that set it — doing so manufactures drift that never happened.** p941's
2,907★ is left standing, since page-rendered was its channel. Only like-for-like re-measurement counts.

Substantive drift on the same repo, which *is* real: the README headline now reads **"152 installable
Claude skills"**, and the API's description still says *"100+"*. The KB's existing **"76 builder+reviewer
pairs"** is correct and equals 152. **No correction needed — the KB was right and the API is stale.**

### ✅ Three new real agent rows — one current, two honestly legacy

Written to `agents/top.md`. All three are real, MIT and byte-read; only the third is a recommendation:

| Repo | Licence | ★ / forks | State |
|---|---|--:|---|
| [Eloquent-Algorithmics/Automotive-AI](https://github.com/Eloquent-Algorithmics/Automotive-AI) | **MIT**, 1,061 b | 38 / 14 | Voice OBD-II diagnostic assistant, 127 commits. **README's newest entry is 2024-03-17 and it pins `gpt-3.5-turbo-0125`** — a live reference implementation of the shape, on a two-year-old model. |
| [via-intelligent-vision/VIA-AI](https://github.com/via-intelligent-vision/VIA-AI) | **MIT**, 1,079 b | 59 / 26 | ACC + LKAS + CAN bus on an Android phone. ⚠️ **Legacy: `Copyright (c) 2019`, 1 commit, requires comma.ai White Panda + Giraffe (both discontinued) and an HTC U11+/U12+/Pixel 2.** Historical interest only. |
| [surendranb/CarDash](https://github.com/surendranb/CarDash) | **MIT**, 1,079 b | 61 / — | ✅ **The one worth keeping.** Android/Kotlin + Jetpack Compose OBD-II dashboard, **pushed 2026-08-03**. Persistent local vehicle-health ledger in **Room/SQLite**, **Google Gemini as an on-demand assistant**. README is explicit: *"No Data Collection"*, *"100% Local Storage"*, no account, no analytics, no ads. |

⚠️ **A 2026 listicle recommended both as current.** `medevel.com`'s "Top 15 Open-Source Car AI Projects
(2026)" lists VIA-AI as a live option; the repo's own bytes say 2019 and its hardware is off the market.
**A listicle's publication year is not the repo's freshness** — the same pathology as a licence badge on
a listicle, one layer up. (That article could not be read first-hand: `medevel.com` does not resolve
from this session. Candidate names came from search snippets; **every row above was then verified
against `raw.githubusercontent.com` and the repo page directly.**)

### ❌ Negative results — recorded so silence is not mistaken for coverage

- **`CarDash` — and this is the method defect catching its own author, inside one pass.** The first
  probe sent `CarDash OBD2 AI assistant` and got **zero**, which was about to be written down here as
  "may not exist under that name". It was re-run short on the strength of the finding above —
  `q=cardash` returns **eight repositories**, and the right one is real, permissive and current. It is
  now a row in `agents/top.md`, not a negative result. **The false zero was one edit away from being
  published as a gap in the same document that documents false zeros.**
- **`DriveSense`** resolved to [TensorTrove/DriveSense](https://github.com/TensorTrove/DriveSense) —
  **MIT, but 4★ and last pushed 2024-08-09.** Real, permissive, and too small/stale to carry a row.
- **`XiaomiAutoL3/DriveZero` re-probed as p941 asked: still NO licence file.** `main` and `master` both
  serve a README; no `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `COPYING` on either. The open item stays
  open — an unlicensed 147★ model, **unchanged, and still excluded.**
- **`iDoka/awesome-automotive-can-id`** (API: CC0-1.0, 1,033★) and **`linux-can/can-utils`** (API:
  `None`, 2,961★): **no licence file found at either root** under six filenames × two branches.
  `can-utils` is widely held to be per-file dual GPL-2.0/BSD-3 but **this pass could not byte-read a
  grant**, so both are left **unrecorded as usable** rather than guessed.

### 🔧 Correction to this file's own verification script

The pass's first licence classifier reported `TOSUN-Shanghai/TSMaster` and `autoas/as` as plain `GPL`.
**Both were wrong, and the cause is reusable:** LGPL's text *contains the string* "GNU GENERAL PUBLIC
LICENSE" in its preamble, so a grep for that phrase silently mislabels LGPL as GPL. Re-read matching
`LESSER` first: **TSMaster is LGPL-2.1** (26,526 b — the LGPL-2.1 full text length), **`autoas/as` is
GPL-3.0** (*"Version 3, 29 June 2007"*). `openmobilityfoundation/mobility-data-specification` resolved
the same way: not UNKNOWN but **CC-BY-4.0** (14,527 b) — a *data spec*, attribution-only, usable.

## 2026-11-21 — third pass (13:40Z)

**Window:** 2026-11-21 12:45Z → 13:40Z (≈1 hour, same day — the third automotive pass today). The two
earlier sections below are preserved unchanged. **This pass went after the three gaps this KB has
carried longest instead of re-measuring a shelf measured 55 minutes ago.** Two of the three moved.
**Channel:** `git ls-remote --symref` (liveness **and** default branch), byte-read `LICENSE` from
`raw.githubusercontent.com`, `gh api -X GET search/repositories` for metadata.

### 🆕 Gap CLOSED — plant-floor quality AI, after five passes at zero

Full detail in `repos/foundations.md` → **Layer G**. The headline: **[open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib)**,
**Apache-2.0** (byte-read, 11,357 bytes, canonical), **6,414★ / 1,047f, pushed 2026-11-20**.

**Why five passes missed it:** the searches all said *automotive*. This layer calls itself **industrial
anomaly detection** and never mentions cars. **The gap was in the query, not in the world** — worth
applying to every remaining `0-repos` gap in this KB and in the other eleven.

🔴 **And the trap that comes with it:** `anomalib`'s code is Apache-2.0; **MVTec AD, the benchmark
everything in this layer reports against, is CC BY-NC-SA 4.0 — non-commercial.** Code licence and
dataset licence are independent axes and **byte-reading `LICENSE` does not catch the second one.**

### 🔴 Gap CONFIRMED OPEN with a measured reason — driver monitoring (DMS)

Prior passes recorded "DMS = none." This pass establishes **why**, which is more useful than the count:

| Candidate | Measured | ★ | Pushed | Verdict |
|---|---|--:|---|---|
| [kiralygomba/nottired_guard](https://github.com/kiralygomba/nottired_guard) | 🔴 **GPL-3.0** — `LICENSE`, 35,149 bytes | **1** | ⚠️ **2024-03-08** | **Rejected, twice over.** The *only* framework-grade open DMS found — head pose + gaze + blink + yawn, with a 2025 peer-reviewed preprint behind it. **Copyleft *and* abandoned for 20 months.** |

Everything else returned by the leg is a **single-file eye-aspect-ratio demo** (MediaPipe or dlib,
0–3★, no temporal model, no gaze, no standards claim). **One search result advertised "EU regulation
C(2023)4523-compliant gaze-zone detection" without naming a repo — unverifiable, so not recorded.**

**The conclusion to carry, because it is a sales argument rather than an absence:** DMS is **mandated**
in the EU (GSR / UN R159-adjacent driver-attention requirements) and there is **no permissively-licensed
implementation to start from.** A regulatory mandate with zero viable open supply is **the strongest
build-versus-adopt case in this entire KB** — everywhere else the honest advice is "adopt the open base."

### 🔴 Gap STILL OPEN but better characterised — EV / battery AI

Five passes recorded `0 repos`. There is in fact a **populated but uniformly sub-scale** layer: the leg
returned ~10 SoC/SoH estimators, of which the two best are below. **Nothing here is a base to build on.**

| Candidate | Measured | ★ | Pushed | Verdict |
|---|---|--:|---|---|
| [ArpanBiswas99/Battery-State-of-Charge-Estimation](https://github.com/ArpanBiswas99/Battery-State-of-Charge-Estimation) | **MIT** — `LICENSE`, 1,069 bytes | 83 | ⚠️ 2024-01-22 | Best-of-breed of a weak field: FCN/CNN/LSTM SoC estimation on LG HG2 cells with Optuna tuning. **Dissertation-grade and dormant 22 months — a method reference, not a platform.** |
| [MayankGangwal-code/ev-battery-soc-estimation](https://github.com/MayankGangwal-code/ev-battery-soc-estimation) | **MIT** — `LICENSE`, 1,280 bytes (GitHub says `NOASSERTION`) | 0 | 2026-11-02 | Not recommendable at 0★, but **methodologically the most honest repo found this pass**: Extended Kalman Filter on a Thevenin cell model *versus* ML, on 62 real drive cycles from −20 °C to 40 °C. **It is also the specimen that explains `NOASSERTION`** — see below. |

**Revised gap statement:** the EV/battery gap is **not** "no open work exists." It is **"no open work
above hobby scale exists."** The physics-plus-ML correction architecture (EKF for the state, ML for the
residual) is the consensus design across the whole field — **take the architecture, leave the code.**

### 🆕 `NOASSERTION` explained, and the signal runs backwards

Measured twice this pass. Both are **verbatim licence text made non-matching by appending honest
information**, which defeats GitHub's near-exact-match classifier:

- `PythonRobotics` (30,951★) inserts a **contributors URL** after the copyright line → MIT, misread.
- `MayankGangwal-code/ev-battery-soc-estimation` appends a **dataset attribution** — *"derived from 'LG
  18650HG2 Li-ion Battery Data' … Mendeley Data, doi:10.17632/cp3473x7xv.3, **licensed CC BY 4.0**"* →
  MIT, misread.

**So `NOASSERTION` tracks conscientious authors, not risky ones** — the careless repos in this KB carry
**no licence file at all** and measure `NONE`. And note what the second one disclosed: **the dataset
licence**, CC BY 4.0, which *is* commercially usable — the opposite of MVTec AD. **`NOASSERTION` is
frequently a pointer to a dataset grant**, the one axis `LICENSE` cannot express.

### ✅ Independent re-verification of the whole shelf, with a stricter oracle

Re-probed **all 193 repo slugs** in the eight files. **190 live, 3 dead — the same three already
recorded, none a recommendation.** 0 new rot in the 55 minutes since 12:45Z, as expected.

🔴 **Method correction that matters to this fleet's standing instructions:** the task spec says *verify
every URL with `curl -sI`*. Executed literally against `github.com` from this environment **that
instruction returns no information at all** — the proxy answers **403 for a live repo
(`torvalds/linux`) and 403 for a repo that does not exist**, identically. It is not a liveness test
here. `git ls-remote --symref` **is** one, and it returns the **default branch** in the same call —
which `raw.githubusercontent.com` licence reads need, and guessing it `main`/`master` is a silent
false-negative generator. `anomalib` is `main`; `sagemaker-defect-detection` is **`mainline`**;
`hcengineering/platform` is **`develop`**. See `compose/patterns.md` P19, channel 1, updated this pass.

---

## 2026-11-21 — second pass (verification, 12:45Z)

**Window:** 2026-11-21 09:55Z → 12:45Z (≈3 hours, same day). **This is a same-day re-measurement, so
read it for drift direction, not for growth rates.** The 09:55Z section below is preserved unchanged.
**Channel:** batched `gh api -X GET search/repositories` (8 slugs/query, 188 URLs),
`raw.githubusercontent.com` byte-reads, `git ls-remote` for exact-case liveness.

### 🆕 New this window — two permissive repos, and the MIT one matters more than its star count

| Repo | Licence (byte-read) | ★ | Note |
|---|---|--:|---|
| [LogosIntelligenceLab/SGDrive](https://github.com/LogosIntelligenceLab/SGDrive) | **MIT** — 1,077 bytes, *"Copyright (c) 2025 Logos Robotics Group"* | 81 | **The only MIT-licensed driving model in this KB.** Every other model row is Apache-2.0 at best. For work that must be sublicensed into a proprietary stack, **the licence outranks the star count.** Pushed 2026-10-23. |
| [TUM-AVS/FM-AD-Survey](https://github.com/TUM-AVS/FM-AD-Survey) | **Apache-2.0** — 11,337 bytes, canonical | 249 | TU Munich AVS chair; foundation-models-for-AD survey. **Pushed 2026-11-19** — a live index, attributable to a named academic group. |

### 🔴 Rejected on licence this window

| Repo | Measured | ★ | Verdict |
|---|---|--:|---|
| [XiaomiAutoL3/DriveZero](https://github.com/XiaomiAutoL3/DriveZero) | **`NONE`** — no licence file | **147** | **Rejected.** *"End-to-end driving beyond human demonstrations."* **The lesson is about vendors, not this repo: this KB already holds Xiaomi's `recogdrive` as Apache-2.0 (631★). The same vendor is inconsistent across its own repositories, so vendor reputation is not a licence signal.** Worth re-probing — an unlicensed 147★ model is a plausible candidate for a grant being added later. |

### 📈 Drift this window — attention is concentrating on one cluster

Largest absolute moves among rows with ≥200 claimed stars, **all four in the VLA / world-model layer**:

| Repo | Written | Measured | Δ |
|---|--:|--:|--:|
| [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | 205 | **245** | **+40** |
| [NVlabs/alpamayo2](https://github.com/NVlabs/alpamayo2) | 287 | **314** | **+27** |
| [QwenLM/Qwen-Drive-1.0](https://github.com/QwenLM/Qwen-Drive-1.0) | 537 | **563** | **+26** |
| [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | 520 | **542** | **+22** |

Everything with a large base moved in single digits — `commaai/openpilot` measures **64,192**,
`AtsushiSakai/PythonRobotics` 30,951 → **30,953**, `esmini/esmini` 949 → **954**. **The open stacks are
stable; the open VLA/world-model frontier is where attention is moving, and the NVIDIA Alpamayo line is
its centre.** Fast movers on a small base: `autowarefoundation/autoware_latent_drive` **42 → 95**,
`superdeman/cockpit-agent` **1 → 30**, `masoudjtehrani/pcla` 77 → **103**.

⚠️ **Method caveat, carried from the education KB's finding that an inference and a measurement are not
the same evidence:** these deltas are **drift since each row was written** (snapshot dates range from
2026-10-31 to 2026-11-21), **not** a 3-hour rate. Direction is sound; **do not quote a per-day figure.**

### ✅ The licence layer held — 20 flags, 0 real errors

188 URLs re-probed → **185 live, 3 dead (the same 3 already recorded, none a recommendation — zero new
rot)**. 20 rows where the written licence disagreed with measured SPDX, **all 20 resolved in the base's
favour**: 13 were `NOASSERTION`-as-pointer (byte-read confirmed `nuscenes-devkit` Apache-2.0, `odoo`
LGPL-3.0, `auto-agent-protocol` Apache-2.0 code + CC BY 4.0 docs), and **7 were the differ catching the
base's own warning prose** — "README says MIT; there is **NO** LICENSE file", "**Not** Apache-2.0".
**A base that states its exceptions precisely will trip a naive grep-based checker.** Detail in
`agents/top.md` §V1.

### 🔴 Method correction this window — the filename list is not the instrument

`autowarefoundation/autoware-safety-island` returned **404 on 18/18** probe combinations
(`LICENSE`/`LICENSE.md`/`LICENSE.txt`/`LICENCE`/`COPYING`/`NOTICE` × `main`/`master`/`develop`) and would
have been written up as *"Apache-2.0 claimed, no licence file"* — **a false correction against a correct
base.** It carries a full **10,894-byte Apache-2.0 text in `license.rst`**, plus
`SPDX-License-Identifier: Apache-2.0` in its README header under an **Arm Limited** copyright.
**The row already cited `license.rst`. Read a row's stated evidence before re-probing it**, and add
`license.rst`/`LICENSE.rst` to the probe list.

### Declared gaps this window

1. **`SpaceDrive`** — named by an aggregator as a CVPR 2026 driving project; **resolves to no repository.**
2. **`carlover`** — MIT automotive assistant cited by an ecosystems aggregator; **slug does not exist**
   (only 0–3★ unlicensed namesakes). **Two aggregator-sourced candidates evaporated in one pass — resolve
   the slug before writing the row.**
3. **Model weights licences: still unverifiable.** `huggingface.co` DNS-dead, re-probed, 6th consecutive
   pass. Also dead this pass: `eur-lex.europa.eu`, `unece.org`, `www.federalregister.gov`.
4. **No LATAM-origin automotive agent** surfaced again. **6th consecutive pass.** The gap is in *supply*.
5. **No permissive dealership DMS/ERP — 7th consecutive negative.** `Dolibarr` GPL-3.0, `YetiForceCRM`
   `NOASSERTION` + stale since 2024, `SuiteCRM` unresolved; `open-mercato` (MIT) is a framework only.

---


## 2026-11-21

**Window:** 2026-11-19 → 2026-11-21 (2 days). **Channel — changed this pass, and it matters:**
`git ls-remote` for liveness, `raw.githubusercontent.com` for **byte-read LICENSE files** (HTTP 200),
`gh api -X GET search/repositories` for stars/forks/`pushed_at`/`archived`. `github.com`,
`api.github.com` and **`gh api repos/<o>/<r>`** (per-repo REST, scoped to this session's own repos) are
all **403**. `huggingface.co` still does not resolve.
**174 KB URLs probed → 170 live, 3 dead, 1 false positive. 152 LICENSE files byte-read.**

### 🚨 The finding of this window is about method, not about a repo

Every pass in this file since 2026-10-26 has carried the line *"`curl` to `github.com` is 403, so figures
come from rendered pages."* That was true and it was also **incomplete**. Two channels were never tried:

```
git ls-remote --heads https://github.com/<owner>/<repo>     # 40-hex SHA = live; credential prompt = gone
curl https://raw.githubusercontent.com/<o>/<r>/main/LICENSE  # HTTP 200 — the grant, byte for byte
```

**Both work.** The licence-verification problem this base has described as blocked for four passes was
never blocked — only the *one* channel everyone kept re-testing was. Recorded as a standing method, not
a one-off: **when a host returns 403, enumerate the host's siblings before declaring the capability
unavailable.** `github.com` is 403; `raw.githubusercontent.com` is 200. Same organisation, different host.

### The 0★ mortality rule, now with evidence

Three of the 174 URLs are dead. **All three were 0★ rows added by an automated discovery pass**, and all
three had already been labelled unusable by a later pass:

| Dead | Was already labelled |
|---|---|
| [RobertSloan22/tars-car-mcp](https://github.com/RobertSloan22/tars-car-mcp) | *"Rejected"* — no licence, gated on a proprietary desktop app |
| [luca1234413/MotionBastard](https://github.com/luca1234413/MotionBastard) | *"not automotive software"* (After Effects motion design) |
| [vaisakhvenugopal/Deconstructing-BYD-s-Technology-Architecture](https://github.com/vaisakhvenugopal/Deconstructing-BYD-s-Technology-Architecture) | licence `?` |

**Every repo in this base with ≥1★ is live.** 0★ is not just weak signal — it is the mortality band. The
rows above sit in historical sections and are **left in place** (this file is append-only and a recorded
rejection that later 404s is evidence, not debris). `github.com/orgs/autowarefoundation` also flagged as
dead and is a **false positive** — an org listing URL in prose, not a repo. Do not re-flag it.

### 🆕 Admitted this window — four agents, all MIT, all byte-read

| Agent | Repo | Licence | ★ | Last push | Why admitted |
|---|---|---|--:|---|---|
| Dealer AI Skills | [arielcoro/dealer-ai-skills](https://github.com/arielcoro/dealer-ai-skills) | **MIT** | 3 | 2026-10-21 | **First dealer-retail agent in this base with a real grant.** SEO/AEO/GEO, BDC, F&I, fixed ops, equity mining. Runs on Claude Code, Codex, Cursor, Gemini CLI. North-America dealer vocabulary throughout. |
| Waypoint | [rogue-media-lab/waypoint](https://github.com/rogue-media-lab/waypoint) | **MIT** | 1 | 2026-11-13 | Service-advisor assistant, SQLite-backed, **VIN decode + labour-time lookup**. Narrow and real. |
| OmniIntent | [neura-edit/omni-intent](https://github.com/neura-edit/omni-intent) | **MIT** | 1 | 2026-10-03 | **Cockpit intent as routing, not generation** — deterministic slot extraction, Kotlin, on-device, *"zero auto-regressive generation delay"*. The only shape that fits an automotive latency budget. |
| deeptest-talking-manual | [keklikci/deeptest-talking-manual-26](https://github.com/keklikci/deeptest-talking-manual-26) | **MIT** | 0 | 2026-08-20 | Generates tests that hunt **omitted safety warnings** in LLM owner's-manual assistants. Pairs with the assurance layer. |

### 🔴 Rejected this window

| Repo | Licence | Why refused |
|---|---|---|
| [mikko-lab/kopilotti-sales-demo](https://github.com/mikko-lab/kopilotti-sales-demo) | 🔴 **"All Rights Reserved"** | Used-car negotiation with rule-based safety bounds — a good design. LICENSE: *"No part … may be copied, distributed, modified, or used commercially without prior written permission."* **Zero grant.** It appears on the `automotive-ai` topic page and looks exactly like a finding; it is not one. |

### 🔄 Licence cells the API cannot answer, settled by byte-read

| Repo | ★ | API | **Byte-read** |
|---|--:|---|---|
| [autoas/as](https://github.com/autoas/as) | 965 | `NOASSERTION` | **GPL-3.0 OR Commercial (dual)** — a commercial escape hatch on an AUTOSAR-class stack |
| [openremote/fleet-management](https://github.com/openremote/fleet-management) | 51 | `NOASSERTION` | **AGPL-3.0** |
| [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics) | 30,954 | `NOASSERTION` | **MIT** |
| [COVESA/vss-tools](https://github.com/COVESA/vss-tools) | 81 | `MPL-2.0` | **MPL-2.0** (cell was *"not read"*) |

### ⚠️ The trap that would have corrupted this pass if the shelf had been overwritten

An automated classifier over the same 152 files disagreed with this base's published cells on **8**
repos — and **the published cells were right all 8 times.** Cause: *every* GNU-family, MPL and EPL
licence text names other licences in its own body (MPL §1.12 defines "Secondary License" as GPL/LGPL/
**AGPL**; GPL-3.0 §13 references **AGPL**; LGPL-3.0 appends the whole GPL; EPL-2.0 names **GPL-2.0**).
Substring matching therefore misreads MPL-2.0 → AGPL, LGPL-3.0 → AGPL, GPL-3.0 → AGPL, EPL-2.0 → GPL-2.0.
**Key on the title line, never on names in the body.** This is the second base in this KB family to hit
the same class of error (`education` recorded it on 2026-11-21 as "the API's SPDX field is not the
published grant"). **The shelf is the asset; a fresh automated read is not automatically an improvement.**

### 🔄 Correction carried into `agents/top.md` §5

`hcengineering/platform` (Huly, 28,161★, EPL-2.0) is recorded here as *"frozen and no longer actively
maintained"*. The notice actually says the **hosted service** is being discontinued for lack of hosting
funding, and points users to **self-hosting**. Repo today: `pushed_at` 2026-11-09, `archived` **false**,
last commits real fixes (`fix(github)`, `fix(gantt)`, `fix(contact)`). **Hosted-SaaS shutdown ≠ dead
project**, and the correction runs in our favour: self-hosted EPL-2.0 is viable for an engagement.


## 2026-11-19

**Window:** 2026-11-13 → 2026-11-19 (6 days). **Channel used:** `gh api -X GET search/repositories`
(the GitHub REST API — `license.spdx_id`, stars, forks, `pushed_at`, `created_at` are first-hand API
fields) plus rendered repository pages for README substance and `raw.githubusercontent.com` for LICENSE
files. `curl` to `github.com` and `api.github.com` is **HTTP 403** (host policy, re-tested today);
`huggingface.co` does not resolve. **39 of 39 repos re-queried by exact `repo:owner/name` resolved.**

### 🚨 The standing conclusion that broke this window

Three previous snapshots in this file recorded the automotive agent category as "0–8★", then "0–26★".
**It is 2,907★.** The error was not in the counting — it was in *where* this file looked. Every prior
pass searched for agents that sit *in the vehicle*. The largest automotive agent artifact on GitHub sits
in the **engineering office**:

**[jherrodthomas/automotive-skills-suite](https://github.com/jherrodthomas/automotive-skills-suite)** —
**MIT, 2,907★, 141 forks**, created 2026-05-01, pushed 2026-10-16, 9 open issues. 76 builder+reviewer
skill pairs across **ISO 26262, ISO/SAE 21434, ISO 21448 SOTIF, AIAG-VDA/IATF 16949, Automotive SPICE**,
plus CAN/LIN/FlexRay/Ethernet, UDS/ODX/DEM, AUTOSAR Classic + Adaptive, A2L/DCM calibration, MBSE/SysML
and V&V traceability. Builders emit `.xlsx`; reviewers check and dashboard without mutating source
artefacts. Installed via "Save skill" in Cowork or Claude Desktop — **the page names no Claude Code or
non-Claude runtime**.

**Correction to this file's own method, recorded as a method change for the next pass:** the 2026-10-31
entry concluded *"in automotive, search the protocol, not the buzzword"* and that produced the
diagnostics-MCP category. It is right but incomplete. The rule that would have found a 2,907★ repo six
months earlier is: **search the standard, not only the protocol** — `ISO 26262`, `ISO 21434`,
`ISO 21448`, `AUTOSAR`, `Automotive SPICE` as query terms. That query
(`AUTOSAR OR ISO26262 OR "ISO 21434" in:name,description,readme pushed:>2026-08-01 stars:>15`) is what
surfaced it, along with `iDoka/awesome-canbus` (CC0, 3,571★), `ebroecker/canmatrix` (BSD-2, 1,093★),
`eclipse-iceoryx/iceoryx` (Apache-2.0, 2,212★) and `autoas/as` (965★, `NOASSERTION`).

### 🆕 Assurance-as-code became a category in six weeks — three projects, one created today

| Repo | Licence | ★/forks | Created | Note |
|---|---|--:|---|---|
| [jherrodthomas/automotive-skills-suite](https://github.com/jherrodthomas/automotive-skills-suite) | MIT | 2,907★ / 141f | 2026-05-01 | 76 builder+reviewer pairs → `.xlsx` |
| [jherrodthomas/LionDriver](https://github.com/jherrodthomas/LionDriver) | MIT | 65★ / 3f | 2026-10-09 | openpilot derivative + **living safety case** |
| [Lieubk/automotive-safety-security-assurance-kit](https://github.com/Lieubk/automotive-safety-security-assurance-kit) | MIT | 2★ / 0f | **2026-11-19** | ASPICE 3.1/4.0 + 26262 + 21434 trace engine |

**LionDriver is the find of the window, not the skills suite.** Read from its page: a living safety case
of **36 claims and 50 evidence items with 0 accepted and 42 open defeaters**; **89 V-cycle work products
(85 draft, 4 skeleton)**; citations to ISO 26262, ISO 21448, ISO/SAE 21434, **ISO/PAS 8800** and
**UL 4600** plus Automotive SPICE — followed by an **explicit statement that it claims no compliance
because no assessment has been performed**. No release build. Development builds not for public roads
outside a controlled test regime. First *evaluated* configuration **Toyota Corolla (E210)**; **no
configuration is yet assurance-supported**. Field monitoring live with a first case tied to
**NHTSA PE26007**. Automated checks of inherited openpilot safety code run in CI but are **not yet
reviewed as evidence**.

Publishing your own 42 unresolved defeaters is the single most credible engineering signal recorded in
this file to date. By contrast the 2,907★ skills suite carries **no "not certified" disclaimer** while
advertising coverage of six standards — ⚠️ recorded here as a risk, not a defect of the code.

### 🆕 Agents drove real cars this window — a standing gap closes

**[aditya-ramabadran/drivingbench_harness_code](https://github.com/aditya-ramabadran/drivingbench_harness_code)**
— **MIT, 63★, 8f**, created 2026-09-18, pushed 2026-11-11. MCP server `drivingbench_sandbox` exposing
`observe()` / `set_motion()` / `stop_now()`; chat models (Codex, Claude Code, Cursor), API models
(OpenRouter, Gemini) and **trained VLA policies served over HTTP** all drive the same course. Real
platforms: **comma four** on pinned openpilot `59fcd340`, **Toyota TSS2**, **Tesla Model 3 HW3**.
Envelope: default **3 m/s** ceiling, **hard 6 m/s cutoff**, command expiry, cancel on any driver input.
Simulator is the v1.1 course as a **Gaussian splat** with the real control stack. Full trace replay
including every image the model saw.

Two design details to copy: the **`reason` argument is logged for the operator and never reaches the
controller** (prompt text cannot become actuation), and `observe()` returns **image age** (staleness is
an input, not an assumption).

⚠️ **No scores and no leaderboard are published.** Releases is empty. This is a harness finding, not a
ranking finding — **do not quote a DrivingBench result**.

### 🆕 openpilot unbundled from comma's hardware this window

- **[zoompilot/jetlink](https://github.com/zoompilot/jetlink)** — MIT, 57★ and **40 forks**, pushed
  2026-11-08: runs **openpilot's large driving model on Jetson Orin Nano, macOS, iOS, Android and CUDA
  laptops** with only a comma device and a USB3 cable. A 0.70 fork-to-star ratio is a *build* signal.
- **[zoompilot/zoompilot](https://github.com/zoompilot/zoompilot)** — MIT, 37★/31f, pushed
  **2026-11-19**: driver assistance for **Mazda** and others.
- **[YassineYousfi/openpilot.distill](https://github.com/YassineYousfi/openpilot.distill)** — MIT, 38★:
  distil openpilot on your own drives.
- **[Sherin-SEF-AI/Lyne-ADAS](https://github.com/Sherin-SEF-AI/Lyne-ADAS)** — MIT, 22★, pushed
  2026-11-18: **100% on-device ADAS for Android** (FCW, drivable-area segmentation, pedestrian, lane,
  traffic-sign), self-tuning from budget phones to flagships.

Together: a permissive driving model is becoming portable to hardware a client already owns.

### 🆕 Vehicle-data MCP: a 142★ leader appears, and the read-only convention holds

[cobanov/teslamate-mcp](https://github.com/cobanov/teslamate-mcp) — **MIT, 142★, 25f, 0 open issues** —
is now **the largest automotive MCP server in this KB**, 5× the previous high. Also new this window:
[cyanheads/nhtsa-vehicle-safety-mcp-server](https://github.com/cyanheads/nhtsa-vehicle-safety-mcp-server)
(Apache-2.0 — VIN decode, recalls, complaints, crash ratings),
[AbbottDevelopments/shopmonkey-mcp-server](https://github.com/AbbottDevelopments/shopmonkey-mcp-server)
(MIT, **69 tools** over a real shop-management API),
[october-dev/car-use](https://github.com/october-dev/car-use) (MIT, created 2026-11-11, **36 open
issues** — very young),
[christianOrona/wtfault-scanner](https://github.com/christianOrona/wtfault-scanner) (Apache-2.0 —
*"never makes anything up"*, every number clickable to raw bytes),
[Sherin-SEF-AI/CanLab](https://github.com/Sherin-SEF-AI/CanLab) (MIT, 94★ — **injection is bench-only
and stays disarmed until armed**), and
[bpawnzZ/lemonwrench](https://github.com/bpawnzZ/lemonwrench) (MIT — OEM service manuals → procedure
and torque tables, **69 makes, 1960–2025**).

The category's **design convention is now settled in code, not just in READMEs**: read-only by default,
actuation disarmed, provenance traceable to raw bytes. That is **T8** (human gate) confirmed from the
supply side.

### 🆕 Non-driving automotive agents spread into cockpit, requirements and procurement

- [yancent-dao/cockpit-agent-sim](https://github.com/yancent-dao/cockpit-agent-sim) — MIT, 98★, CN:
  smart-cockpit agent framework with **tiered permissions, confirmation flow, card orchestration and a
  fast/slow dual layer**. The most reusable in-vehicle HMI agent architecture found so far.
- [BUAksakal/reqlens](https://github.com/BUAksakal/reqlens) — MIT: **LangGraph supervisor + LlamaIndex
  RAG** reading requirements out of PDF specs and flagging conflicts and vague wording, engineer in the
  loop. (Türkiye-origin.)
- [yorkeccak/takt](https://github.com/yorkeccak/takt) — MIT, 19★: automotive **procurement and R&D**
  deep research → PDF/PPTX/DOCX/CSV from patents, SEC filings and papers.
- [aws-samples/sample-manufacturing-automotive-ai-toolkit](https://github.com/aws-samples/sample-manufacturing-automotive-ai-toolkit)
  — **MIT-0**, 19★/7f: **the first hyperscaler-published automotive agent sample set** in this KB.
  MIT-0 means **no attribution requirement** — the most permissive licence recorded here.
- [LeventKent/automotive-sdlc-agent-for-mil-sil-hil](https://github.com/LeventKent/automotive-sdlc-agent-for-mil-sil-hil)
  — MIT, 2★: V-model MIL/SIL/HIL agent.

### 🔴 Rejected on licence this window

| Repo | ★ | Licence | Verdict |
|---|--:|---|---|
| [ThinkOffApp/CarWatch](https://github.com/ThinkOffApp/CarWatch) | **306★** | **AGPL-3.0** | Highest-starred automotive agent after the skills suite. Network copyleft — **reference architecture only**, never in a client deliverable. |
| [FrankRun/WCog-VLA](https://github.com/FrankRun/WCog-VLA) | 76★ | **none** | Do not use. |
| [xiongqi123123/MarginAD](https://github.com/xiongqi123123/MarginAD) | 41★ | **none** | Do not use. |
| [liushengjia-AAL/shengjia](https://github.com/liushengjia-AAL/shengjia) | 21★ | **none** | 47 ECU/TCU calibration skills (A2L/DAMOS/WinOLS, Stage1 tuning, checksum, Ghidra, EDC17/MD1/MG1/DCM). No licence **and** the content is ECU remapping — **out of scope for a client deliverable on both counts**. Recorded so it is not re-found. |
| [TOSUN-Shanghai/TSMaster](https://github.com/TOSUN-Shanghai/TSMaster) | 442★ | **LGPL-2.1** + feature gating | Page states *"free for research and education purpose for some features"*. Tool, not a component. |
| [mahmutcanborann/mcp-ev-digital-twin-agent](https://github.com/mahmutcanborann/mcp-ev-digital-twin-agent) | 6★ | **none** | EV battery SOH estimation as MCP tools — interesting shape, unusable licence. |

### 🟢 Licence false negatives and a name collision

- **`autowarefoundation/AWSIM` (765★/163f) is NOT Apache-2.0.** The LICENSE file read raw opens
  *"AWSIM Licenses — AWSIM License Applies to autowarefoundation/AWSIM repositories and all content
  contained in the Releases"*. A **bespoke licence**. `autoware` and `autoware_universe` remain
  Apache-2.0.
- **`H-EmbodVis/SimWAM`** — API says `NOASSERTION`; LICENSE at `main` is **"MIT License / Copyright (c)
  2026 The SimWAM Authors"**. 🟢 Rescued, same false-negative pattern as 2026-11-13.
- **`auto-agent-protocol/auto-agent-protocol`** — API says `NOASSERTION`; LICENSE at `main` is the
  **Apache-2.0 text verbatim**. Now **112★, pushed 2026-11-19** (110★ on 2026-10-31 — slow but alive).
- ⚠️ **Name collision:** `visionpilot-project/VisionPilot` (**MIT, 43★**, BeamNG.tech simulation
  platform with Foxglove) is **not** `autowarefoundation/vision_pilot` (**Apache-2.0, 928★/197f**, the
  L2 ADAS stack). Different owner, licence and purpose. **Paste full `owner/name` in any SoW.**

### Regions represented this snapshot

- **North America:** DrivingBench (MIT), LionDriver (MIT), zoompilot + jetlink (MIT), car-use (MIT),
  lemonwrench (MIT), aws-samples toolkit (MIT-0), omni-dreams (NVIDIA, Apache-2.0), nhtsa-mcp
  (Apache-2.0), shopmonkey-mcp (MIT), safedrive-vla (UC Irvine, Apache-2.0).
- **APAC:** `xiaomi-research/recogdrive` (**Apache-2.0, 631★, ICLR 2026**), `cockpit-agent-sim` (MIT,
  CN), HERMES / HERMES++ , WorldDrive, DriveWAM, AgentThink, `Thinklab-SJTU/Awesome-LLM4AD`
  (1,906★). **APAC still supplies the model tier.**
- **EMEA:** `de4sdv/DE4SDV` (Apache-2.0, SysML v2 for SDV), `eclipse-leda/*` (Apache-2.0),
  `eclipse-iceoryx/iceoryx` (Apache-2.0, 2,212★), `thi-ad/UrbanIng-V2X` (**MIT, 88★, NeurIPS 2025** —
  Technische Hochschule Ingolstadt), `reqlens` (Türkiye), `canmatrix` (BSD-2).
- **LATAM:** 🔴 **nothing.** No LATAM-origin automotive AI repository surfaced in any of the eleven
  queries run this window. Fifth consecutive snapshot with this result. The gap is in *supply*, not in
  demand — see `intel/market.md` → Opportunities by region → LATAM.

### Declared gaps this window

1. **EV charging / battery AI:** `EV battery charging AI in:name,description pushed:>2026-08-01
   stars:>15` → **0 repos**. Nothing maintained above 15★ in the last quarter.
2. **Plant-floor quality/inspection AI:** `automotive manufacturing quality inspection AI
   in:name,description pushed:>2026-06-01 stars:>3` → **0 repos**. Entirely proprietary.
3. **Fleet telematics:** still only 2 repos above 5★ in the last quarter. Fifth pass.
4. **DMS:** 408 repos for `car dealership management pushed:>2026-01-01`, **top star count 5**, almost
   all unlicensed. Gap holds.
5. **No DrivingBench leaderboard published**, so no model ranking can be stated.
6. **No model weight licence verified** (`huggingface.co` unreachable).
7. **`drivingbench.com` was not fetched** this pass — only the repository page. Any score claim must
   wait for that source.

### 🟢 Data-integrity check on this file's own history

The 2026-11-13, 2026-10-31, 2026-10-26 and 2026-10-15 sections and the pre-2026-10-15 history below
were **read before writing and left byte-for-byte unchanged**. This section was inserted above them.
The one change to an earlier *conclusion* — the "0–26★ agent category" claim — is **corrected here in
place, in this section**, and the earlier text that stated it has **not** been edited, so the record of
what this KB believed and when remains readable.

**Header-as-data check (run this pass, both trending files).** Every markdown table in all eight files
was parsed programmatically: **0 of them have a first row lacking a `|---|` separator**, so there is no
header row sitting in the data. The two Spanish-language headers in the pre-2026-10-15 history
(`| Nombre | Licencia | Descripción | Stars |`) *are* well-formed headers — each is followed by a
separator row — and they were therefore **left byte-for-byte unchanged** rather than rewritten. If a
compiler has ever produced an entity named `nombre` from this KB, the defect is in the compiler's table
parsing, not in these files; the fix belongs upstream and the history should not be edited to work
around it.

## 2026-11-13

**Window:** automotive AI agents and driving models, 10–13 Nov 2026. Verified today by fetching each
repository page and reading GitHub's own licence field and star count; licences that mattered were settled
by fetching the file raw from `raw.githubusercontent.com`. **`curl -sI` on `github.com` and
`api.github.com` both return HTTP 403** under this session's egress policy, re-tested today on three URLs.
**19 candidates probed, 13 admitted, 3 rejected on licence, 3 recorded as corrections.**

### The headline: an Apache-2.0 production L2 ADAS stack exists, with 927 stars and 4,282 commits

[autowarefoundation/vision_pilot](https://github.com/autowarefoundation/vision_pilot) — **Apache-2.0,
927★, 196 forks, 4,282 commits**, updated **12 Nov 2026**. *"Free and fully open-source L2 ADAS stack
powered by End-to-End AI technology"*, and in the README *"a productionizable and safety certifiable
implementation."* **ACC, FCW, AEB, LKAS, LDW, ISA and single-lane hands-free highway Autopilot**, running
**mapless** on **a single front monocular camera (52–55° HFOV, 1–2 MP)** via **ONNX Runtime on GPU or
CPU**, with Docker images, an optional ROS 2 interface and CARLA 0.9.16 closed-loop simulation. Three
models inside a *"Hybrid End-to-End AI Architecture"*: **AutoSpeed**, **AutoSteer**, **AutoDrive**.

**Why this is the most consequential single row this KB has added in four passes.** For four passes the
standing finding was *"the only large permissively-licensed automotive codebase is openpilot (MIT)."*
There are now two, and the second is **Apache-2.0, under vendor-neutral foundation governance, with
ISO 26262 and ISO 8800 on its roadmap** — i.e. aimed at the exact objection ("we cannot certify a
community project") that kills openpilot in OEM conversations. ⚠️ **Certification is a roadmap item, not
a status**, and "safety certifiable" is the project's own aspirational wording. Do not repeat it to a
client as achieved.

### The Autoware Foundation shipped eight repositories in three days

Not a model release — a stack. All verified individually today:

| Repo | Licence | ★ | Commits | What it is |
|---|---|--:|--:|---|
| [vision_pilot](https://github.com/autowarefoundation/vision_pilot) | Apache-2.0 | 927 | 4,282 | L2 ADAS stack (above) |
| [agnocast](https://github.com/autowarefoundation/agnocast) | Apache-2.0 | 212 | 1,258 | rclcpp-compatible **true zero-copy IPC** for ROS 2, all message types, kernel module + heaphook |
| [alpamayo-autoware](https://github.com/autowarefoundation/alpamayo-autoware) | Apache-2.0 | 161 | 42 | Foundation's **own fork of NVlabs/alpamayo**, branch `alpamayo2.0-edge` |
| [autoware_latent_drive](https://github.com/autowarefoundation/autoware_latent_drive) | 🔴 **NONE** | 42 | 64 | V-JEPA ViT-L camera-only latent planner — **rejected, see below** |
| [autoware-safety-island](https://github.com/autowarefoundation/autoware-safety-island) | Apache-2.0 (`license.rst`) | 8 | 608 | Safety island on ARM SoCs — **rescued from a bad label, see below** |
| [scene_3d](https://github.com/autowarefoundation/scene_3d) | Apache-2.0 | 2 | 3 | Monocular depth; part of the **AutoSeg Foundation Model**; Scene3DLite distilled from DepthAnythingV2 |
| [autoware.trucks](https://github.com/autowarefoundation/autoware.trucks) | Apache-2.0 | 2 | 9 | Highway **trucking** autonomy, L2+ → L4 |
| [ego_lanes](https://github.com/autowarefoundation/ego_lanes) | Apache-2.0 | 1 | 30 | Lane-boundary segmentation, mapless; maintainers call it *"legacy"* |

The press channel for this release was **unreachable** — `www.manilatimes.net` does not resolve from this
session — so the repositories were used as the primary source instead. That is the better source, but the
announcement's own framing and any licence statement in it are **unread**. Declared, not papered over.

### 🔴 Rejected on licence: a major foundation shipped a model with no grant

[autowarefoundation/autoware_latent_drive](https://github.com/autowarefoundation/autoware_latent_drive) —
**42★, 64 commits, 6 forks, no licence.** Probed today: **no sidebar licence field**, **no licence
statement anywhere in the README**, and `LICENSE`, `LICENSE.md`, `LICENSE.txt` and `license.rst` **all
return 404 on `main`** when fetched raw.

Technically it is the most novel thing in the batch: **LatentDrive** plans *"in latent space"* with a
**V-JEPA ViT-L** video encoder and **no object detection or tracking in between** — last 2 s of front
camera + six route points + ego motion → **4 s ego trajectory at 10 Hz** — shipped as a **TensorRT C++
library with no ROS dependency** plus a ROS 2 node. README: *"This is a research model: it is not a
certified driving system and must not control a vehicle on public roads."* **No benchmarks at all**; the
plan *"is drawn, not executed."*

**This is the third occurrence of this exact defect in the automotive KB** (after `j2534-mcp-server`, and
`petrpatek/obd2-mcp-server` below) and the **first inside a major foundation's own organisation**. Its
sibling `autoware-safety-island` has a licence file, so the org plainly knows how. Recorded as a pattern,
not an anecdote: **being published by the Autoware Foundation is not a licence.**

### 🟢 Rescued: GitHub's licence label produces false negatives too

[autoware-safety-island](https://github.com/autowarefoundation/autoware-safety-island) — **8★ but 608
commits**, the most substantial safety-relevant repo in the batch — shows as **"Other"** in the org
listing. Reason: its licence lives in **`license.rst`**, not `LICENSE`, so GitHub's detector will not name
it. Fetched raw today, it opens *"Apache License / :Version: 2.0 / :Date: January 2004"* — **verbatim
Apache-2.0.** Shelved as Apache-2.0.

Every prior pass of this pipeline has warned about licence **false positives** (README says MIT, no file).
This is the inverse and it is just as expensive: a KB that trusts the label **silently loses** a usable
Apache-2.0 safety repository. **"Other" is an instruction to fetch the file, not a verdict.**

### 🔴 Addressing defect: `mcp-can` is now `Peykan`

[farzadnadiri/Peykan](https://github.com/farzadnadiri/Peykan) — **MIT, 26★, 29 commits.** *"Talk to Your
Car Using AI."* Every search result still points at **`farzadnadiri/mcp-can`**, which now resolves to this
repository. Same defect class as the `openedx/edx-platform` → `openedx/openedx-platform` rename this
pipeline recorded in the education KB on 2026-11-13 — **a renamed repo silently keeps serving under the
old address until it doesn't.** Record the new name.

Substantively it is now **the highest-starred real diagnostic agent this KB has found in four passes**
(Auto Agent Protocol's 110★ is a *specification*, not an agent). It covers **CAN bus, OBD-II, UDS and SAE
J1939** — and **J1939 is the commercial-vehicle bus**, which nothing else in this category touches. That
pairs directly with `autoware.trucks` above: the freight line now has both a stack charter and a
diagnostics agent.

### The diagnostics-agent category: 0–8★ last pass, 0–26★ now, eight projects deep

| Agent | Licence | ★ | Verdict |
|---|---|--:|---|
| [farzadnadiri/Peykan](https://github.com/farzadnadiri/Peykan) | MIT | 26 | 🆕 **Admitted.** CAN/OBD-II/UDS/**J1939**, simulator, Docker, live dashboard |
| [petrpatek/obd2-mcp-server](https://github.com/petrpatek/obd2-mcp-server) | 🔴 **README says MIT, no file, no field** | 12 | **Rejected.** Ships a **1,937-code Ford-specific DTC database** — the genuinely useful asset, and unusable. 5 commits |
| [castlebbs/Vehicle-Diagnostic-Assistant](https://github.com/castlebbs/Vehicle-Diagnostic-Assistant) | MIT | 8 | Carried. Still the most complete reference design (LangGraph + MCP over JSON-RPC 2.0 + NHTSA vPIC) |
| [shoka-jp/obd2-mcp](https://github.com/shoka-jp/obd2-mcp) | MIT | 2 | Carried. **Mock vehicle bundled** — runs with no hardware |
| [ayhammouda/obd-mcp-server](https://github.com/ayhammouda/obd-mcp-server) | **Apache-2.0 + MIT (dual)** | 1 | 🆕 **Admitted.** *"Safety-first, read-only … simulator-first"*, **7 typed MCP tools**, extensible UDS profiles. Most permissive grant in the category; 19 commits |
| [vehicle-platform/vehicle-mcp](https://github.com/vehicle-platform/vehicle-mcp) | MIT | 0 | 🆕 **Admitted, correcting a secondary source** — see below |
| [RobertSloan22/tars-car-mcp](https://github.com/RobertSloan22/tars-car-mcp) | 🔴 **No licence** | 0 | **Rejected.** OBD-II/UDS/**GM bidirectional**/CAN — deep capability, but gated on the proprietary TARS desktop app. **1 commit** |
| [cyrusdavirusss/j2534-mcp-server](https://github.com/cyrusdavirusss/j2534-mcp-server) | 🔴 **README says MIT, no file** | 0 | Carried as rejected. J2534 professional interface — the deepest and still unusable |

**The category's shape has settled even though no winner has emerged.** MCP is unanimous as the transport
across all eight. The physical layer is ELM327/OBD-II, J2534 and now J1939. And the design convention has
converged independently on **read-only plus simulator-first** — `obd-mcp-server` makes a deterministic
simulator the *default backend*, `obd2-mcp` bundles a mock vehicle, `Peykan` ships a simulator. For
Globant that is a favourable market shape: **the integration contracts are settled and the differentiated
product does not exist.**

### Corrections to secondary sources this pass

1. **"vehicle-mcp is a skeleton with no code yet"** — a search summary's claim. The repository page says
   **v0.2.0**, `src/vehicle_mcp`, a `tests` directory, **CI workflows**, a table of read-only tools, and
   **51 commits**. It is *small* (0★), not *empty*. Admitted. Had this been carried as written, this KB
   would hold wrong data about a real project.
2. **`autowarefoundation/auto_e2e` was reported at 184★ on 2026-10-31** and the org listing today shows it
   updated **10 Nov 2026** — still inside the release wave above, so it is part of this batch rather than
   a separate event.
3. **Star drift:** **openpilot 64.0k → 64.1k** (and its own description now reads **300+** supported cars);
   **Autoware 12.2k — unchanged**; **Senna 558 → 559** between the third-party report and the page read.
   Small numbers, recorded because this file exists to measure movement rather than rediscover it.

### Also admitted this pass

- [hustvl/Senna](https://github.com/hustvl/Senna) — **Apache-2.0, 559★.** *"[IJCV 2026] Senna: Bridging
  Large Vision-Language Models and End-to-End Autonomous Driving."* Peer-reviewed, which almost nothing
  else in this field is. Found through the unlicensed `DatariusAI/AI-in-Automotive` feed — **the first
  time that reading-feed has earned its place in this KB.**
- [sunnypilot/sunnypilot](https://github.com/sunnypilot/sunnypilot) — **MIT, 2.2k★, 19,012 commits.** The
  significant openpilot fork, claiming **350+ car makes and models vs upstream's 300+**. The fork has
  *more* vehicle coverage than upstream under the same grant — check it when a client's vehicle is
  unsupported.
- [JohnsonJiang1996/Awesome-VLA4AD](https://github.com/JohnsonJiang1996/Awesome-VLA4AD) — Apache-2.0,
  631★ — and [worldbench/awesome-vla-for-ad](https://github.com/worldbench/awesome-vla-for-ad) — MIT,
  524★, 103 commits. Survey indexes, not code. ⚠️ **At least five near-identical forks of the latter
  exist** (`776styjsu`, `tongnie`, `ruiguoz`, `mengmengliu1998`, `worldbench`) with differing entries.
  `worldbench` is the apparent upstream. **Cite upstream only** — otherwise this KB acquires five rows
  for one artefact, the same duplicate-entity defect the education KB hit with `edx-platform`.

### 🟢 Data-integrity check on this file's own history (no history was altered)

The run contract warns that a row reading `| Nombre | Repo | Licencia |` has been compiled into a KB
entity literally named *"nombre"* more than once across industries. **Checked this file and
`repos/trending.md` for that defect. Result: not present as data.**

Both files contain **one Spanish-vocabulary header** —
`| Nombre | Licencia | Descripción | Stars |` — in the `2026-07-02` snapshot under
*"History — snapshots before 2026-10-15"*. In both cases it is a **genuine table header followed by ten
real data rows with live links**, and the 2026-10-15 pass already annotated that snapshot as an unfiltered
keyword scrape preserved *"for trend continuity, not as recommendations."*

**Nothing was deleted or rewritten** — this file is append-only and that snapshot is the trend record.
Two things are recorded instead, for whoever maintains the compiler:

1. **The header-skip guard must include the Spanish vocabulary** (`Nombre`, `Licencia`, `Descripción`,
   `Plataforma`, `Componente`), not only the English one. The education KB's guard already does; this is a
   note that automotive needs the same list.
2. **Four entries in that snapshot are not automotive software** (`MotionBastard` — After Effects motion
   design; `git-lanes` — generic git tooling; `AirForce-API-Auto-Register-System`; `video2robot` — general
   robotics) and **four carry `?` or `NOASSERTION` licences**, i.e. **no verified grant**. They remain
   excluded from every shelf in this KB. **An unfiltered scrape preserved as history is history; it is not
   a candidate list.**

### Declared gaps this window

- 🔴 **`huggingface.co` still does not resolve**, so **no model weights were licence-verified**, for the
  fourth pass running. This now blocks a specific decision: `autoware_latent_drive`'s repo has **no
  licence**, and its two ONNX models and all training detail live **only** on Hugging Face — so the model
  card is **the only place a grant could exist** and it cannot be read. **Escalation:** request
  `huggingface.co` in the session's allowed domains.
- 🔴 **No benchmark exists for any model in this release wave.** `vision_pilot` publishes none;
  `autoware_latent_drive` explicitly publishes none and offers only qualitative replays. The eight-model
  ADE/FDE table carried from AutoE2E's README (2026-10-31) remains **the only published multi-model open
  comparison in this field** — it was never like-for-like, and it now covers a **minority** of the
  available models. **It is ageing badly and should not be quoted as a ranking.**
- 🟢 **Three of the four "named but not measured" repos were measured before this pass closed**, all
  Apache-2.0 and all verified from their own pages: **`autoware-index`** (1★, *"Federated registry of
  community Autoware packages (distribution.yaml + sweep-driven validation history)"*),
  **`openadkit-rcar-x5h`** (0★, *"Board support for Open AD Kit on the Renesas R-Car X5H: AutoSD image,
  kernel, CR52 dual boot and demos"*) and **`autoware_carla_scenario`** (0★, pushed today, **no
  description set** — a repo being created as this was written). ⚪ **`autoware_system_designer` remains
  unmeasured** (Apache-2.0 per the org listing, stars/README unread).
- 🔴 **Generic agent searches produced nothing for the fifth pass.** `top open source AI agents automotive
  2026 github MIT` returned OpenClaw, OpenCode, OpenHands, CrewAI, Hermes Agent and AutoGPT (**archived
  28 Jan 2026**) — zero automotive content. **Methodological finding: in automotive, search the protocol,
  not the category.** `automotive MCP server vehicle diagnostics` returned eight real projects.

---

## 2026-10-31

**What moved:** the open end-to-end driving-model field turned into a **race with a published scoreboard**,
and a **vehicle-diagnostics agent layer appeared** where three previous passes recorded an empty category.

### 1. 🆕 AutoE2E v1.0 — released **29 October 2026**, two days before this snapshot

[`autowarefoundation/auto_e2e`](https://github.com/autowarefoundation/auto_e2e) · **Apache-2.0** · **184★** ·
38 forks · region **Global** (Autoware Foundation; Robotaxi working group, TIER IV-linked contributors)

First tagged release of a **camera-first** E2E driving model: **79.9M parameters**, six surround cameras at
10 Hz lifted into a BEV grid, optional map raster, GRU planner emitting **6.4 s of acceleration and
curvature**. Architecturally three cooperating models — the **Reactive** model drives today; the 1 Hz
**World Action** and **Reasoning** models are in development. Project's own speed figure: **~76 FPS**
(SwinV2-Tiny, feature-concat fusion, RTX 5080, batch 1). Positioned for two uses: fused with LiDAR/radar
safety layers for driverless robotaxis, or **camera-only for L2++ hands-free ADAS**.

🟢 **Licence settled by reading the file.** A TIER IV executive's LinkedIn posts describe the release as
**OpenMDW-1.1**; the repository's `LICENSE`, fetched raw today, is **verbatim Apache-2.0**, and the README
badge agrees. Recorded as Apache-2.0 for the code. **Weights unresolved** — see the channel gap below.

### 2. 🆕 Qwen-Drive-1.0 — Alibaba enters, and tops AutoE2E's own benchmark

[`QwenLM/Qwen-Drive-1.0`](https://github.com/QwenLM/Qwen-Drive-1.0) · **Apache-2.0** · **537★** · 56 forks ·
region **APAC**

*"An Initial Step towards a Vision-Language Foundation Model for Autonomous Driving."* A **Qwen3.5-4B** VLM
plus a **BEV perception head** (3D detection, occupancy, map segmentation) and a **flow-matching Planning
Expert**. At 4B it fills the gap between OpenDriveVLA (0.5B) and Alpamayo 1.5 (10B). Weights advertised on
Hugging Face and ModelScope as `Qwen/Qwen-Drive-1.0-4B`.

### 3. 🔴 The scoreboard — and why it is not a ranking

AutoE2E publishes an eight-model open-weights comparison on **KITScenes-Multimodal** validation, open-loop,
3 s horizon (read from the README today):

| Model | ADE @ 3 s | FDE @ 3 s |
|---|--:|--:|
| **Qwen Drive 1.0** | **0.565 m** | **1.397 m** |
| **AutoE2E** (fine-tuned) | 0.744 m | 1.980 m |
| Alpamayo 1.5 · SimForge · METEOR | all behind AutoE2E | — |

**The headline for this KB is uncomfortable and should be said plainly: the NVIDIA Alpamayo line this KB has
recommended as the reference stack since July is mid-table on a competitor's benchmark.** But the table is
**not like-for-like** — the README states inputs differ by model (AutoE2E receives an HD map and the route),
and the Qwen Drive row uses a different checkpoint and keyframe set. Treat it as the **first vendor-neutral
multi-model comparison in open AV**, not as a leaderboard. Reproducible: issue **#210** coordinates the
community benchmark, PRs **#220** and **#229** added the Qwen Drive and Alpamayo 1.5 evaluation scripts.

### 4. 🆕 A vehicle-diagnostics agent category now exists — at 0–8 stars

The category three passes called empty is no longer empty. Its scale is stated alongside it on purpose:

| Agent | Repo | Licence | ★ | Region |
|---|---|---|--:|---|
| Vehicle Diagnostic Assistant | [castlebbs/Vehicle-Diagnostic-Assistant](https://github.com/castlebbs/Vehicle-Diagnostic-Assistant) | MIT | 8 | EMEA |
| obd2-mcp | [shoka-jp/obd2-mcp](https://github.com/shoka-jp/obd2-mcp) | MIT | 2 | APAC |
| automotive-ai-skills | [shoka-jp/automotive-ai-skills](https://github.com/shoka-jp/automotive-ai-skills) | MIT | — | APAC |
| j2534-mcp-server | [cyrusdavirusss/j2534-mcp-server](https://github.com/cyrusdavirusss/j2534-mcp-server) | ⚠️ README "MIT", **no LICENSE file** (404 on both branches) | 0 | — |
| carvector-mcp | [carvectorio/carvector-mcp](https://github.com/carvectorio/carvector-mcp) | MIT **client for a keyed proprietary API** | 1 | — |

**The signal is not the stars, it is the convergence:** every one of these is an **MCP server**, and the
physical layer has settled on ELM327/OBD-II for consumer work and **J2534 for professional** work. The
plumbing standardised before anyone built the winning agent.

### 5. 🆕 Auto Agent Protocol — the dealership contract, 110★

[`auto-agent-protocol/auto-agent-protocol`](https://github.com/auto-agent-protocol/auto-agent-protocol) ·
**Apache-2.0** (spec/schemas/code) · docs **CC BY 4.0** · **110★** · region **Global**

*"The open automotive contract for MCP, A2A and Personal Agent Protocol: dealer discovery, inventory,
evidence, pricing and consented inquiries."* README describes **v3.1** as additive over the published 3.0
contract. Discovery pattern: the dealer domain publishes an **Agent Card**, a **Poppy document** and
**`llms.txt`** pointing at live MCP/A2A/PAP endpoints, with the MCP tool catalogue and A2A OpenAPI at
versioned `/v3.0/` paths. Independent of Google's A2A, which it builds on.

### 6. ⏸ Non-movement worth recording

**openpilot re-read today: MIT, 64.0k★ — unchanged** from 2026-10-26. After three passes of steady growth,
a flat reading is a data point rather than a gap.

### 🔴 Channel gap this snapshot

**`huggingface.co` does not resolve from this session** (DNS failure, consistent with the proxy's
allowed-domain policy), so **no model-weight licence was verified first-hand**. Given that this KB already
caught the Alpamayo 1.5 code/weights split (repo Apache-2.0, weights **OpenMDW-1.1**) and that a secondary
source makes the same claim for AutoE2E, the weights licences for **AutoE2E** and **Qwen-Drive-1.0** are
**explicitly unresolved**. Separately, `curl -sI` on `github.com` returns **HTTP 403** through this proxy, so
existence was proved with `git ls-remote` and figures read from rendered pages — the same constraint the
2026-10-26 and 2026-10-15 passes recorded.

### Regions represented this snapshot

**APAC** (Qwen-Drive-1.0, obd2-mcp, automotive-ai-skills) · **EMEA** (Vehicle Diagnostic Assistant) ·
**Global** (AutoE2E, Auto Agent Protocol). 🔴 **No LATAM-origin automotive AI agent or model appeared in
this snapshot** — consistent with every previous pass; the regional detail is in
[`../intel/market.md`](../intel/market.md).

## 2026-10-26

**What moved:** two additions that were missing rather than new — **Alpamayo 2 Super now has a verified
repository row**, and **a second open VLA line (OpenDriveVLA) exists** and had never been recorded here.
Plus one licence correction that matters more than either.

| Agent / model | Repo | Licence | Stars | Why it is trending |
|---|---|---|---|---|
| 🆕 Alpamayo 2 Super | [NVlabs/alpamayo2](https://github.com/NVlabs/alpamayo2) | Apache-2.0 | 287 | Open **34B** multi-task AV foundation model — 32B VLM backbone + 2B diffusion expert. The previous pass named it in prose; this is its first verified row. Largest open AV model in this KB. |
| 🆕 OpenDriveVLA | [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) | Apache-2.0 | 824 | **[AAAI 2026]** end-to-end VLA from an academic group, with a **0.5B checkpoint on Hugging Face** (2025/11/14). First credible open VLA line in this KB that is *not* NVIDIA's, and by far the smallest — which makes on-target work possible. |
| Alpamayo 1.5 | [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) | Apache-2.0 (code) · ⚠️ **OpenMDW-1.1 (weights)** | 370 | ↑ from 368. Still the practical entry point and the one the recipes target. **Licence split recorded for the first time — see below.** |
| Alpamayo Recipes | [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | Apache-2.0 | 217 | ↑ from 205. Recipe set verified: 1 SFT, 1.5 SFT (HF Trainer + DeepSpeed), 1.x RL (Cosmos-RL + GRPO), 1.5 quantization (FP8, NVFP4+FP8). |
| AlpaGym | [NVlabs/alpagym](https://github.com/NVlabs/alpagym) | Apache-2.0 | 163 | ↑ from 157. Closed-loop RL on AlpaSim. |
| AlpaSim | [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | Flat at 1.3k (rounded). Open AV simulator released with Alpamayo. |
| WorldEngine | [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 528 | ↑ from 520. Stable checkpoints 2026/09/15; post-training via 3DGS reconstruction + RL. |
| openpilot | [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | 64.0k | ↑ from 63.9k — **crossed 64k**. Largest permissive automotive codebase. |
| Alpamayo 1 Nano | [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) | Apache-2.0 | 2.1k | ↑ from 2.0k **while deprecated** — stars still accruing to the repository people should no longer start from. Banner: *"no longer under active development … limited maintenance updates."* |

🔴 **Licence correction, carried into `agents/top.md` and `compose/patterns.md` P6:** the Alpamayo 1.5
repository is Apache-2.0, **but its README states the model weights are under `OpenMDW-1.1`.** Every
earlier section of this file recorded Alpamayo 1.5 as plain Apache-2.0. Code licence ≠ weight licence;
read OpenMDW-1.1 before distributing fine-tuned derivatives.

**Negative result, recorded deliberately (sixth consecutive pass):** no automotive-specific *agent
framework* trended. `top open source AI agents automotive 2026 github MIT` and
`github trending automotive AI 2026` returned general-purpose frameworks with no automotive content
(OpenClaw, OpenCode, OpenHands, CrewAI, AutoGPT) plus 0-star unlicensed hobby projects.
`github.com/trending` still offers no automotive filter. See `agents/top.md` → "Verified but NOT usable".

**Method note:** `api.github.com` returns **HTTP 403** for repositories not attached to this session, so
every licence and star figure above was read from the rendered repository page on 2026-10-26, and every
URL was probed with `git ls-remote --symref` the same day.

---

## 2026-10-15

**What moved:** the Alpamayo line. Nothing else in automotive AI changed comparably this period.

| Agent / model | Repo | Licence | Stars | Why it is trending |
|---|---|---|---|---|
| Alpamayo 1.5 | [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) | Apache-2.0 | 368 | Current head of NVIDIA's open reasoning-VLA line (Mar 2026). RL-enhanced reasoning + navigation guidance + VQA. |
| AlpaSim | [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | Open AV simulator released with Alpamayo; fastest-growing of the new NVIDIA automotive repos. |
| Alpamayo Recipes | [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | Apache-2.0 | 205 | New developer hub; absorbed the SFT/RL scripts from the deprecated `NVlabs/alpamayo`. The place work actually happens now. |
| AlpaGym | [NVlabs/alpagym](https://github.com/NVlabs/alpagym) | Apache-2.0 | 157 | Closed-loop RL framework on AlpaSim — completes the open post-training loop. |
| WorldEngine | [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 520 | Updated Sep 2026 with stable checkpoints. Post-training via 3DGS scene reconstruction + RL. |

**Status change to note:** [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) (Apache-2.0, 2.0k★) now
carries a banner — *"no longer under active development ... limited maintenance updates"* — and redirects
to Alpamayo Recipes. Anyone who started from Alpamayo 1 Nano should migrate.

**Negative result, recorded deliberately:** no automotive-specific *agent framework* trended this period.
Searches (`top open source AI agents automotive 2026 github MIT`, `github trending automotive AI 2026`)
returned general-purpose frameworks (CrewAI, LangGraph, OpenHands, browser-use) with no automotive content,
plus 0-star unlicensed hobby projects. `github.com/trending` offers no automotive filter. See
`agents/top.md` → "Verified but NOT usable".

---

## History — snapshots before 2026-10-15

> ⚠️ **Accuracy note added 2026-10-15:** the snapshot below was produced by an unfiltered keyword scrape.
> Several entries are **not automotive software** — `MotionBastard` (After Effects motion design),
> `git-lanes` (generic git tooling for coding agents), `AirForce-API-Auto-Register-System` (unrelated API
> registration), `video2robot` (general robotics). Several carry `?` or `NOASSERTION` licences, meaning no
> verified grant. Preserved verbatim for trend continuity, **not** as recommendations.


> Última actualización: 2026-07-02

| Nombre | Licencia | Descripción | Stars |
|--------|----------|-------------|-------|
| [MotionBastard](https://github.com/luca1234413/MotionBastard) | MIT | Build AI motion design for After Effects and frontend animations from chat with  | 0 |
| [InterFuser-UI](https://github.com/zubairm8580/InterFuser-UI) | Apache-2.0 | Monitor InterFuser in real time with a Pygame UI for CARLA driving, showing came | 1 |
| [autoware_universe](https://github.com/autowarefoundation/autoware_universe) | Apache-2.0 |  | 1.7k |
| [git-lanes](https://github.com/ferdifi/git-lanes) | MIT | Enable parallel AI coding agents to work on a Git repository with isolated branc | 1 |
| [PCLA](https://github.com/MasoudJTehrani/PCLA) | Apache-2.0 | PCLA: A framework for testing autonomous agents in the CARLA simulator | 77 |
| [robotaxi-tpm-work-samples-](https://github.com/ramika2/robotaxi-tpm-work-samples-) | ? | 🚖 Explore robotaxi pain points through practical work samples focused on produc | 0 |
| [AirForce-API-Auto-Register-System](https://github.com/Nahsen1271/AirForce-API-Auto-Register-System) | Apache-2.0 | 🚀 Automate API registration with the AirForce system, simplifying the process a | 4 |
| [video2robot](https://github.com/ShiroNekoe/video2robot) | NOASSERTION | 🤖 Generate robot motions from video or prompts using an efficient end-to-end pi | 1 |
| [cockpit-agent](https://github.com/SuperdeMan/cockpit-agent) | ? | 面向智能座舱的云边协同 Multi-Agent 系统，支持端侧快意图、云端 LLM 规划、跨域 Agent 编排、车控 VAL 安全执行、HMI 流式交互、语义 | 1 |
| [Deconstructing-BYD-s-Technology-Architecture](https://github.com/vaisakhvenugopal/Deconstructing-BYD-s-Technology-Architecture) | ? | 🚗 Deconstructing BYD's Software-Defined Vehicle (SDV) & AI-DV Strategy. A deepl | 0 |

---
*Pipeline automático — se actualiza cada hora.*

