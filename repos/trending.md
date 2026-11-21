---
industry: automotive
region: Global
updated: 2026-11-21
---

# 📈 Trending repos — Automotive

> **APPEND-ONLY.** Newest dated section on top; history preserved below. Never rewrite earlier sections.

## 2026-11-21 — fourth pass (14:50Z)

**Window:** 2026-11-21 13:54Z → 14:50Z (≈1 hour, same day). Earlier sections preserved unchanged.
**Channel:** byte-read `LICENSE` from `raw.githubusercontent.com`, `gh api -X GET
search/repositories` for metadata, `WebFetch` on `github.com` for page-rendered counts.

### 🆕 The discovery ceiling was a query-shape artifact, not an exhausted world

Eight **short** `gh` queries returned **49 unique repositories; 22 already held; 27 new.** The
preceding passes' long natural-language queries return **literal zero** against the same index —
`search/repositories` matches name/description/topics only and ANDs every term, so a five-word phrase
asks for five words inside one short field. **Full defect write-up in `agents/trending.md` → this
date.** Rows below are new *to this KB*; most are years old. Detail: `repos/foundations.md` → **Layer H**.

| Repo | Licence (byte-read) | ★ | Pushed | Status |
|---|---|--:|---|---|
| [pylessard/python-udsoncan](https://github.com/pylessard/python-udsoncan) | **MIT**, `LICENSE.txt`, 1,074 b | 746 | 2026-10-26 | ✅ **New anchor.** UDS / ISO-14229 in Python |
| [oxibus/automotive_diag](https://github.com/oxibus/automotive_diag) | **MIT**, `LICENSE-MIT`, 1,139 b | 105 | 2026-11-09 | ✅ UDS + KWP2000 + OBD-II + DoIP constants (Rust) |
| [ecubus/EcuBus-Pro](https://github.com/ecubus/EcuBus-Pro) | ⚠️ **Apache-2.0 in `package.json` only — no `LICENSE` file** | 914 | 2026-11-05 | ⚠️ Open CANoe-class bench; grant is metadata-only |
| [cogu/autosar](https://github.com/cogu/autosar) | **MIT**, 1,088 b | 503 | 2026-10-16 | ✅ Python modules for AUTOSAR **ARXML** |
| [COVESA/vsomeip](https://github.com/COVESA/vsomeip) | **MPL-2.0**, 16,725 b | 1,471 | 2026-11-13 | ✅ **SOME/IP** middleware, COVESA-governed |
| [COVESA/dlt-viewer](https://github.com/COVESA/dlt-viewer) | **MPL-2.0**, 372 b (short form) | 557 | 2026-11-19 | ✅ Diagnostic Log & Trace viewer |
| [autonomousvision/transfuser](https://github.com/autonomousvision/transfuser) | **MIT**, 1,073 b | 1,616 | 2026-09-21 | ✅ PAMI'23 transformer sensor fusion; CARLA baseline |
| [sjtuyinjie/Ultra-Fusion](https://github.com/sjtuyinjie/Ultra-Fusion) | **MIT**, 1,074 b | 930 | 2026-08-29 | ✅ Multi-sensor SLAM under sensor degradation |
| [YuruiAI/DistillDrive](https://github.com/YuruiAI/DistillDrive) | **MIT**, 1,063 b | 127 | 2026-08-30 | ✅ ICCV'25 E2E driving distillation |
| [OpenSparX/MasterAgent](https://github.com/OpenSparX/MasterAgent) | **Apache-2.0**, 11,259 b | 966 | 2026-09-28 | ✅ **On-device agents, sub-100 ms on Qualcomm NPU, zero cloud** |
| [toyota-connected/ivi-homescreen](https://github.com/toyota-connected/ivi-homescreen) | **Apache-2.0**, 571 b (short notice) | 404 | 2026-11-21 | ✅ Flutter IVI embedder — Wayland, DRM/KMS, Vulkan |
| [Chanchaldhiman/CANviz](https://github.com/Chanchaldhiman/CANviz) | **MIT**, 1,076 b | 299 | 2026-08-08 | ✅ Browser-based CAN bus analyzer |
| [kkonteh97/SwiftOBD2](https://github.com/kkonteh97/SwiftOBD2) | **MIT** (API) | 163 | 2026-01-26 | ✅ Swift/iOS OBD-II library |
| [sw-mobility/open-sdv](https://github.com/sw-mobility/open-sdv) | **Apache-2.0**, 11,357 b, canonical | 12 | 2026-11-16 | 🌱 Early Apache SDV framework — watch item |
| [openmobilityfoundation/mobility-data-specification](https://github.com/openmobilityfoundation/mobility-data-specification) | **CC-BY-4.0**, 14,527 b | 754 | 2026-09-17 | 📄 **Data spec**, not code; right-of-way/geofence policy |

### 🔴 Excluded this pass — byte-read refused the grant

| Repo | ★ | API said | **Byte-read** | Why excluded |
|---|--:|---|---|---|
| [ucla-mobility/OpenCDA](https://github.com/ucla-mobility/OpenCDA) | 1,174 | `NOASSERTION` | **Academic Software License**, 1,882 b | *"academic or nonprofit researchers"* only; *"prohibited from further transferring"*; commercial use requires a separate licence. **Not open source.** |
| [riebl/vanetza](https://github.com/riebl/vanetza) | 231 | `NOASSERTION` | **CC-BY-NC**, 43,043 b | Non-commercial. The ETSI C-ITS stack — bites exactly where EMEA V2X work lands. |
| [Ircama/ELM327-emulator](https://github.com/Ircama/ELM327-emulator) | 708 | `NOASSERTION` | **CC-BY-NC**, 20,849 b | Non-commercial — **and it is the documented test dependency of MIT-licensed `Automotive-AI`.** |
| [autoas/as](https://github.com/autoas/as) | 966 | `NOASSERTION` | **GPL-3.0**, *"Version 3, 29 June 2007"* | Strong copyleft; AUTOSAR BSW |
| [TOSUN-Shanghai/TSMaster](https://github.com/TOSUN-Shanghai/TSMaster) | 442 | `LGPL-2.1` | **LGPL-2.1**, 26,526 b | Weak copyleft — linkable, not forkable-closed. APAC-origin CANoe peer |
| [linux-can/can-utils](https://github.com/linux-can/can-utils) | 2,961 | `None` | **no licence file at root** | Held to be per-file dual GPL-2.0/BSD-3; **no grant byte-read**, so unrecorded rather than guessed |
| [iDoka/awesome-automotive-can-id](https://github.com/iDoka/awesome-automotive-can-id) | 1,033 | `CC0-1.0` | **no licence file at root** | CAN-ID payload database; grant unverified |
| [MatthewKuKanich/CAN_Commander](https://github.com/MatthewKuKanich/CAN_Commander) | 1,094 | `None` | **no licence file** | CAN reverse-engineering tool; no grant |
| [hypery11/flipper-tesla-fsd](https://github.com/hypery11/flipper-tesla-fsd) | 1,336 | `NOASSERTION` | not read | ⛔ **Excluded on suitability as well as licence:** *"nag killer, FSD region unlock"* defeats vehicle restrictions. Not appropriate for a client engagement whatever its grant. |

> **3-for-3 again:** every refused grant above arrived as `NOASSERTION`/`None` from the API. **A short
> or absent SPDX is a pointer to read the bytes, not a licence.**

### ⚠️ `home-assistant/android` matched and is NOT automotive

Apache-2.0, 4,067★, pushed 2026-11-21 — it surfaced on `topic:automotive` because of Android Auto
support. **Recorded here as a known false positive** so a later pass does not "discover" it again.

## 2026-11-21 — third pass (13:40Z)

**Window:** 2026-11-21 12:45Z → 13:40Z (≈1 hour, same day). Earlier sections preserved unchanged.
**Channel:** `git ls-remote --symref` (liveness + default branch), byte-read `LICENSE` from
`raw.githubusercontent.com`, `gh api -X GET search/repositories` for metadata.

### 🆕 New layer, not new repos: the industrial-inspection stack enters this KB

The three rows below are **not newly created** — `anomalib` is years old at 6,414★. They are **newly
visible to this KB**, because five passes of `automotive`-worded queries could not see a layer that
never says "automotive". Full detail and the dataset trap: `repos/foundations.md` → **Layer G**.

| Repo | Licence (byte-read) | ★ / forks | Pushed | Default branch | Status |
|---|---|--:|---|---|---|
| [open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib) | **Apache-2.0**, 11,357 b, canonical | **6,414** / 1,047 | **2026-11-20** | `main` | ✅ **Live anchor.** Intel; 20+ anomaly algorithms; OpenVINO export |
| [sundyCoder/DEye](https://github.com/sundyCoder/DEye) | **Apache-2.0**, 11,357 b, canonical | 885 / 367 | ⚠️ 2023-03-14 | `master` | ⏸ Dormant 3.5 y — reference only |
| [awslabs/sagemaker-defect-detection](https://github.com/awslabs/sagemaker-defect-detection) | **Apache-2.0**, 10,142 b, canonical | 62 / 25 | ⚠️ 2022-12-21 | **`mainline`** | ⏸ Dormant 4 y — architecture reference |

**Note the third row's default branch.** It is `mainline`. A `main`-then-`master` licence probe reports
**"no licence file"** on an Apache-2.0 repo — the same false negative that `autoware-safety-island`
produced for a different reason (`license.rst`) in the 12:45Z pass. **Resolve the branch; do not guess
it.**

### 🔴 Rejected this window

| Repo | Measured | ★ | Verdict |
|---|---|--:|---|
| [kiralygomba/nottired_guard](https://github.com/kiralygomba/nottired_guard) | 🔴 **GPL-3.0**, 35,149 b | 1 | **Rejected** — copyleft *and* unpushed since 2024-03-08. Recorded because it is the **only** framework-grade open DMS in existence as far as three search legs can tell. |
| [charanvalavala/inspectlab](https://github.com/charanvalavala/inspectlab) | **MIT**, 1,077 b | **0** | Not recommendable at 0★. **Recorded for the licence lesson: the search snippet stated "its code is Apache-2.0"; the file byte-reads MIT.** A snippet licence is a claim, not a measurement — this KB's N11 error class, caught again. |

### ✅ Shelf re-verified under a stricter oracle — 193 slugs, 190 live, 3 dead

| Check | Result |
|---|---|
| Slugs probed | **193** (every distinct owner/name repository slug referenced in the eight files) |
| Live | **190** |
| Dead | **3** — `RobertSloan22/tars-car-mcp`, `luca1234413/MotionBastard`, `vaisakhvenugopal/Deconstructing-BYD-s-Technology-Architecture` (all three already recorded; **none is a recommendation**) |
| New dead since 12:45Z | **0** |
| Written licence vs. independently measured | **25 flagged → 0 real errors.** Every one was the differ attributing the wrong licence token to a line naming several repos, or catching the base's **own** claimed-vs-measured table. The KB was right in all 25. |
| Licence spread (byte-read, 190 live) | **82 Apache-2.0, 62 MIT, 20 no-licence-file, 4 BSD, 3 MPL, 3 LGPL, 3 GPL, 3 CC, 2 AGPL, 8 needing title-line classification** |

**Two independent re-measurements, 55 minutes apart, using different liveness oracles, returning the
same dead set and zero licence errors.** The shelf is in good condition and **further whole-shelf
re-probing is now low-value** — the binding constraint is discovery and primary-source access, not rot.

---

## 2026-11-21 — second pass (verification, 12:45Z)

**Window:** 2026-11-21 09:55Z → 12:45Z (≈3 hours, same day). The 09:55Z section below is preserved
unchanged. **Channel:** batched `gh api -X GET search/repositories` (8 slugs/query), byte-read
`LICENSE` from `raw.githubusercontent.com`, `git ls-remote` for exact-case liveness.

### ✅ Shelf re-measured from scratch: 188 URLs → 185 live, 3 dead, zero new rot

| Check | Result |
|---|---|
| URLs probed | **188** |
| Live | **185** |
| Dead | **3** — `RobertSloan22/tars-car-mcp`, `luca1234413/MotionBastard`, `vaisakhvenugopal/Deconstructing-BYD-s-Technology-Architecture` |
| New dead since 09:55Z | **0** — all three were already recorded as dead, **none is a recommendation** |
| Written licence ≠ measured SPDX | **20 rows → 0 real errors** (see `agents/top.md` §V1) |
| Archived repos presented as live | **0** — `ChanMeng666/automotive-repair-management-system`, `eclipse-score/inc_feo`, `microsoft/AutonomousDrivingCookbook` are all already labelled |

**An independent re-probe reproducing the prior pass's dead-URL set exactly is the strongest available
evidence that this file's addresses are trustworthy** — it is the first time the whole shelf has been
re-measured by a separate pass on the same day and agreed to the row.

**Liveness instrument note:** `git ls-remote` on a deleted or private repo fails with
`could not read Username for 'https://github.com'` — **an auth prompt, not a 404**. A control
(`COMMAAI/OPENPILOT`, deliberately wrong case) resolved **LIVE**, confirming **owner/repo case does not
affect the probe** and that the three failures above are genuine disappearances rather than case errors.

### 🆕 New repos this window

| Repo | Licence (byte-read 2026-11-21) | ★ | Note |
|---|---|--:|---|
| [LogosIntelligenceLab/SGDrive](https://github.com/LogosIntelligenceLab/SGDrive) | **MIT**, 1,077 bytes | 81 | **The only MIT-licensed driving model in this KB.** Pushed 2026-10-23. |
| [TUM-AVS/FM-AD-Survey](https://github.com/TUM-AVS/FM-AD-Survey) | **Apache-2.0**, 11,337 bytes | 249 | TU Munich foundation-models-for-AD survey, pushed 2026-11-19. |

### 📈 Measured movement — the VLA/world-model cluster is where the stars are going

`NVlabs/alpamayo-recipes` 205 → **245**, `NVlabs/alpamayo2` 287 → **314**, `QwenLM/Qwen-Drive-1.0`
537 → **563**, `OpenDriveLab/WorldEngine` 520 → **542**. Large-base repos essentially flat:
`commaai/openpilot` **64,192**, `ApolloAuto/apollo` **26,915** (⚠️ last pushed **2026-04-16**),
`carla-simulator/carla` **14,670**, `autowarefoundation/autoware` **12,268**, `traccar/traccar`
**8,162**. Small-base fast movers: `autowarefoundation/autoware_latent_drive` 42 → **95**,
`superdeman/cockpit-agent` 1 → **30**, `masoudjtehrani/pcla` 77 → **103**.
⚠️ Deltas are **drift since each row was written** (2026-10-31 → 2026-11-21), not a 3-hour rate.

### 🔴 Measured SPDX distribution across the 182 resolved rows — the shelf is 71% permissive

| Licence | Rows |
|---|--:|
| Apache-2.0 | **76** |
| MIT | **53** |
| `NOASSERTION` | 16 |
| `NONE` (no licence file) | 16 |
| MPL-2.0 / CC0-1.0 / BSD-3-Clause / AGPL-3.0 | 3 each |
| GPL-3.0 / EPL-2.0 | 2 each |
| GPL-2.0 / LGPL-2.1 / LGPL-3.0 / MIT-0 / BSD-2-Clause | 1 each |

**129 of 182 rows (71%) are MIT or Apache-2.0** — the two licences Globant can build on without
copyleft analysis. **Only 9 rows carry a copyleft grant**, and each is labelled as such in place.
**The 32 `NOASSERTION`/`NONE` rows are the real work surface**: this pass byte-read every one that a
written row claimed as permissive and found **no misstatement**, but they remain the rows where a
future automated checker will keep raising false alarms.

### 🔴 Declared gaps this window

- **`SpaceDrive`** (named as a CVPR 2026 driving project by an aggregator) — **no repository resolves.**
- **`carlover`** (MIT automotive assistant per an ecosystems aggregator) — **slug does not exist.**
  **Two aggregator-sourced candidates evaporated in one pass; resolve a slug before writing its row.**
- **Permissive dealership ERP/CRM: 7th consecutive negative.** `Dolibarr/dolibarr` **GPL-3.0** (7,889★),
  `YetiForceCompany/YetiForceCRM` **`NOASSERTION`, unpushed since 2024-09-13**, `SuiteCRM` unresolved.
  **`open-mercato/open-mercato` (MIT, 1,953★) is a framework, not a dealership product.**
- **`huggingface.co` DNS-dead (6th pass)** — weights licences unverifiable from this environment.

---


## 2026-11-21

**Window:** 2026-11-19 → 2026-11-21 (2 days). **Channel:** `git ls-remote` (liveness),
`raw.githubusercontent.com` (**byte-read LICENSE**, HTTP 200), `gh api -X GET search/repositories`
(stars/forks/`pushed_at`/`archived`). `github.com`, `api.github.com` and `gh api repos/<o>/<r>` are
**403**. **174 URLs probed, 170 live; 152 LICENSE files byte-read.**

### Seventh snapshot: still no automotive trending feed — but the *shelf audit* is now cheap

Six previous snapshots recorded that GitHub publishes no automotive trending feed and that the
rotation's prescribed query (`github trending automotive AI 2026`) returns general-purpose agent lists.
**Confirmed a seventh time, verbatim.** Today's run of that exact query returned: a DEV Community listicle,
two news-radar issue threads, a ZimaSpace blog, and the `automotive-ai` / `automotive` **topic pages** —
which are the only genuinely useful results in the set.

What changed is cheaper **maintenance**: `git ls-remote` probes the entire shelf for liveness with no API
quota at all, and `raw.githubusercontent.com` settles licences without the REST API. A full 174-URL
sweep now costs minutes. **Recommendation for the next pass: sweep every time, discover second.** An
audited shelf of 170 verified repos is worth more to an engagement than three new 0★ rows.

### Trending substitute that works — the two channels, ranked

1. **`gh api -X GET search/repositories`** with star + date floors. Still the best discovery channel.
   The 2026-11-19 insight holds: **search the standard, not the buzzword**
   (`AUTOSAR OR ISO26262 OR "ISO 21434"`), which is what found a 2,907★ repo five passes late.
2. **GitHub topic pages**, read as rendered pages: `github.com/topics/automotive-ai` (25 repos) and
   `github.com/topics/autonomous-driving` (3,344 repos). The `automotive-ai` topic is **small and
   low-star** — its top entry is 30★ — so it is readable end to end in one pass. The
   `autonomous-driving` topic is where the ★1k+ repos are.

### 🆕 Repos added to `repos/foundations.md` this window — the dormant perception commons

The `autonomous-driving` topic page surfaced nine canonical repos this base did not hold. **Seven of the
nine have not been pushed in over a year and one is formally archived** — which is itself the finding:

| Repo | Licence (byte-read) | ★ | Last push | State |
|---|---|--:|---|---|
| [fundamentalvision/BEVFormer](https://github.com/fundamentalvision/BEVFormer) | Apache-2.0 | 4,652 | 2024-08-15 | 🔴 Dormant 2+ yrs |
| [Ly0n/awesome-robotic-tooling](https://github.com/Ly0n/awesome-robotic-tooling) | CC0-1.0 | 3,924 | 2023-11-20 | 🔴 Dormant |
| [OpenDriveLab/End-to-end-Autonomous-Driving](https://github.com/OpenDriveLab/End-to-end-Autonomous-Driving) | MIT | 3,730 | 2025-07-02 | ⚠️ Slow |
| [waymo-research/waymo-open-dataset](https://github.com/waymo-research/waymo-open-dataset) | Apache-2.0 **except `wdl_limited/`** | 3,438 | 2026-01-08 | ⚠️ Slow |
| [PJLab-ADG/SensorsCalibration](https://github.com/PJLab-ADG/SensorsCalibration) | Apache-2.0 | 3,261 | 2024-06-17 | 🔴 Dormant |
| [zhulf0804/3D-PointCloud](https://github.com/zhulf0804/3D-PointCloud) | 🔴 **none** | 2,949 | 2024-08-30 | 🔴 Dormant, no grant |
| [daohu527/dig-into-apollo](https://github.com/daohu527/dig-into-apollo) | MIT | 2,457 | 2026-02-03 | ✅ Live-ish |
| [microsoft/AutonomousDrivingCookbook](https://github.com/microsoft/AutonomousDrivingCookbook) | MIT | 2,440 | 2025-08-25 | 🔴 **ARCHIVED** |
| [hustvl/YOLOP](https://github.com/hustvl/YOLOP) | MIT | 2,258 | 2023-10-20 | 🔴 Dormant 3 yrs |

**The automotive perception commons is frozen research code.** The live investment moved to end-to-end /
VLA models and the Autoware/Apollo stacks this base already tracks. Take **algorithms and calibration
maths** from these; take **runnable infrastructure** from the stacks. Note `waymo-open-dataset`'s API
licence is `NOASSERTION` only because of the named `src/waymo_open_dataset/wdl_limited` carve-out — a
carve-out is actionable, `NOASSERTION` is not.

### 🔴 `xtuple/xtuple` is gone

404 via `git ls-remote`. It appears in current ERP roundups (including one returned by today's searches)
and in older automotive-ERP shortlists. **Any shortlist citing XTuple is stale.** Live alternative found:
[idempiere/idempiere](https://github.com/idempiere/idempiere) — 678★, pushed 2026-11-20, but
**GPL-2.0** (byte-read; API says `NOASSERTION`), so it is a copyleft base, not a permissive one.

### Declared gaps this window

- **No open-source dealership DMS.** Searched `open source platform automotive ERP CRM dealership MIT
  Apache`; every hit is a general-purpose ERP/CRM (OFBiz, Huly, Krayin, iDURAR, Open Mercato, Dolibarr,
  iDempiere). Nothing with inventory + F&I + deal-desk modules. Seventh consecutive confirmation.
- **No LATAM-origin automotive repo** across four region-scoped searches. Informed gap, not coverage.
- **`huggingface.co` does not resolve** — no first-hand model-weight licences. Unchanged.


## 2026-11-19

**Window:** 2026-11-13 → 2026-11-19 (6 days). **Channel:** `gh api -X GET search/repositories`
(GitHub REST API — licence/stars/forks/push dates are first-hand API fields), rendered repository pages
for README substance, `raw.githubusercontent.com` for LICENSE files. `github.com` and `api.github.com`
are **HTTP 403** via `curl` (host policy, re-tested today). **11 queries run, 39 repos verified by exact
`repo:owner/name`, 39 resolved.**

### Still no "GitHub Trending for automotive" — and the substitute got better

Sixth snapshot recording this: GitHub publishes no automotive trending feed, and the generic queries the
rotation prescribes (`github trending automotive AI 2026`) return general-purpose agent lists. The
substitute that works is **the REST search API with a date floor and a star floor**, and this window it
produced a result the previous five passes missed entirely, because of one query shape:

```
AUTOSAR OR ISO26262 OR "ISO 21434" in:name,description,readme pushed:>2026-08-01 stars:>15
```

**Search the standard, not the buzzword.** That single query surfaced
`jherrodthomas/automotive-skills-suite` (**MIT, 2,907★**), `iDoka/awesome-canbus` (CC0, 3,571★),
`ebroecker/canmatrix` (BSD-2, 1,093★), `eclipse-iceoryx/iceoryx` (Apache-2.0, 2,212★),
`autoas/as` (965★) and `TrampolineRTOS/trampoline` (GPL-2.0, 759★) — six repos above 700★ that five
previous passes of protocol- and category-shaped queries never returned.

### The trend of the window: the open automotive stack grew *downward* and *sideways*, not upward

Previous windows recorded movement in the model tier (E2E/VLA) and then in the stack tier (vision_pilot,
S-CORE). This window the additions are **middleware, bus tooling and assurance** — the parts an SDV
programme bills the most hours against:

| Repo | Licence | ★ / forks | Pushed | Layer |
|---|---|--:|---|---|
| [iDoka/awesome-canbus](https://github.com/iDoka/awesome-canbus) | CC0-1.0 | 3,571★ / 426f | 2026-11-16 | Bus index |
| [Farama-Foundation/HighwayEnv](https://github.com/Farama-Foundation/HighwayEnv) | MIT | 3,342★ / 906f | 2026-11-11 | Simulation |
| [nanomq/nanomq](https://github.com/nanomq/nanomq) | MIT | 2,666★ / 325f | **2026-11-19** | SDV/edge broker |
| [eclipse-iceoryx/iceoryx](https://github.com/eclipse-iceoryx/iceoryx) | Apache-2.0 | 2,212★ / 491f | 2026-08-18 | Zero-copy IPC |
| [jherrodthomas/automotive-skills-suite](https://github.com/jherrodthomas/automotive-skills-suite) | MIT | **2,907★** / 141f | 2026-10-16 | Assurance |
| [Thinklab-SJTU/Awesome-LLM4AD](https://github.com/Thinklab-SJTU/Awesome-LLM4AD) | Apache-2.0 | 1,906★ / 115f | 2026-10-15 | Index |
| [ShisatoYano/AutonomousVehicleControlBeginnersGuide](https://github.com/ShisatoYano/AutonomousVehicleControlBeginnersGuide) | MIT | 1,963★ | **2026-11-19** | Onboarding |
| [hanruihua/ir-sim](https://github.com/hanruihua/ir-sim) | MIT | 1,239★ | 2026-11-18 | Simulation |
| [eclipse-ecal/ecal](https://github.com/eclipse-ecal/ecal) | Apache-2.0 | 1,060★ | **2026-11-19** | Middleware |
| [worldbench/awesome-3d-4d-world-models](https://github.com/worldbench/awesome-3d-4d-world-models) | Apache-2.0 | 1,031★ | 2026-11-14 | Survey (TPAMI 2026) |
| [ebroecker/canmatrix](https://github.com/ebroecker/canmatrix) | BSD-2-Clause | 1,093★ / 441f | 2026-11-18 | ARXML ⇄ DBC |
| [autoas/as](https://github.com/autoas/as) | ⚠️ `NOASSERTION` | 965★ | 2026-11-18 | AUTOSAR BSW |
| [autowarefoundation/AWSIM](https://github.com/autowarefoundation/AWSIM) | 🔴 bespoke | 765★ / 163f | 2026-10-20 | Digital twin |
| [TrampolineRTOS/trampoline](https://github.com/TrampolineRTOS/trampoline) | 🔴 GPL-2.0 | 759★ | 2026-10-19 | OSEK/AUTOSAR OS |
| [xiaomi-research/recogdrive](https://github.com/xiaomi-research/recogdrive) | Apache-2.0 | 631★ / 78f | **2026-11-19** | E2E policy (ICLR 2026) |
| [TOSUN-Shanghai/TSMaster](https://github.com/TOSUN-Shanghai/TSMaster) | ⚠️ LGPL-2.1 | 442★ | 2026-10-28 | Bus tooling |
| [nv-tlabs/omni-dreams](https://github.com/nv-tlabs/omni-dreams) | Apache-2.0 | 367★ / 27f | 2026-10-02 | World model (NVIDIA) |
| [ThinkOffApp/CarWatch](https://github.com/ThinkOffApp/CarWatch) | 🔴 AGPL-3.0 | 306★ / 20f | 2026-10-09 | In-car agent |

### Movement in tracked repos

| Repo | Then | Now (2026-11-19) | Read |
|---|---|---|---|
| `commaai/openpilot` | 64.1k★ (2026-11-13) | **64,177★ / 11,410f**, pushed 2026-11-19, 141 open issues | Flat in 6 days, as expected at this size |
| `autowarefoundation/vision_pilot` | 927★ / 196f / 4,282 commits | **928★ / 197f**, pushed 2026-11-17, 23 open issues | +1★ in 6 days. **The 2026-11-13 "headline" is real but not yet growing.** Recorded plainly rather than re-narrated. |
| `autowarefoundation/autoware` | 12.2k★ | **12,265★ / 3,752f**, pushed 2026-11-19, 74 open issues | Steady |
| `NVlabs/alpasim` | — | **1,304★ / 170f**, pushed 2026-11-19, 20 open issues | Active |
| `auto-agent-protocol/auto-agent-protocol` | 110★ (2026-10-31) | **112★**, pushed 2026-11-19 | +2★ in 19 days. The dealership contract layer is alive but **not** gaining adoption. Treat as a specification to implement, not a community to join. |
| `sunnypilot/sunnypilot` | 2.2k★ | **2,178★**, pushed 2026-11-19 | Steady |
| `openremote/fleet-management` | — | **51★**, `NOASSERTION`, pushed 2026-10-13 | Licence still unclassified; the telematics gap holds |

### 🆕 New repos admitted this snapshot (beyond the table above)

- **openpilot ecosystem:** [`zoompilot/jetlink`](https://github.com/zoompilot/jetlink) (MIT, 57★/**40f**),
  [`zoompilot/zoompilot`](https://github.com/zoompilot/zoompilot) (MIT, 37★/31f, pushed 2026-11-19),
  [`YassineYousfi/openpilot.distill`](https://github.com/YassineYousfi/openpilot.distill) (MIT, 38★),
  [`StarPilotHQ/StarPilot`](https://github.com/StarPilotHQ/StarPilot) (MIT, 163★),
  [`commaai/connect`](https://github.com/commaai/connect) (MIT, 153★),
  [`Sherin-SEF-AI/Lyne-ADAS`](https://github.com/Sherin-SEF-AI/Lyne-ADAS) (MIT, 22★, pushed 2026-11-18).
- **Assurance:** [`jherrodthomas/LionDriver`](https://github.com/jherrodthomas/LionDriver) (MIT, 65★,
  pushed 2026-11-19),
  [`Lieubk/automotive-safety-security-assurance-kit`](https://github.com/Lieubk/automotive-safety-security-assurance-kit)
  (MIT, 2★, **created today**).
- **Benchmark:** [`aditya-ramabadran/drivingbench_harness_code`](https://github.com/aditya-ramabadran/drivingbench_harness_code)
  (MIT, 63★/8f).
- **SDV:** [`eclipse-leda/leda-distro`](https://github.com/eclipse-leda/leda-distro) (Apache-2.0, 21★),
  [`de4sdv/DE4SDV`](https://github.com/de4sdv/DE4SDV) (Apache-2.0, 13★, **SysML v2**, pushed
  2026-11-19), [`xronos-inc/xronos`](https://github.com/xronos-inc/xronos) (BSD-3, 41★).
- **World models / policies:** [`LMD0311/HERMES`](https://github.com/LMD0311/HERMES) (Apache-2.0, 265★),
  [`H-EmbodVis/HERMESV2`](https://github.com/H-EmbodVis/HERMESV2) (Apache-2.0, 73★, IEEE TPAMI),
  [`H-EmbodVis/SimWAM`](https://github.com/H-EmbodVis/SimWAM) (**MIT** per raw LICENSE, 212★),
  [`AFARI-Research/WA-JEPA`](https://github.com/AFARI-Research/WA-JEPA) (Apache-2.0, 89★),
  [`HaoranZhuExplorer/AD-E2E-JEPA`](https://github.com/HaoranZhuExplorer/AD-E2E-JEPA) (Apache-2.0, 82★),
  [`TabGuigui/WorldDrive`](https://github.com/TabGuigui/WorldDrive) (Apache-2.0, 85★, NeurIPS 2026),
  [`chenshi3/DriveWAM`](https://github.com/chenshi3/DriveWAM) (Apache-2.0, 70★, NeurIPS 2026),
  [`ASGuard-UCI/safedrive-vla`](https://github.com/ASGuard-UCI/safedrive-vla) (Apache-2.0, 36★,
  CoRL 2026), [`OpenDriveLab/ViRA`](https://github.com/OpenDriveLab/ViRA) (Apache-2.0, 38★),
  [`curryqka/AgentThink`](https://github.com/curryqka/AgentThink) (Apache-2.0, 154★, EMNLP 2025).
- **V2X:** [`thi-ad/UrbanIng-V2X`](https://github.com/thi-ad/UrbanIng-V2X) (MIT, 88★, NeurIPS 2025),
  [`radar-lab/OpenCDA-MARL`](https://github.com/radar-lab/OpenCDA-MARL) (Apache-2.0, 16★).

**Licence composition of the 14 new model/world-model rows: 11 Apache-2.0, 1 MIT, 2 none.** The research
tier has become licence-safe by convention — a change worth recording, because two passes ago the
no-licence rate in this tier was the main obstacle.

### 🔴 Verified and deliberately excluded

| Repo | ★ | Reason |
|---|--:|---|
| [`ThinkOffApp/CarWatch`](https://github.com/ThinkOffApp/CarWatch) | 306★ | **AGPL-3.0** network copyleft |
| [`TrampolineRTOS/trampoline`](https://github.com/TrampolineRTOS/trampoline) | 759★ | **GPL-2.0** |
| [`TOSUN-Shanghai/TSMaster`](https://github.com/TOSUN-Shanghai/TSMaster) | 442★ | **LGPL-2.1** + *"free for research and education for some features"* |
| [`autowarefoundation/AWSIM`](https://github.com/autowarefoundation/AWSIM) | 765★ | **Bespoke "AWSIM License"** — raw LICENSE reads *"AWSIM Licenses — AWSIM License Applies to autowarefoundation/AWSIM repositories and all content contained in the Releases"*. **Not Apache-2.0.** `autoware` and `autoware_universe` unaffected. |
| [`AtsushiSakai/PythonRobotics`](https://github.com/AtsushiSakai/PythonRobotics) | 30,951★ | `NOASSERTION` — the largest unclassified-licence repo in this KB. Settle before vendoring. |
| [`autoas/as`](https://github.com/autoas/as) | 965★ | `NOASSERTION` — the only substantial open AUTOSAR BSW; licence must be settled first |
| [`LMD0311/Awesome-World-Model`](https://github.com/LMD0311/Awesome-World-Model) | 2,304★ | No licence — read, do not vendor |
| [`Little-Podi/Collaborative_Perception`](https://github.com/Little-Podi/Collaborative_Perception) | 639★ | No licence |
| [`liushengjia-AAL/shengjia`](https://github.com/liushengjia-AAL/shengjia) | 21★ | No licence **and** ECU remapping content — out of scope twice over |
| [`vxedge/*`](https://github.com/vxedge/vxedge) | 0–1★ | Apache-2.0 and architecturally interesting (manifest-driven SDV testbed, OTA, SysML v2, `vxmcp` on MCP spec 2026-07-28, ARINC-665-shaped part numbers) but **single-contributor, six weeks old**. Watch item. |

### ⚠️ Name collision recorded

`visionpilot-project/VisionPilot` (**MIT, 43★**, BeamNG.tech AD simulation with Foxglove) is **not**
`autowarefoundation/vision_pilot` (**Apache-2.0, 928★/197f**, L2 ADAS stack). Both answer to
"VisionPilot". **Full `owner/name` in every SoW and ADR.**

### Declared negatives for this snapshot

1. `EV battery charging AI … stars:>15 pushed:>2026-08-01` → **0 repos.**
2. `automotive manufacturing quality inspection AI … stars:>3 pushed:>2026-06-01` → **0 repos.**
3. `fleet management telematics … stars:>5 pushed:>2026-08-01` → **2 repos.**
4. `car dealership management … pushed:>2026-01-01` → 408 repos, **top star count 5**, nearly all
   unlicensed. DMS gap holds for a fifth pass.
5. `autonomous driving OR automotive OR vehicle in:name,description created:>2026-09-15 stars:>25` →
   **80 repos, and essentially none are automotive**: the word "autonomous" is dominated by autonomous
   *agent* projects (pentest legions, dev harnesses, desktop agents). **Recorded as a query-design
   finding**: the token "autonomous" is no longer an automotive signal in 2026 and must be paired with
   `driving`, `vehicle`, `ADAS` or a standard name.
6. **No LATAM-origin automotive repository** in any of the 11 queries. Fifth consecutive snapshot.
7. **`drivingbench.com` not fetched** — repository page only. No benchmark scores available.

### 🟢 Data-integrity check on this file's own history

The 2026-11-13, 2026-10-31, 2026-10-26 and 2026-10-15 sections and the pre-2026-10-15 history below were
read before writing and are **unchanged**. This section was inserted above them. Where this snapshot
contradicts an earlier one — the agent-category star ceiling, and the `vision_pilot` growth expectation
— the contradiction is stated **here**, and the earlier text is left as written.

**Header-as-data check (run this pass, both trending files).** Every markdown table in all eight files
was parsed programmatically: **0 of them have a first row lacking a `|---|` separator**, so there is no
header row sitting in the data. The two Spanish-language headers in the pre-2026-10-15 history
(`| Nombre | Licencia | Descripción | Stars |`) *are* well-formed headers — each is followed by a
separator row — and they were therefore **left byte-for-byte unchanged** rather than rewritten. If a
compiler has ever produced an entity named `nombre` from this KB, the defect is in the compiler's table
parsing, not in these files; the fix belongs upstream and the history should not be edited to work
around it.

## 2026-11-13

**Window:** foundational and trending automotive repos, 10–13 Nov 2026. Verified from the rendered
repository page (GitHub licence field + star count), with licences settled by fetching the file raw.
`curl` and `api.github.com` are both **HTTP 403** in this session. **The whole trend this window comes
from one organisation.**

### There is no "GitHub Trending for automotive", and that is a finding

`github trending automotive AI 2026` does **not** return a trending page filtered to automotive — no such
view exists. It returns topic pages (`/topics/automotive`, `/topics/automotive-ai`), a daily-refreshed
research feed, and general AI-agent roundups with no automotive content. **Three passes have now confirmed
this.** The usable substitutes, in order:

1. **An organisation's "recently pushed" listing.** `github.com/orgs/autowarefoundation/repositories?sort=updated`
   is where this entire window's trend was found. For an industry whose open source concentrates in one or
   two foundations, **watching the org beats watching trending.**
2. [DatariusAI/AI-in-Automotive](https://github.com/DatariusAI/AI-in-Automotive) — a daily-refreshed hub of
   automotive AI research and code from arXiv and GitHub. 🔴 **No licence**, so it is a *reading feed*, not
   a dependency. It earned its keep this pass by surfacing `hustvl/Senna`.
3. **Topic pages**, which are low-signal but did surface the VLA-for-AD survey lists.

### The trend: Autoware Foundation published a vertical ADAS slice in three days

Eight repositories pushed 10–12 Nov 2026, all verified individually:

| Repo | Licence | ★ | Commits | Layer |
|---|---|--:|--:|---|
| [vision_pilot](https://github.com/autowarefoundation/vision_pilot) | Apache-2.0 | **927** | 4,282 | **Production L2 ADAS stack** |
| [agnocast](https://github.com/autowarefoundation/agnocast) | Apache-2.0 | 212 | 1,258 | ROS 2 zero-copy IPC middleware |
| [alpamayo-autoware](https://github.com/autowarefoundation/alpamayo-autoware) | Apache-2.0 | 161 | 42 | Fork of NVlabs/alpamayo (`alpamayo2.0-edge`) |
| [autoware_latent_drive](https://github.com/autowarefoundation/autoware_latent_drive) | 🔴 **NONE** | 42 | 64 | Latent-space planner — **unusable** |
| [autoware-safety-island](https://github.com/autowarefoundation/autoware-safety-island) | Apache-2.0 (`license.rst`) | 8 | 608 | ARM-SoC safety island |
| [scene_3d](https://github.com/autowarefoundation/scene_3d) | Apache-2.0 | 2 | 3 | Monocular depth (AutoSeg FM) |
| [autoware.trucks](https://github.com/autowarefoundation/autoware.trucks) | Apache-2.0 | 2 | 9 | Trucking autonomy charter |
| [ego_lanes](https://github.com/autowarefoundation/ego_lanes) | Apache-2.0 | 1 | 30 | Lane-boundary segmentation |

**Read the star distribution, not just the names.** One repo at 927★, two in the low hundreds, and four in
single digits. This is **not** an ecosystem of eight healthy projects — it is **one real stack plus its
freshly published components**. The right engagement posture is to build on `vision_pilot` and `agnocast`,
and to treat `scene_3d`, `ego_lanes` and `autoware.trucks` as **components whose APIs will churn**.

**The structural signal:** the Autoware Foundation is moving from *"the vendor-neutral AV research stack"*
to *"a vendor-neutral ADAS product stack with silicon support and a safety story"* — `vision_pilot` (L2
features), `autoware-safety-island` (ARM SoC safety element), `openadkit-rcar-x5h` (Renesas R-Car X5H
board support) and an ISO 26262 / ISO 8800 roadmap are the same move seen from four angles. For a Tier-1
or OEM engagement, that is the first open stack that answers "how would we ever certify this" with
something other than silence.

### Movement on existing rows

| Repo | Previous | Now | Note |
|---|---|---|---|
| [commaai/openpilot](https://github.com/commaai/openpilot) | 64.0k | **64.1k** | Description now reads **300+** supported cars |
| [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | 12.2k | **12.2k** | Unchanged — second pass running, worth recording |
| [autowarefoundation/auto_e2e](https://github.com/autowarefoundation/auto_e2e) | 184 | 184 ⏸ | Org listing shows it pushed **10 Nov 2026**, so it is part of this wave |

### New non-Autoware repos admitted

- [sunnypilot/sunnypilot](https://github.com/sunnypilot/sunnypilot) — **MIT, 2.2k★, 19,012 commits.** The
  significant openpilot fork, **350+ car makes and models vs upstream's 300+**. A fork with broader
  hardware coverage than upstream, under the same grant.
- [hustvl/Senna](https://github.com/hustvl/Senna) — **Apache-2.0, 559★.** IJCV 2026 VLM↔E2E bridge.
- [JohnsonJiang1996/Awesome-VLA4AD](https://github.com/JohnsonJiang1996/Awesome-VLA4AD) — Apache-2.0, 631★.
- [worldbench/awesome-vla-for-ad](https://github.com/worldbench/awesome-vla-for-ad) — MIT, 524★, 103
  commits. ⚠️ **Five near-identical forks exist** (`776styjsu`, `tongnie`, `ruiguoz`,
  `mengmengliu1998`, `worldbench`); `worldbench` is the apparent upstream and links
  `worldbench.github.io/vla4ad`. **Cite upstream only** — five rows for one artefact is a data defect.

### ERP/CRM candidates probed for the aftersales slot — and three secondary-source licence claims broken

Searched `open source platform automotive ERP CRM dealership MIT Apache`. **No dealership-specific open
platform exists** (fifth consecutive pass). General ERP/CRM probed instead; see
`verticals/solutions.md` for the full reasoning.

| Repo | Claimed by search | **Actually (page read today)** | Verdict |
|---|---|---|---|
| [aureuserp/aureuserp](https://github.com/aureuserp/aureuserp) | MIT | **MIT**, 12.2k★ | ✅ Claim held. Admitted |
| [open-mercato/open-mercato](https://github.com/open-mercato/open-mercato) | "MIT core" | **MIT**, 1.9k★ — **but `packages/enterprise` is under a separate commercial licence** | ⚠️ Admitted with the carve-out recorded |
| [idurar/idurar-erp-crm](https://github.com/idurar/idurar-erp-crm) | *"fully open-source under the MIT license"* | 🔴 **AGPL-3.0**, 9.0k★ | ❌ **Claim false.** Strong copyleft — excluded |
| [hcengineering/platform](https://github.com/hcengineering/platform) (Huly) | *"Apache License 2.0"* | 🔴 **EPL-2.0**, 28.1k★, **and the page states the repo is "frozen and is no longer actively maintained"** | ❌ **Claim false twice** — wrong licence *and* dead. Excluded |

**Three of four licence claims from search summaries were wrong or incomplete, in a single batch.** Two
would have put strong-copyleft or abandoned code onto a buildable shelf. This is the strongest evidence
yet for the pipeline's own rule: **the repository page is the source; a search summary is a lead.**

### 🟢 Data-integrity check on this file's own history (no history was altered)

Checked for the placeholder-row defect the run contract warns about (a header row compiled into an entity
named *"nombre"*). **Not present as data.** The `2026-07-02` snapshot below carries one Spanish header,
`| Nombre | Licencia | Descripción | Stars |`, followed by **ten real data rows with live links** — a
genuine header, not a placeholder. The 2026-10-15 pass already recorded that this snapshot was
**byte-identical to `agents/trending.md`**, i.e. the same scrape written to both files, so it recorded no
distinct *repo* trend at all.

**Nothing was deleted or rewritten** (this file is append-only). Recorded for the compiler instead: the
header-skip guard needs the **Spanish** vocabulary (`Nombre`, `Licencia`, `Descripción`, `Plataforma`,
`Componente`) as well as the English, and the snapshot's `?` / `NOASSERTION` licence rows carry **no
verified grant** and stay excluded from every shelf.

### Declared gaps this window

- 🟢 **Measured before close** (all Apache-2.0, read from their own pages): `autoware-index` **1★**
  (*"Federated registry of community Autoware packages (distribution.yaml + sweep-driven validation
  history)"*), `openadkit-rcar-x5h` **0★** (*"AutoSD image, kernel, CR52 dual boot and demos"* for the
  Renesas R-Car X5H), `autoware_carla_scenario` **0★** (pushed today, no description set).
  ⚪ **Still unmeasured:** `autoware_system_designer`.
- 🔴 **`huggingface.co` unreachable** — no model weights verified, fourth pass running.
- 🔴 **`www.manilatimes.net` unreachable** — the TIER IV announcement of this release wave could not be
  read; repositories used as the primary source instead.
- 🔴 **No LATAM-origin automotive repository found. Fifth pass, zero.** Durable finding, not a miss.
- 🔴 **No open-source DMS. Fifth pass.** The search explicitly confirms general ERP/CRM candidates lack
  **inventory-by-VIN, deal jacket and DMS integration**.

---

## 2026-10-31

**Method note unchanged and still binding:** `github.com/trending` has **no automotive topic filter**, and
`curl -sI` against `github.com` returns **HTTP 403** through this session's proxy. So this file is not a
scrape of a trending page — it is a dated record of repositories located by targeted search and then
verified with `git ls-remote` plus a rendered-page read. 🔴 **`huggingface.co` does not resolve from this
session**, so weight repositories could not be inspected.

### New this snapshot

| Repo | Licence | ★ | Region | Why it is here |
|---|---|--:|---|---|
| [autowarefoundation/auto_e2e](https://github.com/autowarefoundation/auto_e2e) | **Apache-2.0** (`LICENSE` read raw) | 184 | Global | **AutoE2E v1.0 tagged 29 Oct 2026** — the freshest significant release in this KB. Camera-first E2E driving model, 79.9M params, 6 cameras @10 Hz, 6.4 s plan horizon, ~76 FPS on an RTX 5080. 38 forks. Autoware Foundation Robotaxi working group. |
| [QwenLM/Qwen-Drive-1.0](https://github.com/QwenLM/Qwen-Drive-1.0) | Apache-2.0 | 537 | APAC | Alibaba's open AV VLA: Qwen3.5-4B + BEV perception head + flow-matching planner. **Tops AutoE2E's published eight-model comparison.** 56 forks. |
| [auto-agent-protocol/auto-agent-protocol](https://github.com/auto-agent-protocol/auto-agent-protocol) | Apache-2.0 spec/schemas/code · docs CC BY 4.0 | 110 | Global | The open dealership contract over MCP + A2A + PAP. **The only thing found in the retail layer with real governance** after three passes concluding the layer is closed. |
| [castlebbs/Vehicle-Diagnostic-Assistant](https://github.com/castlebbs/Vehicle-Diagnostic-Assistant) | MIT (`LICENSE` read raw) | 8 | EMEA | Most complete open diagnostics agent design: LangGraph + MCP over streamable HTTP, sandboxed OBD-II formula evaluator, NHTSA vPIC VIN decode, ELM327→CAN hardware path. |
| [shoka-jp/obd2-mcp](https://github.com/shoka-jp/obd2-mcp) | MIT (`LICENSE` read raw) | 2 | APAC | ELM327 MCP server with a **bundled mock vehicle** — runs with no hardware, which is what makes it demo-able. |
| [shoka-jp/automotive-ai-skills](https://github.com/shoka-jp/automotive-ai-skills) | MIT (`LICENSE` read raw) | — | APAC | Companion skill pack to `obd2-mcp`: diagnostics, maintenance, repair, EV. |

### Verified and deliberately excluded

| Repo | Licence state | Why excluded |
|---|---|---|
| [cyrusdavirusss/j2534-mcp-server](https://github.com/cyrusdavirusss/j2534-mcp-server) | ⚠️ README says "MIT"; **no `LICENSE` file** — `LICENSE`, `LICENSE.md`, `LICENSE.txt` all **404 on `main` and `master`**; sidebar names no licence | Deepest vehicle access of anything found this pass (J2534 PassThru: CAN channels, UDS/OBD-II/KWP2000, DTC lookup, PID decoding, tested on Toyota/Lexus) and **the one that cannot be built on**. 0★. |
| [carvectorio/carvector-mcp](https://github.com/carvectorio/carvector-mcp) | MIT, client only | README: bundles **no data**, every call forwards to the **keyed CarVector API**, exits without `CARVECTOR_API_KEY`. Open client, proprietary service. 1★. |
| [navariltd/Fleet-Management-System](https://github.com/navariltd/Fleet-Management-System) | ⚠️ **GPL-3.0** (README + badge; sidebar does not name it) | Frappe-framework fleet solution, default branch `develop`, 12★/18 forks. Copyleft — unusable as a base for a proprietary client deliverable. Recorded so it is not rediscovered as a candidate. |
| [Dolibarr/dolibarr](https://github.com/Dolibarr/dolibarr) | ⚠️ **GPL-3.0** (sidebar) | 7.8k★ PHP ERP/CRM, default branch `develop`. Came up as an ERP base for aftersales; **GPL-3.0 rules it out** where Odoo (LGPL-3.0) and OFBiz (Apache-2.0) are already recorded. Negative result, now settled. |
| [rgy2291929165-boop/vehicle-diagnosis-agent](https://github.com/rgy2291929165-boop/vehicle-diagnosis-agent) | not read | EV fault analysis, RAG + LangGraph + MCP **with a human-approval gate**. Snapshot 2026-10-19; README says learning project on **simulated data catalogues**. |

### Declared negatives for this snapshot

- 🔴 **No LATAM-origin automotive repository found**, in this or any previous pass.
- 🔴 **No open-source Dealership Management System still exists.** Searched again; the finding is unchanged.
  What changed is that an **open contract** to reach dealerships now exists (Auto Agent Protocol above) —
  see [`../verticals/solutions.md`](../verticals/solutions.md).
- ⏸ **openpilot: MIT, 64.0k★ — unchanged** from 2026-10-26.

## 2026-10-26

**Method note stands, and is the reason this file reads the way it does:** `github.com/trending` has **no
automotive topic filter**, and the relevant topic pages (`automotive-ai`, `automotive`,
`autonomous-vehicles`, `automotive-data`) surface mostly 0–5 star projects. There is no reliable trending
feed for this industry. What follows is movement in *verified* repos plus vendor/foundation releases — the
only signal available. 🔴 Additional constraint this pass: `api.github.com` returns **HTTP 403** for
repositories not attached to this session, so all figures were read from rendered repository pages.

### The find of this pass: Eclipse S-CORE was invisible to the previous one

| Repo | Licence | Stars | Movement |
|---|---|---|---|
| 🆕 [eclipse-score/score](https://github.com/eclipse-score/score) | Apache-2.0 | 111 | **First appearance in this KB.** The ASIL-B-targeted open SDV platform core. Releases read from the GitHub releases page today: `v0.7.3` (07 Oct), `v0.7.2` (02 Sep), `v0.7.1`/`v0.7.0` (24 Aug), `v0.6.4` (07 Aug), `v0.6.3` (31 Jul), `v0.6.2` (14 Jul), `v0.6.1` (13 Jul), `v0.6.0` (26 Jun), `v0.5.5` (26 Apr) — **ten releases, ~monthly, all 2026.** VDA memorandum now 32 companies; Hyundai Mobis joined May 2026; Qorix ships a commercial distribution on top. |
| 🆕 [eclipse-score/inc_feo](https://github.com/eclipse-score/inc_feo) | Apache-2.0 | 7 | Incubation repo for the fixed execution order framework — deterministic execution, the piece a safety argument needs. 7 stars: design input, not a shippable dependency. |
| 🆕 [eclipse-sdv-blueprints/fleet-management](https://github.com/eclipse-sdv-blueprints/fleet-management) | Apache-2.0 | 27 | **Most immediately useful new repo for engagement work.** Runnable topology: Kuksa CSV Provider → Databroker → FMS Forwarder → **Eclipse uProtocol** → FMS Consumer → InfluxDB → Grafana, plus an **rFMS API** server. Replaces ~2 weeks of architecture debate at project start. |

### Movement in tracked repos

| Repo | Licence | Stars | Movement |
|---|---|---|---|
| 🆕 [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) | Apache-2.0 | 824 | First appearance. AAAI 2026 end-to-end VLA with a **0.5B** Hugging Face checkpoint — the small-model option this KB lacked. |
| 🆕 [NVlabs/alpamayo2](https://github.com/NVlabs/alpamayo2) | Apache-2.0 | 287 | First verified row. 34B (32B VLM + 2B diffusion expert). |
| [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | 64.0k | ↑ 63.9k → **64.0k**, crossed 64k. |
| [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) | Apache-2.0 | 2.1k | ↑ 2.0k → 2.1k **while deprecated**. |
| [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | Apache-2.0 | 217 | ↑ from 205. The hub where Alpamayo work actually happens. |
| [NVlabs/alpagym](https://github.com/NVlabs/alpagym) | Apache-2.0 | 163 | ↑ from 157. |
| [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 528 | ↑ from 520. |
| [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) | Apache-2.0 (code) · ⚠️ OpenMDW-1.1 (weights) | 370 | ↑ from 368. **Weight licence recorded for the first time.** |
| [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker) | Apache-2.0 | 82 | ↑ from 80. Release 0.6.1 + Quarkslab audit. Maturity signal despite low stars. |
| [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification) | MPL-2.0 | 451 | ↑ from 449. COVESA hosts 100+ companies around it. |
| [eclipse-ankaios/ankaios](https://github.com/eclipse-ankaios/ankaios) | Apache-2.0 | 125 | Flat. Workload orchestration for automotive HPCs. |
| [ApolloAuto/apollo](https://github.com/ApolloAuto/apollo) | Apache-2.0 | 26.9k | Flat. README line is now **Apollo 11.0**, *"focuses on the large-scale deployment of functional autonomous vehicles."* |
| [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | Apache-2.0 | 12.2k | Flat. Remains the leading vendor-neutral AV stack. |
| [traccar/traccar](https://github.com/traccar/traccar) | Apache-2.0 | 7.9k | Flat. 200+ device protocols; steady, not spiking. |
| [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | Flat (rounded). |

### Stable anchors (re-verified, no significant movement)

[carla-simulator/carla](https://github.com/carla-simulator/carla) MIT 14.5k★ ·
[open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) Apache-2.0 6.6k★ ·
[OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) Apache-2.0 4.8k★ ·
[commaai/opendbc](https://github.com/commaai/opendbc) MIT 3.5k★

### New repos recorded but NOT recommended

Found while re-searching the dealership-management gap. All live on 2026-10-26; none is a usable base.

| Repo | Licence | Stars | Why it is here |
|---|---|---|---|
| [winterautollc/OpenAutoCore](https://github.com/winterautollc/OpenAutoCore) | ⚠️ **GPL-3.0** | 9 | Live independent-repair-shop manager (Python/PyQt6/MySQL). Recorded so the DMS gap is precise: shop managers exist, a DMS does not. GPL blocks proprietary deliverables. |
| [ChanMeng666/Automotive-Repair-Management-System](https://github.com/ChanMeng666/Automotive-Repair-Management-System) | not read | — | The most feature-complete hit — **archived by its owner 2026-07-08**. Recorded as a dead end so it is not rediscovered as a candidate. |
| [dimitar-grigorov/GarageBuddy](https://github.com/dimitar-grigorov/GarageBuddy) | not read | — | ASP.NET Core garage management; README marks features "work in progress". |

---

## 2026-10-15

**Method note first, because it changes how this file should be read:** `github.com/trending` has **no
automotive topic filter**, and the relevant topic pages (`automotive-ai`, `automotive`,
`autonomous-vehicles`, `automotive-data`) surface mostly 0–5 star projects. There is no reliable trending
feed for this industry. The entries below are therefore movements in *verified foundational repos* and
vendor releases, which is the only signal available — not a scraped trending list.

### Movement this period

| Repo | Licence | Stars | Movement |
|---|---|---|---|
| [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | New in 2026; open AV simulation platform for end-to-end policies. Now rivals CARLA in mindshare for policy evaluation. |
| [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) | Apache-2.0 | 2.0k | Reached 2.0k★ then was **deprecated** in favour of Alpamayo Recipes / 1.5. |
| [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 520 | Stable checkpoints published Sep 2026. |
| [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker) | Apache-2.0 | 80 | Release 0.6.1 (Apr 2026) + completed Quarkslab security audit — meaningful maturity signal despite low stars. |
| [traccar/traccar](https://github.com/traccar/traccar) | Apache-2.0 | 7.9k | Actively maintained (updated Oct 2026); 200+ device protocols. Steady, not spiking. |
| [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | Apache-2.0 | 12.2k | Stable; remains the leading vendor-neutral AV stack. |

### Stable anchors (no significant movement, listed for reference)

[commaai/openpilot](https://github.com/commaai/openpilot) MIT 63.9k★ ·
[ApolloAuto/apollo](https://github.com/ApolloAuto/apollo) Apache-2.0 26.9k★ ·
[carla-simulator/carla](https://github.com/carla-simulator/carla) MIT 14.5k★ ·
[open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) Apache-2.0 6.6k★ ·
[open-mmlab/OpenPCDet](https://github.com/open-mmlab/OpenPCDet) Apache-2.0 5.7k★ ·
[OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) Apache-2.0 4.8k★ ·
[eclipse-sumo/sumo](https://github.com/eclipse-sumo/sumo) EPL-2.0 4.2k★ ·
[commaai/opendbc](https://github.com/commaai/opendbc) MIT 3.5k★

---

## History — snapshots before 2026-10-15

> ⚠️ **Accuracy note added 2026-10-15:** the snapshot below was byte-identical to `agents/trending.md` —
> the same scrape written to both files, so it recorded no distinct repo trend. Several entries are not
> automotive software and several have `?` / `NOASSERTION` licences (no verified grant). Preserved verbatim
> for continuity, **not** as recommendations.


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

