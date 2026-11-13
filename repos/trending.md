---
industry: automotive
region: Global
updated: 2026-11-13
---

# 📈 Trending repos — Automotive

> **APPEND-ONLY.** Newest dated section on top; history preserved below. Never rewrite earlier sections.

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

