---
industry: automotive
region: Global
updated: 2026-11-13
---

# 🎯 AI agents & models — Automotive

> Open-source AI agents, policies and models for the automotive industry. Focus: MIT / Apache 2.0 / BSD.
> **Verification method this pass (2026-11-13):** `curl -sI` against `github.com` returns **HTTP 403**
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
