---
industry: automotive
region: Global
updated: 2026-11-13
---

# 📈 Trending AI agents & models — Automotive

> **APPEND-ONLY.** Newest dated section on top; history preserved below. Never rewrite earlier sections.

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

