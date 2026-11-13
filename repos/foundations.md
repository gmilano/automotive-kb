---
industry: automotive
region: Global
updated: 2026-11-13
---

# 🏗️ Foundational repos — Automotive

> The bases to build on. Open licence, active community. Grouped by layer, because "automotive open source"
> is four unrelated stacks that are routinely confused.
> **Verification (2026-11-13):** `curl -sI` on `github.com` returns **HTTP 403** through this session's
> proxy — re-tested today on three URLs including `api.github.com`, all 403 — so figures are read from
> rendered repository pages. Where the licence was the point, the file was fetched raw from
> `raw.githubusercontent.com`; that is how `autoware-safety-island` was reclassified from GitHub's
> **"Other"** label to **verbatim Apache-2.0** (its file is `license.rst`) and how
> `autoware_latent_drive` was confirmed to have **no licence at all**.
> 🔴 **`huggingface.co` still does not resolve from this session**, so no model-weight licence was verified.
> 🆕 = added 2026-11-13. 🔄 = licence/stars re-read today. ⏸ = URL re-probed, figures carried forward.
> ⚪ = URL live, licence/stars deliberately left blank rather than guessed.

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
